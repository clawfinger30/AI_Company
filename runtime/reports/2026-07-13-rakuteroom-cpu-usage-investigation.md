# RakuteRoom CPU使用率調査・低減変更レポート

- 日時: 2026-07-13T10:05:31+09:00
- 対象アプリ: RakuteRoom
- 実体パス: `@RakuteRoom/`
- 変更種別: CPU負荷低減

## 調査結果

5秒サンプリングで、CPU使用率上位は `RakuteRoom` の renderer プロセスだった。

- default: renderer が約 8-9%
- 母: renderer が約 8-9%
- 父: renderer が約 8-9%
- main / gpu-process は主因ではなかった

複数アカウントで楽天ページを開いた webview renderer が残り、非アクティブでもCPUを使い続けている可能性が高い。

## 実装内容

- `renderer/renderer.js`
  - ログ表示更新を `requestAnimationFrame` 毎回更新から 250ms 間隔の debounce に変更。
  - 未使用 webview を定期的に `about:blank` へ戻す `setupWebviewCpuCleanup()` を追加。
  - 自動化中の webview はアンロード対象外。
  - ログイン中の `followWebview` はアンロード対象外。
  - 表示中 webview は、ウィンドウが非フォーカスかつ3分以上無操作の場合のみアンロード。
  - 起動10秒後にも非アクティブ webview を一度整理。

## 検証

- `node --check renderer\renderer.js`: 成功
- `git diff --check`: 成功
- `npm run pack:portable`: 成功。`dist\RakuteRoom-win32-x64\RakuteRoom.exe` を生成。

## 注意

- 現在起動中の `dist\RakuteRoom-2.3.35-x64.exe` プロセスにはこの変更は反映されない。変更反映には新しい梱包版の起動、または次回ビルド版への差し替えが必要。
- 実測CPU低下は、変更反映後のアプリを起動して同じ5秒サンプリングで確認する必要がある。
