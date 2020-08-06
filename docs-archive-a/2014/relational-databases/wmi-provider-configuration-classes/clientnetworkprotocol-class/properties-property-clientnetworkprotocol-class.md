---
title: Properties 屬性 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09836db1f510ac77635924c51e5341686627d54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607305"
---
# <a name="properties-property-clientnetworkprotocol-class"></a><span data-ttu-id="c0141-102">Properties 屬性 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="c0141-102">Properties Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="c0141-103">取得與[設定用戶端通訊](https://technet.microsoft.com/library/ms181035.aspx)協定指定之目前用戶端網路通訊協定相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0141-103">Gets the properties associated with the current client network protocol specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0141-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0141-104">Syntax</span></span>  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c0141-105">組件</span><span class="sxs-lookup"><span data-stu-id="c0141-105">Parts</span></span>  
 <span data-ttu-id="c0141-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c0141-106">*object*</span></span>  
 <span data-ttu-id="c0141-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c0141-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c0141-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="c0141-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c0141-109">[ClientNetworkProtocolProperty 類別](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)物件的陣列，代表屬性所參考之目前用戶端網路通訊協定所支援的屬性 `OrderValue` 。</span><span class="sxs-lookup"><span data-stu-id="c0141-109">An array of [ClientNetworkProtocolProperty Class](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objects that represent the properties supported by the current client network protocol that is referenced by the `OrderValue` property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0141-110">備註</span><span class="sxs-lookup"><span data-stu-id="c0141-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0141-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0141-111">See Also</span></span>  
 [<span data-ttu-id="c0141-112">設定用戶端網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="c0141-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
