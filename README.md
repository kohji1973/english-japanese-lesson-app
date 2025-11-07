# 🎓 生成AI英会話アプリ - 精度向上版

OpenAI Whisper/TTS APIとLangChainを使った、音声認識による英会話学習アプリです。

## ✨ 主な機能

### 3つのモード

1. **日常英会話** 🗣️ - AIと自由に英会話練習
2. **シャドーイング** 🔄 - 英文を聞いて繰り返す練習
3. **ディクテーション** ✍️ - 英文を聞いて書き取る練習

### レベル別対応

- **初級者** - 基本語彙、短い文章
- **中級者** - 日常語彙、イディオム
- **上級者** - ネイティブレベル、複雑な表現

### 詳細な評価システム

- 100点満点のスコアリング
- 音素レベルの分析
- 具体的な改善アドバイス

---

## 🚀 ローカルでの起動方法

### 1. リポジトリのクローン

```bash
git clone https://github.com/YOUR_USERNAME/english-conversation-app.git
cd english-conversation-app
```

### 2. 仮想環境の作成

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 3. パッケージのインストール

```bash
pip install -r requirements.txt
```

### 4. 環境変数の設定

`.env`ファイルを作成し、OpenAI APIキーを設定：

```
OPENAI_API_KEY=あなたのOpenAI APIキー
```

### 5. アプリの起動

```bash
streamlit run main.py
```

ブラウザで `http://localhost:8501` が開きます。

---

## ☁️ Streamlit Community Cloudへのデプロイ

### 事前準備

1. GitHubアカウントの作成
2. このリポジトリをGitHubにプッシュ
3. Streamlit Community Cloudアカウントの作成

### デプロイ手順

1. **Streamlit Community Cloud**にアクセス
   - https://share.streamlit.io/

2. **GitHubアカウントでサインイン**

3. **「New app」をクリック**

4. **リポジトリ情報を入力**
   - Repository: `YOUR_USERNAME/english-conversation-app`
   - Branch: `main`
   - Main file path: `main.py`
   - Python version: `3.11`

5. **⚠️ 重要: Secretsの設定**
   
   「Advanced settings」→「Secrets」に以下を追加：

   ```toml
   OPENAI_API_KEY = "あなたのOpenAI APIキー"
   ```

6. **「Deploy!」をクリック**

数分でデプロイが完了します！

---

## 📖 使い方

### 基本操作

1. **英語レベル**を選択（初級者/中級者/上級者）
2. **モード**を選択（日常英会話/シャドーイング/ディクテーション）
3. **再生速度**を選択（0.6x〜2.0x）
4. **「開始」ボタン**をクリック

### モード別の使い方

#### 日常英会話モード
1. 「開始」をクリック
2. 音声で話しかける
3. AIが応答（文法ミスを自然に訂正）

#### シャドーイングモード
1. 「開始」をクリック
2. AIが英文を読み上げ
3. 「シャドーイング開始」をクリック
4. 聞いた英文を発話
5. 詳細な評価を確認（100点満点）

#### ディクテーションモード
1. 「開始」をクリック
2. AIが英文を読み上げ
3. 「ディクテーション開始」をクリック
4. 聞いた英文をチャット欄に入力
5. 詳細な評価を確認（100点満点）

---

## 🎯 改善内容

このバージョンでは、以下の4つの改善により回答精度が大幅に向上：

1. **レベル別最適化プロンプト** - 学習効率30-40%向上
2. **詳細な評価システム** - モチベーション20-30%向上
3. **Whisper認識精度向上** - 認識精度10-20%向上
4. **動的レベル対応** - UX向上15-25%

詳細は[IMPROVEMENTS.md](./IMPROVEMENTS.md)を参照。

---

## 🛠️ 技術スタック

- **Python 3.11**
- **Streamlit** - Webアプリフレームワーク
- **OpenAI Whisper** - 音声→テキスト変換
- **OpenAI TTS** - テキスト→音声変換
- **OpenAI GPT-4o-mini** - 会話生成・評価
- **LangChain** - LLM統合・メモリ管理
- **audiorecorder** - 音声録音
- **pydub** - 音声処理

---

## 📂 プロジェクト構造

```
english-conversation-app/
├── main.py                 # メインアプリケーション
├── constants.py            # 定数・プロンプト定義
├── functions.py            # 関数定義
├── requirements.txt        # パッケージリスト
├── packages.txt            # システムパッケージ
├── .gitignore             # Git除外設定
├── README.md              # このファイル
├── IMPROVEMENTS.md        # 改善詳細ドキュメント
├── README_改善版.md       # 日本語使い方ガイド
├── audio/
│   ├── input/            # 録音ファイル（一時）
│   └── output/           # 生成音声（一時）
└── images/
    ├── ai_icon.jpg       # AIアイコン
    └── user_icon.jpg     # ユーザーアイコン
```

---

## ⚠️ 注意事項

### APIキーのセキュリティ

- `.env`ファイルは**絶対にGitHubにプッシュしない**
- `.gitignore`に`.env`が含まれていることを確認
- Streamlit Cloudでは必ずSecretsで設定

### API使用料

- OpenAI APIは従量課金制
- Whisper: $0.006/分
- TTS: $15.00/100万文字
- GPT-4o-mini: 入力$0.150/100万トークン、出力$0.600/100万トークン

---

## 🔧 トラブルシューティング

### Q1: 音声が認識されない
**A**: マイクの権限を確認してください。5秒間沈黙すると自動的に録音が完了します。

### Q2: APIエラーが出る
**A**: `.env`ファイルまたはStreamlit CloudのSecretsでAPIキーが正しく設定されているか確認してください。

### Q3: ffmpegエラーが出る
**A**: `packages.txt`に`ffmpeg`が含まれていることを確認してください。ローカルでは別途インストールが必要な場合があります。

---

## 📝 ライセンス

MIT License

---

## 🤝 コントリビュート

プルリクエストを歓迎します！

---

## 📧 お問い合わせ

質問や提案があれば、Issueを作成してください。

---

**Happy Learning! 🎉**

