---
title: Microsoft 複寫衝突檢視器 (異動複寫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cc3f2ea3d1d2b29fba9c9d9121e23bf4bcd88bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584426"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a><span data-ttu-id="250d8-102">Microsoft 複寫衝突檢視器 (異動複寫)</span><span class="sxs-lookup"><span data-stu-id="250d8-102">Microsoft Replication Conflict Viewer (Transactional Replication)</span></span>
  <span data-ttu-id="250d8-103">「複寫衝突檢視器」可讓您檢視在點對點異動複寫和具有佇列更新訂閱之異動複寫的同步處理期間發生的衝突。</span><span class="sxs-lookup"><span data-stu-id="250d8-103">The Replication Conflict Viewer enables you to view conflicts that have occurred during synchronization for peer-to-peer transactional replication and transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="250d8-104">如需詳細資訊，請參閱[檢視交易式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="250d8-104">For more information, see [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="250d8-105">「複寫衝突檢視器」會顯示在合併式複寫和異動複寫中發生的衝突。</span><span class="sxs-lookup"><span data-stu-id="250d8-105">The Replication Conflict Viewer displays conflicts that occur in merge replication and in transactional replication.</span></span> <span data-ttu-id="250d8-106">若為異動複寫，您可以使用「複寫衝突檢視器」來檢視衝突資料，但是無法針對衝突選擇不同的解決方案。</span><span class="sxs-lookup"><span data-stu-id="250d8-106">For transactional replication, you can use Replication Conflict Viewer to view conflict data, but you cannot choose a different resolution for the conflict.</span></span>  
  
## <a name="options"></a><span data-ttu-id="250d8-107">選項</span><span class="sxs-lookup"><span data-stu-id="250d8-107">Options</span></span>  
 <span data-ttu-id="250d8-108">複寫衝突檢視器會劃分為兩個區段。</span><span class="sxs-lookup"><span data-stu-id="250d8-108">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="250d8-109">對話方塊的上半段會顯示選取之資料表的衝突清單。</span><span class="sxs-lookup"><span data-stu-id="250d8-109">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="250d8-110">當您按一下衝突清單中的某個項目時，對話方塊的下半段中會顯示衝突的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="250d8-110">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="250d8-111">下半段中的衝突資料，會在兩個對應的資料行 (**[衝突成功者]** 和 **[衝突失敗者]**) 中顯示。</span><span class="sxs-lookup"><span data-stu-id="250d8-111">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="250d8-112">如果衝突是發生在已更新和已刪除的資料之間，那麼衝突中已刪除的一方可能沒有資料可以顯示。</span><span class="sxs-lookup"><span data-stu-id="250d8-112">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="250d8-113">在此情況下，複寫衝突檢視器會在其中一個資料行裡顯示訊息，這表示資料列在一處已遭刪除，而在另一處已被更新。</span><span class="sxs-lookup"><span data-stu-id="250d8-113">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="250d8-114">它也會指出建議的解決方式。</span><span class="sxs-lookup"><span data-stu-id="250d8-114">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="250d8-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="250d8-115">**Database**</span></span>  
 <span data-ttu-id="250d8-116">選擇包含有衝突之發行集的資料庫。</span><span class="sxs-lookup"><span data-stu-id="250d8-116">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="250d8-117">**發行**</span><span class="sxs-lookup"><span data-stu-id="250d8-117">**Publication**</span></span>  
 <span data-ttu-id="250d8-118">選擇包含有衝突之資料表的發行集。</span><span class="sxs-lookup"><span data-stu-id="250d8-118">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="250d8-119">**資料表**</span><span class="sxs-lookup"><span data-stu-id="250d8-119">**Table**</span></span>  
 <span data-ttu-id="250d8-120">選擇包含衝突的資料表。</span><span class="sxs-lookup"><span data-stu-id="250d8-120">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="250d8-121">**定義篩選**</span><span class="sxs-lookup"><span data-stu-id="250d8-121">**Define Filter**</span></span>  
 <span data-ttu-id="250d8-122">按一下即可開啟 **[定義篩選]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="250d8-122">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="250d8-123">**套用或移除篩選**</span><span class="sxs-lookup"><span data-stu-id="250d8-123">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="250d8-124">按一下即可套用或移除在 **[定義篩選]** 對話方塊中已定義的篩選。</span><span class="sxs-lookup"><span data-stu-id="250d8-124">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="250d8-125">**全選**</span><span class="sxs-lookup"><span data-stu-id="250d8-125">**Select All**</span></span>  
 <span data-ttu-id="250d8-126">按一下即可選取在方格中列出的所有衝突。</span><span class="sxs-lookup"><span data-stu-id="250d8-126">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="250d8-127">**選取無**</span><span class="sxs-lookup"><span data-stu-id="250d8-127">**Select None**</span></span>  
 <span data-ttu-id="250d8-128">按一下即可取消選取方格中列出的所有衝突。</span><span class="sxs-lookup"><span data-stu-id="250d8-128">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="250d8-129">**移除**</span><span class="sxs-lookup"><span data-stu-id="250d8-129">**Remove**</span></span>  
 <span data-ttu-id="250d8-130">按一下即可從檢視器中移除選取的衝突，以及從複寫系統資料表中移除其相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="250d8-130">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span>  
  
 <span data-ttu-id="250d8-131">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="250d8-131">**Show all columns**</span></span>  
 <span data-ttu-id="250d8-132">選取即可顯示資料表的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="250d8-132">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="250d8-133">**顯示前五個資料行和有衝突資料的其他資料行。**</span><span class="sxs-lookup"><span data-stu-id="250d8-133">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="250d8-134">選取即可顯示前五個資料行和有衝突的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="250d8-134">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="250d8-135">當資料表有大量資料行，但是您只想查看與解決衝突最相關的資料行時，這很有用。</span><span class="sxs-lookup"><span data-stu-id="250d8-135">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="250d8-136">前五個資料行一律會包含在此檢視中做為識別資料列的欄位，例如主索引鍵或名稱欄位，通常是在資料表的前幾個資料行中。</span><span class="sxs-lookup"><span data-stu-id="250d8-136">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="250d8-137">**顯示資料行資訊** ([...]\*\*\*\*)</span><span class="sxs-lookup"><span data-stu-id="250d8-137">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="250d8-138">按一下即可檢視資料行資訊： **[資料表名稱]**、 **[資料行名稱]**、 **[資料類型]** 和 **[資料行值]**。</span><span class="sxs-lookup"><span data-stu-id="250d8-138">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span>  
  
 <span data-ttu-id="250d8-139">**記錄衝突的詳細資料**</span><span class="sxs-lookup"><span data-stu-id="250d8-139">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="250d8-140">選取此方塊即可將衝突的詳細資料記錄到檔案。</span><span class="sxs-lookup"><span data-stu-id="250d8-140">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="250d8-141">若要指定檔案的位置，請指向 **[檢視]** 功能表，然後按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="250d8-141">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="250d8-142">輸入一個值，或按一下瀏覽 (**...**)，然後導覽至適當的檔案。</span><span class="sxs-lookup"><span data-stu-id="250d8-142">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="250d8-143">按一下 **[確定]** 即可結束 **[選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="250d8-143">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250d8-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="250d8-144">See Also</span></span>  
 <span data-ttu-id="250d8-145">[點對點複寫中的衝突偵測](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span><span class="sxs-lookup"><span data-stu-id="250d8-145">[Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span></span>  
 [<span data-ttu-id="250d8-146">檢視交易式發行集的資料衝突 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="250d8-146">View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;</span></span>](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
