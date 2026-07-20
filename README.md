# イラストスケジュール手帖 🎨

イラスト制作のスケジュール管理・練習記録・キャラクター育成を1つにまとめた、インストール可能なWebアプリ（PWA）です。ビルド不要・依存ライブラリなしの単一HTMLで動きます。

## 主な機能

- 📅 **スケジュール**：カレンダーで制作予定・工程チェック・作業時間を記録
- ✏️ **練習モード**：大／小カテゴリ（例：体 → 手）ごとに練習時間を記録し、グラフで振り返り
- 💗 **キャラ**：8人の部員との好感度・会話イベント・プレゼント
- 🖼️ **部活**：サークルランク・展示会・展示リスト
- ✅ **完成済み** / 📊 **統計**：作品数の推移・制作時間の累計・実績バッジ・思い出アルバム
- ⚙️ **設定**：背景テーマ・ダークモード・セーブスロット・バックアップ

データはすべて端末内（localStorage）に保存されます。サーバー送信はありません。

## 公開のしかた（GitHub Pages）

1. GitHubで新しいリポジトリを作成します（例：`irasuto-techo`）。Publicにしてください。
2. このフォルダの中身を**まるごと**そのリポジトリに入れて push します。

   ```bash
   cd irasuto-techo          # このフォルダ
   git init
   git add .
   git commit -m "イラストスケジュール手帖 初版"
   git branch -M main
   git remote add origin https://github.com/<あなたのユーザー名>/irasuto-techo.git
   git push -u origin main
   ```

3. GitHubのリポジトリ画面で **Settings → Pages** を開きます。
4. **Build and deployment** の **Source** を **Deploy from a branch** にし、Branch を **main / (root)** に設定して **Save**。
5. 1〜2分待つと `https://<ユーザー名>.github.io/irasuto-techo/` で公開されます。

## スマホにアプリとして入れる

- **iPhone（Safari）**：公開URLを開く → 共有ボタン → 「ホーム画面に追加」
- **Android（Chrome）**：公開URLを開く → メニュー → 「アプリをインストール」

一度開けばオフラインでも起動します（Service Workerがアプリ本体をキャッシュします）。

## 中身

```
├── index.html              アプリ本体（単一HTML・これだけで動く）
├── manifest.webmanifest    PWA設定（名前・アイコン・表示モード）
├── sw.js                   Service Worker（オフライン対応・更新管理）
├── icons/                  アプリアイコン各サイズ
├── .nojekyll               GitHubのJekyll処理を無効化
└── README.md               このファイル
```

## アプリを更新したとき

新しい `index.html` に差し替えたら、`sw.js` の先頭にある

```js
const CACHE_VERSION = "v1";
```

の数字を `"v2"` のように上げてから push してください。利用者の端末で古いキャッシュが自動的に新しいものに置き換わります。

## 動作環境

- モダンブラウザ（iOS Safari / Chrome / Edge / Firefox）
- 外部ネットワーク接続・アカウント登録・ビルド作業は不要
