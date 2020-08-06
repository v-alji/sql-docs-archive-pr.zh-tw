---
title: 資料採礦查詢工作和操作說明 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], how-to topics
ms.assetid: 1bc2a775-6e62-4c66-a53c-201f2ea66295
author: minewiskan
ms.author: owend
ms.openlocfilehash: 454a3af33d0c18232bb36771235b328a17da6b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606514"
---
# <a name="data-mining-query-tasks-and-how-tos"></a><span data-ttu-id="f995d-102">資料採礦查詢工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="f995d-102">Data Mining Query Tasks and How-tos</span></span>
  <span data-ttu-id="f995d-103">建立查詢的功能對於使用資料採礦模型十分重要。</span><span class="sxs-lookup"><span data-stu-id="f995d-103">The ability to create queries is critical if you are to make use of your data mining models.</span></span> <span data-ttu-id="f995d-104">本節提供一些範例連結，這些範例示範如何透過使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中提供的工具針對資料採礦模型建立查詢。</span><span class="sxs-lookup"><span data-stu-id="f995d-104">This section provides links to examples of how to create queries against a data mining model by using the tools provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f995d-105">如果您需要有關資料採礦查詢的作用或者可建立之不同查詢類型的詳細資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="f995d-105">If you need more information about what a data mining query is, or the different types of queries you can create, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="creating-queries-with-prediction-query-builder"></a><span data-ttu-id="f995d-106">使用預測查詢產生器建立查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-106">Creating Queries with Prediction Query Builder</span></span>  
 <span data-ttu-id="f995d-107">預測查詢產生器在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中都有提供，做為以圖形方式針對資料採礦模型建立查詢的方法。</span><span class="sxs-lookup"><span data-stu-id="f995d-107">The Prediction Query Builder is provided in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a way of graphically building queries against data mining models.</span></span> <span data-ttu-id="f995d-108">下列主題說明如何選取模型、指定資料來源、自訂預測和儲存輸出。</span><span class="sxs-lookup"><span data-stu-id="f995d-108">The following topics explain how you can select a model, specify a data source, customize the predictions, and save output.</span></span>  
  
-   [<span data-ttu-id="f995d-109">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-109">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="f995d-110">在資料採礦設計師中建立單一查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-110">Create a Singleton Query in the Data Mining Designer</span></span>](create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [<span data-ttu-id="f995d-111">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-111">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="f995d-112">檢視及儲存預測查詢的結果</span><span class="sxs-lookup"><span data-stu-id="f995d-112">View and Save the Results of a Prediction Query</span></span>](view-and-save-the-results-of-a-prediction-query.md)  
  
-   [<span data-ttu-id="f995d-113">手動編輯預測查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-113">Manually Edit a Prediction Query</span></span>](manually-edit-a-prediction-query.md)  
  
-   [<span data-ttu-id="f995d-114">將預測函數套用至模型</span><span class="sxs-lookup"><span data-stu-id="f995d-114">Apply Prediction Functions to a Model</span></span>](apply-prediction-functions-to-a-model.md)  
  
-   [<span data-ttu-id="f995d-115">為預測查詢選擇和對應輸入資料</span><span class="sxs-lookup"><span data-stu-id="f995d-115">Choose and Map Input Data for a Prediction Query</span></span>](choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a><span data-ttu-id="f995d-116">使用其他資料採礦查詢工具</span><span class="sxs-lookup"><span data-stu-id="f995d-116">Using Other Data Mining Query Tools</span></span>  
 <span data-ttu-id="f995d-117">除了使用預測查詢產生器之外，您也可以使用 DMX 或使用 XMLA 將查詢直接輸入 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="f995d-117">In addition to using the Prediction Query Builder, you can type a query directly into [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using DMX or by using XMLA.</span></span> <span data-ttu-id="f995d-118">您還可以透過程式設計方式建立預測查詢並且將這些查詢傳送至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f995d-118">You can also build prediction queries programmatically and send them to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="f995d-119">下列主題提供有關如何在預測查詢產生器之外建立和使用預測查詢的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f995d-119">The following topics provide more information about how to create and work with prediction queries outside of the Prediction Query Builder.</span></span>  
  
 [<span data-ttu-id="f995d-120">根據範本建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-120">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="f995d-121">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的工具來建立和執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="f995d-121">Describes how to use the tools in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to build and run a prediction query.</span></span>  
  
 [<span data-ttu-id="f995d-122">根據範本建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-122">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="f995d-123">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 所提供的範本，將參數加入預測查詢。</span><span class="sxs-lookup"><span data-stu-id="f995d-123">Describes how to use the templates that are provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add parameters to a prediction query.</span></span>  
  
 [<span data-ttu-id="f995d-124">針對資料採礦查詢變更逾時值</span><span class="sxs-lookup"><span data-stu-id="f995d-124">Change the Time-out Value for Data Mining Queries</span></span>](change-the-time-out-value-for-data-mining-queries.md)  
 <span data-ttu-id="f995d-125">描述如何設定伺服器的屬性，以便控制資料採礦查詢的相關行為。</span><span class="sxs-lookup"><span data-stu-id="f995d-125">Describes how to set properties on the server that control behavior related to data mining queries.</span></span>  
  
 [<span data-ttu-id="f995d-126">建立採礦模型內容查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-126">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
 <span data-ttu-id="f995d-127">描述如何使用資料採礦結構描述資料列集來建立查詢，以便傳回採礦模型中所儲存的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f995d-127">Describes how to create queries that return detailed information that is stored in the mining model by using the data mining schema rowsets.</span></span>  
  
 [<span data-ttu-id="f995d-128">使用 XMLA 建立資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="f995d-128">Create a Data Mining Query by Using XMLA</span></span>](create-a-data-mining-query-by-using-xmla.md)  
 <span data-ttu-id="f995d-129">描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 XMLA 範本，針對採礦模型內容建立查詢。</span><span class="sxs-lookup"><span data-stu-id="f995d-129">Describes how to create a query against mining model content by using the XMLA templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f995d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f995d-130">See Also</span></span>  
 <span data-ttu-id="f995d-131">[查詢和運算式語言參考 &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span><span class="sxs-lookup"><span data-stu-id="f995d-131">[Query and Expression Language Reference &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span></span>  
 [<span data-ttu-id="f995d-132">資料採礦預存程序 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f995d-132">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
