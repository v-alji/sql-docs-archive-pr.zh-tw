---
title: ResumeService 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ResumeService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 53d07c8697c6303bc371f442745e2d1864682e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594961"
---
# <a name="resumeservice-method-sqlservice-class"></a><span data-ttu-id="c0d67-102">ResumeService 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="c0d67-102">ResumeService Method (SqlService Class)</span></span>
  <span data-ttu-id="c0d67-103">嘗試將此服務置於繼續狀態。</span><span class="sxs-lookup"><span data-stu-id="c0d67-103">Attempts to place the service in the resumed state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d67-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0d67-104">Syntax</span></span>  
  
```  
  
object  
.ResumeService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c0d67-105">組件</span><span class="sxs-lookup"><span data-stu-id="c0d67-105">Parts</span></span>  
 <span data-ttu-id="c0d67-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c0d67-106">*object*</span></span>  
 <span data-ttu-id="c0d67-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="c0d67-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c0d67-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="c0d67-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c0d67-109">uint32 值，如果已接受 `ResumeService` 要求為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。</span><span class="sxs-lookup"><span data-stu-id="c0d67-109">A uint32 value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0d67-110">備註</span><span class="sxs-lookup"><span data-stu-id="c0d67-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d67-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0d67-111">See Also</span></span>  
 <span data-ttu-id="c0d67-112">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c0d67-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
