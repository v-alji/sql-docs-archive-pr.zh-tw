---
title: 開啟知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f727a5ab75a60d29c830403892c56c87fc6d4ebf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705433"
---
# <a name="open-a-knowledge-base"></a><span data-ttu-id="e1953-102">開啟知識庫</span><span class="sxs-lookup"><span data-stu-id="e1953-102">Open a Knowledge Base</span></span>
  <span data-ttu-id="e1953-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中開啟現有的知識庫，並預備此知識庫進行定義域管理、知識探索或是加入比對原則。</span><span class="sxs-lookup"><span data-stu-id="e1953-103">This topic describes how to open an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e1953-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="e1953-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e1953-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e1953-105">Prerequisites</span></span>  
 <span data-ttu-id="e1953-106">若要開啟知識庫，必須已建立該知識庫，而且它必須已發行 (如果是由另一個人建立) 或關閉 (如果是由您建立)。</span><span class="sxs-lookup"><span data-stu-id="e1953-106">To open a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e1953-107">Security</span><span class="sxs-lookup"><span data-stu-id="e1953-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e1953-108">權限</span><span class="sxs-lookup"><span data-stu-id="e1953-108">Permissions</span></span>  
 <span data-ttu-id="e1953-109">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-109">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="open-a-knowledge-base"></a><a name="Open"></a><span data-ttu-id="e1953-110">開啟知識庫</span><span class="sxs-lookup"><span data-stu-id="e1953-110">Open a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="e1953-111">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e1953-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="e1953-112">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，按一下 **[開啟知識庫]**。</span><span class="sxs-lookup"><span data-stu-id="e1953-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="e1953-113">在資料表中選取知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-113">Select a knowledge base in the table.</span></span> <span data-ttu-id="e1953-114">知識庫中的定義域和比對規則將會顯示在頁面的右窗格中。</span><span class="sxs-lookup"><span data-stu-id="e1953-114">The domains and matching rules in the knowledge base will be displayed in the right-hand pane of the page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1953-115">您可以在資料表中按一下滑鼠右鍵，對知識庫執行作業。</span><span class="sxs-lookup"><span data-stu-id="e1953-115">You can perform operations on a knowledge base by right-clicking it in the table.</span></span> <span data-ttu-id="e1953-116">您可以開啟知識庫、以另一個名稱儲存、解除鎖定、捨棄工作、重新命名或顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="e1953-116">You can open the knowledge base, save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
4.  <span data-ttu-id="e1953-117">在 **[選取活動]** 中，選取您想要在知識庫上執行的活動：</span><span class="sxs-lookup"><span data-stu-id="e1953-117">In **Select Activity**, select the activity that you want to perform on the knowledge base:</span></span>  
  
    -   <span data-ttu-id="e1953-118">選取 **[定義域管理]** ，進入用來修改知識庫內之定義域的畫面。</span><span class="sxs-lookup"><span data-stu-id="e1953-118">Select **Domain Management** to enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="e1953-119">選取 **[知識探索]** ，進入用來分析資料樣本並以結果擴展知識庫定義域的精靈。</span><span class="sxs-lookup"><span data-stu-id="e1953-119">Select **Knowledge Discovery** to enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="e1953-120">選取 **[比對原則]** 建立比對原則，並將其加入至知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-120">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
5.  <span data-ttu-id="e1953-121">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="e1953-121">Click **Open**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1953-122">若要開啟知識庫，您也可以在知識庫上按一下滑鼠右鍵，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="e1953-122">You can also open the knowledge base by right-clicking it, and then clicking Open.</span></span> <span data-ttu-id="e1953-123">內容功能表中的其他命令可讓您以另一個名稱儲存、解除鎖定、捨棄工作、重新命名或顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="e1953-123">Other commands in the context menu enable you to save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1953-124">如果您因為知識庫已鎖定所以無法將它開啟，請參閱底下的章節。</span><span class="sxs-lookup"><span data-stu-id="e1953-124">If you cannot open the knowledge base because it is locked, see the section below.</span></span>  
  
## <a name="open-a-recent-knowledge-base"></a><span data-ttu-id="e1953-125">開啟最近使用的知識庫</span><span class="sxs-lookup"><span data-stu-id="e1953-125">Open a Recent Knowledge Base</span></span>  
 <span data-ttu-id="e1953-126">最近開啟的五個知識庫會顯示在 DQS 首頁的 **[最近使用的知識庫]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="e1953-126">The five most recently opened knowledge bases are displayed in the **Recent Knowledge Base** list in the DQS home page.</span></span> <span data-ttu-id="e1953-127">如此可讓您開啟最近使用過的知識庫，而不需要透過 **[開啟知識庫]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="e1953-127">This enables you to open a knowledge base that you recently worked on without going through the **Open Knowledge Base** page.</span></span>  
  
-   <span data-ttu-id="e1953-128">若要在最近使用清單中開啟未鎖定的知識庫，請按一下知識庫的向右箭號，然後選取您要開啟之知識庫所在的活動。</span><span class="sxs-lookup"><span data-stu-id="e1953-128">To open a knowledge base in the Recent list that is not locked, click the right arrow for the knowledge base, and then select the activity that you want to open the knowledge base in.</span></span>  
  
-   <span data-ttu-id="e1953-129">若要在最近使用清單中開啟您鎖定的知識庫，請按一下知識庫，它就會在括號所指示的活動與頁面中開啟。</span><span class="sxs-lookup"><span data-stu-id="e1953-129">To open a knowledge base in the Recent list that you locked, click the knowledge base and it will open in the activity and page indicated in parentheses.</span></span>  
  
-   <span data-ttu-id="e1953-130">若要在最近使用清單中開啟已由他人鎖定的知識庫，請連絡這個人，請他解除鎖定知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-130">To open a knowledge base in the Recent list that has been locked by someone else, contact that person and have them unlock the knowledge base.</span></span>  
  
##  <a name="follow-up-after-opening-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="e1953-131">後續操作：開啟知識庫之後</span><span class="sxs-lookup"><span data-stu-id="e1953-131">Follow Up: After Opening a Knowledge Base</span></span>  
 <span data-ttu-id="e1953-132">在您開啟知識庫之後，此知識庫會處於 [知識庫] 資料表的 [狀態] 資料行所指示的狀態。</span><span class="sxs-lookup"><span data-stu-id="e1953-132">After you open a knowledge base, the knowledge base is put into the state indicated in the State column of the Knowledge Base table.</span></span> <span data-ttu-id="e1953-133">如果是知識探索和比對原則活動，將會在特定精靈頁面中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-133">For the knowledge discovery and matching policy activities, the knowledge base will be opened in a specific wizard page.</span></span> <span data-ttu-id="e1953-134">如果是定義域管理活動，將會在定義域管理頁面中開啟知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-134">For the domain management activity, the knowledge base will be opened in the domain management page.</span></span> <span data-ttu-id="e1953-135">如需狀態的詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="e1953-135">For more information about the states, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="if-the-knowledge-base-is-locked"></a><a name="Locked"></a><span data-ttu-id="e1953-136">如果知識庫已鎖定</span><span class="sxs-lookup"><span data-stu-id="e1953-136">If the knowledge base is locked</span></span>  
 <span data-ttu-id="e1953-137">第一個資料行中的鎖定圖示顯示知識庫是否已鎖定。</span><span class="sxs-lookup"><span data-stu-id="e1953-137">The lock icon in the first column shows whether the knowledge base is locked.</span></span> <span data-ttu-id="e1953-138">已鎖定的知識庫名稱將會是紅色字型。</span><span class="sxs-lookup"><span data-stu-id="e1953-138">The name of a locked knowledge base will be in red font.</span></span> <span data-ttu-id="e1953-139">特定使用者透過知識庫活動正在修改的知識庫會標示為已鎖定。</span><span class="sxs-lookup"><span data-stu-id="e1953-139">A knowledge base that is being modified by a specific user through a knowledge base activity is marked as Locked.</span></span> <span data-ttu-id="e1953-140">鎖定的知識庫無法由另一個使用者操作。</span><span class="sxs-lookup"><span data-stu-id="e1953-140">A locked knowledge base cannot be worked on by a second user.</span></span> <span data-ttu-id="e1953-141">正在處理知識庫的使用者若要將知識庫解除鎖定，可以在 [開啟知識庫] 頁面上資料表中的知識庫上按一下滑鼠右鍵，然後按一下 **[解除鎖定]**，或是發行知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-141">The user who is working on the knowledge base can unlock it by right-clicking the knowledge base in the table on the Open Knowledge Base page, and clicking **Unlock**, or by publishing it.</span></span> <span data-ttu-id="e1953-142">當游標置於鎖定的知識庫上時，DQS 將會顯示一個提示，指示鎖定知識庫的人以及鎖定的時間。</span><span class="sxs-lookup"><span data-stu-id="e1953-142">When the cursor is positioned on a locked knowledge base, DQS will display a hint showing who locked the knowledge base and when they locked it.</span></span>  
  
##  <a name="state-of-a-knowledge-base"></a><a name="State"></a><span data-ttu-id="e1953-143">知識庫的狀態</span><span class="sxs-lookup"><span data-stu-id="e1953-143">State of a Knowledge Base</span></span>  
 <span data-ttu-id="e1953-144">狀態欄位會指示知識庫位於活動的哪一個階段。</span><span class="sxs-lookup"><span data-stu-id="e1953-144">The State field indicates which stage of an activity the knowledge base is at.</span></span> <span data-ttu-id="e1953-145">如果您開啟知識庫，它將會開啟到這個階段。</span><span class="sxs-lookup"><span data-stu-id="e1953-145">If you open the knowledge base, it will open to that stage.</span></span>  
  
-   <span data-ttu-id="e1953-146">**\<Empty>**：知識庫的 [狀態] 欄位是空的，如果已在 [定義域管理] 活動中按一下 [**發行**]，然後按一下 [**是-發行知識庫並結束]** 來發行知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-146">**\<Empty>**: The State field is empty for a knowledge base if the knowledge base has been published by clicking **Publish** in the Domain Management activity, and clicking **Yes - Publish the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="e1953-147">**工作中**：已在 [定義域管理] 活動中按一下 [**發行**]，然後按一下 [**否-儲存知識庫工作並**結束] 來儲存知識庫工作。</span><span class="sxs-lookup"><span data-stu-id="e1953-147">**In Work**: Work on the knowledge base has been saved by clicking **Publish** in the Domain Management activity, and clicking **No - Save the work on the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="e1953-148">**定義域管理**：已輸入知識庫的定義域資料，但尚未發行知識庫，而且工作仍在 [定義域管理] 活動中。</span><span class="sxs-lookup"><span data-stu-id="e1953-148">**Domain Management**: Data has been entered for a domain in the knowledge base, but the knowledge base has not been published and the work remains in the Domain Management activity.</span></span> <span data-ttu-id="e1953-149">知識探索活動無法使用。</span><span class="sxs-lookup"><span data-stu-id="e1953-149">The Knowledge Discovery activity is not available.</span></span> <span data-ttu-id="e1953-150">當您在 **[定義域管理]** 畫面中按一下 **[關閉]** 時，就會發生這種狀況。</span><span class="sxs-lookup"><span data-stu-id="e1953-150">This occurs when you click **Close** in the **Domain Management** screen.</span></span>  
  
-   <span data-ttu-id="e1953-151">**探索 - 對應**：已在 **[知識庫管理: 對應]** 頁面上關閉知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-151">**Discovery - Mapping**: The knowledge base was closed on the **Knowledge Base Management: Mapping** page.</span></span> <span data-ttu-id="e1953-152">知識庫已鎖定，無法使用 [定義域管理] 和 [比對] 活動。</span><span class="sxs-lookup"><span data-stu-id="e1953-152">The knowledge base is locked, and the Domain Management and Matching activities are not available.</span></span>  
  
-   <span data-ttu-id="e1953-153">**探索 - 探索**：已在 **[知識庫管理: 分析]** 頁面上關閉知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-153">**Discovery - Discover**: The knowledge base was closed on the **Knowledge Base Management: Analyze** page.</span></span> <span data-ttu-id="e1953-154">知識庫已鎖定，[定義域管理] 活動無法使用。</span><span class="sxs-lookup"><span data-stu-id="e1953-154">The knowledge base is locked, and The Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="e1953-155">**探索-值管理**：已在 [**知識庫管理：管理定義域詞彙**] 頁面上關閉知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-155">**Discovery - Value Management**: The knowledge base was closed on the **Knowledge Base Management: Manage Domain Terms** page.</span></span> <span data-ttu-id="e1953-156">知識庫已鎖定，[定義域管理] 活動無法使用。</span><span class="sxs-lookup"><span data-stu-id="e1953-156">The knowledge base is locked, and the Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="e1953-157">比對**原則-** 比對原則：已在 [比對**原則-** 比對原則] 頁面上關閉知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-157">**Matching Policy - Matching Policy**: The knowledge base was closed on the **Matching Policy - Matching Policy** page.</span></span> <span data-ttu-id="e1953-158">知識庫已鎖定，無法使用 [知識探索] 和 [定義域管理] 活動。</span><span class="sxs-lookup"><span data-stu-id="e1953-158">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
-   <span data-ttu-id="e1953-159">比對**原則-** 比對結果：已在 [比對**原則-** 比對結果] 頁面上關閉知識庫。</span><span class="sxs-lookup"><span data-stu-id="e1953-159">**Matching Policy - Matching Results**: The knowledge base was closed on the **Matching Policy - Matching Results** page.</span></span> <span data-ttu-id="e1953-160">知識庫已鎖定，無法使用 [知識探索] 和 [定義域管理] 活動。</span><span class="sxs-lookup"><span data-stu-id="e1953-160">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
  
