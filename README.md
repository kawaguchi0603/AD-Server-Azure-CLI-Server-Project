# Windows-AD-Server+Azure CLI Server-Project

1. プロジェクト概要
- VirtualBox 上に Windows Server 2022 を構築

- Primary を DC として構築

- Secondary をドメイン参加

- Primary に Azure CLI を導入

- OpenSSH Server を構築し、ローカル PC から遠隔操作

- Azure CLI で Azure リソース操作可能な踏み台サーバーを構築

2. 構成図（テキストで OK）

[Local PC] --SSH--> [Primary (DC + Azure CLI)]
                         |
                         +-- Domain --> [Secondary]
## 3. 実装手順

### 3-1. VirtualBox で Windows Server 2022 VM を作成
- Primary（DC 用）
- Secondary（メンバーサーバー）
- ネットワーク：NAT + Host-Only

### 3-2. Primary をドメインコントローラーに昇格
- AD DS をインストール
- 新規フォレスト lab.local を作成

### 3-3. Secondary をドメインに参加
- DNS を Primary に設定
- lab.local に参加

### 3-4. Primary に OpenSSH Server を導入
（コマンドを記載）

### 3-5. Primary に Azure CLI をインストール
（手順と確認コマンドを記載）

### 3-6. ローカル PC から SSH 接続
（接続コマンドを記載）

4. 動作確認
SSH 接続成功のスクショ

az --version

az login

Azure リソース一覧取得の結果
<img width="1895" height="696" alt="image" src="https://github.com/user-attachments/assets/a444c93b-4d39-4f0e-8fcd-f3024e4c9e65" />
