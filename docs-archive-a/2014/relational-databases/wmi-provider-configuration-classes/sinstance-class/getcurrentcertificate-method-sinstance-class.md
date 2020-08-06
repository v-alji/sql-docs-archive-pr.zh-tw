---
title: GetCurrentCertificate 方法 (SInstance 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47838190e3791e01f8482e3fb064a9dca3a764af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607298"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="b68c3-102">GetCurrentCertificate 方法 (SInstance 類別)</span><span class="sxs-lookup"><span data-stu-id="b68c3-102">GetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="b68c3-103">取得目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="b68c3-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b68c3-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b68c3-105">組件</span><span class="sxs-lookup"><span data-stu-id="b68c3-105">Parts</span></span>  
 <span data-ttu-id="b68c3-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b68c3-106">*object*</span></span>  
 <span data-ttu-id="b68c3-107">代表 [執行個體上之伺服器設定的](sinstance-class.md) SInstance 類別 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="b68c3-107">An [SInstance Class](sinstance-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b68c3-108">參數</span><span class="sxs-lookup"><span data-stu-id="b68c3-108">Parameters</span></span>  
  
|<span data-ttu-id="b68c3-109">參數</span><span class="sxs-lookup"><span data-stu-id="b68c3-109">Parameter</span></span>|<span data-ttu-id="b68c3-110">描述</span><span class="sxs-lookup"><span data-stu-id="b68c3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b68c3-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="b68c3-111">*SHA*</span></span>|<span data-ttu-id="b68c3-112">在方法完成之後指定目前安全性憑證的字串物件值 (輸出參數)。</span><span class="sxs-lookup"><span data-stu-id="b68c3-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b68c3-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="b68c3-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b68c3-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="b68c3-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b68c3-115">備註</span><span class="sxs-lookup"><span data-stu-id="b68c3-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68c3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68c3-116">See Also</span></span>  
 <span data-ttu-id="b68c3-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b68c3-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
