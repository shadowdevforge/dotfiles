
<div align="center">
  <img width="1600" height="900" alt="ShadowDevForge Dotfiles Cockpit" src="https://github.com/user-attachments/assets/4633eed3-76ba-4ec5-b960-76bc28a3d498" />
</div>

<div align="center">

**A fiercely forged configuration for Zsh, Tmux, Neovim, and the modern command line.**

</div>

This repository contains the soul of my development environment. It is not a framework, but a living system of configurations meticulously crafted for performance, aesthetic harmony, and ergonomic efficiency. It is the blueprint for my personal "flow state."

This setup is built on the Arch Linux philosophy of control, minimalism, and user-centric design, using modern, community-standard tools.

---

### Philosophy

*   **Flow State:** The environment must be an invisible extension of thought. Navigation between `tmux` panes and `nvim` splits is seamless. The shell predicts my needs.
*   **Aesthetic Harmony:** The entire terminal experience shares a cohesive, beautiful, and soothing visual language (Catppuccin Mocha). A calm environment breeds clear thought.
*   **Ergonomics First:** Common actions require the fewest keystrokes, achieved through intelligent keymaps and prefix-less navigation.
*   **Informative, Not Loud:** The UI provides all necessary context at a glance—Git status, system time, current directory—without ever being cluttered.

---

## 🚀 Replicating the Forge (Installation)

This guide will help you replicate this environment on a fresh, minimal Arch Linux system (like one built by my [ArchBTW Forge](https://github.com/shadowdevforge/archbtw)).

### Step 1: Prerequisites

Before you begin, ensure your system has the following installed and configured.

1.  **A Linux System:** Works on WSL 2 or bare metal Arch Linux.
2.  **Essential Tools:** `git`, `zsh`, `tmux`, `neovim`, `fastfetch` must be installed.
    ```bash
    # On Arch, you can install them with:
    sudo pacman -S git zsh tmux neovim fastfetch
    ```
3.  **A Nerd Font:** A font with patched-in icons is **essential** for the UI to render correctly. [FiraCode Nerd Font](https://www.nerdfonts.com/font-downloads) is recommended. Install it on your host system and set it as your terminal's font.
4.  **TPM (Tmux Plugin Manager):** Required to manage `tmux` plugins.
    ```bash
    git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
    ```
5.  **Essential Zsh Plugins:** These provide IDE-like syntax highlighting and auto-completion in your terminal.
    ```bash
    # Clone the plugins into the Oh My Zsh custom plugins directory
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```

### Step 2: Deploy the Dotfiles

This single command will download and place all configuration files into their correct locations. It will back up your existing Neovim config to `~/.config/nvim.bak`.

```bash
# This command fetches the core configuration files.
curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.zshrc -o ~/.zshrc
curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.p10k.zsh -o ~/.p10k.zsh
curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.tmux.conf -o ~/.tmux.conf

# This command sets up the fastfetch and Neovim (NvShade) configurations.
mkdir -p ~/.config/fastfetch
curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/fastfetch.jsonc -o ~/.config/fastfetch/config.jsonc
mv ~/.config/nvim ~/.config/nvim.bak 2>/dev/null || true
git clone https://github.com/shadowdevforge/NvShade.git ~/.config/nvim

```

### Step 3: Finalization

1.  **Launch `tmux` and Install Plugins:**
    *   Open a new terminal and run `tmux`.
    *   Press **`Ctrl`** + **`s`**, then **`Shift`** + **`I`** (capital I). This will trigger TPM to install all the plugins listed in `.tmux.conf`.

2.  **Launch `nvim` and Install Plugins:**
    *   Inside or outside of tmux, run `nvim`.
    *   `lazy.nvim` will automatically start and install all the plugins for NvShade. This may take a minute.

3.  **Restart Your Shell:**
    *   Close and reopen your terminal. Your entire personalized environment is now perfectly restored.

---

## ⚙️ Key Components & Configuration

This environment is composed of several key configuration files that work in harmony.

| File | Component | Role & Purpose |
| :--- | :--- | :--- |
| **`~/.zshrc`** | Zsh Shell | Configures the shell via `Oh My Zsh`, loads `Powerlevel10k`, sets aliases, and manages the startup sequence. |
| **`~/.p10k.zsh`** | Prompt Theme | The generated configuration for the Powerlevel10k prompt. All visual customization for the prompt lives here. (Run `p10k configure` to change it). |
| **`~/.tmux.conf`**| Terminal Multiplexer | Configures the `tmux` cockpit, defining keybindings, plugins (via TPM), and the status bar theme. |
| **`~/.config/fastfetch/config.jsonc`** | System Info | The JSON configuration that customizes the look, feel, and content of the `fastfetch` startup screen. |
| **`~/.config/nvim/`** | Code Editor | The complete [NvShade](https://github.com/shadowdevforge/NvShade) Neovim distribution, providing a full IDE experience. |

---

## ⌨️ `tmux` Keymaps: The Cockpit Controls

My `tmux` configuration is designed for a fast, ergonomic, and Vim-centric workflow. The prefix key is **`Ctrl + s`**.

#### Core Session & Window Management

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl`** + **`s`**, then **`r`** | Reload Config | Instantly reloads the `.tmux.conf` file to apply changes. |
| **`Ctrl`** + **`s`**, then **`d`** | Detach Session | Detaches from the current session, leaving it running in the background. |
| **`Ctrl`** + **`s`**, then **`c`** | New Window | Creates a new window (tab) in the current session. |
| **`Shift`** + **`←`** | Previous Window | **(No Prefix)** Switches to the previous window. |
| **`Shift`** + **`→`** | Next Window | **(No Prefix)** Switches to the next window. |
| **`Alt`** + **`h`** | Previous Window | **(No Prefix)** An alternative, Vim-style way to switch to the previous window. |
| **`Alt`** + **`l`** | Next Window | **(No Prefix)** An alternative, Vim-style way to switch to the next window. |

#### Pane Creation & Navigation

These bindings enable seamless, prefix-less navigation between `tmux` panes and `nvim` splits.

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl`** + **`s`**, then **`%`** | Split Vertically | Splits the current pane into a left and a right pane. |
| **`Ctrl`** + **`s`**, then **`"`** | Split Horizontally | Splits the current pane into a top and a bottom pane. |
| **`Alt`** + **`h`** / **`←`** | Select Left Pane | **(No Prefix)** Moves the cursor to the pane on the left. |
| **`Alt`** + **`j`** / **`↓`** | Select Down Pane | **(No Prefix)** Moves the cursor to the pane below. |
| **`Alt`** + **`k`** / **`↑`** | Select Up Pane | **(No Prefix)** Moves the cursor to the pane above. |
| **`Alt`** + **`l`** / **`→`** | Select Right Pane | **(No Prefix)** Moves the cursor to the pane on the right. |

#### Copy Mode (Vim Style)

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl`** + **`s`**, then **`[`** | Enter Copy Mode | Enters scrollback/copy mode. |
| `v` | Begin Selection | (Inside Copy Mode) Starts a character-wise selection. |
| `Ctrl`+`v`| Begin Block Selection | (Inside Copy Mode) Starts a rectangular/block selection. |
| `y` | Yank (Copy) | (Inside Copy Mode) Copies the selected text and exits copy mode. |

#### TPM (Plugin Manager)

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl`** + **`s`**, then **`Shift`**+**`I`** | Install Plugins | Installs any new plugins listed in your `.tmux.conf`. |
| **`Ctrl`** + **`s`**, then **`Shift`**+**`U`** | Update Plugins | Updates all installed plugins to their latest versions. |

---

<div align="center">

*This configuration was fiercely forged.*

</div>
