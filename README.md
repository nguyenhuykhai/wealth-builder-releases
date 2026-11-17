# Wealth Builder

An AI-powered desktop research workspace for Vietnamese stocks.

Wealth Builder brings AI conversations, stock reports, a watchlist, market news, and your investment profile into one application. Its interface and research workflows are designed for Vietnamese-speaking investors.

[Download releases](https://github.com/nguyenhuykhai/wealth-builder-releases/releases) · [Installation guide](installation.md) · [Report an issue](https://github.com/nguyenhuykhai/wealth-builder-releases/issues)

## Release status

Wealth Builder is in early testing. Desktop packages have been built in CI for Linux x64, Windows x64, and macOS Apple Silicon. Installation and everyday use on clean machines are still being verified, particularly on Windows and macOS.

There are no published releases in this repository yet. Download links will appear on the Releases page when the first testing version is published. Each release's notes will describe its available installers and known issues.

## What you can do

- **Research through AI chat:** use Claude Code, Codex CLI, or Antigravity CLI, with streaming responses and saved conversations.
- **Organize stock reports:** browse Markdown reports, filter by sector or rating, and restore saved report versions.
- **Maintain a watchlist:** record the stocks you follow and your preferred buy zones.
- **Read market news:** browse daily news saved in your workspace.
- **Keep an investment profile:** manage your goals, risk appetite, investment principles, and watchlist from the app.
- **Keep a local research workspace:** reports and news are Markdown files; conversations are stored in a local database.

## Before you start

You need an internet connection and at least one supported AI CLI installed and signed in on your computer. AI access uses your own provider account and is subject to that provider's availability, usage limits, and pricing. The desktop installer does not include an AI subscription or install the CLI for you.

The app bundles its Python backend, so you do not need to install Python or clone the development repository. A CLI may have its own runtime requirements.

**Live prices are not included in the current desktop package.** The price-data integration is still being completed. You can maintain watchlist entries, read reports, and use AI chat, but automatic price checks, price charts, and data-driven report initialization need a working compatible data source. Installing a Python package separately does not currently connect it to the packaged app.

## Choose a download

| Your computer | Installer |
| :--- | :--- |
| Windows x64 | `.exe` or `.msi` — install one |
| Fedora / RPM-based Linux x64 | `.rpm` |
| Ubuntu / Debian-based Linux x64 | `.deb` |
| macOS on Apple Silicon | `.dmg` |

Intel Mac and ARM Linux/Windows packages are not currently built. Compatibility with a particular OS release is still being verified; check the release notes before installing.

Open the [Releases page](https://github.com/nguyenhuykhai/wealth-builder-releases/releases), select a testing version, and expand **Assets** to download your installer. The automatically generated **Source code** archives contain this repository's public documentation, not the application installer.

Follow the [installation and first-run guide](installation.md) to set up your AI CLI, install the app, and create your investor profile.

## Current limitations

- Windows installers are built and the packaged backend passes a startup check, but the full Python test suite is not yet enabled on Windows.
- Windows installers are not code-signed, and macOS builds are not Developer ID signed or notarized.
- Automatic updates are not implemented yet; download and install newer versions manually.
- Run only one instance of Wealth Builder at a time.
- Some external links inside the desktop app do not open yet; copy the URL into your browser.
- AI-generated research can contain errors. Verify figures, dates, and sources before using the results to make investment decisions.

## Your data

Your reports, profile, settings, backups, and chat history are stored on your computer, outside the installation folder. See [data storage and backups](installation.md#data-storage-and-backups) for the locations.

Local storage does not mean offline AI processing: your selected CLI can send prompts and workspace content it reads to its AI provider. Provider CLIs may also keep their own local history outside Wealth Builder's data folder. Review your provider's data settings before sharing sensitive information.

## Feedback

Use [Issues](https://github.com/nguyenhuykhai/wealth-builder-releases/issues) to report a problem or suggest an improvement. Include your app version, OS and architecture, selected AI CLI, steps to reproduce, and the error message. Remove personal investment details, account information, and credentials from screenshots and logs.

This repository hosts public documentation and downloadable releases. The application development source is maintained separately in a private repository.
