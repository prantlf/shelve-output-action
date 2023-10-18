# Shelve Build Output

[![Latest version](https://img.shields.io/npm/v/shelve-output-action) ![Dependency status](https://img.shields.io/librariesio/release/npm/shelve-output)](https://www.npmjs.com/package/shelve-output)

GitHub action for shelving a build output, usually a binary executable, on each platform to cache, so that it can be unshelved later in the final job, which will produce a release for all platforms.

Only platforms Linux, macOS, Windows on the architecture X64 are supported.

## Usage

Pack the binary executable produced with the project name to the project root:

```yml
- uses: prantlf/shelve-output-action@v1
```

Use a different name, platform and architecture that defaults in the package archive name. Specify a custom path to the binary:

```yml
jobs:
  build:
    steps:
    - uses: actions/checkout@v4
    - uses: prantlf/setup-v-action@v1
    - run: ...
    - uses prantlf/shelve-output-action@v1
      with:
        name: vpm-ubuntu-amd64.zip
        path: bin/vpm
```

## Inputs

The following parameters can be specified using the `with` object:

### archive

Type: `String`<br>
Default: (read from `v.mod`)

The name of the archive to be created. The project name from `v.mod` will be used by default. The name of the archive will be `{name}-{os}-{arch}.zip`, for example: `newchanges-linux-x64.zip`.

### path

Type: `String`<br>
Default: (read from `v.mod`)

The path to the binary file to package. The project name from `v.mod` will be used by default, with the file extenson according to the platform. (`.exe` will be appended on Windows by default.)

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

The key, whcih was used to store the created archive to cache.

## License

Copyright (C) 2023 Ferdinand Prantl

Licensed under the [MIT License].

[MIT License]: http://en.wikipedia.org/wiki/MIT_License
