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


#this does not work due to many pthread compile and link issues
# no-deprecated-builtins to skip warning
# bazel build hello-world-with-absl-wasm --copt="-Wno-deprecated-builtins" --sandbox_debug
# todo fix: 
#err-1: --shared-memory is disallowed by raw_logging.o because it was not compiled with 'atomics' or 'bulk-memory' features.
wasm_cc_binary(
    name = "hello-world-with-absl-wasm",
    cc_target = ":hello-world-with-absl",
)