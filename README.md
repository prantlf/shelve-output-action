# Shelve Build Output

GitHub action for shelving a build output, usually a binary executable, on each platform to cache, so that it can be unshelved later in the final job by [unshelve-output-action], to be able to produce a release for all platforms.

Only platforms Linux, macOS, Windows on the architecture X64 are supported.

## Usage

Pack the binary executable produced with the project name to the project root:

```yml
- uses: prantlf/shelve-output-action@v2
```

Depending on the platform, where the action is running, and the `name` of the executable, it will create one of the following archives and upload it to the cache. For example, for the name `newchanges`:

|    OS   | Architecture |            Archive           |            Cache Key               |
|:--------|:-------------|:-----------------------------|:-----------------------------------|
| Linux   |      X64     | `newchanges-linux-x64.zip`   | `newchanges-linux-x64.zip-{sha}`   |
| macOS   |     ARM64    | `newchanges-macos-arm64.zip` | `newchanges-macos-arm64.zip-{sha}` |
| macOS   |      X64     | `newchanges-macos-x64.zip`   | `newchanges-macos-x64.zip-{sha}`   |
| Windows |      X64     | `newchanges-windows-x64.zip` | `newchanges-windows-x64.zip-{sha}` |

The name and path to the executable can be specified by `path`. The name prefix of the archive can be specified by `name`, the full file name by `archive`. If not specified, it will be inferred from the project configuration (`v.mod`). The `{sha}` in the cache key is the SHA-1 hash of the current commit.

Use a different name, platform and architecture in the package archive name than the defaults. Specify a custom path to the binary. Work only in specific release branches:

```yml
jobs:
  build:
    steps:
    - uses: actions/checkout@v4
    - uses: prantlf/setup-v-action@v2
    - run: ...
    - uses prantlf/shelve-output-action@v2
      with:
        archive: vpm-ubuntu-amd64.zip
        path: bin/vpm
        branches: master v1.x
```

## Inputs

The following parameters can be specified using the `with` object:

### name

Type: `String`<br>
Default: (read from `v.mod`)

The name of the archive without the platform and architecture and without the `.zip` extension. The project name from `v.mod` will be used by default. The name of the archive will be `{name}-{os}-{arch}.zip`, for example: `newchanges-linux-x64.zip`.

### archive

Type: `String`<br>
Default: (read from `v.mod`)

The name of the archive to be created. The project name from `v.mod` will be used by default, if `name` isn't provided. The name of the archive will be `{name}-{os}-{arch}.zip`, for example: `newchanges-linux-x64.zip`.

### os

Type: `String`<br>
Default: (read from `runner.os`)

Override the operating system of the runner. Use if you are cross-compiling. Possible values: `linux`, `macos`, and `windows`.

### arch

Type: `String`<br>
Default: (read from `runner.arch`)

Override the architecture of the runner. Use if you are cross-compiling. Possible values: `arm`, `arm64`, `x64`, and `x86`.

### path

Type: `String`<br>
Default: (read from `v.mod`)

The path to the binary file to package, on Windows including the `.exe` extension. The project name from `v.mod` will be used by default, with the file extension according to the platform (`.exe` will be appended on Windows).

### branches

Type: `String`<br>
Default: `'main master'`

Branches which this action should run for, which are used to publishing releases. Use whitespace for separating the branch names. If you want to use multiple lines in YAML, introduce them with ">-". If you want to allow all branches, set the value to "*".

### enable

Type: `Boolean`<br>
Default: `true`

Can be set to `false` to prevent this action from packing the archive. It's helpful in the pipeline, which will not continue releasing, but only building and testing, and that will be decided in the middle of a job execution.

## Outputs

The following parameters can be accessed by the `github` context:

### archive

Type: `String`<br>

The name of the archive, which was created.

### path

Type: `String`<br>

The path to the file, which was packed.

### cache-key

Type: `String`<br>

The key, which was used to store the created archive to cache.

## License

Copyright (C) 2023 Ferdinand Prantl

Licensed under the [MIT License].

[MIT License]: http://en.wikipedia.org/wiki/MIT_License
[unshelve-output-action]: https://github.com/prantlf/unshelve-output-action
