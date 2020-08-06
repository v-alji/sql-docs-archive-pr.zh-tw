---
title: SetProtocolsOrder 方法 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aaa1d43c8a2f7f210f61761b28313a93ac6c7a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606693"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a><span data-ttu-id="4929b-102">SetProtocolsOrder 方法 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="4929b-102">SetProtocolsOrder Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="4929b-103">變更通訊協定清單的順序。</span><span class="sxs-lookup"><span data-stu-id="4929b-103">Changes the order of the protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4929b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4929b-104">Syntax</span></span>  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="4929b-105">組件</span><span class="sxs-lookup"><span data-stu-id="4929b-105">Parts</span></span>  
 <span data-ttu-id="4929b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="4929b-106">*object*</span></span>  
 <span data-ttu-id="4929b-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4929b-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="4929b-108">參數</span><span class="sxs-lookup"><span data-stu-id="4929b-108">Parameters</span></span>  
  
|<span data-ttu-id="4929b-109">參數</span><span class="sxs-lookup"><span data-stu-id="4929b-109">Parameter</span></span>|<span data-ttu-id="4929b-110">描述</span><span class="sxs-lookup"><span data-stu-id="4929b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4929b-111">*ProtocolOrderList*</span><span class="sxs-lookup"><span data-stu-id="4929b-111">*ProtocolOrderList*</span></span>|<span data-ttu-id="4929b-112">以新的順序列出用戶端網路通訊協定的 string[] 陣列。</span><span class="sxs-lookup"><span data-stu-id="4929b-112">A string[] array that lists the client network protocols in the new order.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4929b-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="4929b-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="4929b-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="4929b-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4929b-115">備註</span><span class="sxs-lookup"><span data-stu-id="4929b-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4929b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4929b-116">See Also</span></span>  
 <span data-ttu-id="4929b-117">[設定用戶端通訊協定](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="4929b-117">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="4929b-118">設定用戶端網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="4929b-118">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
