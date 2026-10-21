# fukuoka.todokede.jp の接続と公開設定

名古屋市版（nagoya-shobo-soudan）の `docs/domain-setup.md` と同じ構成。SaaS ゾーンは共通基盤の meher-edge.com。

| 項目 | 値 |
|---|---|
| Worker | fukuoka-shobo-soudan（Workers Builds で meher-inc/fukuoka-shobo-soudan の main を自動デプロイ。デプロイコマンド `pnpm run deploy`） |
| D1 | fukuoka-shobo-soudan（`scripts/ensure-d1.mjs` が初回デプロイで作成） |
| カスタムホスト名 | fukuoka.todokede.jp（meher-edge.com） |
| ルート | `fukuoka.todokede.jp/*`（zone: meher-edge.com） |
| レート制限 | namespace_id 8430 |
| 正規URL | `CANONICAL_ORIGIN = https://fukuoka.todokede.jp` |

todokede.jp の DNS（お名前.com）には、`fukuoka` の CNAME（`customers.meher-edge.com`）と、Cloudflare が示す TXT（`_cf-custom-hostname.fukuoka`）・CNAME（`_acme-challenge.fukuoka`）を登録する。Google の OAuth クライアントの承認済みリダイレクト URI に `https://fukuoka.todokede.jp/auth/callback` を追加する。
