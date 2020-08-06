---
title: 選擇和對應預測查詢的輸入資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tables [Analysis Services], prediction queries
- Mining Model Prediction [Analysis Services], input tables
ms.assetid: 00d330a0-879d-4da0-9f29-53c288116f4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54e11752d6278e01e50a379bf7bb57521ff9bb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594851"
---
# <a name="choose-and-map-input-data-for-a-prediction-query"></a><span data-ttu-id="4e98d-102">為預測查詢選擇和對應輸入資料</span><span class="sxs-lookup"><span data-stu-id="4e98d-102">Choose and Map Input Data for a Prediction Query</span></span>
  <span data-ttu-id="4e98d-103">從採礦模型建立預測時，通常是透過饋送新資料至模型 </span><span class="sxs-lookup"><span data-stu-id="4e98d-103">When you create predictions from a mining model, you generally do this by feeding new data into the model.</span></span> <span data-ttu-id="4e98d-104">(時間序列模型是例外，它只能根據歷程記錄資料進行預測)。若要提供新資料給模型，您必須確保資料是做為資料來源檢視的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="4e98d-104">(The exception is time series models, which can make predictions based on historical data only.) To provide the model with new data, you must make sure that the data is available as part of a data source view.</span></span> <span data-ttu-id="4e98d-105">如果您事先知道哪些資料要用於預測，可以將資料包含在用於建立模型的資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="4e98d-105">If you know in advance which data you will use for prediction, you can include it in the data source view that you used to create the model.</span></span> <span data-ttu-id="4e98d-106">否則，您可能需要建立新的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="4e98d-106">Otherwise, you might have to create a new data source view.</span></span> <span data-ttu-id="4e98d-107">如需詳細資訊，請參閱 [多維度模型中的資料來源檢視](../multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="4e98d-107">For more information, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="4e98d-108">有時候，所需資料可能包含在一對多聯結中的多個資料表內。</span><span class="sxs-lookup"><span data-stu-id="4e98d-108">Sometimes the data that you need might be contained within more than one table in a one-to-many join.</span></span> <span data-ttu-id="4e98d-109">當資料用於關聯模型或時序叢集模型，而其中所用的案例資料表連結至包含產品或交易詳細資料的巢狀資料表時，就是這種情況。</span><span class="sxs-lookup"><span data-stu-id="4e98d-109">This is the case with data used for association models or sequence clustering models, which use a case table linked to a nested table that contains product or transaction details.</span></span> <span data-ttu-id="4e98d-110">如果您的模型使用案例巢狀資料表結構，則用於預測的資料也必須具有案例巢狀資料表結構。</span><span class="sxs-lookup"><span data-stu-id="4e98d-110">If your model uses a case-nested table structure, the data that you use for prediction must also have a case-nested table structure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4e98d-111">您無法加入新的資料行或是對應不同資料來源檢視中的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-111">You cannot add new columns or map columns that are in a different data source view.</span></span> <span data-ttu-id="4e98d-112">您所選的資料來源檢視必須包含預測查詢所需的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-112">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
 <span data-ttu-id="4e98d-113">在您識別包含將用於預測之資料的資料表之後，必須將外部資料中的資料行對應至採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-113">After you have identified the tables that contain the data you will use for predictions, you must map the columns in the external data to the columns in the mining model.</span></span> <span data-ttu-id="4e98d-114">例如，如果您的模型根據人口統計和問卷調查回應來預測客戶購買行為，則您的輸入資料應包含通常與模型資料對應的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e98d-114">For example, if your model predicts customer purchasing behavior based on demographics and survey responses, your input data should contains information that generally corresponds to what is in the model.</span></span> <span data-ttu-id="4e98d-115">不需要每個單一資料行都有對應的資料，但對應的資料行越多，預測效果就越好。</span><span class="sxs-lookup"><span data-stu-id="4e98d-115">You do not need to have matching data for every single column, but the more columns you can match, the better.</span></span> <span data-ttu-id="4e98d-116">如果您嘗試對應具有不同資料類型的資料行，系統可能會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4e98d-116">If you try to map columns that have different data types, you might get an error.</span></span> <span data-ttu-id="4e98d-117">在此情況下，您可以在資料來源檢視中定義命名計算，將新的資料行資料轉型或轉換為模型所需的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e98d-117">In that case, you could define a named calculation in the data source view to cast or convert the new column data to the data type required by the model.</span></span> <span data-ttu-id="4e98d-118">如需詳細資訊，請參閱[在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4e98d-118">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).</span></span>  
  
 <span data-ttu-id="4e98d-119">在您選擇要用於預測的資料時，所選資料來源中的某些資料行可能會根據名稱相似度和相符的資料類型，自動對應至採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-119">When you choose the data to use for prediction, some columns in the selected data source might be automatically mapped to the mining model columns, based on name similarity and matching data type.</span></span> <span data-ttu-id="4e98d-120">您可以使用 **[採礦模型預測]** 中的 **[修改對應]** 對話方塊變更對應的資料行、刪除不適當的對應，或為現有資料行建立新對應。</span><span class="sxs-lookup"><span data-stu-id="4e98d-120">You can use the **Modify Mapping** dialog box in the **Mining Model Prediction** to change the columns that are mapped, delete inappropriate mappings, or create new mappings for existing columns.</span></span> <span data-ttu-id="4e98d-121">[採礦模型預測]\*\*\*\* 設計介面也支援連接的拖放編輯。</span><span class="sxs-lookup"><span data-stu-id="4e98d-121">The **Mining Model Prediction** design surface also supports drag-and-drop editing of connections.</span></span>  
  
-   <span data-ttu-id="4e98d-122">若要建立新的連接，只需在 [採礦模型]\*\*\*\* 資料表中選取資料行，並將其拖曳到 [選取輸入資料表]\*\*\*\* 資料表中的對應資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-122">To create a new connection, just select a column in the **Mining Model** table and drag it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
-   <span data-ttu-id="4e98d-123">若要移除連接，請選取連接線並按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="4e98d-123">To remove a connection, select the connection line and press the DELETE key.</span></span>  
  
 <span data-ttu-id="4e98d-124">下列程序描述如何使用 **[指定巢狀聯結]** 對話方塊來修改案例資料表和巢狀資料表之間已建立的聯結 (當做預測查詢的輸入)。</span><span class="sxs-lookup"><span data-stu-id="4e98d-124">The following procedure describes how you can modify the joins that have been created between the case table and a nested table used as inputs to a prediction query, using the **Specify Nested Join** dialog box.</span></span>  
  
### <a name="select-an-input-table"></a><span data-ttu-id="4e98d-125">選取輸入資料表</span><span class="sxs-lookup"><span data-stu-id="4e98d-125">Select an input table</span></span>  
  
1.  <span data-ttu-id="4e98d-126">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師中之 [採礦精確度圖表]\*\*\*\* 的 [選取輸入資料表]\*\*\*\* 資料表上，按一下 [選取案例資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e98d-126">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="4e98d-127">就會開啟 **[選取資料表]** 對話方塊，供您選取包含查詢作為基礎之資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e98d-127">The **Select Table** dialog box opens, in which you can select the table that contains the data on which to base your queries.</span></span>  
  
2.  <span data-ttu-id="4e98d-128">在 **[選取資料表]** 對話方塊中，從 **[資料來源]** 清單裡選取一個資料來源。</span><span class="sxs-lookup"><span data-stu-id="4e98d-128">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span>  
  
3.  <span data-ttu-id="4e98d-129">在 [資料表/檢視名稱]\*\*\*\* 之下，選取包含您要用來測試模型之資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e98d-129">Under **Table/View Name**, select the table that contains the data you want to use to test the models.</span></span>  
  
4.  <span data-ttu-id="4e98d-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4e98d-130">Click **OK**.</span></span>  
  
     <span data-ttu-id="4e98d-131">採礦結構中的資料行，會自動對應到輸入資料表中之名稱相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-131">The columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
### <a name="change-the-way-that-input-data-is-mapped-to-the-model"></a><span data-ttu-id="4e98d-132">變更輸入資料對應至模型的方式</span><span class="sxs-lookup"><span data-stu-id="4e98d-132">Change the way that input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="4e98d-133">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的資料採礦設計師中，選取 **[採礦模型預測]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4e98d-133">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="4e98d-134">在 **[採礦模型]** 功能表上，選取 **[修改連接]**。</span><span class="sxs-lookup"><span data-stu-id="4e98d-134">On the **Mining Model** menu, select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="4e98d-135">**[修改對應]** 對話方塊會開啟。</span><span class="sxs-lookup"><span data-stu-id="4e98d-135">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="4e98d-136">在此對話方塊中， **[採礦模型資料行]** 資料行會在選取的採礦結構中列出資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-136">In this dialog box, the column **Mining Model Column** lists the columns in the selected mining structure.</span></span> <span data-ttu-id="4e98d-137">[資料表資料行]\*\*\*\* 資料行會在外部資料來源中，列出您在 [選取輸入資料表]\*\*\*\* 對話方塊中選擇的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-137">The column **Table Column** lists the columns in the external data source that you chose in the **SelectInput Table(s)** dialog box.</span></span> <span data-ttu-id="4e98d-138">外部資料來源中的資料行會對應到採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-138">The columns in the external data source are mapped to columns in the mining model.</span></span>  
  
3.  <span data-ttu-id="4e98d-139">在 **[資料表資料行]** 之下，選取對應到您要對應之目標採礦模型的資料列。</span><span class="sxs-lookup"><span data-stu-id="4e98d-139">Under **Table Column**, select the row that corresponds to the mining model column that you want to map to.</span></span>  
  
4.  <span data-ttu-id="4e98d-140">從外部資料來源的可用資料行清單中，選取新的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-140">Select a new column from the list of available columns in the external data source.</span></span> <span data-ttu-id="4e98d-141">選取清單中的空白項目來刪除資料行對應。</span><span class="sxs-lookup"><span data-stu-id="4e98d-141">Select the blank item in the list to delete the column mapping.</span></span>  
  
5.  <span data-ttu-id="4e98d-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4e98d-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="4e98d-143">新的資料行對應會在設計師中顯示。</span><span class="sxs-lookup"><span data-stu-id="4e98d-143">The new column mappings are displayed in the designer.</span></span>  
  
### <a name="remove-a-relationship-between-input-tables"></a><span data-ttu-id="4e98d-144">移除輸入資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="4e98d-144">Remove a relationship between input tables</span></span>  
  
1.  <span data-ttu-id="4e98d-145">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的資料採礦設計師中，[採礦模型預測]\*\*\*\* 索引標籤的 [選取輸入資料表]\*\*\*\* 資料表上，按一下 [修改聯結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e98d-145">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Modify Join**.</span></span>  
  
     <span data-ttu-id="4e98d-146">**[指定巢狀聯結]** 對話方塊就會開啟。</span><span class="sxs-lookup"><span data-stu-id="4e98d-146">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="4e98d-147">選取關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e98d-147">Select a relationship.</span></span>  
  
3.  <span data-ttu-id="4e98d-148">按一下 **[移除關聯性]**。</span><span class="sxs-lookup"><span data-stu-id="4e98d-148">Click **Remove Relationship**.</span></span>  
  
4.  <span data-ttu-id="4e98d-149">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4e98d-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="4e98d-150">即移除案例資料表和巢狀資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e98d-150">The relationship between the case table and the nested table has been removed.</span></span>  
  
### <a name="create-a-new-relationship-between-input-tables"></a><span data-ttu-id="4e98d-151">建立輸入資料表之間的新關聯性</span><span class="sxs-lookup"><span data-stu-id="4e98d-151">Create a new relationship between input tables</span></span>  
  
1.  <span data-ttu-id="4e98d-152">在資料採礦設計師的 [採礦模型預測]\*\*\*\* 索引標籤中，於 [選取輸入資料表]\*\*\*\* 資料表上，按一下 [修改聯結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e98d-152">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer, click **Modify Join**.</span></span>  
  
     <span data-ttu-id="4e98d-153">**[指定巢狀聯結]** 對話方塊就會開啟。</span><span class="sxs-lookup"><span data-stu-id="4e98d-153">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="4e98d-154">按一下 **[加入關聯性]**。</span><span class="sxs-lookup"><span data-stu-id="4e98d-154">Click **Add Relationship**.</span></span>  
  
     <span data-ttu-id="4e98d-155">**[建立關聯性]** 對話方塊就會開啟。</span><span class="sxs-lookup"><span data-stu-id="4e98d-155">The **Create Relationship** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4e98d-156">在 **[來源資料行]** 中選取巢狀資料表的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e98d-156">Select the key of the nested table in **Source Columns**.</span></span>  
  
4.  <span data-ttu-id="4e98d-157">在 **[目的地資料行]** 中選取案例資料表的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4e98d-157">Select the key of the case table in **Destination Columns**.</span></span>  
  
5.  <span data-ttu-id="4e98d-158">在 **[建立關聯性]** 對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4e98d-158">Click **OK** in the **Create Relationship** dialog box.</span></span>  
  
6.  <span data-ttu-id="4e98d-159">在 **[指定巢狀聯結]** 對話方塊中按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4e98d-159">Click **OK** in the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="4e98d-160">即在案例資料表和巢狀資料表之間建立新的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e98d-160">A new relationship has been created between the case table and the nested table.</span></span>  
  
### <a name="add-a-nested-table-to-the-input-tables-of-a-prediction-query"></a><span data-ttu-id="4e98d-161">加入巢狀資料表至預測查詢的輸入資料表</span><span class="sxs-lookup"><span data-stu-id="4e98d-161">Add a nested table to the input tables of a prediction query</span></span>  
  
1.  <span data-ttu-id="4e98d-162">在資料採礦設計師的 **[採礦模型預測]** 索引標籤上，按一下 **[選取案例資料表]** 來開啟 **[選取資料表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4e98d-162">On the **Mining Model Prediction** tab in Data Mining Designer, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e98d-163">在指定案例資料表之前，無法新增巢狀資料表至輸入。</span><span class="sxs-lookup"><span data-stu-id="4e98d-163">You cannot add a nested table to the inputs unless you have specified a case table.</span></span> <span data-ttu-id="4e98d-164">如果使用巢狀資料表，用於預測的採礦模型也需要使用巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="4e98d-164">Use of a nested table requires that the mining model you are using for prediction also uses a nested table.</span></span>  
  
2.  <span data-ttu-id="4e98d-165">在 **[選取資料表]** 對話方塊中，從 **[資料來源]** 清單選取資料來源，然後在資料來源檢視中選取包含案例資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e98d-165">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="4e98d-166">按一下 **[選取巢狀資料表]** 來開啟 **[選取資料表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4e98d-166">Click **Select Nested Table** to open the **Select Table** dialog box.</span></span>  
  
4.  <span data-ttu-id="4e98d-167">在 **[選取資料表]** 對話方塊中，從 **[資料來源]** 清單選取資料來源，然後在資料來源檢視中選取包含巢狀資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e98d-167">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the nested data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="4e98d-168">如果關聯性已經存在，採礦模型中的資料行就會自動對應到輸入資料表中的同名資料行。</span><span class="sxs-lookup"><span data-stu-id="4e98d-168">If a relationship already exists, the columns in the mining model are automatically mapped to the columns that have the same name in the input table.</span></span> <span data-ttu-id="4e98d-169">您可以按一下 **[修改聯結]**，這會開啟 **[建立關聯性]** 對話方塊，在其中修改巢狀資料表和案例資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e98d-169">You can modify the relationship between the nested table and the case table by clicking **Modify Join**, which opens the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e98d-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e98d-170">See Also</span></span>  
 [<span data-ttu-id="4e98d-171">預測查詢 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e98d-171">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
