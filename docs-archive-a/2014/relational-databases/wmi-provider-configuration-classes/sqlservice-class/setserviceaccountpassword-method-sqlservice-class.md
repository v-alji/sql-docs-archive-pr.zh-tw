---
title: SetServiceAccountPassword 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccountPassword Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7a83a6d3686b2ec2df98ae79b4c9d3347f621ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687597"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a><span data-ttu-id="f9559-102">SetServiceAccountPassword 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="f9559-102">SetServiceAccountPassword Method (SqlService Class)</span></span>
  <span data-ttu-id="f9559-103">修改參考之服務執行時所使用之帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="f9559-103">Modifies the password for the account that the referenced service runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9559-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9559-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccountPassword(  
AccountOldPassword , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="f9559-105">組件</span><span class="sxs-lookup"><span data-stu-id="f9559-105">Parts</span></span>  
 <span data-ttu-id="f9559-106">*object*</span><span class="sxs-lookup"><span data-stu-id="f9559-106">*object*</span></span>  
 <span data-ttu-id="f9559-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="f9559-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="f9559-108">參數</span><span class="sxs-lookup"><span data-stu-id="f9559-108">Parameters</span></span>  
 <span data-ttu-id="f9559-109">*AccountOldPassword*</span><span class="sxs-lookup"><span data-stu-id="f9559-109">*AccountOldPassword*</span></span>  
 <span data-ttu-id="f9559-110">指定帳戶之現有密碼的字串值。</span><span class="sxs-lookup"><span data-stu-id="f9559-110">A string value that specifies the existing password for the account.</span></span>  
  
 <span data-ttu-id="f9559-111">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="f9559-111">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="f9559-112">指定帳戶之新密碼的字串值。</span><span class="sxs-lookup"><span data-stu-id="f9559-112">A string value that specifies the new password for the account.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f9559-113">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="f9559-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="f9559-114">`uint32` 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="f9559-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9559-115">備註</span><span class="sxs-lookup"><span data-stu-id="f9559-115">Remarks</span></span>  
  
