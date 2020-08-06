---
title: GetCurrentCertificate 方法 (SecurityCertificate 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab96b2e2a8fabf9e9ccce647e54be1983fe40ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687678"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a><span data-ttu-id="a7203-102">GetCurrentCertificate 方法 (SecurityCertificate 類別)</span><span class="sxs-lookup"><span data-stu-id="a7203-102">GetCurrentCertificate Method (SecurityCertificate Class)</span></span>
  <span data-ttu-id="a7203-103">取得目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="a7203-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7203-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7203-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a7203-105">組件</span><span class="sxs-lookup"><span data-stu-id="a7203-105">Parts</span></span>  
 <span data-ttu-id="a7203-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a7203-106">*object*</span></span>  
 <span data-ttu-id="a7203-107">代表安全性憑證的 [SecurityCertificate 類別](securitycertificate-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="a7203-107">A [SecurityCertificate Class](securitycertificate-class.md) object that represents a security certificate.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a7203-108">參數</span><span class="sxs-lookup"><span data-stu-id="a7203-108">Parameters</span></span>  
  
|<span data-ttu-id="a7203-109">參數</span><span class="sxs-lookup"><span data-stu-id="a7203-109">Parameter</span></span>|<span data-ttu-id="a7203-110">描述</span><span class="sxs-lookup"><span data-stu-id="a7203-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7203-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="a7203-111">*SHA*</span></span>|<span data-ttu-id="a7203-112">在方法完成之後指定目前安全性憑證 SHA 指模的字串值 (輸出參數)。</span><span class="sxs-lookup"><span data-stu-id="a7203-112">A string value (output parameter) that specifies the current security certificate SHA thumbprint after the method completes.</span></span>|  
|<span data-ttu-id="a7203-113">*SQLInstance*</span><span class="sxs-lookup"><span data-stu-id="a7203-113">*SQLInstance*</span></span>|<span data-ttu-id="a7203-114">指定需要憑證之執行個體的字串值。</span><span class="sxs-lookup"><span data-stu-id="a7203-114">A string value that specifies the instance for which the certificate is required.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a7203-115">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="a7203-115">Property Value/Return Value</span></span>  
 <span data-ttu-id="a7203-116">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="a7203-116">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7203-117">備註</span><span class="sxs-lookup"><span data-stu-id="a7203-117">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7203-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7203-118">See Also</span></span>  
 <span data-ttu-id="a7203-119">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a7203-119">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
