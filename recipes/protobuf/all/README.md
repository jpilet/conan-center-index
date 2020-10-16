The conan cmake setup will make the cmake variable
`PROTOBUF_PROTOC_EXECUTABLE` point to the protoc executable.

It will also define an imported executable target: `protobuf::protoc`.

To consume this package, you can do:


```
conan_basic_setup(TARGETS)

# no need for findPackage(Protobuf)

# Add .proto as sources
add_executable(greeter_client_server helloworld.proto greeter_client_server.cc)

protobuf_generate(APPEND_PATH LANGUAGE cpp TARGET greeter_client_server)

target_link_libraries(greeter_client_server CONAN_PKG::protobuf)
```

