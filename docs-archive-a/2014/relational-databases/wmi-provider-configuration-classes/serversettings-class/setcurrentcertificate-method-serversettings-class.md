---
title: SetCurrentCertificate 方法 (ServerSettings 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: f9c6e172-11be-42de-b19b-a5b3436e84da
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7071937a7d7e601597fe008187448bb16a5a15ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699343"
---
# <a name="setcurrentcertificate-method-serversettings-class"></a><span data-ttu-id="bfb08-102">SetCurrentCertificate 方法 (ServerSettings 類別)</span><span class="sxs-lookup"><span data-stu-id="bfb08-102">SetCurrentCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="bfb08-103">設定目前的安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="bfb08-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb08-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfb08-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="bfb08-105">組件</span><span class="sxs-lookup"><span data-stu-id="bfb08-105">Parts</span></span>  
 <span data-ttu-id="bfb08-106">*object*</span><span class="sxs-lookup"><span data-stu-id="bfb08-106">*object*</span></span>  
 <span data-ttu-id="bfb08-107">[ServerSettings 類別] ServerSettings-class.md) 物件，代表實例上的伺服器設定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bfb08-107">A [ServerSettings Class]serversettings-class.md) object that represents the server setting on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="bfb08-108">參數</span><span class="sxs-lookup"><span data-stu-id="bfb08-108">Parameters</span></span>  
  
|<span data-ttu-id="bfb08-109">參數</span><span class="sxs-lookup"><span data-stu-id="bfb08-109">Parameter</span></span>|<span data-ttu-id="bfb08-110">描述</span><span class="sxs-lookup"><span data-stu-id="bfb08-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfb08-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="bfb08-111">*SHA*</span></span>|<span data-ttu-id="bfb08-112">指定目前安全性憑證的字串值。</span><span class="sxs-lookup"><span data-stu-id="bfb08-112">A string value that specifies the current security certificate.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bfb08-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="bfb08-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="bfb08-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="bfb08-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfb08-115">備註</span><span class="sxs-lookup"><span data-stu-id="bfb08-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb08-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfb08-116">See Also</span></span>  
 <span data-ttu-id="bfb08-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bfb08-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
