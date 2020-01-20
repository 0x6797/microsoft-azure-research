# Ubuntu でもデスクトップ環境が使いたい（X Server編）

## Ubuntu （ゲストOS）側の設定

### SSH でログイン

最初はコマンドライン端末に SSH でログインします。

### パッケージのアップデートとインストール

#### Ubuntu Ja REMIX のインストール

日本語にも対応するために、追加パッケージをインストールします。

```bash
$ wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add -
$ wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add -
$ sudo wget https://www.ubuntulinux.jp/sources.list.d/bionic.list -O /etc/apt/sources.list.d/ubuntu-ja.list
$ sudo apt update -y
$ sudo apt upgrade -y
$ sudo apt install -y ubuntu-defaults-ja
```

#### XDMCP の設定

> XDMCP Server はインストールされているはず…

`/etc/hosts.allow` に以下を追加

```
ALL: ALL
```

`/etc/gdm3/custom.conf` に以下を追加

```
[security]
DisallowTCP=false

[xdmcp]
Enable=true
```

`gdm` の再起動

```bash
$ sudo /etc/init.d/gdm3 restart
```

## Windows （ホストOS）側の設定

### VcXsrv のインストール

[https://sourceforge.net/projects/vcxsrv/](https://sourceforge.net/projects/vcxsrv/) から VcXsrv をインストール

### VxXsrv の起動と設定

> TBD

