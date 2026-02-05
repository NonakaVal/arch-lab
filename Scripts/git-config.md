```
git config --global user.name "username" \
&& git config --global user.email "useremail" \
&& [ -f ~/.ssh/id_ed25519 ] || ssh-keygen -t ed25519 -C "useremail" -f ~/.ssh/id_ed25519 \
&& systemctl --user enable --now ssh-agent.socket \
&& export SSH_AUTH_SOCK="$XDG_RUNTIME_DIR/ssh-agent.socket" \
&& ssh-add ~/.ssh/id_ed25519 \
&& git config --global url."git@github.com:".insteadOf https://github.com/ \
&& ssh -T git@github.com
```