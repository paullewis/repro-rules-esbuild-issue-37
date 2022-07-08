# Repro for rules_esbuild issue 37

This is a repro for https://github.com/aspect-build/rules_esbuild/issues/37

## Running

1. `pnpm install`
1. `bazel clean`
1. `bazel build //:index`

This should fail due to missing deps.

## Using esbuild directly

1. `npm run build`

This build should write the contents to stdout.
