# oase-site

## 前提条件

1. 自身の開発PC上にVSCodeがインストール済みであること
1. VSCodeから開発サーバに対して拡張機能「Remote - SSH」を使ってログインできること
1. 開発サーバは、CentOS 7であること
1. 開発サーバ上にDocker環境が構築済みであること
1. 開発サーバは個人用に設定済みの環境であること
   1. `~/.gitconfig` の設定が個人のものとなっていること
   1. `~/.netrc` にGitのログイン情報が入っていること

## 各リポジトリをフォーク

下記の exastro-suite にある各リポジトリを自身のアカウントのリポジトリにフォークする。
- [oase-site をフォーク](https://github.com/exastro-suite/oase-site/fork)
- [oase-docs をフォーク](https://github.com/exastro-suite/oase-docs/fork)
- [docs をフォーク](https://github.com/exastro-suite/docs/fork)

## 各リポジトリのクローン
1. 作業用のサーバにログインする
2. 下記のコマンドを実行し、oase-site リポジトリをクローンする
   ```bash
   # 自身のGitHubアカウントを変数に格納
   # your-github-account を自身のGitHubアカウント名に変更
   MY_GITHUB_ACCOUNT="your-github-account"
   
   # 作業用のディレクトリを作成
   mkdir ~/${MY_GITHUB_ACCOUNT}
   
   # oase-site のフォークリポジトリをクローンする
   cd ~/${MY_GITHUB_ACCOUNT}
   git clone https://github.com/${MY_GITHUB_ACCOUNT}/oase-site.git
   ```
3. oase-docs と docs リポジトリをサブモジュールとしてクローンする
   ```bash
   # サブモジュールを自身のリポジトリに置き換える
   cd ~/${MY_GITHUB_ACCOUNT}/oase-site
   sed -i -e "s|https://github.com/exastro-suite|https://github.com/${MY_GITHUB_ACCOUNT}|g" .gitmodules

   # リモートリポジトリと動機
   git submodule sync
   git submodule foreach git pull
   ```

## ドキュメントの作成・更新

1. VSCode の拡張機能の"Remote - SSH"を使って、開発サーバにログインする
2. 「ファイル」-「ファイルでワークスペースを開く」から上記でクローンしたoase-site内にある「oase-site.code-workspace」を開く。
3. 左下のRemote接続用の「><」アイコンをクリックし、「Reopen in Container」を開く。
4. あとはoase-docs配下のファイルを編集する。

## Talismanのセットアップ
環境に合わせて適当に設定をする。

## 編集中のドキュメントの確認
下記の拡張機能をインストールし、プレビュー画面で確認する。

- lextudio.restructuredtext
- lextudio.restructuredtext-pack
- trond-snekvik.simple-rst
- searKing.preview-vscode

## 画面確認

http://127.0.0.1:8000