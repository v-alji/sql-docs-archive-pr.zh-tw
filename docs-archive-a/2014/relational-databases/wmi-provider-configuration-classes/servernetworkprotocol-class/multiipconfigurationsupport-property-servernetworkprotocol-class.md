---
title: MultiIpConfigurationSupport 屬性 (ServerNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584315"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a><span data-ttu-id="1837d-102">MultiIpConfigurationSupport 屬性 (ServerNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="1837d-102">MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="1837d-103">取得布林屬性，該屬性可指定伺服器網路通訊協定是否支援多個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1837d-103">Gets the Boolean property that specifies whether multiple IP addresses are supported by a server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1837d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1837d-104">Syntax</span></span>  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="1837d-105">組件</span><span class="sxs-lookup"><span data-stu-id="1837d-105">Parts</span></span>  
 <span data-ttu-id="1837d-106">*object*</span><span class="sxs-lookup"><span data-stu-id="1837d-106">*object*</span></span>  
 <span data-ttu-id="1837d-107">[ProtocolName 屬性 (ServerNetworkProtocol 類別，) ](servernetworkprotocol-class.md)物件，代表實例所使用的網路通訊協定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1837d-107">A [ProtocolName Property (ServerNetworkProtocol Class)](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1837d-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="1837d-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1837d-109">指定伺服器網路通訊協定是否支援多個 IP 位址的布林值：如果伺服器網路通訊協定可支援多個 IP 位址為 `true`，如果伺服器網路通訊協定不支援多個 IP 位址則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1837d-109">A Boolean value that specifies whether multiple IP addresses are supported by the server network protocol: `true` if multiple IP addresses are supported by the server network protocol, or `false` if multiple IP addresses are not supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1837d-110">備註</span><span class="sxs-lookup"><span data-stu-id="1837d-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1837d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1837d-111">See Also</span></span>  
 <span data-ttu-id="1837d-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1837d-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
