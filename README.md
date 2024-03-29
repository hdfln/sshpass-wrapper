# sshpass-wrapper

[![asciicast](https://asciinema.org/a/Q5lA1c0cr1CGvmZWocpQF7wa9.svg)](https://asciinema.org/a/Q5lA1c0cr1CGvmZWocpQF7wa9)

## 要件

- [sshpass](https://linux.die.net/man/1/sshpass)
- [fzf](https://github.com/junegunn/fzf)

## インストール

```bash
ghq get git@github.com:hdfln/sshpass-wrapper.git
cat <'<EOF' >> ~/.zshrc
SSHPASS_WRAPPER_DEFINITION_FILE=~/ghq/github.com/hdfln/sshpass-wrapper/.zsh_sshpass_wrapper
if [ -f ${SSHPASS_WRAPPER_DEFINITION_FILE} ]; then
    source ${SSHPASS_WRAPPER_DEFINITION_FILE}
fi
EOF
source ~/.zshrc
```

### ~/sshpass-wrapper/hostsにIPアドレスを記述したファイルを追加


ファイル名は任意です。空行、または、「#」で始まる行は無視します。

例：`~/sshpass-wrapper/hosts/list`

```tsv
192.168.10.1  my-host1
192.168.10.2  my-host2
...
```

### クレデンシャルファイルの作成

1行目にユーザー名、2行目にパスワードを入力します。

例：`~/sshpass-wrapper/secrets/my-credential`

```
user-hoge
pass-fuga
```

### 使用例

構文は以下の通りです。

`sshpass-wrapper <使用するクレデンシャル>`

実行すると、接続先のホストの候補が表示されます。
クレデンシャルファイルに設定したユーザー名・パスワードで接続します。

`get-pass <使用するクレデンシャル>`

実行すると、パスワードがクリップボードに保存されます。クレデンシャルを省略すると、クレデンシャルの選択画面が表示されます。
