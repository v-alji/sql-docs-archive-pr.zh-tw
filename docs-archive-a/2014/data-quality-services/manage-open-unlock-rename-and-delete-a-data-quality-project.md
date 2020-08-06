---
title: 管理 (開啟、解除鎖定、重新命名和刪除資料品質專案) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599675"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a><span data-ttu-id="7b190-102">管理 (開啟、解除鎖定、重新命名和刪除) 資料品質專案</span><span class="sxs-lookup"><span data-stu-id="7b190-102">Manage (Open, Unlock, Rename, and Delete) a Data Quality Project</span></span>
  <span data-ttu-id="7b190-103">此主題描述如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 管理資料品質專案，例如開啟、解除鎖定、重新命名和刪除資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-103">This topic describes how to manage a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] such as open, unlock, rename, and delete a data quality project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b190-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="7b190-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="7b190-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="7b190-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7b190-106">您無法開啟另一個使用者所建立且已鎖定的專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-106">You cannot open a locked project that is created by another user.</span></span>  
  
-   <span data-ttu-id="7b190-107">您無法解除鎖定、重新命名或刪除另一個使用者所建立的資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-107">You cannot unlock, rename, or delete a data quality project that is created by another user.</span></span>  
  
-   <span data-ttu-id="7b190-108">您不能刪除已鎖定的資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-108">You cannot delete a locked data quality project.</span></span> <span data-ttu-id="7b190-109">您必須先解除鎖定，然後才能刪除。</span><span class="sxs-lookup"><span data-stu-id="7b190-109">You must first unlock it to delete.</span></span>  
  
-   <span data-ttu-id="7b190-110">您只能解除鎖定由您建立的資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-110">You can only unlock a data quality project that is created by you.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="7b190-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="7b190-111">Prerequisites</span></span>  
 <span data-ttu-id="7b190-112">您至少必須有一個資料品質專案可供管理。</span><span class="sxs-lookup"><span data-stu-id="7b190-112">You must have at least one data quality project to manage.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b190-113">Security</span><span class="sxs-lookup"><span data-stu-id="7b190-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b190-114">權限</span><span class="sxs-lookup"><span data-stu-id="7b190-114">Permissions</span></span>  
 <span data-ttu-id="7b190-115">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 或 dqs_kb_operator 角色，才能管理資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-115">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to manage a data quality project.</span></span>  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> <span data-ttu-id="7b190-116">開啟資料品質專案</span><span class="sxs-lookup"><span data-stu-id="7b190-116">Open a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7b190-117">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7b190-117">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7b190-118">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟資料品質專案]**。</span><span class="sxs-lookup"><span data-stu-id="7b190-118">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="7b190-119">**[開啟專案]** 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b190-119">The **Open project** screen appears.</span></span>  
  
     <span data-ttu-id="7b190-120">或者，您也可以按一下 **[最近使用的資料品質專案]** 區域底下所列出的資料品質專案，直接將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7b190-120">Alternately, you can directly open a data quality project listed under **Recent data quality project** area by clicking it.</span></span>  
  
3.  <span data-ttu-id="7b190-121">在 **[開啟專案]** 畫面中，按一下來選取您想要開啟的資料品質專案，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7b190-121">In the **Open project** screen, click to select the data quality project that you want to open, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="7b190-122">隨即以上次活動關閉時的相同狀態來開啟資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-122">The data quality project opens at the same state of the activity where it was last closed.</span></span> <span data-ttu-id="7b190-123">資料品質專案具有以下狀態：</span><span class="sxs-lookup"><span data-stu-id="7b190-123">A data quality project has the following states:</span></span>  
  
    -   <span data-ttu-id="7b190-124">針對 [**清理**] 活動，資料品質專案可以具有下列狀態： [**清理-對應**]、[**清理-** 清理]、[**清理-管理和查看結果**] 和 [**清理-匯出**]。</span><span class="sxs-lookup"><span data-stu-id="7b190-124">For the **Cleansing** activity, a data quality project can have the following states: **Cleansing - Map**, **Cleansing - Cleanse**, **Cleansing - Manage and View Results**, and **Cleansing - Export**.</span></span>  
  
    -   <span data-ttu-id="7b190-125">針對比**對活動，** 資料品質專案可以具有下列狀態：比**對對應**、比對**對應、比**對-**生存**和比**對匯出**。</span><span class="sxs-lookup"><span data-stu-id="7b190-125">For the **Matching** activity, a data quality project can have the following states: **Matching - Map**, **Matching - Matching**, **Matching - Survivorship**, and **Matching - Export**.</span></span>  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> <span data-ttu-id="7b190-126">解除鎖定資料品質專案</span><span class="sxs-lookup"><span data-stu-id="7b190-126">Unlock a Data Quality Project</span></span>  
 <span data-ttu-id="7b190-127">當您建立資料品質專案時，它處於已鎖定狀態，以防止其他使用者使用或修改。</span><span class="sxs-lookup"><span data-stu-id="7b190-127">When you create a data quality project, it is in a locked state to prevent usage or modification by other users.</span></span> <span data-ttu-id="7b190-128">如果您希望其他使用者使用您的資料品質專案，在您完成工作之後必須解除鎖定資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="7b190-128">You must unlock the data quality project after you have completed your work if you want other users to work on your data quality project.</span></span> <span data-ttu-id="7b190-129">鎖定的專案會顯示鎖定符號。</span><span class="sxs-lookup"><span data-stu-id="7b190-129">A lock symbol is displayed for projects that are locked.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7b190-130">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7b190-130">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7b190-131">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟資料品質專案]**。</span><span class="sxs-lookup"><span data-stu-id="7b190-131">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="7b190-132">**[開啟專案]** 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b190-132">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="7b190-133">在 **[開啟專案]** 畫面中，以滑鼠右鍵按一下您所建立且已鎖定的資料品質專案，然後按一下快速鍵功能表中的 **[解除鎖定]** 。</span><span class="sxs-lookup"><span data-stu-id="7b190-133">In the **Open project** screen, right-click a locked data quality project that is created by you, and then click **Unlock** in the shortcut menu.</span></span> <span data-ttu-id="7b190-134">專案會顯示綠色核取記號，表示專案已解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="7b190-134">A green check mark is displayed for the project indicating that it is unlocked.</span></span>  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> <span data-ttu-id="7b190-135">重新命名資料品質專案</span><span class="sxs-lookup"><span data-stu-id="7b190-135">Rename a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7b190-136">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7b190-136">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7b190-137">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟資料品質專案]**。</span><span class="sxs-lookup"><span data-stu-id="7b190-137">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="7b190-138">**[開啟專案]** 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b190-138">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="7b190-139">在 **[開啟專案]** 畫面中，以滑鼠右鍵按一下您所建立的資料品質專案，然後按一下快速鍵功能表中的 **[重新命名]** 。</span><span class="sxs-lookup"><span data-stu-id="7b190-139">In the **Open project** screen, right-click a data quality project that is created by you, and then click **Rename** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="7b190-140">此資料品質專案名稱就可以在 **[名稱]** 資料行中編輯。</span><span class="sxs-lookup"><span data-stu-id="7b190-140">The data quality project name becomes editable in the **Name** column.</span></span> <span data-ttu-id="7b190-141">輸入新的名稱，然後按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="7b190-141">Type a new name, and then press Enter.</span></span>  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> <span data-ttu-id="7b190-142">刪除資料品質專案</span><span class="sxs-lookup"><span data-stu-id="7b190-142">Delete a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7b190-143">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7b190-143">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7b190-144">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面中，按一下 **[開啟資料品質專案]**。</span><span class="sxs-lookup"><span data-stu-id="7b190-144">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="7b190-145">**[開啟專案]** 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b190-145">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="7b190-146">在 **[開啟專案]** 畫面中，以滑鼠右鍵按一下您所建立且解除鎖定的資料品質專案，然後按一下快速鍵功能表中的 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="7b190-146">In the **Open project** screen, right-click an unlocked data quality project that is created by you, and then click **Delete** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="7b190-147">確認訊息隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b190-147">A confirmation message appears.</span></span> <span data-ttu-id="7b190-148">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="7b190-148">Click **Yes**.</span></span>  
  
  
