# Alpha Orbits

衛星軌道解析ツール。TLEまたはケプラー6要素から衛星軌道を伝播・可視化します。

## 機能

- **衛星追加** — TLE直接入力 / Celestrakデータベース / ローカルファイル / ケプラー6要素
- **軌道伝播** — Two-body / J2摂動 / SGP4（Skyfield、IAU 2006/2000A準拠）
- **2D表示** — 地上トラック・現在位置（Matplotlib + Cartopy、ズーム/パン対応）
- **3D表示** — 軌道・地球テクスチャ・自転（PyOpenGL、ドラッグ回転）
- **アニメーション** — 再生速度可変（最大100,000倍速）、タイムラインスライダー
- **CSVエクスポート** — 緯度経度高度 / ケプラー要素 / ECI / ECEF を時系列出力
- **CLI/GUIミラー** — GUI操作をPythonスクリプトとして記録・再実行可能

## 動作環境

| OS | 配布形式 | 備考 |
|---|---|---|
| Windows 10/11 | `.exe`（ZIPに同梱） | OpenGL 2.0以上推奨。未対応GPUでは3Dビューをテキスト表示に置換 |
| macOS 12以降 | `.app`（ZIPに同梱） | Intel/Apple Silicon両対応（x86_64、Rosetta 2経由でM1/M2/M3でも動作） |

**OpenGL 2.0について**
- GeForce / Radeon / Intel HD Graphics 第4世代以降など、標準的なGPUであれば問題ありません
- OpenGL 2.0 未対応の環境では、3DビューをOpenGLを使わないメッセージ表示に置換します（アプリ自体は起動します）

## ダウンロード

[Releases](../../releases) から最新版をダウンロードしてください。

| ファイル名 | 対象 |
|---|---|
| `alpha-orbits-windows-vX.X.X.zip` | Windows 10/11 |
| `alpha-orbits-macos-vX.X.X.zip` | macOS 12以降（Intel / Apple Silicon） |

**Windows:** ZIPを展開して `alpha-orbits.exe` を実行（インストール不要）

**macOS:** ZIPを展開して `Alpha Orbits.app` をアプリケーションフォルダに移動。
初回起動時は右クリック→「開く」→「開く」の操作が必要です（Gatekeeper警告の回避）。

> **注意:** Releasesページに表示される `Source code (zip/tar.gz)` はGitHubが自動生成するファイルで、アプリ本体・ソースコードは含まれていません。上記の `alpha-orbits-windows-*.zip` または `alpha-orbits-macos-*.zip` をダウンロードしてください。

## 開発フェーズ

| バージョン | 状態 | 内容 |
|---|---|---|
| v0.1 | **公開中** | 衛星追加・軌道伝播・2D/3D表示・アニメーション・CSVエクスポート・CLI同期 |
| v0.2 | 開発予定 | 地上局・可視解析 |
| v0.3 | 開発予定 | センサ |
| v1.0 | 開発予定 | ライセンス認証・正式リリース |

## 技術スタック

| 用途 | ライブラリ |
|---|---|
| GUI | PySide6 (LGPL) |
| 2D地図 | Matplotlib + Cartopy |
| 3D地球 | PyOpenGL + QOpenGLWidget（要: OpenGL 2.0以上） |
| 軌道計算・座標変換 | Skyfield (IAU 2006/2000A) |
