---
title: ProtocolOrder 屬性 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bccb7109972dea4697e9e289081cbf47d2f9492
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606698"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a><span data-ttu-id="ca3b3-102">ProtocolOrder 屬性 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="ca3b3-102">ProtocolOrder Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="ca3b3-103">取得 SetOrderValue 方法所指定之目前參考的用戶端網路通訊協定的順序號碼， [) 方法 (ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)。</span><span class="sxs-lookup"><span data-stu-id="ca3b3-103">Gets the order number of the currently referenced client network protocol as specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca3b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca3b3-104">Syntax</span></span>  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="ca3b3-105">組件</span><span class="sxs-lookup"><span data-stu-id="ca3b3-105">Parts</span></span>  
 <span data-ttu-id="ca3b3-106">*object*</span><span class="sxs-lookup"><span data-stu-id="ca3b3-106">*object*</span></span>  
 <span data-ttu-id="ca3b3-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ca3b3-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ca3b3-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="ca3b3-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ca3b3-109">`uint32` 值，可指定 `OrderValue` 方法設定之目前參考的用戶端網路通訊協定的順序號碼。</span><span class="sxs-lookup"><span data-stu-id="ca3b3-109">A `uint32` value that specifies the order number of the currently referenced client network protocol as set by the `OrderValue` method.</span></span> <span data-ttu-id="ca3b3-110">如果停用用戶端網路通訊協定，這個值將會是零。</span><span class="sxs-lookup"><span data-stu-id="ca3b3-110">If the client network protocol is disabled, this value will be zero.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca3b3-111">備註</span><span class="sxs-lookup"><span data-stu-id="ca3b3-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3b3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca3b3-112">See Also</span></span>  
 <span data-ttu-id="ca3b3-113">[設定用戶端通訊協定](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="ca3b3-113">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="ca3b3-114">設定用戶端網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="ca3b3-114">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
