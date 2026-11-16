# Demo repositories for Git Revenge

Scripts that build **Tidewater**, the made-up repository that [Git Revenge](https://github.com/Git-Revenge/GitRevenge)'s documentation, walkthroughs and screenshots use. Tidewater is a dashboard for a network of coastal weather stations, built by a small team over almost two years. It's big enough to show every feature and put some load on the app, and it comes out the same every time.

## Build it

You need `git`, `bash` and `awk`. On Windows, use Git Bash, which comes with Git for Windows.

```sh
curl -fsSL https://raw.githubusercontent.com/Git-Revenge/demo-repos/main/demo-repo.sh -o demo-repo.sh
bash demo-repo.sh ~/gitrevenge-practice
```

That makes `~/gitrevenge-practice/tidewater` and the things around it, in under a minute:

- `tidewater`, the repository, with uncommitted changes and a stash;
- `origin.git`, its remote, one commit ahead of it;
- `tidewater-hotfix`, a linked worktree;
- `harbour-api` and `tide-tables`, two small sibling projects, for a group of repositories;
- `gitconfig`, `gitignore` and `work.gitconfig`, a made-up global config. Point `GIT_CONFIG_GLOBAL` at `gitconfig` to keep your own settings out of screenshots.

Each run deletes and rebuilds the folders it made, so run it again for a clean start. The repository sets its own author (Emily Carter) and never signs commits, so nothing you do in it uses your identity or keys.

### As Git 3.0 will make it

```sh
curl -fsSL https://raw.githubusercontent.com/Git-Revenge/demo-repos/main/demo-repo-git3.sh -o demo-repo-git3.sh
bash demo-repo-git3.sh ~/gitrevenge-practice
```

This builds the same history as `tidewater-git3`, `origin-git3.git` and so on, next to the other build. Every repository uses SHA-256 object IDs and reftable refs, the defaults [Git 3.0](https://git-scm.com/docs/BreakingChanges) plans for new repositories, and git refuses any bare repository it isn't pointed at. It needs git 2.45 or later and `demo-repo.sh` in the same folder.

## What's in it

**January 2025 to September 2026, generated.** An awk program at the end of `demo-repo.sh` writes the history as a `git fast-import` stream.

- **People:** six (Emily Carter, Marcus Johnson, Sarah Mitchell, Tyler Brooks, Jessica Nguyen, David Ramirez), plus a contractor who leaves in June and a dependency bot.
- **Pull requests:** about 450. Most are merged; some are squashed, and a few are reverted.
- **Trailers:** `Closes #n` and `Co-authored-by`.
- **Releases:** monthly from v0.1.0, then every eight weeks from v1.0.0 to v1.7.0, with `release/v1.x` branches and their patch releases.
- **Other changes:** weekly dependency bumps and monthly data archives.
- **Branches left behind:** in-progress work, stale branches, merged branches nobody deleted, open bot bumps, a stack of three (`feature/export-api` → `feature/export-csv` → `feature/export-ui`), and branches only the remote has.

**The last few weeks, written by hand,** for the walkthroughs:

- stations moved to a CSV file (v1.8.0);
- the station map and wind alerts (v1.9.0);
- a git note and trailers;
- a file for each rendered preview (CSV, GeoJSON, HTML, Mermaid, a Jupyter notebook);
- `feature/offline-cache`, work in progress with *fixup!* and *wip* commits, for interactive rebase;
- `feature/metric-units`, which conflicts with `main`;
- a bug after v1.9.0 for bisect to find;
- a branch whose upstream is gone.

In all, about 1,500 commits, 20 tags and 33 branches.

## Same every time

Dates, authors and the random choices are all fixed. The generator uses its own random numbers rather than awk's `rand()`, so gawk, mawk and macOS's awk make the same commits. CI builds on Linux (gawk and mawk), macOS (its own awk and bash 3.2) and Windows, then checks that every build has exactly the same commit IDs.

## Changing it

Git Revenge pins a tag of this repository, and its screenshot script builds Tidewater from that tag. So:

1. Change the scripts here in a pull request. CI must pass, including **Same everywhere**.
2. If the walkthroughs or screenshot scenes rely on something you changed, such as a commit subject, a branch name or a tag, update them in Git Revenge too.
3. Tag a release here (`v1.1.0` and so on, annotated), then move Git Revenge's pin to it and retake the screenshots.

## License

[Apache 2.0](LICENSE), like Git Revenge.
