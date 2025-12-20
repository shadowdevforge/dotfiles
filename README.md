<div align="center">
  <img width="1600" height="900" alt="ShadowDevForge Dotfiles Cockpit" src="https://github.com/user-attachments/assets/8dab271d-a962-4552-beaf-02c62b3ab50f" />
</div>

<div align="center">

# ShadowDevForge Dotfiles

**My personal configuration laboratory.**

</div>

---

### ⚠️ Disclaimer
**This is not a distribution. This is my personal setup.**
It works perfectly on my machine (Arch Linux + Hyprland). It might break yours. Feel free to copy, fork, or steal code, but expect to tweak things to fit your needs.

---

### 🛠️ The Stack

I run a vertically integrated environment where every tool follows the same keybindings and **Catppuccin Mocha** aesthetic.

| Component | Tool | Notes |
| :--- | :--- | :--- |
| **Multiplexer** | **Zellij** | Configured to emulate **Tmux**. Uses `Ctrl+s` prefix. |
| **Shell** | **Fish** | Fast, autosuggestions, powered by `Tide` prompt. |
| **Editor** | **Neovim** | my custom [shadowforge.nvim](https://github.com/shadowdevforge/shadowforge.nvim) config. |
| **Terminal** | **Ghostty** | GPU-accelerated, supports true color & ligatures. |
| **OS** | **Arch Linux** | my custom [CelestialShade-Config](https://github.com/shadowdevforge/CelestialShade-Config) config. |

---

### ⚡ Key Workflows

#### 1. Zellij as Tmux
I switched to Zellij for the rendering performance, but I kept my Tmux muscle memory.
*   **Prefix:** `Ctrl + s`
*   **Splits:** `"` (Horizontal) and `%` (Vertical).
*   **Navigation:** `h` `j` `k` `l` to move between panes.
*   **Tabs:** `1` through `9` to switch tabs (windows).

*Note: Zellij auto-starts when I open a terminal (unless I'm in VS Code which never happens i use Neovim).*

#### 2. CodePacker Script
Included in `.bin/codepacker.py`.
This is a custom Python script I use to dump entire codebases into a single Markdown file.
*   **Usage:** `python ~/.bin/codepacker.py`
*   **Why?** It makes it incredibly easy to feed context to LLMs (ChatGPT/Claude) for code review or learning.

---

---

<div align="center">
  <code>Forged by ShadowDevForge</code>
</div>
