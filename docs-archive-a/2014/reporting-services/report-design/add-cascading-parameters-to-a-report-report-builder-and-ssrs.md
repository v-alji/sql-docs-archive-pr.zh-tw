---
title: 將串聯參數新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a22eec3-57a7-478e-b6fc-102a9dbe0591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5419d448b2fa9526224e1bccd80d5c195e2763d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687450"
---
# <a name="add-cascading-parameters-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="61934-102">將串聯參數加入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="61934-102">Add Cascading Parameters to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="61934-103">串聯參數會提供管理大量報表資料的方法。</span><span class="sxs-lookup"><span data-stu-id="61934-103">Cascading parameters provide a way of managing large amounts of report data.</span></span> <span data-ttu-id="61934-104">您可以定義一組相關的參數，讓某一個參數的值清單會視另一個參數所選擇的值而定。</span><span class="sxs-lookup"><span data-stu-id="61934-104">You can define a set of related parameters so that the list of values for one parameter depends on the value chosen in another parameter.</span></span> <span data-ttu-id="61934-105">例如，第一個參數是獨立的，而且可能代表一個產品類別目錄的清單。</span><span class="sxs-lookup"><span data-stu-id="61934-105">For example, the first parameter is independent and might present a list of product categories.</span></span> <span data-ttu-id="61934-106">使用者選取類別目錄時，第二個參數會相依於第一個參數的值。</span><span class="sxs-lookup"><span data-stu-id="61934-106">When the user selects a category, the second parameter is dependent on the value of the first parameter.</span></span> <span data-ttu-id="61934-107">其值會隨著所選類別目錄內的子類別目錄清單更新。</span><span class="sxs-lookup"><span data-stu-id="61934-107">Its values are updated with a list of subcategories within the chosen category.</span></span> <span data-ttu-id="61934-108">當使用者檢視報表時，類別目錄與子類別目錄參數的值都用於篩選報表資料。</span><span class="sxs-lookup"><span data-stu-id="61934-108">When the user views the report, the values for both the category and subcategory parameters are used to filter report data.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="61934-109">若要建立串聯參數，您要先定義資料集查詢，然後加入所需之每個串聯參數的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="61934-109">To create cascading parameters, you define the dataset query first and include a query parameter for each cascading parameter that you need.</span></span> <span data-ttu-id="61934-110">您也必須針對每個串聯參數建立個別的資料集來提供可用的值。</span><span class="sxs-lookup"><span data-stu-id="61934-110">You must also create a separate dataset for each cascading parameter to provide available values.</span></span> <span data-ttu-id="61934-111">如需詳細資訊，請參閱[為報表參數新增、變更或刪除可用的值 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="61934-111">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
 <span data-ttu-id="61934-112">順序對於串聯參數相當重要，因為列在清單中後面之參數的資料集查詢會包含清單中前面每個參數的參考。</span><span class="sxs-lookup"><span data-stu-id="61934-112">Order is important for cascading parameters because the dataset query for a parameter later in the list includes a reference to each parameter that is earlier in the list.</span></span> <span data-ttu-id="61934-113">在執行階段，參數在 [報表資料] 窗格中的順序會決定參數查詢出現在報表中的順序，因此，也會決定使用者選擇每個後續參數值的順序。</span><span class="sxs-lookup"><span data-stu-id="61934-113">At run time, the order of the parameters in the Report Data pane determines the order in which the parameter queries appear in the report, and therefore, the order in which a user chooses each successive parameter value.</span></span>  
  
 <span data-ttu-id="61934-114">如需有關使用多個值 (包含全選功能) 建立串聯式參數的詳細資訊，請參閱 [如何擁有全選多值的串聯式參數](https://go.microsoft.com/fwlink/?LinkId=184757)。</span><span class="sxs-lookup"><span data-stu-id="61934-114">For information about creating cascading parameters with multiple values and including the Select All feature, see [How to have a Select All Multivalue Cascading Parameter](https://go.microsoft.com/fwlink/?LinkId=184757).</span></span>  
  
### <a name="to-create-the-main-dataset-with-a-query-that-includes-multiple-related-parameters"></a><span data-ttu-id="61934-115">若要利用包含多個相關參數的查詢建立主資料集</span><span class="sxs-lookup"><span data-stu-id="61934-115">To create the main dataset with a query that includes multiple related parameters</span></span>  
  
1.  <span data-ttu-id="61934-116">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後按一下 **[加入資料集]** 。</span><span class="sxs-lookup"><span data-stu-id="61934-116">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="61934-117">在 **[名稱]** 中，輸入資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-117">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="61934-118">在 **[資料來源]** 中，選擇資料來源的名稱，或是按一下 **[新增]** 來建立一個名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-118">In **Data source**, choose the name of the data source or click **New** to create one.</span></span>  
  
4.  <span data-ttu-id="61934-119">在 **[查詢類型]** 中，選擇所選資料來源的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-119">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="61934-120">在本主題中，會假設 **[文字]** 查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-120">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="61934-121">在 **[查詢]** 中，輸入用於擷取此報表之資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="61934-121">In **Query**, type the query to use to retrieve data for this report.</span></span> <span data-ttu-id="61934-122">查詢必須包括下列部分：</span><span class="sxs-lookup"><span data-stu-id="61934-122">The query must include the following parts:</span></span>  
  
    1.  <span data-ttu-id="61934-123">資料來源欄位的清單。</span><span class="sxs-lookup"><span data-stu-id="61934-123">A list of data source fields.</span></span> <span data-ttu-id="61934-124">例如，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中，SELECT 陳述式會指定給定資料表或資料列中的資料庫資料行名稱清單。</span><span class="sxs-lookup"><span data-stu-id="61934-124">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, the SELECT statement specifies a list of database column names from a given table or view.</span></span>  
  
    2.  <span data-ttu-id="61934-125">適用於每個串聯參數的一個查詢參數。</span><span class="sxs-lookup"><span data-stu-id="61934-125">One query parameter for each cascading parameter.</span></span> <span data-ttu-id="61934-126">查詢參數會指定要在查詢中包含或排除的特定值，藉以限制從資料來源擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="61934-126">A query parameter limits the data retrieved from the data source by specifying certain values to include or exclude from the query.</span></span> <span data-ttu-id="61934-127">查詢參數通常出現在查詢的限制子句中。</span><span class="sxs-lookup"><span data-stu-id="61934-127">Typically, query parameters occur in a restriction clause in the query.</span></span> <span data-ttu-id="61934-128">例如，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 陳述式中，查詢參數會出現在 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="61934-128">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement, query parameters occur in the WHERE clause.</span></span> <span data-ttu-id="61934-129">如需詳細資訊，請參閱《 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 線上叢書 [》中](https://go.microsoft.com/fwlink/?linkid=120955)文件集的＜使用 WHERE 和 HAVING 篩選資料列＞。</span><span class="sxs-lookup"><span data-stu-id="61934-129">For more information, see "Filtering Rows by Using WHERE and HAVING" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
6.  <span data-ttu-id="61934-130">按一下 **[執行]** (**!**)。</span><span class="sxs-lookup"><span data-stu-id="61934-130">Click **Run** (**!**).</span></span> <span data-ttu-id="61934-131">加入查詢參數然後執行查詢之後，會自動建立對應到查詢參數的報表參數。</span><span class="sxs-lookup"><span data-stu-id="61934-131">After you include query parameters and then run the query, report parameters that correspond to the query parameters are automatically created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="61934-132">您第一次執行查詢時，查詢參數的順序會決定這些參數在報表中建立的順序。</span><span class="sxs-lookup"><span data-stu-id="61934-132">The order of query parameters the first time you run a query determines the order that they are created in the report.</span></span> <span data-ttu-id="61934-133">若要變更順序，請參閱[變更報表參數的順序 &#40;報表產生器及 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="61934-133">To change the order, see [Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="61934-134">下一步，您將建立資料集，提供獨立參數的值。</span><span class="sxs-lookup"><span data-stu-id="61934-134">Next, you will create a dataset that provides the values for the independent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-an-independent-parameter"></a><span data-ttu-id="61934-135">建立資料集以提供獨立參數的值</span><span class="sxs-lookup"><span data-stu-id="61934-135">To create a dataset to provide values for an independent parameter</span></span>  
  
1.  <span data-ttu-id="61934-136">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後按一下 **[加入資料集]**。</span><span class="sxs-lookup"><span data-stu-id="61934-136">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="61934-137">在 **[名稱]** 中，輸入資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-137">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="61934-138">在 **[資料來源]** 中，確認名稱為您在步驟 1 中選擇之資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-138">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="61934-139">在 **[查詢類型]** 中，選擇所選資料來源的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-139">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="61934-140">在本主題中，會假設 **[文字]** 查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-140">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="61934-141">在 **[查詢]** 中，輸入用於擷取此參數之值的查詢。</span><span class="sxs-lookup"><span data-stu-id="61934-141">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="61934-142">獨立參數的查詢通常不包含查詢參數。</span><span class="sxs-lookup"><span data-stu-id="61934-142">Queries for independent parameters typically do not contain query parameters.</span></span> <span data-ttu-id="61934-143">例如，若要建立提供所有類別目錄值之參數的查詢，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，類似如下：</span><span class="sxs-lookup"><span data-stu-id="61934-143">For example, to create a query for a parameter that provides all category values, you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT <column name> FROM <table>  
    ```  
  
     <span data-ttu-id="61934-144">SELECT DISTINCT 命令會從結果集移除重複的值，讓您可以從指定之資料表的指定資料行中取得每個唯一的值。</span><span class="sxs-lookup"><span data-stu-id="61934-144">The SELECT DISTINCT command removes duplicate values from the result set so that you get each unique value from the specified column in the specified table.</span></span>  
  
     <span data-ttu-id="61934-145">按一下 **[執行]** (**!**)。</span><span class="sxs-lookup"><span data-stu-id="61934-145">Click **Run** (**!**).</span></span> <span data-ttu-id="61934-146">結果集會顯示可用於這個第一個參數的值。</span><span class="sxs-lookup"><span data-stu-id="61934-146">The result set shows the values that are available for this first parameter.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="61934-147">下一步，您將設定第一個參數的屬性，以便在執行階段使用此資料集擴展其可用的值。</span><span class="sxs-lookup"><span data-stu-id="61934-147">Next, you will set the properties of the first parameter to use this dataset to populate its available values at run-time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="61934-148">設定報表參數的可用值</span><span class="sxs-lookup"><span data-stu-id="61934-148">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="61934-149">在 [報表資料] 窗格的 [參數] 資料夾中，以滑鼠右鍵按一下第一個參數，然後按一下 **[參數屬性]**。</span><span class="sxs-lookup"><span data-stu-id="61934-149">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="61934-150">在 **[名稱]** 中，確認參數的名稱正確。</span><span class="sxs-lookup"><span data-stu-id="61934-150">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="61934-151">按一下 **[可用的值]**。</span><span class="sxs-lookup"><span data-stu-id="61934-151">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="61934-152">按一下 **[從查詢取得值]**。</span><span class="sxs-lookup"><span data-stu-id="61934-152">Click **Get values from a query**.</span></span> <span data-ttu-id="61934-153">三個欄位隨即出現。</span><span class="sxs-lookup"><span data-stu-id="61934-153">Three fields appear.</span></span>  
  
5.  <span data-ttu-id="61934-154">在 **[資料集]** 中，從下拉式清單按一下您在先前程序中建立之資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-154">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="61934-155">在 **[值]** 欄位中，按一下提供參數值之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-155">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="61934-156">在 **[標籤]** 欄位中，按一下提供參數標籤之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-156">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="61934-157">下一步，您將建立資料集，提供相依參數的值。</span><span class="sxs-lookup"><span data-stu-id="61934-157">Next, you will create a dataset that provides the values for a dependent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-a-dependent-parameter"></a><span data-ttu-id="61934-158">建立資料集以提供相依參數的值</span><span class="sxs-lookup"><span data-stu-id="61934-158">To create a dataset to provide values for a dependent parameter</span></span>  
  
1.  <span data-ttu-id="61934-159">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後按一下 **[加入資料集]**。</span><span class="sxs-lookup"><span data-stu-id="61934-159">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="61934-160">在 **[名稱]** 中，輸入資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-160">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="61934-161">在 **[資料來源]** 中，確認名稱為您在步驟 1 中選擇之資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-161">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="61934-162">在 **[查詢類型]** 中，選擇所選資料來源的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-162">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="61934-163">在本主題中，會假設 **[文字]** 查詢類型。</span><span class="sxs-lookup"><span data-stu-id="61934-163">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="61934-164">在 **[查詢]** 中，輸入用於擷取此參數之值的查詢。</span><span class="sxs-lookup"><span data-stu-id="61934-164">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="61934-165">相依參數的查詢通常包含查詢參數，以供此參數所相依的每個參數使用。</span><span class="sxs-lookup"><span data-stu-id="61934-165">Queries for dependent parameters typically include query parameters for each parameter that this parameter is dependent on.</span></span> <span data-ttu-id="61934-166">例如，若要建立針對某個類別目錄 (獨立參數) 提供所有子類別目錄 (相依參數) 值之參數的查詢，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，類似如下：</span><span class="sxs-lookup"><span data-stu-id="61934-166">For example, to create a query for a parameter that provides all subcategory (dependent parameter) values for a category (independent parameter), you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT Subcategory FROM <table>   
    WHERE (Category = @Category)  
    ```  
  
     <span data-ttu-id="61934-167">在 WHERE 子句中，Category 是來自的欄位名稱， \<table> 而 @Category 則是查詢參數。</span><span class="sxs-lookup"><span data-stu-id="61934-167">In the WHERE clause, Category is the name of a field from \<table> and @Category is a query parameter.</span></span> <span data-ttu-id="61934-168">此陳述式會針對在 @Category 中指定的類別目錄，產生子類別目錄的清單。</span><span class="sxs-lookup"><span data-stu-id="61934-168">This statement produces a list of subcategories for the category specified in @Category.</span></span> <span data-ttu-id="61934-169">在執行階段，系統會利用使用者針對報表參數選擇的同名值填入此值。</span><span class="sxs-lookup"><span data-stu-id="61934-169">At run time, this value will be filled in with the value that the user chooses for the report parameter that has the same name.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="61934-170">下一步，您將設定第二個參數的屬性，以便在執行階段使用此資料集擴展其可用的值。</span><span class="sxs-lookup"><span data-stu-id="61934-170">Next, you will set the properties of the second parameter to use this dataset to populate its available values at run time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="61934-171">設定報表參數的可用值</span><span class="sxs-lookup"><span data-stu-id="61934-171">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="61934-172">在 [報表資料] 窗格的 [參數] 資料夾中，以滑鼠右鍵按一下第一個參數，然後按一下 **[參數屬性]**。</span><span class="sxs-lookup"><span data-stu-id="61934-172">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="61934-173">在 **[名稱]** 中，確認參數的名稱正確。</span><span class="sxs-lookup"><span data-stu-id="61934-173">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="61934-174">按一下 **[可用的值]**。</span><span class="sxs-lookup"><span data-stu-id="61934-174">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="61934-175">按一下 **[從查詢取得值]**。</span><span class="sxs-lookup"><span data-stu-id="61934-175">Click **Get values from a query**.</span></span>  
  
5.  <span data-ttu-id="61934-176">在 **[資料集]** 中，從下拉式清單按一下您在先前程序中建立之資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-176">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="61934-177">在 **[值]** 欄位中，按一下提供參數值之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-177">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="61934-178">在 **[標籤]** 欄位中，按一下提供參數標籤之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="61934-178">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-cascading-parameters"></a><span data-ttu-id="61934-179">測試串聯參數</span><span class="sxs-lookup"><span data-stu-id="61934-179">To test the cascading parameters</span></span>  
  
1.  <span data-ttu-id="61934-180">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="61934-180">Click **Run**.</span></span>  
  
2.  <span data-ttu-id="61934-181">從第一個獨立參數的下拉式清單中選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="61934-181">From the drop-down list for the first, independent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="61934-182">報表處理器會執行下一個參數的資料集查詢，並傳遞您針對第一個參數選擇的值。</span><span class="sxs-lookup"><span data-stu-id="61934-182">The report processor runs the dataset query for the next parameter and passes it the value you chose for the first parameter.</span></span> <span data-ttu-id="61934-183">第二個參數的下拉式清單會根據第一個參數值，以可用的值擴展。</span><span class="sxs-lookup"><span data-stu-id="61934-183">The drop-down list for the second parameter is populated with the available values based on the first parameter value.</span></span>  
  
3.  <span data-ttu-id="61934-184">從第二個相依參數的下拉式清單中選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="61934-184">From the drop-down list for the second, dependent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="61934-185">報表不會在選擇最後一個參數後自動執行，因此您可以變更您的選擇。</span><span class="sxs-lookup"><span data-stu-id="61934-185">The report does not run automatically after you choose the last parameter so that you can change your choice.</span></span>  
  
4.  <span data-ttu-id="61934-186">按一下 [檢視報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="61934-186">Click **View Report**.</span></span> <span data-ttu-id="61934-187">報表會根據您所選擇的參數，更新顯示。</span><span class="sxs-lookup"><span data-stu-id="61934-187">The report updates the display based on the parameters you have chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61934-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61934-188">See Also</span></span>  
 <span data-ttu-id="61934-189">[&#40;報表產生器和 SSRS 新增、變更或刪除報表參數&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="61934-189">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="61934-190">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="61934-190">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="61934-191">[教學課程：將參數加入至您的報表 &#40;報表產生器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="61934-191">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="61934-192">[教學課程 &#40;報表產生器&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="61934-192">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="61934-193">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="61934-193">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="61934-194">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="61934-194">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
