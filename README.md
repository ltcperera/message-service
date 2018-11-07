# A Messaging Service Implementation

### Building

The project requires [CMake](https://cmake.org). The `runbuild.sh` script included will create the **build** directory and invoke CMake followed by make to build the project. The CMake script will download and build the Google Test framework as a dependency first, followed by building the tests for the dynamic array library. The final test binary is stored in the **build** directory.

Run the `runbuild.sh` script to build everything including the google tests.
