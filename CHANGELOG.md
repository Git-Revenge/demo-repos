# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/2.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html), for what the scripts build: see [Versions](README.md#versions).

## [Unreleased]

### Added

- `feature/station-checks`, for a diff that reads the code to show from one language to the next. It holds 15 commits by all six people, dated 21 September to 2 October 2026:
  - a nightly check of every station: a Python script, an SQL table, a shell script and a PowerShell one, a GitHub Actions workflow, a JSON file of limits, an HTML page with its CSS and JavaScript, a Markdown guide and a Dockerfile;
  - then one commit for each language that changes its file, with renames, code wrapped in new structure or moved, formatting, and a real change beside them.

  It's cut from the last generated commit on `main` and dated before the last few weeks, so the top of the graph is as it was. (Git-Revenge/GitRevenge#941)
- `feature/reading-times`, three commits by Jessica cut from v1.9.0 and dated 17 and 18 October. Merged into `main`, it stops on conflicts in `src/feed.js` and `config.yaml`:
  - two places where the sides changed different parts of the same lines, which Git Revenge's conflict tool can combine;
  - one where both sides changed the wind alert's limit, `wind_knots: 32` on `main` and `wind_kmh: 55` on the branch, which someone has to settle.

  `feature/metric-units`'s conflict is as it was. (Git-Revenge/GitRevenge#946)

Every commit, branch and tag an earlier release built is unchanged.

### Fixed

- A build away from UTC dated the last few weeks by its own clock, so its commits had other IDs than a build in UTC, such as CI's and the docs'. Builds now come out the same in any time zone, and CI builds in three of them. A build in UTC is unchanged.

## [3.0.0] - 2026-11-22

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

[Unreleased]: https://github.com/Git-Revenge/demo-repos/compare/v3.0.0...HEAD
[3.0.0]: https://github.com/Git-Revenge/demo-repos/compare/v2.0.0...v3.0.0
[2.0.0]: https://github.com/Git-Revenge/demo-repos/compare/v1.0.0...v2.0.0
[1.0.0]: https://github.com/Git-Revenge/demo-repos/releases/tag/v1.0.0
