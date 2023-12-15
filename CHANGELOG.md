# Changes

# [2.2.0](https://github.com/prantlf/shelve-output-action/compare/v2.1.0...v2.2.0) (2023-12-15)

## Features

* Allow packing extra files to the archives ([7571632](https://github.com/prantlf/shelve-output-action/commit/757163265caaa45eae8bf722211928e9f939081e))

# [2.1.0](https://github.com/prantlf/shelve-output-action/compare/v2.0.0...v2.1.0) (2023-11-13)

## Features

* Allow overriding runner.os and runner.arch by inputs ([dd0f43d](https://github.com/prantlf/shelve-output-action/commit/dd0f43daa86b7896493ebb28d7db30601b1b5520))

# [2.0.0](https://github.com/prantlf/shelve-output-action/compare/v1.1.0...v2.0.0) (2023-10-22)

## Features

* Run only in specified branches ([16faccb](https://github.com/prantlf/shelve-output-action/commit/16faccba212b872ecce93d8cf6e9ce21008c1e3f))

## BREAKING CHANGES

If you used this action for branches `main` or `master`, your configuration will continue working, because those branches are enabled by default. If you used it for other branches, specify all their names in the input `branches`. If you used this action on all branches, set the input `branches` to `*`.

# [1.1.0](https://github.com/prantlf/shelve-output-action/compare/v1.0.3...v1.1.0) (2023-10-21)

## Features

* Add input "name" to specify archive name with suffixes ([aee2579](https://github.com/prantlf/shelve-output-action/commit/aee2579d863ddd9d5b86554574dea3d6f446fd34))
* Add input "enable" to optionally skip this action ([0163c0f](https://github.com/prantlf/shelve-output-action/commit/0163c0f968fe7cdd7065554fd1d38b8e888e4129))

## Bug Fixes

* Drop the path from the packed executable ([88749fb](https://github.com/prantlf/shelve-output-action/commit/88749fb28b3f8dc9a12a371d855614331b2b4b74))

# [1.0.3](https://github.com/prantlf/shelve-output-action/compare/v1.0.2...v1.0.3) (2023-10-19)

## Bug Fixes

* Append .exe to the binary name on Windows ([49af19b](https://github.com/prantlf/shelve-output-action/commit/49af19b914f99d04dd79a4f1f0ed3a7492521a3e))

# [1.0.2](https://github.com/prantlf/shelve-output-action/compare/v1.0.1...v1.0.2) (2023-10-18)

## Bug Fixes

* Use powershell to pack on Windows ([608e128](https://github.com/prantlf/shelve-output-action/commit/608e128358114eb4e63abe26657fe102a36d1c5a))
* Allow restoring the cache cross-os ([61a3011](https://github.com/prantlf/shelve-output-action/commit/61a301119c8edbc474c2ebfd0bf538fa30d58669))

# [1.0.1](https://github.com/prantlf/shelve-output-action/compare/v1.0.0...v1.0.1) (2023-10-18)

## Bug Fixes

* Mention unshelve-output-action ([c4f48d8](https://github.com/prantlf/shelve-output-action/commit/c4f48d89a3c4650cc8f51681c532d67057c16b34))

# 1.0.0 (2023-10-18)

Initial release
