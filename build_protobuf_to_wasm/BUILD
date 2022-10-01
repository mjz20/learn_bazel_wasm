load("@rules_cc//cc:defs.bzl", "cc_binary")
load("@emsdk//emscripten_toolchain:wasm_rules.bzl", "wasm_cc_binary")

cc_binary(
    name = "hello-world",
    srcs = ["hello.cc"],
)

wasm_cc_binary(
    name = "hello-world-wasm",
    cc_target = ":hello-world",
)

wasm_cc_binary(
    name = "protobuf",
    cc_target = "@my_com_google_protobuf//src/google/protobuf:protobuf",
)

cc_binary(
    name = "test",
    srcs = ["tmp.cc"],
    deps = [
        "@absl//absl/strings"
    ]
)