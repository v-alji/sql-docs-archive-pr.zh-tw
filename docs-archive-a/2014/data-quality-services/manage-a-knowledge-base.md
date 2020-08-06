---
title: 管理知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cc5fdd87ddb3ea687db10a29d7001564fd8ff107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599688"
---
# <a name="manage-a-knowledge-base"></a><span data-ttu-id="adf1c-102">管理知識庫</span><span class="sxs-lookup"><span data-stu-id="adf1c-102">Manage a Knowledge Base</span></span>
  <span data-ttu-id="adf1c-103">本主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中針對知識庫執行管理功能。</span><span class="sxs-lookup"><span data-stu-id="adf1c-103">This topic describes how to perform management functions on a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="adf1c-104">您可以刪除知識庫、解除鎖定知識庫、捨棄知識庫工作、重新命名知識庫，以及顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="adf1c-104">You can delete a knowledge base, unlock it, discard your work on it, rename it, and display its properties.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="adf1c-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="adf1c-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="adf1c-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="adf1c-106">Prerequisites</span></span>  
 <span data-ttu-id="adf1c-107">若要管理知識庫，該知識庫必須已經建立完成，而且它必須已發行 (如果是由另一個人建立) 或關閉 (如果是由您建立)。</span><span class="sxs-lookup"><span data-stu-id="adf1c-107">To manage a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="adf1c-108">Security</span><span class="sxs-lookup"><span data-stu-id="adf1c-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="adf1c-109">權限</span><span class="sxs-lookup"><span data-stu-id="adf1c-109">Permissions</span></span>  
 <span data-ttu-id="adf1c-110">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-110">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="manage-a-knowledge-base"></a><a name="Manage"></a><span data-ttu-id="adf1c-111">管理知識庫</span><span class="sxs-lookup"><span data-stu-id="adf1c-111">Manage a Knowledge Base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="adf1c-112">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="adf1c-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="adf1c-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，按一下 **[開啟知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="adf1c-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="adf1c-114">以滑鼠右鍵按一下知識庫資料表中的知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-114">Right-click a knowledge base in the knowledge base table.</span></span>  
  
4.  <span data-ttu-id="adf1c-115">在內容功能表中，您可以進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="adf1c-115">In the context menu, you can do the following:</span></span>  
  
    1.  <span data-ttu-id="adf1c-116">**開啟**：按一下即可開啟 **[選取活動]** 窗格中選取之活動內的知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-116">**Open**: Click to open the knowledge base in the activity selected in the **Select Activity** pane.</span></span>  
  
    2.  <span data-ttu-id="adf1c-117">**解除鎖定**：如果您是原本正在處理知識庫的使用者、進行了定義域管理、知識探索和比對原則活動的其中一個步驟，而且已關閉知識庫，就可以解除鎖定知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-117">**Unlock**: You can unlock the knowledge base if you are the user who was working on the knowledge base in one of the steps of domain management, knowledge discovery, and the matching policy activity, and closed it.</span></span> <span data-ttu-id="adf1c-118">如果您解除鎖定知識庫，另一位人員就能夠開啟並處理知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-118">If you unload the knowledge base, another person will be able to open it and work on it.</span></span> <span data-ttu-id="adf1c-119">如果知識庫並未處於活動的狀態，您就無法使用此命令。</span><span class="sxs-lookup"><span data-stu-id="adf1c-119">This command is not available if the knowledge base is not in a state of an activity.</span></span> <span data-ttu-id="adf1c-120">如需詳細資訊，請參閱 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="adf1c-120">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    3.  <span data-ttu-id="adf1c-121">**捨棄工作**：當知識庫處於正在處理的狀態 (如資料表中 [狀態] 欄位的項目所示) 時，請按一下此命令。</span><span class="sxs-lookup"><span data-stu-id="adf1c-121">**Discard work**: Click when the knowledge base is in a state of being worked on, as shown with an entry in the State field in the table.</span></span> <span data-ttu-id="adf1c-122">如果知識庫並未處於活動的狀態，您就無法使用此命令。如果知識庫已鎖定，您也無法使用此命令。</span><span class="sxs-lookup"><span data-stu-id="adf1c-122">This command is not available if the knowledge base is not in a state of an activity, and it is not available if the knowledge base is locked.</span></span> <span data-ttu-id="adf1c-123">如需詳細資訊，請參閱 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="adf1c-123">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    4.  <span data-ttu-id="adf1c-124">**重新命名**：按一下即可針對您以滑鼠右鍵按一下的知識庫，讓其資料表的 [知識庫] 欄位變成可編輯狀態。</span><span class="sxs-lookup"><span data-stu-id="adf1c-124">**Rename**: Click to make the Knowledge Base field of the table editable for the knowledge base that you right-clicked on.</span></span> <span data-ttu-id="adf1c-125">請變更名稱，然後按一下該知識庫和欄位中的另一個知識庫，接受名稱變更。</span><span class="sxs-lookup"><span data-stu-id="adf1c-125">Change the name, and then click on that knowledge base and another one in the field to accept the name change.</span></span>  
  
    5.  <span data-ttu-id="adf1c-126">**刪除**：按一下即可從 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]的 DQS_MAIN 資料庫中移除知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-126">**Delete**: Click to remove the knowledge base from the DQS_MAIN database on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
    6.  <span data-ttu-id="adf1c-127">**屬性**：按一下即可將資料庫的屬性顯示在唯讀畫面中。</span><span class="sxs-lookup"><span data-stu-id="adf1c-127">**Properties**: Click to display properties for the database in a read-only display.</span></span>  
  
        1.  <span data-ttu-id="adf1c-128">**來源知識庫**：做為此資料庫基礎的知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-128">**Source Knowledge Base**: the knowledge base that this database was based on.</span></span> <span data-ttu-id="adf1c-129">這是選用的選項。</span><span class="sxs-lookup"><span data-stu-id="adf1c-129">This is optional.</span></span>  
  
        2.  <span data-ttu-id="adf1c-130">**狀態**：指出知識庫是否處於 **[工作中]** 狀態，以及它是否正在進行特定的知識管理活動，由上次關閉時所處的狀態決定。</span><span class="sxs-lookup"><span data-stu-id="adf1c-130">**State**: Indicates if the knowledge base is **In Work** and if it is in a specific knowledge management activity, as determined when it was last closed.</span></span> <span data-ttu-id="adf1c-131">此狀態可能是 **[工作中]**(表示已在知識管理工作階段中開啟知識庫，但是並未進行特定活動)，或是 **[工作中]** 再加上知識管理活動 (表示已在知識管理工作階段中開啟知識庫，而且正在進行特定活動)。</span><span class="sxs-lookup"><span data-stu-id="adf1c-131">The state can be **In Work**, in which the knowledge base is opened in a knowledge management session, but not in a specific activity, or **In Work** plus a knowledge management activity, in which the knowledge base is opened in a knowledge management session, and in a specific activity.</span></span>  
  
        3.  <span data-ttu-id="adf1c-132">**已鎖定**：如果知識庫已鎖定，則為 **True** ，否則為 **False**</span><span class="sxs-lookup"><span data-stu-id="adf1c-132">**Is Locked**: **True** if the knowledge base was locked, **False** if not</span></span>  
  
        4.  <span data-ttu-id="adf1c-133">**包含未發行的內容**：如果知識庫包含尚未透過發行所儲存的內容，則為 True，否則為 False</span><span class="sxs-lookup"><span data-stu-id="adf1c-133">**Contains unpublished content**: True if the knowledge base contains content that has not been saved by publishing, False if not</span></span>  
  
        5.  <span data-ttu-id="adf1c-134">**鎖定者**：關閉知識庫並加以鎖定之使用者的名稱</span><span class="sxs-lookup"><span data-stu-id="adf1c-134">**Locked By**: the name of the user who closed the knowledge base, locking it</span></span>  
  
        6.  <span data-ttu-id="adf1c-135">**鎖定日期**：鎖定的日期</span><span class="sxs-lookup"><span data-stu-id="adf1c-135">**Locked Date**: date when locked</span></span>  
  
        7.  <span data-ttu-id="adf1c-136">**建立者**：建立知識庫之使用者的名稱，以及該使用者所屬的網路</span><span class="sxs-lookup"><span data-stu-id="adf1c-136">**Created By**: the name of the user who created the knowledge base, with the network that he or she belongs to</span></span>  
  
        8.  <span data-ttu-id="adf1c-137">**建立日期**：建立的日期</span><span class="sxs-lookup"><span data-stu-id="adf1c-137">**Created Date**: date when created</span></span>  
  
##  <a name="follow-up-after-managing-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="adf1c-138">後續操作：管理知識庫之後</span><span class="sxs-lookup"><span data-stu-id="adf1c-138">Follow Up: After Managing a Knowledge Base</span></span>  
 <span data-ttu-id="adf1c-139">管理知識庫之後，下一個步驟將取決於您針對知識庫所採取的動作：</span><span class="sxs-lookup"><span data-stu-id="adf1c-139">After you manage a knowledge base, your next step depends upon the action you took on the knowledge base:</span></span>  
  
-   <span data-ttu-id="adf1c-140">如果您開啟了知識庫，就要繼續進行已選取的活動。</span><span class="sxs-lookup"><span data-stu-id="adf1c-140">If you opened the knowledge base, you will continue in the activity that you selected.</span></span>  
  
-   <span data-ttu-id="adf1c-141">如果您解除鎖定了知識庫，另一位人員就可以在指出的狀態中開啟並處理該知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-141">If you unlocked it, it will be available for another person to open and work on, in the state indicated.</span></span>  
  
-   <span data-ttu-id="adf1c-142">如果您捨棄了知識庫工作，該知識庫將處於上次發行的狀態。</span><span class="sxs-lookup"><span data-stu-id="adf1c-142">If you discarded the work on it, the knowledge base will be available in its last published state.</span></span>  
  
-   <span data-ttu-id="adf1c-143">如果您重新命名了知識庫，就必須開啟已重新命名的知識庫，才能進行處理。</span><span class="sxs-lookup"><span data-stu-id="adf1c-143">If you renamed it, you will have to open the renamed knowledge base to work on it.</span></span>  
  
-   <span data-ttu-id="adf1c-144">如果您刪除了知識庫，就必須選取另一個要處理的知識庫，或是建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="adf1c-144">If you delete it, you will have to select another knowledge base to work on, or create a new one.</span></span>  
  
  
