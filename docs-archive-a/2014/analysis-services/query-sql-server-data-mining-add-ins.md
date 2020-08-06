---
title: 查詢 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90794aae8a3d664d47ab251ffdd954f22d48f992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706857"
---
# <a name="query-sql-server-data-mining-add-ins"></a><span data-ttu-id="b88c8-102">查詢 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="b88c8-102">Query (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="b88c8-103">![資料採礦功能區中的查詢模型按鈕](media/dmc-query.gif "資料採礦功能區中的查詢模型按鈕")</span><span class="sxs-lookup"><span data-stu-id="b88c8-103">![Query Model button, Data Mining ribbon](media/dmc-query.gif "Query Model button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="b88c8-104">**查詢**嚮導可協助您與現有的採礦模型互動，以根據 excel 資料表、excel 範圍或另一個資料來源中的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="b88c8-104">The **Query** wizard helps you interact with existing mining models to make predictions based on data in an Excel table, an Excel range, or another data source.</span></span> <span data-ttu-id="b88c8-105">將新資料套用至現有模型以預測趨勢的程式稱為「*預測查詢*」。</span><span class="sxs-lookup"><span data-stu-id="b88c8-105">The process of applying new data to an existing model to predict trends is called a *prediction query*.</span></span>  
  
 <span data-ttu-id="b88c8-106">**查詢**wizard 也會提供一個 [高級編輯器]，用於建立或修改資料採礦模型、產生自訂查詢，或使用其他工具（例如，嵌套資料集）不支援的結構。</span><span class="sxs-lookup"><span data-stu-id="b88c8-106">The **Query** wizard also provides an advanced editor for creating or modifying data mining models, for generating custom queries, or for working with structures not supported in the other tools, such as nested datasets.</span></span>  
  
-   <span data-ttu-id="b88c8-107">使用文字編輯器，輸入或貼上您在別處建立的「資料採礦延伸模組」 (DMX) 語句。</span><span class="sxs-lookup"><span data-stu-id="b88c8-107">Use the text editor to type or paste in the Data Mining Extensions (DMX) statements you've created elsewhere.</span></span>  
  
-   <span data-ttu-id="b88c8-108">使用互動式查詢產生器，透過範本和對話方塊的協助撰寫自訂 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b88c8-108">Use the interactive Query Builder to compose a custom DMX statement with the help of templates and dialog boxes.</span></span>  
  
-   <span data-ttu-id="b88c8-109">建立 DMX 陳述式以管理或備份採礦模型和結構。</span><span class="sxs-lookup"><span data-stu-id="b88c8-109">Create DMX statements to manage or back up mining models and structures.</span></span>  
  
## <a name="using-the-query-wizard"></a><span data-ttu-id="b88c8-110">使用查詢精靈</span><span class="sxs-lookup"><span data-stu-id="b88c8-110">Using the Query Wizard</span></span>  
  
1.  <span data-ttu-id="b88c8-111">首先，您必須針對要當做輸入使用的資料指定來源。</span><span class="sxs-lookup"><span data-stu-id="b88c8-111">First, you must specify a source for the data to use as input.</span></span> <span data-ttu-id="b88c8-112">您可以使用現有 Excel 資料表或範圍中的資料，或者也可以指定 SQL 陳述式來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="b88c8-112">You can use data in an existing Excel table or range, or you can specify a SQL statement to retrieve the data.</span></span>  
  
2.  <span data-ttu-id="b88c8-113">接下來，此精靈會呈現連接之伺服器上的資料採礦模型清單。</span><span class="sxs-lookup"><span data-stu-id="b88c8-113">Next, the wizard presents a list of data mining models on the server to which you are connected.</span></span> <span data-ttu-id="b88c8-114">如果您知道您想要的模型，並熟悉資料採礦，您也可以按一下 [ **Advanced** ] 以開啟 [**資料採礦的先進查詢編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="b88c8-114">If you know the model you want and are familiar with data mining, you can also click **Advanced** to open the **Data Mining Advanced Query Editor**.</span></span>  
  
3.  <span data-ttu-id="b88c8-115">根據選擇的模型類型而定，您必須指定包含要評估之資料的資料行，以及定義輸入資料行和模型資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="b88c8-115">Depending on the type of model that you choose, you must specify the column that contains the data to be evaluated, and define mappings between the input data columns and the model columns.</span></span> <span data-ttu-id="b88c8-116">根據選擇的演算法而定，您可以設定此模型的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="b88c8-116">Depending on the algorithm you choose, you can set other properties on the model.</span></span>  
  
4.  <span data-ttu-id="b88c8-117">最後，此精靈也會讓您有能力可選擇一或多個預測，以及指定要儲存結果的目的地。</span><span class="sxs-lookup"><span data-stu-id="b88c8-117">Finally, the wizard also gives you the ability to choose one or more predictions, and specify a destination in which to store the results.</span></span>  
  
 <span data-ttu-id="b88c8-118">您隨時都可以按一下 [ **Advanced** ]，切換至 [**資料採礦先進查詢編輯器**]，讓您更充分掌控 DMX 語句的每個部分。</span><span class="sxs-lookup"><span data-stu-id="b88c8-118">At any time, you can click **Advanced** to switch to the **Data Mining Advanced Query Editor**, which gives you more control over each part of the DMX statement.</span></span> <span data-ttu-id="b88c8-119">如需如何使用 advanced query 編輯工具的詳細資訊，請參閱[先進資料採礦查詢編輯器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b88c8-119">For more information about how to use the advanced query editing tools, see [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="b88c8-120">需求</span><span class="sxs-lookup"><span data-stu-id="b88c8-120">Requirements</span></span>  
 <span data-ttu-id="b88c8-121">若要使用**查詢**嚮導，您必須連接到的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b88c8-121">To use the **Query** wizard, you must be connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b88c8-122">此外，此伺服器必須至少包含一個適當類型的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b88c8-122">Moreover, the server must contain at least one data mining model of an appropriate type.</span></span> <span data-ttu-id="b88c8-123">如果沒有可用的採礦模型，您可以使用適用於 Excel 的資料採礦用戶端中所提供的精靈來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b88c8-123">If no mining models are available, you can create one by using the wizards provided in the Data Mining Client for Excel.</span></span> <span data-ttu-id="b88c8-124">如需如何使用 wizard 建立新的「挖掘模式」的詳細資訊，請參閱[建立資料採礦模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b88c8-124">For information about how to create a new mining mode by using a wizard, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88c8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b88c8-125">See Also</span></span>  
 <span data-ttu-id="b88c8-126">[&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b88c8-126">[Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="b88c8-127">適用于 Excel &#40;SQL Server 資料採礦增益集的資料採礦用戶端&#41;</span><span class="sxs-lookup"><span data-stu-id="b88c8-127">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
