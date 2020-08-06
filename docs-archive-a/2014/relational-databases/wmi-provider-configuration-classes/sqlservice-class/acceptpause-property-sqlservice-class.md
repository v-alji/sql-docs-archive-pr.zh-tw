---
title: AcceptPause 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 930c82f6e4538f7f2e916deaa374e928b756909b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606671"
---
# <a name="acceptpause-property-sqlservice-class"></a><span data-ttu-id="204db-102">AcceptPause 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="204db-102">AcceptPause Property (SqlService Class)</span></span>
  <span data-ttu-id="204db-103">取得可指定是否可暫停服務的布林屬性值。</span><span class="sxs-lookup"><span data-stu-id="204db-103">Gets the Boolean property value that specifies whether the service can be paused.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="204db-104">語法</span><span class="sxs-lookup"><span data-stu-id="204db-104">Syntax</span></span>  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="204db-105">組件</span><span class="sxs-lookup"><span data-stu-id="204db-105">Parts</span></span>  
 <span data-ttu-id="204db-106">*object*</span><span class="sxs-lookup"><span data-stu-id="204db-106">*object*</span></span>  
 <span data-ttu-id="204db-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="204db-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="204db-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="204db-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="204db-109">指定是否可暫停服務的布林值。</span><span class="sxs-lookup"><span data-stu-id="204db-109">A Boolean value that specifies whether the service can be paused.</span></span> <span data-ttu-id="204db-110">如果可暫停服務為 `true`，如果無法暫停則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="204db-110">`true` if the service can be paused; `false` if the service cannot be paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="204db-111">備註</span><span class="sxs-lookup"><span data-stu-id="204db-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204db-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="204db-112">See Also</span></span>  
 <span data-ttu-id="204db-113">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="204db-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
