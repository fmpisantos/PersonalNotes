export PATH=/opt/homebrew/bin:/Users/fmpi.santos/.docker/bin:/Users/fmpi.santos/.cargo/bin:/Users/fmpi.santos/.docker/bin:/Users/fmpi.santos/.pyenv/bin:/Users/fmpi.santos/.nvm/versions/node/v18.7.0/bin:/Library/Frameworks/Python.framework/Versions/3.10/bin:/usr/local/bin:/System/Cryptexes/App/usr/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/go/bin:/Library/Apple/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/local/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/appleinternal/bin:/Users/fmpi.santos/Library/Android/Sdk/emulator:/Users/fmpi.santos/Library/Android/Sdk/tools:/Users/fmpi.santos/Library/Android/Sdk/tools/bin:/Users/fmpi.santos/Library/Android/Sdk/platform-tools
eval export HOMEBREW_PREFIX="/opt/homebrew";
export HOMEBREW_CELLAR="/opt/homebrew/Cellar";
export HOMEBREW_REPOSITORY="/opt/homebrew";
export PATH="/opt/homebrew/bin:/opt/homebrew/sbin${PATH+:$PATH}";
export MANPATH="/opt/homebrew/share/man${MANPATH+:$MANPATH}:";
export INFOPATH="/opt/homebrew/share/info:${INFOPATH:-}";

if [ -f ~/.bash_profile ]; then 
    . ~/.bash_profile;
fi
test -e "${HOME}/.iterm2_shell_integration.zsh" && source "${HOME}/.iterm2_shell_integration.zsh" || true
export NVM_DIR="$HOME/.nvm"
  [ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
export PATH="/opt/homebrew/opt/mysql-client/bin:$PATH"
export PATH="/opt/homebrew/opt/mysql-client@8.4/bin:$PATH"
export PATH="$PATH:/usr/local/share/dotnet"

