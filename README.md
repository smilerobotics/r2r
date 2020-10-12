R2R - Minimal ROS2 Rust bindings
====================

Minimal bindings for ROS2 that do *not* require hooking in to the ROS2 build infrastructure. If you want a more ROS-oriented approach, see <https://github.com/ros2-rust/ros2_rust>. In these bindings, convenience Rust types are created by calling into the c introspection libraries to circumvent the .msg/.idl pipeline. The convenience types can be ignored when you need to trade convenience for performance, e.g. treating large chunks of data manually.

Manual is available on github pages <https://sequenceplanner.github.io/r2r/>

How to use
--------------------
1. Make sure you have libclang installed. (e.g. libclang-dev on ubuntu)
2. Depend on this package: r2r = { git = "https://github.com/sequenceplanner/r2r" }.
3. You need to source your ROS2 installation before building/running.
4. The bindings will rebuild automatically if/when you source your workspace(s).
5. If you make changes to existing message types, run cargo clean -p msg_gen to force recompilation of the rust message types on the next build.

A couple of examples are included in examples/
```
. /opt/ros/foxy/setup.sh
cargo build
cargo run --example subscriber_with_thread
```
An example application can be found here <https://github.com/sequenceplanner/r2r-echo>, which can be installed by running cargo install --git https://github.com/sequenceplanner/r2r-echo.

What works?
--------------------
- Up to date with ROS2 ~Dashing~ ~Eloquent~ Foxy
- Building Rust types
- Publish/subscribe
- Services
- Parameters

TODO
--------------------
- The code generation is currently just a big hack. Needs cleanup and refactoring.
- Expose more of the RCL like QoS settings.
- Action types?
- Async API!