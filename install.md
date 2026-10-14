# moomoo ニュース解読 Stock Digest Skill インストールガイド

本ドキュメントは、moomoo ニュース解読 Stock Digest Skill を Claude Code 環境へ導入する手順を説明します。

## 前提条件

- Claude Code CLI がインストール済みであること
- moomoo OpenAPI の認証設定が完了していること
- UNIX 系コマンド(curl, openssl, date)が利用可能であること(Windows の場合は Git Bash 環境を推奨)

## インストール手順

### Step 1: リポジトリのクローン

以下のコマンドをターミナルで実行し、Skill ファイルをローカルに取得します。

```bash
git clone https://github.com/alicialin0420/moomoo-stock-digest.git
```

### Step 2: Skill ディレクトリへの配置

クローンした `SKILL.md` を Claude Code の Skill 格納ディレクトリに配置します。

#### macOS / Linux の場合

```bash
mkdir -p ~/.claude/skills/moomoo-stock-digest
cp moomoo-stock-digest/SKILL.md ~/.claude/skills/moomoo-stock-digest/
```

#### Windows の場合

```powershell
New-Item -ItemType Directory -Force -Path $env:USERPROFILE\.claude\skills\moomoo-stock-digest
Copy-Item moomoo-stock-digest\SKILL.md $env:USERPROFILE\.claude\skills\moomoo-stock-digest\
```

### Step 3: 設定の反映

Claude Code を再起動する、または新しいセッションを開始することで、Skill が認識されます。

### Step 4: 動作確認

Claude Code 上で以下のように呼び出し、Skill が反応することを確認します。

```
US.TSLA の最新ニュースを解読して
```

または

```
HK.09988 の stock digest を作成して
```

## アンインストール手順

Skill ディレクトリから `SKILL.md` を削除してください。

```bash
rm -rf ~/.claude/skills/moomoo-stock-digest
```

## トラブルシューティング

### Skill が認識されない場合

- `~/.claude/skills/moomoo-stock-digest/` ディレクトリが存在するか確認してください
- ディレクトリ内に `SKILL.md` が存在するか確認してください
- ディレクトリ名が `moomoo-stock-digest` になっているか確認してください
- Claude Code を完全に再起動してください

### API 認証エラーが出る場合

- moomoo OpenAPI の認証設定が完了しているか確認してください
- OpenD が起動済みであるか確認してください

### ニュースが取得できない場合

- 指定銘柄コードが正しい形式(US.TSLA / HK.09988 等)になっているか確認してください
- 当該銘柄に近日中のニュースが存在するか確認してください

## サポート

不具合や改善要望は本リポジトリの Issue よりご報告ください。
