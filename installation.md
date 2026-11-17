# Installation and first run

[Back to the overview](README.md) · [Download releases](https://github.com/nguyenhuykhai/wealth-builder-releases/releases)

These instructions describe the desktop testing builds. Published release notes take precedence for version-specific requirements and known issues. No public installer has been published in this repository yet.

## 1. Set up an AI CLI

Install and sign in to at least one of these tools using its official instructions:

| Provider CLI | Official instructions | Command to open it |
| :--- | :--- | :--- |
| Claude Code | [Setup and authentication](https://code.claude.com/docs/en/setup) | `claude` |
| Codex CLI | [Installation and sign-in](https://developers.openai.com/codex/cli/) | `codex` |
| Antigravity CLI | [CLI documentation](https://antigravity.google/docs/cli/reference) | `agy` |

Run the CLI in a terminal, complete its sign-in process, and confirm that it can answer a short prompt. Use the same OS user account that will run Wealth Builder. On Windows, a CLI installed only inside WSL may not be discoverable by the native desktop app; use a native installation supported by the provider.

Wealth Builder uses your existing CLI account. You do not enter provider credentials into the app. Account eligibility, subscriptions, and usage charges depend on your selected provider. Install any runtime the provider requires according to its documentation.

## 2. Download the right installer

Go to [Releases](https://github.com/nguyenhuykhai/wealth-builder-releases/releases), read the release notes, and expand **Assets**. Choose the installer matching your OS and processor. Versions marked **Pre-release** are testing builds.

Download only one installer format for your OS. Do not download **Source code (zip)** or **Source code (tar.gz)** to install the application.

## 3. Install Wealth Builder

### Windows x64

1. Download the `.exe` installer, or use `.msi` if you prefer Windows Installer.
2. Open it and follow the installation prompts.
3. Launch **Wealth Builder** from the Start menu.

Current Windows builds are unsigned, so Windows may show a publisher or SmartScreen warning. Check that the file came from this repository's Releases page. Windows compatibility testing is still in progress; a successful CI build does not establish that every feature works on Windows.

The desktop interface uses Microsoft Edge WebView2. If installation reports that it is missing, follow the installer's prompt or obtain it from [Microsoft's WebView2 download page](https://developer.microsoft.com/en-us/microsoft-edge/webview2/).

### macOS — Apple Silicon

1. Download the `.dmg` for Apple Silicon (`arm64` / `aarch64`). Intel Mac packages are not currently available.
2. Open the disk image and drag **Wealth Builder** to **Applications**.
3. Open the app from **Applications**.

Current macOS builds are not Developer ID signed or notarized. If macOS blocks the first launch, check the download's origin and follow [Apple's guidance for opening apps](https://support.apple.com/en-us/102445). Do not disable Gatekeeper system-wide. Installation on a clean Mac has not yet been verified.

### Fedora / RPM-based Linux x64

Download the `.rpm` and open it with your distribution's software installer. On Fedora, you can also install it from the terminal:

```bash
sudo dnf install ./<downloaded-installer>.rpm
```

Replace `<downloaded-installer>` with the actual filename. Launch **Wealth Builder** from the application menu.

### Ubuntu / Debian-based Linux x64

Download the `.deb` and open it with your distribution's software installer. You can also use:

```bash
sudo apt install ./<downloaded-installer>.deb
```

Replace `<downloaded-installer>` with the actual filename. Launch **Wealth Builder** from the application menu. Package-manager installation allows declared system dependencies to be resolved; compatibility with individual distribution versions is still being verified. AppImage packages are not currently provided.

## 4. Complete the first run

1. Open **Wealth Builder** and wait for the app to finish starting.
2. Open **Cài đặt** (Settings). Confirm that your chosen AI CLI is detected and signed in. If you installed or signed in to a CLI while the app was open, restart Wealth Builder.
3. Open **Hồ sơ** (Profile). Create your investor profile, add your investment principles, and enter your watchlist. This information gives the research agent context for your requests.
4. Open **Trò chuyện** (Chat), start a new conversation, and select an available agent in the message composer.
5. Send a short prompt to confirm the connection, then start your research.

For example:

> Hãy giúp tôi lập danh sách thông tin cần kiểm tra trước khi phân tích cổ phiếu FPT. Nêu rõ nguồn cần tra cứu và những dữ liệu còn thiếu.

Your first workspace starts without personal reports or news. Reports and news appear after they are created or added to the workspace. Live-price features require a compatible data source that is not currently included in the desktop package.

## Data storage and backups

The default data folder depends on your OS:

| OS | Default location |
| :--- | :--- |
| Windows | `%APPDATA%\wealth-builder` |
| macOS | `~/Library/Application Support/wealth-builder` |
| Linux | `~/.local/share/wealth-builder` (or `$XDG_DATA_HOME/wealth-builder`) |

The folder contains `stocks/` for reports, `daily-news/` for news, `core-knowledge/user-memory.md` for your profile, and `.app-data/` for chat history, settings, and backups. A custom `WEALTH_BUILDER_DATA_DIR` environment variable overrides the default location.

To make a complete backup, close Wealth Builder and copy the entire data folder, including the hidden `.app-data/` directory. Report versions can be restored from the report page. Profile backups are stored under `.app-data/backups/user-memory/`; restoring them currently requires manually copying a backup into place with the app closed.

## Updating

Automatic updates are not available yet. Close the app, back up your data folder, then download and install the newer version for the same OS and architecture. Data is stored outside the installation folder. Check release notes for any migration instructions before updating or downgrading.

## Troubleshooting

| Problem | What to check |
| :--- | :--- |
| No installers on the Releases page | No public version has been published yet. CI artifacts from the development repository are not public releases. |
| Agent is unavailable | Run its CLI directly, complete sign-in, and restart Wealth Builder. Check **Cài đặt** for its detected path and status. |
| The app stays on its startup screen | Wait up to 90 seconds. If an error appears, record it and report your app version and OS. |
| Chat fails or stops | Confirm the CLI works directly and check the provider's connection, account access, and usage limits. |
| Watchlist prices or charts are missing | The current desktop package has no bundled price-data provider. Installing Vnstock in a separate Python environment does not connect it to the packaged app. |
| External links do not open | Copy the URL and open it in your browser. |
| Two app windows are running | Close both, then start one instance. Multiple-instance protection is not implemented yet. |

If the problem persists, [open an issue](https://github.com/nguyenhuykhai/wealth-builder-releases/issues). Include your app version, OS and architecture, selected CLI and its version, reproduction steps, and the exact error. Remove account information and personal research data before sharing logs or screenshots.
