---
title: 訂閱頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c67895babe99c92b7c09afd8cb75ca88d5cd7553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703761"
---
# <a name="subscriptions-page-report-manager"></a><span data-ttu-id="a19a0-102">訂閱頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="a19a0-102">Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="a19a0-103">使用 [訂閱] 頁面即可列出目前報表或共用資料來源的全部訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-103">Use the Subscriptions page to list all of the subscriptions for the current report or shared data source.</span></span> <span data-ttu-id="a19a0-104">如果您擁有足夠的權限 (如同「管理所有訂閱」工作所表示)，就可以檢視所有使用者的訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-104">If you have sufficient permission (as conveyed by the "Manage all subscriptions" task), you can view the subscriptions of all users.</span></span> <span data-ttu-id="a19a0-105">否則，此頁面只會顯示您擁有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-105">Otherwise, this page shows only the subscriptions that you own.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a19a0-106">其他頁面也會包含訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="a19a0-106">Other pages also contain subscription information.</span></span> <span data-ttu-id="a19a0-107">如需詳細資訊，請參閱[我的訂閱頁面 &#40;報表管理員&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md)在同一個位置存取您所有的訂用帳戶，或使用 [[新增訂閱] 或 [編輯訂閱] 頁面 &#40;報表管理員](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)&#41;建立或編輯訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="a19a0-107">For more information, see [My Subscriptions Page &#40;Report Manager&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md) to access all your subscriptions in one place or the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) to create or edit a subscription.</span></span>  
  
 <span data-ttu-id="a19a0-108">有些選項只會在有現有的訂閱可用時才看得見。</span><span class="sxs-lookup"><span data-stu-id="a19a0-108">Some options are visible only if there are existing subscriptions to work with.</span></span> <span data-ttu-id="a19a0-109">如果未定義任何訂閱，而且您是從報表中存取此頁面，頁面上就只會有 **[新增訂閱]** 和 **[新增資料驅動訂閱]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a19a0-109">If no subscriptions are defined and you are accessing this page from a report, the **New Subscription** and **New Data-Driven Subscription** are the only options on the page.</span></span>  
  
 <span data-ttu-id="a19a0-110">建立新訂閱之前，您必須確認報表資料來源是否使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="a19a0-110">Before you can create a new subscription, you must verify that the report data source uses stored credentials.</span></span> <span data-ttu-id="a19a0-111">使用 [資料來源屬性] 頁面即可儲存認證。</span><span class="sxs-lookup"><span data-stu-id="a19a0-111">Use the Data Sources properties page to store credentials.</span></span> <span data-ttu-id="a19a0-112">如需詳細資訊，請參閱[資料來源屬性頁面 &#40;報表管理員&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a19a0-112">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a19a0-113">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="a19a0-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a19a0-114">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="a19a0-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="a19a0-115">導覽</span><span class="sxs-lookup"><span data-stu-id="a19a0-115">Navigation</span></span>  
 <span data-ttu-id="a19a0-116">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="a19a0-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-subscriptions-page-for-report"></a><span data-ttu-id="a19a0-117">若要開啟報表的訂閱頁面</span><span class="sxs-lookup"><span data-stu-id="a19a0-117">To open the Subscriptions page for report</span></span>  
  
1.  <span data-ttu-id="a19a0-118">開啟報表管理員，然後找出您想要檢視或設定訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="a19a0-118">Open Report Manager, and locate the report for which you want to view or configure a subscription.</span></span>  
  
2.  <span data-ttu-id="a19a0-119">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="a19a0-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="a19a0-120">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="a19a0-120">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="a19a0-121">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="a19a0-121">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="a19a0-122">選取 **[訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a19a0-122">Select the **Subscriptions** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a19a0-123">選項</span><span class="sxs-lookup"><span data-stu-id="a19a0-123">Options</span></span>  
 <span data-ttu-id="a19a0-124">**刪除**</span><span class="sxs-lookup"><span data-stu-id="a19a0-124">**Delete**</span></span>  
 <span data-ttu-id="a19a0-125">按一下即可刪除訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-125">Click to delete a subscription.</span></span> <span data-ttu-id="a19a0-126">在刪除訂閱之前，請選取您想要刪除之每一個訂閱旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a19a0-126">Before you can delete a subscription, select the check box next to each subscription that you want to delete.</span></span>  
  
 <span data-ttu-id="a19a0-127">**新增訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="a19a0-127">**New Subscription**</span></span>  
 <span data-ttu-id="a19a0-128">按一下即可建立目前報表的新訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-128">Click to create a new subscription to the current report.</span></span> <span data-ttu-id="a19a0-129">當報表使用預存認證或無認證時，就會啟用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="a19a0-129">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="a19a0-130">當您開啟共用資料來源的 [訂閱] 頁面時，無法使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="a19a0-130">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="a19a0-131">**[新增資料驅動訂閱]**</span><span class="sxs-lookup"><span data-stu-id="a19a0-131">**New Data-Driven Subscription**</span></span>  
 <span data-ttu-id="a19a0-132">按一下即可針對包含此資訊之資料存放區執行的命令或查詢，產生訂閱者清單和傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="a19a0-132">Click to generate a subscriber list and delivery options from a command or query against a data store that contains this information.</span></span> <span data-ttu-id="a19a0-133">當報表使用預存認證或無認證時，就會啟用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="a19a0-133">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="a19a0-134">當您開啟共用資料來源的 [訂閱] 頁面時，無法使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="a19a0-134">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="a19a0-135">**編輯**</span><span class="sxs-lookup"><span data-stu-id="a19a0-135">**Edit**</span></span>  
 <span data-ttu-id="a19a0-136">按一下即可檢視或編輯訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-136">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="a19a0-137">**Report**</span><span class="sxs-lookup"><span data-stu-id="a19a0-137">**Report**</span></span>  
 <span data-ttu-id="a19a0-138">當您從共用資料來源開啟這個頁面時，此資料行會識別定義此訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="a19a0-138">When you open this page from a shared data source, this column identifies the report for which the subscription is defined.</span></span> <span data-ttu-id="a19a0-139">**[資料夾]** 資料行會識別報表的位置。</span><span class="sxs-lookup"><span data-stu-id="a19a0-139">The **Folder** column identifies the location of the report.</span></span>  
  
 <span data-ttu-id="a19a0-140">**說明**</span><span class="sxs-lookup"><span data-stu-id="a19a0-140">**Description**</span></span>  
 <span data-ttu-id="a19a0-141">顯示訂閱的描述。</span><span class="sxs-lookup"><span data-stu-id="a19a0-141">Shows a description of the subscription.</span></span>  
  
 <span data-ttu-id="a19a0-142">**觸發程序**</span><span class="sxs-lookup"><span data-stu-id="a19a0-142">**Trigger**</span></span>  
 <span data-ttu-id="a19a0-143">識別造成執行訂閱的條件。</span><span class="sxs-lookup"><span data-stu-id="a19a0-143">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="a19a0-144">**TimedSubscription** 觸發程序是以執行訂閱時定義的排程為基礎。</span><span class="sxs-lookup"><span data-stu-id="a19a0-144">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="a19a0-145">**SnapshotUpdated** 觸發程序是以報表快照集的更新為基礎。</span><span class="sxs-lookup"><span data-stu-id="a19a0-145">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="a19a0-146">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="a19a0-146">**Owner**</span></span>  
 <span data-ttu-id="a19a0-147">顯示建立訂閱的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-147">Shows the name of the user who created the subscription.</span></span>  
  
 <span data-ttu-id="a19a0-148">**最後執行**</span><span class="sxs-lookup"><span data-stu-id="a19a0-148">**Last Run**</span></span>  
 <span data-ttu-id="a19a0-149">顯示最後處理訂閱的時間。</span><span class="sxs-lookup"><span data-stu-id="a19a0-149">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="a19a0-150">**狀態**</span><span class="sxs-lookup"><span data-stu-id="a19a0-150">**Status**</span></span>  
 <span data-ttu-id="a19a0-151">顯示訂閱的狀態。</span><span class="sxs-lookup"><span data-stu-id="a19a0-151">Shows the status of the subscription.</span></span> <span data-ttu-id="a19a0-152">通常，狀態值若不是新的 (New)，就會是上一次執行訂閱的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a19a0-152">Usually, the status value is either New or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="a19a0-153">訂閱若是包含指向 (對執行報表所使用的預存認證) 已經無效之加密值的指標，則會出現「不正確的資料」狀態值。</span><span class="sxs-lookup"><span data-stu-id="a19a0-153">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="a19a0-154">在報表伺服器上重新建立用於加密和解密資料的對稱金鑰時，現有的加密值將變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="a19a0-154">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="a19a0-155">如果訂閱已經停用，則無法處理該訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-155">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="a19a0-156">若要更新訂閱並讓其運作，請開啟然後儲存訂閱。</span><span class="sxs-lookup"><span data-stu-id="a19a0-156">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19a0-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a19a0-157">See Also</span></span>  
 <span data-ttu-id="a19a0-158">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a19a0-158">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="a19a0-159">[以原生模式 &#40;Reporting Services 建立、修改和刪除標準訂閱&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="a19a0-159">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="a19a0-160">[建立、修改和刪除共用排程](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="a19a0-160">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="a19a0-161">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="a19a0-161">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
