---
title: 使用預測查詢產生器來建立預測查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13f39de4085cb74949e9540570d574c09e72ee27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592336"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a><span data-ttu-id="42637-102">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="42637-102">Create a Prediction Query Using the Prediction Query Builder</span></span>
  <span data-ttu-id="42637-103">您可以建立預測查詢，方法是當您在 BI Development Studio 中建立資料採礦方案時，或是在 SQL Server Management Studio 中以滑鼠右鍵按一下現有的採礦模型，然後選擇 [建立預測查詢]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="42637-103">You can create prediction queries either while you are building a data mining solution in BI Development Studio, or by right-clicking an existing mining model in SQL Server Management Studio, and then choosing the option, **Build Prediction Query**.</span></span>  
  
 <span data-ttu-id="42637-104">[預測查詢產生器]\*\*\*\* 有以下三個設計模式，您可以按一下左上角的圖示切換模式。</span><span class="sxs-lookup"><span data-stu-id="42637-104">The **Prediction Query Builder** has the following three design modes, which you can switch among by clicking the icons in the upper-left corner.</span></span>  
  
-   <span data-ttu-id="42637-105">**設計**</span><span class="sxs-lookup"><span data-stu-id="42637-105">**Design**</span></span>  
  
-   <span data-ttu-id="42637-106">**查詢**</span><span class="sxs-lookup"><span data-stu-id="42637-106">**Query**</span></span>  
  
-   <span data-ttu-id="42637-107">**結果**</span><span class="sxs-lookup"><span data-stu-id="42637-107">**Result**</span></span>  
  
 <span data-ttu-id="42637-108">**[設計]** 模式可讓您建立預測查詢，方式是選擇輸入資料、將資料對應到模型，然後將預測函數加入至使用方格所建立的陳述式中。</span><span class="sxs-lookup"><span data-stu-id="42637-108">**Design** mode lets you build a prediction query by choosing input data, mapping the data to the model, and then adding prediction functions into statements you build by using the grid.</span></span> <span data-ttu-id="42637-109">設計方格包含以下建置組塊：</span><span class="sxs-lookup"><span data-stu-id="42637-109">The design grid contains these building blocks:</span></span>  
  
 <span data-ttu-id="42637-110">**Source**</span><span class="sxs-lookup"><span data-stu-id="42637-110">**Source**</span></span>  
 <span data-ttu-id="42637-111">選擇新資料行的來源。</span><span class="sxs-lookup"><span data-stu-id="42637-111">Choose the source of the new column.</span></span> <span data-ttu-id="42637-112">您可以使用採礦模型中的資料行、資料來源檢視中包含的輸入資料表、預測函數或自訂運算式。</span><span class="sxs-lookup"><span data-stu-id="42637-112">You can use columns from the mining model, input tables included in the data source view, a prediction function, or a customized expression.</span></span>  
  
 <span data-ttu-id="42637-113">**欄位**</span><span class="sxs-lookup"><span data-stu-id="42637-113">**Field**</span></span>  
 <span data-ttu-id="42637-114">決定與 [來源]\*\*\*\* 資料行中之選取範圍相關聯的特定資料行或函數。</span><span class="sxs-lookup"><span data-stu-id="42637-114">Determines the specific column or function that is associated with the selection in the **Source** column.</span></span>  
  
 <span data-ttu-id="42637-115">**鋸齒**</span><span class="sxs-lookup"><span data-stu-id="42637-115">**Alias**</span></span>  
 <span data-ttu-id="42637-116">決定如何在結果集內命名資料行。</span><span class="sxs-lookup"><span data-stu-id="42637-116">Determines how the column is to be named in the result set.</span></span>  
  
 <span data-ttu-id="42637-117">**顯示**</span><span class="sxs-lookup"><span data-stu-id="42637-117">**Show**</span></span>  
 <span data-ttu-id="42637-118">決定 [來源]\*\*\*\* 資料行中的選取範圍是否顯示在結果中。</span><span class="sxs-lookup"><span data-stu-id="42637-118">Determines whether the selection in the **Source** column is displayed in the results.</span></span>  
  
 <span data-ttu-id="42637-119">**群組**</span><span class="sxs-lookup"><span data-stu-id="42637-119">**Group**</span></span>  
 <span data-ttu-id="42637-120">使用 [及/或]\*\*\*\* 資料行，以括號將運算式群組在一起。</span><span class="sxs-lookup"><span data-stu-id="42637-120">Works with the **And/Or** column to group expressions together by using parentheses.</span></span> <span data-ttu-id="42637-121">例如，(expr1 或 expr2) 及 expr3。</span><span class="sxs-lookup"><span data-stu-id="42637-121">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="42637-122">**和/或**</span><span class="sxs-lookup"><span data-stu-id="42637-122">**And/Or**</span></span>  
 <span data-ttu-id="42637-123">在查詢中建立邏輯。</span><span class="sxs-lookup"><span data-stu-id="42637-123">Creates logic in the query.</span></span> <span data-ttu-id="42637-124">例如，(expr1 或 expr2) 及 expr3。</span><span class="sxs-lookup"><span data-stu-id="42637-124">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="42637-125">**準則/引數**</span><span class="sxs-lookup"><span data-stu-id="42637-125">**Criteria/Argument**</span></span>  
 <span data-ttu-id="42637-126">指定適用於資料行的條件或使用者運算式。</span><span class="sxs-lookup"><span data-stu-id="42637-126">Specifies a condition or user expression that applies to the column.</span></span> <span data-ttu-id="42637-127">您可以將資料行從資料表拖曳至資料格。</span><span class="sxs-lookup"><span data-stu-id="42637-127">You can drag columns from the tables to the cell.</span></span>  
  
 <span data-ttu-id="42637-128">[查詢]\*\*\*\* 模式提供一個文字編輯器，可讓您直接存取資料採礦延伸模組 (DMX) 語言，連同輸入資料和模型資料行的檢視。</span><span class="sxs-lookup"><span data-stu-id="42637-128">**Query** mode provides a text editor that gives you direct access to the Data Mining Extensions (DMX) language, along with a view of the input data and model columns.</span></span> <span data-ttu-id="42637-129">當您選取 **[查詢]** 模式時，基本文字編輯器會取代您用來定義查詢的方格。</span><span class="sxs-lookup"><span data-stu-id="42637-129">When you select **Query** mode, the grid that you used to define the query is replaced by a basic text editor.</span></span> <span data-ttu-id="42637-130">您可以使用此編輯器來複製和儲存您所撰寫的查詢，或是從剪貼簿貼入現有 DMX 查詢中，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="42637-130">You can use this editor to copy and save queries you have composed, or to paste in existing DMX queries and from the Clipboard and run them.</span></span>  
  
 <span data-ttu-id="42637-131">**[結果]** 檢視會執行目前的查詢，並將結果顯示在方格中。</span><span class="sxs-lookup"><span data-stu-id="42637-131">**Result** view runs the current query and displays the results in a grid.</span></span> <span data-ttu-id="42637-132">如果基礎資料已變更而且您想要重新執行查詢，請按一下狀態上的 [執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="42637-132">If the underlying data has changed and you want to rerun the query, click the Play button in the status bar</span></span>  
  
 <span data-ttu-id="42637-133">您可以使用視覺工具與文字編輯器的組合來設計資料採礦查詢。</span><span class="sxs-lookup"><span data-stu-id="42637-133">You can design a data mining query by using a combination of the visual tools and the text editor.</span></span> <span data-ttu-id="42637-134">如果在文字編輯器中輸入查詢的變更，然後切換回 **[設計]** 檢視，則所有變更都會遺失，且查詢會還原為預測查詢產生器所建立的原始查詢。本主題會逐步引導您使用圖形化查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="42637-134">If you type changes to the query in the text editor and switch back to the **Design** view, all the changes are lost, and the query reverts to the original query created by Prediction Query Builder This topic walks you through use of the graphical query builder.</span></span>  
  
### <a name="to-create-a-prediction-query"></a><span data-ttu-id="42637-135">若要建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="42637-135">To create a prediction query</span></span>  
  
1.  <span data-ttu-id="42637-136">按一下資料採礦設計師中的 **[採礦模型預測]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="42637-136">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="42637-137">按一下 **[採礦模型]** 資料表上的 **[選取模型]** 。</span><span class="sxs-lookup"><span data-stu-id="42637-137">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="42637-138">**[選取採礦模型]** 對話方塊就會開啟，以顯示存在於目前專案中的所有採礦結構。</span><span class="sxs-lookup"><span data-stu-id="42637-138">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
3.  <span data-ttu-id="42637-139">選取您要建立預測的模型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="42637-139">Select the model on which you want to create a prediction, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="42637-140">在 [選取輸入資料表]\*\*\*\* 資料表中，按一下 [選取案例資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="42637-140">On the **Select Input Table(s)** table, click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="42637-141">此時會開啟 **[選取資料表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="42637-141">The **Select Table** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="42637-142">在 **[資料來源]** 清單中，選取包含要建立預測之資料的資料來源。</span><span class="sxs-lookup"><span data-stu-id="42637-142">In the **Data Source** list, select the data source that contains the data on which to create a prediction.</span></span>  
  
6.  <span data-ttu-id="42637-143">在 [資料表/檢視表名稱]\*\*\*\* 方塊中，選取包含要建立預測之資料的資料表，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="42637-143">In the **Table/View Name** box, select the table that contains the data on which to create a prediction, and then click **OK**.</span></span>  
  
     <span data-ttu-id="42637-144">選好輸入資料表之後，「預測查詢產生器」會根據資料行的名稱，在採礦模型和輸入資料表之間建立預設的對應。</span><span class="sxs-lookup"><span data-stu-id="42637-144">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="42637-145">若要刪除對應，請按一下以選取將 [採礦模型]\*\*\*\* 資料表中的資料行連結到 [選取輸入資料表]\*\*\*\* 資料表中之對應資料行的線條，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="42637-145">To delete a mapping, click to select the line that links the column in the **Mining Model** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span> <span data-ttu-id="42637-146">您也可以手動建立對應，方式是按一下 [選取輸入資料表]\*\*\*\* 資料表中的資料行，然後將它拖曳至 [採礦模型]\*\*\*\* 資料表中的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="42637-146">You can also manually create mappings by clicking a column in the **Select Input Table(s)** table and dragging it onto the corresponding column in the **Mining Model** table.</span></span>  
  
7.  <span data-ttu-id="42637-147">將下列三種類型資訊的任何結合加入至 [預測查詢產生器] 方格：</span><span class="sxs-lookup"><span data-stu-id="42637-147">Add any combination of the following three types of information to the Prediction Query Builder grid:</span></span>  
  
    -   <span data-ttu-id="42637-148">**[採礦模型]** 方塊中的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="42637-148">Predictable columns from the **Mining Model** box.</span></span>  
  
    -   <span data-ttu-id="42637-149">[選取輸入資料表]\*\*\*\* 方塊中輸入資料行的任何組合。</span><span class="sxs-lookup"><span data-stu-id="42637-149">Any combination of input columns from the **Select Input Table(s)** box.</span></span>  
  
    -   <span data-ttu-id="42637-150">預測函數</span><span class="sxs-lookup"><span data-stu-id="42637-150">Prediction functions</span></span>  
  
8.  <span data-ttu-id="42637-151">按一下 **[採礦模型預測]** 索引標籤之工具列上的第一個按鈕，然後選取 **[結果]** 來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="42637-151">Run the query by clicking the first button on the toolbar of the **Mining Model Prediction** tab, and then selecting **Result**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42637-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42637-152">See Also</span></span>  
 <span data-ttu-id="42637-153">[在資料採礦設計工具中建立單一查詢](create-a-singleton-query-in-the-data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="42637-153">[Create a Singleton Query in the Data Mining Designer](create-a-singleton-query-in-the-data-mining-designer.md) </span></span>  
 [<span data-ttu-id="42637-154">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="42637-154">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
