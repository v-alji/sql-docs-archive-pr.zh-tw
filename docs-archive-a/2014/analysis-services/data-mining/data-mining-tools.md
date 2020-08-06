---
title: 資料採礦工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tools [Analysis Services]
- mining models [Analysis Services], tools
- data mining [Analysis Services], tools
- data mining [Analysis Services], development
ms.assetid: 003ada6a-0bcd-4f16-8c34-1a9ffc75cd2c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4be2f343f0fb7969f76b63ec1eb1677c1c9e589f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607165"
---
# <a name="data-mining-tools"></a><span data-ttu-id="93ad6-102">資料採礦工具。</span><span class="sxs-lookup"><span data-stu-id="93ad6-102">Data Mining Tools</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="93ad6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供下列工具，可讓您用來建立資料採礦解決方案：</span><span class="sxs-lookup"><span data-stu-id="93ad6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides the following tools that you can use to create data mining solutions:</span></span>  
  
-   <span data-ttu-id="93ad6-104">\*\*\*\* 中的資料採礦精靈 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 可讓您在 Cube 中使用關聯式資料來源或多維度資料，輕鬆建立採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="93ad6-104">The **Data Mining Wizard** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] makes it easy to create mining structures and mining models, using either relational data sources or multidimensional data in cubes.</span></span>  
  
     <span data-ttu-id="93ad6-105">在此精靈中，您會選擇要使用的資料，然後套用特定的資料採礦技術，例如叢集、類神經網路或時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="93ad6-105">In the wizard, you choose data to use, and then apply specific data mining techniques, such as clustering, neural networks, or time series modeling.</span></span>  
  
-   <span data-ttu-id="93ad6-106">\*\*\*\* 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中都有提供模型檢視器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，可讓您在建立採礦模型之後加以探索。</span><span class="sxs-lookup"><span data-stu-id="93ad6-106">**Model viewers** are provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], for exploring your mining models after they are created.</span></span>  <span data-ttu-id="93ad6-107">您可以使用針對每一個演算法所量身打造的檢視器來瀏覽模型，或者可以使用模型內容檢視器深入分析。</span><span class="sxs-lookup"><span data-stu-id="93ad6-107">You can browse models using viewers tailored to each algorithm, or go deeper into analysis by using the model content viewer.</span></span>  
  
-   <span data-ttu-id="93ad6-108">\*\*\*\* 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中都有提供預測查詢產生器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，可幫助您建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="93ad6-108">The **Prediction Query Builder** is provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to help you create prediction queries.</span></span> <span data-ttu-id="93ad6-109">您也可以針對鑑效組資料集或外部資料來測試模型的精確度，或者使用交叉驗證來評估資料集的品質。</span><span class="sxs-lookup"><span data-stu-id="93ad6-109">You can also test the accuracy of models against a holdout data set or external data, or use cross-validation to assess the quality of your data set.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="93ad6-110">是您用來管理現有資料採礦方案的介面，這些方案已經部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="93ad6-110">is the interface where you manage existing data mining solutions that have been deployed to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="93ad6-111">您可以重新處理結構和模型，以更新其中的資料。</span><span class="sxs-lookup"><span data-stu-id="93ad6-111">You can reprocess structures and models to update the data in them.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="93ad6-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]包含可用來清除資料、自動化工作（例如建立預測和更新模型）及建立文字挖掘解決方案的工具。</span><span class="sxs-lookup"><span data-stu-id="93ad6-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains tools that you can use to clean data, to automate tasks such as creating predictions and updating models, and to create text mining solutions.</span></span>  
  
 <span data-ttu-id="93ad6-113">下列章節提供有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中之資料採礦工具的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="93ad6-113">The following sections provide more information about the data mining tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="data-mining-wizard"></a><span data-ttu-id="93ad6-114">資料採礦精靈</span><span class="sxs-lookup"><span data-stu-id="93ad6-114">Data Mining Wizard</span></span>  
 <span data-ttu-id="93ad6-115">使用資料採礦精靈開始建立資料採礦方案。</span><span class="sxs-lookup"><span data-stu-id="93ad6-115">Use the Data Mining Wizard to get started creating data mining solutions.</span></span> <span data-ttu-id="93ad6-116">此精靈非常快速且容易使用，可引導您建立資料採礦結構和初始相關之採礦模型的程序，並包含選取演算法類型和資料來源以及定義案例資料進行分析的工作。</span><span class="sxs-lookup"><span data-stu-id="93ad6-116">The wizard is quick and easy, and guides you through the process of creating a data mining structure and an initial related mining model, and includes the tasks of selecting an algorithm type and a data source, and defining the case data used for analysis.</span></span>  
  
 <span data-ttu-id="93ad6-117">**如需詳細資訊︰** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md) (資料採礦精靈 (Analysis Services - 資料採礦))。</span><span class="sxs-lookup"><span data-stu-id="93ad6-117">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md)</span></span>  
  
## <a name="data-mining-designer"></a><span data-ttu-id="93ad6-118">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="93ad6-118">Data Mining Designer</span></span>  
 <span data-ttu-id="93ad6-119">在您使用資料採礦精靈建立採礦結構和採礦模型之後，您可以從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 使用資料採礦設計師來處理現有的模型與結構。</span><span class="sxs-lookup"><span data-stu-id="93ad6-119">After you have created a mining structure and mining model by using the Data Mining Wizard, you can use the Data Mining Designer from either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to work with existing models and structures.</span></span>  
  
 <span data-ttu-id="93ad6-120">此設計師包含適用於以下工作的工具：</span><span class="sxs-lookup"><span data-stu-id="93ad6-120">The designer includes tools for these tasks:</span></span>  
  
-   <span data-ttu-id="93ad6-121">修改採礦結構的屬性、加入資料行及建立資料行別名、變更分類收納方法或預期的值分佈。</span><span class="sxs-lookup"><span data-stu-id="93ad6-121">Modify the properties of mining structures, add columns and create column aliases, change the binning method or expected distribution of values.</span></span>  
  
-   <span data-ttu-id="93ad6-122">將新的模型加入現有的結構中；複製模型、變更模型屬性或中繼資料，或是定義採礦模型的篩選。</span><span class="sxs-lookup"><span data-stu-id="93ad6-122">Add new models to an existing structure; copy models, change model properties or metadata, or define filters on a mining model.</span></span>  
  
-   <span data-ttu-id="93ad6-123">瀏覽模型中的模式與規則；探索關聯或決策樹。</span><span class="sxs-lookup"><span data-stu-id="93ad6-123">Browse the patterns and rules within the model; explore associations or decision trees.</span></span> <span data-ttu-id="93ad6-124">取得詳細統計資料</span><span class="sxs-lookup"><span data-stu-id="93ad6-124">Get detailed statistics about</span></span>  
  
     <span data-ttu-id="93ad6-125">每一個不同的時間序列模型都會提供自訂檢視器，幫助您分析資料及探索資料採礦所揭露的模式。</span><span class="sxs-lookup"><span data-stu-id="93ad6-125">Custom viewers are provided for each different time of model, to help you analyze your data and explore the patterns revealed by data mining.</span></span>  
  
-   <span data-ttu-id="93ad6-126">藉由建立增益圖或分析模型的收益曲線來驗證模型。</span><span class="sxs-lookup"><span data-stu-id="93ad6-126">Validate models by creating lift charts, or analyzing the profit curve for models.</span></span> <span data-ttu-id="93ad6-127">使用分類矩陣比較模型，或是使用交叉驗證來驗證資料集及其模型。</span><span class="sxs-lookup"><span data-stu-id="93ad6-127">Compare models using classification matrices, or validate a data set and its models by using cross-validation.</span></span>  
  
-   <span data-ttu-id="93ad6-128">針對現有的採礦模型建立預測和內容查詢。</span><span class="sxs-lookup"><span data-stu-id="93ad6-128">Create predictions and content queries against existing mining models.</span></span> <span data-ttu-id="93ad6-129">建立一次性查詢，或是設定查詢來針對外部資料的整個資料表產生預測。</span><span class="sxs-lookup"><span data-stu-id="93ad6-129">Build one-off queries, or set up queries to generate predictions for entire tables of external data.</span></span>  
  
 <span data-ttu-id="93ad6-130">**如需詳細資訊：** [資料採礦設計](data-mining-designer.md)工具</span><span class="sxs-lookup"><span data-stu-id="93ad6-130">**For More Information:** [Data Mining Designer](data-mining-designer.md)</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="93ad6-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="93ad6-131">SQL Server Management Studio</span></span>  
 <span data-ttu-id="93ad6-132">在您建立並將採礦模型部署到伺服器之後，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來管理裝載資料採礦物件的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93ad6-132">After you create and deploy mining models to a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that hosts the data mining objects.</span></span> <span data-ttu-id="93ad6-133">您也可以繼續執行使用此模型的工作，例如瀏覽模型、處理新的資料和建立預測。</span><span class="sxs-lookup"><span data-stu-id="93ad6-133">You can also continue to perform tasks that use the model, such as exploring the models, processing new data, and creating predictions.</span></span>  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="93ad6-134">也包含查詢編輯器，您可以用來設計及執行資料採礦延伸 (DMX) 查詢，或是透過 XMLA 來處理資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="93ad6-134">also contains query editors that you can use to design and execute Data Mining Extensions (DMX) queries, or ot work with data mining objects by using XMLA.</span></span>  
  
## <a name="integration-services-data-mining-tasks-and-transformations"></a><span data-ttu-id="93ad6-135">Integration Services 資料採礦工作和轉換</span><span class="sxs-lookup"><span data-stu-id="93ad6-135">Integration Services Data Mining Tasks and Transformations</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="93ad6-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]提供許多支援資料採礦的元件。</span><span class="sxs-lookup"><span data-stu-id="93ad6-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides many components that support data mining.</span></span>  
  
 <span data-ttu-id="93ad6-137">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的一些工具的目的是為了將常見的資料採礦工作自動化，包括預測、模型建立和處理。</span><span class="sxs-lookup"><span data-stu-id="93ad6-137">Some tools in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] are designed to help automate common data mining tasks, including prediction, model building, and processing.</span></span> <span data-ttu-id="93ad6-138">例如：</span><span class="sxs-lookup"><span data-stu-id="93ad6-138">For example:</span></span>  
  
-   <span data-ttu-id="93ad6-139">建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，每當新的客戶更新資料集時，此封裝都會自動更新模型</span><span class="sxs-lookup"><span data-stu-id="93ad6-139">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that automatically updates the model every time the dataset is updated with new customers</span></span>  
  
-   <span data-ttu-id="93ad6-140">執行案例記錄的自訂分割或自訂取樣。</span><span class="sxs-lookup"><span data-stu-id="93ad6-140">Perform custom segmentation or custom sampling of case records.</span></span>  
  
-   <span data-ttu-id="93ad6-141">根據傳遞的參數自動產生模型。</span><span class="sxs-lookup"><span data-stu-id="93ad6-141">Automatically generate models passed on parameters.</span></span>  
  
 <span data-ttu-id="93ad6-142">但是，您也可以在封裝工作流程中使用資料採礦當做其他處理序的輸入。</span><span class="sxs-lookup"><span data-stu-id="93ad6-142">However, you can also use data mining in a package workflow, as an input to other processes.</span></span> <span data-ttu-id="93ad6-143">例如：</span><span class="sxs-lookup"><span data-stu-id="93ad6-143">For example:</span></span>  
  
-   <span data-ttu-id="93ad6-144">使用模型產生的機率值，針對文字採礦或其他分類工作的分數來加權。</span><span class="sxs-lookup"><span data-stu-id="93ad6-144">Use probability values generated by the model to weight scores for text mining or other classification tasks.</span></span>  
  
-   <span data-ttu-id="93ad6-145">根據之前的資料自動產生預測，並使用這些值來評估新的值的有效性。</span><span class="sxs-lookup"><span data-stu-id="93ad6-145">Automatically generate predictions based on prior data and use those values to assess the validity of new data.</span></span>  
  
-   <span data-ttu-id="93ad6-146">使用羅吉斯迴歸，根據風險區隔送入的客戶。</span><span class="sxs-lookup"><span data-stu-id="93ad6-146">Using logistic regression to segment incoming customers by risk.</span></span>  
  
 <span data-ttu-id="93ad6-147">**如需詳細資訊：** [Related Projects for Data Mining Solutions](data-mining-solutions.md) (資料採礦方案的相關專案)</span><span class="sxs-lookup"><span data-stu-id="93ad6-147">**For More Information:** [Related Projects for Data Mining Solutions](data-mining-solutions.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ad6-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93ad6-148">See Also</span></span>  
 <span data-ttu-id="93ad6-149">[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="93ad6-149">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="93ad6-150">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="93ad6-150">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="93ad6-151">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="93ad6-151">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="93ad6-152">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="93ad6-152">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
