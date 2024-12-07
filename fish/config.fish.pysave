if status is-interactive
    # Commands to run in interactive sessions can go here
end

if test (uname) = Darwin
    # macOS Silicon
    #set BREW_BIN /opt/homebrew/bin/brew
    # macOS Intel
    set BREW_BIN /usr/local/bin/brew
    # Linux
else
    set BREW_BIN /home/linuxbrew/.linuxbrew/bin/brew
end

eval ($BREW_BIN shellenv)

# set tmux session with your name
if not set -q TMUX
    set SESSION_NAME tone
    if tmux has-session -t $SESSION_NAME 2>/dev/null
        tmux attach-session -t $SESSION_NAME
    else
        tmux new-session -s $SESSION_NAME
    end
end

# shell enhancements
starship init fish | source
zoxide init fish | source
atuin init fish | source
set -x PATH $HOME/.cargo/bin $PATH
set -Ux CARAPACE_BRIDGES 'zsh,fish,bash,inshellisense'
mkdir -p ~/.config/fish/completions
carapace --list | awk '{print $1}' | xargs -I{} touch ~/.config/fish/completions/{}.fish
carapace _carapace | source

# JAVA_HOME
set -x JAVA_HOME /usr/local/Cellar/openjdk@21/21.0.5/libexec/openjdk.jdk/Contents/Home
set -x PATH $JAVA_HOME/bin $PATH

# greeting message
set -g fish_greeting ""

## alias
alias ls='gls --color=auto'
alias fzfbat='fzf --preview="bat --theme=gruvbox-dark --color=always {}"'
alias fzfnvim='nvim (fzf --preview="bat --theme=gruvbox-dark --color=always {}")'

# colors
set -x LS_COLORS "di=38;5;67:ow=48;5;60:ex=38;5;132:ln=38;5;144:*.tar=38;5;180:*.zip=38;5;180:*.jpg=38;5;175:*.png=38;5;175:*.mp3=38;5;175:*.wav=38;5;175:*.txt=38;5;223:*.sh=38;5;132"

# kanagawa dragon colors
set -l foreground DCD7BA # dragonWhite
set -l selection 2D4F67 # waveBlue2
set -l comment 7A8382 # dragonGray3
set -l red C4746E # dragonRed
set -l orange B98D7B # dragonOrange2
set -l yellow C4B28A # dragonYellow
set -l green 87A987 # dragonGreen
set -l purple 957FB8 # oniViolet
set -l cyan 8EA4A2 # dragonAqua
set -l pink D27E99 # sakuraPink

# Syntax Highlighting Colors
set -g fish_color_normal $foreground
set -g fish_color_command $cyan
set -g fish_color_keyword $pink
set -g fish_color_quote $yellow
set -g fish_color_redirection $foreground
set -g fish_color_end $orange
set -g fish_color_error $red
set -g fish_color_param $purple
set -g fish_color_comment $comment
set -g fish_color_selection --background=$selection
set -g fish_color_search_match --background=$selection
set -g fish_color_operator $green
set -g fish_color_escape $pink
set -g fish_color_autosuggestion $comment

# Completion Pager Colors
set -g fish_pager_color_progress $comment
set -g fish_pager_color_prefix $cyan
set -g fish_pager_color_completion $foreground
set -g fish_pager_color_description $comment

clear
