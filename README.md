# 汎道具規格協会 / Pan Tool Standards Association

チンパンジーの道具を JIS 規格票の体裁で記述する、架空の標準化団体のコンセプトサイト。

## 構成

ビルド工程なし。素の HTML と CSS のみ。JavaScript は 1 バイトも使用していない。

```
public/            公開対象（Cloudflare Pages の出力ディレクトリ）
├─ index.html      協会について
├─ standards.html  規格一覧及び条文（PTS-001 / PTS-014）
├─ regional.html   地域規格と整合化（12地域）
├─ committee.html  技術委員会と審議手続
├─ assets/base.css 全ページ共通のスタイル
└─ _headers        Cloudflare Pages 用のヘッダー設定
```

`_headers` では `script-src 'none'` を指定している。サイトの奥付に「本サイトはスクリプトを使用していない」と
記載しているため、それを HTTP ヘッダーでも強制している。

## デプロイ

Cloudflare Pages（GitHub 連携）。`main` への push で自動デプロイされる。

| 設定項目 | 値 |
|---|---|
| Framework preset | None |
| Build command | （空欄） |
| Build output directory | `public` |

`wrangler.toml` の `pages_build_output_dir` にも同じ値を書いてある。

## ローカル確認

`serve.mjs`（`.gitignore` で除外）は依存ゼロの静的サーバーで、`public/_headers` と同じヘッダーを返す。

```
node serve.mjs   # http://localhost:4180/
```

## 使用している主な CSS

`@layer` / `@view-transition` / `animation-timeline: view()` / コンテナクエリ / CSS カウンタ。
いずれも非対応環境では演出が発生しないだけで、規格票としての表示と可読性は保たれる。

## 制作

「ふざけてるけど真面目」をテーマに Anthropic Claude Opus 5 が制作。
同じテーマで OpenAI GPT-5.6 Sol が制作した姉妹サイトは
<https://banana-needs-no-reason.kyotomalmal25.workers.dev/>。
