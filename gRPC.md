# gRPC

## Terms

1. **IDL(Interface Definition Language)**

2. What's stream in protobuf.
   1. Unary RPC
   2. Server Streaming RPC
   3. Client Streaming RPC
   4. Bidirectional Streaming RPC

```protobuf
rpc BidiHello(stream HelloRequest) returns (stream HelloResponse);
```

3. Stub = client

## [Authentication](https://grpc.io/docs/guides/auth/)

