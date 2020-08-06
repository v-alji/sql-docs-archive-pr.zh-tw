---
title: SetCurrentCertificate 方法 (SInstance 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 7349fb87-b973-4160-a2be-cab73abf5b31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 44e65ab30659cacca09e63a94a1f3596a182dda5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687637"
---
# <a name="setcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="fe69c-102">SetCurrentCertificate 方法 (SInstance 類別)</span><span class="sxs-lookup"><span data-stu-id="fe69c-102">SetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="fe69c-103">設定目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="fe69c-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe69c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe69c-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="fe69c-105">組件</span><span class="sxs-lookup"><span data-stu-id="fe69c-105">Parts</span></span>  
 <span data-ttu-id="fe69c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="fe69c-106">*object*</span></span>  
 <span data-ttu-id="fe69c-107">代表實例上之伺服器設定的[SInstance 類別](sinstance-class.md)物件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe69c-107">An [SInstance Class](sinstance-class.md) object that represents the server setting on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="fe69c-108">參數</span><span class="sxs-lookup"><span data-stu-id="fe69c-108">Parameters</span></span>  
  
|<span data-ttu-id="fe69c-109">參數</span><span class="sxs-lookup"><span data-stu-id="fe69c-109">Parameter</span></span>|<span data-ttu-id="fe69c-110">描述</span><span class="sxs-lookup"><span data-stu-id="fe69c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe69c-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="fe69c-111">*SHA*</span></span>|<span data-ttu-id="fe69c-112">指定目前安全性憑證的字串值。</span><span class="sxs-lookup"><span data-stu-id="fe69c-112">A string value that specifies the current security certificate.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fe69c-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="fe69c-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="fe69c-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="fe69c-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe69c-115">備註</span><span class="sxs-lookup"><span data-stu-id="fe69c-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe69c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe69c-116">See Also</span></span>  
 <span data-ttu-id="fe69c-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fe69c-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
