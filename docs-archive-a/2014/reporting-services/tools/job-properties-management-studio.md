---
title: 作業屬性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4d309ba78a21114cf51c48f0a5c5b3b2f7c2500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700708"
---
# <a name="job-properties-management-studio"></a><span data-ttu-id="4c0ae-102">作業屬性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4c0ae-102">Job Properties (Management Studio)</span></span>
  <span data-ttu-id="4c0ae-103">您可以使用 [作業屬性]  頁面來檢視有關進行中報表或訂閱的資訊，然後再加以取消。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-103">Use the **Job Properties** page to view information about an in-progress report or subscription before you cancel it.</span></span>  
  
 <span data-ttu-id="4c0ae-104">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連線至報表伺服器，然後開啟 [作業]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, and open the **Jobs** folder.</span></span> <span data-ttu-id="4c0ae-105">以滑鼠右鍵按一下執行中的作業，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-105">Right-click a job that is running, and then click **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c0ae-106">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services 不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-106">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="4c0ae-107">因此，當您執行 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]時，不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-107">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="4c0ae-108">工作</span><span class="sxs-lookup"><span data-stu-id="4c0ae-108">Tasks</span></span>  
 <span data-ttu-id="4c0ae-109">在您檢視有關某項作業的資訊之前，請重新整理此頁面，以便擷取報表伺服器上目前正在執行之作業的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="4c0ae-109">Before you can view information about a job, refresh the page to retrieve information about jobs that are currently running on the report server:</span></span>  
  
1.  <span data-ttu-id="4c0ae-110">開啟報表伺服器資料夾。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-110">Open the report server folder.</span></span>  
  
2.  <span data-ttu-id="4c0ae-111">以滑鼠右鍵按一下 [作業]  ，然後按一下 [重新整理]  。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-111">Right-click **Jobs**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="4c0ae-112">如果已列出作業，請以滑鼠右鍵按一下該作業，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-112">If a job is listed, right-click the job, and then click **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c0ae-113">選項。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-113">Options</span></span>  
 <span data-ttu-id="4c0ae-114">**作業識別碼**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-114">**Job ID**</span></span>  
 <span data-ttu-id="4c0ae-115">在處理作業時指派給作業的 GUID。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-115">A GUID that is assigned to a job while it is processing.</span></span> <span data-ttu-id="4c0ae-116">此值是在每次報表或訂閱執行時隨機產生的。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-116">The value is randomly generated each time a report or subscription runs.</span></span>  
  
 <span data-ttu-id="4c0ae-117">**作業狀態**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-117">**Job Status**</span></span>  
 <span data-ttu-id="4c0ae-118">有效值為 **[新增]** 和 **[正在執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-118">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="4c0ae-119">當作業啟動時，狀態永遠是 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-119">Status is always **New** when the job begins.</span></span> <span data-ttu-id="4c0ae-120">60 秒之後，狀態會變更為 **[正在執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-120">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="4c0ae-121">您必須重新整理此頁面，才能收取變更。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-121">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="4c0ae-122">**作業類型**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-122">**Job Type**</span></span>  
 <span data-ttu-id="4c0ae-123">有效值為 [使用者]  和 [系統]  。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-123">Valid values are **User** and **System**.</span></span> <span data-ttu-id="4c0ae-124">使用者作業是由個別使用者起始的任何作業。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-124">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="4c0ae-125">這種作業包括視需要執行報表、手動產生報表記錄快照集，或者手動建立報表執行快照集。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-125">This includes running a report on-demand, manually generating a report history snapshot, or manually creating a report execution snapshot.</span></span> <span data-ttu-id="4c0ae-126">進行中標準訂閱也是使用者作業。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-126">An in-progress standard subscription is also a user job.</span></span> <span data-ttu-id="4c0ae-127">系統作業是由報表伺服器起始的作業。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-127">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="4c0ae-128">系統作業包括由排程觸發的報表處理。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-128">System jobs include report processing that is triggered by a schedule.</span></span>  
  
 <span data-ttu-id="4c0ae-129">**作業動作**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-129">**Job Action**</span></span>  
 <span data-ttu-id="4c0ae-130">若為報表，此資料行會顯示執行中的報表執行處理序。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-130">For reports, this column shows which report execution processes are underway.</span></span> <span data-ttu-id="4c0ae-131">這個值永遠是 [轉譯]  。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-131">This value is always **Render**.</span></span>  
  
 <span data-ttu-id="4c0ae-132">**作業描述**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-132">**Job Description**</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4c0ae-133">預設不會提供作業描述。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-133">does not provide job descriptions by default.</span></span>  
  
 <span data-ttu-id="4c0ae-134">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-134">**Server Name**</span></span>  
 <span data-ttu-id="4c0ae-135">顯示正在處理此作業之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-135">Shows the name of the report server that is processing the job.</span></span> <span data-ttu-id="4c0ae-136">如果您設定了向外延展部署，這個值將會顯示正在處理此作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-136">If you configured a scale-out deployment, this value will show which server is processing the job.</span></span>  
  
 <span data-ttu-id="4c0ae-137">**報表名稱**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-137">**Report Name**</span></span>  
 <span data-ttu-id="4c0ae-138">顯示報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-138">Shows the name of the report.</span></span> <span data-ttu-id="4c0ae-139">依據描述來識別訂閱。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-139">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="4c0ae-140">**報表路徑**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-140">**Report Path**</span></span>  
 <span data-ttu-id="4c0ae-141">顯示報表伺服器資料夾階層中之報表的路徑。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-141">Shows the path of the report in the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="4c0ae-142">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-142">**Start Time**</span></span>  
 <span data-ttu-id="4c0ae-143">顯示處理序的開始時間。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-143">Shows when the process started.</span></span>  
  
 <span data-ttu-id="4c0ae-144">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="4c0ae-144">**User Name**</span></span>  
 <span data-ttu-id="4c0ae-145">若為使用者起始的處理序，此資料行會顯示使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-145">For processes initiated by a user, this column shows the name of the user.</span></span> <span data-ttu-id="4c0ae-146">若為系統作業，這就是報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4c0ae-146">For system jobs, this is the name of the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0ae-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c0ae-147">See Also</span></span>  
 <span data-ttu-id="4c0ae-148">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4c0ae-148">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="4c0ae-149">[連接至 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="4c0ae-149">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="4c0ae-150">管理執行中的處理序</span><span class="sxs-lookup"><span data-stu-id="4c0ae-150">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
