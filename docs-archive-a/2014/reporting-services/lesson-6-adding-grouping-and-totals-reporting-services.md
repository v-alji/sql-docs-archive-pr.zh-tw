---
title: 第 6 課：新增群組和總計 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b98798005a984edf00aff469d4c1b09aa2e34d98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606074"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a><span data-ttu-id="e7a8c-102">第 6 課：新增群組和總計 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e7a8c-102">Lesson 6: Adding Grouping and Totals (Reporting Services)</span></span>
  <span data-ttu-id="e7a8c-103">將群組和總計加入至報表以組織和摘要資料。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-103">Add grouping and totals to your report to organize and summarize your data.</span></span>  
  
 <span data-ttu-id="e7a8c-104">如需有關將執行總計加入至報表的詳細資訊，請參閱：[將總計加入至 Reporting Services (SSRS) 報表](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/)。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-104">For information about adding running totals to reports, see: [Adding totals to Reporting Services (SSRS) reports](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).</span></span>  
  
 <span data-ttu-id="e7a8c-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="e7a8c-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="e7a8c-106">若要將報表中的資料分組</span><span class="sxs-lookup"><span data-stu-id="e7a8c-106">To group data in a report</span></span>](#bkmk_groupdata)  
  
-   [<span data-ttu-id="e7a8c-107">若要將總計加入至報表</span><span class="sxs-lookup"><span data-stu-id="e7a8c-107">To add totals to a report</span></span>](#bkmk_addtotals)  
  
-   [<span data-ttu-id="e7a8c-108">在報表中加入每日總計</span><span class="sxs-lookup"><span data-stu-id="e7a8c-108">To add a daily total to a report</span></span>](#bkmk_adddailytotal)  
  
-   [<span data-ttu-id="e7a8c-109">若要將總計加入至報表</span><span class="sxs-lookup"><span data-stu-id="e7a8c-109">To add a grand total to a report</span></span>](#bkmk_addgrandtotal)  
  
-   [<span data-ttu-id="e7a8c-110">若要將報表發行至報表伺服器 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="e7a8c-110">To Publish the Report to the Report Server (Optional)</span></span>](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a><span data-ttu-id="e7a8c-111">若要將報表中的資料分組</span><span class="sxs-lookup"><span data-stu-id="e7a8c-111">To group data in a report</span></span>  
  
1.  <span data-ttu-id="e7a8c-112">按一下 **[設計]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="e7a8c-113">如果您看不到 [資料**列群組**] 窗格，請以滑鼠右鍵按一下設計介面，然後按一下 [**視圖**]，再按一下 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-113">If you do not see the **Row Groups** pane , right-click the design surface and click **view** and then click **Grouping**.</span></span>  
  
3.  <span data-ttu-id="e7a8c-114">將 `Date` 欄位從 [報表資料]\*\*\*\* 窗格拖曳到 [資料列群組]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-114">From the **Report Data** pane, drag the `Date` field to the **Row Groups** pane.</span></span> <span data-ttu-id="e7a8c-115">將它放在稱為 [(詳細資料)]\*\*\*\* 之資料列的上方。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-115">Place it above the row called **(Details)**.</span></span>  
  
     <span data-ttu-id="e7a8c-116">請注意，資料列控制代碼中現在具有一個用來顯示群組的方括號。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-116">Note that the row handle now has a bracket in it, to show a group.</span></span> <span data-ttu-id="e7a8c-117">資料表現在也具有兩個 [日期] 資料行 – 垂直虛線兩側各有一個。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-117">The table now also has two Date columns -- one on either side of a vertical dotted line.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  <span data-ttu-id="e7a8c-118">將 `Order` 欄位從 [報表資料]\*\*\*\* 窗格拖曳到 [資料列群組]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-118">From the **Report Data** pane, drag the `Order` field to the **Row Groups** pane.</span></span> <span data-ttu-id="e7a8c-119">將它放在 [日期] 下方和 [(詳細資料)]\*\*\*\* 上方。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-119">Place it below Date and above **(Details)**.</span></span>  
  
     <span data-ttu-id="e7a8c-120">請注意，資料列控制代碼中現在具有兩個方括號，用來顯示兩個群組。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-120">Note that the row handle now has two brackets in it, to show two groups.</span></span> <span data-ttu-id="e7a8c-121">資料表現在也有兩個數據 `Order` 行。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-121">The table now has two `Order` columns, too.</span></span>  
  
5.  <span data-ttu-id="e7a8c-122">刪除雙線**右側**的原始 [日期] 和 [訂單] 資料行。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-122">Delete the original Date and Order columns to the **right** of the double line.</span></span> <span data-ttu-id="e7a8c-123">這樣會移除這個個別記錄值，所以只有群組值會顯示。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-123">This removes this individual record values so that only the group value is displayed.</span></span> <span data-ttu-id="e7a8c-124">選取這兩個資料行的資料行控制代碼，並按一下滑鼠右鍵，然後按一下 [刪除資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-124">Select the column handles for the two columns, right-click and click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="e7a8c-125">![選取要刪除的資料行](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "選取要刪除的資料行")</span><span class="sxs-lookup"><span data-stu-id="e7a8c-125">![Select columns to delete](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Select columns to delete")</span></span>  
  
     <span data-ttu-id="e7a8c-126">您可以再次設定資料行標頭和日期的格式。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-126">You can format the column headers and date again.</span></span>  
  
6.  <span data-ttu-id="e7a8c-127">切換到 **[預覽]** 索引標籤預覽報表。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-127">Switch to the **Preview** tab to preview the report.</span></span> <span data-ttu-id="e7a8c-128">報表應看起來類似下圖：</span><span class="sxs-lookup"><span data-stu-id="e7a8c-128">It should look similar to the following illustration:</span></span>  
  
     <span data-ttu-id="e7a8c-129">![依照日期後依照訂單分組的資料表](../../2014/tutorials/media/rs-basictablegroupspreview.gif "依照日期後依照訂單分組的資料表")</span><span class="sxs-lookup"><span data-stu-id="e7a8c-129">![Table grouped by date and then order](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table grouped by date and then order")</span></span>  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a><span data-ttu-id="e7a8c-130">若要將總計加入至報表</span><span class="sxs-lookup"><span data-stu-id="e7a8c-130">To add totals to a report</span></span>  
  
1.  <span data-ttu-id="e7a8c-131">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-131">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="e7a8c-132">以滑鼠右鍵按一下含有 `[LineTotal]` 欄位的資料區資料格，然後按一下 [新增總計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-132">Right-click the data region cell that contains the field `[LineTotal]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="e7a8c-133">這樣會加入每筆訂單的總金額資料列。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-133">This adds a row with a sum of the dollar amount for each order.</span></span>  
  
3.  <span data-ttu-id="e7a8c-134">以滑鼠右鍵按一下含有 `[Qty]` 欄位的資料格，然後按一下 [新增總計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-134">Right-click the cell that contains the field `[Qty]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="e7a8c-135">這樣會在總計資料列中加入每筆訂單的總數量。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-135">This adds a sum of the quantity for each order to the totals row.</span></span>  
  
4.  <span data-ttu-id="e7a8c-136">在 `Sum[Qty]`左側的空白資料格中，輸入**訂單總額**標籤。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-136">In the empty cell to the left of `Sum[Qty]`, type the label "**Order Total"**.</span></span>  
  
5.  <span data-ttu-id="e7a8c-137">您也可以在總計資料列中加入背景色彩。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-137">You can add a background color to the totals row.</span></span> <span data-ttu-id="e7a8c-138">選取兩個總和資料格以及標籤資料格。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-138">Select the two sum cells and the label cell.</span></span>  
  
6.  <span data-ttu-id="e7a8c-139">在 **[格式]** 功能表上，依序按一下 **[背景色彩]**、 **[淺灰]** 和 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-139">On the **Format** menu, click **Background Color**, click **Light Gray**, and click **OK**.</span></span>  
  
     <span data-ttu-id="e7a8c-140">![設計檢視：具有訂單總計的基本資料表](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "設計檢視：具有訂單總計的基本資料表")</span><span class="sxs-lookup"><span data-stu-id="e7a8c-140">![Design view: Basic table with order total](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")</span></span>  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a><span data-ttu-id="e7a8c-141">若要在報表中加入每日總計</span><span class="sxs-lookup"><span data-stu-id="e7a8c-141">To add a daily total to a report</span></span>  
  
1.  <span data-ttu-id="e7a8c-142">以滑鼠右鍵按一下 [訂單] 資料格，並指向 [加入總計]\*\*\*\*，然後按一下 [之後]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-142">Right-click the Order cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="e7a8c-143">這會加入新的資料列，其中包含每日數量和金額的總和，以及 [訂單] 資料行中的「**總計**」標籤。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-143">This adds a new row containing sums of the quantity and dollar amount for each day, and the label "**Total**" in the Order column.</span></span>  
  
2.  <span data-ttu-id="e7a8c-144">在同一資料格的 **總計** 一詞之前，輸入 **每日** 一詞，使其讀為 **[每日總計]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-144">Type the word **Daily** before the word **Total** in the same cell, so it reads **Daily Total**.</span></span>  
  
3.  <span data-ttu-id="e7a8c-145">選取 **[每日總計]** 資料格、兩個 **[總和]** 資料格以及它們之間的空白資料格。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-145">Select the **Daily Total** cell, the two **Sum** cells and the empty cell between them.</span></span>  
  
4.  <span data-ttu-id="e7a8c-146">在 **[格式]** 功能表上，依序按一下 **[背景色彩]**、 **[橙色]** 和 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-146">On the **Format** menu, click **Background Color**, click **Orange**, and click **OK**.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a><span data-ttu-id="e7a8c-147">若要將總計加入至報表</span><span class="sxs-lookup"><span data-stu-id="e7a8c-147">To add a grand total to a report</span></span>  
  
1.  <span data-ttu-id="e7a8c-148">以滑鼠右鍵按一下 [日期] 資料格，並指向 [加入總計]\*\*\*\*，然後按一下 [之後]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-148">Right-click the Date cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="e7a8c-149">這會加入新的資料列，其中包含整份報表的數量和金額總和，以及資料行中的**總**標籤 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-149">This adds a new row containing sums of the quantity and dollar amount for the entire report, and the **Total** label in the `Date` column.</span></span>  
  
2.  <span data-ttu-id="e7a8c-150">在同一資料格的 **總計** 一詞之前，輸入 **全部** 一詞，使其讀為 **[全部總計]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-150">Type the word **Grand** before the word **Total** in the same cell, so it reads **Grand Total**.</span></span>  
  
3.  <span data-ttu-id="e7a8c-151">選取 **[全部總計]** 資料格、兩個 **[總和]** 資料格以及它們之間的空白資料格。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-151">Select the **Grand Total** cell, the two **Sum** cells and the empty cells between them.</span></span>  
  
4.  <span data-ttu-id="e7a8c-152">在 **[格式]** 功能表上，依序按一下 **[背景色彩]**、 **[淺藍]** 和 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-152">On the **Format** menu, click **Background Color**, click **Light Blue**, and click **OK**.</span></span>  
  
     <span data-ttu-id="e7a8c-153">![設計檢視：基本資料表中的總計](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "設計檢視：基本資料表中的總計")</span><span class="sxs-lookup"><span data-stu-id="e7a8c-153">![Design view: Grand total in basic table](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")</span></span>  
  
5.  <span data-ttu-id="e7a8c-154">按一下 [預覽]。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-154">Click Preview.</span></span>  
  
     <span data-ttu-id="e7a8c-155">最後一頁碼看起來可能如下：</span><span class="sxs-lookup"><span data-stu-id="e7a8c-155">The last page should look something like this:</span></span>  
  
     <span data-ttu-id="e7a8c-156">![預覽：具有總計的基本資料表](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "預覽：具有總計的基本資料表")</span><span class="sxs-lookup"><span data-stu-id="e7a8c-156">![Preview: Basic table with grand total](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")</span></span>  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a><span data-ttu-id="e7a8c-157">若要將報表發行至報表伺服器 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="e7a8c-157">To Publish the Report to the Report Server (Optional)</span></span>  
  
1.  <span data-ttu-id="e7a8c-158">選擇性步驟是將已完成的報表發行至原生模式報表伺服器，讓您能夠從報表管理員檢視報表。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-158">An optional step is to publish the completed report to the native mode report server so you can view the report from Report Manager.</span></span>  
  
2.  <span data-ttu-id="e7a8c-159">在工具列上，按一下 **[專案]** ，然後按一下 **[Tutorial 屬性]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-159">On the toolbar click **Project** and then click **tutorial Properties...**</span></span>  
  
3.  <span data-ttu-id="e7a8c-160">在**TargetServerURL**中，輸入報表伺服器名稱的名稱，例如**HTTP:// \<servername> /reportserver**</span><span class="sxs-lookup"><span data-stu-id="e7a8c-160">In the **TargetServerURL** type the name of the name of your report server, for example **http://\<servername>/reportserver**</span></span>  
  
4.  <span data-ttu-id="e7a8c-161">按一下 [檔案] &gt; [新增] &gt; [專案]</span><span class="sxs-lookup"><span data-stu-id="e7a8c-161">Click **OK**</span></span>  
  
5.  <span data-ttu-id="e7a8c-162">在工具列上，按一下 **[建置]** ，然後按一下 **[部署教學課程]**。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-162">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>  
  
     <span data-ttu-id="e7a8c-163">如果您在輸出視窗中看見類似下面的訊息，就表示部署成功。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-163">If you see a message similar to the following in the output window, it indicates a successful deployment.</span></span>  
  
    > <span data-ttu-id="e7a8c-164">------ 已經開始建立: 專案: 教學課程，組態: 偵錯 ------ 正在略過 'Sales Orders.rdl'。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-164">------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'.</span></span> <span data-ttu-id="e7a8c-165">專案是最新的。組建完成--0 個錯誤，0個警告------部署已開始：專案：教學課程，設定： Debug------部署至 HTTP:// \<server name> /reportserverDeploying 報表 '/Tutorial/Sales Orders '。部署完成--0 個錯誤，0個警告 = = = = = = = = = = 組建：1成功或最新、0失敗、0略過 = = = = = = = = = = = = = = = = = = = = = = 部署：1成功、0失敗、0略過 = = = = = = = = = =</span><span class="sxs-lookup"><span data-stu-id="e7a8c-165">Item is up to date.Build complete -- 0 errors, 0 warnings------ Deploy started: Project: tutorial, Configuration: Debug ------Deploying to http://\<server name>/reportserverDeploying report '/tutorial/Sales Orders'.Deploy complete -- 0 errors, 0 warnings========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==================== Deploy: 1 succeeded, 0 failed, 0 skipped ==========</span></span>  
  
     <span data-ttu-id="e7a8c-166">如果您看見類似下面的錯誤訊息，請確認自己擁有報表伺服器的權限，而且已經以系統管理員權限啟動 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-166">If you see an error message similar to the following, verify you have permissions on the report server and you have started [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] with administrator privileges.</span></span>  
  
    > <span data-ttu-id="e7a8c-167">「授與使用者 ' XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX 的許可權 \\<您的使用者名稱 \> ' 不足，無法執行此作業」</span><span class="sxs-lookup"><span data-stu-id="e7a8c-167">"The permissions granted to user 'XXXXXXXX\\<your user name\>' are insufficient for performing this operation"</span></span>  
  
6.  <span data-ttu-id="e7a8c-168">以系統管理員許可權啟動報表管理員，例如，以滑鼠右鍵按一下 Internet Explorer 的圖示，然後按一下 [以**系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-168">Start Report Manager with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>  
  
     <span data-ttu-id="e7a8c-169">瀏覽至報表管理員 URL，例如： `http://<server name>/reports`。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-169">Browse to the Report Manager URL, for example: `http://<server name>/reports`.</span></span>  
  
7.  <span data-ttu-id="e7a8c-170">瀏覽至包含報表的資料夾，然後按一下 `Sales Orders` 報表的名稱，即可在瀏覽器中檢視轉譯的報表。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-170">Browse to the folder that contains the report and click the name of the report `Sales Orders` to view the rendered report in the browser.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e7a8c-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e7a8c-171">Next Steps</span></span>  
 <span data-ttu-id="e7a8c-172">您已成功完成「建立基本資料表報表」教學課程。</span><span class="sxs-lookup"><span data-stu-id="e7a8c-172">You have successfully completed the Creating a Basic Table Report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a8c-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a8c-173">See Also</span></span>  
 [<span data-ttu-id="e7a8c-174">篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e7a8c-174">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
