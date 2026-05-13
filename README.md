# Azure-Mid-Server-Project

# 1.プロジェクト概要

Azureを操作する踏み台サーバーを作成し、踏み台サーバーの冗長化を行うまでをプロジェクトとし構築しました。
Node1へAzure CLIをインストールし、ADを構築。
Node2でドメインへ参加しFailover Clustering (WSFC) 実装のため、iSCSIターゲットサーバーを構築。
2Nodeをクラスターへ追加しフェールオーバーを機能させる。

# 2.システム構成図

- プライマリサーバー(Node1):Windows Server2022、Azure CLI、Active Directory、iSCSI
- セカンダリサーバー(Node2):Windows Server2022、Azure CLI

# 3.ネットワーク

**設計図**

【IP設計の意図】

NIC1 (Bridged): ローカルPCおよびAzureへの外部通信用。DHCPにて動的取得。

NIC2 (Internal): 内部サーバー（AD/DB等）とのセキュアな通信用。

Network: 192.168.10.0/24

GW-SRV-01: 192.168.0.187 (Static)

VLAN分離のシミュレーション: 外部からのRDPトラフィックと、内部のサーバー間トラフィックを物理的（仮想的）に分離し、セキュリティを強化。


# Azure CLI

【なぜ、Azure CLIをインストールするのか】

・自動化の促進: 「GUI（ポータル画面）での操作はミスが起きやすいため、CLIやスクリプトによる構成管理を導入した」

・運用効率: 「踏み台サーバーから直接コマンドでリソースの状態を確認・操作できる体制を整えた」

# AD

【Active Directory構築の目的】

・統合管理: 複数サーバーのユーザー権限やセキュリティポリシー（GPO）を一括管理するため。

・クラスター構成の必須条件: Windows Server Failover Clustering (WSFC) を実装するための、認証基盤としてのドメイン環境を構築。

・ハイブリッドIDの基礎: 将来的にオンプレミスのADを Azure Entra ID (旧Azure AD) と同期させ、ハイブリッド環境をシミュレートするための足がかりとする。

