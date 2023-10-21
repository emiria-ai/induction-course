# Git と GitHub の必要性と使い方について

この章では、なぜ Git や GitHub が必要なのか、実際にどのように Git を使用したり、リモートリポジトリに展開するのかを解説します。

## なぜ Git が必要か

1. バージョン管理: ソフトウェアの変更履歴を管理できます。
1. 協力作業: 複数人での開発が容易になります。
1. コードの履歴: 誰が何をしたのかが一目瞭然です。

## GitHub との関連性

1. 前提として、Git と GitHub は別物です
1. リモートリポジトリ: オンラインでコードを保存・共有できます。
1. コラボレーション: チームでの作業が容易になります。
1. オープンソース: オープンソースプロジェクトでよく使用されます。

## Git のインストール

Mac であれば、HomeBrew でインストールするのが一番手っ取り早いです。

```bash
brew install git
```

## .gitconfig について

.gitconfig は Git の設定ファイルで、ユーザー名やメールアドレス、使いたいエディタなどを設定できます。GitHub と同じ情報で揃える事によって、活動履歴が表示されるようになります。

注意としては、GitHub などにこのメールアドレスでコミットして公開リポジトリでプッシュすると、この情報は誰でも見られるので注意してください。このために、GitHub では noreply メールアドレスが一人一つ割り当てられています。

> 個人のメール アドレスを非公開にする場合は、コミット メール アドレスとして GitHub の noreply メール アドレスを使用できます。 コマンド ラインからプッシュするコミットに noreply メール アドレスを使用するには、Git でコミット メール アドレスを設定するときにそのメール アドレスを使用します。 Web ベースの Git 操作に noreply アドレスを使用するには、GitHub にコミット メール アドレスを設定し、 [Keep my email address private](メール アドレスを非公開にする) を選択します。

[コミットメールアドレスを設定する](https://docs.github.com/ja/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)

```ini
[user]
    name = "あなたの名前"
    email = "you@example.com"
[core]
    editor = vim
```

name や email をグローバルで登録するには、以下のコマンドを打ちます。

```bash
git config --global user.name "Mona Lisa"
git config --global user.email "YOUR_EMAIL"
```

## GitHub にプッシュするまでの手順

### リポジトリのクローンまたは初期化

リポジトリをリモートリポジトリからクローンするか、新規に Git の初期化を行います。

```bash
git clone [リポジトリURL]
# または
git init
```

### 変更をステージング

ステージングは、Git リポジトリにコミットするファイルを置いておくためのエリアです。以下のコマンドでは、まだ取り込んでいない内容をすべてステージングします。

```bash
git add .
```

### コミット

コミットとは、`Git`に変更を記録するための作業です。

```bash
git commit -m "コミットメッセージ"
```

### リモートリポジトリを設定

GitHub などのリモートリポジトリのアドレスに.git をつけたアドレスです。例えば、このリポジトリであれば、`https://github.com/emiria-ai/induction-course.git`です。

```bash
git remote add origin [リポジトリURL]
```

### アクセストークンの設定

GitHub では、パスワード認証ではなく Personal access tokens を使います。GitHub の[Developer settings](https://github.com/settings/developers)からトークンを発行します。安全のため、有効期限を設けたほうがいいかと思います。

発行したトークンはコピーして保管しておきましょう。

### プッシュ

プッシュは、GitHub などのリモートリポジトリにコミットしたファイルをアップロードすることを指します。プッシュでは複数のコミットをまとめてアップロードすることもできます。

git push を行う際に、アクセストークンをパスワードとして入力します。すること GitHub を確認したら反映されているはずです 🎉

```bash
git push -u origin main
```
