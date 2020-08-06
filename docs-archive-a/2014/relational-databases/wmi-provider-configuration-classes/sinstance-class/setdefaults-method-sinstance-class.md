---
title: SetDefaults 方法 (SInstance 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c581834d3c97bed622d16fbb35e48704f8679531
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687633"
---
# <a name="setdefaults-method-sinstance-class"></a><span data-ttu-id="a73bf-102">SetDefaults 方法 (SInstance 類別)</span><span class="sxs-lookup"><span data-stu-id="a73bf-102">SetDefaults Method (SInstance Class)</span></span>
  <span data-ttu-id="a73bf-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用覆寫現有資料的選項，設定實例的所有預設值。</span><span class="sxs-lookup"><span data-stu-id="a73bf-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="a73bf-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a73bf-105">組件</span><span class="sxs-lookup"><span data-stu-id="a73bf-105">Parts</span></span>  
 <span data-ttu-id="a73bf-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a73bf-106">*object*</span></span>  
 <span data-ttu-id="a73bf-107">代表伺服器實例的[SInstance 類別](sinstance-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a73bf-107">An [SInstance Class](sinstance-class.md) object that represents a server instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a73bf-108">參數</span><span class="sxs-lookup"><span data-stu-id="a73bf-108">Parameters</span></span>  
  
|<span data-ttu-id="a73bf-109">參數</span><span class="sxs-lookup"><span data-stu-id="a73bf-109">Parameter</span></span>|<span data-ttu-id="a73bf-110">描述</span><span class="sxs-lookup"><span data-stu-id="a73bf-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a73bf-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="a73bf-111">*OverwriteAll*</span></span>|<span data-ttu-id="a73bf-112">指定是否要覆寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端執行個體上之現有值的布林值：`true` 表示要覆寫現有的資料，`false` 表示不覆寫現有的資料。</span><span class="sxs-lookup"><span data-stu-id="a73bf-112">A Boolean value that specifies whether to overwrite existing value on the instance of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client: `true` if existing data is overwritten, or `false` if existing data is not overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a73bf-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="a73bf-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a73bf-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="a73bf-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a73bf-115">備註</span><span class="sxs-lookup"><span data-stu-id="a73bf-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73bf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a73bf-116">See Also</span></span>  
 <span data-ttu-id="a73bf-117">[設定伺服器網路通訊協定與網路程式庫](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a73bf-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
