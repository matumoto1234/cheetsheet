# base16の設定



```bash
$ git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
```

を実行して、`~/.bashrc`に以下を書き込む

```bash
BASE16_SHELL="$HOME/.config/base16-shell/"
[ -n "$PS1" ] && \
    [ -s "$BASE16_SHELL/profile_helper.sh" ] && \
        eval "$("$BASE16_SHELL/profile_helper.sh")"
```

