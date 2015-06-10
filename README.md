# tmux-config
My tmux-configuration - Thanks to Ben


# unbind control + b - default tmux prefix
unbind C-b

# bind global prefix to control + S
set -g prefix C-s
bind-key -r C-s send-prefix

bind-key r source-file ~/.tmux.conf \; display-message "~/.tmux.conf reloaded"

bind-key -n C-h select-pane -L
bind-key -n C-j select-pane -D
bind-key -n C-k select-pane -U
bind-key -n C-l select-pane -R

set-option -g default-terminal "screen-256color"
set-option -g status-keys "emacs"

set-option -g status-left-length 50

set-option -g status-right " #(battery -t) "

bind-key - split-window -v  -c '#{pane_current_path}'
bind-key \ split-window -h  -c '#{pane_current_path}'

bind -n S-Left resize-pane -L 2
bind -n S-Right resize-pane -R 2
bind -n S-Down resize-pane -D 1
bind -n S-Up resize-pane -U 1

bind -n C-Left resize-pane -L 10
bind -n C-Right resize-pane -R 10
bind -n C-Down resize-pane -D 5
bind -n C-Up resize-pane -U 5

bind c new-window -c '#{pane_current_path}'

set-option -g base-index 1
set-option -g renumber-windows on

bind-key b break-pane -d

bind-key C-j choose-tree

# Use vim keybindings in copy mode
setw -g mode-keys vi

# Setup 'v' to begin selection as in Vim
bind-key -t vi-copy v begin-selection
bind-key -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"

# Update default binding of `Enter` to also use copy-pipe
unbind -t vi-copy Enter
bind-key -t vi-copy Enter copy-pipe "reattach-to-user-namespace pbcopy"
