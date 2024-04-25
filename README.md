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
set -g prefix ^a
set -g mouse on
set -ag terminal-overrides ",xterm-256color:RGB"
set  -g default-terminal "tmux-256color"

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-pain-control'
set -g @plugin 'christoomey/vim-tmux-navigator'


# Smart pane switching with awareness of Vim splits.
# See: https://github.com/christoomey/vim-tmux-navigator
is_vim="ps -o state= -o comm= -t '#{pane_tty}' \
    | grep -iqE '^[^TXZ ]+ +(\\S+\\/)?g?(view|l?n?vim?x?|fzf)(diff)?$'"
bind-key -n 'C-h' if-shell "$is_vim" 'send-keys C-h'  'select-pane -L'
bind-key -n 'C-j' if-shell "$is_vim" 'send-keys C-j'  'select-pane -D'
bind-key -n 'C-k' if-shell "$is_vim" 'send-keys C-k'  'select-pane -U'
bind-key -n 'C-l' if-shell "$is_vim" 'send-keys C-l'  'select-pane -R'
tmux_version='$(tmux -V | sed -En "s/^tmux ([0-9]+(.[0-9]+)?).*/\1/p")'
if-shell -b '[ "$(echo "$tmux_version < 3.0" | bc)" = 1 ]' \
    "bind-key -n 'C-\\' if-shell \"$is_vim\" 'send-keys C-\\'  'select-pane -l'"
if-shell -b '[ "$(echo "$tmux_version >= 3.0" | bc)" = 1 ]' \
    "bind-key -n 'C-\\' if-shell \"$is_vim\" 'send-keys C-\\\\'  'select-pane -l'"

bind-key -T copy-mode-vi 'C-h' select-pane -L
bind-key -T copy-mode-vi 'C-j' select-pane -D
bind-key -T copy-mode-vi 'C-k' select-pane -U
bind-key -T copy-mode-vi 'C-l' select-pane -R
bind-key -T copy-mode-vi 'C-\' select-pane -l

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run -b '~/.tmux/plugins/tpm/tpm'
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
