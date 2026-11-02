---
name: ros2-engineering
description: Use for ROS 2 Jazzy package architecture, C++ development, dependencies, builds, testing, and runtime debugging.
license: MIT
metadata:
  author: Niklas Peter
  version: "1.0.2 & upwards"
---

# ROS 2 Jazzy Engineering

Develop maintainable ROS 2 Jazzy systems using C++20, `rclcpp`, and `ament_cmake`. Respect existing project conventions and approved development scope.

## Architecture

- For new projects, identify robot subsystems and document a proposed package architecture during onboarding. Create packages only in a later approved milestone, initially as buildable skeletons without nodes.
- Preserve reasonable existing workspace structures.
- Prefer fewer cohesive packages with multiple related nodes rather than one package per node.
- Use packages by responsibility: `<robot>_bringup` for all launch files and configuration, `<robot>_description` for URDF/Xacro and meshes, `<robot>_perception` for sensor processing, `<robot>_control` for control logic, and `<robot>_interfaces` for custom `.msg`, `.srv`, and `.action`.
- Keep hardware drivers separate from processing nodes. Create only packages that are actually needed.

## Environment and Dependencies

- Verify ROS 2 Jazzy, workspace structure, sourced overlays, and relevant package declarations.
- Before ROS development, check dependencies across the entire workspace:
  `rosdep check --from-paths src --ignore-src --rosdistro jazzy`
- If any dependency is missing or a new external ROS/system dependency is required, **stop and inform the operator**. Explain what is needed and why. The operator handles installation.
- Never silently install dependencies, change ROS distributions, or treat a successful `rosdep` check as proof of runtime correctness.

## C++ and Nodes

- Prefer C++20 and `rclcpp` for nodes; use Python only when technically justified.
- Use `ament_cmake` and maintain accurate `package.xml` and `CMakeLists.txt` files.
- Each implementation `.cpp` has a matching `.hpp`, except standalone test files. A node's `main()` resides in its own implementation `.cpp`.
- Naming: `PascalCase` classes, `camelCase` functions, `snake_case` files and variables, trailing `_` for private members.
- Header order: includes, class with `public` before `private`, constructors/destructors, function declarations, variables, and ROS members.
- Default new packages to C++20 with `-Wall -Wextra -Wpedantic`, without mandatory `-Werror`. Inspect existing build flags before changing them.
- Keep nodes functionally focused. Check interfaces, message types, and publisher/subscriber QoS compatibility; investigate QoS through targeted testing rather than fixed universal defaults.
- Use ROS logging instead of `std::cout`; throttle repetitive messages when necessary.
- End each node constructor with an `RCLCPP_INFO` initialization message. Prefer ordinary `rclcpp::Node` unless lifecycle behavior is needed.

## Launch and Configuration

- Store all launch files in `<robot>_bringup`, including alternative operational modes.
- Prefer YAML launch files. Propose Python only when YAML becomes unnecessarily complicated.
- Avoid parameter configuration files initially. At roughly ten parameters per launch, consolidate them into a corresponding YAML file in `bringup/config/`.

## Builds and Tests

- Build using `colcon build` in Debug mode, without `--symlink-install`.
- Rebuild only affected packages. Include dependent consumers when interfaces or shared dependencies change.
- Use appropriate package-selection options; inspect compiler flags and build errors before troubleshooting.
- Write automated tests against existing requirements and reference their IDs. Every new node package needs automated tests.
- Run relevant `colcon test` checks and inspect results. Verify runtime behavior when compilation alone is insufficient.
- Never weaken tests or assertions just to obtain a passing result.

## Runtime Debugging

- Form a specific hypothesis and choose the smallest test that can validate it.
- Use concurrent shell sessions as needed, sourcing ROS Jazzy and the correct workspace overlay independently.
- Start only the required nodes. Use targeted diagnostics such as `ros2 topic hz`, single-message inspection, or `ros2 topic pub --once`.
- Allow controlled background processes and PID tracking where useful.
- Set an appropriate timeout or completion condition; never leave diagnostic commands waiting indefinitely.
- After each session, stop every process started for that test and close its shells. Never terminate unrelated processes.
- Diagnose from actual logs, ROS graph state, parameters, and observations rather than assumptions.

## Verification and Safety

- Software-only testing and simulation are permitted within the approved scope.
- Never operate connected physical hardware or actuators. Physical verification belongs to the operator.
- Report affected packages, dependency status, requirement-linked test results, runtime findings, and unverified behavior.
