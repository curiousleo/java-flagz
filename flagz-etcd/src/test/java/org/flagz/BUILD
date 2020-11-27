java_test(
    name = "tests",
    size = "large",
    srcs = glob(["*.java"]),
    tags = ["exclusive"],
    deps = [
        "//flagz-etcd/src/main/java/org/flagz",
        "//flagz-java/src/main/java/org/flagz",
        "//third_party/etcd4j",
        "//third_party/guava",
        "//third_party/slf4j:api",
        "//third_party/slf4j:simple-stdout",
        "//third_party/testing",
    ],
)
