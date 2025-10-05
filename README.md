
<div align="center">
<pre>
<img width="1600" height="900" alt="Screenshot 2025-09-26 223032" src="https://github.com/user-attachments/assets/118a7be7-97aa-4340-94d1-b14c2dd1eac4" />
</pre>
</div>

<div align="center">

**My personal digital cockpit. A fiercely forged configuration for Zsh, Tmux, fastfetch and Neovim.**

</div>

This repository contains the soul of my development environment. It is not a framework, but a living, breathing system of configurations that I have meticulously crafted for maximum performance, aesthetic pleasure, and ergonomic efficiency.

It is built on a foundation of modern, community-standard tools and a deep, uncompromising respect for the Arch Linux philosophy of control, minimalism, and customization.

---

*   **The Flow State:** The environment must be an invisible extension of my thoughts. Navigation between `tmux` panes and `nvim` splits must be seamless. The shell must predict my needs with intelligent auto-completion.
*   **Aesthetic Harmony:** The entire terminal experience, from the shell prompt to the editor, must share a cohesive, beautiful, and soothing visual language. A calm environment breeds clear thought.
*   **Ergonomics First:** The most common actions must require the fewest keystrokes. This is achieved through prefix-less `tmux` bindings and a mnemonic `nvim` leader key structure.
*   **Informative, Not Loud:** The UI should provide all necessary context at a glance—Git status, system time, current directory—without ever being cluttered or distracting.

---


## 🚀 **Replicating the Forge (Installation)**

This is the process to restore this environment on any fresh, minimal Arch Linux system (like one built by the [ArchBTW Forge](https://github.com/shadowdevforge/archbtw)).

### **1. Prerequisites**

*   A Linux system (WSL 2 or bare metal).
*   Essential tools installed: `git`, `zsh`, `tmux`, `neovim`, `fastfetch`.
*   A **Nerd Font** installed and enabled in your terminal (e.g., [FiraCode Nerd Font](https://www.nerdfonts.com/font-downloads)).
*   Tmux tpm installation `git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`

### **2. Application**

 **Clone the config:**
 

    curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.zshrc -o ~/.zshrc && curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.p10k.zsh -o ~/.p10k.zsh && curl -fsSL https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/.tmux.conf -o ~/.tmux.conf && curl https://raw.githubusercontent.com/shadowdevforge/dotfiles/main/fastfetch.jsonc >> ~/.config/fastfetch/config.jsonc && mv ~/.config/nvim ~/.config/nvim.bak && git clone https://github.com/shadowdevforge/NvShade.git ~/.config/nvim
    


### **3. Final Setup**

1.  **Install `tmux` plugins:**
    *   Launch `tmux`.
    *   Press **`Ctrl+s`** + **`Shift+I`** to have TPM install all the plugins.

2.  **Install `neovim` plugins:**
    *   Launch `nvim`.

Your entire personalized environment is now perfectly restored.

---

## ⚙️ **Key Components**

### **`~/.zshrc`**
*   **Shell Engine:** Configures the Zsh shell via `Oh My Zsh`.
*   **Theming:** Loads the `Powerlevel10k` theme.
*   **Startup Sequence:** Automatically launches `fastfetch` and attaches to a persistent `tmux` session on startup.

### **`~/.p10k.zsh`**
*   **The Prompt:** The generated configuration file for the Powerlevel10k prompt. All visual customization for the prompt lives here. To reconfigure, run `p10k configure`.

### **`~/.tmux.conf`**
*   **The Cockpit:** Configures the `tmux` terminal multiplexer.
*   **Keybindings:** Defines all ergonomic, prefix-less navigation keys.
*   **Plugins:** Manages the plugin ecosystem via `TPM`, including the custom `tmux-power` status line.

### **[NvShade](https://github.com/shadowdevforge/nvshade)**

- NvShade is a meticulously crafted Neovim configuration that emphasizes performance, clarity, and developer ergonomics. It is not a bloated framework, but a sharp, responsive tool that provides a complete IDE experience without sacrificing the speed and soul of Neovim.

---
Of course. A clear, well-structured keymap table is the most important part of the documentation for a tool like `tmux`. It transforms the configuration from a personal setup into a usable, shareable system that others can learn from.

Here is a clean, professional, Markdown-formatted table of the keymaps from your `tmux.conf`. This is designed to be dropped directly into your new `DotFiles` README.md.

---

### **`tmux` Keymaps**

My `tmux` configuration is designed for a fast, ergonomic, and Vim-centric workflow. The prefix key is **`Ctrl + s`**.

#### **Core Session & Window Management**

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl + s`** + **`r`** | Reload Config | Instantly reloads the `~/.tmux.conf` file to apply changes. |
| **`Ctrl + s`** + **`d`** | Detach Session | Detaches from the current session, leaving it running in the background. |
| **`Ctrl + s`** + **`c`** | New Window | Creates a new window in the current session. |
| **`Shift`** + **`←`** | Previous Window | **(No Prefix)** Switches to the previous window. |
| **`Shift`** + **`→`** | Next Window | **(No Prefix)** Switches to the next window. |
| **`Alt`** + **`H`** | Previous Window | **(No Prefix)** An alternative, Vim-style way to switch to the previous window. |
| **`Alt`** + **`L`** | Next Window | **(No Prefix)** An alternative, Vim-style way to switch to the next window. |

#### **Pane Creation & Navigation**

These keybindings are designed for seamless, prefix-less navigation between `tmux` panes and `nvim` splits, powered by the `vim-tmux-navigator` plugin.

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl + s`** + **`%`** | Split Vertically | Splits the current pane into a left and a right pane. |
| **`Ctrl + s`** + **`"`** | Split Horizontally | Splits the current pane into a top and a bottom pane. |
| **`Alt`** + **`←`** / **`h`** | Select Left Pane | **(No Prefix)** Moves the cursor to the pane on the left. |
| **`Alt`** + **`↓`** / **`j`** | Select Down Pane | **(No Prefix)** Moves the cursor to the pane below. |
| **`Alt`** + **`↑`** / **`k`** | Select Up Pane | **(No Prefix)** Moves the cursor to the pane above. |
| **`Alt`** + **`→`** / **`l`** | Select Right Pane | **(No Prefix)** Moves the cursor to the pane on the right. |

#### **Copy Mode (Vim Style)**

The copy/scroll mode is configured to use Vim keybindings.

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl + s`** + **`[`** | Enter Copy Mode | Enters scrollback/copy mode. |
| **`v`** | Begin Selection | (Inside Copy Mode) Starts a character-wise selection. |
| **`Ctrl + v`** | Begin Block Selection | (Inside Copy Mode) Starts a rectangular/block selection. |
| **`y`** | Yank (Copy) | (Inside Copy Mode) Copies the selected text to the clipboard and exits copy mode. |

#### **TPM (Plugin Manager)**

| Keybinding | Action | Description |
| :--- | :--- | :--- |
| **`Ctrl + s`** + **`Shift + I`** | Install Plugins | Installs any new plugins listed in your `.tmux.conf`. |
| **`Ctrl + s`** + **`Shift + U`** | Update Plugins | Updates all installed plugins to their latest versions. |


<div align="center">

*Configuration forged*

</div>
