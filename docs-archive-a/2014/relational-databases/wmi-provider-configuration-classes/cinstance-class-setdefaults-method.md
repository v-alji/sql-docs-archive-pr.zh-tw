---
title: SetDefaults 方法 (CInstance 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e589796f973592d7f9f549bffbbf8dfbe49cc27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584327"
---
# <a name="setdefaults-method-cinstance-class"></a><span data-ttu-id="c4407-102">SetDefaults 方法 (CInstance 類別)</span><span class="sxs-lookup"><span data-stu-id="c4407-102">SetDefaults Method (CInstance Class)</span></span>
  <span data-ttu-id="c4407-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用覆寫現有資料的選項，設定用戶端實例的所有預設值。</span><span class="sxs-lookup"><span data-stu-id="c4407-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4407-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4407-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c4407-105">組件</span><span class="sxs-lookup"><span data-stu-id="c4407-105">Parts</span></span>  
 <span data-ttu-id="c4407-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c4407-106">*object*</span></span>  
 <span data-ttu-id="c4407-107">代表 [用戶端執行個體的](cinstance-class.md) CInstance 類別 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="c4407-107">A [CInstance Class](cinstance-class.md) object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="c4407-108">參數</span><span class="sxs-lookup"><span data-stu-id="c4407-108">Parameters</span></span>  
  
|<span data-ttu-id="c4407-109">參數</span><span class="sxs-lookup"><span data-stu-id="c4407-109">Parameter</span></span>|<span data-ttu-id="c4407-110">描述</span><span class="sxs-lookup"><span data-stu-id="c4407-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4407-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="c4407-111">*OverwriteAll*</span></span>|<span data-ttu-id="c4407-112">指定是否要覆寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端執行個體上之現有值的布林值：`true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。</span><span class="sxs-lookup"><span data-stu-id="c4407-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c4407-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="c4407-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="c4407-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="c4407-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4407-115">備註</span><span class="sxs-lookup"><span data-stu-id="c4407-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4407-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4407-116">See Also</span></span>  
 [<span data-ttu-id="c4407-117">設定用戶端通訊協定</span><span class="sxs-lookup"><span data-stu-id="c4407-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
