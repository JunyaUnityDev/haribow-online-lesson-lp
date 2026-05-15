# HARIBOW Online Lesson 募集LP

HARIBOW Online Lesson の **受講者募集用ランディングページ**。Jekyll + GitHub Pages。

## 公開URL

https://junyaunitydev.github.io/haribow-online-lesson-lp/

## ローカルプレビュー

```bash
cd ~/projects/haribow/haribow-online-lesson-lp
bundle install   # 初回のみ
bundle exec jekyll serve
```

→ http://localhost:4000/haribow-online-lesson-lp/

## ファイル構成

```
haribow-online-lesson-lp/
├── _config.yml              ← Jekyll 設定
├── Gemfile                  ← 依存
├── _layouts/default.html    ← 共通レイアウト
├── _includes/
│   ├── header.html          ← ヘッダー（LP用CTAボタン付き）
│   └── footer.html
├── assets/
│   ├── css/main.scss        ← 既存記事サイトのCSS+LP固有スタイル
│   └── images/junya.jpg     ← JUNYAプロフィール写真
├── index.html               ← LP本体（全セクション）
└── .github/workflows/jekyll.yml ← GitHub Actions デプロイ
```

## セクション構成（MVP）

1. ヒーロー（キャッチコピー + CTA）
2. 講師紹介（実績・出演歴）
3. サービス内容（動画提出 / LINE練習bot / 月次配信記事）
4. 料金（月額¥3,000）
5. 申込CTA

## 編集ガイド

### 文言修正
- ヒーローコピー、サービス内容、料金等は `index.html` を直接編集
- 受賞歴・出演歴の追加削除も `index.html` の該当セクション

### デザイン調整
- カラー・サイズ等は `assets/css/main.scss` の末尾 LP 関連セクション
- カラー変数は SCSS 冒頭で定義（既存記事サイトと共通）

### 記事サイトのテーマ一覧チラ見せ
- `index.html` の `.services-articles ul` 内のリスト。本文URLは載せない方針
- 新規記事が増えたら手動で追加

## 申込フォーム

現状プレースホルダー（`href="#"`）。Google Form を作成したら、`index.html` 末尾 `.apply-cta` の `href` を差し替える。

## 親プロジェクトとの連携

- 親 CLAUDE.md: `~/projects/haribow/CLAUDE.md`
- 既存記事サイト（受講者向け）: `~/projects/haribow/haribow-online-lesson-articles/`
- LP は外向き、記事サイトとは独立運用
