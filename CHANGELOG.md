# Changelog

What changed, newest first, in pig's format: `## [x.y.z] - YYYY-MM-DD`, then only the sections that
have entries (`### New Features`, `### Added`, `### Changed`, `### Fixed`). Notes under
`## Unreleased` belong to no version yet; the version itself lives in the git tag.

## [0.1.0] - 2026-11-02

### New Features

- Web search as its own package — The extension that was bundled with pig as `extensions/pig-web-search` is now this package, installed with `pig install git:github.com/owner888/pig-web-search`. Tools and command are the ones pig shipped; `HeadlessBrowser` stays `PigWebSearch\HeadlessBrowser`, now under `src/`, and the extension is still named `pig-web-search`, so `disabledExtensions` keeps working.
