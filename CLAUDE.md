# HARIBOW Online Lesson 募集LP

未受講者向けの **募集用ランディングページ**。2026/05/15 着手。

## 立ち位置

| サイト | 役割 | ターゲット | URL |
|---|---|---|---|
| **このLP** | 募集・申込誘導 | 未受講者（外向き） | `/haribow-online-lesson-lp/` |
| 既存記事サイト | 教材記事配信 | 受講者（内向き） | `/haribow-online-lesson-articles/` |

**意図的に分離**しています。LP から記事サイトへの URL リンクは設置しません（受講者限定価値の保護）。

## 技術スタック

- Jekyll 4.3 + GitHub Pages（既存記事サイトと統一）
- SCSS は既存記事サイトのコピー + LP固有スタイルを末尾 append
- カラー: ダークブラウン + ベージュ + テラコッタ（HARIBOWブランド）
- スマホ優先のレスポンシブ（ブレークポイント 768px）

## デザインコンセプト

- 既存記事サイトと同トーン（同じ CSS 変数・フォント Hannari / Noto Serif JP / Noto Sans JP）
- 「感情論ではなく、構造的に理解する」という既存記事サイトの方針を踏襲
- 習慣化軸のキャッチコピー（続けられる / 孤独ケア）

## CTA 設計

- ヘッダー右上に小さな「申込はこちら」ボタン（常時表示）
- ヒーロー直下にメインCTAボタン
- 最終セクション `#apply` にコンバージョン誘導ボタン
- 全部 Google Form を指す想定（URL は後で差し替え）

## 編集パターン

| やりたいこと | 編集箇所 |
|---|---|
| ヒーローコピー変更 | `index.html` の `.hero-catch` `.hero-sub` |
| 講師実績更新 | `index.html` の `.creds-list` 内 ul |
| サービス内容変更 | `index.html` の `.services-grid` |
| 料金変更 | `index.html` の `.pricing-amount` `.pricing-list` |
| 記事テーマチラ見せ追加 | `index.html` の `.services-articles ul` |
| 申込フォームURL設定 | `index.html` 末尾の `.apply-cta` の href |
| 色・余白調整 | `assets/css/main.scss` 末尾 LP セクション |

## デプロイ

GitHub Actions（`.github/workflows/jekyll.yml`）が main push 時に自動ビルド・公開。

```bash
git add .
git commit -m "..."
git push
```

## 親プロジェクトとの参照

- 親 CLAUDE.md: `~/projects/haribow/CLAUDE.md`
- 兄弟: `haribow-online-lesson-articles/`（記事サイト）、`online_lesson/`（GAS）、`insta_stories/`（ストーリー生成）

## 既存記事サイトの noindex 化（別タスク・推奨）

LP 立ち上げに伴い、既存記事サイトは検索エンジンから隠す方が良い：

- 現状 `_config.yml` に noindex 設定なし、`robots.txt` も存在しない
- 推奨: `_layouts/default.html` に `<meta name="robots" content="noindex">` 追加 or `robots.txt` で全クロール禁止
- URL 直打ち / LINE 配信URL からのアクセスは引き続き可能
