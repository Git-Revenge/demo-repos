# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/2.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html), for what the scripts build: see [Versions](README.md#versions).

## [Unreleased]

### Added

- **Breaking:** what lands on `main` in the generated history carries two trailers: `Changelog`, a label that says what kind of change it is (`added`, `fixed`, `changed` or `none`), and `Reviewed-by`, the person who merged it. That's 338 commits. Eleven of them misspell the key as `Reviewd-by`, and seven name Jessica as `Jess Nguyen` at her usual address, so the history has a key written two ways and one person under two names. Every commit, branch, tag, subject, author and date is as it was; the messages are longer, so the commits have new IDs.
- **Breaking:** nine of the commits made by hand on `main` in the last few weeks carry `Changelog` too, and eight of them `Reviewed-by`, so the newest history shows them as the generated history does. Their subjects are as they were.

## [2.0.0] - 2026-11-21

### Added

- One person under two addresses, for a mailmap to join: Jessica Nguyen fixes a gauge from her own laptop as `jessica.nguyen@harbourmail.example`, in two commits on `fix/gull-point-gauge-drift`, a branch only the remote has. They're dated late September 2026, before the hand-written weeks, so the top of the graph is as it was. Tidewater has no `.mailmap`; Git Revenge's walkthrough makes one. (Git-Revenge/GitRevenge#840)

### Fixed

- **Breaking:** a `Co-authored-by` trailer in the generated history names one person. Most of them paired one person's name with another's address, such as `Emily Carter <david@tidewater.example>`, so anything that counts people by their trailers saw the same name under several addresses. Every commit's author, date and subject, every branch and tag name and every file are as they were; the trailers' addresses change, and with them the ID of almost every commit.

## [1.0.0] - 2026-11-16

The first release, moved here from Git Revenge's `docs-site/scripts` (Git-Revenge/GitRevenge#730, Git-Revenge/GitRevenge#736).

### Added

- `demo-repo.sh` builds Tidewater, about 1,500 commits by a team of six over almost two years:
  - January 2025 to September 2026 generated with `git fast-import`: pull requests merged and squashed, releases v0.1.0 to v1.7.0 with release branches and patch releases, reverts, dependency bumps, and the branches a team leaves behind (stale, merged and never deleted, a stack of three, remote-only);
  - the last few weeks by hand, for Git Revenge's walkthroughs and screenshots: releases v1.8.0 and v1.9.0, a branch to tidy with interactive rebase, a branch that conflicts with `main`, a bug for bisect, a stash, uncommitted changes, a linked worktree, a gone upstream, and a file for each rendered preview;
  - its remote, two sibling projects and a made-up global git config.
- `demo-repo.sh --git3` and `demo-repo-git3.sh` build the same history as `tidewater-git3`, the way Git 3.0 makes a new repository: SHA-256 object IDs and reftable refs, with `safe.bareRepository=explicit`. Needs git 2.45 or later.
- `demo-repo.sh --version`.
- Every build is the same: gawk, mawk and macOS's awk, bash 3.2 and later, on Linux, macOS and Windows all make identical commits, and CI checks it.

[Unreleased]: https://github.com/Git-Revenge/demo-repos/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/Git-Revenge/demo-repos/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/Git-Revenge/demo-repos/releases/tag/v1.0.0
