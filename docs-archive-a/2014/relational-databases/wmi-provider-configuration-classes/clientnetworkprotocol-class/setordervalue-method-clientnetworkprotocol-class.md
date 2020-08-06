---
title: SetOrderValue 方法 (ClientNetworkProtocol 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6839e85b6131c54e233d980c84a8727eeda2202a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606697"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="36222-102">SetOrderValue 方法 (ClientNetworkProtocol 類別)</span><span class="sxs-lookup"><span data-stu-id="36222-102">SetOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="36222-103">從用戶端通訊協定清單中選取指定之順序值的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="36222-103">Selects the protocol with the specified order value from the client protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36222-104">語法</span><span class="sxs-lookup"><span data-stu-id="36222-104">Syntax</span></span>  
  
```  
  
object  
.SetOrderValue(  
OrderValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="36222-105">組件</span><span class="sxs-lookup"><span data-stu-id="36222-105">Parts</span></span>  
 <span data-ttu-id="36222-106">*object*</span><span class="sxs-lookup"><span data-stu-id="36222-106">*object*</span></span>  
 <span data-ttu-id="36222-107">代表用戶端所使用之網路通訊協定的[ClientNetworkProtocol 類別](clientnetworkprotocol-class.md)物件 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="36222-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="36222-108">參數</span><span class="sxs-lookup"><span data-stu-id="36222-108">Parameters</span></span>  
  
|<span data-ttu-id="36222-109">參數</span><span class="sxs-lookup"><span data-stu-id="36222-109">Parameter</span></span>|<span data-ttu-id="36222-110">描述</span><span class="sxs-lookup"><span data-stu-id="36222-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36222-111">*OrderValue*</span><span class="sxs-lookup"><span data-stu-id="36222-111">*OrderValue*</span></span>|<span data-ttu-id="36222-112">設定順序值的 u`int32` 值。</span><span class="sxs-lookup"><span data-stu-id="36222-112">A u`int32` value that sets the order value.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="36222-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="36222-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="36222-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="36222-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36222-115">備註</span><span class="sxs-lookup"><span data-stu-id="36222-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36222-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36222-116">See Also</span></span>  
 [<span data-ttu-id="36222-117">用戶端通訊協定屬性 (順序索引標籤)</span><span class="sxs-lookup"><span data-stu-id="36222-117">Client Protocols Properties (Order Tab)</span></span>](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
