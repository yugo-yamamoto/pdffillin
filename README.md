# PDF 文字入れ

ブラウザだけで PDF にテキストを書き足せるツールです。PC とスマホで使えます。
PDF はブラウザの中だけで処理され、サーバーには送信されません。

**公開ページ:** https://yugo-yamamoto.github.io/pdffillin/

## できること

- PDF を開く（ボタン、またはドラッグ＆ドロップ）
- ページの好きな位置にテキストを追加する（複数行可）
- 文字サイズを選ぶ（6〜72pt）
- テキストを複製・移動・削除する
- テキストを書き込んだ PDF を保存する（`元の名前_記入済.pdf`）

フォントはゴシック体（BIZ UDゴシック）、色は黒 100% のみです。

## 使い方

### PC

| 操作 | 方法 |
|---|---|
| 追加 | ページをクリック |
| 複製（すぐ下に） | `Ctrl` + `D` |
| 選択状態にする | `Esc` |
| 移動 | 左上の ■ をドラッグ ／ `Alt` + ドラッグ ／ 選択中に `←↑→↓`（`Shift` で 10pt） |
| 削除 | 選択中に `Delete` ／「選択を削除」ボタン |
| 保存 | `Ctrl` + `S` ／「PDFを保存」ボタン |

### スマホ

| 操作 | 方法 |
|---|---|
| 追加 | 「＋テキスト」を押してから、置きたい場所をタップ |
| 選択 | テキストをタップ |
| 移動 | 選択中のテキストを指でドラッグ |
| 編集 | 選択中のテキストをもう一度タップ |
| サイズ変更・複製・削除 | 選択時に出るメニュー（A− / A＋ / 複製 / 削除 / 完了） |

## ローカルで動かす

フォントなどを読み込むため、ファイルを直接開くのではなく Web サーバー経由で開いてください。

```bash
uv run --no-project python -m http.server 8000
# → http://localhost:8000/
```

## 構成

| ファイル | 内容 |
|---|---|
| `index.html` | アプリ本体（HTML / CSS / JS） |
| `fonts/BIZUDGothic-Regular.ttf` | 表示と PDF 埋め込み用フォント |
| `lib/hb-subset.wasm` | 保存時に、使った文字だけをフォントから切り出す（harfbuzz） |

使用ライブラリ（CDN から読み込み）:

- [PDF.js](https://mozilla.github.io/pdf.js/) 4.4.168 — PDF の表示
- [pdf-lib](https://pdf-lib.js.org/) 1.17.1 + @pdf-lib/fontkit 1.1.1 — PDF への書き込み
- [harfbuzzjs](https://github.com/harfbuzz/harfbuzzjs) 0.4.13 — フォントのサブセット化

## ライセンス

- BIZ UDゴシック: SIL Open Font License 1.1（`fonts/OFL.txt`）
- harfbuzz: MIT License
