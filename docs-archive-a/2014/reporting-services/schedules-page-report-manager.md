---
title: 排程頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ef19d96e-9f00-4434-950e-152dda9c1ced
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e31bc25473aad23ecd2654f74ee3e837e65b65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594381"
---
# <a name="schedules-page-report-manager"></a><span data-ttu-id="ea591-102">排程頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="ea591-102">Schedules Page (Report Manager)</span></span>
  <span data-ttu-id="ea591-103">您可以使用 [排程] 頁面來建立、修改、刪除、暫停或繼續執行共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-103">Use the Schedules page to create, modify, delete, pause, or resume shared schedules.</span></span> <span data-ttu-id="ea591-104">共用排程是具名的排程，可以和報表、訂閱及消耗排程資訊的其他處理序分開建立和管理。</span><span class="sxs-lookup"><span data-stu-id="ea591-104">A shared schedule is a named schedule that you can create and manage separately from reports, subscriptions, and other processes that consume schedule information.</span></span> <span data-ttu-id="ea591-105">使用者可以選取您提供的共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-105">Users can select shared schedules that you provide.</span></span>  
  
 <span data-ttu-id="ea591-106">若要刪除、暫停或繼續執行共用排程，請選取想要修改的共用排程旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ea591-106">To delete, pause, or resume a shared schedule, select the check box next to the shared schedule that you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea591-107">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="ea591-107">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ea591-108">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="ea591-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ea591-109">導覽</span><span class="sxs-lookup"><span data-stu-id="ea591-109">Navigation</span></span>  
 <span data-ttu-id="ea591-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="ea591-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-schedules-page"></a><span data-ttu-id="ea591-111">若要開啟排程頁面</span><span class="sxs-lookup"><span data-stu-id="ea591-111">To open the Schedules page</span></span>  
  
1.  <span data-ttu-id="ea591-112">開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="ea591-112">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="ea591-113">在頁面的頂端，按一下右邊角落的 **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="ea591-113">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="ea591-114">這樣就會開啟該站台的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="ea591-114">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="ea591-115">選取 **[排程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ea591-115">Select the **Schedules** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ea591-116">選項</span><span class="sxs-lookup"><span data-stu-id="ea591-116">Options</span></span>  
 <span data-ttu-id="ea591-117">**新增排程**</span><span class="sxs-lookup"><span data-stu-id="ea591-117">**New Schedule**</span></span>  
 <span data-ttu-id="ea591-118">按一下即可開啟 [排程] 頁面，可用來指定頻率資訊。</span><span class="sxs-lookup"><span data-stu-id="ea591-118">Click to open the Scheduling page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="ea591-119">**刪除**</span><span class="sxs-lookup"><span data-stu-id="ea591-119">**Delete**</span></span>  
 <span data-ttu-id="ea591-120">按一下即可移除共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-120">Click to remove a shared schedule.</span></span>  
  
 <span data-ttu-id="ea591-121">**暫停**</span><span class="sxs-lookup"><span data-stu-id="ea591-121">**Pause**</span></span>  
 <span data-ttu-id="ea591-122">按一下即可暫時停止執行共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-122">Click to stop a shared schedule from running temporarily.</span></span> <span data-ttu-id="ea591-123">暫停排程可避免訂閱及其他已排程處理序的執行。</span><span class="sxs-lookup"><span data-stu-id="ea591-123">Pausing a schedule prevents subscriptions and other scheduled processes from running.</span></span>  
  
 <span data-ttu-id="ea591-124">**繼續**</span><span class="sxs-lookup"><span data-stu-id="ea591-124">**Resume**</span></span>  
 <span data-ttu-id="ea591-125">按一下即可重新恢復共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-125">Click to reinstate a shared schedule.</span></span> <span data-ttu-id="ea591-126">不會啟動在暫停排程時排定執行的失效處理序。</span><span class="sxs-lookup"><span data-stu-id="ea591-126">Lapsed processes that were scheduled to run while the schedule was paused are not made up.</span></span>  
  
 <span data-ttu-id="ea591-127">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="ea591-127">**Schedule**</span></span>  
 <span data-ttu-id="ea591-128">顯示目前定義的共用排程。</span><span class="sxs-lookup"><span data-stu-id="ea591-128">Shows the shared schedules that are currently defined.</span></span> <span data-ttu-id="ea591-129">按一下共用排程以檢視或編輯頻率資訊。</span><span class="sxs-lookup"><span data-stu-id="ea591-129">Click a shared schedule to view or edit frequency information.</span></span>  
  
 <span data-ttu-id="ea591-130">**建立者**</span><span class="sxs-lookup"><span data-stu-id="ea591-130">**Creator**</span></span>  
 <span data-ttu-id="ea591-131">顯示建立共用排程的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ea591-131">Shows the name of the user who created the shared schedule.</span></span>  
  
 <span data-ttu-id="ea591-132">**最後執行 / 下一個執行**</span><span class="sxs-lookup"><span data-stu-id="ea591-132">**Last Run, Next Run**</span></span>  
 <span data-ttu-id="ea591-133">顯示最後執行共用排程和下一個執行共用排程的時間。</span><span class="sxs-lookup"><span data-stu-id="ea591-133">Shows when the shared schedule was last run and when it will run next.</span></span>  
  
 <span data-ttu-id="ea591-134">**狀態**</span><span class="sxs-lookup"><span data-stu-id="ea591-134">**Status**</span></span>  
 <span data-ttu-id="ea591-135">顯示共用排程是否為暫停或使用中。</span><span class="sxs-lookup"><span data-stu-id="ea591-135">Shows whether a shared schedule is paused or active.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea591-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea591-136">See Also</span></span>  
 <span data-ttu-id="ea591-137">[建立、修改和刪除共用排程](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="ea591-137">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="ea591-138">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="ea591-138">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
