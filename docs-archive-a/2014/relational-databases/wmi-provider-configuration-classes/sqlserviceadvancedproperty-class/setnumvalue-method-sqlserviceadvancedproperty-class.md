---
title: SetNumValue 方法 (SqlServiceAdvancedProperty 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 01388855a27dcf14754f677a42c13f8d29cbaacc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702526"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="015d2-102">SetNumValue 方法 (SqlServiceAdvancedProperty 類別)</span><span class="sxs-lookup"><span data-stu-id="015d2-102">SetNumValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="015d2-103">設定屬性的數值。</span><span class="sxs-lookup"><span data-stu-id="015d2-103">Sets the numeric value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="015d2-104">Syntax</span></span>  
  
```  
  
object  
.SetNumValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="015d2-105">組件</span><span class="sxs-lookup"><span data-stu-id="015d2-105">Parts</span></span>  
 <span data-ttu-id="015d2-106">*object*</span><span class="sxs-lookup"><span data-stu-id="015d2-106">*object*</span></span>  
 <span data-ttu-id="015d2-107">代表進階屬性的 [SqlServiceAdvancedProperty 類別](sqlserviceadvancedproperty-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="015d2-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="015d2-108">參數</span><span class="sxs-lookup"><span data-stu-id="015d2-108">Parameters</span></span>  
  
|<span data-ttu-id="015d2-109">參數</span><span class="sxs-lookup"><span data-stu-id="015d2-109">Parameter</span></span>|<span data-ttu-id="015d2-110">描述</span><span class="sxs-lookup"><span data-stu-id="015d2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="015d2-111">*Numvalue 個*</span><span class="sxs-lookup"><span data-stu-id="015d2-111">*NumValue*</span></span>|<span data-ttu-id="015d2-112">指定進階屬性值的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="015d2-112">A `uint32` value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="015d2-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="015d2-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="015d2-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="015d2-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="015d2-115">備註</span><span class="sxs-lookup"><span data-stu-id="015d2-115">Remarks</span></span>  
 <span data-ttu-id="015d2-116">屬性值類型必須是數值，才能將屬性設定為數值。</span><span class="sxs-lookup"><span data-stu-id="015d2-116">The property value type must be numeric to be able to set the property to a numeric value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015d2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="015d2-117">See Also</span></span>  
 <span data-ttu-id="015d2-118">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="015d2-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
