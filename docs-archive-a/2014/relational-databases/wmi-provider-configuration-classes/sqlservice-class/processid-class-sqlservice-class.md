---
title: ProcessId 類別 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c4c40eea826b5009e52d26b1d930eaf5febbcdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595843"
---
# <a name="processid-class-sqlservice-class"></a><span data-ttu-id="105af-102">ProcessId 類別 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="105af-102">ProcessId Class (SqlService Class)</span></span>
  <span data-ttu-id="105af-103">取得可唯一識別服務的系統處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="105af-103">Gets the system process ID that uniquely identifies a service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105af-104">語法</span><span class="sxs-lookup"><span data-stu-id="105af-104">Syntax</span></span>  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="105af-105">組件</span><span class="sxs-lookup"><span data-stu-id="105af-105">Parts</span></span>  
 <span data-ttu-id="105af-106">*object*</span><span class="sxs-lookup"><span data-stu-id="105af-106">*object*</span></span>  
 <span data-ttu-id="105af-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="105af-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="105af-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="105af-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="105af-109">指定可唯一識別處理序之識別碼的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="105af-109">A `uint32` value that specifies the ID that uniquely identifies the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="105af-110">備註</span><span class="sxs-lookup"><span data-stu-id="105af-110">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="105af-111">範例</span><span class="sxs-lookup"><span data-stu-id="105af-111">Example</span></span>  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a><span data-ttu-id="105af-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="105af-112">See Also</span></span>  
 <span data-ttu-id="105af-113">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="105af-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
