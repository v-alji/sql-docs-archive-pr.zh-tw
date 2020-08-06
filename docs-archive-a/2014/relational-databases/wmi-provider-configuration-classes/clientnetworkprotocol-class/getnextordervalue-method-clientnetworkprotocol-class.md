---
title: GetNextOrderValue 方法 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bdc3eecd9e151d7da32a5fd65a90552c0743b3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607307"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="41f79-102">GetNextOrderValue 方法 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="41f79-102">GetNextOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="41f79-103">在通訊協定清單中選取下一個位置的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="41f79-103">Selects the protocol that is in the next position in the list of protocols.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f79-104">語法</span><span class="sxs-lookup"><span data-stu-id="41f79-104">Syntax</span></span>  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="41f79-105">組件</span><span class="sxs-lookup"><span data-stu-id="41f79-105">Parts</span></span>  
 <span data-ttu-id="41f79-106">*object*</span><span class="sxs-lookup"><span data-stu-id="41f79-106">*object*</span></span>  
 <span data-ttu-id="41f79-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="41f79-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="41f79-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="41f79-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="41f79-109">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="41f79-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41f79-110">備註</span><span class="sxs-lookup"><span data-stu-id="41f79-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f79-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41f79-111">See Also</span></span>  
 <span data-ttu-id="41f79-112">[設定用戶端通訊協定](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="41f79-112">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="41f79-113">設定用戶端網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="41f79-113">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
