---
title: 作業活動監視器 (篩選設定) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feba7b992d5d1d375b93df12135487a092792ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598353"
---
# <a name="job-activity-monitor-filter-settings"></a><span data-ttu-id="902ad-102">作業活動監視器 (篩選設定)</span><span class="sxs-lookup"><span data-stu-id="902ad-102">Job Activity Monitor (Filter Settings)</span></span>
  <span data-ttu-id="902ad-103">使用此頁面來減少可以在作業活動監視器看到的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="902ad-103">Use this page to reduce the number of rows visible in the Job Activity Monitor.</span></span> <span data-ttu-id="902ad-104">在一或數個可用的方塊中輸入準則，只顯示符合指定值的資料列。</span><span class="sxs-lookup"><span data-stu-id="902ad-104">Enter criteria in one or several of the available boxes, to show only the rows that meet the specified values.</span></span> <span data-ttu-id="902ad-105">有些方塊 (例如 [狀態]  或 [封鎖類型]  ) 提供有限數目的可能值，經由下拉式清單提供。</span><span class="sxs-lookup"><span data-stu-id="902ad-105">Some of the boxes, such as **Status** or **Blocking Type** offer a finite number of possible values, provided by a drop-down list.</span></span> <span data-ttu-id="902ad-106">其他的方塊 (例如 [應用程式]  ) 則允許您以逗號分隔的清單，輸入任何值以及隨您想要之數量的值。</span><span class="sxs-lookup"><span data-stu-id="902ad-106">Others, such as **Application,** allow you to enter whatever value and as many values as you wish, as a comma separated list.</span></span> <span data-ttu-id="902ad-107">工具列圖示允許您依類別或字母順序排序可用的方塊。</span><span class="sxs-lookup"><span data-stu-id="902ad-107">Toolbar icons allow you to sort the available boxes by category or alphabetically.</span></span> <span data-ttu-id="902ad-108">按一下準則以顯示每個準則的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="902ad-108">Click the criteria to show a short description of the each one.</span></span>  
  
 <span data-ttu-id="902ad-109">若要篩選作業活動監視器，請依照需要提供篩選準則，並按一下 [套用篩選]  ，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="902ad-109">To filter the Job Activity Monitor, provide as many filter criteria as you want, click **Apply filter**, and then click **OK**.</span></span>  
  
## <a name="all-jobs"></a><span data-ttu-id="902ad-110">所有作業</span><span class="sxs-lookup"><span data-stu-id="902ad-110">All Jobs</span></span>  
 <span data-ttu-id="902ad-111">這組篩選準則可在篩選作業活動監視器時使用。</span><span class="sxs-lookup"><span data-stu-id="902ad-111">This group of filter criteria is available when filtering the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="902ad-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="902ad-112">**Name**</span></span>  
 <span data-ttu-id="902ad-113">依名稱篩選作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-113">Filter jobs by name.</span></span>  
  
 <span data-ttu-id="902ad-114">**下次執行**</span><span class="sxs-lookup"><span data-stu-id="902ad-114">**Next Run**</span></span>  
 <span data-ttu-id="902ad-115">依下一個排程的執行日期篩選。</span><span class="sxs-lookup"><span data-stu-id="902ad-115">Filter by the date next scheduled to run.</span></span>  
  
 <span data-ttu-id="902ad-116">**可執行的**</span><span class="sxs-lookup"><span data-stu-id="902ad-116">**Runnable**</span></span>  
 <span data-ttu-id="902ad-117">檢視可以執行的作業，或無法執行的作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-117">View jobs that can be run, or jobs that cannot be run.</span></span> <span data-ttu-id="902ad-118">選取 [是]  只能檢視可以執行的作業，選取 [否]  只能檢視無法執行的作業，選取 [全部]  則能同時檢視可以執行與無法執行的作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-118">Select **Yes** to view only jobs that can be run, select **No** to view only jobs that cannot be run, or select **All** to view both jobs that can be run and those that cannot.</span></span>  
  
 <span data-ttu-id="902ad-119">**最後執行**</span><span class="sxs-lookup"><span data-stu-id="902ad-119">**Last Run**</span></span>  
 <span data-ttu-id="902ad-120">依上次執行日期篩選。</span><span class="sxs-lookup"><span data-stu-id="902ad-120">Filter by the date last run.</span></span>  
  
 <span data-ttu-id="902ad-121">**上次執行結果**</span><span class="sxs-lookup"><span data-stu-id="902ad-121">**Last Run Outcome**</span></span>  
 <span data-ttu-id="902ad-122">依上次執行作業的狀態篩選作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-122">Filter jobs by the status last time the jobs were run.</span></span>  
  
 <span data-ttu-id="902ad-123">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="902ad-123">**Enabled**</span></span>  
 <span data-ttu-id="902ad-124">只檢視已啟用或未啟用的作業</span><span class="sxs-lookup"><span data-stu-id="902ad-124">View only enabled or not enabled jobs</span></span>  
  
 <span data-ttu-id="902ad-125">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="902ad-125">**Category**</span></span>  
 <span data-ttu-id="902ad-126">依作業類別目錄篩選作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-126">Filter jobs by the job category.</span></span>  
  
 <span data-ttu-id="902ad-127">**已排程**</span><span class="sxs-lookup"><span data-stu-id="902ad-127">**Scheduled**</span></span>  
 <span data-ttu-id="902ad-128">檢視具有排程或無排程的所有作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-128">View all jobs with schedules, or without schedules.</span></span>  
  
 <span data-ttu-id="902ad-129">**狀態**</span><span class="sxs-lookup"><span data-stu-id="902ad-129">**Status**</span></span>  
 <span data-ttu-id="902ad-130">依狀態篩選作業。</span><span class="sxs-lookup"><span data-stu-id="902ad-130">Filter jobs by the status.</span></span>  
  
## <a name="description-area"></a><span data-ttu-id="902ad-131">描述區域</span><span class="sxs-lookup"><span data-stu-id="902ad-131">Description Area</span></span>  
 <span data-ttu-id="902ad-132">**描述方塊**</span><span class="sxs-lookup"><span data-stu-id="902ad-132">**Description Box**</span></span>  
 <span data-ttu-id="902ad-133">這個未命名的方塊，在準則被選取時提供準則的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="902ad-133">This unnamed box provides a short description of the criteria as they are selected.</span></span>  
  
 <span data-ttu-id="902ad-134">**套用篩選**</span><span class="sxs-lookup"><span data-stu-id="902ad-134">**Apply filter**</span></span>  
 <span data-ttu-id="902ad-135">若要套用篩選，請按一下 [套用**篩選**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="902ad-135">To apply the filter, click **Apply filter** and then click **OK**.</span></span> <span data-ttu-id="902ad-136">若要在 [**篩選設定**] 對話方塊中保留篩選設定，但不套用它們，請取消選取 [套用**篩選**]，然後按一下 **[確定]** 以顯示所有資料列。</span><span class="sxs-lookup"><span data-stu-id="902ad-136">To retain the filter settings in the **Filter Settings** dialog box, but not apply them, uncheck **Apply filter**, and then click **OK**, to display all rows.</span></span>  
  
 <span data-ttu-id="902ad-137">**Clear**</span><span class="sxs-lookup"><span data-stu-id="902ad-137">**Clear**</span></span>  
 <span data-ttu-id="902ad-138">將篩選設定恢復成預設值。</span><span class="sxs-lookup"><span data-stu-id="902ad-138">Returns the filter settings back to the default settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902ad-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="902ad-139">See Also</span></span>  
 [<span data-ttu-id="902ad-140">監視作業活動</span><span class="sxs-lookup"><span data-stu-id="902ad-140">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
