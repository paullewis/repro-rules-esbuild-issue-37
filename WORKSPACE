load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "aspect_rules_esbuild",
    sha256 = "77c414e7d82c9a66b4b6d6cb81a7a379f462215b52f5bae90faecde81798189f",
    strip_prefix = "rules_esbuild-0.9.0",
    url = "https://github.com/aspect-build/rules_esbuild/archive/refs/tags/v0.9.0.tar.gz",
)

http_archive(
    name = "aspect_rules_js",
    sha256 = "80e168f9cd62f3640de429b70b34ff817d0d94ada2abaf2cffeef46e35434e1d",
    strip_prefix = "rules_js-1.0.0-rc.1",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.0.0-rc.1.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    verify_node_modules_ignored = "//:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()

load("@aspect_rules_esbuild//esbuild:dependencies.bzl", "rules_esbuild_dependencies")

rules_esbuild_dependencies()

# Register a toolchain containing esbuild npm package and native bindings
load("@aspect_rules_esbuild//esbuild:repositories.bzl", "LATEST_VERSION", "esbuild_register_toolchains")

esbuild_register_toolchains(
    name = "esbuild",
    esbuild_version = LATEST_VERSION,
)
