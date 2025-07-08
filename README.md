# Go gRPC Learning Project

This project is a minimal example to help you understand how to work with gRPC in Golang. It demonstrates all four types of gRPC calls: unary, server streaming, client streaming, and bidirectional streaming.

## Project Structure

```
go-grpc/
  client/    # gRPC client implementations
  server/    # gRPC server implementations
  proto/     # Protobuf definitions and generated code
  go.mod     # Go module definition
  go.sum     # Go dependencies
```

## Prerequisites

- Go 1.23 or newer ([download Go](https://golang.org/dl/))
- `protoc` Protocol Buffers compiler ([installation guide](https://grpc.io/docs/protoc-installation/))
- `protoc-gen-go` and `protoc-gen-go-grpc` plugins:
  ```sh
  go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
  go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
  ```
  Ensure your `$GOPATH/bin` is in your `$PATH`.

## Setup

1. Clone the repository:
   ```sh
   git clone https://github.com/csush/go-grpc.git
   cd go-grpc
   ```
2. Install dependencies:
   ```sh
   go mod tidy
   ```
3. (Optional) Regenerate gRPC code if you modify `proto/greet.proto`:
   ```sh
   protoc --go_out=proto --go-grpc_out=proto proto/greet.proto
   ```

## Running the Server

In one terminal, start the gRPC server:
```sh
cd server
go run main.go
```
The server listens on `localhost:8080` by default.

## Running the Client

In another terminal, run the client:
```sh
cd client
# Edit main.go to uncomment the call you want to test (unary, server stream, client stream, or bidi stream)
go run main.go
```

## gRPC Methods Implemented

See [`proto/greet.proto`](proto/greet.proto) for full service and message definitions.

- **Unary RPC**: `SayHello(NoParam) returns (HelloResponse)`
- **Server Streaming RPC**: `SayHelloServerStreaming(NamesList) returns (stream HelloResponse)`
- **Client Streaming RPC**: `SayHelloClientStreaming(stream HelloRequest) returns (MessagesList)`
- **Bidirectional Streaming RPC**: `SayHelloBidirectionalStreaming(stream HelloRequest) returns (stream HelloResponse)`

## Customizing/Testing
- To try different RPC types, edit `client/main.go` and uncomment the relevant function call.
- You can modify the proto file and regenerate Go code as described above.

---

This project is for educational purposes and is not production-ready. Contributions and suggestions are welcome!
