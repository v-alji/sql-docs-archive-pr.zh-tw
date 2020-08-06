---
title: 工作 4 (選擇性) ：結合、比對及發行新的資料集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ddcec19fa8b957bf77b6ea5269b4d033779bdf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585690"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a><span data-ttu-id="e96d5-102">工作 4 (選擇性)：結合、比對及發行新的資料集</span><span class="sxs-lookup"><span data-stu-id="e96d5-102">Task 4 (Optional): Combining, Matching, and Publishing New Set of Data</span></span>
  <span data-ttu-id="e96d5-103">經過一段時間後，您需要將更多的資料加入至 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="e96d5-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="e96d5-104">在加入資料之前，比較新資料與已在 MDS 中管理的資料可能會很有用，以確保您不會加入重複或不正確的資料。</span><span class="sxs-lookup"><span data-stu-id="e96d5-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure that you are not adding duplicate or inaccurate data.</span></span> <span data-ttu-id="e96d5-105">在適用於 Excel 的 Master Data Services 增益集中，您可以結合兩個工作表中的資料然後比較資料，以識別重複項並加以移除，之後再將資料發行到 MDS。</span><span class="sxs-lookup"><span data-stu-id="e96d5-105">In the Master Data Services Add-in for Excel, you can combine data from two worksheets and the compare the data to identify and remove duplicates before publishing the data to MDS.</span></span> <span data-ttu-id="e96d5-106">MDS Excel 增益集的比對功能會使用 DQS 比對功能來識別資料中的相符內容。</span><span class="sxs-lookup"><span data-stu-id="e96d5-106">The matching feature of MDS Excel Add-in uses the DQS matching functionality to identify matches in the data.</span></span> <span data-ttu-id="e96d5-107">在這項工作中，您會將兩個工作表中的資料結合到一個工作表，然後執行比對活動來識別重複項並加以移除，之後再將資料發行到 MDS。</span><span class="sxs-lookup"><span data-stu-id="e96d5-107">In this task, you will combine data from a two worksheets into one and then perform the matching activity to identify and remove duplicates before publishing to MDS.</span></span> <span data-ttu-id="e96d5-108">如需詳細資訊，請參閱[適用于 Excel 的 MDS 增益集中的資料品質](https://msdn.microsoft.com/library/hh548681.aspx)比對和[合併資料](https://msdn.microsoft.com/library/hh548680.aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="e96d5-108">See [Data Quality Matching in the MDS Add-in for Excel](https://msdn.microsoft.com/library/hh548681.aspx) and [Combine Data](https://msdn.microsoft.com/library/hh548680.aspx) topics for more details.</span></span>  
  
1.  <span data-ttu-id="e96d5-109">啟動新的**Excel**實例。</span><span class="sxs-lookup"><span data-stu-id="e96d5-109">Launch new instance of **Excel**.</span></span> <span data-ttu-id="e96d5-110">按一下 [**開始**]，指向 [**執行**]，輸入**Excel**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-110">Click **Start**, point to **Run**, type **Excel**, and click **OK**.</span></span>  
  
2.  <span data-ttu-id="e96d5-111">按一下功能表列上的 [**主要資料**]，切換至 [**主要資料**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e96d5-111">Switch to the **Master Data** tab by clicking **Master Data** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="e96d5-112">在 [**連接和載入]** 群組中，按一下功能區上的 **[連接**]，連接到**MDS 伺服器**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-112">Click **Connect** on the ribbon in the **Connect and Load** group to connect to the **MDS server**.</span></span> <span data-ttu-id="e96d5-113">您在這一課的稍早已經設定這個連接。</span><span class="sxs-lookup"><span data-stu-id="e96d5-113">You have configured this connection earlier in this lesson.</span></span>  
  
     <span data-ttu-id="e96d5-114">![Excel - [主要資料] 索引標籤上的 [顯示總管] 按鈕](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - [主要資料] 索引標籤上的 [顯示總管] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="e96d5-114">![Excel - Show Explorer Button on Master Data Tabl](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - Show Explorer Button on Master Data Tabl")</span></span>  
  
4.  <span data-ttu-id="e96d5-115">您應該會在右側看到 [**主要資料總管**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e96d5-115">You should see the **Master Data Explorer** pane to the right.</span></span> <span data-ttu-id="e96d5-116">如果您看不到主要資料總管，請按一下功能區上的 [**顯示瀏覽器**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e96d5-116">If you do not see the Master Data Explorer, click **Show Explorer** button on the ribbon.</span></span>  
  
5.  <span data-ttu-id="e96d5-117">在 [**主資料總管**] 視窗中，選取**模型**下拉式清單中的 [**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-117">In the **Master Data Explorer** Window, select **Suppliers** in the drop-down list for the **Model**.</span></span> <span data-ttu-id="e96d5-118">您應該會看到此模型有一個實體：**供應商**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-118">You should see that the model has one entity: **Supplier**.</span></span>  
  
     <span data-ttu-id="e96d5-119">![Excel - [主資料總管] 視窗](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - [主資料總管] 視窗")</span><span class="sxs-lookup"><span data-stu-id="e96d5-119">![Excel - Master Data Explorer Window](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - Master Data Explorer Window")</span></span>  
  
6.  <span data-ttu-id="e96d5-120">按兩下 [實體] 清單中的 [**供應商**]，將實體成員載入至 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="e96d5-120">Double-click **Supplier** in the entity list to load the entity members into the Excel worksheet.</span></span>  
  
7.  <span data-ttu-id="e96d5-121">按一下底部的 [ **sheet2** ] 以切換至 [ **sheet2** ] 索引標籤。如果您沒有看到 [ **Sheet2**]，請加入新的工作表。</span><span class="sxs-lookup"><span data-stu-id="e96d5-121">Click **Sheet2** at the bottom to switch to the **Sheet2** tab. If you do not see **Sheet2**, add a new worksheet.</span></span>  
  
8.  <span data-ttu-id="e96d5-122">開啟**Suppliers.xls**檔案 (包含在教學課程檔案中的原始輸入檔) 並將所有 (三個) 資料列從**CombineAndCleanse**工作表複製到**Sheet2**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-122">Open **Suppliers.xls** file (the original input file that is included in the tutorial files) and copy all (three) rows from the **CombineAndCleanse** worksheet to **Sheet2**.</span></span>  
  
9. <span data-ttu-id="e96d5-123">切換回書籍1中的**供應商**工作表 **-Microsoft Excel** (不是連接至**MDS**的**清理和符合供應商清單**Excel) 。</span><span class="sxs-lookup"><span data-stu-id="e96d5-123">Switch back to the **Supplier** sheet in the **Book 1 - Microsoft Excel** (not the **Cleansed and Matched Supplier List** Excel) that is connected to **MDS**.</span></span>  
  
10. <span data-ttu-id="e96d5-124">按一下功能表列上的 [**主要資料**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-124">Click **Master Data** on the menu bar.</span></span>  
  
11. <span data-ttu-id="e96d5-125">按一下功能區上的 [**合併資料**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-125">Click **Combine Data** on the ribbon.</span></span> <span data-ttu-id="e96d5-126">您會看到 [**結合資料**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e96d5-126">You will see the **Combine Data** dialog box.</span></span>  
  
12. <span data-ttu-id="e96d5-127">在 [**結合資料**] 對話方塊中，按一下 [**要與 MDS 資料結合的範圍**] 文字方塊旁邊的按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e96d5-127">In the **Combine Data** dialog box, click the button next to **Range to combine with MDS data** text box as shown in the following image.</span></span>  
  
     <span data-ttu-id="e96d5-128">![Excel - [結合資料] 對話方塊](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - [結合資料] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="e96d5-128">![Excel - Combine Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - Combine Data Dialog Box")</span></span>  
  
13. <span data-ttu-id="e96d5-129">您現在應該會看到縮小的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e96d5-129">You should see the shrunken dialog box now.</span></span> <span data-ttu-id="e96d5-130">現在，按一下 [ **sheet2** ] 切換至 [ **sheet2** ] 索引標籤，其中包含4個數據列的新供應商資料 (包括一個標題列) 。</span><span class="sxs-lookup"><span data-stu-id="e96d5-130">Now, click **Sheet2** to switch to the **Sheet2** tab that has the new supplier data with 4 rows (including one header row).</span></span>  
  
14. <span data-ttu-id="e96d5-131">在 [ **Sheet2**] 中，選取**包含標頭資料列的所有資料列**，即使它們似乎已選取) ，也 (。</span><span class="sxs-lookup"><span data-stu-id="e96d5-131">In the **Sheet2**, select **all rows including the header row** (even if they seem to be already selected).</span></span> <span data-ttu-id="e96d5-132">您應該會看到 [**要與 MDS 資料結合的範圍**] 已自動更新。</span><span class="sxs-lookup"><span data-stu-id="e96d5-132">You should see the **Range to combine with MDS data** is automatically updated.</span></span>  
  
     <span data-ttu-id="e96d5-133">![Excel - [結合資料] 對話方塊 - 最小化](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - [結合資料] 對話方塊 - 最小化")</span><span class="sxs-lookup"><span data-stu-id="e96d5-133">![Excel - Combine Data Dialog Box - Minimized](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - Combine Data Dialog Box - Minimized")</span></span>  
  
15. <span data-ttu-id="e96d5-134">切換回 [**供應商**] 索引標籤，而不關閉 [**結合資料**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e96d5-134">Switch back to the **Suppliers** tab without closing the **Combine Data** dialog box.</span></span>  
  
16. <span data-ttu-id="e96d5-135">按一下**文字方塊**旁邊的**按鈕**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-135">Click the **button** next to the **text box**.</span></span> <span data-ttu-id="e96d5-136">您現在應該會看到對話方塊已放大。</span><span class="sxs-lookup"><span data-stu-id="e96d5-136">You should see that the dialog box is expanded now.</span></span> <span data-ttu-id="e96d5-137">您應該會看到 [**供應商**MDS**實體**] 資料行與**Excel**資料行之間的所有對應都會自動填入。</span><span class="sxs-lookup"><span data-stu-id="e96d5-137">You should see all the mappings between columns of the **Supplier** MDS **entity** to **Excel** columns are automatically populated.</span></span>  
  
     <span data-ttu-id="e96d5-138">![Excel - 有資料填入的 [結合資料] 對話方塊](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - 有資料填入的 [結合資料] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="e96d5-138">![Excel - Combine Data Dialog Box Filled with Data](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - Combine Data Dialog Box Filled with Data")</span></span>  
  
17. <span data-ttu-id="e96d5-139">請確定 [程式**代碼**實體] 資料行對應至工作表中的 [已**供應**專案] 資料行，而且 [**郵遞區號**] 實體資料行對應至工作表中的 [**郵遞區號**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="e96d5-139">Ensure that **Code** entity column is mapped to the **SupplierID** column in the worksheet and **Zip Code** entity column is mapped to the **Zip Code** column in the worksheet.</span></span>  
  
18. <span data-ttu-id="e96d5-140">在 [**結合資料**] 對話方塊中，按一下 [**合併**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-140">On the **Combine Data** dialog box, click **Combine**.</span></span>  
  
19. <span data-ttu-id="e96d5-141">確認三個資料列已加入至工作表底部，而且應該有色彩標示。</span><span class="sxs-lookup"><span data-stu-id="e96d5-141">Confirm that three data rows are added to the bottom of the worksheet and they should be color coded.</span></span>  
  
     <span data-ttu-id="e96d5-142">![Excel - 結合之後的新元素](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - 結合之後的新元素")</span><span class="sxs-lookup"><span data-stu-id="e96d5-142">![Excel - New Elements after Combining](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - New Elements after Combining")</span></span>  
  
20. <span data-ttu-id="e96d5-143">按一下功能區上的 [**數學資料**] 以識別重複專案。</span><span class="sxs-lookup"><span data-stu-id="e96d5-143">Click **Math Data** on the ribbon to identify duplicates.</span></span> <span data-ttu-id="e96d5-144">此功能會使用 DQS 的比對功能。</span><span class="sxs-lookup"><span data-stu-id="e96d5-144">This feature uses the matching functionality of DQS.</span></span>  
  
21. <span data-ttu-id="e96d5-145">在 [比對**資料**] 對話方塊中，選取 [適用于**DQS 知識庫**的**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-145">In the **Match Data** dialog box, select **Suppliers** for **DQS Knowledge Base**.</span></span>  
  
     <span data-ttu-id="e96d5-146">![Excel - [比對資料] 對話方塊](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - [比對資料] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="e96d5-146">![Excel - Match Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Match Data Dialog Box")</span></span>  
  
22. <span data-ttu-id="e96d5-147">將工作表資料行對應至定義域，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="e96d5-147">Map worksheet columns to domains as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e96d5-148">工作表資料行</span><span class="sxs-lookup"><span data-stu-id="e96d5-148">Worksheet Column</span></span>|<span data-ttu-id="e96d5-149">網域</span><span class="sxs-lookup"><span data-stu-id="e96d5-149">Domain</span></span>|  
    |----------------------|------------|  
    |<span data-ttu-id="e96d5-150">Code (您已上傳供應商識別碼當做 MDS 中供應商實體的代碼)</span><span class="sxs-lookup"><span data-stu-id="e96d5-150">Code (you uploaded Supplier ID as the Code for the Supplier entity in MDS)</span></span>|<span data-ttu-id="e96d5-151">Supplier ID</span><span class="sxs-lookup"><span data-stu-id="e96d5-151">Supplier ID</span></span>|  
    |<span data-ttu-id="e96d5-152">Name (您已上傳供應商名稱當做 MDS 中供應商實體的名稱)</span><span class="sxs-lookup"><span data-stu-id="e96d5-152">Name (you uploaded Supplier Name as the Name for the Supplier entity to MDS)</span></span>|<span data-ttu-id="e96d5-153">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="e96d5-153">Supplier Name</span></span>|  
    |<span data-ttu-id="e96d5-154">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="e96d5-154">ContactEmailAddress</span></span>|<span data-ttu-id="e96d5-155">ContactEmail</span><span class="sxs-lookup"><span data-stu-id="e96d5-155">ContactEmail</span></span>|  
  
23. <span data-ttu-id="e96d5-156">針對 [程式**代碼**資料**行對應]** 選取 [必要條件]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-156">Select **Prerequisite** for the **Code** column mapping.</span></span>  
  
24. <span data-ttu-id="e96d5-157">輸入 [ **70%** ] 作為 [**供應商名稱**] 的**權數**，而**30%** 作為 [**連絡人電子郵件**] 的**權數**（如圖所示）。</span><span class="sxs-lookup"><span data-stu-id="e96d5-157">Enter **70%** as the **weight** for **Supplier Name** and **30%** as the **weight** for **Contact Email** as shown in the image.</span></span>  
  
25. <span data-ttu-id="e96d5-158">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e96d5-158">Click **OK**.</span></span>  
  
26. <span data-ttu-id="e96d5-159">比對程式應該會為供應商識別一個重複的**代碼： S1**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-159">The matching process should identify one duplicate for the supplier with **Code: S1**.</span></span>  
  
     <span data-ttu-id="e96d5-160">![Excel - 比對結果](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - 比對結果")</span><span class="sxs-lookup"><span data-stu-id="e96d5-160">![Excel - Matching Results](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - Matching Results")</span></span>  
  
27. <span data-ttu-id="e96d5-161">選取\*\* (橙色) 的重復資料列**，按一下滑鼠右鍵，然後按一下 [**刪除\*\*] 來刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="e96d5-161">Select the **duplicate row (orange)**, right-click, and click **Delete** to delete the row.</span></span>  
  
28. <span data-ttu-id="e96d5-162">刪除**CLUSTER_ID**的資料行，因為您不再需要它。</span><span class="sxs-lookup"><span data-stu-id="e96d5-162">Delete the **CLUSTER_ID** column since you don't need it anymore.</span></span>  
  
29. <span data-ttu-id="e96d5-163">按一下 [**發佈**]，將具有**代碼 S66**和**S57**的其他兩個新記錄發佈到 MDS。</span><span class="sxs-lookup"><span data-stu-id="e96d5-163">Click **Publish** to publish the other two new records with **Codes S66** and **S57** to MDS.</span></span>  
  
30. <span data-ttu-id="e96d5-164">在 [**發行並批註**] 對話方塊中，加入**批註**，然後按一下 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-164">In the **Publish and Annotate** dialog box, add an **annotation**, and click **Publish**.</span></span>  
  
31. <span data-ttu-id="e96d5-165">切換至**主資料管理員 Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e96d5-165">Switch to the **Master Data Manager Web application**.</span></span>  
  
32. <span data-ttu-id="e96d5-166">在 [首頁] 頁面上，確定已針對**模型**選取 [**供應商**]，然後按一下 [ **Explorer**]。</span><span class="sxs-lookup"><span data-stu-id="e96d5-166">On the home page, ensure that **Suppliers** is selected for the **Model**, and click **Explorer**.</span></span> <span data-ttu-id="e96d5-167">如果您已經開啟**Explorer** ，請重新整理網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e96d5-167">If you already have the **Explorer** open, refresh the internet browser.</span></span>  
  
33. <span data-ttu-id="e96d5-168">依程式**代碼\*\*\*\*排序**清單，並使用**S57**和**S66**做為程式碼尋找記錄。</span><span class="sxs-lookup"><span data-stu-id="e96d5-168">**Sort** the list by **Code** and look for records with **S57** and **S66** as codes.</span></span> <span data-ttu-id="e96d5-169">您也可以使用工具列上的 [**篩選**] 按鈕來搜尋清單中的特定記錄。</span><span class="sxs-lookup"><span data-stu-id="e96d5-169">You can also use the **Filter** button on the toolbar to search for a specific record in the list.</span></span>  
  
34. <span data-ttu-id="e96d5-170">現在，關閉**Book1-Microsoft Excel**視窗，而不儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="e96d5-170">Now, close **Book1 - Microsoft Excel** window without saving the file.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e96d5-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e96d5-171">Next Step</span></span>  
 [<span data-ttu-id="e96d5-172">工作 5：從 Excel 建立定義域屬性</span><span class="sxs-lookup"><span data-stu-id="e96d5-172">Task 5: Creating a Domain-Based Attribute from Excel</span></span>](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
