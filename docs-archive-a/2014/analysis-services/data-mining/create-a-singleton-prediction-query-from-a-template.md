---
title: 從範本建立單一預測查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80e853875cce349dd8623fab3c30f1ad09bfbf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592335"
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a><span data-ttu-id="e559b-102">根據範本建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="e559b-102">Create a Singleton Prediction Query from a Template</span></span>
  <span data-ttu-id="e559b-103">當您有想要用於預測的模型，但不想要將它對應至外部輸入資料集或進行大量預測時，單一查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="e559b-103">A singleton query is useful when you have a model that you want to use for prediction, but don't want to map it to an external input data set or make bulk predictions.</span></span> <span data-ttu-id="e559b-104">使用單一查詢，您可以向模型提供一個或多個值，並且立即會看到預測值。</span><span class="sxs-lookup"><span data-stu-id="e559b-104">With a singleton query, you can provide a value or values to the model and instantly see the predicted value.</span></span>  
  
 <span data-ttu-id="e559b-105">例如，下列 DMX 查詢表示針對目標郵寄模型 TM_Decision_Tree 的單一查詢。</span><span class="sxs-lookup"><span data-stu-id="e559b-105">For example, the following DMX query represents a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="e559b-106">下列程序描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的範本總管來快速建立此查詢。</span><span class="sxs-lookup"><span data-stu-id="e559b-106">The procedure that follows describes how to use the Template Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to quickly create this query.</span></span>  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a><span data-ttu-id="e559b-107">在 SQL Server Management Studio 中開啟 Analysis Services 範本</span><span class="sxs-lookup"><span data-stu-id="e559b-107">To open the Analysis Services templates in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e559b-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。</span><span class="sxs-lookup"><span data-stu-id="e559b-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="e559b-109">按一下 Cube 圖示，即可開啟 [Analysis Server]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="e559b-109">Click the cube icon to open the **Analysis Server**templates.</span></span>  
  
### <a name="to-open-a-prediction-query-template"></a><span data-ttu-id="e559b-110">開啟預測查詢範本</span><span class="sxs-lookup"><span data-stu-id="e559b-110">To open a prediction query template</span></span>  
  
1.  <span data-ttu-id="e559b-111">在**範本總管**中，於 Analysis Server 範本的清單內，展開 [DMX]\*\*\*\*，然後展開 [預測查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e559b-111">In **Template Explorer**, in the list of Analysis Server templates, expand **DMX**, and thenexpand **Prediction Queries**.</span></span>  
  
2.  <span data-ttu-id="e559b-112">按兩下 [單一預測]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e559b-112">Double-click **Singleton Prediction**.</span></span>  
  
3.  <span data-ttu-id="e559b-113">在 [連接到 Analysis Services]\*\*\*\* 對話方塊中，輸入具有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體 (包含即將進行查詢的採礦模型) 的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="e559b-113">In the **Connect to Analysis Services** dialog box, type the name of the server that has the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining model to be queried.</span></span>  
  
4.  <span data-ttu-id="e559b-114">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="e559b-114">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="e559b-115">此範本會在指定的資料庫中開啟，並提供採礦模型物件瀏覽器，其中包含資料採礦函數和資料採礦結構與相關模型的清單。</span><span class="sxs-lookup"><span data-stu-id="e559b-115">The template opens in the specified database, together with a mining model Object Browser that contains data mining functions and a list of data mining structures and related models.</span></span>  
  
### <a name="to-customize-the-singleton-query-template"></a><span data-ttu-id="e559b-116">自訂單一查詢範本</span><span class="sxs-lookup"><span data-stu-id="e559b-116">To customize the singleton query template</span></span>  
  
1.  <span data-ttu-id="e559b-117">在此範本中，按一下 [可用的資料庫]\*\*\*\* 下拉式清單，然後從清單中選取 Analysis Service 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e559b-117">In the template, click the **Available Databases** drop-down list, and then select an instance of Analysis Service from the list.</span></span>  
  
2.  <span data-ttu-id="e559b-118">在 [採礦模型]\*\*\*\* 清單中，選取您想要查詢的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e559b-118">In the **Mining Model** list, select the mining model that you want to query.</span></span>  
  
     <span data-ttu-id="e559b-119">採礦模型中的資料行清單會顯示在物件瀏覽器的 [中繼資料]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e559b-119">The list of columns in the mining model appears in the **Metadata** pane of the object browser.</span></span>  
  
3.  <span data-ttu-id="e559b-120">在 [查詢]\*\*\*\* 功能表上，選取 [指定範本參數的值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e559b-120">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="e559b-121">在 [選取清單]\*\*\*\* 資料列中，輸入 \* 以便傳回所有資料行，或輸入資料行和運算式的逗號分隔清單以便傳回特定的資料行。</span><span class="sxs-lookup"><span data-stu-id="e559b-121">In the **select list** row, type \* to return all columns, or type a comma-delimited list of columns and expressions to return specific columns.</span></span>  
  
     <span data-ttu-id="e559b-122">如果您輸入 \*，就會傳回可預測資料行，以及您在步驟 6 中提供新值的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="e559b-122">If you type \*, the predictable column is returned, together with any columns for which you provide new values for in step 6.</span></span>  
  
     <span data-ttu-id="e559b-123">若為本主題開頭所顯示的範例程式碼，[選取清單]\*\*\*\* 資料列設定為 \*。</span><span class="sxs-lookup"><span data-stu-id="e559b-123">For the sample code shown at the start of this topic, the **select list** row was set to \*.</span></span>  
  
5.  <span data-ttu-id="e559b-124">在 [採礦模型]\*\*\*\* 資料列中，根據**物件總管**中顯示的採礦模型清單，輸入採礦模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="e559b-124">In the **mining model** row, type the name of the mining model from among the list of mining models that appear in **Object Explorer**.</span></span>  
  
     <span data-ttu-id="e559b-125">針對本主題開頭所顯示的範例程式碼，已將 [**採礦模型**] 資料列設定為 [名稱] `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="e559b-125">For the sample code shown at the start of this topic, the **mining model** row was set to the name, `TM_Decision_Tree`.</span></span>  
  
6.  <span data-ttu-id="e559b-126">在 [值]\*\*\*\* 資料列中，針對您想要進行預測的項目輸入新資料值。</span><span class="sxs-lookup"><span data-stu-id="e559b-126">In the **value** row, type the new data value for which you want to make a prediction.</span></span>  
  
     <span data-ttu-id="e559b-127">針對本主題開頭所顯示的範例程式碼，[**值**] 資料列設定為， `2` 以根據家中子女的數目來預測自行車購買行為。</span><span class="sxs-lookup"><span data-stu-id="e559b-127">For the sample code shown at the start of this topic, the **value** row was set to `2` to predict bike buying behavior based on the number of children at home.</span></span>  
  
7.  <span data-ttu-id="e559b-128">在 [資料行]\*\*\*\* 資料列中，輸入新資料應該對應至採礦模型中的目標資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e559b-128">In the **column** row, type the name of the column in the mining model to which the new data should be mapped.</span></span>  
  
     <span data-ttu-id="e559b-129">針對本主題開頭所顯示的範例程式碼，資料行資料**列**已設定為 `Number Children at Home` 。</span><span class="sxs-lookup"><span data-stu-id="e559b-129">For the sample code shown at the start of this topic, the **column** row was set to `Number Children at Home`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e559b-130">當您使用 [指定範本參數的值]\*\*\*\* 對話方塊時，不需要在資料行名稱前後加上方括號。</span><span class="sxs-lookup"><span data-stu-id="e559b-130">When you use the **Specify Values for Template Parameters** dialog box, you do not have to add square brackets around the column name.</span></span> <span data-ttu-id="e559b-131">系統會自動為您加入括號。</span><span class="sxs-lookup"><span data-stu-id="e559b-131">The brackets will automatically be added for you.</span></span>  
  
8.  <span data-ttu-id="e559b-132">將 [**輸入別名**] 保留為 `t` 。</span><span class="sxs-lookup"><span data-stu-id="e559b-132">Leave the **input alias** as `t`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="e559b-133">在查詢文字窗格中，尋找逗號和省略符號底下的紅色不規則曲線，表示語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="e559b-133">In the query text pane, find the red squiggle under the comma and ellipsis that indicates a syntax error.</span></span> <span data-ttu-id="e559b-134">請刪除省略符號，然後加入所需的任何其他查詢條件。</span><span class="sxs-lookup"><span data-stu-id="e559b-134">Delete the ellipsis, and add any additional query condition that you want.</span></span> <span data-ttu-id="e559b-135">如果您沒有加入任何其他條件，請刪除逗號。</span><span class="sxs-lookup"><span data-stu-id="e559b-135">If you do not add any other conditions, delete the comma.</span></span>  
  
     <span data-ttu-id="e559b-136">若為本主題開頭所顯示的範例程式碼，其他查詢條件設定為 `'45' as [Age]`。</span><span class="sxs-lookup"><span data-stu-id="e559b-136">For the sample code shown at the start of this topic, the additional query condition was set to `'45' as [Age]`.</span></span>  
  
11. <span data-ttu-id="e559b-137">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e559b-137">Click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e559b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e559b-138">See Also</span></span>  
 [<span data-ttu-id="e559b-139">建立預測 &#40;資料採礦基本教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="e559b-139">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
  
