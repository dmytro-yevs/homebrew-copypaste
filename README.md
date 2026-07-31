# homebrew-copypaste

Homebrew tap for [CopyPaste](https://github.com/dmytro-yevs/copypaste) — an
encrypted clipboard manager with local history and peer sync.

## Install

```sh
brew tap dmytro-yevs/copypaste
brew install --cask copypaste     # the app
brew install copypaste-cli        # the command-line client and the daemon
```

The daemon does not fork, so launchd runs it:

```sh
brew services start copypaste-cli
```

The app and the CLI are separate on purpose: one is an `.app` bundle, the other
a pair of binaries. Either works without the other.

## Upgrade

```sh
brew update
brew upgrade --cask copypaste
brew upgrade copypaste-cli
```

## Uninstall

```sh
brew services stop copypaste-cli
brew uninstall --cask copypaste
brew uninstall copypaste-cli
brew untap dmytro-yevs/copypaste
```

`brew uninstall` leaves the signing certificate in your keychain, which is what
lets a later reinstall keep the permissions you granted. `brew zap --cask
copypaste` removes it along with the app's data.

## How updates land here

`.github/workflows/sync.yml` copies `Casks/copypaste.rb` and
`Formula/copypaste-cli.rb` out of the newest release of the main repository,
hourly and on demand from the Actions tab.

It reads the **release assets**, not the main repository's branch: the checked-in
cask is a template carrying version `0.0.0` and an all-zero `sha256`, so that an
unreleased copy cannot install anything. The sync refuses to publish a file
still in that state.

## Notes

- Apple Silicon and macOS Sonoma or newer. The release builds a single arm64
  slice, not a universal binary.
- **Not notarised** — the project has no Apple Developer ID. On install the cask
  removes the quarantine attribute from its own bundle and re-signs it with a
  certificate generated on your machine, which never leaves it. That certificate
  is what makes macOS treat an update as the same app and keep your grants.
- **v2 does not read v0.4.x data.** Upgrading from 0.4 loses the clipboard
  history and the paired devices. The old files are left on disk untouched.

## License

The tap is provided as-is. CopyPaste is licensed under its upstream terms.
