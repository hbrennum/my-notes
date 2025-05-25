# Zero Message Queue library
ZeroMQ (also known as ØMQ or ZMQ) is a high-performance, asynchronous messaging library for use in distributed applications. ZeroMQ is brokerless, providing a direct peer-to-peer communication model.

PyZMQ is the official Python binding for the ZeroMQ library, making its powerful features accessible to Python developers.

## Example tasks
- Communication backbone for *distributed systems* and high-performance computing clusters
- Efficient communication between processes or microservices on the same machine
- Distributing workloads among multiple worker processes or machines

## Core concepts
ZeroMQ focus on complete messages and not byte streams like UDP or TCP protocols. ZMQ provides sockets that implement specific messaging patterns.

- **Brokerless**: Communication is directly between peers, which can reduce latency and simplify deployment.
- **Message-Oriented**: Messages are sent and received as complete units, simplifying parsing and handling.
- **Platform Agnostic**: ZeroMQ is implemented in C++ and has bindings for numerous programming languages.
- **Scalable**: Its design promotes highly scalable architectures, from simple client-server setups to complex distributed systems with many nodes.

## Typical Messaging Patterns

1. **Request-Reply (REQ-REP)** Classic client-server pattern. A client (REQ socket) sends a request and then waits for a reply from a server (REP socket). The server receives a request, processes it, and sends a reply. This pattern is strictly synchronous on the client side (send, then receive).
    - Sockets: zmq.REQ (client), zmq.REP (server)
1. **Publish-Subscribe (PUB-SUB)** A publisher (PUB socket) broadcasts messages to multiple subscribers (SUB sockets). Subscribers can filter messages based on a "topic" (a string prefix). Messages sent by the publisher before a subscriber connects are generally not received by that subscriber (no message buffering).
    - Sockets: zmq.PUB (publisher), zmq.SUB (subscriber)
1. **Pipeline (PUSH-PULL)** Parallel task distribution and collection. A PUSH socket distributes messages to connected PULL sockets in a round-robin fashion (for load balancing). PULL sockets receive messages from connected PUSH sockets in a fair-queued manner. It's often used for "fan-out" (distributing work) or "fan-in" (collecting results).
    - Sockets: zmq.PUSH (producer/distributor), zmq.PULL (worker/collector)

## Example code (client-server pattern)

### Server

```python
import time
import zmq      # sudo apt install python3-zmq

def main():
    # Define ZMQ queue
    context = zmq.Context()             # Declare ZMQ context
    socket = context.socket(zmq.REP)    # Define a REPly socket (server)
    socket.bind("tcp://*:5556")         # Bind socket to TCP port 5556
    
    # Server main loop
    while True:
        try:
            # wait for next request from client
            message = socket.recv()
            print(f"Received request from client: {message}")

            # Do some work
            time.sleep(1)

            # Send reply back to client
            socket.send_string("World")
        except KeyboardInterrupt:
            socket.close()
            print(f"Server closed by user")
            break

if __name__ == '__main__':
    main()    
```

### Client

```python
import zmq

def main():
    
    print(f"Connecting to hello world server ...")

    context = zmq.Context()                     # Declare ZMQ context
    socket = context.socket(zmq.REQ)            # REQuest socket
    socket.connect("tcp://localhost:5556")      # Bind socket to TCP port 5556

    for request in range(10):
        print(f"Sending request {request} ...")
        socket.send_string("Hello")

        # Get the reply
        message = socket.recv()
        print(f"Received reply {request} [ {message} ]")

if __name__ == '__main__':
    main()
```

## More information
 - [ØMQ - The Guide](https://zguide.zeromq.org/)
 - https://zeromq.org/languages/python/
 - https://github.com/zeromq/pyzmq