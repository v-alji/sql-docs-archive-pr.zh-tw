---
title: 在關聯式查詢設計工具中建立查詢 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28b25861-f3b4-4c3e-a9b0-03d6e4cfea26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 555d72c4d3bca8677d04fdc4160639f004d6bbe9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707193"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a><span data-ttu-id="65ef6-102">在關聯式查詢設計工具中建立查詢 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="65ef6-102">Build a Query in the Relational Query Designer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="65ef6-103">查詢設計工具可協助您針對報表資料集，指定要從外部資料來源擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="65ef6-103">A query designer helps you specify which data to retrieve from an external data source for a report dataset.</span></span> <span data-ttu-id="65ef6-104">當您在精靈中建置查詢或建立資料集查詢時，就會使用查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="65ef6-104">You use a query designer when you build a query in a wizard or create a dataset query.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="65ef6-105">資料集是以資料來源為基礎。</span><span class="sxs-lookup"><span data-stu-id="65ef6-105">A dataset is based on a data source.</span></span> <span data-ttu-id="65ef6-106">資料來源的類型以及撰寫環境會決定當您定義資料集查詢時開啟的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="65ef6-106">The type of data source and the authoring environment determines which query designer opens when you define the dataset query.</span></span> <span data-ttu-id="65ef6-107">查詢設計工具功能會因基礎資料來源而異。</span><span class="sxs-lookup"><span data-stu-id="65ef6-107">Query designer features vary based on the underlying data source.</span></span> <span data-ttu-id="65ef6-108">如需資料層的詳細資訊，請參閱 Reporting Services 中報表產生器或[資料連線、資料來源和連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)[中的資料連線、資料來源和連接](../data-connections-data-sources-and-connection-strings-in-report-builder.md)字串。</span><span class="sxs-lookup"><span data-stu-id="65ef6-108">For more information about data layers, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="65ef6-109">您可以使用查詢設計工具進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="65ef6-109">You can use a query designer for the following tasks:</span></span>  
  
-   <span data-ttu-id="65ef6-110">瀏覽外部資料來源上多個結構描述的中繼資料</span><span class="sxs-lookup"><span data-stu-id="65ef6-110">Explore the metadata for multiple schemas on the external data source</span></span>  
  
-   <span data-ttu-id="65ef6-111">指定要為資料集擷取的欄位</span><span class="sxs-lookup"><span data-stu-id="65ef6-111">Specify fields to retrieve for the dataset</span></span>  
  
-   <span data-ttu-id="65ef6-112">指定兩個物件 (如資料表) 之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="65ef6-112">Specify relationships between two objects such as tables</span></span>  
  
-   <span data-ttu-id="65ef6-113">指定篩選條件來限制擷取的報表資料</span><span class="sxs-lookup"><span data-stu-id="65ef6-113">Specify filters to restrict the data before it is retrieved as report data</span></span>  
  
-   <span data-ttu-id="65ef6-114">指出是否要建立參數</span><span class="sxs-lookup"><span data-stu-id="65ef6-114">Indicate whether to create parameters</span></span>  
  
-   <span data-ttu-id="65ef6-115">指定要在外部資料來源上執行計算的彙總</span><span class="sxs-lookup"><span data-stu-id="65ef6-115">Specify aggregates to perform calculations on the external data source</span></span>  
  
 <span data-ttu-id="65ef6-116">開啟查詢設計工具後，不論是內嵌資料集或共用資料集，建立查詢的方式均相同。</span><span class="sxs-lookup"><span data-stu-id="65ef6-116">After you open a query designer, you build a query in the same way for either an embedded dataset or a shared dataset.</span></span> <span data-ttu-id="65ef6-117">下列程序使用內嵌資料集查詢。</span><span class="sxs-lookup"><span data-stu-id="65ef6-117">The following procedures use an embedded dataset query.</span></span>  
  
 <span data-ttu-id="65ef6-118">如需詳細資訊，請參閱[關聯式查詢設計工具使用者介面 &#40;報表產生器&#41;](relational-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="65ef6-118">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md).</span></span>  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a><span data-ttu-id="65ef6-119">若要在報表設計檢視中建立內嵌資料集的查詢</span><span class="sxs-lookup"><span data-stu-id="65ef6-119">To build a query for an embedded dataset in Report Design View</span></span>  
  
1.  <span data-ttu-id="65ef6-120">開啟查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="65ef6-120">Open the query designer.</span></span> <span data-ttu-id="65ef6-121">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料集，然後按一下 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="65ef6-121">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
     <span data-ttu-id="65ef6-122">隨即開啟與資料來源相關聯的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="65ef6-122">The query designer that is associated with the data source opens.</span></span>  
  
2.  <span data-ttu-id="65ef6-123">在 [資料庫檢視] 窗格中，展開資料夾，顯示資料庫結構描述物件 (如資料表、檢視表和預存程序) 的階層式檢視。</span><span class="sxs-lookup"><span data-stu-id="65ef6-123">In the Database view pane, expand the folders that display a hierarchical view of database schema objects such as tables, views, and stored procedures.</span></span> <span data-ttu-id="65ef6-124">按一下選取方塊來選取物件的所有欄位，或展開節點來選取個別欄位。</span><span class="sxs-lookup"><span data-stu-id="65ef6-124">Click the select box to select all fields for an object or expand the node to select individual fields.</span></span>  
  
     <span data-ttu-id="65ef6-125">當您從 [資料庫檢視] 窗格選取欄位時， **[選取欄位]** 窗格會顯示您選取的項目。</span><span class="sxs-lookup"><span data-stu-id="65ef6-125">As you select fields from the Database view pane, the **Select fields** pane displays your selections.</span></span>  
  
     <span data-ttu-id="65ef6-126">如果您從一個以上的關聯資料庫資料表選取欄位，請使用 [關聯性] 窗格檢視從資料庫結構描述偵測到的資料表關聯性。</span><span class="sxs-lookup"><span data-stu-id="65ef6-126">If you select fields from more than one related database table, use the Relationships pane to view the table relationships that were detected from the database schema.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="65ef6-127">資料集欄位清單會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="65ef6-127">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-specify-limits-for-a-query"></a><span data-ttu-id="65ef6-128">若要指定查詢的限制條件</span><span class="sxs-lookup"><span data-stu-id="65ef6-128">To specify limits for a query</span></span>  
  
1.  <span data-ttu-id="65ef6-129">在關聯式查詢設計工具中，確認您已選取欄位，且欄位出現在 **[選取的欄位]** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="65ef6-129">In the relational query designer, verify that you have fields selected and that the fields appear in the **Selected fields** pane.</span></span>  
  
2.  <span data-ttu-id="65ef6-130">在 [套用的篩選器] 窗格工具列中，按一下 **[加入篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="65ef6-130">In the Applied filters pane toolbar, click **Add Filter**.</span></span> <span data-ttu-id="65ef6-131">新的篩選資料列隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="65ef6-131">A new filter row appears.</span></span>  
  
3.  <span data-ttu-id="65ef6-132">在 [欄位名稱]  中，按一下以顯示欄位的下拉式清單，然後按一下要作為篩選依據的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="65ef6-132">In **Field name**, click to display the drop-down list of fields, and then click the name of the field that you want to filter by.</span></span> <span data-ttu-id="65ef6-133">例如，若要依數量篩選，請按一下包含項目數的欄位。</span><span class="sxs-lookup"><span data-stu-id="65ef6-133">For example, to filter by quantity, click the field that contains the number of items.</span></span>  
  
4.  <span data-ttu-id="65ef6-134">在 [運算子]  中，按一下以顯示運算子的下拉式清單，然後選取要用於篩選的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="65ef6-134">In **Operator**, click to display the drop-down list of operators, and then select the comparison operator to use in the filter.</span></span>  
  
5.  <span data-ttu-id="65ef6-135">在 **[值]** 中，輸入篩選所要依據的值。</span><span class="sxs-lookup"><span data-stu-id="65ef6-135">In **Value**, type the value that you want to filter by.</span></span> <span data-ttu-id="65ef6-136">例如，若要篩選出超過 100 的數量，請輸入 100。</span><span class="sxs-lookup"><span data-stu-id="65ef6-136">For example, to filter on quantity greater than 100, type 100.</span></span>  
  
6.  <span data-ttu-id="65ef6-137">在此資料列中選取參數選項來建立資料集參數，以便讓使用者指定篩選值。</span><span class="sxs-lookup"><span data-stu-id="65ef6-137">Select the parameter option in this row to create a dataset parameter to enable a user to specify a filter value.</span></span> <span data-ttu-id="65ef6-138">系統會自動建立符合資料集參數的報表參數。</span><span class="sxs-lookup"><span data-stu-id="65ef6-138">A report parameter that matches the dataset parameter is automatically created.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="65ef6-139">資料集欄位清單會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="65ef6-139">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-view-a-query-result-set"></a><span data-ttu-id="65ef6-140">若要檢視查詢結果集</span><span class="sxs-lookup"><span data-stu-id="65ef6-140">To view a query result set</span></span>  
  
1.  <span data-ttu-id="65ef6-141">在查詢設計工具工具列上，按一下 [執行查詢 (!)]  。</span><span class="sxs-lookup"><span data-stu-id="65ef6-141">On the query designer toolbar, click **Run Query (!)**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65ef6-142">查詢設計工具會使用設計階段認證執行查詢和擷取結果集。</span><span class="sxs-lookup"><span data-stu-id="65ef6-142">The query designer uses design time credentials to run the query and retrieve the result set.</span></span> <span data-ttu-id="65ef6-143">如需詳細資訊，請參閱 [在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="65ef6-143">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="65ef6-144">查詢會在資料來源上執行，並將範例資料傳回 [查詢結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="65ef6-144">The query runs on the data source and returns example data in the Query results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ef6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65ef6-145">See Also</span></span>  
 <span data-ttu-id="65ef6-146">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-146">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="65ef6-147">[從外部資料來源新增資料 &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-147">[Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="65ef6-148">[查詢設計工具 &#40;報表產生器&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-148">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="65ef6-149">[建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-149">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="65ef6-150">[報表設計檢視 &#40;報表產生器&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-150">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="65ef6-151">[共用資料集設計檢視 &#40;報表產生器&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="65ef6-151">[Shared Dataset Design View &#40;Report Builder&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span></span>  
 [<span data-ttu-id="65ef6-152">Reporting Services 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="65ef6-152">Reporting Services Query Designers</span></span>](../reporting-services-query-designers.md)  
  
  
