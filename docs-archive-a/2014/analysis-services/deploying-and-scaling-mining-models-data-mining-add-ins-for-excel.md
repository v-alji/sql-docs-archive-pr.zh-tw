---
title: " (適用于 Excel 的資料採礦增益集) 部署和調整採礦模型 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- manage
ms.assetid: 4c617375-6b01-4a71-9680-de0cbf2cff05
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd2839144d4d1667da09830aaabd1ec3f17a9c21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598051"
---
# <a name="deploying-and-scaling-mining-models-data-mining-add-ins-for-excel"></a><span data-ttu-id="6bc7c-102">部署及調整採礦模型 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="6bc7c-102">Deploying and Scaling Mining Models (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="6bc7c-103">**模型使用**方式和**管理**群組中的工具可協助您管理和流覽現有的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-103">The tools in the **Model Usage** and **Management** group are provided to help you manage and browse existing mining models.</span></span> <span data-ttu-id="6bc7c-104">您可以使用這些工具，檢視儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上的任何模型，而不單只限使用增益集建立的模型。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-104">You can use these tools to view any models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], not just those created using the add-ins.</span></span>  
  
 <span data-ttu-id="6bc7c-105">如果您有必要的權限，可以在不離開 Excel 的情況下，刪除、修改、重新命名或處理現有的採礦模型和結構。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-105">If you have the necessary permissions, you can delete, modify, rename, or process existing mining models and structures without leaving Excel.</span></span>  
  
## <a name="model-usage-toolbar"></a><span data-ttu-id="6bc7c-106">模型使用方式工具列</span><span class="sxs-lookup"><span data-stu-id="6bc7c-106">Model Usage Toolbar</span></span>  
  
### <a name="browse"></a><span data-ttu-id="6bc7c-107">瀏覽</span><span class="sxs-lookup"><span data-stu-id="6bc7c-107">Browse</span></span>  
 <span data-ttu-id="6bc7c-108">使用 [**流覽**嚮導] 來選取現有的資料採礦模型，然後在包含多個圖形和工具的檢視器中，查看並流覽此模型。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-108">Use the **Browse** wizard to select an existing data mining model, and then view and explore the model in a viewer that contains multiple graphs and tools.</span></span>  
  
 <span data-ttu-id="6bc7c-109">如需詳細資訊，請參閱[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-109">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="document-model"></a><span data-ttu-id="6bc7c-110">文件模型</span><span class="sxs-lookup"><span data-stu-id="6bc7c-110">Document Model</span></span>  
 <span data-ttu-id="6bc7c-111">按一下 [**檔模型**] 以啟動精靈，以建立您所建立之「採礦結構」和「採礦模型」的報表。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-111">Click **Document Model** to start a wizard that creates a report of the mining structures and mining models that you have created.</span></span> <span data-ttu-id="6bc7c-112">您可以建立基本報表或進階報表。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-112">You can create basic or advanced reports.</span></span> <span data-ttu-id="6bc7c-113">報表包含了資料行和模型中繼資料，因此對於記載您的工作及追蹤模型內的變更非常實用。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-113">The reports include column and model metadata, so are useful for documenting your work and tracking changes in models.</span></span>  
  
 <span data-ttu-id="6bc7c-114">如需詳細資訊，請參閱[記載 &#40;適用于 Excel 的資料採礦增益集&#41;的採礦模型](documenting-mining-models-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-114">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
### <a name="query"></a><span data-ttu-id="6bc7c-115">查詢</span><span class="sxs-lookup"><span data-stu-id="6bc7c-115">Query</span></span>  
 <span data-ttu-id="6bc7c-116">按一下 [**查詢**]，啟動 [**查詢**嚮導]。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-116">Click **Query** to start the **Query** wizard.</span></span> <span data-ttu-id="6bc7c-117">此精靈將以互動方式帶領您逐步完成針對現有資料採礦模型建立預測查詢的程序。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-117">The wizard interactively walks you through the process of creating a prediction query against an existing data mining model.</span></span>  
  
 <span data-ttu-id="6bc7c-118">若要進一步自訂查詢，或建立不包含在 wizard 中的查詢，只要按一下 [ **Advanced** ] 按鈕即可啟動 [**資料採礦查詢進階編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-118">To further customize the query, or build queries not included in the wizard, just click the **Advanced** button to start the **Data Mining Query Advanced Editor**.</span></span>  
  
 <span data-ttu-id="6bc7c-119">如需詳細資訊，請參閱[SQL Server 資料採礦增益集&#41;的查詢 &#40;](query-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-119">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="data-mining-advanced-query-editor"></a><span data-ttu-id="6bc7c-120">資料採礦進階查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="6bc7c-120">Data Mining Advanced Query Editor</span></span>  
 <span data-ttu-id="6bc7c-121">在此編輯器中，您可以使用資料採礦延伸模組 (DMX) 範本著手建立查詢，然後修改輸入、輸出、演算法及參數，以建立自訂採礦模型、採礦結構或預測查詢。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-121">In this editor, you can use Data Mining Extensions (DMX) templates to jumpstart a query, and then modify the inputs, outputs, algorithms, and parameters to create a custom mining model, mining structure, or prediction query.</span></span>  
  
 <span data-ttu-id="6bc7c-122">如需詳細資訊，請參閱[先進資料採礦查詢編輯器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-122">For more information, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="management"></a><span data-ttu-id="6bc7c-123">管理性</span><span class="sxs-lookup"><span data-stu-id="6bc7c-123">Management</span></span>  
 <span data-ttu-id="6bc7c-124">使用 [**管理模型**] wizard，即可在目前的連接上查看現有的模型。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-124">Use the **Manage Models** wizard to view existing models on the current connection.</span></span> <span data-ttu-id="6bc7c-125">您也可以刪除、重新命名、處理或匯入及匯出採礦模型和結構。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-125">You can also delete, rename, process, or import and export mining models and structures.</span></span>  
  
 <span data-ttu-id="6bc7c-126">如需詳細資訊，請參閱[&#40;SQL Server 資料採礦增益集&#41;管理模型](manage-models-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc7c-126">For more information, see [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc7c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc7c-127">See Also</span></span>  
 <span data-ttu-id="6bc7c-128">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="6bc7c-128">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="6bc7c-129">驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6bc7c-129">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
