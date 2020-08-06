---
title: 樞紐轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.pivottrans.f1
helpviewer_keywords:
- Pivot transformation
- normalized data [Integration Services]
- PivotUsage property
- datasets [Integration Services], normalized data
- less normalized data set [Integration Services]
ms.assetid: 55f5db6e-6777-435f-8a06-b68c129f8437
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43bdc5be709ea00d4be4601f52c38e96fe3f1ce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710770"
---
# <a name="pivot-transformation"></a><span data-ttu-id="16445-102">樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="16445-102">Pivot Transformation</span></span>
  <span data-ttu-id="16445-103">「樞紐」轉換可藉由樞紐資料行值上的輸入資料，將正規化的資料集轉換為較不正規但更精簡的版本。</span><span class="sxs-lookup"><span data-stu-id="16445-103">The Pivot transformation makes a normalized data set into a less normalized but more compact version by pivoting the input data on a column value.</span></span> <span data-ttu-id="16445-104">例如，列出客戶名稱、產品及購買數量的正規化 **Orders** 資料集，對於購買多個產品的客戶一般都具有多個資料列，且該客戶的每個資料列都顯示不同產品的訂單詳細資料。</span><span class="sxs-lookup"><span data-stu-id="16445-104">For example, a normalized **Orders** data set that lists customer name, product, and quantity purchased typically has multiple rows for any customer who purchased multiple products, with each row for that customer showing order details for a different product.</span></span> <span data-ttu-id="16445-105">藉由樞紐產品資料行上的資料集，「樞紐」轉換可以為每位客戶輸出含單一資料列的資料集。</span><span class="sxs-lookup"><span data-stu-id="16445-105">By pivoting the data set on the product column, the Pivot transformation can output a data set with a single row per customer.</span></span> <span data-ttu-id="16445-106">該單一資料列會列出客戶購買的所有產品，產品名稱顯示為資料行名稱，而數量則顯示為產品資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="16445-106">That single row lists all the purchases by the customer, with the product names shown as column names, and the quantity shown as a value in the product column.</span></span> <span data-ttu-id="16445-107">因為不是每位客戶都會購買所有產品，所以許多資料行可能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="16445-107">Because not every customer purchases every product, many columns may contain null values.</span></span>  
  
 <span data-ttu-id="16445-108">當樞紐資料集時，輸入資料行會在樞紐處理中執行不同的角色。</span><span class="sxs-lookup"><span data-stu-id="16445-108">When a dataset is pivoted, input columns perform different roles in the pivoting process.</span></span> <span data-ttu-id="16445-109">資料行的參與方式如下：</span><span class="sxs-lookup"><span data-stu-id="16445-109">A column can participate in the following ways:</span></span>  
  
-   <span data-ttu-id="16445-110">資料行未經變更便傳送至輸出。</span><span class="sxs-lookup"><span data-stu-id="16445-110">The column is passed through unchanged to the output.</span></span> <span data-ttu-id="16445-111">因為許多輸入資料列只產生一個輸出資料列，所以轉換僅複製資料行的第一個輸入值。</span><span class="sxs-lookup"><span data-stu-id="16445-111">Because many input rows can result only in one output row, the transformation copies only the first input value for the column.</span></span>  
  
-   <span data-ttu-id="16445-112">資料行用作識別一組記錄的索引鍵或索引鍵的一部分。</span><span class="sxs-lookup"><span data-stu-id="16445-112">The column acts as the key or part of the key that identifies a set of records.</span></span>  
  
-   <span data-ttu-id="16445-113">資料行定義樞紐。</span><span class="sxs-lookup"><span data-stu-id="16445-113">The column defines the pivot.</span></span> <span data-ttu-id="16445-114">此資料行中的值與已樞紐之資料集中的資料行關聯。</span><span class="sxs-lookup"><span data-stu-id="16445-114">The values in this column are associated with columns in the pivoted dataset.</span></span>  
  
-   <span data-ttu-id="16445-115">資料行包含樞紐建立之資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="16445-115">The column contains values that are placed in the columns that the pivot creates.</span></span>  
  
 <span data-ttu-id="16445-116">這個轉換有一個輸入、一個規則輸出及一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="16445-116">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="sort-and-duplicate-rows"></a><span data-ttu-id="16445-117">排序和複製資料列</span><span class="sxs-lookup"><span data-stu-id="16445-117">Sort and Duplicate Rows</span></span>  
 <span data-ttu-id="16445-118">若要有效地樞紐資料 (即在輸出資料集中建立盡可能少的記錄)，輸入資料必須根據樞紐資料行進行排序。</span><span class="sxs-lookup"><span data-stu-id="16445-118">To pivot data efficiently, which means creating as few records in the output dataset as possible, the input data must be sorted on the pivot column.</span></span> <span data-ttu-id="16445-119">如果資料未排序，「樞紐」轉換可能會為集索引鍵 (定義集成員資格的資料行) 中的每個值產生多筆記錄。</span><span class="sxs-lookup"><span data-stu-id="16445-119">If the data is not sorted, the Pivot transformation might generate multiple records for each value in the set key, which is the column that defines set membership.</span></span> <span data-ttu-id="16445-120">例如，如果資料集在 **Name** 資料行上進行樞紐但名稱未排序，則輸出資料集中的每位客戶可能會一個以上的資料列，因為 **Name** 中的值在每次變更時都會進行樞紐。</span><span class="sxs-lookup"><span data-stu-id="16445-120">For example, if a dataset is pivoted on a **Name** column but the names are not sorted, the output dataset could have more than one row for each customer, because a pivot occurs every time that the value in **Name** changes.</span></span>  
  
 <span data-ttu-id="16445-121">輸入資料可能會包含重複資料列，因而造成「樞紐」轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="16445-121">The input data might contain duplicate rows, which will cause the Pivot transformation to fail.</span></span> <span data-ttu-id="16445-122">「重複資料列」表示集索引鍵資料行及樞紐資料行中有相同值的資料列。</span><span class="sxs-lookup"><span data-stu-id="16445-122">"Duplicate rows" means rows that have the same values in the set key columns and the pivot columns.</span></span> <span data-ttu-id="16445-123">若要避免失敗，您可以設定轉換，而將錯誤資料列重新導向至錯誤輸出，也可以預先彙總值，以確定沒有重複資料列。</span><span class="sxs-lookup"><span data-stu-id="16445-123">To avoid failure, you can either configure the transformation to redirect error rows to an error output or you can pre-aggregate values to ensure there are no duplicate rows.</span></span>  
  
##  <a name="options-in-the-pivot-dialog-box"></a><a name="options"></a> <span data-ttu-id="16445-124">樞紐對話方塊中的選項</span><span class="sxs-lookup"><span data-stu-id="16445-124">Options in the Pivot Dialog Box</span></span>  
 <span data-ttu-id="16445-125">您可以在 [樞紐]  對話方塊中設定選項，以設定樞紐作業。</span><span class="sxs-lookup"><span data-stu-id="16445-125">You configure the pivot operation by setting the options in the **Pivot** dialog box.</span></span> <span data-ttu-id="16445-126">若要開啟 [樞紐]  對話方塊，請將樞紐轉換加入 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中的封裝，然後以滑鼠右鍵按一下元件，再按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="16445-126">To open the **Pivot** dialog box, add the Pivot transformation to the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and then right-click the component and click **Edit**.</span></span>  
  
 <span data-ttu-id="16445-127">下列清單描述 [樞紐]  對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="16445-127">The following list describes the options in the **Pivot** dialog box.</span></span>  
  
 <span data-ttu-id="16445-128">**樞紐索引鍵**</span><span class="sxs-lookup"><span data-stu-id="16445-128">**Pivot Key**</span></span>  
 <span data-ttu-id="16445-129">指定要用於跨資料表頂端列 (標頭資料列) 之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="16445-129">Specifies the column to use for values across the top row (header row) of the table.</span></span>  
  
 <span data-ttu-id="16445-130">**設定索引鍵**</span><span class="sxs-lookup"><span data-stu-id="16445-130">**Set Key**</span></span>  
 <span data-ttu-id="16445-131">指定要用於資料表左側資料行之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="16445-131">Specifies the column to use for values in the left column of the table.</span></span> <span data-ttu-id="16445-132">輸入日期必須儲存在此資料行上。</span><span class="sxs-lookup"><span data-stu-id="16445-132">The input date must be sorted on this column.</span></span>  
  
 <span data-ttu-id="16445-133">**樞紐值**</span><span class="sxs-lookup"><span data-stu-id="16445-133">**Pivot Value**</span></span>  
 <span data-ttu-id="16445-134">指定要用於跨資料表值 (非標頭資料列或左側資料行中的值) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="16445-134">Specifies the column to use for the table values, other than the values in the header row and the left column.</span></span>  
  
 <span data-ttu-id="16445-135">**忽略不相符的樞紐索引鍵值，並在 DataFlow 執行後回報**</span><span class="sxs-lookup"><span data-stu-id="16445-135">**Ignore un-matched Pivot Key values and report them after DataFlow execution**</span></span>  
 <span data-ttu-id="16445-136">選取此選項可將樞紐轉換設定為忽略包含 [樞紐索引鍵]  資料行中未辨識之值的資料列，並在執行封裝時，將所有樞紐索引鍵值輸出至記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="16445-136">Select this option to configure the Pivot transformation to ignore rows containing unrecognized values in the **Pivot Key** column and to output all of the pivot key values to a log message, when the package is run.</span></span>  
  
 <span data-ttu-id="16445-137">您也可以將 `PassThroughUnmatchedPivotKeys` 自訂屬性設定為 `True`，以便將轉換設定為輸出值。</span><span class="sxs-lookup"><span data-stu-id="16445-137">You can also configure the transformation to output the values by setting the `PassThroughUnmatchedPivotKeys` custom property to `True`.</span></span>  
  
 <span data-ttu-id="16445-138">**根據值產生樞紐輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="16445-138">**Generate pivot output columns from values**</span></span>  
 <span data-ttu-id="16445-139">在此方塊中輸入樞紐索引鍵值，讓樞紐轉換針對每個值建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="16445-139">Enter the pivot key values in this box to enable the Pivot transformation to create output columns for each value.</span></span> <span data-ttu-id="16445-140">您可以在執行封裝之前輸入值，或執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="16445-140">You can either enter the values prior to running the package, or do the following.</span></span>  
  
1.  <span data-ttu-id="16445-141">選取 [忽略不相符的樞紐索引鍵值，並在 DataFlow 執行後回報]  選項，然後在 [樞紐]  對話方塊中按一下 [確定]  ，以儲存樞紐轉換的變更。</span><span class="sxs-lookup"><span data-stu-id="16445-141">Select the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then click **OK** in the **Pivot** dialog box to save the changes to the Pivot transformation.</span></span>  
  
2.  <span data-ttu-id="16445-142">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="16445-142">Run the package.</span></span>  
  
3.  <span data-ttu-id="16445-143">當封裝成功時，按一下 [進度]  索引標籤，然後從包含樞紐索引鍵值的樞紐轉換中尋找資訊記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="16445-143">When the package succeeds, click the **Progress** tab and look for the information log message from the Pivot transformation that contains the pivot key values.</span></span>  
  
4.  <span data-ttu-id="16445-144">以滑鼠右鍵按一下訊息，然後按一下 [複製訊息文字]  。</span><span class="sxs-lookup"><span data-stu-id="16445-144">Right-click the message and click **Copy Message Text**.</span></span>  
  
5.  <span data-ttu-id="16445-145">按一下 [偵錯]  功能表上的 [停止偵錯]  以切換到設計模式。</span><span class="sxs-lookup"><span data-stu-id="16445-145">Click **Stop Debugging** on the **Debug** menu to switch to the design mode.</span></span>  
  
6.  <span data-ttu-id="16445-146">以滑鼠右鍵按一下樞紐轉換，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="16445-146">Right-click the Pivot transformation, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="16445-147">取消核取 [忽略不相符的樞紐索引鍵值，並在 DataFlow 執行後回報]  選項，然後使用下列格式，將樞紐索引鍵值貼到 [根據值產生樞紐輸出資料行]  方塊中。</span><span class="sxs-lookup"><span data-stu-id="16445-147">Uncheck the **Ignore un-matched Pivot Key values and report them after DataFlow execution** option, and then paste the pivot key values in the **Generate pivot output columns from values** box using the following format.</span></span>  
  
     <span data-ttu-id="16445-148">[value1],[value2],[value3]</span><span class="sxs-lookup"><span data-stu-id="16445-148">[value1],[value2],[value3]</span></span>  
  
 <span data-ttu-id="16445-149">**立即產生資料行**</span><span class="sxs-lookup"><span data-stu-id="16445-149">**Generate Columns Now**</span></span>  
 <span data-ttu-id="16445-150">按一下以便針對 [根據值產生樞紐輸出資料行]  方塊中列出的每個樞紐索引鍵值，建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="16445-150">Click to create an output column for each pivot key value that is listed in the **Generate pivot output columns from values** box.</span></span>  
  
 <span data-ttu-id="16445-151">輸出資料行會出現在 [現有的樞紐輸出資料行]  方塊中。</span><span class="sxs-lookup"><span data-stu-id="16445-151">The output columns appear in the **Existing pivoted output columns** box.</span></span>  
  
 <span data-ttu-id="16445-152">**現有的樞紐輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="16445-152">**Existing pivoted output columns**</span></span>  
 <span data-ttu-id="16445-153">列出樞紐索引鍵值的輸出資料行</span><span class="sxs-lookup"><span data-stu-id="16445-153">Lists the output columns for the pivot key values</span></span>  
  
 <span data-ttu-id="16445-154">下表顯示資料在 **Year** 資料行上樞紐之前的資料集。</span><span class="sxs-lookup"><span data-stu-id="16445-154">The following table shows a data set before the data is pivoted on the **Year** column.</span></span>  
  
|<span data-ttu-id="16445-155">Year</span><span class="sxs-lookup"><span data-stu-id="16445-155">Year</span></span>|<span data-ttu-id="16445-156">產品名稱</span><span class="sxs-lookup"><span data-stu-id="16445-156">Product Name</span></span>|<span data-ttu-id="16445-157">總計</span><span class="sxs-lookup"><span data-stu-id="16445-157">Total</span></span>|  
|----------|------------------|-----------|  
|<span data-ttu-id="16445-158">2004</span><span class="sxs-lookup"><span data-stu-id="16445-158">2004</span></span>|<span data-ttu-id="16445-159">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="16445-159">HL Mountain Tire</span></span>|<span data-ttu-id="16445-160">1504884.15</span><span class="sxs-lookup"><span data-stu-id="16445-160">1504884.15</span></span>|  
|<span data-ttu-id="16445-161">2003</span><span class="sxs-lookup"><span data-stu-id="16445-161">2003</span></span>|<span data-ttu-id="16445-162">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="16445-162">Road Tire Tube</span></span>|<span data-ttu-id="16445-163">35920.50</span><span class="sxs-lookup"><span data-stu-id="16445-163">35920.50</span></span>|  
|<span data-ttu-id="16445-164">2004</span><span class="sxs-lookup"><span data-stu-id="16445-164">2004</span></span>|<span data-ttu-id="16445-165">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="16445-165">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="16445-166">2805.00</span><span class="sxs-lookup"><span data-stu-id="16445-166">2805.00</span></span>|  
|<span data-ttu-id="16445-167">2002</span><span class="sxs-lookup"><span data-stu-id="16445-167">2002</span></span>|<span data-ttu-id="16445-168">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="16445-168">Touring Tire</span></span>|<span data-ttu-id="16445-169">62364.225</span><span class="sxs-lookup"><span data-stu-id="16445-169">62364.225</span></span>|  
  
 <span data-ttu-id="16445-170">下表顯示資料在 **Year** 資料行上進行樞紐之後的資料集。</span><span class="sxs-lookup"><span data-stu-id="16445-170">The following table shows a data set after the data has been pivoted on the **Year** column.</span></span>  
  
||<span data-ttu-id="16445-171">2002</span><span class="sxs-lookup"><span data-stu-id="16445-171">2002</span></span>|<span data-ttu-id="16445-172">2003</span><span class="sxs-lookup"><span data-stu-id="16445-172">2003</span></span>|<span data-ttu-id="16445-173">2004</span><span class="sxs-lookup"><span data-stu-id="16445-173">2004</span></span>|  
|-|----------|----------|----------|  
|<span data-ttu-id="16445-174">HL Mountain Tire</span><span class="sxs-lookup"><span data-stu-id="16445-174">HL Mountain Tire</span></span>|<span data-ttu-id="16445-175">141164.10</span><span class="sxs-lookup"><span data-stu-id="16445-175">141164.10</span></span>|<span data-ttu-id="16445-176">446297.775</span><span class="sxs-lookup"><span data-stu-id="16445-176">446297.775</span></span>|<span data-ttu-id="16445-177">1504884.15</span><span class="sxs-lookup"><span data-stu-id="16445-177">1504884.15</span></span>|  
|<span data-ttu-id="16445-178">Road Tire Tube</span><span class="sxs-lookup"><span data-stu-id="16445-178">Road Tire Tube</span></span>|<span data-ttu-id="16445-179">3592.05</span><span class="sxs-lookup"><span data-stu-id="16445-179">3592.05</span></span>|<span data-ttu-id="16445-180">35920.50</span><span class="sxs-lookup"><span data-stu-id="16445-180">35920.50</span></span>|<span data-ttu-id="16445-181">89801.25</span><span class="sxs-lookup"><span data-stu-id="16445-181">89801.25</span></span>|  
|<span data-ttu-id="16445-182">Water Bottle - 30 oz.</span><span class="sxs-lookup"><span data-stu-id="16445-182">Water Bottle - 30 oz.</span></span>|<span data-ttu-id="16445-183">*NULL*</span><span class="sxs-lookup"><span data-stu-id="16445-183">*NULL*</span></span>|<span data-ttu-id="16445-184">*NULL*</span><span class="sxs-lookup"><span data-stu-id="16445-184">*NULL*</span></span>|<span data-ttu-id="16445-185">2805.00</span><span class="sxs-lookup"><span data-stu-id="16445-185">2805.00</span></span>|  
|<span data-ttu-id="16445-186">Touring Tire</span><span class="sxs-lookup"><span data-stu-id="16445-186">Touring Tire</span></span>|<span data-ttu-id="16445-187">62364.225</span><span class="sxs-lookup"><span data-stu-id="16445-187">62364.225</span></span>|<span data-ttu-id="16445-188">375051.60</span><span class="sxs-lookup"><span data-stu-id="16445-188">375051.60</span></span>|<span data-ttu-id="16445-189">1041810.00</span><span class="sxs-lookup"><span data-stu-id="16445-189">1041810.00</span></span>|  
  
 <span data-ttu-id="16445-190">若要在 **Year** 資料行上樞紐資料 (如上所示)，則會在 [樞紐] 對話方塊中設定下列選項。</span><span class="sxs-lookup"><span data-stu-id="16445-190">To pivot the data on the **Year** column, as shown above, the following options are set in the **Pivot** dialog box.</span></span>  
  
-   <span data-ttu-id="16445-191">年在 [樞紐索引鍵] 清單方塊中呈選取狀態。</span><span class="sxs-lookup"><span data-stu-id="16445-191">Year is selected in the **Pivot Key** list box.</span></span>  
  
-   <span data-ttu-id="16445-192">產品名稱在[設定索引鍵] 清單方塊中呈選取狀態。</span><span class="sxs-lookup"><span data-stu-id="16445-192">Product Name is selected in the **Set Key** list box.</span></span>  
  
-   <span data-ttu-id="16445-193">總計在 [樞紐值] 清單方塊中呈選取狀態。</span><span class="sxs-lookup"><span data-stu-id="16445-193">Total is selected in the **Pivot Value** list box.</span></span>  
  
-   <span data-ttu-id="16445-194">在 [根據值產生樞紐輸出資料行] 方塊中會輸入下列值。</span><span class="sxs-lookup"><span data-stu-id="16445-194">The following values are entered in the **Generate pivot output columns from values** box.</span></span>  
  
     <span data-ttu-id="16445-195">[2002],[2003],[2004]</span><span class="sxs-lookup"><span data-stu-id="16445-195">[2002],[2003],[2004]</span></span>  
  
## <a name="configuration-of-the-pivot-transformation"></a><span data-ttu-id="16445-196">設定樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="16445-196">Configuration of the Pivot Transformation</span></span>  
 <span data-ttu-id="16445-197">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="16445-197">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="16445-198">如需有關 [進階編輯器] 對話方塊中可設定屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="16445-198">For more information about the properties that you can set in the **Advanced Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="16445-199">Common Properties</span><span class="sxs-lookup"><span data-stu-id="16445-199">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="16445-200">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="16445-200">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-content"></a><span data-ttu-id="16445-201">相關內容</span><span class="sxs-lookup"><span data-stu-id="16445-201">Related Content</span></span>  
 <span data-ttu-id="16445-202">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="16445-202">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16445-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16445-203">See Also</span></span>  
 <span data-ttu-id="16445-204">[取消樞紐轉換](pivot-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="16445-204">[Unpivot Transformation](pivot-transformation.md) </span></span>  
 <span data-ttu-id="16445-205">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="16445-205">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="16445-206">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="16445-206">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
