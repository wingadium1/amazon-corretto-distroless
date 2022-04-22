workspace(name = "distroless-amazon-corretto-11")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_file")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "92779d3445e7bdc79b961030b996cb0c91820ade7ffa7edca69273f404b085d5",
    strip_prefix = "rules_docker-0.20.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.20.0/rules_docker-v0.20.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//container:container.bzl", "container_pull")

container_pull(
    name = "alpine-x64",
    registry = "index.docker.io",
    repository = "alpine",
    tag = "latest",
)

container_pull(
    name = "java_base-nonroot-x64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "nonroot",
)

container_pull(
    name = "java_base_debug-nonroot-x64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "debug-nonroot",
)

container_pull(
    name = "java_base-root-x64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "latest",
)

container_pull(
    name = "java_base_debug-root-x64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "debug",
)

container_pull(
    name = "java_base-nonroot-arm64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "nonroot-arm64",
)

container_pull(
    name = "java_base_debug-nonroot-arm64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "debug-nonroot-arm64",
)

container_pull(
    name = "java_base-root-arm64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "latest-arm64",
)

container_pull(
    name = "java_base_debug-root-arm64",
    registry = "gcr.io",
    repository = "distroless/java-base-debian11",
    tag = "debug-arm64",
)
