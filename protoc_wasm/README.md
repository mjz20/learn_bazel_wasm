This project is to build protobuf to wasm, there are several issues:
-"Protobuf only supports C++14 and newer.", and --cxxopt="-std=c++17" does not work, I see other has the same [issue](https://stackoverflow.com/a/70867347),so will need set --action_env=BAZEL_CXXOPTS="-std=c++17"
- After add more -Wno-XYZ to avoid errors from warning, there is still one i cannot get rid of: 
```
external/com_google_absl/absl/hash/internal/low_level_hash.cc:43:38: error: argument 'salt' of type 'const uint64_t[]' (aka 'const unsigned long long[]') with mismatched bound [-Werror,-Warray-parameter]
                      const uint64_t salt[]) {
                                     ^
external/com_google_absl/absl/hash/internal/low_level_hash.h:44:38: note: previously declared as 'const uint64_t[5]' (aka 'const unsigned long long[5]') here
                      const uint64_t salt[5]);
```
I think the reason maybe because the order of copt, to reproduce: 

```
bazel build  --action_env=BAZEL_CXXOPTS="-std=c++17" --copt=-Wno-array-parameter --copt=-Wno-deprecated-builtins --copt=-Wno-deprecated-non-prototype --copt=-Wno-unused-function protoc-wasm --sandbox_debug 2>&1|tee /tmp/build.log
```
