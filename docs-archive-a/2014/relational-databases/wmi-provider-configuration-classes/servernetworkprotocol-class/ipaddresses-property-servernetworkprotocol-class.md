---
title: IpAddresses 屬性 (ServerNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b94c4c11327abc1f02bd1e99c414f806f75bc145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584316"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a><span data-ttu-id="f0f5e-102">IpAddresses 屬性 (ServerNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="f0f5e-102">IpAddresses Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="f0f5e-103">取得與伺服器網路通訊協定相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f0f5e-103">Gets the IP addresses associated with the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0f5e-104">Syntax</span></span>  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="f0f5e-105">組件</span><span class="sxs-lookup"><span data-stu-id="f0f5e-105">Parts</span></span>  
 <span data-ttu-id="f0f5e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="f0f5e-106">*object*</span></span>  
 <span data-ttu-id="f0f5e-107">`ServerNetworkProtocol`物件，表示實例所使用的網路通訊協定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f0f5e-107">A `ServerNetworkProtocol` object that represents the network protocol used by the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f0f5e-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="f0f5e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="f0f5e-109">[ServerNetworkProtocolIPAdress 類別](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)物件的陣列，代表伺服器網路通訊協定所支援的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f0f5e-109">An array of [ServerNetworkProtocolIPAdress Class](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) objects that represent the IP addresses supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f5e-110">備註</span><span class="sxs-lookup"><span data-stu-id="f0f5e-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f5e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0f5e-111">See Also</span></span>  
 <span data-ttu-id="f0f5e-112">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f0f5e-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
