# env
export EDITOR="vim"

autoload -U compinit
compinit

setopt auto_pushd
setopt auto_cd
setopt correct
setopt cdable_vars

## keybind
bindkey -v

# aliases
#alias ls='ls -G'
alias ls='ls --color=auto'
alias ll='ls -ltr'
alias vi='vim'
alias gd='dirs -v; echo -n "select number: "; read newdir; cd +"$newdir"'
alias screen="screen -D -R"
alias r='rails'

export LSCOLORS=gxfxcxdxbxegedabagacad

# colors for logged in user
autoload colors
colors
case ${UID} in
0)
  PROMPT="%B%{${fg[red]}%}${USER}@${HOST}#%{${reset_color}%}%b "
  PROMPT2="%B%{${fg[red]}%}${USER}@${HOST}#%{${reset_color}%}%b "
  SPROMPT="%B%{${fg[red]}%}%r is correct? [n,y,a,e]:%{${reset_color}%}%] "
  RPROMPT="[%/]"
  ;;
*)
  PROMPT="%{%B${fg[blue]}%}${USER}@${HOST}$%{${reset_color}%}%b "
  PROMPT2="%B%{${fg[blue]}%}${USER}@${HOST}$%{${reset_color}%}%b "
  SPROMPT="%B%{${fg[blue]}%}%r is correct? [n,y,a,e]:%{${reset_color}%}%b "
  RPROMPT="[%~]"
  ;;
esac

# C-s, C-qを無効にする。
setopt NO_flow_control

# history settings =====================================================
# history
HISTFILE=~/.histfile
HISTSIZE=10000
SAVEHIST=10000

# write timestamp to history file
setopt extended_history

# 直前と同じコマンドラインはヒストリに追加しない
setopt hist_ignore_dups

# 重複したヒストリは追加しない
setopt hist_ignore_all_dups

# ヒストリを呼び出してから実行する間に一旦編集できる状態になる
setopt hist_verify

# auto_list の補完候補一覧で、ls -F のようにファイルの種別をマーク表示しない
setopt NO_list_types

# 複数の zsh を同時に使う時など history ファイルに上書きせず追加
setopt append_history

# end history settings =================================================

# compinit settings ====================================================
# 補完するかの質問は画面を超える時にのみに行う｡
LISTMAX=0

# 補完の利用設定
autoload -Uz compinit; compinit

# sudo でも補完の対象
zstyle ':completion:*:sudo:*' command-path /usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin

# 補完候補が複数ある時に、一覧表示
setopt auto_list

# 補完キー（Tab, Ctrl+I) を連打するだけで順に補完候補を自動で補完
setopt auto_menu

# カッコの対応などを自動的に補完
setopt auto_param_keys

# ディレクトリ名の補完で末尾の / を自動的に付加し、次の補完に備える
setopt auto_param_slash

# ファイル名の展開でディレクトリにマッチした場合末尾に / を付加する
setopt mark_dirs

# auto_list の補完候補一覧で、ls -F のようにファイルの種別をマーク表示しない
setopt NO_list_types

# コマンドラインの引数で --prefix=/usr などの = 以降でも補完できる
setopt magic_equal_subst

# 8 ビット目を通すようになり、日本語のファイル名を表示可能
setopt print_eight_bit

# シェルのプロセスごとに履歴を共有
setopt share_history

# Ctrl+wで､直前の/までを削除する｡
WORDCHARS='*?_-.[]~=&;!#$%^(){}<>'

# ファイルリスト補完でもlsと同様に色をつける｡
zstyle ':completion:*' list-colors ${(s.:.)LS_COLORS}

# end compinit settings ================================================


# history search
autoload history-search-end
zle -N history-beginning-search-backward-end history-search-end
zle -N history-beginning-search-forward-end history-search-end
bindkey "^P" history-beginning-search-backward-end
bindkey "^N" history-beginning-search-forward-end


# load vi mode configuration
[ -f ~/.zsh/.zshrc.vimode ] && source ~/.zsh/.zshrc.vimode

# load mintty configuration
[ -f ~/.zsh/.zshrc.mintty ] && source ~/.zsh/.zshrc.mintty

export PATH="$PATH:$HOME/.rvm/bin" # Add RVM to PATH for scripting

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

# undef stop
stty stop undef

# terminal setting
export TERM=xterm-256color

# start ssh-agent
eval $(ssh-agent)
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/agileware_core_rsa
ssh-add ~/.ssh/oncloud.pem
ssh-add ~/.ssh/learning-encollege-production-vpc.pem
ssh-add ~/.ssh/encollege-production-vpc.pem

# ruby settings
alias be='bundle exec'
alias brake='bundle exec rake'
export PATH=~/pebble-dev/pebble-sdk-4.0.1-linux64/bin:$PATH

### Added by the Heroku Toolbelt
export PATH="/usr/local/heroku/bin:$PATH"

### AWS CLI
source /usr/local/bin/aws_zsh_completer.sh
complete -C aws_completer aws

if [[ -s ~/.nvm/nvm.sh ]];
  then source ~/.nvm/nvm.sh
fi

### go
export GOPATH=$HOME/.go
