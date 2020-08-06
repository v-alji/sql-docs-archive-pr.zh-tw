---
title: GetCurrentCertificate 方法 (ServerSettings 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 450e33c6-91d4-420f-ab7c-1905111f5658
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b36a5fe7cd39da0f336d05fc4c450170fa21199d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687661"
---
# <a name="getcurrentcertificate-method-serversettings-class"></a><span data-ttu-id="b27b9-102">GetCurrentCertificate 方法 (ServerSettings 類別)</span><span class="sxs-lookup"><span data-stu-id="b27b9-102">GetCurrentCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="b27b9-103">取得目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="b27b9-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b27b9-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b27b9-105">組件</span><span class="sxs-lookup"><span data-stu-id="b27b9-105">Parts</span></span>  
 <span data-ttu-id="b27b9-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b27b9-106">*object*</span></span>  
 <span data-ttu-id="b27b9-107">表示 `ServerSettings` 執行個體上之伺服器設定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="b27b9-107">A `ServerSettings` object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b27b9-108">參數</span><span class="sxs-lookup"><span data-stu-id="b27b9-108">Parameters</span></span>  
  
|<span data-ttu-id="b27b9-109">參數</span><span class="sxs-lookup"><span data-stu-id="b27b9-109">Parameter</span></span>|<span data-ttu-id="b27b9-110">描述</span><span class="sxs-lookup"><span data-stu-id="b27b9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b27b9-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="b27b9-111">*SHA*</span></span>|<span data-ttu-id="b27b9-112">在方法完成之後指定目前安全性憑證的字串物件值 (輸出參數)。</span><span class="sxs-lookup"><span data-stu-id="b27b9-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b27b9-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="b27b9-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b27b9-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="b27b9-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b27b9-115">備註</span><span class="sxs-lookup"><span data-stu-id="b27b9-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27b9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b27b9-116">See Also</span></span>  
 <span data-ttu-id="b27b9-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b27b9-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
