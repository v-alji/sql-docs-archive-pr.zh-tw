---
title: 在「採礦模型」上建立內容查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: a0ce837a-89ed-46cf-9ce1-801ccb75fa04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26af1100d6ba80185c1cc4de18548df0e387824c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686546"
---
# <a name="create-a-content-query-on-a-mining-model"></a><span data-ttu-id="13b28-102">建立採礦模型內容查詢</span><span class="sxs-lookup"><span data-stu-id="13b28-102">Create a Content Query on a Mining Model</span></span>
  <span data-ttu-id="13b28-103">雖然您可以使用 AMO 或 XML/A，以程式設計方式查詢採礦模型內容，但是使用 DMX 來建立查詢是比較簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="13b28-103">You can query the mining model content programmatically by using AMO or XML/A, but it is easier to create queries by using DMX.</span></span> <span data-ttu-id="13b28-104">您也可以針對資料採礦結構描述資料列集建立查詢，方法是建立與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的連接，然後使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]所提供的 DMV 建立查詢。</span><span class="sxs-lookup"><span data-stu-id="13b28-104">You can also create queries against the data mining schema rowsets by establishing a connection to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and creating a query using the DMVs provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="13b28-105">下列程序示範如何使用 DMX 來針對採礦模型建立查詢，以及如何查詢資料採礦結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="13b28-105">The following procedures demonstrate how to create queries against a mining model by using DMX, and how to query the data mining schema rowsets.</span></span>  
  
 <span data-ttu-id="13b28-106">如需如何使用 XML/A 來建立類似查詢的範例，請參閱 [使用 XMLA 建立資料採礦查詢](create-a-data-mining-query-by-using-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="13b28-106">For an example of how to create a similar query by using XML/A, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="querying-data-mining-model-content-by-using-dmx"></a><span data-ttu-id="13b28-107">使用 DMX 來查詢資料採礦模型內容</span><span class="sxs-lookup"><span data-stu-id="13b28-107">Querying Data Mining Model Content by Using DMX</span></span>  
  
#### <a name="to-create-a-dmx-model-content-query"></a><span data-ttu-id="13b28-108">建立 DMX 模型內容查詢</span><span class="sxs-lookup"><span data-stu-id="13b28-108">To create a DMX model content query</span></span>  
  
1.  <span data-ttu-id="13b28-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。</span><span class="sxs-lookup"><span data-stu-id="13b28-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="13b28-110">在 [範本總管]\*\*\*\* 窗格中，按一下 Cube 圖示，即可變更清單並顯示 Analysis Services 範本。</span><span class="sxs-lookup"><span data-stu-id="13b28-110">In the **Template Explorer** pane, click the cube icon to change the list and display Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="13b28-111">在範本類別目錄的清單中，依序展開 [DMX]\*\*\*\* 和 [模型內容]\*\*\*\*，然後按兩下 [內容查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13b28-111">In the list of template categories, expand **DMX**, expand **Model Content**, and double-click **Content Query**.</span></span>  
  
4.  <span data-ttu-id="13b28-112">在 [連接到 Analysis Services]\*\*\*\* 對話方塊中，選取包含您要查詢之採礦模型的執行個體，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13b28-112">In the **Connect to Analysis Services** dialog box, select the instance that contains the mining model you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="13b28-113">[內容查詢]\*\*\*\* 範本就會在適當的程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="13b28-113">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="13b28-114">[中繼資料] 窗格會列出目前資料庫中可用的模型。</span><span class="sxs-lookup"><span data-stu-id="13b28-114">The metadata pane lists the models that are available in the current database.</span></span> <span data-ttu-id="13b28-115">若要變更資料庫，請從 [可用的資料庫]\*\*\*\* 清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="13b28-115">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
5.  <span data-ttu-id="13b28-116">在 [] 行中輸入採礦模型的名稱 `FROM` *\<mining model, name, MyModel>* `.CONTENT` 。</span><span class="sxs-lookup"><span data-stu-id="13b28-116">Enter the name of a mining model in the line, `FROM` [*\<mining model, name, MyModel>*]`.CONTENT`.</span></span> <span data-ttu-id="13b28-117">如果採礦模型名稱包含空格，您就必須以方括號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="13b28-117">If the mining model name contains spaces, you must enclose the name in brackets.</span></span>  
  
     <span data-ttu-id="13b28-118">如果您不想要輸入名稱，可以在 **物件總管** 中選取採礦模型，然後將它拖曳至範本中。</span><span class="sxs-lookup"><span data-stu-id="13b28-118">If you don't want to type the name, you can select a mining model in **Object Explorer** and drag it into the template.</span></span>  
  
6.  <span data-ttu-id="13b28-119">在這一行中， `SELECT` *\<select list, expr list, \*>* 輸入 [採礦模型內容架構] 資料列集中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="13b28-119">In the line, `SELECT`*\<select list, expr list, \*>*, type the names of columns in the mining model content schema rowset.</span></span>  
  
     <span data-ttu-id="13b28-120">若要檢視您可以在採礦模型內容查詢中傳回的資料行清單，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)所提供的 DMV 建立查詢。</span><span class="sxs-lookup"><span data-stu-id="13b28-120">To view a list of columns that you can return in mining model content queries, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
7.  <span data-ttu-id="13b28-121">(選擇性) 在範本的 WHERE 子句中輸入條件，以便將傳回的資料列限制為特定節點或值。</span><span class="sxs-lookup"><span data-stu-id="13b28-121">Optionally, type a condition in the WHERE clause of the template to restrict the rows returned to specific nodes or values.</span></span>  
  
8.  <span data-ttu-id="13b28-122">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="13b28-122">Click **Execute**.</span></span>  
  
## <a name="querying-the-data-mining-schema-rowsets"></a><span data-ttu-id="13b28-123">查詢資料採礦結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="13b28-123">Querying the Data Mining Schema Rowsets</span></span>  
  
#### <a name="to-create-a-query-against-the-data-mining-schema-rowset"></a><span data-ttu-id="13b28-124">針對資料採礦結構描述資料列集建立查詢</span><span class="sxs-lookup"><span data-stu-id="13b28-124">To create a query against the data mining schema rowset</span></span>  
  
1.  <span data-ttu-id="13b28-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [新增查詢]\*\*\*\* 工具列上，按一下 [Analysis Services DMX 查詢]\*\*\*\* 或 [Analysis Services MDX 查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13b28-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **New Query** toolbar, click **Analysis Services DMX Query**, or **Analysis Services MDX query**.</span></span>  
  
2.  <span data-ttu-id="13b28-126">在 [連接到 Analysis Services]\*\*\*\* 對話方塊中，選取包含您要查詢之物件的執行個體，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13b28-126">In the **Connect to Analysis Services** dialog box, select the instance that contains the objects you want to query, and click **Connect**.</span></span>  
  
     <span data-ttu-id="13b28-127">[內容查詢]\*\*\*\* 範本就會在適當的程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="13b28-127">The **Content Query** template opens in the appropriate code editor.</span></span> <span data-ttu-id="13b28-128">[中繼資料] 窗格會列出目前資料庫中可用的物件。</span><span class="sxs-lookup"><span data-stu-id="13b28-128">The metadata pane lists the objects that are available in the current database.</span></span> <span data-ttu-id="13b28-129">若要變更資料庫，請從 [可用的資料庫]\*\*\*\* 清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="13b28-129">To change the database, select a different database from the **Available Databases** list.</span></span>  
  
3.  <span data-ttu-id="13b28-130">在查詢編輯器中，輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="13b28-130">In the query editor, type the following:</span></span>  
  
     `SELECT *`  
  
     `FROM $system.DMSCHEMA_MINING_MODEL_CONTENT`  
  
     `WHERE MODEL_NAME = '<model name>'`  
  
4.  <span data-ttu-id="13b28-131">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="13b28-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="13b28-132">[結果] 窗格就會顯示模型的內容。</span><span class="sxs-lookup"><span data-stu-id="13b28-132">The Results pane displays the contents of the model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13b28-133">若要檢視您可以針對目前執行個體查詢之所有結構描述資料列集的清單，請使用這個查詢： `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS。</span><span class="sxs-lookup"><span data-stu-id="13b28-133">To view a list of all the schema rowsets that you can query on the current instance, use this query: `SELECT * FROM $system.`DISCOVER_SCHEMA_ROWSETS.</span></span> <span data-ttu-id="13b28-134">或者，如需資料採礦特有之結構描述資料列集的清單，請參閱 [資料採礦結構描述資料列集](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)。</span><span class="sxs-lookup"><span data-stu-id="13b28-134">Or, for a list of schema rowsets specific to data mining, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b28-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13b28-135">See Also</span></span>  
 <span data-ttu-id="13b28-136">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="13b28-136">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="13b28-137">資料採礦結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="13b28-137">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
