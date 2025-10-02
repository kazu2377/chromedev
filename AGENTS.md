q# Repository Guidelines

## Project Structure & Module Organization
- `index.html` は本番公開用の LP。レビュー後の変更は必ずここへ反映します。
- `index_test.html` は開発用ドラフト。新機能やレイアウト調整はまずこちらで検証し、合格後 `index.html` に移植してください。
- メディア資産（`head_logo.png`、`logo.png`、`キャプチャ*.PNG`、`20251001_1426_*.mp4`）はリポジトリ直下に配置し、相対パスで参照します。大容量ファイルは 1GB を超えないよう再エンコード・圧縮を行ってください。

## Build, Test, and Development Commands
- `python3 -m http.server 3000` : ルートディレクトリで実行し、ローカル検証用の簡易サーバーを起動します。
- `npx live-server --port=3000` : ホットリロード付きサーバー。UI 調整やレスポンシブ確認に使用します。
- `npx prettier --check "*.{html,md}"` : フォーマット差分を検査します。整形が必要な場合は `--write` を併用してください。

## Coding Style & Naming Conventions
- HTML5 のセマンティック要素と Tailwind CSS ユーティリティを優先します。インラインスタイルは避け、共通ルールは必要に応じて Tailwind プラグイン拡張で管理します。
- インデントは 2 スペース統一。`<script>` セクションは最小限とし、複雑なロジックには日本語コメントで目的を記述します。
- 新規アセットは英語ケバブケース（例: `hero-student-showcase.webp`）で命名し、キャッシュ制御のためバージョン番号を付ける場合は末尾に `-v2` などを追加します。

## Testing Guidelines
- 自動テストは未整備のため、主要ブレークポイント（375px / 768px / 1280px）で手動確認します。
- JavaScript の挙動（アコーディオン、スライダー、自動再生）をブラウザ最新バージョンの Chrome / Firefox / Safari で検証し、差異があれば PR 内で共有してください。
- 重要な UI 変更を行った場合は、手動テスト結果やスクリーンショット、またはショート動画を記録します。

## Commit & Pull Request Guidelines
- コミットメッセージは短い命令形（日本語 / 英語可）を使用し、1 つの意図に絞ってください。例: `Update hero CTA color` / `ヘッダーのナビ文言を調整`。
- PR には目的、主要変更点、確認結果（スクリーンショット・録画）、関連 Issue を記載します。`index_test.html` と `index.html` の整合性状況も明記してください。
- レビュー後は指摘への対応状況をチェックリスト化し、再レビューの際に進捗がわかるようコメントします。

## Asset & Configuration Tips
- 画像は WebP または最適化 PNG を推奨し、1 ファイル 1MB 以下を目安とします。動画は H.264 / 1080p 以下でエンコードし、可能であればストリーミングサービスへのオフロードを検討してください。
- 簡易サーバー運用のため、環境変数は使用していません。今後導入する場合は `.env.example` を追加し、機密情報をコミットしないよう注意してください。
