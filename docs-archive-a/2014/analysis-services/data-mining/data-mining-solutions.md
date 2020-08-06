---
title: 資料採礦解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0ab4b5ddcc9958fa36d6c8ecae0e7fd79585b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594845"
---
# <a name="data-mining-solutions"></a><span data-ttu-id="b01a5-102">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="b01a5-102">Data Mining Solutions</span></span>
  <span data-ttu-id="b01a5-103">資料採礦方案是包含一個或多個資料採礦專案的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="b01a5-103">A data mining solution is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution that contains one or more data mining projects.</span></span>  
  
 <span data-ttu-id="b01a5-104">本節中的主題提供有關如何使用來設計和執行整合式資料採礦解決方案的資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b01a5-104">The topics in this section provide information about how to design and implement an integrated data mining solution by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b01a5-105">如需資料採礦設計程序與相關工具的概觀，請參閱 [資料採礦概念](data-mining-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="b01a5-105">For an overview of the data mining design process and related tools, see [Data Mining Concepts](data-mining-concepts.md).</span></span>  
  
 <span data-ttu-id="b01a5-106">如需有關對資料採礦非常實用之其他專案類型的詳細資訊，請參閱 [資料採礦方案的相關專案](data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="b01a5-106">For more information about additional projects types that are useful for data mining, see [Related Projects for Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
 [<span data-ttu-id="b01a5-107">關聯式與多維度方案的比較</span><span class="sxs-lookup"><span data-stu-id="b01a5-107">Relational vs. Multidimensional Solutions</span></span>](#bkmk_RelMD)  
  
 [<span data-ttu-id="b01a5-108">部署資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="b01a5-108">Deploying Data Mining Solutions</span></span>](#bkmk_Deploy)  
  
 [<span data-ttu-id="b01a5-109">方案逐步解說</span><span class="sxs-lookup"><span data-stu-id="b01a5-109">Solution Walkthroughs</span></span>](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a><span data-ttu-id="b01a5-110">關聯式與多維度方案的比較</span><span class="sxs-lookup"><span data-stu-id="b01a5-110">Relational vs. Multidimensional Solutions</span></span>  
 <span data-ttu-id="b01a5-111">資料採礦解決方案可以根據多維度資料（也就是現有的 cube）或單純的關聯式資料（例如資料倉儲中的資料表和觀點，或是文字檔、Excel 活頁簿或其他外部資料源）。</span><span class="sxs-lookup"><span data-stu-id="b01a5-111">A data mining solution can be based either on multidimensional data-that is, an existing cube-or on purely relational data, such as the tables and views in a data warehouse, or on text files, Excel workbooks, or other external data sources.</span></span>  
  
-   <span data-ttu-id="b01a5-112">您可以在現有的多維度資料庫方案內建立資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="b01a5-112">You can create data mining objects within an existing multidimensional database solution.</span></span>  
  
     <span data-ttu-id="b01a5-113">一般來說，如果您已經建立 Cube 而且想要使用此 Cube 當做資料來源來執行資料採礦，您就會建立這樣的方案。</span><span class="sxs-lookup"><span data-stu-id="b01a5-113">Typically you would create a solution like this if you have already created a cube and want to perform data mining by using the cube as a data source.</span></span> <span data-ttu-id="b01a5-114">當您移動和備份以 Cube 為基礎的模型時，也必須移動或複製此 Cube。</span><span class="sxs-lookup"><span data-stu-id="b01a5-114">When you move and backup models based on a cube, the cube must also be moved or copied.</span></span>  
  
-   <span data-ttu-id="b01a5-115">您可以建立只包含資料採礦物件 (包括支援的資料來源和資料來源檢視) 而且只使用關聯式資料來源的資料採礦方案。</span><span class="sxs-lookup"><span data-stu-id="b01a5-115">You can create a data mining solution that contains only data mining objects, including the supporting data sources and data source views, and that uses relational data source only.</span></span>  
  
     <span data-ttu-id="b01a5-116">這是建立資料採礦模型的慣用方法，因為通常針對關聯式資料來源時，處理和查詢會最快速。</span><span class="sxs-lookup"><span data-stu-id="b01a5-116">This is the preferred method for creating data mining models, as processing and querying is generally fastest against relational data sources.</span></span> <span data-ttu-id="b01a5-117">您也可以使用 EXPORT 和 IMPORT 命令，輕鬆地在伺服器之間移動和備份模型。</span><span class="sxs-lookup"><span data-stu-id="b01a5-117">You can also easily move and backup models between servers by using the EXPORT and IMPORT commands.</span></span>  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a><span data-ttu-id="b01a5-118">部署資料採礦解決方案</span><span class="sxs-lookup"><span data-stu-id="b01a5-118">Deploying Data Mining Solutions</span></span>  
 <span data-ttu-id="b01a5-119">部署方案的目標 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體必須在支援多維度物件和資料採礦物件的模式下執行；也就是說，您不能將資料採礦物件部署到裝載表格式模型或 PowerPivot 資料的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b01a5-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="b01a5-120">因此，當您在 Visual Studio 中建立資料採礦方案時，請務必使用 [Analysis Services 多維度和資料採礦專案]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="b01a5-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="b01a5-121">當您部署方案時，用於資料採礦的物件會在指定的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中建立 (位於與方案檔同名的資料庫中)。</span><span class="sxs-lookup"><span data-stu-id="b01a5-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
 <span data-ttu-id="b01a5-122">如需有關如何部署關聯式和多維度方案的詳細資訊，請參閱 [部署資料採礦方案](deployment-of-data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="b01a5-122">For more information about how to deploy both relational and multidimensional solutions, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a> <span data-ttu-id="b01a5-123">方案逐步解說</span><span class="sxs-lookup"><span data-stu-id="b01a5-123">Solution Walkthrough</span></span>  
 <span data-ttu-id="b01a5-124">提供如何使用資料採礦精靈建立資料採礦方案的概觀。</span><span class="sxs-lookup"><span data-stu-id="b01a5-124">Provides an overview of how to create data mining solutions by using the Data Mining Wizard.</span></span>  
  
 [<span data-ttu-id="b01a5-125">建立關聯式採礦結構</span><span class="sxs-lookup"><span data-stu-id="b01a5-125">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="b01a5-126">從關聯式資料、文字檔以及可以結合在資料來源檢視中的其他來源建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="b01a5-126">Create a mining structure from relational data, text files, and other sources that can be combined in a data source view.</span></span>  
  
 [<span data-ttu-id="b01a5-127">建立 OLAP 採礦結構</span><span class="sxs-lookup"><span data-stu-id="b01a5-127">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="b01a5-128">建立以 OLAP Cube 中的資料為根據的採礦結構</span><span class="sxs-lookup"><span data-stu-id="b01a5-128">Create a mining structure based on data in an OLAP cube.</span></span> <span data-ttu-id="b01a5-129">您從 OLAP 資料建立的模型可以儲存為資料採礦維度，或者可以將此資料集和模型儲存為新的 Cube。</span><span class="sxs-lookup"><span data-stu-id="b01a5-129">Models that you create from OLAP data can be saved as a data mining dimension, or you can save the set of data and your models as a new cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b01a5-130">本節內容</span><span class="sxs-lookup"><span data-stu-id="b01a5-130">In This Section</span></span>  
 [<span data-ttu-id="b01a5-131">資料採礦專案</span><span class="sxs-lookup"><span data-stu-id="b01a5-131">Data Mining Projects</span></span>](data-mining-projects.md)  
  
 [<span data-ttu-id="b01a5-132">處理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="b01a5-132">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)  
  
 [<span data-ttu-id="b01a5-133">資料採礦方案的相關專案</span><span class="sxs-lookup"><span data-stu-id="b01a5-133">Related Projects for Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
 [<span data-ttu-id="b01a5-134">部署資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="b01a5-134">Deployment of Data Mining Solutions</span></span>](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a><span data-ttu-id="b01a5-135">相關工作和主題</span><span class="sxs-lookup"><span data-stu-id="b01a5-135">Related Tasks and Topics</span></span>  
 <span data-ttu-id="b01a5-136">在您建立基本的資料採礦方案 (包括資料來源和採礦結構) 之後，您可以在此方案上加入新的模型、測試和比較模型、建立預測及試驗資料子集來進行建置。</span><span class="sxs-lookup"><span data-stu-id="b01a5-136">After you have created a basic data mining solution, including data sources and a mining structure, you can build on the solution by adding new models, testing and comparing models, creating predictions, and experimenting with subsets of data.</span></span>  
  
 <span data-ttu-id="b01a5-137">如需詳細資訊，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="b01a5-137">For more information, see the following links:</span></span>  
  
|<span data-ttu-id="b01a5-138">工作</span><span class="sxs-lookup"><span data-stu-id="b01a5-138">Tasks</span></span>|<span data-ttu-id="b01a5-139">主題</span><span class="sxs-lookup"><span data-stu-id="b01a5-139">Topics</span></span>|  
|-----------|------------|  
|<span data-ttu-id="b01a5-140">測試您建立的模型、驗證定型資料的品質，然後建立代表資料採礦模型精確度的圖表。</span><span class="sxs-lookup"><span data-stu-id="b01a5-140">Test the models you create, validate the quality of your training data, and create charts that represent the accuracy of data mining models.</span></span>|[<span data-ttu-id="b01a5-141">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b01a5-141">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)|  
|<span data-ttu-id="b01a5-142">將資料填入結構和相關模型中來定型模型。</span><span class="sxs-lookup"><span data-stu-id="b01a5-142">Train the model by populating the structure and related models with data.</span></span> <span data-ttu-id="b01a5-143">使用新的資料來更新和擴充模型。</span><span class="sxs-lookup"><span data-stu-id="b01a5-143">Update and extend models with new data.</span></span>|[<span data-ttu-id="b01a5-144">處理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="b01a5-144">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)|  
|<span data-ttu-id="b01a5-145">將篩選套用到定型資料、選擇不同的演算法或是設定進階演算法參數來自訂採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b01a5-145">Customize a mining model by applying filters to the training data, choosing a different algorithm, or setting advanced algorithm parameters.</span></span>|[<span data-ttu-id="b01a5-146">自訂採礦模型和結構</span><span class="sxs-lookup"><span data-stu-id="b01a5-146">Customize Mining Models and Structure</span></span>](customize-mining-models-and-structure.md)|  
|<span data-ttu-id="b01a5-147">將篩選套用到定型模式時所使用的資料來自訂採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b01a5-147">Customize a mining model by applying filters to the data used in training the mode.</span></span>|[<span data-ttu-id="b01a5-148">將採礦模型加入結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b01a5-148">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|<span data-ttu-id="b01a5-149">更新和管理資料採礦方案。</span><span class="sxs-lookup"><span data-stu-id="b01a5-149">Update and manage data mining solutions.</span></span>|<span data-ttu-id="b01a5-150">Link TBD</span><span class="sxs-lookup"><span data-stu-id="b01a5-150">Link TBD</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b01a5-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b01a5-151">See Also</span></span>  
 [<span data-ttu-id="b01a5-152">資料採礦教學課程 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b01a5-152">Data Mining Tutorials &#40;Analysis Services&#41;</span></span>](../data-mining-tutorials-analysis-services.md)  
  
  
