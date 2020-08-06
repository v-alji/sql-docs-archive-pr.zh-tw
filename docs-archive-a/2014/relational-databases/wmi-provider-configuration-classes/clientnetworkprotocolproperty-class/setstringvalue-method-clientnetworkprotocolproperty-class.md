---
title: SetStringValue 方法 (ClientNetworkProtocolProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba2350b798f1d7092a37a28ca35c17d6f4536a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708126"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="a7428-102">SetStringValue 方法 (ClientNetworkProtocolProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="a7428-102">SetStringValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="a7428-103">設定 PropertyIdx 屬性所參考之目前屬性的字串值， [ (ClientNetworkProtocolProperty 類別) ](clientnetworkprotocolproperty-class.md)值。</span><span class="sxs-lookup"><span data-stu-id="a7428-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7428-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7428-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a7428-105">組件</span><span class="sxs-lookup"><span data-stu-id="a7428-105">Parts</span></span>  
 <span data-ttu-id="a7428-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a7428-106">*object*</span></span>  
 <span data-ttu-id="a7428-107">[ClientNetworkProtocolProperty 類別](clientnetworkprotocolproperty-class.md)物件，代表 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 用戶端所使用之網路通訊協定的屬性 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a7428-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a7428-108">參數</span><span class="sxs-lookup"><span data-stu-id="a7428-108">Parameters</span></span>  
  
|<span data-ttu-id="a7428-109">參數</span><span class="sxs-lookup"><span data-stu-id="a7428-109">Parameter</span></span>|<span data-ttu-id="a7428-110">描述</span><span class="sxs-lookup"><span data-stu-id="a7428-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7428-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="a7428-111">*StrValue*</span></span>|<span data-ttu-id="a7428-112">指定目前屬性之新值的字串值。</span><span class="sxs-lookup"><span data-stu-id="a7428-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a7428-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="a7428-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a7428-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="a7428-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7428-115">備註</span><span class="sxs-lookup"><span data-stu-id="a7428-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7428-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7428-116">See Also</span></span>  
 [<span data-ttu-id="a7428-117">設定用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="a7428-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
