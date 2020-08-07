---
title: 建立資料驅動訂用帳戶 (SSRS 教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53be7cf793d8fa38d177643c7f366115d4df8b7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703938"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a><span data-ttu-id="d411a-102">建立資料驅動訂閱 (SSRS 教學課程)</span><span class="sxs-lookup"><span data-stu-id="d411a-102">Create a Data-Driven Subscription (SSRS Tutorial)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="d411a-103">提供了資料驅動訂閱，讓您可以依據動態訂閱者資料來自訂報表的散發。</span><span class="sxs-lookup"><span data-stu-id="d411a-103">provides data-driven subscriptions so that you can customize the distribution of a report based on dynamic subscriber data.</span></span> <span data-ttu-id="d411a-104">資料驅動訂閱適用於下列狀況：</span><span class="sxs-lookup"><span data-stu-id="d411a-104">Data-driven subscriptions are intended for the following kinds of scenarios:</span></span>  
  
-   <span data-ttu-id="d411a-105">將報表散發給成員資格可能隨著不同的散發而變更的大型收件者集區。</span><span class="sxs-lookup"><span data-stu-id="d411a-105">Distributing reports to a large recipient pool whose membership may change from one distribution to the next.</span></span> <span data-ttu-id="d411a-106">例如，將月報表散發給目前的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="d411a-106">For example, distribute a monthly report to all current customers.</span></span>  
  
-   <span data-ttu-id="d411a-107">依據預先定義的準則，將報表散發給特定收件者群組。</span><span class="sxs-lookup"><span data-stu-id="d411a-107">Distributing reports to a specific group of recipients based on predefined criteria.</span></span> <span data-ttu-id="d411a-108">例如，將銷售績效報表傳給組織中的前 10 名銷售經理。</span><span class="sxs-lookup"><span data-stu-id="d411a-108">For example, send a sales performance report to the top ten sales managers in an organization.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="d411a-109">學習內容</span><span class="sxs-lookup"><span data-stu-id="d411a-109">What You Will Learn</span></span>  
 <span data-ttu-id="d411a-110">本教學課程使用簡單的範例說明概念，告訴您如何使用資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d411a-110">This tutorial shows you how to use data-driven subscriptions using a simple example to illustrate the concepts.</span></span>  
  
 <span data-ttu-id="d411a-111">本教學課程分成三個課程：</span><span class="sxs-lookup"><span data-stu-id="d411a-111">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="d411a-112">第 1 課：建立範例訂閱者資料庫</span><span class="sxs-lookup"><span data-stu-id="d411a-112">Lesson 1: Creating a Sample Subscriber Database</span></span>](lesson-1-creating-a-sample-subscriber-database.md)  
 <span data-ttu-id="d411a-113">在這一課，您將學習如何建立包含訂閱者資訊的本機 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d411a-113">In this lesson you will learn how to create a local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains subscriber information.</span></span>  
  
 [<span data-ttu-id="d411a-114">第 2 課：修改報表資料來源屬性</span><span class="sxs-lookup"><span data-stu-id="d411a-114">Lesson 2: Modifying the Report Data Source Properties</span></span>](lesson-2-modifying-the-report-data-source-properties.md)  
 <span data-ttu-id="d411a-115">在這一課，您將學習如何修改報表資料來源屬性，讓報表能夠自動執行。</span><span class="sxs-lookup"><span data-stu-id="d411a-115">In this lesson, you will learn how to modify report data source properties so that the report can run unattended.</span></span> <span data-ttu-id="d411a-116">自動處理需要預存認證。</span><span class="sxs-lookup"><span data-stu-id="d411a-116">Unattended processing requires stored credentials.</span></span> <span data-ttu-id="d411a-117">您也會將報表資料集修改為包含訂閱者資料所提供的參數。</span><span class="sxs-lookup"><span data-stu-id="d411a-117">You will also modify the report dataset to include a parameter that is supplied by the subscriber data.</span></span>  
  
 [<span data-ttu-id="d411a-118">第 3 課：定義資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="d411a-118">Lesson 3: Defining a Data-Driven Subscription</span></span>](lesson-3-defining-a-data-driven-subscription.md)  
 <span data-ttu-id="d411a-119">在這一課，您將學習如何定義資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d411a-119">In this lesson you will learn how to define a data-driven subscription.</span></span> <span data-ttu-id="d411a-120">本課程會逐步引導您完成「資料驅動訂閱精靈」的每個頁面。</span><span class="sxs-lookup"><span data-stu-id="d411a-120">This lesson guides you through each page in the Data-Driven Subscription Wizard.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d411a-121">需求</span><span class="sxs-lookup"><span data-stu-id="d411a-121">Requirements</span></span>  
 <span data-ttu-id="d411a-122">資料驅動訂閱通常是由報表伺服器管理員來建立和維護。</span><span class="sxs-lookup"><span data-stu-id="d411a-122">Data-driven subscriptions are typically created and maintained by report server administrators.</span></span> <span data-ttu-id="d411a-123">您必須是建立查詢的專家、擁有包含訂閱者資料之資料來源的知識，且具備較高的報表伺服器權限，才能夠建立資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d411a-123">The ability to create data-driven subscriptions requires expertise in building queries, knowledge of data sources that contain subscriber data, and elevated permissions on a report server.</span></span>  
  
 <span data-ttu-id="d411a-124">本教學課程會使用[建立基本資料表報表](create-a-basic-table-report-ssrs-tutorial.md)教學課程中所建立的報表 &#40;SSRS 教學課程&#41;和來自的資料[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d411a-124">The tutorial will use the report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md) and data from [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span></span>  
  
 <span data-ttu-id="d411a-125">您的系統必須已經安裝下列項目，才能使用這個教學課程：</span><span class="sxs-lookup"><span data-stu-id="d411a-125">Your system must have the following installed to use this tutorial:</span></span>  
  
-   <span data-ttu-id="d411a-126">支援資料驅動訂閱的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="d411a-126">An edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that supports data-driven subscriptions.</span></span> <span data-ttu-id="d411a-127">如需詳細資訊，請參閱[SQL Server 2014 的版本和元件](../sql-server/editions-and-components-of-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="d411a-127">For more information, see [Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
-   <span data-ttu-id="d411a-128">報表伺服器必須以原生模式執行。</span><span class="sxs-lookup"><span data-stu-id="d411a-128">The report server must be running in native mode.</span></span> <span data-ttu-id="d411a-129">此教學課程中描述的使用者介面是以原生模式報表伺服器為基礎。</span><span class="sxs-lookup"><span data-stu-id="d411a-129">The user interface described in this tutorial is based on a native mode report server.</span></span> <span data-ttu-id="d411a-130">雖然 SharePoint 模式報表伺服器也支援訂閱，不過其使用者介面與此教學課程所描述的使用者介面有所不同。</span><span class="sxs-lookup"><span data-stu-id="d411a-130">Subscriptions are supported on SharePoint mode report servers but the user interface will be different than what is described in this tutorial.</span></span>  
  
-   <span data-ttu-id="d411a-131">SQL Server Agent 服務必須在執行中。</span><span class="sxs-lookup"><span data-stu-id="d411a-131">SQL Server Agent service must be running.</span></span>  
  
-   <span data-ttu-id="d411a-132">包括參數的報表。</span><span class="sxs-lookup"><span data-stu-id="d411a-132">A report that includes parameters.</span></span> <span data-ttu-id="d411a-133">本教學課程採用您使用 `Sales Orders` 建立基本資料表報表 &#40;SSRS 教學課程&#41; [建立基本資料表報表 &amp;#40;SSRS 教學課程&amp;#41;](create-a-basic-table-report-ssrs-tutorial.md)中的資料。</span><span class="sxs-lookup"><span data-stu-id="d411a-133">This tutorial assumes the sample report, `Sales Orders` you create using the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
-   <span data-ttu-id="d411a-134">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 範例資料庫，它會將資料提供給範例報表。</span><span class="sxs-lookup"><span data-stu-id="d411a-134">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database, which provides data to the sample report.</span></span>  
  
-   <span data-ttu-id="d411a-135">包括範例報表之「管理所有訂閱」工作的角色指派。</span><span class="sxs-lookup"><span data-stu-id="d411a-135">A role assignment that includes the Manage all subscriptions task on the sample report.</span></span> <span data-ttu-id="d411a-136">定義資料驅動訂閱需要這項工作。</span><span class="sxs-lookup"><span data-stu-id="d411a-136">This task is required for defining a data-driven subscription.</span></span> <span data-ttu-id="d411a-137">如果您是電腦的管理員，本機管理員的預設角色指派提供必要權限來建立資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="d411a-137">If you are an administrator on the computer, the default role assignment for local administrators provides the permissions necessary for creating data-driven subscriptions.</span></span> <span data-ttu-id="d411a-138">如需詳細資訊，請參閱 [在原生模式報表伺服器上授與權限](security/granting-permissions-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d411a-138">For more information, see [Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md).</span></span>  
  
-   <span data-ttu-id="d411a-139">您有寫入權的共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="d411a-139">A shared folder for which you have write permissions.</span></span> <span data-ttu-id="d411a-140">共用資料夾必須可透過網路連接存取。</span><span class="sxs-lookup"><span data-stu-id="d411a-140">The shared folder must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="d411a-141">**完成這個教學課程的估計時間：** 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="d411a-141">**Estimated time to complete the tutorial:** 30 minutes.</span></span> <span data-ttu-id="d411a-142">如果您尚未完成基本報表教學課程，還需額外 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="d411a-142">An additional 30 minutes if you have not completed the basic report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d411a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d411a-143">See Also</span></span>  
 <span data-ttu-id="d411a-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="d411a-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="d411a-145">建立基本資料表報表 &#40;SSRS 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="d411a-145">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
