Basic components of protobuf:

- syntax = proto2;: There are two versions of the protocol buffers language, namely `proto2` and `proto3`. 
- message: message
- field rule, type, name, number: A field is a portion of a message.
  - field rule: specifies if the field under consideration is required, optional, or repeated. They mean just that.
  - field type: specifies the data type of the field e.g., number (uint32), string etc.
  - field name: name of the field
  - field number: unique identifier for said field. It is a good practice to start numbering from 1 since smaller integers require lesser storage.

## Resources
- https://dev.to/techschoolguru/protocol-buffer-deep-dive-52d9. A good resource.
- [Protocol Buffers Crash Course](https://www.youtube.com/watch?v=46O73On0gyI). A good resource to start.
- [Serialization formats: JSON and Protobuf](https://www.youtube.com/watch?v=uGYZn6xk-hA)
- [Protocol Buffers & JSON - SingaporeJS](https://www.youtube.com/watch?v=9IUrAZHxn3s)
- [The Need for Protocol Buffers](https://www.youtube.com/watch?v=BywIOD_Y3CE)
- [What are Protocol Buffers & When to Use them | Protobuf vs JSON](https://www.youtube.com/watch?v=9fh-XdUH7qw)
