# My Engineering Notes

Vite + React + TypeScriptで構築したエンジニア向けブログ。GitHub Pagesにデプロイし、Markdown投稿をスレッド単位でまとめて閲覧できます。UIはMaterial UIのみで構成しています。

## 画面

- `Posts`(ホーム): すべての投稿を新しい順で並べたタイムライン。
- `Threads`: スレッド一覧。チャレンジやカテゴリ単位でまとめた投稿を閲覧。

## 開発環境

```bash
npm install
npm run dev
```

## 投稿の追加

1. `content/<thread>/<slug>.md` を作成。フォルダ名がスレッドIDになります。
2. 冒頭にFrontmatterを記述:

```
---
title: "タイトル"
date: "2025-01-10"
excerpt: "任意: 一覧で表示する短い概要"
threadTitle: "任意: スレッド表示名"
threadDescription: "任意: スレッド説明"
---
本文をMarkdownで記述
```

- `excerpt`/`threadDescription` は省略可能です。`excerpt` が無い場合は本文から自動生成され、`threadDescription` が無いスレッドは最初の投稿の概要を利用します。

3. ファイルをコミットすると、ビルド時に自動的に読み込まれます。

## GitHub Pagesデプロイ

`vite.config.ts` の `base` は `/<repo-name>/` に合わせて調整してください。GitHub Pagesの`gh-pages`ブランチへ公開する場合:

```bash
npm run deploy
```

内部的に`npm run build`実行後、`dist`フォルダを`gh-pages`ブランチへpushします。初回はリポジトリ設定でPagesのブランチを`gh-pages`に変更してください。

## 技術スタック

- Vite + React + TypeScript
- Material UI (`@mui/material`, `@emotion/*`)
- React Router v6
- Markdownは`import.meta.glob`で取り込み、シンプルな独自パーサで描画

