# mypy-test

- mypyの挙動確認用リポジトリ

## やりたいこと

- repo1はpre-commitのhookでmypyでチェックする。
- repo2はmypyでチェックしない。
- mypy, pre-commitはrepo1の.venvにインストールしたものを用いる

## 問題の再現までの環境構築

1. uvのインストール ([公式サイト](https://docs.astral.sh/uv/#getting-started)）
2. uvで環境構築をする
  ```bash
  $ cd mypy-test/app/repo1
  $ uv sync
  $ uv run pre-commit install
  ```
3. repo2の中にmypyに絶対弾かれるコードを書く（定義されてない変数名とかを書けばOK）
4. commitする
  ```
  $ git add .
  $ git commit -m "hogehoge"
  ```
5. ここでrepo2にmypyが走ってしまう。本当はrepo1以外はチェックして欲しくないので、すんなりとコミットできて欲しい。
