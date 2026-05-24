# homebrew-copypaste

Homebrew tap for [CopyPaste](https://github.com/dmytro-yevs/CopyPaste) — an
encrypted clipboard manager with end-to-end sync.

## Install

```sh
brew tap dmytro-yevs/copypaste
brew install dmytro-yevs/copypaste/copypaste
```

Or in a single command:

```sh
brew install dmytro-yevs/copypaste/copypaste
```

## Upgrade

```sh
brew update
brew upgrade dmytro-yevs/copypaste/copypaste
```

## Uninstall

```sh
brew uninstall dmytro-yevs/copypaste/copypaste
brew untap dmytro-yevs/copypaste
```

## How updates land here

This tap is updated automatically by a GitHub Actions workflow
(`.github/workflows/sync.yml`) that watches for new release tags
on the upstream [CopyPaste](https://github.com/dmytro-yevs/CopyPaste)
repository and bumps `Casks/copypaste.rb` (`version` + `sha256`)
accordingly. Each bump opens a commit on `main`.

To trigger a sync manually, dispatch the workflow from the Actions tab.

## Notes

- CopyPaste is **ad-hoc signed** (no Apple Developer ID). The cask
  strips the quarantine attribute on install, so Gatekeeper will not
  warn. See the cask's `caveats` block for details.
- Requires macOS Sonoma or newer.
- The daemon installs as a LaunchAgent under your user.

## License

This tap repository is provided as-is. CopyPaste itself is licensed
under its upstream terms (see the main repository).
