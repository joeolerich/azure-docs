---
ms.author: cherylmc
author: cherylmc
ms.date: 09/26/2023
ms.service: vpn-gateway
ms.topic: include
---

When you create a virtual network gateway, you need to specify the gateway SKU that you want to use. Select the SKU that satisfies your requirements based on the types of workloads, throughput, features, and SLAs. For virtual network gateway SKUs in Azure Availability Zones (*AZ SKUs), see [Zone-redundant gateway SKUs](../articles/vpn-gateway/about-zone-redundant-vnet-gateways.md).

###  <a name="benchmark"></a>Gateway SKUs by tunnel, connection, and throughput

[!INCLUDE [Aggregated throughput by SKU](./vpn-gateway-table-gwtype-aggtput-include.md)]

> [!NOTE]
> * For information about working with the legacy gateway SKUs (Basic, Standard, and HighPerformance), see [Working with VPN gateway SKUs (legacy SKUs)](../articles/vpn-gateway/vpn-gateway-about-skus-legacy.md).
> * For ExpressRoute gateway SKUs, see [Virtual Network Gateways for ExpressRoute](../articles/expressroute/expressroute-about-virtual-network-gateways.md).
> * For Availability Zone SKUs (*AZ SKUs), see [About Zone redundant gateway SKUs](../articles/vpn-gateway/about-zone-redundant-vnet-gateways.md).
>

###  <a name="feature"></a>Gateway SKUs by feature set

The new VPN gateway SKUs streamline the feature sets offered on the gateways:

| **SKU**| **Features**|
| ---    | ---         |
|**Basic** (**)   | **Route-based VPN**: 10 tunnels for S2S/connections; no RADIUS authentication for P2S; no IKEv2 for P2S<br>**Policy-based VPN**: (IKEv1): 1 S2S/connection tunnel; no P2S|
| **All Generation1 and Generation2 SKUs except Basic** | **Route-based VPN**: up to 100 tunnels (*), P2S, BGP, active-active, custom IPsec/IKE policy, ExpressRoute/VPN coexistence |
|        |             |

(*) You can configure "PolicyBasedTrafficSelectors" to connect a route-based VPN gateway to multiple on-premises policy-based firewall devices. Refer to [Connect VPN gateways to multiple on-premises policy-based VPN devices using PowerShell](../articles/vpn-gateway/vpn-gateway-connect-multiple-policybased-rm-ps.md) for details.

(\*\*) The Basic SKU is considered a legacy SKU. The Basic SKU has certain feature limitations. You can't resize a gateway that uses a Basic SKU to another SKU, you must instead change to a new SKU, which involves deleting and recreating your VPN gateway. You can't deploy a Basic SKU to a VNet that uses IPv6 address space. The Basic SKU can only be configured using PowerShell or Azure CLI.

###  <a name="workloads"></a>Gateway SKUs - Production vs. Dev-Test Workloads

Due to the differences in SLAs and feature sets, we recommend the following SKUs for production vs. dev-test:

| **Workload**                       | **SKUs**               |
| ---                                | ---                    |
| **Production, critical workloads** | All Generation1 and Generation2 SKUs except Basic |
| **Dev-test or proof of concept**   | Basic (**)                 |
|                                    |                        |

(\*\*) The Basic SKU is considered a legacy SKU and has feature limitations. Verify that the feature that you need is supported before you use the Basic SKU. Additionally, the Basic SKU can only be configured using Azure CLI or PowerShell.

If you are using the old SKUs (legacy), the production SKU recommendations are Standard and HighPerformance. For information and instructions for old SKUs, see [Gateway SKUs (legacy)](../articles/vpn-gateway/vpn-gateway-about-skus-legacy.md).
