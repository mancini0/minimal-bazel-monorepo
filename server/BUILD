load("@io_bazel_rules_docker//nodejs:image.bzl", "nodejs_image")
load("@npm_bazel_typescript//:index.bzl", "ts_library")

ts_library(
    name = "lib",
    srcs = [
        "util.ts",
    ],
)

ts_library(
    name = "main",
    srcs = [
        "index.ts",
    ],
    deps = [":lib"],
)

filegroup(
    name = "libfiles",
    srcs = ["lib"],
    output_group = "es5_sources",
)

filegroup(
    name = "mainfile",
    srcs = ["main"],
    output_group = "es5_sources",
)

nodejs_image(
    name = "server",
    data = [
        ":libfiles",
        ":mainfile",
    ],
    entry_point = ":mainfile",
)
