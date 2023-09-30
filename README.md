# init-monitor

- ansibleで下記をubuntu環境にデプロイ
  - prometheus
  - grafana
- ディレクトリ構成
  - 下記の公式推奨構成に従う
    - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#alternative-directory-layout
    - vault周りは下記の公式ガイドに従う
      - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html#variables-and-vaults

## 使用方法

- control nodeセットアップ
  - 前提
    - docker, ansibleインストール済み
  - デプロイコマンド実行
    - `ansible-playbook -i inventories/development/hosts.yml control_node.yml -K`
      - 途中でsudoパスワードを聞かれるので入力

