# monitor-ansible

- ansibleで下記をlinux環境にデプロイ
  - prometheus
  - grafana
- prometheus/grafanaサーバと、監視対象(target)の両方を構築
- ディレクトリ構成
  - 下記の公式推奨構成に従う
    - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#alternative-directory-layout
    - vault周りは下記の公式ガイドに従う
      - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#variables-and-vaults

## 前提

- ansible control node
  - sshpassインストール済み
    - 未インストールの場合は下記でインストール
      - `sudo apt install -y sshpass`
- prometheusサーバ
  - 対応アーキ
    - amd64
    - arm64
      - ラズパイ3系以降
  - dockerインストール済み

## 使用方法

- 設定情報記載
  - inventories/development/hosts.yml
    - ssh接続パス
      - ansible_ssh_pass
    - sudoパス
      - ansible_sudo_pass
    - デプロイ先host追記／修正
  - inventories/development/group_vars/prometheus_server/vars
    - grafana認証情報
      - grafana_user
      - grafana_pass
  - inventories/development/group_vars/targets/vars
    - インストール対象のnode_exporterのバージョン
      - node_exporter_version
- セットアップ
  - 下記コマンド実行
    - `ansible-playbook -i inventories/development/hosts.yml monitoring.yml`
