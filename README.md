# A Messaging Service Implementation

Message queues are used in software to allow multiple components to communicate by asynchronously sending data between each other. This implementation of a messaging service enables components to send messages synchronously or asynchronously. 

Messages are sent as broadcast messages to all subscribers registered for the specific message. For synchronous messages, the service blocks the sender thread until the message is delivered to all subscribers. The messaging service sends an acknowledgement once the message is delivered to all subscribers. With asynchronous messages, the sender thread specifies a callback and continues execution after sending the message. The messaging service sends the acknowledgement asynchronously via the callback after the message is delivered to all subscribers.

### Building

The project requires [CMake](https://cmake.org). The `runbuild.sh` script included will create the **build** directory and invoke CMake followed by make to build the project. The CMake script will download and build the Google Test framework as a dependency first, followed by building the tests for the dynamic array library. The final test binary is stored in the **build** directory.

Run the `runbuild.sh` script to build everything including the google tests.
