---
title: ErrorControl 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706313"
---
# <a name="errorcontrol-property-sqlservice-class"></a><span data-ttu-id="c86e7-102">ErrorControl 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="c86e7-102">ErrorControl Property (SqlService Class)</span></span>
  <span data-ttu-id="c86e7-103">當服務在啟動期間無法啟動時，取得或設定錯誤的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="c86e7-103">Gets or sets the severity of the error if the service fails to start during startup.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c86e7-104">Syntax</span></span>  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c86e7-105">組件</span><span class="sxs-lookup"><span data-stu-id="c86e7-105">Parts</span></span>  
 <span data-ttu-id="c86e7-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c86e7-106">*object*</span></span>  
 <span data-ttu-id="c86e7-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="c86e7-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c86e7-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="c86e7-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c86e7-109">字串值，可指定當服務在啟動期間失敗時所報告的錯誤嚴重性。</span><span class="sxs-lookup"><span data-stu-id="c86e7-109">A string value that specifies the error severity reported if the service fails during startup.</span></span> <span data-ttu-id="c86e7-110">下表顯示可能的值。</span><span class="sxs-lookup"><span data-stu-id="c86e7-110">The following table shows the possible values.</span></span>  
  
 <span data-ttu-id="c86e7-111">忽略</span><span class="sxs-lookup"><span data-stu-id="c86e7-111">Ignore</span></span>  
 <span data-ttu-id="c86e7-112">不通知使用者。</span><span class="sxs-lookup"><span data-stu-id="c86e7-112">User is not notified.</span></span>  
  
 <span data-ttu-id="c86e7-113">正常</span><span class="sxs-lookup"><span data-stu-id="c86e7-113">Normal</span></span>  
 <span data-ttu-id="c86e7-114">通知使用者。</span><span class="sxs-lookup"><span data-stu-id="c86e7-114">User is notified.</span></span>  
  
 <span data-ttu-id="c86e7-115">Severe</span><span class="sxs-lookup"><span data-stu-id="c86e7-115">Severe</span></span>  
 <span data-ttu-id="c86e7-116">使用上次的正確組態重新啟動系統。</span><span class="sxs-lookup"><span data-stu-id="c86e7-116">System is restarted with the last-known-good configuration.</span></span>  
  
 <span data-ttu-id="c86e7-117">重要</span><span class="sxs-lookup"><span data-stu-id="c86e7-117">Critical</span></span>  
 <span data-ttu-id="c86e7-118">系統嘗試以正確的組態重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c86e7-118">System attempts to restart with a good configuration.</span></span>  
  
 <span data-ttu-id="c86e7-119">Unknown</span><span class="sxs-lookup"><span data-stu-id="c86e7-119">Unknown</span></span>  
 <span data-ttu-id="c86e7-120">嚴重性未知。</span><span class="sxs-lookup"><span data-stu-id="c86e7-120">The severity is unknown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c86e7-121">備註</span><span class="sxs-lookup"><span data-stu-id="c86e7-121">Remarks</span></span>  
 <span data-ttu-id="c86e7-122">此值表示在發生失敗時由啟動程式採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c86e7-122">The value indicates the action taken by the startup program if a failure occurs.</span></span> <span data-ttu-id="c86e7-123">電腦系統會記錄所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="c86e7-123">All errors are logged by the computer system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86e7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c86e7-124">See Also</span></span>  
 <span data-ttu-id="c86e7-125">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c86e7-125">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
