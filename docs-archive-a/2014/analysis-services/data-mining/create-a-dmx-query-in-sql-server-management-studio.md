---
title: 在 SQL Server Management Studio 中建立 DMX 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20fc7a618f4977058203d8f35d235b543609dd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597459"
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="cec7b-102">在 SQL Server Management Studio 中建立 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="cec7b-102">Create a DMX Query in SQL Server Management Studio</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cec7b-103">提供一組功能，可幫助您針對採礦模型和採礦結構建立預測查詢、內容查詢和資料定義查詢。</span><span class="sxs-lookup"><span data-stu-id="cec7b-103">provides a set of features to help you create prediction queries, content queries, and data definition queries against mining models and mining structures.</span></span>  
  
-   <span data-ttu-id="cec7b-104">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中都有提供圖形化預測查詢產生器，可簡化撰寫預測查詢以及將資料集對應至模型的程序。</span><span class="sxs-lookup"><span data-stu-id="cec7b-104">The graphical Prediction Query Builder is available in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], to simplify the process of writing prediction queries and mapping data sets to a model.</span></span>  
  
-   <span data-ttu-id="cec7b-105">[範本總管] 中所提供的查詢範本會開始建立許多種類的 DMX 查詢，包括許多類型的預測查詢。</span><span class="sxs-lookup"><span data-stu-id="cec7b-105">The query templates provided in the Template Explorer jump-start the creation of many kinds of DMX queries, including many types of prediction queries.</span></span> <span data-ttu-id="cec7b-106">內容查詢、使用巢狀資料集的查詢、從採礦結構傳回案例的查詢，甚至是資料定義查詢都有提供範本。</span><span class="sxs-lookup"><span data-stu-id="cec7b-106">Templates are provided for content queries, queries used nested data sets, queries that return cases from the mining structure, and even data definition queries.</span></span>  
  
-   <span data-ttu-id="cec7b-107">MDX 和 DMX 查詢窗格中的 [中繼資料總管] 會提供可用模型和結構的清單 (您可以將其拖放到查詢產生器) 及 DMX 函數的清單。</span><span class="sxs-lookup"><span data-stu-id="cec7b-107">The Metadata Explorer in the MDX and DMX query panes provides a list of available models and structures that you can drag and drop into the query builder, as well as a list of DMX functions.</span></span> <span data-ttu-id="cec7b-108">這項功能可讓您輕鬆獲得正確的物件名稱，而不需要輸入。</span><span class="sxs-lookup"><span data-stu-id="cec7b-108">This feature makes it easy to get object names right, without typing.</span></span>  
  
 <span data-ttu-id="cec7b-109">本主題描述如何使用 [中繼資料總管] 和 DMX 查詢編輯器來建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="cec7b-109">This topic describes how to build a DMX query by using the Metadata Explorer and the DMX query editor.</span></span>  
  
##  <a name="dmx-query-templates"></a><a name="BKMK_Templates"></a><span data-ttu-id="cec7b-110">DMX 查詢範本</span><span class="sxs-lookup"><span data-stu-id="cec7b-110">DMX Query Templates</span></span>  
 <span data-ttu-id="cec7b-111">[範本總管] 有提供用來建立基本 DMX 查詢的範本。</span><span class="sxs-lookup"><span data-stu-id="cec7b-111">Templates for creating basic DMX queries are available in Template Explorer.</span></span> <span data-ttu-id="cec7b-112">[DMX]\*\*\*\* 資料夾包含資料採礦範本，這些範本分成以下類別：</span><span class="sxs-lookup"><span data-stu-id="cec7b-112">The **DMX** folder contains data mining templates, which are divided into these categories:</span></span>  
  
-   <span data-ttu-id="cec7b-113">**模型內容**</span><span class="sxs-lookup"><span data-stu-id="cec7b-113">**Model Content**</span></span>  
  
-   <span data-ttu-id="cec7b-114">**模型管理**</span><span class="sxs-lookup"><span data-stu-id="cec7b-114">**Model Management**</span></span>  
  
-   <span data-ttu-id="cec7b-115">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="cec7b-115">**Prediction Queries**</span></span>  
  
-   <span data-ttu-id="cec7b-116">**結構內容**</span><span class="sxs-lookup"><span data-stu-id="cec7b-116">**Structure Content**</span></span>  
  
 <span data-ttu-id="cec7b-117">您也可以針對經常執行的查詢或命令建立自訂範本。</span><span class="sxs-lookup"><span data-stu-id="cec7b-117">You can also create custom templates, for queries or commands that you run frequently.</span></span>  
  
## <a name="xmla-query-templates"></a><span data-ttu-id="cec7b-118">XMLA 查詢範本</span><span class="sxs-lookup"><span data-stu-id="cec7b-118">XMLA Query Templates</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="cec7b-119">也提供 XMLA 查詢的範本。</span><span class="sxs-lookup"><span data-stu-id="cec7b-119">also provides templates for XMLA queries.</span></span>  
  
 <span data-ttu-id="cec7b-120">您可以使用 XMLA 和 DMX 執行的查詢類型之間有一些重疊。</span><span class="sxs-lookup"><span data-stu-id="cec7b-120">There is some overlap between the types of queries that you can perform by using XMLA and DMX.</span></span> <span data-ttu-id="cec7b-121">例如，您可以使用 DMX 或資料採礦結構描述資料列集來建立某些模型內容查詢，但是結構描述資料列集有時會包含未在 DMX 內容查詢中公開的資訊。</span><span class="sxs-lookup"><span data-stu-id="cec7b-121">For example, you can create some model content queries by using either DMX or the data mining schema rowsets, but the schema rowsets sometimes contain information that is not exposed in DMX content queries.</span></span>  
  
 <span data-ttu-id="cec7b-122">在 DMX 和 XMLA 中處理作業的方式也有一些重大差異。</span><span class="sxs-lookup"><span data-stu-id="cec7b-122">There are also some key differences in the way that operations are handled in DMX and in XMLA.</span></span> <span data-ttu-id="cec7b-123">例如，您可以使用 XMLA 來執行管理作業 (例如備份整個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫)，但是如果您要備份單一採礦模型，DMX 會提供單一命令 [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx)，這個命令比較適合這個用途。</span><span class="sxs-lookup"><span data-stu-id="cec7b-123">For example, you can use XMLA to perform administrative operations such as backup of an entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but if you want to back up a single mining model, DMX provides a simple command, [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx), that is better suited to that purpose.</span></span>  
  
##  <a name="build-and-run-a-dmx-query"></a><a name="BKMK_Building_Queries"></a><span data-ttu-id="cec7b-124">建立並執行 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="cec7b-124">Build and Run a DMX Query</span></span>  
  
#### <a name="open-a-new-dmx-query-window"></a><span data-ttu-id="cec7b-125">開啟新的 DMX 查詢視窗</span><span class="sxs-lookup"><span data-stu-id="cec7b-125">Open a new DMX Query window</span></span>  
  
1.  <span data-ttu-id="cec7b-126">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中按一下 [新增查詢]\*\*\*\*，然後選取 [新增 Analysis Server DMX 查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cec7b-126">Click **New Query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then select **New Analysis Server DMX Query**.</span></span>  
  
2.  <span data-ttu-id="cec7b-127">當 [連接到伺服器]\*\*\*\* 對話方塊出現時，請選取 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，其中包含您要使用的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="cec7b-127">When the **Connect to Server** dialog box appears, select the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining models you want to work with.</span></span>  
  
#### <a name="open-template-explorer"></a><span data-ttu-id="cec7b-128">開啟範本總管</span><span class="sxs-lookup"><span data-stu-id="cec7b-128">Open Template Explorer</span></span>  
  
1.  <span data-ttu-id="cec7b-129">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [檢視]\*\*\*\* 功能表上，選取 [範本總管]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cec7b-129">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="cec7b-130">按一下 [Analysis Server]\*\*\*\*，即可查看要套用至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 之範本的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="cec7b-130">Click **Analysis Server** to see a tree view of the templates that apply to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="apply-a-template-to-build-a-query"></a><span data-ttu-id="cec7b-131">套用範本來建立查詢</span><span class="sxs-lookup"><span data-stu-id="cec7b-131">Apply a template to build a query</span></span>  
  
-   <span data-ttu-id="cec7b-132">以滑鼠右鍵按一下適當的查詢類型，然後選取 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cec7b-132">Right-click the appropriate query type and select **Open**.</span></span>  
  
-   <span data-ttu-id="cec7b-133">或者將範本拖曳到查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="cec7b-133">Or, drag the template into the query editor.</span></span>  
  
-   <span data-ttu-id="cec7b-134">您也可以使用 [查詢]\*\*\*\* 功能表上的 [指定參數值]\*\*\*\* 選項，填入查詢的參數。</span><span class="sxs-lookup"><span data-stu-id="cec7b-134">You can also fill in the parameters for the query by using the option, **Specify Values for Parameters**, from the **Query** menu.</span></span>  
  
 <span data-ttu-id="cec7b-135">如需如何從範本建立特定查詢類型的範例，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="cec7b-135">For examples of how to create specific types of queries from templates, see the following topics:</span></span>  
  
 [<span data-ttu-id="cec7b-136">根據範本建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="cec7b-136">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
  
 [<span data-ttu-id="cec7b-137">建立採礦模型內容查詢</span><span class="sxs-lookup"><span data-stu-id="cec7b-137">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="cec7b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec7b-138">See Also</span></span>  
 <span data-ttu-id="cec7b-139">[資料採礦查詢介面](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="cec7b-139">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="cec7b-140">資料採礦延伸模組 &#40;DMX&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="cec7b-140">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
