---
title: 從資料採礦模型擷取資料 (DMX) (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a59184524967a9bfe772e41890afc3b900cc9e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706253"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a><span data-ttu-id="2c549-102">從資料採礦模型擷取資料 (DMX) (SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c549-102">Retrieve Data from a Data Mining Model (DMX) (SSRS)</span></span>
  <span data-ttu-id="2c549-103">若要在報表中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料採礦模型內的資料，您必須定義 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源並建立一或多個報表資料集。</span><span class="sxs-lookup"><span data-stu-id="2c549-103">To use data from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data mining model in your report, you must define a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source and one or more report datasets.</span></span> <span data-ttu-id="2c549-104">當您建立資料來源定義時，您必須指定連接字串和認證，好讓您可以從用戶端電腦存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="2c549-104">When you create the data source definition, you must specify a connection string and credentials so that you can access the data source from your client computer.</span></span>  
  
 <span data-ttu-id="2c549-105">您可以建立內嵌資料來源定義供單一報表使用，或是建立共用資料來源定義供多個報表使用。</span><span class="sxs-lookup"><span data-stu-id="2c549-105">You can create an embedded data source definition for use by a single report or a shared data source definition that can be used by multiple reports.</span></span> <span data-ttu-id="2c549-106">本主題的程序描述如何建立內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="2c549-106">The procedures in this topic describe how to create an embedded data source.</span></span> <span data-ttu-id="2c549-107">如需共用資料來源的詳細資訊，請參閱[內嵌和共用資料連線或資料來源 &#40;報表產生器及 SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) 和[建立、修改及刪除共用資料來源 &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2c549-107">For more information about shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) and [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="2c549-108">在您建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源之後，就可以建立一或多個資料集。</span><span class="sxs-lookup"><span data-stu-id="2c549-108">After you create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you can create one or more datasets.</span></span> <span data-ttu-id="2c549-109">您可針對每一個資料集使用資料採礦預測運算式 (DMX) 查詢設計工具，以建立一個指定欄位集合的 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="2c549-109">For each dataset, you use a Data Mining Prediction Expression (DMX) query designer to create a DMX query that specifies the field collection.</span></span> <span data-ttu-id="2c549-110">如需詳細資訊，請參閱 [Analysis Services MDX 查詢設計工具使用者介面](analysis-services-dmx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2c549-110">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="2c549-111">在您建立資料集之後，該資料集的名稱會出現在 [報表資料] 窗格中，當做其資料來源底下的一個節點。</span><span class="sxs-lookup"><span data-stu-id="2c549-111">After you create a dataset, the name of the dataset appears in the Report Data pane as a node under its data source.</span></span>  
  
 <span data-ttu-id="2c549-112">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="2c549-112">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a><span data-ttu-id="2c549-113">建立內嵌 Microsoft SQL Server Analysis Services 資料來源</span><span class="sxs-lookup"><span data-stu-id="2c549-113">To create an embedded Microsoft SQL Server Analysis Services data source</span></span>  
  
1.  <span data-ttu-id="2c549-114">在 [報表資料] 窗格的工具列上，按一下 **[新增]** ，然後按一下 **[資料來源]** 。</span><span class="sxs-lookup"><span data-stu-id="2c549-114">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="2c549-115">在 [資料來源屬性]  對話方塊中，於 [名稱]  文字方塊內鍵入名稱，或是接受預設名稱。</span><span class="sxs-lookup"><span data-stu-id="2c549-115">In the **Data Source Properties** dialog box, type a name in the **Name** text box, or accept the default name.</span></span>  
  
3.  <span data-ttu-id="2c549-116">確認 [內嵌連線]  已選取。</span><span class="sxs-lookup"><span data-stu-id="2c549-116">Verify that **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="2c549-117">從 [類型]  下拉式清單中，選取 [Microsoft SQL Server Analysis Services]  。</span><span class="sxs-lookup"><span data-stu-id="2c549-117">From the **Type** drop-down list, select **Microsoft SQL Server Analysis Services**.</span></span>  
  
5.  <span data-ttu-id="2c549-118">指定與 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源搭配使用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="2c549-118">Specify a connection string that works with your [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
     <span data-ttu-id="2c549-119">請洽詢資料庫管理員，以取得用來連接資料來源的連接資訊和認證。</span><span class="sxs-lookup"><span data-stu-id="2c549-119">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="2c549-120">下列連接字串範例會在本機用戶端上指定範例 [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2c549-120">The following connection string example specifies the sample [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] database on the local client.</span></span>  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  <span data-ttu-id="2c549-121">按一下 **[認證]** 。</span><span class="sxs-lookup"><span data-stu-id="2c549-121">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="2c549-122">設定用來連接資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="2c549-122">Set the credentials to use to connect to the data source.</span></span> <span data-ttu-id="2c549-123">如需詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](../../integration-services/connection-manager/data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="2c549-123">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2c549-124">若要測試資料來源連線，請按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="2c549-124">To test the data source connection, click **Edit**.</span></span> <span data-ttu-id="2c549-125">在 [連接屬性]  對話方塊中，按一下 [測試連線]  。</span><span class="sxs-lookup"><span data-stu-id="2c549-125">In the **Connection Properties** dialog box, click **Test Connection**.</span></span> <span data-ttu-id="2c549-126">如果測試成功，您將會看到「連接測試成功」的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="2c549-126">If the test is successful, you will see the information message "Test connection succeeded."</span></span> <span data-ttu-id="2c549-127">如果測試失敗，您將會看到一個警告訊息，其中包含測試未能成功之原因的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2c549-127">If the test fails, you will see a warning message with more information about why the test was not successful.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2c549-128">資料來源會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="2c549-128">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a><span data-ttu-id="2c549-129">若要為 Microsoft SQL Server Analysis Services 建立資料集</span><span class="sxs-lookup"><span data-stu-id="2c549-129">To create a dataset for a Microsoft SQL Server Analysis Services</span></span>  
  
1.  <span data-ttu-id="2c549-130">在 [報表資料]  窗格中，以滑鼠右鍵按一下連線到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源的資料來源名稱，然後按一下 [新增資料集]  。</span><span class="sxs-lookup"><span data-stu-id="2c549-130">In the **Report Data** pane, right-click the name of the data source that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="2c549-131">在 [資料集屬性]  對話方塊中，於 [名稱]  文字方塊內鍵入名稱。</span><span class="sxs-lookup"><span data-stu-id="2c549-131">In the **Dataset Properties** dialog box, type a name in the **Name** text box.</span></span>  
  
3.  <span data-ttu-id="2c549-132">在 [資料來源]  方塊中，確認該名稱為連線到 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="2c549-132">In the **Data source box**, verify that the name is the name of a data source that connects to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
4.  <span data-ttu-id="2c549-133">按一下 [查詢設計工具]  ，開啟圖形化查詢設計工具來以互動方式建立查詢。</span><span class="sxs-lookup"><span data-stu-id="2c549-133">Click **Query Designer** to open the graphical query designer to build a query interactively.</span></span> <span data-ttu-id="2c549-134">如果在 MDX 模式中開啟查詢設計工具，請按一下工具列上的 [命令類型 DMX]  (![變更為 DMX 查詢語言檢視](../media/rsqdicon-commandtypedmx.gif "變更為 DMX 查詢語言檢視"))，切換到資料採礦查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="2c549-134">If the query designer opens in MDX mode, click **Command Type DMX** (![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) on the toolbar to switch to the data mining query designer.</span></span> <span data-ttu-id="2c549-135">如需詳細資訊，請參閱 [Analysis Services MDX 查詢設計工具使用者介面](analysis-services-dmx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2c549-135">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
     <span data-ttu-id="2c549-136">或者，若要從其他報表匯入現有的 DMX 查詢，請按一下 [匯入]  ，然後巡覽至包含 DMX 查詢的 .rdl 檔案。</span><span class="sxs-lookup"><span data-stu-id="2c549-136">Alternatively, to import an existing DMX query from another report, click **Import**, and then navigate to the .rdl file with the DMX query.</span></span> <span data-ttu-id="2c549-137">不支援從 .dmx 檔案匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="2c549-137">Importing a query from an .dmx file is not supported.</span></span>  
  
5.  <span data-ttu-id="2c549-138">在您建立及執行查詢來查看範例結果之後，請按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2c549-138">After you create and run your query to see sample results, click **OK**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2c549-139">資料集和它的欄位集合會出現在 [報表資料] 窗格的資料來源節點底下。</span><span class="sxs-lookup"><span data-stu-id="2c549-139">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c549-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c549-140">See Also</span></span>  
 <span data-ttu-id="2c549-141">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c549-141">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="2c549-142">[Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2c549-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="2c549-143">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c549-143">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2c549-144">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2c549-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
