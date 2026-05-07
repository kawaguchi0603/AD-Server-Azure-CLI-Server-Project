# Azure-Mid-Server-Project

# ネットワーク設計図

【IP設計の意図】

NIC1 (Bridged): ローカルPCおよびAzureへの外部通信用。DHCPにて動的取得。

NIC2 (Internal): 内部サーバー（AD/DB等）とのセキュアな通信用。

Network: 192.168.10.0/24

GW-SRV-01: 192.168.0.187 (Static)

VLAN分離のシミュレーション: 外部からのRDPトラフィックと、内部のサーバー間トラフィックを物理的（仮想的）に分離し、セキュリティを強化。
