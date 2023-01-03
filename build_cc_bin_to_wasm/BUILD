load("@rules_cc//cc:defs.bzl", "cc_binary")
load("@emsdk//emscripten_toolchain:wasm_rules.bzl", "wasm_cc_binary")


#simple hello world
cc_binary(
    name = "hello-world-simple",
    srcs = ["hello-world-simple.cc"],
)

#wasm version of the hello world
#
wasm_cc_binary(
    name = "hello-world-simple-wasm",
    cc_target = ":hello-world-simple",
)


#dont build this, but build simd_wasm
cc_binary(
    name = "simd",
    srcs = ["simd.cc"],
)

# bazel build simd_wasm
wasm_cc_binary(
    name = "simd_wasm",
    cc_target = ":simd",
    simd = True,
)


# bazel run hello-world-with-absl
cc_binary(
    name = "hello-world-with-absl",
    srcs = ["hello_world_with_absl.cc"],
    deps = [
        "@com_google_absl//absl/strings:strings"
    ]
)


# no-deprecated-builtins to skip warning
# build:
# clear&bazel build hello-world-with-absl-wasm --copt="-Wno-deprecated-builtins" --copt="-pthread" --linkopt="-pthread"
# node --experimental-wasm-threads --experimental-wasm-bulk-memory bazel-bin/hello-world-with-absl-wasm/hello-world-with-absl.js
wasm_cc_binary(
    name = "hello-world-with-absl-wasm",
    cc_target = ":hello-world-with-absl",
)