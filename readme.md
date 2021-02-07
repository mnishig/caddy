# Caddy server reverse proxy sample

非常に単純な Caddy のリバースプロキシサンプル

動作環境
- docker (docker compose)
- caddy

docker-compose 内で Caddyfile をコンテナ内の以下にコピーしている。(デフォルトの設定を上書きしてる。)
/etc/caddy/Caddyfile

docker は以下のポートをマッピングしている
5000 > 80
5443 > 443

80, 443 で受けた Caddy 側では、
80: 自分でレスポンスを返す
443: upstream の　txn.myds.me:80 に流す

### 注意
ちょっとよく分かっていないが、
reverse_proxy として設定したものは、https でアクセスしないとダメっぽい。

今回の例だと、
```
http://localhost:5443/ は、エラー
https://localhost:5443/ は、OK
```
