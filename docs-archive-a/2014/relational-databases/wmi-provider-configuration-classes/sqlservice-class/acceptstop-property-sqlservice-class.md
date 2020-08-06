---
title: AcceptStop 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d555a3763b4e8c769cd52ce72019b66bddd594fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595845"
---
# <a name="acceptstop-property-sqlservice-class"></a><span data-ttu-id="c3aa0-102">AcceptStop 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="c3aa0-102">AcceptStop Property (SqlService Class)</span></span>
  <span data-ttu-id="c3aa0-103">取得可指定是否可停止服務的布林屬性值。</span><span class="sxs-lookup"><span data-stu-id="c3aa0-103">Gets the Boolean property value that specifies whether the service can be stopped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3aa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3aa0-104">Syntax</span></span>  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c3aa0-105">組件</span><span class="sxs-lookup"><span data-stu-id="c3aa0-105">Parts</span></span>  
 <span data-ttu-id="c3aa0-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c3aa0-106">*object*</span></span>  
 <span data-ttu-id="c3aa0-107">代表服務的[SqlService 類別](sqlservice-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="c3aa0-107">A [SqlService Class](sqlservice-class.md) object that represents the service</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c3aa0-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="c3aa0-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c3aa0-109">指定是否可停止服務的布林值：如果可停止服務為 `true`，如果無法停止則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c3aa0-109">A Boolean value that specifies whether the service can be stopped: `true` if the service can be stopped, or `false` if the service cannot be stopped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3aa0-110">備註</span><span class="sxs-lookup"><span data-stu-id="c3aa0-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3aa0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3aa0-111">See Also</span></span>  
 <span data-ttu-id="c3aa0-112">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c3aa0-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
