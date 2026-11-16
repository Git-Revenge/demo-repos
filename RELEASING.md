# Releasing

A release is a tag. Pushing an annotated `vX.Y.Z` tag runs [`release.yml`](.github/workflows/release.yml), which builds both Tidewaters once more and publishes the GitHub release.

## Every pull request

Add a line under `## [Unreleased]` in [CHANGELOG.md](CHANGELOG.md), under the type it is ([Keep a Changelog 2.0.0](https://keepachangelog.com/en/2.0.0/)):

- **Added** for something new in what's built;
- **Changed** for something that's built differently;
- **Removed**;
- **Fixed** for a bug, such as a platform that built different commits.

Mark a change that needs a major version with **Breaking:** at the start of its line. [Versions](README.md#versions) says which changes do. CI-only and README-only changes don't get a line.

## Cutting a release

1. Pick the version from the Unreleased lines and [the rules](README.md#versions).
2. In a pull request:
   - set `version=` near the top of `demo-repo.sh`;
   - rename `## [Unreleased]` to `## [X.Y.Z] - YYYY-MM-DD` (the day you'll tag) and add a fresh, empty `## [Unreleased]` above it;
   - update the links at the bottom: `[Unreleased]` compares `vX.Y.Z...HEAD`, and `[X.Y.Z]` compares the previous release with `vX.Y.Z`.

   CI fails if the script's version and the newest changelog section disagree.
3. Once that's merged and CI is green on `main`, tag the merge commit. The tag must be **annotated from the first push**, because releases are immutable: a published release's tag can't be moved or deleted.

   ```sh
   git tag -a vX.Y.Z -m "vX.Y.Z"
   git push origin vX.Y.Z
   ```

The workflow then:

1. checks that the tag, `demo-repo.sh --version` and the changelog agree;
2. builds Tidewater and its Git 3.0 version;
3. publishes the release with that version's changelog section as its notes, and attaches `demo-repo.sh`, `demo-repo-git3.sh` and `SHA256SUMS`.

## After a release

Git Revenge pins a release in `docs-site/scripts/screenshots.mjs` (`DEMO_REPOS_TAG`). If the release changes what the screenshots or walkthroughs show, move the pin in a Git Revenge pull request, update the walkthroughs, and retake the pictures.
