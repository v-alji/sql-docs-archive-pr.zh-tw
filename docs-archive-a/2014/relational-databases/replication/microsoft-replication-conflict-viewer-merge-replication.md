---
title: Microsoft 複寫衝突檢視器 (合併式複寫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvmerge.f1
ms.assetid: bfef5e21-ac04-4bc5-a55e-595421e34923
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1354a35e06f58b56f9678267338917a272ff8b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585314"
---
# <a name="microsoft-replication-conflict-viewer-merge-replication"></a><span data-ttu-id="41bce-102">Microsoft 複寫衝突檢視器 (合併式複寫)</span><span class="sxs-lookup"><span data-stu-id="41bce-102">Microsoft Replication Conflict Viewer (Merge Replication)</span></span>
  <span data-ttu-id="41bce-103">複寫衝突檢視器可以讓您檢視在複寫同步處理過程中發生的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-103">The Replication Conflict Viewer allows you to view any conflicts that have occurred during replication synchronization.</span></span> <span data-ttu-id="41bce-104">如果在兩個不同的伺服器端 (例如，在發行者端和訂閱者端，或在兩個不同的訂閱者端) 修改相同的資料，就會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-104">Conflicts occur when the same data is modified at two separate servers, for example, at a Publisher and Subscriber, or at two different Subscribers.</span></span> <span data-ttu-id="41bce-105">複寫會使用建立發行項時選取的 Conflict Resolver 以自動解決衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-105">Replication automatically resolves conflicts using the conflict resolver you selected when the article was created.</span></span> <span data-ttu-id="41bce-106">不過，複寫衝突檢視器可讓您在必要時選擇衝突的不同解決方案。</span><span class="sxs-lookup"><span data-stu-id="41bce-106">However, the Replication Conflict Viewer allows you to choose a different resolution for the conflict when necessary.</span></span> <span data-ttu-id="41bce-107">會發生下列衝突：</span><span class="sxs-lookup"><span data-stu-id="41bce-107">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="41bce-108">更新衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-108">Update conflicts.</span></span> <span data-ttu-id="41bce-109">更新衝突發生於相同的資料在兩個位置同時更改時。</span><span class="sxs-lookup"><span data-stu-id="41bce-109">Update conflicts occur when the same data is changed at two locations.</span></span> <span data-ttu-id="41bce-110">一個變更成功，而另一個變更失敗。</span><span class="sxs-lookup"><span data-stu-id="41bce-110">One change wins, and the other one loses.</span></span> <span data-ttu-id="41bce-111">您可以選擇保存現有的資料 (成功的資料)、以衝突的資料覆寫現有的資料 (失敗的資料)，或者合併成功與失敗的資料並更新現有的資料。</span><span class="sxs-lookup"><span data-stu-id="41bce-111">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="41bce-112">插入衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-112">Insert conflicts.</span></span> <span data-ttu-id="41bce-113">當資料列插入的位置在合併其他位置的變更時違反某些資料一致性規則時，就會發生插入衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-113">Insert conflicts occur when a row is inserted at one location that violates some data consistency rule when merged with changes at other locations.</span></span> <span data-ttu-id="41bce-114">您可以選擇保存現有的資料 (成功的資料)、以衝突的資料覆寫現有的資料 (失敗的資料)，或者合併成功與失敗的資料並更新現有的資料。</span><span class="sxs-lookup"><span data-stu-id="41bce-114">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="41bce-115">刪除衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-115">Delete conflicts.</span></span> <span data-ttu-id="41bce-116">當資料列在一處已遭刪除，而在另一處已被更新，就會發生此衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-116">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="41bce-117">同步處理期間解決衝突時，遺失之資料列的資料會寫入衝突資料表。</span><span class="sxs-lookup"><span data-stu-id="41bce-117">When conflicts are resolved during synchronization, the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="41bce-118">不論您接受原始解決方案或為衝突選擇不同的解決方案，都會從衝突資料表刪除記錄的衝突資料列。</span><span class="sxs-lookup"><span data-stu-id="41bce-118">Whether you accept the original resolution or choose a different resolution for the conflict, the logged conflict row is deleted from the conflict table.</span></span> <span data-ttu-id="41bce-119">您應該定期檢閱衝突，以協助減少衝突追蹤資料表的大小。</span><span class="sxs-lookup"><span data-stu-id="41bce-119">You should periodically review conflicts to help reduce the size of the conflict tracking tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41bce-120">「衝突檢視器」中不會顯示涉及邏輯記錄的衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-120">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="41bce-121">若要檢視這些衝突的相關資訊，請使用複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="41bce-121">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="41bce-122">如需詳細資訊，請參閱[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="41bce-122">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="41bce-123">選項</span><span class="sxs-lookup"><span data-stu-id="41bce-123">Options</span></span>  
 <span data-ttu-id="41bce-124">複寫衝突檢視器會劃分為兩個區段。</span><span class="sxs-lookup"><span data-stu-id="41bce-124">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="41bce-125">對話方塊的上半段會顯示選取之資料表的衝突清單。</span><span class="sxs-lookup"><span data-stu-id="41bce-125">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="41bce-126">當您按一下衝突清單中的某個項目時，對話方塊的下半段中會顯示衝突的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="41bce-126">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="41bce-127">描述為何發生衝突的資訊 (例如，同時在發行者與訂閱者端更新相同的資料列)，會顯示在對話方塊的下半段中。</span><span class="sxs-lookup"><span data-stu-id="41bce-127">Information describing why the conflict occurred (for example, the same row was updated at both the Publisher and the Subscriber) is displayed in the lower section of the dialog box.</span></span> <span data-ttu-id="41bce-128">下半段中的衝突資料，會在兩個對應的資料行 (**[衝突成功者]** 和 **[衝突失敗者]**) 中顯示。</span><span class="sxs-lookup"><span data-stu-id="41bce-128">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="41bce-129">如果衝突是發生在已更新和已刪除的資料之間，那麼衝突中已刪除的一方可能沒有資料可以顯示。</span><span class="sxs-lookup"><span data-stu-id="41bce-129">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="41bce-130">在此情況下，複寫衝突檢視器會在其中一個資料行裡顯示訊息，指出刪除一個位置的資料列而更新另一個位置的資料列。</span><span class="sxs-lookup"><span data-stu-id="41bce-130">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating that the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="41bce-131">它也會指出建議的解決方式。</span><span class="sxs-lookup"><span data-stu-id="41bce-131">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="41bce-132">無法在複寫衝突檢視器中編輯的資料 (例如， **rowguid** 資料)，會使用陰影方塊以唯讀顯示。</span><span class="sxs-lookup"><span data-stu-id="41bce-132">Data that cannot be edited in the Replication Conflict Viewer (for example, **rowguid** data) is displayed read-only with the box shaded.</span></span>  
  
 <span data-ttu-id="41bce-133">**Database**</span><span class="sxs-lookup"><span data-stu-id="41bce-133">**Database**</span></span>  
 <span data-ttu-id="41bce-134">選擇包含有衝突之發行集的資料庫。</span><span class="sxs-lookup"><span data-stu-id="41bce-134">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="41bce-135">**發行**</span><span class="sxs-lookup"><span data-stu-id="41bce-135">**Publication**</span></span>  
 <span data-ttu-id="41bce-136">選擇包含有衝突之資料表的發行集。</span><span class="sxs-lookup"><span data-stu-id="41bce-136">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="41bce-137">**資料表**</span><span class="sxs-lookup"><span data-stu-id="41bce-137">**Table**</span></span>  
 <span data-ttu-id="41bce-138">選擇包含衝突的資料表。</span><span class="sxs-lookup"><span data-stu-id="41bce-138">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="41bce-139">**定義篩選**</span><span class="sxs-lookup"><span data-stu-id="41bce-139">**Define Filter**</span></span>  
 <span data-ttu-id="41bce-140">按一下即可開啟 **[定義篩選]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="41bce-140">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="41bce-141">**套用或移除篩選**</span><span class="sxs-lookup"><span data-stu-id="41bce-141">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="41bce-142">按一下即可套用或移除在 **[定義篩選]** 對話方塊中已定義的篩選。</span><span class="sxs-lookup"><span data-stu-id="41bce-142">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="41bce-143">**全選**</span><span class="sxs-lookup"><span data-stu-id="41bce-143">**Select All**</span></span>  
 <span data-ttu-id="41bce-144">按一下即可選取在方格中列出的所有衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-144">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="41bce-145">**選取無**</span><span class="sxs-lookup"><span data-stu-id="41bce-145">**Select None**</span></span>  
 <span data-ttu-id="41bce-146">按一下即可取消選取方格中列出的所有衝突。</span><span class="sxs-lookup"><span data-stu-id="41bce-146">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="41bce-147">**移除**</span><span class="sxs-lookup"><span data-stu-id="41bce-147">**Remove**</span></span>  
 <span data-ttu-id="41bce-148">按一下即可從檢視器中移除選取的衝突，以及從複寫系統資料表中移除其相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="41bce-148">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span> <span data-ttu-id="41bce-149">相當於為所選的每個衝突按一下 [提交成功者] 按鈕 (不對資料做任何變更)。</span><span class="sxs-lookup"><span data-stu-id="41bce-149">Equivalent to clicking the Submit Winner button (without making any changes to the data) for each selected conflict.</span></span>  
  
 <span data-ttu-id="41bce-150">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="41bce-150">**Show all columns**</span></span>  
 <span data-ttu-id="41bce-151">選取即可顯示資料表的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="41bce-151">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="41bce-152">**顯示前五個資料行和有衝突資料的其他資料行。**</span><span class="sxs-lookup"><span data-stu-id="41bce-152">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="41bce-153">選取即可顯示前五個資料行和有衝突的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="41bce-153">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="41bce-154">當資料表有大量資料行，但是您只想查看與解決衝突最相關的資料行時，這很有用。</span><span class="sxs-lookup"><span data-stu-id="41bce-154">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="41bce-155">前五個資料行一律會包含在此檢視中做為識別資料列的欄位，例如主索引鍵或名稱欄位，通常是在資料表的前幾個資料行中。</span><span class="sxs-lookup"><span data-stu-id="41bce-155">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="41bce-156">**顯示資料行資訊** ([...]\*\*\*\*)</span><span class="sxs-lookup"><span data-stu-id="41bce-156">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="41bce-157">按一下即可檢視資料行資訊： **[資料表名稱]**、 **[資料行名稱]**、 **[資料類型]** 和 **[資料行值]**。</span><span class="sxs-lookup"><span data-stu-id="41bce-157">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span> <span data-ttu-id="41bce-158">**[資料行值]** 是可編輯的，除非以唯讀顯示該值。</span><span class="sxs-lookup"><span data-stu-id="41bce-158">**Column Value** is editable unless the value is displayed as read-only.</span></span>  
  
 <span data-ttu-id="41bce-159">**提交成功者**</span><span class="sxs-lookup"><span data-stu-id="41bce-159">**Submit Winner**</span></span>  
 <span data-ttu-id="41bce-160">按一下即可使 Conflict Resolver 所決定的資料列仍是成功者。</span><span class="sxs-lookup"><span data-stu-id="41bce-160">Click to keep the row the conflict resolver determined to be the winner.</span></span> <span data-ttu-id="41bce-161">按一下此按鈕之前，可以變更非顯示為唯讀之任何資料行的值。</span><span class="sxs-lookup"><span data-stu-id="41bce-161">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="41bce-162">**提交失敗者**</span><span class="sxs-lookup"><span data-stu-id="41bce-162">**Submit Loser**</span></span>  
 <span data-ttu-id="41bce-163">按一下即可接受 Conflict Resolver 所決定的資料列為失敗者。</span><span class="sxs-lookup"><span data-stu-id="41bce-163">Click to accept the row the conflict resolver determined to be the loser.</span></span> <span data-ttu-id="41bce-164">按一下此按鈕之前，可以變更非顯示為唯讀之任何資料行的值。</span><span class="sxs-lookup"><span data-stu-id="41bce-164">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="41bce-165">**記錄衝突的詳細資料**</span><span class="sxs-lookup"><span data-stu-id="41bce-165">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="41bce-166">選取此方塊即可將衝突的詳細資料記錄到檔案。</span><span class="sxs-lookup"><span data-stu-id="41bce-166">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="41bce-167">若要指定檔案的位置，請指向 **[檢視]** 功能表，然後按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="41bce-167">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="41bce-168">輸入一個值，或按一下瀏覽 (**...**)，然後導覽至適當的檔案。</span><span class="sxs-lookup"><span data-stu-id="41bce-168">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="41bce-169">按一下 **[確定]** 即可結束 **[選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="41bce-169">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bce-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41bce-170">See Also</span></span>  
 <span data-ttu-id="41bce-171">[查看和解決合併式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="41bce-171">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 [<span data-ttu-id="41bce-172">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="41bce-172">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
