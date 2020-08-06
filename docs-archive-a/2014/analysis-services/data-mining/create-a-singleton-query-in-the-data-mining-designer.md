---
title: 在資料採礦設計工具中建立單一查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton queries [Analysis Services]
- Mining Model Prediction [Analysis Services], singleton queries
ms.assetid: 6cdca8a0-cf16-46eb-a652-0bff820625ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07491924dbcf0bd35d049e6a7c290d49becfb45d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592334"
---
# <a name="create-a-singleton-query-in-the-data-mining-designer"></a><span data-ttu-id="97f9e-102">在資料採礦設計師中建立單一查詢</span><span class="sxs-lookup"><span data-stu-id="97f9e-102">Create a Singleton Query in the Data Mining Designer</span></span>
  <span data-ttu-id="97f9e-103">如果您想要針對單一案例建立預測，單一查詢便很有用。</span><span class="sxs-lookup"><span data-stu-id="97f9e-103">A singleton query is useful if you want to create a prediction for a single case.</span></span> <span data-ttu-id="97f9e-104">如需單一查詢的詳細資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="97f9e-104">For more information about singleton queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="97f9e-105">在資料採礦設計師的 [採礦模型預測]\*\*\*\* 索引標籤中，您可以建立許多不同類型的查詢。</span><span class="sxs-lookup"><span data-stu-id="97f9e-105">In the **Mining Model Prediction** tab of Data Mining Designer, you can create many different types of queries.</span></span> <span data-ttu-id="97f9e-106">您可以使用此設計師或輸入資料採礦延伸模組 (DMX) 陳述式，藉以建立查詢。</span><span class="sxs-lookup"><span data-stu-id="97f9e-106">You can create a query by using the designer, or by typing Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="97f9e-107">此外，您也可以從設計師開始，然後透過變更 DMX 陳述式或加入 WHERE 或 ORDER BY 子句，修改它所建立的查詢。</span><span class="sxs-lookup"><span data-stu-id="97f9e-107">You can also start with the designer and modify the query that it creates by changing the DMX statements, or by adding a WHERE or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="97f9e-108">若要在查詢設計檢視與查詢文字檢視之間切換，請按一下工具列上的第一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="97f9e-108">To switch between the query design view and the query text view, click the first button on the toolbar.</span></span> <span data-ttu-id="97f9e-109">您在查詢文字檢視中時，可以檢視預測查詢產生器所建立的 DMX 程式碼。</span><span class="sxs-lookup"><span data-stu-id="97f9e-109">When you are in the query text view, you can view the DMX code that Prediction Query Builder creates.</span></span> <span data-ttu-id="97f9e-110">您也可以執行查詢、修改查詢，以及執行修改過的查詢。</span><span class="sxs-lookup"><span data-stu-id="97f9e-110">You can also run the query, modify the query, and run the modified query.</span></span> <span data-ttu-id="97f9e-111">不過，您若切換回查詢設計檢視，修改過的查詢並不會保存。</span><span class="sxs-lookup"><span data-stu-id="97f9e-111">However, the modified query is not persisted if you switch back to the query design view.</span></span>  
  
 <span data-ttu-id="97f9e-112">下列程式碼顯示針對目標郵寄模型 TM_Decision_Tree 進行單一查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="97f9e-112">The following code shows an example of a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT [Bike Buyer], PredictProbability([Bike Buyer]) as ProbableBuyer  
FROM [TM_Decision_Tree]  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="97f9e-113">下列步驟將說明如何建立此預測查詢。</span><span class="sxs-lookup"><span data-stu-id="97f9e-113">The following steps explain how to create this prediction query.</span></span>  
  
### <a name="to-create-a-singleton-query-by-using-the-data-mining-designer"></a><span data-ttu-id="97f9e-114">使用資料採礦設計師來建立單一查詢</span><span class="sxs-lookup"><span data-stu-id="97f9e-114">To create a singleton query by using the Data Mining Designer</span></span>  
  
1.  <span data-ttu-id="97f9e-115">按一下資料採礦設計師中的 **[採礦模型預測]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="97f9e-115">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="97f9e-116">按一下 **[採礦模型]** 資料表上的 **[選取模型]** 。</span><span class="sxs-lookup"><span data-stu-id="97f9e-116">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="97f9e-117">**[選取採礦模型]** 對話方塊就會開啟，以顯示存在於目前專案中的所有採礦結構。</span><span class="sxs-lookup"><span data-stu-id="97f9e-117">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
     <span data-ttu-id="97f9e-118">選取您想要用來建立預測的模型。</span><span class="sxs-lookup"><span data-stu-id="97f9e-118">Select the model that you want to use for creating a prediction.</span></span>  
  
     <span data-ttu-id="97f9e-119">例如，若要建立本主題開頭所顯示的範例程式碼，請選取 TM_Decision_Tree，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f9e-119">For example, to create the sample code shown at the start of this topic, select TM_Decision_Tree, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="97f9e-120">在 [採礦模型預測]\*\*\*\* 索引標籤的工具列上，按一下 [單一查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f9e-120">Click **Singleton query** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="97f9e-121">[單一查詢輸入]\*\*\*\* 資料表就會出現在索引標籤上，其中的資料行會自動對應到 [採礦模型]\*\*\*\* 資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="97f9e-121">The **Singleton Query Input** table appears on the tab, with the columns automatically mapped to the columns in the **Mining Model** table.</span></span>  
  
4.  <span data-ttu-id="97f9e-122">在 [單一查詢輸入]\*\*\*\* 資料表上，選取 [值]\*\*\*\* 資料行中的值來描述您要建立預測的案例。</span><span class="sxs-lookup"><span data-stu-id="97f9e-122">On the **Singleton Query Input** table, select values in the **Value** column to describe the case for which you want to create a prediction.</span></span>  
  
     <span data-ttu-id="97f9e-123">例如，針對 [在家中的**數位子**系] 選取 [ **2** ]，然後 `45` 針對 [ **Age**] 輸入。</span><span class="sxs-lookup"><span data-stu-id="97f9e-123">For example, select **2** for **Number Children At Home**, and then type `45` for **Age**.</span></span>  
  
5.  <span data-ttu-id="97f9e-124">將可預測資料行從 [**採礦模型**] 資料表拖曳到索引標籤底部的 [**源**資料行]。您也可以選擇輸入資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="97f9e-124">Drag a predictable column from the **Mining Model** table to the **Source** column at the bottom of the tab. Optionally, you can type an alias for the column.</span></span>  
  
     <span data-ttu-id="97f9e-125">例如，將 [Bike Buyer]\*\*\*\* 拖曳至 [來源]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="97f9e-125">For example, drag **Bike Buyer** to the **Source** column.</span></span>  
  
6.  <span data-ttu-id="97f9e-126">從 [來源]\*\*\*\* 資料行的下拉式清單中，選取 [預測函數]\*\*\*\* 或 [自訂運算式]\*\*\*\*，將其他功能加入至查詢中。</span><span class="sxs-lookup"><span data-stu-id="97f9e-126">Add any additional functions to the query by selecting **Prediction Function** or **Custom Expression** from the drop-down list in the **Source** column.</span></span>  
  
     <span data-ttu-id="97f9e-127">例如，按一下 [預測函數]\*\*\*\*，然後選取 [PredictProbability]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f9e-127">For example, click **Prediction Function**, and select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="97f9e-128">按一下 [PredictProbability]\*\*\*\* 資料列中的 [準則/引數]\*\*\*\*，然後輸入要預測的資料行名稱，並選擇性地輸入要預測的特定值。</span><span class="sxs-lookup"><span data-stu-id="97f9e-128">Click **Criteria/Argument** in the **PredictProbability** row, and type the name of the column to predict, and optionally a specific value to predict.</span></span>  
  
     <span data-ttu-id="97f9e-129">例如，輸入 `[Bike Buyer], 1`。</span><span class="sxs-lookup"><span data-stu-id="97f9e-129">For example, type `[Bike Buyer], 1`.</span></span>  
  
8.  <span data-ttu-id="97f9e-130">按一下 [PredictProbability]\*\*\*\* 資料列中的 [別名]\*\*\*\* 方塊，然後輸入代表新資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="97f9e-130">Click the **Alias** box in the **PredictProbability** row, and type a name to refer to the new column.</span></span>  
  
     <span data-ttu-id="97f9e-131">例如，輸入 `ProbableBuyer`。</span><span class="sxs-lookup"><span data-stu-id="97f9e-131">For example, type `ProbableBuyer`.</span></span>  
  
9. <span data-ttu-id="97f9e-132">在 [採礦模型預測]\*\*\*\* 索引標籤的工具列上，按一下 [切換到查詢結果檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f9e-132">Click **Switch to query result view** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="97f9e-133">這時會開啟新的畫面，以顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="97f9e-133">A new screen opens to show the result of the query.</span></span> <span data-ttu-id="97f9e-134">若要檢視您剛建立的 DMX 陳述式，請按一下 [SQL]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97f9e-134">To view the DMX statement that you just created, click **SQL**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f9e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f9e-135">See Also</span></span>  
 [<span data-ttu-id="97f9e-136">預測查詢 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="97f9e-136">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
