## `docker-mirakurun-chinachu` Installer for CentOS 7 w/ PLEX drivers

`S64/ansible-chinachu-gamma-playbook`はCentOS 7上に`docker-mirakurun-chinachu`を用いた Mirakurun / Chinachu 環境を構築し、併せてPLEXドライバや関連ツールを導入するAnsible Playbookです。

以下の環境を想定しています。

- CentOS 7 Minimal
- PLEX社製USBデータ供給テレビチューナ
- SCR3310等スマートカードリーダ

## 行うこと

以下の操作を行うため注意してください。

- `/usr/bin/pcsc_scan`等関連ツールインストール
- `arib25`インストール
- Dockerオフィシャルリポジトリ追加
  - `docker-ce` / `docker-compose` インストール
- `/usr/lib64/usb-px4.ko`等インストール
- `/opt/chinachu`書き込み
- `/etc/systemd/system/mirakurun-chinachu.service`作成

また、`docker-mirakurun-chinachu`に対し

- PLEX向け`recpt1` (MyRecpt1) を `/usr/local/bin/recpx4` としてインストール
- `alioth.debian.org`がよく落ちるため、`ccid-1.4.26.tar.bz2`のミラーを追加

などのカスタマイズを加えています。  
なお、現バージョンは冪等性を担保していないため注意してください。

## 設定ファイル

`docker-mirakurun-chinachu`を`/opt/chinachu/docker-mirakurun-chinachu`へcloneしているため、その配下ディレクトリへ配置してください。  
`recpx4`を用いた`tuners.yml`の設定例は[こちら](https://gist.github.com/S64/b42c6b901f875d1779d4c82b3bcd4b98)にあります。
