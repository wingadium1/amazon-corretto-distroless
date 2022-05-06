# amazon-corretto-distroless
Provide a distroless image for Amazon Corretto based on **gcr.io/distroless/java-base**

## Step to build
1. Build all target image
```shell
bazel build //:all
```
2. Create docker image for specific target, please refer to bazel **BUILD** file.
```
# Create nonroot image for Arm64 architecture.
bazel run //:java11corretto_nonroot_arm64
```
