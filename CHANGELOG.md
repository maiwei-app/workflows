# Changelog

## [1.0.2](https://github.com/maiwei-app/workflows/compare/v1.0.1...v1.0.2) (2026-08-15)


### Bug Fixes

* document release PR customization ([#23](https://github.com/maiwei-app/workflows/issues/23)) ([fdc9d9b](https://github.com/maiwei-app/workflows/commit/fdc9d9b85a7bcc26decee0da4943f5cf9cb23c9d))


### Reverts

* remove all release-please customization changes ([#25](https://github.com/maiwei-app/workflows/issues/25)) ([3ca08a5](https://github.com/maiwei-app/workflows/commit/3ca08a5ba5abde34cc6ab6771560a272c266ceef))

## [1.0.1](https://github.com/maiwei-app/workflows/compare/v1.0.0...v1.0.1) (2026-08-15)


### Bug Fixes

* **ci:** map known JSON files to their real schema instead of guessing ([#16](https://github.com/maiwei-app/workflows/issues/16)) ([2ffa775](https://github.com/maiwei-app/workflows/commit/2ffa77592d6fd6b3a27275962205c509b006c580))
* **ci:** real JSON schema validation and honest test tolerance ([#14](https://github.com/maiwei-app/workflows/issues/14)) ([4b9d637](https://github.com/maiwei-app/workflows/commit/4b9d6372c0742b4792cc2378d4cea46c79be9df0))
* **release:** use release-please's actual config key names ([#17](https://github.com/maiwei-app/workflows/issues/17)) ([857ccfd](https://github.com/maiwei-app/workflows/commit/857ccfd7550df56ad527949f316b242ec4d9d30c))
* **sonar:** stop excluding .github/** from analysis ([#18](https://github.com/maiwei-app/workflows/issues/18)) ([441176d](https://github.com/maiwei-app/workflows/commit/441176d137f7b36c5edca78b140d10ce5f5329a9))

## 1.0.0 (2026-08-15)


### Features

* add ci-flutter reusable workflow ([20d3399](https://github.com/maiwei-app/workflows/commit/20d339909667e47f664ebfbcecfd013e07924acc))
* add ci-hugo reusable workflow ([59af9a4](https://github.com/maiwei-app/workflows/commit/59af9a419a9685bcc6caa59c1b26a7d9420427d9))
* add ci-python reusable workflow ([fa53d65](https://github.com/maiwei-app/workflows/commit/fa53d65bbfbb2625b86e3b7a35c25a4de9291936))
* add no-ai-attribution reusable workflow ([c39017d](https://github.com/maiwei-app/workflows/commit/c39017d38c6de074bc9267602a8cf7028b202814))
* add sonar-scan reusable workflow ([122b597](https://github.com/maiwei-app/workflows/commit/122b597c7936d0248523537fcdaf5ee2c175c0ef))
* **ci:** implement versioning policy with commitlint and release-please ([#7](https://github.com/maiwei-app/workflows/issues/7)) ([c2f1224](https://github.com/maiwei-app/workflows/commit/c2f1224165dc99bd0b665cd2a2ffc5347e7173c8))
* **ci:** use maibot-app token for release-please ([440e93c](https://github.com/maiwei-app/workflows/commit/440e93ce49c55ab17ba9a097a7017191da37617d))
* **ci:** use maibot-app token for release-please ([299eaa8](https://github.com/maiwei-app/workflows/commit/299eaa8e52552e578b216cf985344a066cf300c2))


### Bug Fixes

* access SONAR_TOKEN directly from organization secret ([efc5c5f](https://github.com/maiwei-app/workflows/commit/efc5c5f1ce60967f32667fbbfa040cec1f400c23))
* add pull_request trigger so ruleset can enforce as required workflow ([ca08dca](https://github.com/maiwei-app/workflows/commit/ca08dca6bd7af16d720c1fb79622335246a36fad))
* add version pinning and HTTPS enforcement for security ([2e78fd3](https://github.com/maiwei-app/workflows/commit/2e78fd3c1db2eaf7a55584b8b7f2f2fb94e2d5db))
* **ci:** allow maibot-app[bot] as commit author in no-ai-attribution check ([2cd4b67](https://github.com/maiwei-app/workflows/commit/2cd4b672677f8c354bff024226f09926b20bdbe3))
* **ci:** allow maibot-app[bot] as commit author in no-ai-attribution check ([555d481](https://github.com/maiwei-app/workflows/commit/555d4819ffa382fdef9bc9dd1a8e03a37dbd66a1))
* **ci:** correct release-please-action org reference ([48b5789](https://github.com/maiwei-app/workflows/commit/48b5789bd219e93bbb2e0fb7d28d875d97a15e74))
* **ci:** correct release-please-action org reference ([cd167db](https://github.com/maiwei-app/workflows/commit/cd167db02c1992ab8d4073b8ac7fa82da450e050))
* **ci:** drop --require-hashes from ci-python.yml ([#8](https://github.com/maiwei-app/workflows/issues/8)) ([03bd6a3](https://github.com/maiwei-app/workflows/commit/03bd6a3ed8892caf7d216c78ebaa7c526b383ae1))
* **ci:** scope generated-with/by pattern to actual AI tool names ([858534f](https://github.com/maiwei-app/workflows/commit/858534f3739e7530e9e9e4cbc64f65ce95314cf8))
* **ci:** scope generated-with/by pattern to actual AI tool names ([1fb40ab](https://github.com/maiwei-app/workflows/commit/1fb40ab107959a6de22e45d2e1763b32e28e42a4))
* pass SONAR_TOKEN as required secret parameter ([70afa53](https://github.com/maiwei-app/workflows/commit/70afa53dec1f1e370f8017549ff8dc7f85f4efef))
* remove --no-deps from yamllint (breaks transitive dependencies) ([e234018](https://github.com/maiwei-app/workflows/commit/e2340181a05e52a8934d5e5615fbf912e238d900))
* strengthen Flutter dependency locking verification with --no-precompile ([68eca53](https://github.com/maiwei-app/workflows/commit/68eca53f29bb80f8da7ee2494ab7e55698b701a1))
* use correct SHA256 for actionlint download script ([391ead4](https://github.com/maiwei-app/workflows/commit/391ead458013f0413d844d287d20e99a7a902ebc))
* use valid action commit SHAs ([44b8c9f](https://github.com/maiwei-app/workflows/commit/44b8c9f658ffef27c26f2e1c068129c7ae6971af))
* verify Flutter lock file and pin sonar-scan workflow SHA ([976297f](https://github.com/maiwei-app/workflows/commit/976297fd4b8b925c9c1d79f70ebddd23b1a47732))
