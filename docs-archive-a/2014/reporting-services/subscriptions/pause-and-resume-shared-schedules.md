---
title: 暫停及繼續共用排程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f525a15b07b79b5c0d37f9a88ed9483b351af326
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596464"
---
# <a name="pause-and-resume-shared-schedules"></a><span data-ttu-id="dd936-102">Pause and Resume Shared Schedules</span><span class="sxs-lookup"><span data-stu-id="dd936-102">Pause and Resume Shared Schedules</span></span>
  <span data-ttu-id="dd936-103">您可以暫停並繼續使用中的共用排程。</span><span class="sxs-lookup"><span data-stu-id="dd936-103">You can pause and resume a shared schedule that is in use.</span></span> <span data-ttu-id="dd936-104">暫停共用排程提供暫時凍結用於觸發報表處理與訂閱排程的方法。</span><span class="sxs-lookup"><span data-stu-id="dd936-104">Pausing a shared schedule provides a way to temporarily freeze a schedule that is used to trigger report processing and subscriptions.</span></span> <span data-ttu-id="dd936-105">只有共用排程可以暫停並繼續。</span><span class="sxs-lookup"><span data-stu-id="dd936-105">Only shared schedules can be paused and resumed.</span></span> <span data-ttu-id="dd936-106">您無法暫停報表特定排程。</span><span class="sxs-lookup"><span data-stu-id="dd936-106">You cannot pause report-specific schedules.</span></span>  
  
 <span data-ttu-id="dd936-107">您不能暫停和繼續已在進行中的報表處理。</span><span class="sxs-lookup"><span data-stu-id="dd936-107">You cannot pause and resume report processing that is in progress.</span></span> <span data-ttu-id="dd936-108">您只能暫停和繼續 SQL Server Agent 服務之排程佇列中的排程。</span><span class="sxs-lookup"><span data-stu-id="dd936-108">You can only pause and resume schedules that are in the scheduling queue of SQL Server Agent service.</span></span> <span data-ttu-id="dd936-109">進行中的作業是在排程引擎的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="dd936-109">A job that is in progress is outside the scope of the scheduling engine.</span></span> <span data-ttu-id="dd936-110">如需詳細資訊，請參閱 [管理執行中的處理序](manage-a-running-process.md)</span><span class="sxs-lookup"><span data-stu-id="dd936-110">For more information, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="dd936-111">當共用排程暫停時，允許任何可能發生的作業失效。</span><span class="sxs-lookup"><span data-stu-id="dd936-111">While a shared schedule is paused, any operations that would have occurred are allowed to lapse.</span></span> <span data-ttu-id="dd936-112">繼續共用排程之後，報表和訂閱處理就會按照伺服器的當地時間，在下次排程的時間進行。</span><span class="sxs-lookup"><span data-stu-id="dd936-112">After you resume a shared schedule, report and subscription processing occurs at the next scheduled time, using the local time of the server.</span></span> <span data-ttu-id="dd936-113">原生模式報表伺服器或 SharePoint 服務應用程式不會回頭處理在排程暫停期間原本應該執行的預定作業。</span><span class="sxs-lookup"><span data-stu-id="dd936-113">The native mode report server or SharePoint service applications, do not make up scheduled operations that would have occurred had the schedule not been paused.</span></span>  
  
 <span data-ttu-id="dd936-114">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="dd936-114">In this Topic:</span></span>  
  
-   [<span data-ttu-id="dd936-115">暫停及繼續共用排程 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="dd936-115">Pause and Resume Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="dd936-116">暫停及繼續共用排程 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="dd936-116">Pause and Resume Shared Schedules (SharePoint mode)</span></span>](#bkmk_sharepoint)  
  
##  <a name="pause-and-resume-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="dd936-117">暫停及繼續共用排程 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="dd936-117">Pause and Resume Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="dd936-118">若要暫停和繼續共用排程，請使用報表管理員的 [排程] 頁面。</span><span class="sxs-lookup"><span data-stu-id="dd936-118">To pause and resume a shared schedule, use the Schedules page in Report Manager.</span></span> <span data-ttu-id="dd936-119">您不能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，因為其未提供暫停和繼續排程的選項。</span><span class="sxs-lookup"><span data-stu-id="dd936-119">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]; it does not provide options for pausing and resuming schedules.</span></span> <span data-ttu-id="dd936-120">如需詳細資訊，請參閱 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="dd936-120">For more information, see [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md).</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="dd936-121">若要暫停或繼續共用排程</span><span class="sxs-lookup"><span data-stu-id="dd936-121">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="dd936-122">從報表管理員中，按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-122">From Report Manager Click, **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="dd936-123">按一下 **[排程]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-123">Click **Schedules**.</span></span>  
  
3.  <span data-ttu-id="dd936-124">選取排程，然後按一下功能區中的 **[暫停]** 或 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-124">Select the schedule, and click **Pause** or **Resume** in the ribbon.</span></span> <span data-ttu-id="dd936-125">如果排程目前為暫停狀態，則 **[狀態]** 資料行將包含 **[已暫停]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-125">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
##  <a name="pause-and-resume-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="dd936-126">暫停及繼續共用排程 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="dd936-126">Pause and Resume Shared Schedules (SharePoint mode)</span></span>  
 <span data-ttu-id="dd936-127">若要暫停及繼續共用排程，請使用 [站台設定] 頁面或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dd936-127">To pause and resume a shared schedule, use the Site Settings page or PowerShell.</span></span> <span data-ttu-id="dd936-128">排程是以每個 SharePoint 網站為單位管理。</span><span class="sxs-lookup"><span data-stu-id="dd936-128">Schedules are managed per SharePoint site.</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="dd936-129">若要暫停或繼續共用排程</span><span class="sxs-lookup"><span data-stu-id="dd936-129">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="dd936-130">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-130">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="dd936-131">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-131">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="dd936-132">在 [Reporting Services] 區段中，按一下 **[管理共用排程]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-132">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="dd936-133">選取排程，然後按一下 **[暫停選取的排程]** 或 **[執行選取的排程]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-133">Select the schedule, and click **Pause Selected Schedules** or **Run Selected Schedules**.</span></span> <span data-ttu-id="dd936-134">如果排程目前為暫停狀態，則 **[狀態]** 資料行將包含 **[已暫停]** 。</span><span class="sxs-lookup"><span data-stu-id="dd936-134">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd936-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd936-135">See Also</span></span>  
 <span data-ttu-id="dd936-136">[[排程]](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="dd936-136">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="dd936-137">[建立、修改和刪除共用排程](create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="dd936-137">[Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="dd936-138">[變更報表伺服器上的時區和時鐘設定](change-time-zones-and-clock-settings-on-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd936-138">[Change Time Zones and Clock Settings on a Report Server](change-time-zones-and-clock-settings-on-a-report-server.md) </span></span>  
 [<span data-ttu-id="dd936-139">管理執行中的處理序</span><span class="sxs-lookup"><span data-stu-id="dd936-139">Manage a Running Process</span></span>](manage-a-running-process.md)  
  
  
