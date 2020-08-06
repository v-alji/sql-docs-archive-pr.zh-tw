---
title: 取消報表伺服器作業 (Management Studio) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0ef8ada32aab4ac368871da711d0fe63fff7620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706182"
---
# <a name="cancel-report-server-jobs-management-studio"></a><span data-ttu-id="7b7d5-102">取消報表伺服器作業 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7b7d5-102">Cancel Report Server Jobs (Management Studio)</span></span>
  <span data-ttu-id="7b7d5-103">您可以使用 [取消報表伺服器作業]  對話方塊來檢視或取消進行中的報表。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-103">Use the **Cancel Report Server Jobs** dialog box to view or cancel in-progress reports.</span></span> <span data-ttu-id="7b7d5-104">這個對話方塊會顯示目前正在報表伺服器上執行的所有作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-104">This dialog box shows all jobs that are currently running on the report server.</span></span> <span data-ttu-id="7b7d5-105">雖然您無法暫停或重新啟動目前正在處理中的作業，但是如果完成作業需要花太長的時間，您就可以取消所有作業或個別作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-105">Although you cannot pause or restart jobs that are currently processing, you can cancel all jobs or individual jobs if they are taking too long to complete.</span></span>  
  
 <span data-ttu-id="7b7d5-106">您可以取消使用者作業和系統作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-106">You can cancel user jobs and system jobs.</span></span>  
  
-   <span data-ttu-id="7b7d5-107">使用者作業是由個別使用者起始的任何作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-107">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="7b7d5-108">這種作業包括視需要執行報表、手動建立報表記錄快照集，或者手動建立報表執行快照集。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-108">This includes running a report on-demand, manually creating a report history snapshot, or manually creating report execution snapshot.</span></span> <span data-ttu-id="7b7d5-109">進行中標準訂閱也是使用者作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-109">An in-progress standard subscription is also a user job.</span></span>  
  
-   <span data-ttu-id="7b7d5-110">系統作業是由報表伺服器起始的作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-110">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="7b7d5-111">系統作業包括排程的報表處理。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-111">System jobs include scheduled report processing.</span></span>  
  
 <span data-ttu-id="7b7d5-112">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，連接至報表伺服器，以滑鼠右鍵按一下 [作業]  ，然後按一下 [取消所有作業]  。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Jobs**, and then click **Cancel All Jobs**.</span></span> <span data-ttu-id="7b7d5-113">您也可以開啟 [作業]  ，以滑鼠右鍵按一下正在報表伺服器上執行的作業，然後選取 [取消作業]  。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-113">You can also open **Jobs**, right-click a job that is running on the report server, and select **Cancel Job(s)**.</span></span>  
  
 <span data-ttu-id="7b7d5-114">取消作業之前，您可以檢視其屬性，以便判斷該作業的開始時間。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-114">Before cancelling a job, you can view its properties to determine when the job started.</span></span> <span data-ttu-id="7b7d5-115">如需詳細資訊，請參閱[作業屬性 &#40;Management Studio&#41;](job-properties-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-115">For more information, see [Job Properties &#40;Management Studio&#41;](job-properties-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b7d5-116">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services 不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-116">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="7b7d5-117">因此，當您執行 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]時，不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-117">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b7d5-118">選項。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-118">Options</span></span>  
 <span data-ttu-id="7b7d5-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-119">**Name**</span></span>  
 <span data-ttu-id="7b7d5-120">顯示報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-120">Shows the name of the report.</span></span> <span data-ttu-id="7b7d5-121">依據描述來識別訂閱。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-121">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="7b7d5-122">**型別**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-122">**Type**</span></span>  
 <span data-ttu-id="7b7d5-123">有效值為 [使用者]  和 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-123">Valid values are **User** and **System**.</span></span>  
  
 <span data-ttu-id="7b7d5-124">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-124">**Start Time**</span></span>  
 <span data-ttu-id="7b7d5-125">顯示作業的開始時間。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-125">Shows when the job started.</span></span>  
  
 <span data-ttu-id="7b7d5-126">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-126">**User Name**</span></span>  
 <span data-ttu-id="7b7d5-127">若為使用者所起始的作業，這個資料行會顯示該使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-127">For jobs that are initiated by a user, this column shows the name of the user.</span></span>  
  
 <span data-ttu-id="7b7d5-128">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-128">**Status**</span></span>  
 <span data-ttu-id="7b7d5-129">顯示作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-129">Shows the status of the job.</span></span> <span data-ttu-id="7b7d5-130">有效值為 **[新增]** 和 **[正在執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-130">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="7b7d5-131">當作業啟動時，狀態永遠是 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-131">Status is always **New** when the job begins.</span></span> <span data-ttu-id="7b7d5-132">60 秒之後，狀態會變更為 **[正在執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-132">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="7b7d5-133">您必須重新整理此頁面，才能收取變更。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-133">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="7b7d5-134">**確定**</span><span class="sxs-lookup"><span data-stu-id="7b7d5-134">**OK**</span></span>  
 <span data-ttu-id="7b7d5-135">取消單一作業或多項作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-135">Cancel a single job or multiple jobs.</span></span> <span data-ttu-id="7b7d5-136">作業會立即取消而且無法繼續進行。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-136">The jobs are cancelled immediately and cannot be resumed.</span></span> <span data-ttu-id="7b7d5-137">如果您不小心取消了作業，就必須再次要求報表或訂閱，才能啟動新的作業。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-137">If you mistakenly cancel a job, you must request the report or subscription again to start a new job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7d5-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b7d5-138">See Also</span></span>  
 <span data-ttu-id="7b7d5-139">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7b7d5-139">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="7b7d5-140">[連接至 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7b7d5-140">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="7b7d5-141">管理執行中的處理序</span><span class="sxs-lookup"><span data-stu-id="7b7d5-141">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
