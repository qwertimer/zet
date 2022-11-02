# gRPC and protobuf - the world of microservices

Recently i have been looking into gRPC and protobuf, learning about how
and why they are used. Below are some notes i have collated on this
topic.

* gRPC - gRPC Remote Procedure Call.
* Protobuf - protocol buffer

gRPC can use protocol buffers as its interface language and its message
interchange format. The idea of the gRPC is  that a client can make a
call to a servers method directly on a different machine as if it were a
local object. 

The goal is to define a service specifying the methods that can be
called with their parameters and return types.
The client has a stub that provides the same methods as the server. gRPC
can use json, but defaults to protobuf.

The protocol is defined in a `.proto` file. It is structured as
messages. Where each message is a logical record of information
containing key value pairs called fields. Once defined you use protoc to
generate data access classes. Including field access and serialisers for
the data.

## Core Concepts

Based around the idea of services. Defining methods that can be called
remotely.

We can use four service types.
- Unary - client and servre send single message response.
* Server streamer - where client requests and server streams response.
* Client streamer - where the client writes sequence of messages and
  server sends a response.
* Bidirectional - Both streaming.

Users generate client and server side code and typically call the API on
the client side and implement the server side.

gRPC uses DEADLINE_EXCEEDED error for timeouts.




