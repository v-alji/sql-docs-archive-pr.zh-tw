---
title: 工作12：探索知識 (知識探索) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2dee66f94f1df609701f92d591f2c31863702465
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698998"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a><span data-ttu-id="ac3e5-102">工作 12：探索知識 (知識探索)</span><span class="sxs-lookup"><span data-stu-id="ac3e5-102">Task 12: Discovering Knowledge (Knowledge Discovery)</span></span>
  <span data-ttu-id="ac3e5-103">在這項工作中，您會對**供應商識別碼**和**供應商名稱**網域執行**知識探索**活動。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-103">In this task, you perform the **Knowledge Discovery** activity on **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="ac3e5-104">在此案例中，知識探索程序主要會匯入這兩個定義域的值。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-104">In this scenario, the knowledge discovery process mainly imports values for these two domains.</span></span>  
  
 <span data-ttu-id="ac3e5-105">在本教學課程中，您會從頭開始建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-105">In this tutorial, you started building knowledge base from scratch.</span></span> <span data-ttu-id="ac3e5-106">您也可以藉由執行知識探索活動來開始建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-106">You can also start creating a knowledge base by performing a knowledge discovery activity.</span></span> <span data-ttu-id="ac3e5-107">當您在主頁面中按一下 [**建立知識庫**] 時，DQS 用戶端會帶您前往已針對活動選取 [**定義域管理**] 活動的頁面。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-107">When you click **Create a Knowledge Base** in the main page, DQS client takes you to a page with **Domain Management** activity selected for the activity.</span></span> <span data-ttu-id="ac3e5-108">您可以將**活動**變更為 [**知識探索**]，然後在下一個頁面中，您可以在知識探索程式中建立定義域。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-108">You can change the **activity** to **Knowledge Discovery** and then in the next page you can create domains as part of the knowledge discovery process.</span></span> <span data-ttu-id="ac3e5-109">如需詳細資訊，請參閱[執行知識探索](https://msdn.microsoft.com/library/hh510398.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-109">See [Perform Knowledge Discovery](https://msdn.microsoft.com/library/hh510398.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="ac3e5-110">在 DQS 用戶端的主頁面中，于 [**最近使用的知識庫**] 區段中，按一下 [**供應商**] 知識庫旁的**向右箭**號，然後按一下 [**知識探索**]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-110">In the main page of DQS Client, in the **Recent Knowledge Base** section, click **right-arrow** next to the **Suppliers** knowledge base and click **Knowledge Discovery**.</span></span> <span data-ttu-id="ac3e5-111">或者，您可以按一下 [**開啟知識庫**]，從**知識庫清單**中選取 [**供應商**]，選取 [**知識探索**] 作為 [**活動**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-111">Alternatively, you can click **Open Knowledge Base**, select **Suppliers** from the **list of knowledge bases**, select **Knowledge Discovery** as **activity** and click **Next**.</span></span>  
  
     <span data-ttu-id="ac3e5-112">![主頁面上的 [知識探索] 功能表](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "主頁面上的 [知識探索] 功能表")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-112">![Knowledge Discovery Menu on Main Page](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Knowledge Discovery Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="ac3e5-113">針對 [**資料來源**] 選取 [ **Excel**檔案]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-113">Select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="ac3e5-114">按一下 **[流覽]**，流覽並選取 [ **Suppliers.xls**]，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-114">Click **Browse**, navigate and select **Suppliers.xls**, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="ac3e5-115">針對 [**工作表**] 選取 [**探索供應商**]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-115">Select **Suppliers for Discovery** for **Worksheet**.</span></span>  
  
5.  <span data-ttu-id="ac3e5-116">**在 [對應] 區段中**，使用**下拉式清單**，將來自**Excel**檔案的 [供貨**商\*\*\*\*識別碼**]**資料行對應**至供貨**商名稱**網域。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-116">In the **Mappings** section, map **SupplierID** column from the **Excel** file to the **Supplier ID** domain and **Supplier Name** column to the **Supplier Name** domain by using **drop-down lists**.</span></span> <span data-ttu-id="ac3e5-117">Excel 檔案包含**供應商識別碼**和**供應商名稱**網域的範例資料。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-117">The Excel file has sample data for the **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="ac3e5-118">在探索程序中，您可以選取要探索值的定義域。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-118">In the discovery process, you can select the domains for which you want to discover the values.</span></span> <span data-ttu-id="ac3e5-119">您可以在此頁面建立定義域，然後將來源資料行對應到這些定義域。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-119">You can create domains on this page and then map the source columns to those domains.</span></span> <span data-ttu-id="ac3e5-120">在知識探索活動期間建立定義域是可能發生的狀況 (而不是在定義域管理活動期間建立定義域)。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-120">It is not uncommon to create domains during knowledge discovery activity instead of creating domains during domain management activity.</span></span>  
  
     <span data-ttu-id="ac3e5-121">![探索程序的 [對應] 頁面](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "探索程序的 [對應] 頁面")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-121">![Map Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Map Page of Discovery Process")</span></span>  
  
6.  <span data-ttu-id="ac3e5-122">按 **[下一步]** 切換至 [**探索**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-122">Click **Next** to switch to the **Discover** page.</span></span>  
  
7.  <span data-ttu-id="ac3e5-123">在 [**探索**] 頁面上，按一下 [**啟動**] 以啟動探索程式。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-123">On the **Discover** page, click **Start** to start the discovery process.</span></span> <span data-ttu-id="ac3e5-124">探索會針對**Suppliers.xls**檔案中的 [**資料行]** 、[廠商] 和 [**供應商名稱**] 執行。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-124">Discovery is performed on the columns **SupplierID** and **Supplier Name** in the **Suppliers.xls** file.</span></span> <span data-ttu-id="ac3e5-125">**供應商識別碼**和**供應商名稱**網域應該填入從探索所繪製的知識。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-125">The **Supplier ID** and **Supplier Name** domains should be populated with the knowledge drawn from the discovery.</span></span>  
  
     <span data-ttu-id="ac3e5-126">![探索程序的 [探索] 頁面](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "探索程序的 [探索] 頁面")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-126">![Discover Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Discover Page of Discovery Process")</span></span>  
  
8.  <span data-ttu-id="ac3e5-127">分析完成之後，請在頁面底部的 [分析工具 **]** 索引標籤中，查看**來源統計資料**。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-127">After the analysis has completed, review the **Source Statistics** in the **Profiler tab** at the bottom of the page.</span></span> <span data-ttu-id="ac3e5-128">請注意，從**Excel 工作表**) 探索到的10筆新記錄，總計20個值 (的「供貨**商**」和「**廠商名稱**」值。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-128">Notice that 10 new records with total 20 values (**SupplierID** and **Supplier Name** values from the **Excel worksheet**) were discovered.</span></span> <span data-ttu-id="ac3e5-129">您也會看到有多少新的值、唯一的值、新增且唯一的值及有效的值。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-129">You will also see how many of the values are new, unique, new and unique, and valid.</span></span> <span data-ttu-id="ac3e5-130">在右邊的清單方塊中，您可以查看與探索程序有關之每個定義域的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-130">In the list box to the right, you can see more details for each domain involved in the discovery process.</span></span> <span data-ttu-id="ac3e5-131">如果您將滑鼠停留在狀態列的 [完整性] 資料行上方，您可以看到資料行的來源是否有任何遺漏的值。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-131">If you hover the mouse over the status bar in the Completeness column, you can see if there are any missing values in the columns in the source.</span></span>  
  
     <span data-ttu-id="ac3e5-132">![知識探索結果](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "知識探索結果")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-132">![Knowledge Discovery Results](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Knowledge Discovery Results")</span></span>  
  
9. <span data-ttu-id="ac3e5-133">按 **[下一步]** 切換至 [**管理定義域值**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-133">Click **Next** to switch to the **Manage Domain Values** page.</span></span>  
  
10. <span data-ttu-id="ac3e5-134">在 [**管理定義域值**] 頁面中，按一下網域清單中的 [**供應商名稱**網域]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-134">In the **Manage Domain Values** page, click **Supplier Name** domain from the list of domains.</span></span>  
  
11. <span data-ttu-id="ac3e5-135">在右窗格中，以滑鼠右鍵按一下 [消極式**國家/地區 Storex** ] (在結尾) 看到 ' x '，然後選取 [ **Lazy country Store**]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-135">In the right pane, right-click **Lazy Country Storex** (notice 'x' at the end), and select **Lazy Country Store**.</span></span> <span data-ttu-id="ac3e5-136">在針對此定義域執行拼字檢查之後，DQS 會建議這項變更。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-136">DQS suggests this change after running the spell checker on the domain.</span></span> <span data-ttu-id="ac3e5-137">根據預設，您建立的定義域會啟用拼字檢查。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-137">By default, speller is enabled on the domains you create.</span></span>  
  
     <span data-ttu-id="ac3e5-138">![正確供應商名稱 - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "正確供應商名稱 - Lazy Country Store")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-138">![Correct Supplier Name - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Correct Supplier Name - Lazy Country Store")</span></span>  
  
12. <span data-ttu-id="ac3e5-139">在 [定義域值] 清單中，確認 [**延遲 Country Storex** ] 值已設定為錯誤 (紅色**X**標記) 加上 [**延遲國家/地區存放區**] 做為更正，同時也將 [**延遲國家/地區] 存放區**新增為有效的值。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-139">In the domain values list, confirm that the value **Lazy Country Storex** is set as an error (red **X** mark) with **Lazy Country Store** as the correction and also the **Lazy Country Store** is also added as a valid value.</span></span>  
  
     <span data-ttu-id="ac3e5-140">![定義域值和 [更正為] 值](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "定義域值和 [更正為] 值")</span><span class="sxs-lookup"><span data-stu-id="ac3e5-140">![Domain Value and Correct To Value](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domain Value and Correct To Value")</span></span>  
  
13. <span data-ttu-id="ac3e5-141">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-141">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="ac3e5-142">在**SQL Server Data Quality Services** ] 對話方塊上，按一下 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-142">On **SQL Server Data Quality Services** dialog box, click **Publish**.</span></span>  
  
15. <span data-ttu-id="ac3e5-143">按一下 [成功] 訊息方塊上的 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-143">Click **OK** on the success message box.</span></span>  
  
     <span data-ttu-id="ac3e5-144">您已經完成教學課程的第一課。</span><span class="sxs-lookup"><span data-stu-id="ac3e5-144">You have completed the first lesson of the tutorial.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ac3e5-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ac3e5-145">Next Step</span></span>  
 [<span data-ttu-id="ac3e5-146">第 2 課：使用供應商知識庫清理供應商資料</span><span class="sxs-lookup"><span data-stu-id="ac3e5-146">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
