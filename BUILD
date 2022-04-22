load("@io_bazel_rules_docker//container:image.bzl", "container_image")
load("@io_bazel_rules_docker//docker/util:run.bzl", "container_run_and_extract")
load("//:checksums.bzl", "BASE_ARCHITECTURES")

USERS = [
    "root",
    "nonroot",
]

MODES = [
    "_debug",
    "",
]

JAVA_VERSIONS = [
    "11",
    "17",
]

JAVA_BASE = {
    "{REGISTRY}/{PROJECT_ID}/java-base:latest": "//:java11corretto_root_amd64",
    "{REGISTRY}/{PROJECT_ID}/java-base:nonroot": "//:java11corretto_nonroot_amd64",
    "{REGISTRY}/{PROJECT_ID}/java-base:debug": "//:java11corretto_debug_root_amd64",
    "{REGISTRY}/{PROJECT_ID}/java-base:debug-nonroot": "//:java11corretto_debug_nonroot_amd64",
}

[
    container_run_and_extract(
        name = "base_" + arch,
        commands = [
            "mkdir /java",
            "wget https://corretto.aws/downloads/latest/amazon-corretto-11-x64-linux-jdk.tar.gz",
            "tar -C /java -xzf amazon-corretto-11-x64-linux-jdk.tar.gz",
            "mv /java/amazon-corretto-11* /java/amazon-corretto-11",
            "export $(cat /java/amazon-corretto-11/release | grep JAVA_VERSION | xargs)",
        ],
        extract_file = "/java/amazon-corretto-11",
        image = "@alpine-x64//image",
    )
    for arch in BASE_ARCHITECTURES
]

[
    container_image(
        name = "java11corretto" + mode + "_" + user + "_" + arch,
        architecture = arch,
        base = "@java_base" + mode + "-" + user + "-" + arch + "//image",
        entrypoint = [
            "/usr/bin/java",
            "-jar",
        ],
        files = [
            "base_x64/java/amazon-corretto-11",
        ],
        symlinks = {"/usr/bin/java": "/amazon-corretto-11/bin/java"},
    )
    for user in USERS
    for mode in MODES
    for arch in BASE_ARCHITECTURES
]
