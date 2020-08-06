---
title: 新增共用排程 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newschedule.f1
ms.assetid: b2c69586-d98e-4933-827d-f5e6c15c5203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6afd406730f815d3ab61e59cdebd21d564daa74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593798"
---
# <a name="new-shared-schedule-management-studio"></a><span data-ttu-id="eafec-102">新增共用排程 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eafec-102">New Shared Schedule (Management Studio)</span></span>
  <span data-ttu-id="eafec-103">您可以使用這個頁面來建立共用排程，以便執行已發行的報表和訂閱。</span><span class="sxs-lookup"><span data-stu-id="eafec-103">Use this page to create a shared schedule to run published reports and subscriptions.</span></span> <span data-ttu-id="eafec-104">共用排程可以用來取代報表特定或訂閱特定的排程。</span><span class="sxs-lookup"><span data-stu-id="eafec-104">Shared schedules can be used in place of report-specific or subscription-specific schedules.</span></span> <span data-ttu-id="eafec-105">集中式排程資訊以及暫停和繼續排程作業的能力是區別共用排程與項目特有排程的兩個重要功能。</span><span class="sxs-lookup"><span data-stu-id="eafec-105">Centralized schedule information and the ability to pause and resume scheduled operations are two key features that distinguish shared schedules from item-specific schedules.</span></span>  
  
 <span data-ttu-id="eafec-106">單一排程中無法支援所有的頻率組合。</span><span class="sxs-lookup"><span data-stu-id="eafec-106">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="eafec-107">例如，若要在每星期五下午 12:00</span><span class="sxs-lookup"><span data-stu-id="eafec-107">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="eafec-108">到下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="eafec-108">and 4:00 P.M.</span></span> <span data-ttu-id="eafec-109">就必須建立指定星期五為執行日期的兩個每日排程，一個開始時間為下午 12:00，</span><span class="sxs-lookup"><span data-stu-id="eafec-109">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="eafec-110">另一個開始時間為下午 4:00。</span><span class="sxs-lookup"><span data-stu-id="eafec-110">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="eafec-111">排程處理是以主控和處理排程之報表伺服器的本機時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="eafec-111">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
 <span data-ttu-id="eafec-112">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、連線至報表伺服器、以滑鼠右鍵按一下 [共用排程]  ，然後選取 [新增排程]  。</span><span class="sxs-lookup"><span data-stu-id="eafec-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Shared Schedule**, and select **New Schedule**.</span></span> <span data-ttu-id="eafec-113">若要儲存排程，SQL Server Agent 服務必須正在執行。</span><span class="sxs-lookup"><span data-stu-id="eafec-113">To save the schedule, SQL Server Agent service must be running.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eafec-114">並非所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="eafec-114">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eafec-115">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本支援的功能清單，請參閱 [SQL Server 2012 版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="eafec-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="eafec-116">選項。</span><span class="sxs-lookup"><span data-stu-id="eafec-116">Options</span></span>  
 <span data-ttu-id="eafec-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafec-117">**Name**</span></span>  
 <span data-ttu-id="eafec-118">鍵入共用排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="eafec-118">Type a name for the shared schedule.</span></span> <span data-ttu-id="eafec-119">當使用者針對報表和訂閱選取共用排程時，這個名稱會顯示在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="eafec-119">This name appears in drop-down lists when users select a shared schedule for reports and subscriptions.</span></span> <span data-ttu-id="eafec-120">請務必提供可輕易地容納在清單中而且可輕易地區別共用排程的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="eafec-120">Be sure to provide a descriptive name that fits easily within a list and that easily distinguishes one shared schedule from another.</span></span> <span data-ttu-id="eafec-121">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="eafec-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="eafec-122">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="eafec-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="eafec-123">指定名稱時，請勿使用下列字元：</span><span class="sxs-lookup"><span data-stu-id="eafec-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="eafec-124">; ?</span><span class="sxs-lookup"><span data-stu-id="eafec-124">; ?</span></span> <span data-ttu-id="eafec-125">： \@ & = +，$/\*\< ></span><span class="sxs-lookup"><span data-stu-id="eafec-125">: \@ & = + , $ / \* \< ></span></span>  
  
 <span data-ttu-id="eafec-126">" /</span><span class="sxs-lookup"><span data-stu-id="eafec-126">" /</span></span>  
  
 <span data-ttu-id="eafec-127">**開始執行此排程於**</span><span class="sxs-lookup"><span data-stu-id="eafec-127">**Begin running this schedule on**</span></span>  
 <span data-ttu-id="eafec-128">指定此排程的開始日期。</span><span class="sxs-lookup"><span data-stu-id="eafec-128">Specify a start date for this schedule.</span></span>  
  
 <span data-ttu-id="eafec-129">**停止此排程於**</span><span class="sxs-lookup"><span data-stu-id="eafec-129">**Stop this schedule on**</span></span>  
 <span data-ttu-id="eafec-130">指定此排程的到期日。</span><span class="sxs-lookup"><span data-stu-id="eafec-130">Specify an expiration date for this schedule.</span></span>  
  
 <span data-ttu-id="eafec-131">**型別**</span><span class="sxs-lookup"><span data-stu-id="eafec-131">**Type**</span></span>  
 <span data-ttu-id="eafec-132">指定循環模式主要是以小時、天、週或月為基礎。</span><span class="sxs-lookup"><span data-stu-id="eafec-132">Specifies whether the recurrence pattern is based primarily on hours, days, weeks, or months.</span></span>  
  
 <span data-ttu-id="eafec-133">**小時 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="eafec-133">**Hour (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="eafec-134">選取選項以便每隔幾個小時的時間執行已排程的作業 (例如，每 6 個小時執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="eafec-134">Select options to run a scheduled operation in intervals of an hour (for example, to run a report every 6 hours).</span></span> <span data-ttu-id="eafec-135">您可以使用小時和分鐘來指定間隔。</span><span class="sxs-lookup"><span data-stu-id="eafec-135">You can specify the interval in hours and minutes.</span></span>  
  
 <span data-ttu-id="eafec-136">**天 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="eafec-136">**Day (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="eafec-137">選取選項以便每隔幾天的時間執行已排程的作業 (例如，每 2 天執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="eafec-137">Select options to run a scheduled operation in intervals of days (for example, to run a report every 2 days).</span></span> <span data-ttu-id="eafec-138">您可以使用日來指定間隔，並指定希望排程執行的時間。</span><span class="sxs-lookup"><span data-stu-id="eafec-138">You can specify the interval in days and at the hour and minute you want the schedule to run.</span></span>  
  
 <span data-ttu-id="eafec-139">**週 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="eafec-139">**Week (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="eafec-140">選取選項以便每隔幾週的時間執行已排程的作業，或是您希望重複執行的模式是以週為基礎時 (例如，每隔一週執行報表一次)。</span><span class="sxs-lookup"><span data-stu-id="eafec-140">Select options to run a scheduled operation in intervals of a week or when the pattern that you want to repeat is based on weeks (for example, to run a report every other week).</span></span> <span data-ttu-id="eafec-141">您可以指定每週的排程，包括執行排程的日子和時間。</span><span class="sxs-lookup"><span data-stu-id="eafec-141">You can specify a weekly schedule to the day, hour, and minute that you want the schedule to run.</span></span>  
  
 <span data-ttu-id="eafec-142">**月 (循環模式)**</span><span class="sxs-lookup"><span data-stu-id="eafec-142">**Month (Recurrence Pattern)**</span></span>  
 <span data-ttu-id="eafec-143">選取選項以便每隔幾個月的時間執行已排程的作業，或是您希望重複執行的模式是以月為基礎時。</span><span class="sxs-lookup"><span data-stu-id="eafec-143">Select options to run a scheduled operation in intervals of a month or when the pattern that you want to repeat is based on months.</span></span> <span data-ttu-id="eafec-144">您可以指定每月的排程，包括執行排程的日子和時間。</span><span class="sxs-lookup"><span data-stu-id="eafec-144">You can specify a monthly schedule to the day, hour, and minute that you want the schedule to run.</span></span> <span data-ttu-id="eafec-145">排程中可以省略特定的月份。</span><span class="sxs-lookup"><span data-stu-id="eafec-145">You can omit specific months from the schedule.</span></span>  
  
 <span data-ttu-id="eafec-146">**一次**</span><span class="sxs-lookup"><span data-stu-id="eafec-146">**Once**</span></span>  
 <span data-ttu-id="eafec-147">選取此選項，即可建立在特定的日期和時間只執行一次的排程。</span><span class="sxs-lookup"><span data-stu-id="eafec-147">Select this option to create a schedule that runs only once, on a specific date and time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafec-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eafec-148">See Also</span></span>  
 <span data-ttu-id="eafec-149">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="eafec-149">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="eafec-150">[連接至 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eafec-150">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="eafec-151">[建立、修改和刪除共用排程](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="eafec-151">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="eafec-152">[[排程]](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="eafec-152">[Schedules](../subscriptions/schedules.md) </span></span>  
 [<span data-ttu-id="eafec-153">Management Studio F1 說明中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="eafec-153">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
