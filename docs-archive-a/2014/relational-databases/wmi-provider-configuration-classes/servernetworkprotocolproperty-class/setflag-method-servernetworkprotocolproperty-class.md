---
title: SetFlag 方法 (ServerNetworkProtocolProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 95288931-8eb1-4477-ad80-619cf7073e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1a90b4fca194f20cc0a2d70c947577594155f051
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688674"
---
# <a name="setflag-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="0da6e-102">SetFlag 方法 (ServerNetworkProtocolProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="0da6e-102">SetFlag Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="0da6e-103">設定參考之屬性的旗標。</span><span class="sxs-lookup"><span data-stu-id="0da6e-103">Sets the flag of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0da6e-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0da6e-105">組件</span><span class="sxs-lookup"><span data-stu-id="0da6e-105">Parts</span></span>  
 <span data-ttu-id="0da6e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0da6e-106">*object*</span></span>  
 <span data-ttu-id="0da6e-107">[ServerNetworkProtocolProperty 類別] ServerNetworkProtocolProperty-class.md) 物件，代表實例上網路通訊協定的屬性 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0da6e-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0da6e-108">參數</span><span class="sxs-lookup"><span data-stu-id="0da6e-108">Parameters</span></span>  
  
|<span data-ttu-id="0da6e-109">參數</span><span class="sxs-lookup"><span data-stu-id="0da6e-109">Parameter</span></span>|<span data-ttu-id="0da6e-110">描述</span><span class="sxs-lookup"><span data-stu-id="0da6e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0da6e-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="0da6e-111">*BoolValue*</span></span>|<span data-ttu-id="0da6e-112">指定旗標之新值的布林值。</span><span class="sxs-lookup"><span data-stu-id="0da6e-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0da6e-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="0da6e-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0da6e-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="0da6e-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0da6e-115">備註</span><span class="sxs-lookup"><span data-stu-id="0da6e-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da6e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0da6e-116">See Also</span></span>  
 <span data-ttu-id="0da6e-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0da6e-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
