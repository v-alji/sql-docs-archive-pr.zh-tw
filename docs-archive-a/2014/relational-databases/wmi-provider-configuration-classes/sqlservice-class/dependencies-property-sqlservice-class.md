---
title: 相依性屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5b64aee371a41bc0d58ec4a52a1a1526bc13388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706325"
---
# <a name="dependencies-property-sqlservice-class"></a><span data-ttu-id="6968f-102">Dependencies 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="6968f-102">Dependencies Property (SqlService Class)</span></span>
  <span data-ttu-id="6968f-103">取得相依於參考之服務的服務清單。</span><span class="sxs-lookup"><span data-stu-id="6968f-103">Gets a list of services that are dependent on the referenced service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6968f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6968f-104">Syntax</span></span>  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="6968f-105">組件</span><span class="sxs-lookup"><span data-stu-id="6968f-105">Parts</span></span>  
 <span data-ttu-id="6968f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="6968f-106">*object*</span></span>  
 <span data-ttu-id="6968f-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="6968f-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6968f-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="6968f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="6968f-109">string[] 陣列，其中包含相依於參考之服務的服務清單。</span><span class="sxs-lookup"><span data-stu-id="6968f-109">A string[] array that contains a list of services dependent on the referenced service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6968f-110">備註</span><span class="sxs-lookup"><span data-stu-id="6968f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6968f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6968f-111">See Also</span></span>  
 <span data-ttu-id="6968f-112">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6968f-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
