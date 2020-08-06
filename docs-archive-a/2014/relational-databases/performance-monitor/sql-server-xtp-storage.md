---
title: XTP 儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: efd4a9eba36060d3d4bab9b371678ab2b2c409ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596674"
---
# <a name="xtp-storage"></a><span data-ttu-id="14609-102">XTP 儲存體</span><span class="sxs-lookup"><span data-stu-id="14609-102">XTP Storage</span></span>
  <span data-ttu-id="14609-103">XTP 儲存體效能物件包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中與 XTP 儲存體相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="14609-103">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="14609-104">下表描述**XTP 儲存體**計數器。</span><span class="sxs-lookup"><span data-stu-id="14609-104">This table describes the **XTP Storage** counters.</span></span>  
  
|<span data-ttu-id="14609-105">計數器</span><span class="sxs-lookup"><span data-stu-id="14609-105">Counter</span></span>|<span data-ttu-id="14609-106">描述</span><span class="sxs-lookup"><span data-stu-id="14609-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14609-107">**Checkpoints Closed**</span><span class="sxs-lookup"><span data-stu-id="14609-107">**Checkpoints Closed**</span></span>|<span data-ttu-id="14609-108">線上代理程式已關閉的檢查點計數。</span><span class="sxs-lookup"><span data-stu-id="14609-108">Count of checkpoints closed done by online agent.</span></span>|  
|<span data-ttu-id="14609-109">**Checkpoints Completed**</span><span class="sxs-lookup"><span data-stu-id="14609-109">**Checkpoints Completed**</span></span>|<span data-ttu-id="14609-110">離線檢查點執行緒已處理的檢查點計數。</span><span class="sxs-lookup"><span data-stu-id="14609-110">Count of checkpoints processed by offline checkpoint thread.</span></span>|  
|<span data-ttu-id="14609-111">**Core Merges Completed**</span><span class="sxs-lookup"><span data-stu-id="14609-111">**Core Merges Completed**</span></span>|<span data-ttu-id="14609-112">合併工作者執行緒已完成的核心合併數目。</span><span class="sxs-lookup"><span data-stu-id="14609-112">The number of core merges completed by the merge worker thread.</span></span> <span data-ttu-id="14609-113">這些合併仍然需要予以安裝。</span><span class="sxs-lookup"><span data-stu-id="14609-113">These merges still need to be installed.</span></span>|  
|<span data-ttu-id="14609-114">**Merge Policy Evaluations**</span><span class="sxs-lookup"><span data-stu-id="14609-114">**Merge Policy Evaluations**</span></span>|<span data-ttu-id="14609-115">自伺服器啟動後的合併原則評估數目。</span><span class="sxs-lookup"><span data-stu-id="14609-115">The number of merge policy evaluations since the server started.</span></span>|  
|<span data-ttu-id="14609-116">**Merge Requests Outstanding**</span><span class="sxs-lookup"><span data-stu-id="14609-116">**Merge Requests Outstanding**</span></span>|<span data-ttu-id="14609-117">自伺服器啟動後之未處理的合併要求數目。</span><span class="sxs-lookup"><span data-stu-id="14609-117">The number of merge requests outstanding since the server started.</span></span>|  
|<span data-ttu-id="14609-118">**Merges Abandoned**</span><span class="sxs-lookup"><span data-stu-id="14609-118">**Merges Abandoned**</span></span>|<span data-ttu-id="14609-119">由於失敗而放棄的合併數目。</span><span class="sxs-lookup"><span data-stu-id="14609-119">The number of merges abandoned due to failure.</span></span>|  
|<span data-ttu-id="14609-120">**Merges Installed**</span><span class="sxs-lookup"><span data-stu-id="14609-120">**Merges Installed**</span></span>|<span data-ttu-id="14609-121">已成功安裝的合併數目。</span><span class="sxs-lookup"><span data-stu-id="14609-121">The number of merges successfully installed.</span></span>|  
|<span data-ttu-id="14609-122">**Total Files Merged**</span><span class="sxs-lookup"><span data-stu-id="14609-122">**Total Files Merged**</span></span>|<span data-ttu-id="14609-123">已合併的來源檔案總數。</span><span class="sxs-lookup"><span data-stu-id="14609-123">The total number of source files merged.</span></span> <span data-ttu-id="14609-124">此計數可用來尋找合併中的平均來源檔案數目。</span><span class="sxs-lookup"><span data-stu-id="14609-124">This count can be used to find the average number of source files in the merge.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14609-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14609-125">See Also</span></span>  
 [<span data-ttu-id="14609-126">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="14609-126">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
