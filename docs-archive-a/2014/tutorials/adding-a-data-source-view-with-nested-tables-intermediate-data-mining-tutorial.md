---
title: 使用嵌套資料表加入資料來源視圖 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: da1a9bff093e0b59e9d1166554d95bcf61aded08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704506"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a><span data-ttu-id="b40c4-102">加入具有巢狀資料表的資料來源檢視 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="b40c4-102">Adding a Data Source View with Nested Tables (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="b40c4-103">若要建立購物籃模型，您必須使用支援關聯資料的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="b40c4-103">To create a market basket model, you must use a data source view that supports associative data.</span></span> <span data-ttu-id="b40c4-104">此資料來源檢視也會用於時序群集狀況。</span><span class="sxs-lookup"><span data-stu-id="b40c4-104">This data source view will also be used for the sequence clustering scenario.</span></span>  
  
 <span data-ttu-id="b40c4-105">此資料來源視圖與您可能已使用的其他人不同，因為它包含一個*嵌套的資料表*。</span><span class="sxs-lookup"><span data-stu-id="b40c4-105">This data source view is different from others that you may have worked with because it contains a *nested table*.</span></span> <span data-ttu-id="b40c4-106">「*嵌套資料表*」是一個資料表，其中包含有關案例資料表中單一資料列的多個資料列資訊。</span><span class="sxs-lookup"><span data-stu-id="b40c4-106">A *nested table* is a table that contains multiple rows of information about a single row in the case table.</span></span> <span data-ttu-id="b40c4-107">例如，如果您的模型分析客戶的購買行為，您通常會將每一個客戶具有唯一資料列的資料表做為案例資料表使用。</span><span class="sxs-lookup"><span data-stu-id="b40c4-107">For example, if your model analyzes the purchasing behavior of customers, you would typically use a table that has a unique row for each customer as the case table.</span></span> <span data-ttu-id="b40c4-108">不過，每個客戶可能都會購買多個項目，而您可能想要分析購買的順序，或是通常會一起購買的產品。</span><span class="sxs-lookup"><span data-stu-id="b40c4-108">However, each customer might make multiple purchases, and you might want to analyze the sequence of purchases, or products that are frequently purchased together.</span></span> <span data-ttu-id="b40c4-109">若要以邏輯方式在模型中表示這些購買項目，您可以將另一個資料表加入到來源檢視中，其中會列出每個客戶的購買項目資料。</span><span class="sxs-lookup"><span data-stu-id="b40c4-109">To logically represent these purchases in your model, you add another table to the data source view that lists the purchases for each customer.</span></span>  
  
 <span data-ttu-id="b40c4-110">這個巢狀購買資料表與客戶資料表之間具有多對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b40c4-110">This nested purchases table is related to the customer table by a many-to-one relationship.</span></span> <span data-ttu-id="b40c4-111">巢狀資料表可能包含每一個客戶的許多資料列，而每一個資料列都包含已購買的單一產品，可能還包含所下訂單的其他資訊、下訂單時的價格，或是任何適用的促銷。</span><span class="sxs-lookup"><span data-stu-id="b40c4-111">The nested table might contain many rows for each customer, each row containing a single product that was purchased, perhaps with additional information about the order that the purchases were made, the price at the time of the order, or any promotions that applied.</span></span> <span data-ttu-id="b40c4-112">您可以使用巢狀資料表中的資訊當做模型的輸入，或是當做可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="b40c4-112">You can use the information in the nested table as inputs to the model, or as the predictable attribute.</span></span>  
  
 <span data-ttu-id="b40c4-113">在這一課，您將進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b40c4-113">In this lesson, you do the following tasks:</span></span>  
  
-   <span data-ttu-id="b40c4-114">您可以將資料來源視圖加入至 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="b40c4-114">You add a data source view to the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span>  
  
-   <span data-ttu-id="b40c4-115">將案例和巢狀資料表加入至此檢視。</span><span class="sxs-lookup"><span data-stu-id="b40c4-115">You add the case and nested tables to this view.</span></span>  
  
-   <span data-ttu-id="b40c4-116">指定案例與巢狀資料表之間的多對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="b40c4-116">You specify the many-to-one relationship between the case and nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b40c4-117">.</span><span class="sxs-lookup"><span data-stu-id="b40c4-117">.</span></span> <span data-ttu-id="b40c4-118">務必完全遵循所描述的程序，正確地指定案例資料表與巢狀資料表之間的關聯性，以避免在處理模型時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b40c4-118">It is important that you follow the described procedure exactly, to correctly specify the relationship between the case table and the nested table and to avoid errors when you process the model.</span></span>  
  
-   <span data-ttu-id="b40c4-119">定義資料行如何在模型中使用。</span><span class="sxs-lookup"><span data-stu-id="b40c4-119">You define how the columns of data are used in the model.</span></span>  
  
 <span data-ttu-id="b40c4-120">如需使用案例和嵌套資料表以及如何選擇嵌套資料表索引鍵的詳細資訊，請參閱[&#40;Analysis Services 資料採礦&#41;的嵌套資料表](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b40c4-120">For more information about working with case and nested tables, and how to choose a nested table key, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="b40c4-121">若要加入資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="b40c4-121">To add a data source view</span></span>  
  
1.  <span data-ttu-id="b40c4-122">在方案總管中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="b40c4-122">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="b40c4-123">此時會開啟資料來源檢視精靈。</span><span class="sxs-lookup"><span data-stu-id="b40c4-123">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="b40c4-124">在 [歡迎使用資料來源檢視精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="b40c4-124">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="b40c4-125">在 [**選取資料來源**] 頁面的 [**關聯式資料來源**] 底下，選取 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 您在「基本資料採礦」教學課程中建立的資料來源。</span><span class="sxs-lookup"><span data-stu-id="b40c4-125">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="b40c4-126">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="b40c4-126">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="b40c4-127">在 [**選取資料表和 Views** ] 頁面上，選取下列資料表，然後按一下向右箭號，將它們包含在 [新資料來源] 視圖中：</span><span class="sxs-lookup"><span data-stu-id="b40c4-127">On the **Select Tables and Views** page, select the following tables, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  <span data-ttu-id="b40c4-128">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="b40c4-128">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="b40c4-129">在 [**正在完成嚮導]** 頁面上，預設會將 [資料來源] 視圖命名為 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b40c4-129">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="b40c4-130">將 [名稱] 變更為 `Orders` ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="b40c4-130">Change the name to `Orders`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="b40c4-131">[資料來源視圖設計工具] 隨即開啟，並 `Orders` 顯示 [資料來源] 視圖。</span><span class="sxs-lookup"><span data-stu-id="b40c4-131">Data Source View Designer opens and the `Orders` data source view appears.</span></span>  
  
### <a name="to-create-a-relationship-between-tables"></a><span data-ttu-id="b40c4-132">若要建立資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="b40c4-132">To create a relationship between tables</span></span>  
  
1.  <span data-ttu-id="b40c4-133">在資料來源檢視設計師中，放置這兩個資料表，好讓它們水平對齊左邊的 vAssocSeqLineItems 資料表和右邊的 vAssocSeqOrders 資料表。</span><span class="sxs-lookup"><span data-stu-id="b40c4-133">In Data Source View Designer, position the two tables so that the tables are aligned horizontally, with the vAssocSeqLineItems table on the left side and the vAssocSeqOrders table on the right side.</span></span>  
  
2.  <span data-ttu-id="b40c4-134">選取 [vAssocSeqLineItems] 資料表中的 [ **OrderNumber** ] 資料行。</span><span class="sxs-lookup"><span data-stu-id="b40c4-134">Select the **OrderNumber** column in the vAssocSeqLineItems table.</span></span>  
  
3.  <span data-ttu-id="b40c4-135">將資料行拖曳至 [vAssocSeqOrders] 資料表，並將它放在 [ **OrderNumber** ] 資料行上。</span><span class="sxs-lookup"><span data-stu-id="b40c4-135">Drag the column to the vAssocSeqOrders table, and put it on the **OrderNumber** column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b40c4-136">請務必將 [ **OrderNumber** ] 資料行從 vAssocSeqLineItems 的 nested 資料表（代表聯結的許多端）拖曳至 vAssocSeqOrders 案例資料表（代表聯結的一端）。</span><span class="sxs-lookup"><span data-stu-id="b40c4-136">Make sure to drag the **OrderNumber** column from the vAssocSeqLineItems nested table, which represents the many side of the join, to the vAssocSeqOrders case table, which represents the one side of the join.</span></span>  
  
     <span data-ttu-id="b40c4-137">VAssocSeqLineItems 和 vAssocSeqOrders 資料表之間現在有新的*多對一關聯*性。</span><span class="sxs-lookup"><span data-stu-id="b40c4-137">A new *many-to-one relationship* now exists between the vAssocSeqLineItems and vAssocSeqOrders tables.</span></span> <span data-ttu-id="b40c4-138">如果您已經正確聯結這些資料表，資料來源檢視應顯示如下：</span><span class="sxs-lookup"><span data-stu-id="b40c4-138">If you have joined the tables correctly, the data source view should appear as follows:</span></span>  
  
     <span data-ttu-id="b40c4-139">![巢狀和案例資料表之間必須是多對一聯結](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "巢狀和案例資料表之間必須是多對一聯結")</span><span class="sxs-lookup"><span data-stu-id="b40c4-139">![expected many-to-one join on nested and case table](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "expected many-to-one join on nested and case table")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b40c4-140">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b40c4-140">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b40c4-141">建立購物籃結構和模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="b40c4-141">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b40c4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b40c4-142">See Also</span></span>  
 <span data-ttu-id="b40c4-143">[元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b40c4-143">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b40c4-144">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b40c4-144">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="b40c4-145">採礦模型 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b40c4-145">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
