# Changelog

## [1.4.0](https://github.com/maiwei-app/workflows/compare/v1.3.0...v1.4.0) (2026-09-02)


### Features

* **ci:** prepare the policy checks to run at organization level ([#61](https://github.com/maiwei-app/workflows/issues/61)) ([08a0ec6](https://github.com/maiwei-app/workflows/commit/08a0ec672933bd75b04f16f01e429e548d0aece9))

## [1.3.0](https://github.com/maiwei-app/workflows/compare/v1.2.1...v1.3.0) (2026-08-31)


### Features

* pass python coverage to sonar ([#57](https://github.com/maiwei-app/workflows/issues/57)) ([66b7145](https://github.com/maiwei-app/workflows/commit/66b714515f1705dd175d2c0ea2e96edb4cf54d21))

## [1.2.1](https://github.com/maiwei-app/workflows/compare/v1.2.0...v1.2.1) (2026-08-24)


### Bug Fixes

* exempt dependabot[bot] from the AI-authorship check ([#50](https://github.com/maiwei-app/workflows/issues/50)) ([8861be1](https://github.com/maiwei-app/workflows/commit/8861be1d6825a39b68a1195d17c757ff8d192776))

## [1.2.0](https://github.com/maiwei-app/workflows/compare/v1.1.0...v1.2.0) (2026-08-24)


### Features

* add theme mode to ci-hugo.yml ([#48](https://github.com/maiwei-app/workflows/issues/48)) ([8561a08](https://github.com/maiwei-app/workflows/commit/8561a08d4a03fb08e8f2d04125dc6c0ec7a53609))

## [1.1.0](https://github.com/maiwei-app/workflows/compare/v1.0.9...v1.1.0) (2026-08-20)


### Features

* add lint-frontend, lint-toml and lint-yaml reusable workflows ([#45](https://github.com/maiwei-app/workflows/issues/45)) ([9dd7e3b](https://github.com/maiwei-app/workflows/commit/9dd7e3bf910dfa3f5f3bfb050909d89088e2837f))

## [1.0.9](https://github.com/maiwei-app/workflows/compare/v1.0.8...v1.0.9) (2026-08-17)


### Bug Fixes

* drop redundant leading separator from PR footer ([#43](https://github.com/maiwei-app/workflows/issues/43)) ([c6978cc](https://github.com/maiwei-app/workflows/commit/c6978ccaf297caaa1468edfd24f1eda0fb9cb2d4))

## [1.0.8](https://github.com/maiwei-app/workflows/compare/v1.0.7...v1.0.8) (2026-08-17)


### Bug Fixes

* remove release-type input to let action read config file ([#40](https://github.com/maiwei-app/workflows/issues/40)) ([a416b5d](https://github.com/maiwei-app/workflows/commit/a416b5da2a061d7c42e0208eaf13d825886046fd))
* restore packages block, now required by fromManifest path ([#41](https://github.com/maiwei-app/workflows/issues/41)) ([9765fb6](https://github.com/maiwei-app/workflows/commit/9765fb60da5a7a3819f9757506984f39531e5cf5))

## [1.0.7](https://github.com/maiwei-app/workflows/compare/v1.0.6...v1.0.7) (2026-08-17)


### Bug Fixes

* document release-please PR header/footer config ([#38](https://github.com/maiwei-app/workflows/issues/38)) ([c44041a](https://github.com/maiwei-app/workflows/commit/c44041a9b3fe5f4270ffefd6189fa3f4e3742340))
* flatten release-please config, drop packages nesting ([#36](https://github.com/maiwei-app/workflows/issues/36)) ([5c1bf4b](https://github.com/maiwei-app/workflows/commit/5c1bf4b9a726b2bbcf44af148456f91728f7fbeb))

## [1.0.6](https://github.com/maiwei-app/workflows/compare/v1.0.5...v1.0.6) (2026-08-17)


### Bug Fixes

* move release-please header/footer to config file ([#34](https://github.com/maiwei-app/workflows/issues/34)) ([3cbc8b5](https://github.com/maiwei-app/workflows/commit/3cbc8b5b73f337644921198ac25de8ff34f4a225))

## [1.0.5](https://github.com/maiwei-app/workflows/compare/v1.0.4...v1.0.5) (2026-08-17)


### Bug Fixes

* customize release-please PR header/footer ([#32](https://github.com/maiwei-app/workflows/issues/32)) ([c71b567](https://github.com/maiwei-app/workflows/commit/c71b56722890daff9e9ea10b94cb00bd0afe4f2d))

## [1.0.4](https://github.com/maiwei-app/workflows/compare/v1.0.3...v1.0.4) (2026-08-15)


### Bug Fixes

* use single-space footer to work around release-please empty-string bug ([#29](https://github.com/maiwei-app/workflows/issues/29)) ([b099017](https://github.com/maiwei-app/workflows/commit/b09901795dae9549447802f25ca7a9a662c903ac))


### Reverts

* restore repo state to 7aee6e4 (before release-please PR customization) ([#31](https://github.com/maiwei-app/workflows/issues/31)) ([f4b5dae](https://github.com/maiwei-app/workflows/commit/f4b5dae42908b80896f15cd0a8f83fd77b73a851))

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
