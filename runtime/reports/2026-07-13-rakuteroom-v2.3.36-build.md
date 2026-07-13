# RakuteRoom v2.3.36 ビルド記録

- 日時: 2026-07-13T10:25:31+09:00
- 対象アプリ: RakuteRoom
- 実体パス: `@RakuteRoom/`
- バージョン: 2.3.36

## 内容

- CPU使用率低減変更を含めて `package.json` / `package-lock.json` を `2.3.36` に更新。
- バージョン名付きビルドを作成。
- 古いビルドは削除せず保持。

## 生成物

- `@RakuteRoom/dist/RakuteRoom-2.3.36-win32-x64/RakuteRoom-2.3.36.exe`
- サイズ: 211,136,512 bytes

## 検証

- `node --check renderer\renderer.js`: 成功
- `git diff --check`: 成功
- `npm run pack:win:versioned`: 成功
- `node -p "require('./package.json').version + ' / ' + require('./package-lock.json').version"`: `2.3.36 / 2.3.36`

## 備考

- 前回 `electron-builder` は長時間終了しなかったため、今回はバージョン名が明記される `electron-packager` の `pack:win:versioned` を使用した。
