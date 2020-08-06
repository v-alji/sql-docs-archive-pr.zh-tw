---
title: 建立共用資料集或內嵌資料集 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fca74e1ba7965eeef6ce562e79e378af5bb9e145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687514"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a><span data-ttu-id="2664a-102">建立共用資料集或內嵌資料集 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2664a-102">Create a Shared Dataset or Embedded Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2664a-103">您可以建立內嵌資料集供單一報表使用，或建立要儲存到報表伺服器的共用資料集，以供多個報表使用。</span><span class="sxs-lookup"><span data-stu-id="2664a-103">You can create an embedded dataset for use in a single report or a shared dataset to save to a report server, for use by multiple reports.</span></span> <span data-ttu-id="2664a-104">若要建立資料集，您必須已經定義內嵌或共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="2664a-104">To create a dataset, you must have an embedded or shared data source.</span></span>

 <span data-ttu-id="2664a-105">請使用報表產生器來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2664a-105">Use Report Builder to do the following tasks:</span></span>

-   <span data-ttu-id="2664a-106">在資料集設計檢視中建立共用資料集。</span><span class="sxs-lookup"><span data-stu-id="2664a-106">Create a shared dataset in Dataset Design View.</span></span> <span data-ttu-id="2664a-107">共用資料集必須使用已發行的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="2664a-107">Shared datasets must use published shared data sources.</span></span>

-   <span data-ttu-id="2664a-108">在報表設計檢視中建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="2664a-108">Create an embedded dataset in Report Design View.</span></span>

-   <span data-ttu-id="2664a-109">將資料集直接儲存至報表伺服器或 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="2664a-109">Save the dataset directly to the report server or SharePoint site.</span></span>

 <span data-ttu-id="2664a-110">請使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的報表設計師來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2664a-110">Use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to do the following tasks:</span></span>

1.  <span data-ttu-id="2664a-111">在 [方案總管] 中建立共用資料集。</span><span class="sxs-lookup"><span data-stu-id="2664a-111">Create a shared dataset in Solution Explorer.</span></span> <span data-ttu-id="2664a-112">共用資料集必須使用 [方案總管] 中 [共用資料來源] 資料夾內的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2664a-112">Shared datasets must use data sources from the Shared Data Sources folder in Solution Explorer.</span></span>

2.  <span data-ttu-id="2664a-113">在 [報表資料] 窗格中建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="2664a-113">Create an embedded dataset in the Report Data pane.</span></span>

3.  <span data-ttu-id="2664a-114">(選擇性) 使用報表來部署共用資料集和共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="2664a-114">Optionally deploy the shared datasets and shared data source with the report.</span></span> <span data-ttu-id="2664a-115">您可以針對每種項目類型，使用 [專案屬性] 來指定報表伺服器或 SharePoint 網站上資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="2664a-115">For each type of item, use Project Properties to specify paths to folders on the report server or SharePoint site.</span></span>

 <span data-ttu-id="2664a-116">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2664a-116">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-open-report-builder-and-create-a-shared-dataset"></a><span data-ttu-id="2664a-117">若要開啟報表產生器，並建立共用資料集</span><span class="sxs-lookup"><span data-stu-id="2664a-117">To open Report Builder and create a shared dataset</span></span>

1.  <span data-ttu-id="2664a-118">開啟報表產生器。</span><span class="sxs-lookup"><span data-stu-id="2664a-118">Open Report Builder.</span></span> <span data-ttu-id="2664a-119">**[新增報表或資料集]** 窗格隨即開啟，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="2664a-119">The **New report or dataset pane** opens, as shown in the following figure:</span></span>

     <span data-ttu-id="2664a-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span><span class="sxs-lookup"><span data-stu-id="2664a-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2664a-121"> 如果 **[新增報表或資料集]** 窗格未出現，請從 [報表產生器] 按鈕按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-121">If the **New report or dataset pane** does not appear, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="2664a-122">在左窗格的 **[建立資料集]** 底下，按一下 **[共用資料集]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-122">In the left pane, under **Create a dataset**, click **Shared Dataset**.</span></span>

3.  <span data-ttu-id="2664a-123">在右窗格中，按一下 **[瀏覽]** 從報表伺服器選取共用資料來源，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-123">In the right pane, click **Browse** to select a shared data source from the report server, and then click **Create**.</span></span> <span data-ttu-id="2664a-124">隨即開啟與共用資料來源相關聯的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="2664a-124">The query designer associated with the shared data source opens.</span></span>

4.  <span data-ttu-id="2664a-125">在查詢設計工具中，指定要併入資料集的欄位。</span><span class="sxs-lookup"><span data-stu-id="2664a-125">In the query designer, specify the fields to include in the dataset.</span></span>

5.  <span data-ttu-id="2664a-126">按一下 [**執行**] (**！**) 以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2664a-126">Click **Run** (**!**) to run the query.</span></span>

6.  <span data-ttu-id="2664a-127">在 **[報表產生器]** 按鈕上，按一下 **[儲存]** 或 **[另存新檔]** ，將共用資料集儲存在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2664a-127">On the **Report Builder** button, click **Save** or **Save As** to save the shared dataset to the report server.</span></span>

7.  <span data-ttu-id="2664a-128">若要結束報表產生器，請按一下 **[報表產生器]**，然後按一下 **[結束報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-128">To exit Report Builder, click **Report Builder**, and then click **Exit Report Builder**.</span></span> <span data-ttu-id="2664a-129">若要處理報表，按一下 **[報表產生器]**，然後按一下 **[新增]** 或 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-129">To work with reports, click **Report Builder**, and then click **New** or **Open**.</span></span>

### <a name="to-set-query-parameter-options"></a><span data-ttu-id="2664a-130">若要設定查詢參數選項</span><span class="sxs-lookup"><span data-stu-id="2664a-130">To set query parameter options</span></span>

1.  <span data-ttu-id="2664a-131">開啟報表產生器。</span><span class="sxs-lookup"><span data-stu-id="2664a-131">Open Report Builder.</span></span>

2.  <span data-ttu-id="2664a-132">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="2664a-132">Click **Open**.</span></span>

3.  <span data-ttu-id="2664a-133">瀏覽至報表伺服器，並選取共用資料來源的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2664a-133">Browse to the report server, and select the folder for the shared data source.</span></span>

4.  <span data-ttu-id="2664a-134">在 **[下列類型的項目]** 中，按一下下拉式清單中的資料集 (\*.rsd)。</span><span class="sxs-lookup"><span data-stu-id="2664a-134">In **Items of type**, click Datasets (\*.rsd) in the drop-down list.</span></span>

5.  <span data-ttu-id="2664a-135">選取共用資料集，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-135">Select the shared dataset, and then click **Open**.</span></span> <span data-ttu-id="2664a-136">隨即開啟關聯的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="2664a-136">The associated query designer opens.</span></span>

6.  <span data-ttu-id="2664a-137">在功能區上，按一下 **[資料集屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-137">On the Ribbon, click **Dataset Properties**.</span></span>

7.  <span data-ttu-id="2664a-138">按一下 **[參數]** 。</span><span class="sxs-lookup"><span data-stu-id="2664a-138">Click **Parameters**.</span></span> <span data-ttu-id="2664a-139">在這個頁面上，將預設值設定為常數或運算式，並將參數標示為唯讀、可為 Null 或 [從查詢中忽略]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2664a-139">On this page, set a default value to a constant or an expression, mark the parameter as read-only, nullable, or **Omit From Query**.</span></span> <span data-ttu-id="2664a-140">如需詳細資訊，請參閱[資料集屬性對話方塊、參數 &#40;報表產生器&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="2664a-140">For more information, see [Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]


### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a><span data-ttu-id="2664a-141">若要從 SQL Server 關聯式資料庫建立資料集</span><span class="sxs-lookup"><span data-stu-id="2664a-141">To create a dataset from a SQL Server relational database</span></span>

1.  <span data-ttu-id="2664a-142">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源的名稱，然後按一下 **[加入資料集]**。</span><span class="sxs-lookup"><span data-stu-id="2664a-142">In the Report Data pane, right-click the name of the data source, and then click **Add Dataset**.</span></span> <span data-ttu-id="2664a-143">**[資料集屬性]** 對話方塊的 **[查詢]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2664a-143">The **Query** page of the **Dataset Properties** dialog box opens.</span></span>

2.  <span data-ttu-id="2664a-144">在 **[名稱]** 中，輸入資料集名稱或是接受預設名稱。</span><span class="sxs-lookup"><span data-stu-id="2664a-144">In **Name**, type a name for the dataset or accept the default name.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2664a-145">資料集名稱是在報表的內部使用。</span><span class="sxs-lookup"><span data-stu-id="2664a-145">The dataset name is used internally within the report.</span></span> <span data-ttu-id="2664a-146">為了清楚起見，我們建議資料集的名稱應該要描述查詢所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="2664a-146">For clarity, we recommend that the name of the dataset describe the data that the query returns.</span></span>

3.  <span data-ttu-id="2664a-147">在 **[資料來源]** 中，瀏覽並選取現有的共用資料來源名稱，或是按一下 **[新增]** 來建立新的內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="2664a-147">In **Data source**, browse to and select the name of an existing shared data source, or click **New** to create a new embedded data source.</span></span>

4.  <span data-ttu-id="2664a-148">選取 **[查詢類型]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2664a-148">Select a **Query type** option.</span></span> <span data-ttu-id="2664a-149">選項會因資料來源類型而異。</span><span class="sxs-lookup"><span data-stu-id="2664a-149">Options depend on the data source type.</span></span>

    -   <span data-ttu-id="2664a-150">選取 **[Text]** ，即可使用資料來源的查詢語言來撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="2664a-150">Select **Text** to write a query using the query language of the data source.</span></span>

    -   <span data-ttu-id="2664a-151">選取 **[Table]** ，即可傳回關聯式資料庫資料表中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="2664a-151">Select **Table** to return all the fields in a relational database table.</span></span>

    -   <span data-ttu-id="2664a-152">選取 **[StoredProcedure]** 即可依名稱執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="2664a-152">Select **StoredProcedure** to run a stored procedure by name.</span></span>

5.  <span data-ttu-id="2664a-153">在 **[查詢]** 中，輸入查詢、預存程序或資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="2664a-153">In **Query**, type the query, stored procedure, or table name.</span></span> <span data-ttu-id="2664a-154">或者，您也可以按一下 **[查詢設計工具]** 來開啟圖形化或是以文字為基礎的查詢設計工具，或是按一下 **[匯入]** 從現有的報表匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="2664a-154">Alternatively, click **Query Designer** to open the graphical or text-based query designer tool, or **Import** to import the query from an existing report.</span></span>

     <span data-ttu-id="2664a-155">在一些情況下，查詢所指定的欄位集合只能透過在資料來源上執行查詢來判斷。</span><span class="sxs-lookup"><span data-stu-id="2664a-155">In a few cases, the field collection specified by the query can only be determined by running the query on the data source.</span></span> <span data-ttu-id="2664a-156">例如，預存程序可能會在結果集中傳回一組變動的欄位。</span><span class="sxs-lookup"><span data-stu-id="2664a-156">For example, a stored procedure may return a variable set of fields in the result set.</span></span> <span data-ttu-id="2664a-157">按一下 **[重新整理欄位]** 可在資料來源上執行查詢，並擷取在 [報表資料] 窗格中填入資料集欄位集合所需的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="2664a-157">Click **Refresh Fields** to run the query on the data source and retrieve the field names that are needed to populate the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="2664a-158">當您關閉 **[資料集屬性]** 對話方塊之後，資料集節點底下會出現欄位集合。</span><span class="sxs-lookup"><span data-stu-id="2664a-158">The field collection appears under the dataset node after you close the **Dataset Properties** dialog box.</span></span>

6.  <span data-ttu-id="2664a-159">在 **[逾時]** 中，輸入報表伺服器等候資料庫回應的秒數。</span><span class="sxs-lookup"><span data-stu-id="2664a-159">In **Timeout**, type the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="2664a-160">預設值為 0 秒。</span><span class="sxs-lookup"><span data-stu-id="2664a-160">The default value is 0 seconds.</span></span> <span data-ttu-id="2664a-161">當逾時值為 0 秒時，此查詢不會逾時。</span><span class="sxs-lookup"><span data-stu-id="2664a-161">When the time out value is 0 seconds, the query does not time out.</span></span>

7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="2664a-162">資料集和它的欄位集合會出現在 [報表資料] 窗格的資料來源節點底下。</span><span class="sxs-lookup"><span data-stu-id="2664a-162">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>

## <a name="see-also"></a><span data-ttu-id="2664a-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2664a-163">See Also</span></span>
 <span data-ttu-id="2664a-164">[報表內嵌資料集和共用資料集 &#40;報表產生器和 ssrs&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [資料集欄位集合 &#40;報表產生器和 Ssrs&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [查詢設計工具 &#40;報表產生器](../query-designers-report-builder.md)&#41;報表產生器[對話方塊、窗格和](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)工具[將資料新增至報表 &#40;](report-datasets-ssrs.md)報表產生器和[Ssrs&#41;內嵌和共用資料集](embedded-and-shared-datasets-report-builder-and-ssrs.md)報表產生器[資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)&#40;</span><span class="sxs-lookup"><span data-stu-id="2664a-164">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) [Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)</span></span>


