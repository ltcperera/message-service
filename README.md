# A Messaging Service Implementation

Message queues are used in software to allow multiple components to communicate by asynchronously sending data between each other. This implementation of a messaging service enables components to send messages synchronously or asynchronously. 

Messages are sent as broadcast messages to all subscribers registered for the specific message. For synchronous messages, the service blocks the sender thread until the message is delivered to all subscribers. The messaging service sends an acknowledgement once the message is delivered to all subscribers. With asynchronous messages, the sender thread specifies a callback and continues execution after sending the message. The messaging service sends the acknowledgement asynchronously via the callback after the message is delivered to all subscribers.

### Building

The project requires [CMake](https://cmake.org). The `runbuild.sh` script included will create the **build** directory and invoke CMake followed by make to build the project. The CMake script will download and build the Google Test framework as a dependency first, followed by building the tests for the dynamic array library. The final test binary is stored in the **build** directory.

Run the `runbuild.sh` script to build everything including the google tests.

### Usage

1. The messaging service needs to be initialized first. This returns a handle that can be used with subsequent operations.

    ```c
    // Initializes the message service
    handle = message_service_init(); 
    ```

2. Subscribers to messages need to register callbacks with the message service.

    ```c
    // Subscribe for the message. The callback will be triggered when message
    //   matching MESSAGE_ID is received.
    message_service_subscribe(handle, MESSAGE_ID, callback);
    ```

    ```c
    // Callback for processing received messages
    void callback(void *pData)
    {

    }
    ```

3. Senders that need to send messages allocate the memory for the message and sends the message synchronously or asynchronously

    ```c
    // Allocate memory for the message
    struct MESSAGE_DATA *pMessage_data = 
           (MESAGE_DATA*) message_service_allocate(sizeof(MESSAGE_DATA));
    // Populate message data
    pMessage_data->data1 = 50;
    pMessage_data->data2 = 250;

    // Send the message synchronously. 
    // The function will block until the message is delivered.
    message_service_send_sync_message(handle,MESSAGE_ID, pMessage_data, sizeof(MESSAGE_DATA));
    ```

