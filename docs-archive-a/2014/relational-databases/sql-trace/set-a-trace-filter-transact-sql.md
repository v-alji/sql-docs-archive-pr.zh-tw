---
title: SetBoolValue 方法 (SqlServiceAdvancedProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0c7142d6f192e94e9850b3c1a8a9481dc15a222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688690"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="0a563-102">SetBoolValue 方法 (SqlServiceAdvancedProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="0a563-102">SetBoolValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="0a563-103">設定屬性的布林值。</span><span class="sxs-lookup"><span data-stu-id="0a563-103">Sets the Boolean value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a563-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a563-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="0a563-105">組件</span><span class="sxs-lookup"><span data-stu-id="0a563-105">Parts</span></span>  
 <span data-ttu-id="0a563-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0a563-106">*object*</span></span>  
 <span data-ttu-id="0a563-107">代表進階屬性的 [SqlServiceAdvancedProperty 類別](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="0a563-107">A [SqlServiceAdvancedProperty Class](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0a563-108">參數</span><span class="sxs-lookup"><span data-stu-id="0a563-108">Parameters</span></span>  
  
|<span data-ttu-id="0a563-109">參數</span><span class="sxs-lookup"><span data-stu-id="0a563-109">Parameter</span></span>|<span data-ttu-id="0a563-110">描述</span><span class="sxs-lookup"><span data-stu-id="0a563-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a563-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="0a563-111">*BoolValue*</span></span>|<span data-ttu-id="0a563-112">指定進階屬性值的布林值。</span><span class="sxs-lookup"><span data-stu-id="0a563-112">A Boolean value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0a563-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="0a563-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0a563-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="0a563-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a563-115">備註</span><span class="sxs-lookup"><span data-stu-id="0a563-115">Remarks</span></span>  
 <span data-ttu-id="0a563-116">屬性值類型必須是布林，才能將屬性設定為布林值。</span><span class="sxs-lookup"><span data-stu-id="0a563-116">The property value type must be Boolean to set the property to a Boolean value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a563-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a563-117">See Also</span></span>  
 <span data-ttu-id="0a563-118">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a563-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
