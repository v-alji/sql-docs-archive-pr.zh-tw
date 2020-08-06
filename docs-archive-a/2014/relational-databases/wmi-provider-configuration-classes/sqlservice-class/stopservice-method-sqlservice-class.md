---
title: StopService 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StopService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StopService method
ms.assetid: ef8e1856-4930-417a-8f52-be470fd3f15c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 534db69b9c5474638ef5e893847f7d6b9bbb645d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702541"
---
# <a name="stopservice-method-sqlservice-class"></a><span data-ttu-id="de580-102">StopService 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="de580-102">StopService Method (SqlService Class)</span></span>
  <span data-ttu-id="de580-103">嘗試將此服務置於已停止狀態。</span><span class="sxs-lookup"><span data-stu-id="de580-103">Attempts to place the service in the stopped state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de580-104">語法</span><span class="sxs-lookup"><span data-stu-id="de580-104">Syntax</span></span>  
  
```  
  
object  
.StopService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="de580-105">組件</span><span class="sxs-lookup"><span data-stu-id="de580-105">Parts</span></span>  
 <span data-ttu-id="de580-106">*object*</span><span class="sxs-lookup"><span data-stu-id="de580-106">*object*</span></span>  
 <span data-ttu-id="de580-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="de580-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="de580-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="de580-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="de580-109">`uint32` 值，如果已接受 `ResumeService` 要求為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="de580-109">A `uint32` value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de580-110">備註</span><span class="sxs-lookup"><span data-stu-id="de580-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de580-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de580-111">See Also</span></span>  
 <span data-ttu-id="de580-112">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="de580-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
