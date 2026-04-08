# uxd-mac-set-up

Scripts for setting up a new Mac with Claude Code.

If you don't have a Claude.ai account, you'll need an Anthropic API key. Get one at [console.anthropic.com](https://console.anthropic.com/).


## Usage

1. Download this repository (Code > Download ZIP)
2. In your downloads folder, open the uxd-mac-set-up-main.zip file (it will create a folder)
3. Right-click the folder and choose "New Terminal at Folder" (if this option isn't visible, see Troubleshooting below)
4. Make the script executable:
   ```bash
   chmod +x 1-install
   ```
5. Run the script:
   ```bash
   ./1-install
   ```
6. Open a new terminal window and type `claude` — Claude Code will walk you through entering your API key and some initial setup questions.


## What gets installed

- [Homebrew](https://brew.sh/)
- Node, Yarn, GitHub CLI
- Claude (desktop app)
- Claude Code (CLI)
- VS Code and the Claude Code extension


## Extras

Optional but recommended steps.

### Markdown viewers

For viewing `.md` files outside of Claude Code:

- **MacDown3000** — standalone Markdown editor and previewer:
  ```bash
  brew install --cask macdown-3000
  ```
- **QLMarkdown** — Markdown Quick Look extension, lets you preview `.md` files in Finder with spacebar:
  ```bash
  brew install --cask qlmarkdown
  ```

### Show hidden files in Finder

Config files like `.zshrc` are hidden by default in Finder. To make them visible:

1. In Terminal, run:
   ```bash
   defaults write com.apple.finder AppleShowAllFiles YES
   ```
2. Hold Option, then right-click the Finder icon in the dock and choose Relaunch


## Prerequisites

- macOS

## Troubleshooting

- "New Terminal at Folder" doesn't appear in right-click menu: this option needs to be enabled or use the terminal directly
  - **Enable it:** go to System Settings > Privacy & Security > Extensions > Added Extensions and check Terminal under Finder extensions
  - **Or use Services:** right-click the folder and look under Services > New Terminal at Folder
  - **Or use the terminal directly:** open Terminal from Spotlight (Cmd+Space, type "Terminal"), then run:
    ```bash
    cd ~/Downloads/uxd-mac-set-up-main
    ```
- claude doesn't run: if after restarting the terminal the `claude` command isn't recognized, add it to your PATH. Pick one option:
  - **Terminal (easiest):** paste this into the terminal and press enter — it adds the PATH and reloads automatically:
    ```bash
    echo 'export PATH="$PATH:/opt/homebrew/bin/claude"' >> ~/.zshrc && source ~/.zshrc
    ```
  - **TextEdit:** run `open -e ~/.zshrc`, paste `export PATH="$PATH:/opt/homebrew/bin/claude"` at the bottom, save, then open a new terminal window or run `source ~/.zshrc`

## License

This script is provided "as is", without warranty of any kind.
