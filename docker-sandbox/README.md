# Docker Sandbox

Multi Docker Host + Weave + Swarm

## 必要環境

* playbookを実行するHostにdockerクライアントが必須

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
