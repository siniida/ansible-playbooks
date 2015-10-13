# Docker Sandbox

Multi Docker Host + Weave + Swarm

## 必要環境

* playbookを実行するHostにdockerクライアントが必須


## 対象OS

* CentOS 7
* AmazonLinux


## 各種version

* weave v1.1.0
* docker 1.8.2


## 設定ファイル

hosts

    [leader]
    192.168.33.101
    
    [member]
    192.168.33.102
    
    [all:vars]
    leader=192.168.33.101

* leaderグループに必ず1つ以上のhostを設定
* [all:vars]のleaderに同じhostを設定

## 実行例

    $ vagrant up
    $ cd ../
    $ ansible-playbook -i docker-sandbox/hosts docker-sandbox.yml

## DockerHostを追加

`docker-sandbox.yml`で構築したDockerクラスタに、Dockerホストを追加する。

### 設定ファイル

hosts

    [member]
    192.168.33.103
    
    [all:vars]
    leader=192.168.33.101
    token=[SWARM_TOKEN]

### 実行例

    $ cd ../
    $ ansible-playbook -i docker-sandbox/add-hosts join-docker-sandbox.yml