workspace(name = "org_flagz")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

rules_jvm_version = "3.3"

http_archive(
    name = "rules_jvm_external",
    sha256 = "d85951a92c0908c80bd8551002d66cb23c3434409c814179c0ff026b53544dab",
    strip_prefix = "rules_jvm_external-{}".format(rules_jvm_version),
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/{}.zip".format(rules_jvm_version),
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "org.reflections:reflections::0.9.10",
        "org.javassist:javassist::3.20.0-GA",
        "org.slf4j:slf4j-api:1.7.13",
        "org.slf4j:slf4j-simple:1.7.13",
        "com.google.guava:guava:19.0",
        "com.google.code.findbugs:jsr305:1.3.9",
        "junit:junit:4.12",
        "org.hamcrest:hamcrest-all:1.3",
        "org.mockito:mockito-all:1.10.19",
        "org.mousio:etcd4j:2.12.0",
        "io.netty:netty-all:4.1.3.Final",
        "com.fasterxml.jackson.core:jackson-annotations:2.8.0",
        "com.fasterxml.jackson.core:jackson-core:2.8.0",
        "com.fasterxml.jackson.core:jackson-databind:2.8.0",
        "com.fasterxml.jackson.module:jackson-module-afterburner:2.8.0",
    ],
    # Run `bazel run @unpinned_maven//:pin` to update maven_install.json
    maven_install_json = "//:maven_install.json",
    repositories = [
        "https://repo1.maven.org/maven2",
    ],
)

load("@maven//:defs.bzl", "pinned_maven_install")

pinned_maven_install()

# Scala stuff.
skylib_version = "1.0.3"

http_archive(
    name = "bazel_skylib",
    sha256 = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c",
    type = "tar.gz",
    url = "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/{}/bazel-skylib-{}.tar.gz".format(skylib_version, skylib_version),
)

rules_scala_version = "9bd9ffd3e52ab9e92b4f7b43051d83231743f231"

http_archive(
    name = "io_bazel_rules_scala",
    sha256 = "438bc03bbb971c45385fde5762ab368a3321e9db5aa78b96252736d86396a9da",
    strip_prefix = "rules_scala-%s" % rules_scala_version,
    type = "zip",
    url = "https://github.com/bazelbuild/rules_scala/archive/%s.zip" % rules_scala_version,
)

load("@io_bazel_rules_scala//:scala_config.bzl", "scala_config")

scala_config()

load("@io_bazel_rules_scala//scala:scala.bzl", "scala_repositories")

scala_repositories()

load("@io_bazel_rules_scala//scala:toolchains.bzl", "scala_register_toolchains")

scala_register_toolchains()

load("@io_bazel_rules_scala//testing:scalatest.bzl", "scalatest_repositories", "scalatest_toolchain")

scalatest_repositories()

scalatest_toolchain()
