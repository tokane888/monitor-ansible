# init-monitor

- ansibleで下記をubuntu環境にデプロイ
  - prometheus
  - grafana
- ディレクトリ構成
  - 下記の公式推奨構成に従う
    - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#alternative-directory-layout
    - vault周りは下記の公式ガイドに従う
      - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#variables-and-vaults

## 前提

- prometheusサーバ
  - 対応アーキ
    - amd64
    - arm64
      - ラズパイ3系以降
  - dockerインストール済み

## 使用方法

- prometheus serverセットアップ
  - デプロイコマンド実行
    - `ansible-playbook -i inventories/development/hosts.yml prometheus_server.yml -K`
      - 途中でsudoパスワードを聞かれるので入力

