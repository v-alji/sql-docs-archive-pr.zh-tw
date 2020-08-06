---
title: 定義資料來源視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d59c5fbe5fd4a07596745447567a72499ddabd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584797"
---
# <a name="defining-a-data-source-view"></a><span data-ttu-id="03c81-102">定義資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="03c81-102">Defining a Data Source View</span></span>
  <span data-ttu-id="03c81-103">定義您在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案中使用的資料來源之後，下一個步驟通常是定義專案的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-103">After you define the data sources that you will use in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, the next step is generally to define a data source view for the project.</span></span> <span data-ttu-id="03c81-104">資料來源檢視是資料來源在專案中定義之指定資料表和檢視的中繼資料的單一統一檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-104">A data source view is a single, unified view of the metadata from the specified tables and views that the data source defines in the project.</span></span> <span data-ttu-id="03c81-105">在資料來源檢視中儲存中繼資料可讓您在開發期間使用中繼資料，而不需要開啟與任何基礎資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="03c81-105">Storing the metadata in the data source view enables you to work with the metadata during development without an open connection to any underlying data source.</span></span> <span data-ttu-id="03c81-106">如需詳細資訊，請參閱 [多維度模型中的資料來源檢視](multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="03c81-106">For more information, see [Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="03c81-107">在下列工作中，您可以定義一個包含 **AdventureWorksDW2012** 資料來源的 5 個資料表的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-107">In the following task, you define a data source view that includes five tables from the **AdventureWorksDW2012** data source.</span></span>  
  
### <a name="to-define-a-new-data-source-view"></a><span data-ttu-id="03c81-108">若要定義新的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="03c81-108">To define a new data source view</span></span>  
  
1.  <span data-ttu-id="03c81-109">在方案總管中 (於 [Microsoft Visual Studio] 視窗右側)，以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\*，然後按一下 [新增資料來源檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03c81-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Source Views**, and then click **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="03c81-110">在 [歡迎使用資料來源檢視精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="03c81-110">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span> <span data-ttu-id="03c81-111">此時會出現 [選取資料來源]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="03c81-111">The **Select a Data Source** page appears.</span></span>  
  
3.  <span data-ttu-id="03c81-112">在 [關聯式資料來源]\*\*\*\* 底下，已選取 [Adventure Works DW 2012]\*\*\*\* 資料來源。</span><span class="sxs-lookup"><span data-stu-id="03c81-112">Under **Relational data sources**, the **Adventure Works DW 2012** data source is selected.</span></span> <span data-ttu-id="03c81-113">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="03c81-113">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03c81-114">若要建立依據多個資料來源的資料來源檢視，首先要定義一個依據單一資料來源的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-114">To create a data source view that is based on multiple data sources, first define a data source view that is based on a single data source.</span></span> <span data-ttu-id="03c81-115">這個資料來源稱為主要資料來源。</span><span class="sxs-lookup"><span data-stu-id="03c81-115">This data source is then called the primary data source.</span></span> <span data-ttu-id="03c81-116">然後您可以從次要資料來源加入資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-116">You can then add tables and views from a secondary data source.</span></span> <span data-ttu-id="03c81-117">當您根據多個資料來源中的相關資料表設計包含屬性的維度時，可能需要將 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料來源定義為主要資料來源，才能使用其分散式查詢引擎功能。</span><span class="sxs-lookup"><span data-stu-id="03c81-117">When designing dimensions that contain attributes based on related tables in multiple data sources, you might need to define a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source as the primary data source to use its distributed query engine capabilities.</span></span>  
  
4.  <span data-ttu-id="03c81-118">在 [選取資料表和檢視表]\*\*\*\* 頁面上，從所選取資料來源提供的物件清單中選取資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="03c81-118">On the **Select Tables and Views** page, select tables and views from the list of objects that are available from the selected data source.</span></span> <span data-ttu-id="03c81-119">您可以篩選這份清單來幫助您選取資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="03c81-119">You can filter this list to help you select tables and views.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="03c81-120">按一下右上角的最大化按鈕，如此視窗就會涵蓋全螢幕。</span><span class="sxs-lookup"><span data-stu-id="03c81-120">Click the maximize button in the upper-right corner so that the window covers the full screen.</span></span> <span data-ttu-id="03c81-121">這樣做可讓您更輕易地查看完整的可用物件清單。</span><span class="sxs-lookup"><span data-stu-id="03c81-121">This makes it easier to see the complete list of available objects.</span></span>  
  
     <span data-ttu-id="03c81-122">在 [可用的物件]\*\*\*\* 清單中，選取下列物件。</span><span class="sxs-lookup"><span data-stu-id="03c81-122">In the **Available objects** list, select the following objects.</span></span> <span data-ttu-id="03c81-123">您可以在按住 CTRL 鍵的同時，按一下每個資料表，藉以選取多個資料表：</span><span class="sxs-lookup"><span data-stu-id="03c81-123">You can select multiple tables by clicking each while holding down the CTRL key:</span></span>  
  
    -   <span data-ttu-id="03c81-124">**DimCustomer (dbo)**</span><span class="sxs-lookup"><span data-stu-id="03c81-124">**DimCustomer (dbo)**</span></span>  
  
    -   <span data-ttu-id="03c81-125">**DimDate (dbo)**</span><span class="sxs-lookup"><span data-stu-id="03c81-125">**DimDate (dbo)**</span></span>  
  
    -   <span data-ttu-id="03c81-126">**DimGeography (dbo)**</span><span class="sxs-lookup"><span data-stu-id="03c81-126">**DimGeography (dbo)**</span></span>  
  
    -   <span data-ttu-id="03c81-127">**DimProduct (dbo)**</span><span class="sxs-lookup"><span data-stu-id="03c81-127">**DimProduct (dbo)**</span></span>  
  
    -   <span data-ttu-id="03c81-128">**FactInternetSales (dbo)**</span><span class="sxs-lookup"><span data-stu-id="03c81-128">**FactInternetSales (dbo)**</span></span>  
  
5.  <span data-ttu-id="03c81-129">按一下 **>** 即可將選取的資料表加入至 [**包含的物件**] 清單。</span><span class="sxs-lookup"><span data-stu-id="03c81-129">Click **>** to add the selected tables to the **Included objects** list.</span></span>  
  
6.  <span data-ttu-id="03c81-130">按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="03c81-130">Click **Next.**</span></span>  
  
7.  <span data-ttu-id="03c81-131">在 [名稱] 欄位中，確認有顯示 [Adventure Works DW 2012]\*\*\*\*，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03c81-131">In the Name field, make sure **Adventure Works DW 2012** displays, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="03c81-132">[Adventure Works DW 2012]\*\*\*\* 資料來源檢視會出現在方案總管的 [資料來源檢視]\*\*\*\* 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="03c81-132">The **Adventure Works DW 2012** data source view appears in the **Data Source Views** folder in Solution Explorer.</span></span> <span data-ttu-id="03c81-133">資料來源檢視的內容也會顯示在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的 [資料來源檢視設計工具] 中。</span><span class="sxs-lookup"><span data-stu-id="03c81-133">The content of the data source view is also displayed in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="03c81-134">這個設計師包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="03c81-134">This designer contains the following elements:</span></span>  
  
    -   <span data-ttu-id="03c81-135">[圖表]\*\*\*\* 窗格，以圖形表示資料表及其關聯性。</span><span class="sxs-lookup"><span data-stu-id="03c81-135">A **Diagram** pane in which the tables and their relationships are represented graphically.</span></span>  
  
    -   <span data-ttu-id="03c81-136">[資料表]\*\*\*\* 窗格，以樹狀檢視顯示資料表及其結構描述元素。</span><span class="sxs-lookup"><span data-stu-id="03c81-136">A **Tables** pane in which the tables and their schema elements are displayed in a tree view.</span></span>  
  
    -   <span data-ttu-id="03c81-137">[圖表組合管理]\*\*\*\* 窗格，可讓您建立子圖表來檢視資料來源檢視的子集。</span><span class="sxs-lookup"><span data-stu-id="03c81-137">A **Diagram Organizer** pane in which you can create subdiagrams so that you can view subsets of the data source view.</span></span>  
  
    -   <span data-ttu-id="03c81-138">[資料來源檢視設計工具] 特有的工具列。</span><span class="sxs-lookup"><span data-stu-id="03c81-138">A toolbar that is specific to Data Source View Designer.</span></span>  
  
8.  <span data-ttu-id="03c81-139">若要最大化 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 開發環境，請按一下 [最大化]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="03c81-139">To maximize the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment, click the **Maximize** button.</span></span>  
  
9. <span data-ttu-id="03c81-140">若要以 50% 的大小檢視 [圖表]\*\*\*\* 窗格中的資料表，請按一下 [資料來源檢視設計工具] 工具列上的**顯示比例**圖示。</span><span class="sxs-lookup"><span data-stu-id="03c81-140">To view the tables in the **Diagram** pane at 50 percent, click the **Zoom** icon on the Data Source View Designer toolbar.</span></span> <span data-ttu-id="03c81-141">這樣會隱藏每一個資料表的資料行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="03c81-141">This will hide the column details of each table.</span></span>  
  
10. <span data-ttu-id="03c81-142">若要隱藏方案總管，請按一下 [自動隱藏]\*\*\*\* 按鈕，它是標題列上的圖釘圖示。</span><span class="sxs-lookup"><span data-stu-id="03c81-142">To hide Solution Explorer, click the **Auto Hide** button, which is the pushpin icon on the title bar.</span></span> <span data-ttu-id="03c81-143">若要再次檢視 [方案總管]，請沿著開發環境的右側將指標定位在 [方案總管] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="03c81-143">To view Solution Explorer again, position your pointer over the Solution Explorer tab along the right side of the development environment.</span></span> <span data-ttu-id="03c81-144">若要取消隱藏方案總管，請再按一次 [自動隱藏]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="03c81-144">To unhide Solution Explorer, click the **Auto Hide** button again.</span></span>  
  
11. <span data-ttu-id="03c81-145">如果視窗預設並未隱藏，請按一下 [屬性] 視窗和方案總管視窗標題列上的 [自動隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03c81-145">If the windows are not hidden by default, click **Auto Hide** on the title bar of the Properties and Solution Explorer windows.</span></span>  
  
     <span data-ttu-id="03c81-146">現在您可以在 [圖表]\*\*\*\* 窗格中檢視所有資料表及其關聯性。</span><span class="sxs-lookup"><span data-stu-id="03c81-146">You can now view all the tables and their relationships in the **Diagram** pane.</span></span> <span data-ttu-id="03c81-147">請注意，FactInternetSales 資料表和 DimDate 資料表之間有 3 種關聯性。</span><span class="sxs-lookup"><span data-stu-id="03c81-147">Notice that there are three relationships between the FactInternetSales table and the DimDate table.</span></span> <span data-ttu-id="03c81-148">每一個銷售都有 3 個相關的銷售日期：訂購日期、截止日期和出貨日期。</span><span class="sxs-lookup"><span data-stu-id="03c81-148">Each sale has three dates associated with the sale: an order date, a due date, and a ship date.</span></span> <span data-ttu-id="03c81-149">若要檢視任何關聯性的詳細資料，請按兩下 [圖表]\*\*\*\* 窗格內的關聯性箭頭。</span><span class="sxs-lookup"><span data-stu-id="03c81-149">To view the details of any relationship, double-click the relationship arrow in the **Diagram** pane.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="03c81-150">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="03c81-150">Next Task in Lesson</span></span>  
 [<span data-ttu-id="03c81-151">修改預設資料表名稱</span><span class="sxs-lookup"><span data-stu-id="03c81-151">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a><span data-ttu-id="03c81-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03c81-152">See Also</span></span>  
 [<span data-ttu-id="03c81-153">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="03c81-153">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
