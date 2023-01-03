load("@emsdk//emscripten_toolchain:wasm_rules.bzl", "wasm_cc_binary")

# no-deprecated-builtins to skip warning
# build:
# clear&bazel build hello-world-with-absl-wasm --copt="-Wno-deprecated-builtins" --copt="-pthread" --linkopt="-pthread"
# node --experimental-wasm-threads --experimental-wasm-bulk-memory bazel-bin/hello-world-with-absl-wasm/hello-world-with-absl.js
wasm_cc_binary(
    name = "protoc-wasm",
    cc_target = "@com_google_protobuf//:protoc",    
)