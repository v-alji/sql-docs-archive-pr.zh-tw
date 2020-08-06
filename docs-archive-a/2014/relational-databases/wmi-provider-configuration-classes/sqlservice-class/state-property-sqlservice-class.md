---
title: State 屬性 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702542"
---
# <a name="state-property-sqlservice-class"></a><span data-ttu-id="aecaf-102">State 屬性 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="aecaf-102">State Property (SqlService Class)</span></span>
  <span data-ttu-id="aecaf-103">取得或設定服務的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="aecaf-103">Gets or sets the current state of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aecaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="aecaf-104">Syntax</span></span>  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="aecaf-105">組件</span><span class="sxs-lookup"><span data-stu-id="aecaf-105">Parts</span></span>  
 <span data-ttu-id="aecaf-106">*object*</span><span class="sxs-lookup"><span data-stu-id="aecaf-106">*object*</span></span>  
 <span data-ttu-id="aecaf-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="aecaf-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="aecaf-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="aecaf-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="aecaf-109">指定服務狀態的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="aecaf-109">A uint32 value that specifies the state of the service.</span></span>  
  
 <span data-ttu-id="aecaf-110">它可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="aecaf-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="aecaf-111">1</span><span class="sxs-lookup"><span data-stu-id="aecaf-111">1</span></span>  
 <span data-ttu-id="aecaf-112">已停止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-112">Stopped.</span></span> <span data-ttu-id="aecaf-113">服務已停止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-113">The service is stopped.</span></span>  
  
 <span data-ttu-id="aecaf-114">2</span><span class="sxs-lookup"><span data-stu-id="aecaf-114">2</span></span>  
 <span data-ttu-id="aecaf-115">開始暫止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-115">Start Pending.</span></span> <span data-ttu-id="aecaf-116">服務正在等候開始。</span><span class="sxs-lookup"><span data-stu-id="aecaf-116">The service is waiting to start.</span></span>  
  
 <span data-ttu-id="aecaf-117">3</span><span class="sxs-lookup"><span data-stu-id="aecaf-117">3</span></span>  
 <span data-ttu-id="aecaf-118">停止暫止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-118">Stop Pending.</span></span> <span data-ttu-id="aecaf-119">服務正在等候停止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-119">The service is waiting to stop.</span></span>  
  
 <span data-ttu-id="aecaf-120">4</span><span class="sxs-lookup"><span data-stu-id="aecaf-120">4</span></span>  
 <span data-ttu-id="aecaf-121">執行中。</span><span class="sxs-lookup"><span data-stu-id="aecaf-121">Running.</span></span> <span data-ttu-id="aecaf-122">服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="aecaf-122">The service is running.</span></span>  
  
 <span data-ttu-id="aecaf-123">5</span><span class="sxs-lookup"><span data-stu-id="aecaf-123">5</span></span>  
 <span data-ttu-id="aecaf-124">繼續暫止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-124">Continue Pending.</span></span> <span data-ttu-id="aecaf-125">服務正在等候繼續。</span><span class="sxs-lookup"><span data-stu-id="aecaf-125">The service is waiting to continue.</span></span>  
  
 <span data-ttu-id="aecaf-126">6</span><span class="sxs-lookup"><span data-stu-id="aecaf-126">6</span></span>  
 <span data-ttu-id="aecaf-127">暫停暫止。</span><span class="sxs-lookup"><span data-stu-id="aecaf-127">Pause Pending.</span></span> <span data-ttu-id="aecaf-128">服務正在等候暫停。</span><span class="sxs-lookup"><span data-stu-id="aecaf-128">The service is waiting to pause.</span></span>  
  
 <span data-ttu-id="aecaf-129">7</span><span class="sxs-lookup"><span data-stu-id="aecaf-129">7</span></span>  
 <span data-ttu-id="aecaf-130">已暫停。</span><span class="sxs-lookup"><span data-stu-id="aecaf-130">Paused.</span></span> <span data-ttu-id="aecaf-131">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="aecaf-131">The service is paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aecaf-132">備註</span><span class="sxs-lookup"><span data-stu-id="aecaf-132">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecaf-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aecaf-133">See Also</span></span>  
 <span data-ttu-id="aecaf-134">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aecaf-134">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
