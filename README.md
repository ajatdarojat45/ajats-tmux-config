# Ajat's Tmux Config

## Table of Contents

-   [Preview](#preview)
-   [Getting Started](#getting-started)
-   [Usage](#usage)


## Preview

## Getting Started

### Installation

#### Install Tmux on your machine. 
You can follow this [link](https://github.com/tmux/tmux/wiki/Installing#installing-tmux) to install `Tmux`.
After that, to make sure it has been installed in your machine you can run this command

```
$ tmux -v
```

#### Install Tmux Plugin Manager
For install `Tmux Plugin Manager` you can run command bellow:

```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

#### Create Configuration File
Create `.tmux.config` file within root directory and put this code:

```
# Plugin Manager
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'christoomey/vim-tmux-navigator'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'tmux-plugins/tmux-yank'
set -g @plugin 'tmux-plugins/tmux-pain-control'
set -g @plugin 'dracula/tmux'

# Pane Switching Bindings
bind -n C-h select-pane -L
bind -n C-j select-pane -D
bind -n C-k select-pane -U
bind -n C-l select-pane -R

# Synchronize Panes
bind S setw synchronize-panes

# tmux
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# available plugins: battery, cpu-usage, git, gpu-usage, ram-usage, tmux-ram-usage, network, network-bandwidth, network-ping, ssh-session, attached-clients, network-vpn, weather, time, mpc, spotify-tui, krbtgt, playerctl, kubernetes-context, synchronize-panes
set -g @dracula-plugins "git battery ram-usage network network-ping time"

# available colors: white, gray, dark_gray, light_purple, dark_purple, cyan, green, orange, red, pink, yellow
# set -g @dracula-[plugin-name]-colors "[background] [foreground]"

set -g @dracula-battery-colors "pink gray"
set -g @dracula-ram-usage-colors "cyan gray"
set -g @dracula-network-colors "orange gray"
set -g @dracula-network-ping-colors "orange gray"
#set -g @dracula-time-colors "dark_purple white"

set -g @dracula-battery-label "󰁼"
set -g @dracula-ram-usage-label "󰍛"
set -g @dracula-time-format "%a, %d/%m/%y %k:%M:%S"

set -g @dracula-left-icon-padding 1
set -g @dracula-show-powerline true
set -g @dracula-show-left-sep 
set -g @dracula-show-right-sep 
set -g @dracula-show-flags true
set -g @dracula-show-empty-plugins false
set -g @dracula-refresh-rate 1

run '~/.tmux/plugins/tpm/tpm'
```

Reload TMUX environment so TPM is sourced:
```.tmux.conf
# type this in terminal if tmux is already running
tmux source ~/.tmux.conf
```

#### Installing plugins
Press `prefix` + `I` (capital i, as in Install) to fetch the plugin.
> I map the `prefix` to the `control + a`

## Usage

Run this command to start new `Tmux` session:
```
tmux
```

#### Mapping
| Mappings           | Description                                |
| ---------------    | ------------------------------------------ |
| `prefix` + `-`     | Split pane horizontally                    |
| `prefix` + &#124;` | Split pane vertically                      |
| `prefix` + `H`     | Resizes the current pane left              |
| `prefix` + `L`     | Resizes the current pane right             |
| `prefix` + `J`     | Resizes the current pane down              |
| `prefix` + `K`     | Resizes the current pane upward            |
| `prefix` + `D`     | Kill pane                                  |
| `prefix` + `d`     | kill session                               |

> I map the `prefix` to the `control + a`. You can customize it if you need.
