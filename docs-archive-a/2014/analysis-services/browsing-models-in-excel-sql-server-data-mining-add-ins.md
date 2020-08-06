---
title: 在 Excel 中流覽模型 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- browse models
- mining models, viewing
ms.assetid: a8cca1d7-602a-449a-875c-99da564965bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: c992f1f61112478a85276b6596da0137ccd5c9be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593097"
---
# <a name="browsing-models-in-excel-sql-server-data-mining-add-ins"></a><span data-ttu-id="df134-102">在 Excel 中瀏覽模型 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="df134-102">Browsing Models in Excel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="df134-103">![資料採礦功能區的瀏覽模型按鈕](media/dmc-browse.gif "資料採礦功能區的瀏覽模型按鈕")</span><span class="sxs-lookup"><span data-stu-id="df134-103">![Browse Model button in Data Mining ribbon](media/dmc-browse.gif "Browse Model button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="df134-104">以視覺效果方式探索模型通常是了解分析所發現之規則和關聯性最簡單快速的方法。</span><span class="sxs-lookup"><span data-stu-id="df134-104">Visually exploring the model is usually the fastest and easiest way to get an understanding of the rules and relationships discovered by analysis.</span></span> <span data-ttu-id="df134-105">您可以使用適用於 Excel 的資料採礦用戶端來瀏覽在目前 Excel 工作階段期間建立的暫時性模型，以及儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體中的模型。</span><span class="sxs-lookup"><span data-stu-id="df134-105">By using the Data Mining Client for Excel, you can browse both temporary models created during the current Excel session, and models stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="df134-106">若要瀏覽模型，您可以從可用模型的清單中選取模型及其關聯的結構，而且此增益集會自動挑選該資料採礦演算法所適合的檢視器。</span><span class="sxs-lookup"><span data-stu-id="df134-106">To browse a model, you select a model and its associated structure from a list of available models, and the add-in automatically picks the viewer that is appropriate for that data mining algorithm.</span></span> <span data-ttu-id="df134-107">您可以鑽研到最感興趣的趨勢、篩選已完成的資料採礦模型，並且將圖形和資料複製到 Excel 或 Visio。</span><span class="sxs-lookup"><span data-stu-id="df134-107">You can drill into the most interesting trends, filter the completed data mining model, and copy graphs and data to Excel or to Visio.</span></span>  
  
## <a name="using-the-browse-model-wizard"></a><span data-ttu-id="df134-108">使用瀏覽模型精靈</span><span class="sxs-lookup"><span data-stu-id="df134-108">Using the Browse Model Wizard</span></span>  
  
1.  <span data-ttu-id="df134-109">按一下 [**資料採礦**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="df134-109">Click the **Data Mining** tab.</span></span>  
  
2.  <span data-ttu-id="df134-110">在 [**模型使用**方式] 群組中，按一下 **[流覽]**。</span><span class="sxs-lookup"><span data-stu-id="df134-110">In the **Model Usage** group, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="df134-111">在 [**選取模型**] 對話方塊中，從清單中選擇一個 [採礦模型]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="df134-111">In the **Select Model** dialog box, choose a mining model from the list, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="df134-112">此 wizard 會開啟 **[流覽**] 視窗，適用于您所選取的模型類型。</span><span class="sxs-lookup"><span data-stu-id="df134-112">The wizard opens a **Browse** window that is appropriate for the type of model that you selected.</span></span>  
  
## <a name="list-of-data-mining-viewers"></a><span data-ttu-id="df134-113">資料採礦檢視器的清單</span><span class="sxs-lookup"><span data-stu-id="df134-113">List of Data Mining Viewers</span></span>  
 <span data-ttu-id="df134-114">根據您在建立模型時所使用的資料採礦演算法而定，[**流覽**] 視窗看起來會有點不同。</span><span class="sxs-lookup"><span data-stu-id="df134-114">Depending on the data mining algorithm that you used when you created the model, the **Browse** window will look a bit different.</span></span> <span data-ttu-id="df134-115">它可能會包含有助於解譯結果的圖形、含有其他詳細資料的圖例，以及與資料互動的控制項。</span><span class="sxs-lookup"><span data-stu-id="df134-115">It can include graphs to help interpret the results, legends that contain additional detail, and controls for interacting with the data.</span></span>  
  
 <span data-ttu-id="df134-116">下列主題提供了如何使用每個檢視器的指引，其中包括解譯複雜圖形及如何變更、複製或利用結果的秘訣。</span><span class="sxs-lookup"><span data-stu-id="df134-116">The following topics provide guidance in how to use each of the viewers, including tips on interpreting the complex graphs, and how to change, copy, or work with the results.</span></span>  
  
 [<span data-ttu-id="df134-117">瀏覽關聯規則模型</span><span class="sxs-lookup"><span data-stu-id="df134-117">Browsing an Association Rules Model</span></span>](browsing-an-association-rules-model.md)  
  
 [<span data-ttu-id="df134-118">瀏覽群集模型</span><span class="sxs-lookup"><span data-stu-id="df134-118">Browsing a Clustering Model</span></span>](browsing-a-clustering-model.md)  
  
 [<span data-ttu-id="df134-119">瀏覽決策樹模型</span><span class="sxs-lookup"><span data-stu-id="df134-119">Browsing a Decision Trees Model</span></span>](browsing-a-decision-trees-model.md)  
  
 [<span data-ttu-id="df134-120">瀏覽預測模型</span><span class="sxs-lookup"><span data-stu-id="df134-120">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
 [<span data-ttu-id="df134-121">瀏覽貝式機率分類模型</span><span class="sxs-lookup"><span data-stu-id="df134-121">Browsing a Naive Bayes Model</span></span>](browsing-a-naive-bayes-model.md)  
  
 [<span data-ttu-id="df134-122">瀏覽類神經網路模型</span><span class="sxs-lookup"><span data-stu-id="df134-122">Browsing a Neural Network Model</span></span>](browsing-a-neural-network-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="df134-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df134-123">See Also</span></span>  
 <span data-ttu-id="df134-124">[在 Visio 中查看資料採礦模型 &#40;資料採礦增益集&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="df134-124">[Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="df134-125">管理 &#40;SQL Server 資料採礦增益集的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="df134-125">Manage Models &#40;SQL Server Data Mining Add-ins&#41;</span></span>](manage-models-sql-server-data-mining-add-ins.md)  
  
  
