---
title: " (基本資料採礦教學課程建立預測) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686568"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="d2460-102">建立預測 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="d2460-102">Creating Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="d2460-103">在測試過您的採礦模型的精確度並決定您對結果感到滿意之後，您就可以在資料採礦設計工具的 [**採礦模型預測**] 索引標籤上使用預測查詢產生器來產生預測。</span><span class="sxs-lookup"><span data-stu-id="d2460-103">After you have tested the accuracy of your mining models and decided that you are satisfied with the results, you can then generate predictions by using the Prediction Query Builder on the **Mining Model Prediction** tab in the Data Mining Designer.</span></span>  
  
 <span data-ttu-id="d2460-104">預測查詢產生器有三個檢視。</span><span class="sxs-lookup"><span data-stu-id="d2460-104">The Prediction Query Builder has three views.</span></span> <span data-ttu-id="d2460-105">您可以使用 [**設計**] 和 [**查詢**] 視圖來建立及檢查查詢。</span><span class="sxs-lookup"><span data-stu-id="d2460-105">With the **Design** and **Query** views, you can build and examine your query.</span></span> <span data-ttu-id="d2460-106">接著，您可以執行查詢，並在**結果**視圖中查看結果。</span><span class="sxs-lookup"><span data-stu-id="d2460-106">You can then run the query and view the results in the **Result** view.</span></span>  
  
 <span data-ttu-id="d2460-107">所有的預測查詢都是使用 DMX，也就是資料採礦延伸模組 (DMX) 語言的縮寫。</span><span class="sxs-lookup"><span data-stu-id="d2460-107">All prediction queries use DMX, which is short for the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="d2460-108">DMX 的語法與 T-SQL 的語法相似，但用於對資料採礦物件的查詢。</span><span class="sxs-lookup"><span data-stu-id="d2460-108">DMX has syntax like that of T-SQL but is used for queries against data mining objects.</span></span> <span data-ttu-id="d2460-109">雖然 DMX 語法並不複雜，但使用此類的查詢產生器或適用于 Office 的[SQL Server 資料採礦增益集](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)，可讓您更輕鬆地選取輸入和建立運算式，因此強烈建議您瞭解基本概念。</span><span class="sxs-lookup"><span data-stu-id="d2460-109">Although DMX syntax is not complicated, using a query builder like this one, or the one in the [SQL Server Data Mining Add-Ins for Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), makes it much easier to select inputs and build expressions, so we highly recommend that you learn the basics.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="d2460-110">建立查詢</span><span class="sxs-lookup"><span data-stu-id="d2460-110">Creating the Query</span></span>  
 <span data-ttu-id="d2460-111">建立預測查詢的第一個步驟是，選取採礦模型和輸入資料表。</span><span class="sxs-lookup"><span data-stu-id="d2460-111">The first step in creating a prediction query is to select a mining model and input table.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="d2460-112">若要選取模型和輸入資料表</span><span class="sxs-lookup"><span data-stu-id="d2460-112">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="d2460-113">在資料採礦設計師的 [**採礦模型預測**] 索引標籤上，按一下 [**採礦模型**] 方塊中的 [**選取模型**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-113">On the **Mining Model Prediction** tab of Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="d2460-114">在 [**選取模型**] 對話方塊中，流覽樹狀目錄至**目標郵寄**結構，展開結構，選取 `TM_Decision_Tree` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d2460-114">In the **Select Mining Model** dialog box, navigate through the tree to the **Targeted Mailing** structure, expand the structure, select `TM_Decision_Tree`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d2460-115">在 [**選取輸入資料表 (s) \*\* ] 方塊中，按一下 [**選取案例資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="d2460-115">In the **Select Input Table(s)** box, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="d2460-116">在 [**選取資料表**] 對話方塊的 [**資料來源**] 清單中，選取 [資料來源] 視圖 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d2460-116">In the **Select Table** dialog box, in the **Data Source** list, select the data source view [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
5.  <span data-ttu-id="d2460-117">在 [**資料表/視圖名稱**] 中，選取\*\*ProspectiveBuyer (dbo) \*\*資料表，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d2460-117">In **Table/View Name**, select the **ProspectiveBuyer (dbo)** table, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d2460-118">`ProspectiveBuyer`資料表最類似于**vTargetMail**案例資料表。</span><span class="sxs-lookup"><span data-stu-id="d2460-118">The `ProspectiveBuyer` table most closely resembles the **vTargetMail** case table.</span></span>  
  
## <a name="mapping-the-columns"></a><span data-ttu-id="d2460-119">對應資料行</span><span class="sxs-lookup"><span data-stu-id="d2460-119">Mapping the Columns</span></span>  
 <span data-ttu-id="d2460-120">選好輸入資料表之後，「預測查詢產生器」會根據資料行的名稱，在採礦模型和輸入資料表之間建立預設的對應。</span><span class="sxs-lookup"><span data-stu-id="d2460-120">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="d2460-121">此結構中至少必須有一個資料行符合外部資料中的資料行。</span><span class="sxs-lookup"><span data-stu-id="d2460-121">At least one column from the structure must match a column in the external data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2460-122">您用來判斷模型精確度的資料必須包含可對應至可預測資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="d2460-122">The data that you use to determine the accuracy of the models must contain a column that can be mapped to the predictable column.</span></span> <span data-ttu-id="d2460-123">如果這類資料行不存在，您可以建立包含空值的資料行，但是其資料類型必須與預測的資料行相同。</span><span class="sxs-lookup"><span data-stu-id="d2460-123">If such a column does not exist, you can create one with empty values, but it must have the same data type as the predictable column.</span></span>  
  
#### <a name="to-map-the-inputs-to-the-model"></a><span data-ttu-id="d2460-124">將輸入對應至模型</span><span class="sxs-lookup"><span data-stu-id="d2460-124">To map the inputs to the model</span></span>  
  
1.  <span data-ttu-id="d2460-125">以滑鼠右鍵按一下將 [**採礦模型**] 視窗連接到 [**選取輸入資料表**] 視窗的線條，然後選取 [**修改連接**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-125">Right-click the lines connecting the **Mining Model** window to the **Select Input Table** window, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="d2460-126">請注意，並非每一個資料行都會對應。</span><span class="sxs-lookup"><span data-stu-id="d2460-126">Notice that not every column is mapped.</span></span> <span data-ttu-id="d2460-127">我們會加入數個**資料表資料行**的對應。</span><span class="sxs-lookup"><span data-stu-id="d2460-127">We will add mappings for several **Table Columns**.</span></span> <span data-ttu-id="d2460-128">另外還會依據目前的日期資料行產生新的生日資料行，讓資料行更好比對。</span><span class="sxs-lookup"><span data-stu-id="d2460-128">We will also generate a new birth date column based on the current date column, so that the columns match better.</span></span>  
  
2.  <span data-ttu-id="d2460-129">在 [**資料表資料行**] 底下，按一下資料格， `Bike Buyer` 然後從下拉式清單中選取 [ProspectiveBuyer 未知]。</span><span class="sxs-lookup"><span data-stu-id="d2460-129">Under **Table Column**, click the `Bike Buyer` cell and select ProspectiveBuyer.Unknown from the dropdown.</span></span>  
  
     <span data-ttu-id="d2460-130">這會將可預測的資料行 [Bike Buyer] 對應到輸入資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="d2460-130">This maps the predictable column, [Bike Buyer], to an input table column.</span></span>  
  
3.  <span data-ttu-id="d2460-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d2460-131">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="d2460-132">在**方案總管**中，以滑鼠右鍵按一下 [**目標郵寄**資料來源] 視圖，然後選取 [**視圖設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="d2460-132">In **Solution Explorer**, right-click the **Targeted Mailing** data source view and select **View Designer**.</span></span>  
  
5.  <span data-ttu-id="d2460-133">以滑鼠右鍵按一下資料表 ProspectiveBuyer，然後選取 [**新增] [命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-133">Right-click the table, ProspectiveBuyer, and select **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="d2460-134">在 [**建立命名計算**] 對話方塊的 [資料**行名稱**] 中，輸入 `calcAge` 。</span><span class="sxs-lookup"><span data-stu-id="d2460-134">In the **Create Named Calculation** dialog box, for **Column name**, type `calcAge`.</span></span>  
  
7.  <span data-ttu-id="d2460-135">在 [**描述**] 中，輸入**根據出生日期計算存留期**。</span><span class="sxs-lookup"><span data-stu-id="d2460-135">For **Description**, type **Calculate age based on birthdate**.</span></span>  
  
8.  <span data-ttu-id="d2460-136">在 [**運算式**] 方塊中，輸入 `DATEDIFF(YYYY,[BirthDate],getdate())` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d2460-136">In the **Expression** box, type `DATEDIFF(YYYY,[BirthDate],getdate())` and then click **OK**.</span></span>  
  
     <span data-ttu-id="d2460-137">由於輸入資料表沒有對應到模型中的 [ **age** ] 資料行，因此您可以使用此運算式來計算輸入資料表中 [出生日期] 資料行的客戶年齡。</span><span class="sxs-lookup"><span data-stu-id="d2460-137">Because the input table has no **Age** column corresponding to the one in the model, you can use this expression to calculate customer age from the BirthDate column in the input table.</span></span> <span data-ttu-id="d2460-138">因為**年齡**已識別為預測自行車購買的最具影響力資料行，所以它必須同時存在於模型和輸入資料表中。</span><span class="sxs-lookup"><span data-stu-id="d2460-138">Since **Age** was identified as the most influential column for predicting bike buying, it must exist in both the model and in the input table.</span></span>  
  
9. <span data-ttu-id="d2460-139">在資料採礦設計工具中，選取 [**採礦模型預測**] 索引標籤，然後重新開啟 [**修改連接**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d2460-139">In Data Mining Designer, select the **Mining Model Prediction** tab and re-open the **Modify Connections** window.</span></span>  
  
10. <span data-ttu-id="d2460-140">在 [**資料表資料行**] 底下，按一下 [ **Age** ] 資料格，然後從下拉式清單中選取 [ProspectiveBuyer calcAge]。</span><span class="sxs-lookup"><span data-stu-id="d2460-140">Under **Table Column**, click the **Age** cell and select ProspectiveBuyer.calcAge from the dropdown.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="d2460-141">如果您未在清單中看見資料行，可能必須重新整理設計師中所載入資料來源檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="d2460-141">If you do not see the column in the list, you might have to refresh the definition of the data source view that is loaded in the designer.</span></span> <span data-ttu-id="d2460-142">若要這麼做，請**在 [檔案] 功能表中**選取 [**全部儲存**]，然後在設計工具中關閉並重新開啟專案。</span><span class="sxs-lookup"><span data-stu-id="d2460-142">To do this, from the **File** menu, select **Save all**, and then close and re-open the project in the designer.</span></span>  
  
11. <span data-ttu-id="d2460-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d2460-143">Click **OK**.</span></span>  
  
## <a name="designing-the-prediction-query"></a><span data-ttu-id="d2460-144">設計預測查詢</span><span class="sxs-lookup"><span data-stu-id="d2460-144">Designing the Prediction Query</span></span>  
  
1.  <span data-ttu-id="d2460-145">[**採礦模型預測**] 索引標籤工具列上的第一個按鈕是切換到 [**設計檢視]/[切換到結果檢視/切換至查詢檢視**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d2460-145">The first button on the toolbar of the **Mining Model Prediction** tab is the **Switch to design view / Switch to result view / Switch to query view** button.</span></span> <span data-ttu-id="d2460-146">按一下此按鈕上的向下箭號，然後選取 [**設計**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-146">Click the down arrow on this button, and select **Design**.</span></span>  
  
2.  <span data-ttu-id="d2460-147">在 [**採礦模型預測**] 索引標籤上的方格中，按一下 [**來源**] 資料行中第一個空白資料列內的資料格，然後選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-147">In the grid on the **Mining Model Prediction** tab, click the cell in the first empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
3.  <span data-ttu-id="d2460-148">在 [**預測函數**] 資料列的 [**欄位**] 資料行中，選取 [] `PredictProbability` 。</span><span class="sxs-lookup"><span data-stu-id="d2460-148">In the **Prediction Function** row, in the **Field** column, select `PredictProbability`.</span></span>  
  
     <span data-ttu-id="d2460-149">在相同資料列的 [**別名**] 資料行中，輸入**result 的**機率。</span><span class="sxs-lookup"><span data-stu-id="d2460-149">In the **Alias** column of the same row, type **Probability of result**.</span></span>  
  
4.  <span data-ttu-id="d2460-150">從上方的 [**採礦模型**] 視窗中，選取 [自行車買方]，並將其拖曳至 [**準則/引數**] 資料格中。</span><span class="sxs-lookup"><span data-stu-id="d2460-150">From the **Mining Model** window above, select and drag [Bike Buyer] into the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="d2460-151">當您讓 go 時，[TM_Decision_Tree]。[自行車購買者] 出現在 [**準則/引數**] 資料格中。</span><span class="sxs-lookup"><span data-stu-id="d2460-151">When you let go, [TM_Decision_Tree].[Bike Buyer] appears in the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="d2460-152">這會指定 `PredictProbability` 函數的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d2460-152">This specifies the target column for the `PredictProbability` function.</span></span> <span data-ttu-id="d2460-153">如需函式的詳細資訊，請參閱[資料採礦擴充功能 &#40;DMX&#41;](/sql/dmx/data-mining-extensions-dmx-function-reference)函式參考。</span><span class="sxs-lookup"><span data-stu-id="d2460-153">For more information about functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
5.  <span data-ttu-id="d2460-154">按一下 [**來源**] 資料行中的下一個空白資料列，然後選取 [ **TM_Decision_Tree**的採礦模型]。</span><span class="sxs-lookup"><span data-stu-id="d2460-154">Click the next empty row in the **Source** column, and then select **TM_Decision_Tree** mining model.</span></span>  
  
6.  <span data-ttu-id="d2460-155">在資料 `TM_Decision_Tree` 列的 [**欄位**] 資料行中，選取 [] `Bike Buyer` 。</span><span class="sxs-lookup"><span data-stu-id="d2460-155">In the `TM_Decision_Tree` row, in the **Field** column, select `Bike Buyer`.</span></span>  
  
7.  <span data-ttu-id="d2460-156">在資料 `TM_Decision_Tree` 列的 [**準則/引數**] 資料行中，輸入 `=1` 。</span><span class="sxs-lookup"><span data-stu-id="d2460-156">In the `TM_Decision_Tree` row, in the **Criteria/Argument** column, type `=1`.</span></span>  
  
8.  <span data-ttu-id="d2460-157">按一下 [**來源**] 資料行中的下一個空白資料列，然後選取 [ **ProspectiveBuyer 資料表**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-157">Click the next empty row in the **Source** column, and then select **ProspectiveBuyer table**.</span></span>  
  
9. <span data-ttu-id="d2460-158">在資料 `ProspectiveBuyer` 列的 [**欄位**] 資料行中，選取 [ **ProspectiveBuyerKey**]。</span><span class="sxs-lookup"><span data-stu-id="d2460-158">In the `ProspectiveBuyer` row, in the **Field** column, select **ProspectiveBuyerKey**.</span></span>  
  
     <span data-ttu-id="d2460-159">這會在預測查詢中加入唯一識別碼，供您辨識可能會購買和可能不會購買自行車的人。</span><span class="sxs-lookup"><span data-stu-id="d2460-159">This adds the unique identifier to the prediction query so that you can identify who is and who is not likely to buy a bicycle.</span></span>  
  
10. <span data-ttu-id="d2460-160">將其他五個資料列加入至方格中。</span><span class="sxs-lookup"><span data-stu-id="d2460-160">Add five more rows to the grid.</span></span> <span data-ttu-id="d2460-161">針對每個資料列，選取 [ **ProspectiveBuyer 資料表**] 做為**來源**，然後在**欄位**資料格中新增下列資料行：</span><span class="sxs-lookup"><span data-stu-id="d2460-161">For each row, select **ProspectiveBuyer table** as the **Source** and then add the following columns in the **Field** cells:</span></span>  
  
    -   <span data-ttu-id="d2460-162">calcAge</span><span class="sxs-lookup"><span data-stu-id="d2460-162">calcAge</span></span>  
  
    -   <span data-ttu-id="d2460-163">姓氏</span><span class="sxs-lookup"><span data-stu-id="d2460-163">LastName</span></span>  
  
    -   <span data-ttu-id="d2460-164">名字</span><span class="sxs-lookup"><span data-stu-id="d2460-164">FirstName</span></span>  
  
    -   <span data-ttu-id="d2460-165">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="d2460-165">AddressLine1</span></span>  
  
    -   <span data-ttu-id="d2460-166">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="d2460-166">AddressLine2</span></span>  
  
 <span data-ttu-id="d2460-167">最後，執行此查詢並瀏覽結果。</span><span class="sxs-lookup"><span data-stu-id="d2460-167">Finally, run the query and browse the results.</span></span>  
  
 <span data-ttu-id="d2460-168">**預測查詢**產生器也包含下列控制項：</span><span class="sxs-lookup"><span data-stu-id="d2460-168">The **Prediction Query Builder** also includes these controls:</span></span>  
  
-   <span data-ttu-id="d2460-169">**顯示**核取方塊</span><span class="sxs-lookup"><span data-stu-id="d2460-169">**Show** check box</span></span>  
  
     <span data-ttu-id="d2460-170">讓您可以移除查詢中的子句，而不必從設計師將其刪除。</span><span class="sxs-lookup"><span data-stu-id="d2460-170">Lets you remove clauses from the query without having to delete them from the designer.</span></span> <span data-ttu-id="d2460-171">當您使用複雜的查詢而想要保留語法時，這樣就不必複製 DMX 再貼入視窗，所以相當實用。</span><span class="sxs-lookup"><span data-stu-id="d2460-171">This can be useful when you are working with complex queries and want to preserve syntax without having to copy and paste DMX into the window.</span></span>  
  
-   <span data-ttu-id="d2460-172">**群組**</span><span class="sxs-lookup"><span data-stu-id="d2460-172">**Group**</span></span>  
  
     <span data-ttu-id="d2460-173">在所選該行的開頭插入左括號，或在目前該行的結尾插入右括號。</span><span class="sxs-lookup"><span data-stu-id="d2460-173">Inserts an opening (left) parentheses at the beginning of the selected line, or inserts a closing (right) parenthesis at the end of the current line.</span></span>  
  
-   <span data-ttu-id="d2460-174">**和/或**</span><span class="sxs-lookup"><span data-stu-id="d2460-174">**AND/OR**</span></span>  
  
     <span data-ttu-id="d2460-175">在目前的函數或資料行的正後方插入 `AND` 運算子或 `OR` 運算子。</span><span class="sxs-lookup"><span data-stu-id="d2460-175">Inserts the  `AND` operator or the `OR` operator immediately after the current function or column.</span></span>  
  
#### <a name="to-run-the-query-and-view-results"></a><span data-ttu-id="d2460-176">若要執行查詢並檢視結果</span><span class="sxs-lookup"><span data-stu-id="d2460-176">To run the query and view results</span></span>  
  
1.  <span data-ttu-id="d2460-177">在 [**採礦模型預測**] 索引標籤中，選取 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d2460-177">In the **Mining Model Prediction** tab, select the **Result** button.</span></span>  
  
2.  <span data-ttu-id="d2460-178">當執行此查詢並顯示結果之後，您可以檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="d2460-178">After the query runs and the results are displayed, you can review the results.</span></span>  
  
     <span data-ttu-id="d2460-179">[**採礦模型預測**] 索引標籤會顯示可能是自行車購買者之潛在客戶的連絡人資訊。</span><span class="sxs-lookup"><span data-stu-id="d2460-179">The **Mining Model Prediction** tab displays contact information for potential customers who are likely to be bike buyers.</span></span> <span data-ttu-id="d2460-180">[**結果的**機率] 資料行指出預測正確的機率。</span><span class="sxs-lookup"><span data-stu-id="d2460-180">The **Probability of result** column indicates the probability of the prediction being correct.</span></span> <span data-ttu-id="d2460-181">您可以利用這些結果來判斷哪些潛在的客戶應該成為郵寄目標。</span><span class="sxs-lookup"><span data-stu-id="d2460-181">You can use these results to determine which potential customers to target for the mailing.</span></span>  
  
3.  <span data-ttu-id="d2460-182">此時，您可以儲存結果。</span><span class="sxs-lookup"><span data-stu-id="d2460-182">At this point, you can save the results.</span></span> <span data-ttu-id="d2460-183">您有三個選項：</span><span class="sxs-lookup"><span data-stu-id="d2460-183">You have three options:</span></span>  
  
    -   <span data-ttu-id="d2460-184">以滑鼠右鍵按一下結果中的資料列，然後選取 [**複製**]，只儲存該值 (而 [欄標題]) 至 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="d2460-184">Right-click a row of data in the results, and select **Copy** to save just that value (and the column heading) to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="d2460-185">以滑鼠右鍵按一下結果中的任何資料列，然後選取 [**全部複製**]，將整個結果集（包括資料行標題）複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="d2460-185">Right-click any row in the results, and select **Copy All** to copy the entire result set, including column headings, to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="d2460-186">按一下 [**儲存查詢結果**]，將結果直接儲存到資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d2460-186">Click **Save query result** to save the results directly to a database as follows:</span></span>  
  
        1.  <span data-ttu-id="d2460-187">在 [**儲存資料採礦查詢結果**] 對話方塊中，選取資料來源，或定義新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d2460-187">In the **Save Data Mining Query Result** dialog box, select a data source, or define a new data source.</span></span>  
  
        2.  <span data-ttu-id="d2460-188">輸入將包含查詢結果之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2460-188">Type a name for the table that will contain the query results.</span></span>  
  
        3.  <span data-ttu-id="d2460-189">使用 [**加入至 DSV**] 選項來建立資料表，並將它加入至現有的資料來源 view。</span><span class="sxs-lookup"><span data-stu-id="d2460-189">Use the option, **Add to DSV**, to create the table and add it to an existing data source view.</span></span> <span data-ttu-id="d2460-190">如果您想要在相同的資料來源視圖中保留模型的所有相關資料表（例如定型資料、預測來源資料和查詢結果），這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d2460-190">This is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source view.</span></span>  
  
        4.  <span data-ttu-id="d2460-191">使用 [**如果存在則覆寫**] 選項，以使用最新的結果來更新現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="d2460-191">Use the option, **Overwrite if exists**, to update an existing table with the latest results.</span></span>  
  
             <span data-ttu-id="d2460-192">如果您已將任何資料行加入至預測查詢、變更預測查詢中任何資料行的名稱或資料類型，或者已針對目的地資料表執行任何 ALTER 陳述式，就必須使用此選項來覆寫資料表。</span><span class="sxs-lookup"><span data-stu-id="d2460-192">You must use the option to overwrite the table if you have added any columns to the prediction query, changed the names or data types of any columns in the prediction query, or if you have run any ALTER statements on the destination table.</span></span>  
  
             <span data-ttu-id="d2460-193">此外，如果多個資料行具有相同的名稱 (例如，預設資料行名稱**運算式**) 您必須為名稱重複的資料行建立別名，否則當設計工具嘗試將結果儲存至 SQL Server 時，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2460-193">Also, if multiple columns have the same name (for example, the default column name **Expression**) you must create an alias for the columns with duplicate names, or an error will be raised when the designer tries to save the results to SQL Server.</span></span> <span data-ttu-id="d2460-194">原因是 SQL Server 不允許多個資料行具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2460-194">The reason is that SQL Server does not allow multiple columns to have the same name.</span></span>  
  
             <span data-ttu-id="d2460-195">如需詳細資訊，請參閱 &#40;的 [ [&#41;的模型預測視圖儲存資料採礦查詢結果] 對話方塊](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d2460-195">For more information, see [Save Data Mining Query Result Dialog Box &#40;Mining Model Prediction View&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d2460-196">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="d2460-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d2460-197">在結構資料上使用鑽取 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="d2460-197">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2460-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2460-198">See Also</span></span>  
 [<span data-ttu-id="d2460-199">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="d2460-199">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
