---
title: 排程屬性 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a61837cd977526021be948d8c74a93eba6506e67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594368"
---
# <a name="schedule-properties-general-page"></a><span data-ttu-id="dcbdb-102">排程屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="dcbdb-102">Schedule Properties (General Page)</span></span>
  <span data-ttu-id="dcbdb-103">使用此頁面即可檢視或修改共用排程。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-103">Use this page to view or modify a shared schedule.</span></span> <span data-ttu-id="dcbdb-104">共用排程可以用來取代報表特定或訂閱特定的排程。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="dcbdb-105">對排程所做的變更會在您儲存排程之後套用。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-105">Changes to the schedule are applied after you save the schedule.</span></span> <span data-ttu-id="dcbdb-106">編輯排程並不會影響目前正在進行中的作業。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-106">Editing a schedule has no effect on jobs that are currently in progress.</span></span> <span data-ttu-id="dcbdb-107">如果您編輯排程時，該排程正在使用中，則系統會允許根據該排程觸發的所有目前處理中報表和訂閱繼續完成。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-107">If you edit a schedule while it is being used, all currently processing reports and subscriptions triggered from that schedule will be allowed to finish.</span></span>  
  
 <span data-ttu-id="dcbdb-108">單一排程中無法支援所有的頻率組合。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-108">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="dcbdb-109">例如，若要在每星期五下午 12:00</span><span class="sxs-lookup"><span data-stu-id="dcbdb-109">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="dcbdb-110">到下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-110">and 4:00 P.M.</span></span> <span data-ttu-id="dcbdb-111">就必須建立指定星期五為執行日期的兩個每日排程，一個開始時間為下午 12:00，</span><span class="sxs-lookup"><span data-stu-id="dcbdb-111">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="dcbdb-112">另一個開始時間為下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-112">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="dcbdb-113">排程處理是以主控和處理排程之報表伺服器的本機時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-113">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="dcbdb-114">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、連接至報表伺服器、開啟 [**共用**排程] 資料夾、以滑鼠右鍵按一下共用排程，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-114">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcbdb-115">並非所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本都提供此功能，而且在您執行沒有此功能的版本時，此頁面並不會出現。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-115">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and this page does not appear when you are running an edition which does not have this feature.</span></span> <span data-ttu-id="dcbdb-116">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2012 (版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-116">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcbdb-117">選項。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-117">Options</span></span>  
 <span data-ttu-id="dcbdb-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-118">**Name**</span></span>  
 <span data-ttu-id="dcbdb-119">指定共用排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-119">Specifies the name for the shared schedule.</span></span>  
  
 <span data-ttu-id="dcbdb-120">**開始執行此排程於**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-120">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="dcbdb-121">指定此排程的開始日期。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-121">Specifies a start date for this schedule.</span></span>  
  
 <span data-ttu-id="dcbdb-122">**停止此排程於**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-122">**Stop this schedule on**</span></span>  
 <span data-ttu-id="dcbdb-123">指定此排程的到期日。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-123">Specifies an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="dcbdb-124">**型別**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-124">**Type**</span></span>  
 <span data-ttu-id="dcbdb-125">指定循環模式主要是以小時、天、週、月為基礎，還是只執行一次。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-125">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, months, or only runs once.</span></span>  
  
 <span data-ttu-id="dcbdb-126">**小時 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-126">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="dcbdb-127">指定以小時為間隔的選項，來執行排程的作業 (例如，每 6 小時執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-127">Specifies options for running a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="dcbdb-128">您可以使用小時和分鐘來指定間隔。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-128">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="dcbdb-129">**天 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-129">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="dcbdb-130">指定以天數為間隔的選項，來執行排程的作業 (例如，每 2 天執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-130">Specifies options for running a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="dcbdb-131">您可以使用日來指定間隔，並指定希望排程執行的時間。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-131">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="dcbdb-132">**週 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-132">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="dcbdb-133">指定以週為間隔或是以週為基礎的選項，來執行排程的作業 (例如，每隔一週執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-133">Specifies options for running a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="dcbdb-134">您可以指定每週的排程，包括執行排程的日子和時間。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-134">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="dcbdb-135">**月 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-135">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="dcbdb-136">指定以月為間隔或是以月為基礎的選項，來執行排程的作業。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-136">Specifies options for running a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="dcbdb-137">您可以指定每月的排程，包括執行排程的日子和時間。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-137">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="dcbdb-138">排程中可以省略特定的月份。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-138">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="dcbdb-139">**單次**</span><span class="sxs-lookup"><span data-stu-id="dcbdb-139">**Once**</span></span>  
 <span data-ttu-id="dcbdb-140">指定排程只在特定的日期和時間執行一次。</span><span class="sxs-lookup"><span data-stu-id="dcbdb-140">Specifies a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbdb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcbdb-141">See Also</span></span>  
 <span data-ttu-id="dcbdb-142">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="dcbdb-142">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="dcbdb-143">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="dcbdb-143">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="dcbdb-144">[建立、修改和刪除共用排程](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="dcbdb-144">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="dcbdb-145">排程</span><span class="sxs-lookup"><span data-stu-id="dcbdb-145">Schedules</span></span>](../subscriptions/schedules.md)  
  
  
