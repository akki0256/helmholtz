# Discord読み上げbot ヘルムホルツ

特定のテキストチャンネルに書き込まれたメッセージを、
ボイスチャンネルで読み上げます。

マイクをミュートしている人のメッセージしか読み上げません。

## Docker

Discordの各種IDを調べて環境変数に書き込む。

各種IDは設定から開発者モードを有効化して「右クリック→IDをコピー」で取得できる。

* DISCORD_TOKEN: botのトークン（開発者ページの「Bot」から取得）
* DISCORD_GUILD_ID: サーバID
* DISCORD_SOURCE_CHANNEL_ID: テキストチャンネルのID

Google Cloud Platform で Cloud Text-to-Speech APIを有効にし、サービスアカウントを作る。

* GOOGLE_CLIENT_EMAIL: サービスアカウントのメールアドレス
* GOOGLE_PRIVATE_KEY: サービスアカウントのプライベートキー

あとはビルドしてこれらの環境変数とともに実行する。

## 手動で動かす

依存モジュールをインストールする。ffmpeg必須。

```
sudo apt install ffmpeg
npm install
```

Discordの各種IDを調べて環境変数に書き込む。

各種IDは設定から開発者モードを有効化して「右クリック→IDをコピー」で取得できる。

* DISCORD_TOKEN: botのトークン（開発者ページの「Bot」から取得）
* DISCORD_GUILD_ID: サーバID
* DISCORD_SOURCE_CHANNEL_ID: テキストチャンネルのID

Google Cloud Platform で Cloud Text-to-Speech APIを有効にし、サービスアカウントを作る。

* GOOGLE_CLIENT_EMAIL: サービスアカウントのメールアドレス
* GOOGLE_PRIVATE_KEY: サービスアカウントのプライベートキー

これらの環境変数と一緒に以下を実行する。

```
export DISCORD_TOKEN="token"
export DISCORD_GUILD_ID="00000"
export DISCORD_SOURCE_CHANNEL_ID="12345"
export GOOGLE_CLIENT_EMAIL="serviceaccount@mail.com"
export GOOGLE_PRIVATE_KEY=$'privkey'
node app.js
```