# Kea DHCPv4 Server on Docker

Kea DHCPv4 ServerをDocker上で動かし、DHCPサービスを提供します。

Alpine Linuxをベースイメージとして使用し、Alpine LinuxのリポジトリからKea DHCPをインストールして動作します。

Network ModeをHostモードで動作させ、Dockerホストマシンのネットワークインターフェイスで受信したクライアントからの要求を処理します。

## ホスト側で準備する環境

  * Docker
  * Docker-compose

## 使用方法

 1. 各自のネットワーク環境に応じて、conf/kea-dhcp4.confを書き換える。  
    "interfaces-config"は、Dockerホストのネットワークデバイス名を正常に書かないと動作しない。  
    ホストのネットワークインターフェイス名は、`ifconfig`または`ip addr show`などで調べておく。
 2. docker-compose build
 3. docker-compose up -d
 4. (Optional) DockerホストマシンでFirewallを使用している場合、67/udpへの着信を許可する。  
    firewalldを使用している場合、下記のようなコマンドを実行する。  
    `firewall-cmd --add-port 67/udp --permanent && firewall-cmd --reload`

