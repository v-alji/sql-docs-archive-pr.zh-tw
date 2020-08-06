---
title: SetStringValue 方法 (SqlServiceAdvancedProperty 類別 ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (SqlServiceAdvancedProperty Class )
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: a02d05f6-1072-4709-9ecc-e23e51c8c898
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d7939c6af677ac77b9d8005571406315905bfd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702525"
---
# <a name="setstringvalue-method-sqlserviceadvancedproperty-class-"></a><span data-ttu-id="23ac1-102">SetStringValue 方法 (SqlServiceAdvancedProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="23ac1-102">SetStringValue Method (SqlServiceAdvancedProperty Class )</span></span>
  <span data-ttu-id="23ac1-103">設定屬性的字串值。</span><span class="sxs-lookup"><span data-stu-id="23ac1-103">Sets the string value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="23ac1-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="23ac1-105">組件</span><span class="sxs-lookup"><span data-stu-id="23ac1-105">Parts</span></span>  
 <span data-ttu-id="23ac1-106">*object*</span><span class="sxs-lookup"><span data-stu-id="23ac1-106">*object*</span></span>  
 <span data-ttu-id="23ac1-107">代表進階屬性的 [SqlServiceAdvancedProperty 類別](sqlserviceadvancedproperty-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="23ac1-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="23ac1-108">參數</span><span class="sxs-lookup"><span data-stu-id="23ac1-108">Parameters</span></span>  
  
|<span data-ttu-id="23ac1-109">參數</span><span class="sxs-lookup"><span data-stu-id="23ac1-109">Parameter</span></span>|<span data-ttu-id="23ac1-110">描述</span><span class="sxs-lookup"><span data-stu-id="23ac1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23ac1-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="23ac1-111">*StrValue*</span></span>|<span data-ttu-id="23ac1-112">指定進階屬性值的字串值。</span><span class="sxs-lookup"><span data-stu-id="23ac1-112">A string value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="23ac1-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="23ac1-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="23ac1-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="23ac1-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23ac1-115">備註</span><span class="sxs-lookup"><span data-stu-id="23ac1-115">Remarks</span></span>  
 <span data-ttu-id="23ac1-116">屬性值類型必須是 `string`，才能將屬性設定為字串值。</span><span class="sxs-lookup"><span data-stu-id="23ac1-116">The property value type must be `string` to be able to set the property to a string value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ac1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ac1-117">See Also</span></span>  
 <span data-ttu-id="23ac1-118">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="23ac1-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
