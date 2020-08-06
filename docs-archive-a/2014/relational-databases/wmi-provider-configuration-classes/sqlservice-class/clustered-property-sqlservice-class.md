---
title: 叢集屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Clustered Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fdc87bb7b691580f7efd5ccd7b333d88a3aa78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687598"
---
# <a name="clustered-property-sqlservice-class"></a><span data-ttu-id="66f74-102">Clustered 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="66f74-102">Clustered Property (SqlService Class)</span></span>
  <span data-ttu-id="66f74-103">取得可指定服務是否為叢集執行個體之一部分的布林屬性值。</span><span class="sxs-lookup"><span data-stu-id="66f74-103">Gets the Boolean property value that specifies whether the service is part of a clustered instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f74-104">語法</span><span class="sxs-lookup"><span data-stu-id="66f74-104">Syntax</span></span>  
  
```  
  
object  
.Clustered [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="66f74-105">組件</span><span class="sxs-lookup"><span data-stu-id="66f74-105">Parts</span></span>  
 <span data-ttu-id="66f74-106">*object*</span><span class="sxs-lookup"><span data-stu-id="66f74-106">*object*</span></span>  
 <span data-ttu-id="66f74-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="66f74-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="66f74-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="66f74-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="66f74-109">指定服務是否正在參與叢集執行個體的布林值：如果服務正在參與叢集執行個體為 `true`，如果服務未參與叢集執行個體則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="66f74-109">A Boolean value that specifies whether the service is participating in a clustered instance: `true` if the service is participating in a clustered instance, or `false` if the service is not participating in a clustered instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66f74-110">備註</span><span class="sxs-lookup"><span data-stu-id="66f74-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f74-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66f74-111">See Also</span></span>  
 <span data-ttu-id="66f74-112">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="66f74-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
