# Ubuntu でもリモートデスクトップを使いたい

> **まだ作業途中**

Azure の Ubuntu 仮想マシンに RDP サーバーを設定します。

## 目次

## 仮想マシンの作成

オペレーティングシステムは Ubuntu Server 18.04 を選んで、いい感じに仮想マシンを作成します。

ここで注意すべき点はユーザーの作成で、必ずパスワード認証をするようにして下さい。SSH 公開キーではダメです。


## SSH でログイン

最初はコマンドライン端末に SSH でログインします。

## パッケージのアップデートとインストール

### Ubuntu Ja REMIX のインストール

日本語にも対応するために、追加パッケージをインストールします。

```bash
$ wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add -
$ wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add -
$ sudo wget https://www.ubuntulinux.jp/sources.list.d/bionic.list -O /etc/apt/sources.list.d/ubuntu-ja.list
$ sudo apt update -y
$ sudo apt upgrade -y
$ sudo apt install -y ubuntu-defaults-ja
```

### 好きなデスクトップ環境と XRDP のインストール

#### Ubuntu Desktop の場合

```bash
$ sudo apt install -y ubuntu-desktop
$ sudo apt install -y xrdp
```

#### LXDE の場合

```bash
$ sudo apt install -y lubuntu-desktop
$ sudo apt install -y xrdp
$ sudo sed -e 's/^new_cursors=true/new_cursors=false/g' \
 -i /etc/xrdp/xrdp.ini$ echo lxsession -s Lubuntu -e LXDE > ~/.xsession
$ echo lxsession -s Lubuntu -e LXDE > ~/.xsession
$ sudo systemctl restart xrdp
```

#### Authentication Requiredダイアログの回避

ここで RDP でログインすると、`ubuntu` ユーザーの認証が求められます。これを回避するために、ログインする前に以下を実行します。

```bash
$ cat <<EOF | \
   sudo tee /etc/polkit-1/localauthority/50-local.d/xrdp-color-manager.pkla
[Netowrkmanager]
Identity=unix-user:*
Action=org.freedesktop.color-manager.create-device
ResultAny=no
ResultInactive=no
ResultActive=yes
EOF
$ sudo systemctl restart polkit
```

### Windows のリモートデスクトップで接続する

Windows のリモートデスクトップを使用して、Ubuntu に接続します。初回はデスクトップ環境のセットアップウィザードが実行されるので、いい感じに設定します。

その際に注意するのは、キーボード配列を `English (US)` のままにしておくことです。Windows のリモートデスクトップがわでキーボード配列の変換をしてくれるので、無理に日本語キーボードで設定すると悲惨なことになります。

## 日本語入力について

RDP のレベルでキーマッピングの変換を行うため、日本語キーボードの場合は意図した文字が入力できない場合があります…

## RDP の接続に失敗する場合は

SSH でログインして、以下のコマンドを実行する。

```bash
sudo systemctl restart xrdp
```

