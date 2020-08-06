---
title: '[分類矩陣] 索引標籤 () 的挖掘精確度圖表視圖 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
author: minewiskan
ms.author: owend
ms.openlocfilehash: d202d552b25095d0d0845ff64f9c0e289f7bba0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593075"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a><span data-ttu-id="8e17c-102">分類矩陣索引標籤 (採礦精確度圖表檢視)</span><span class="sxs-lookup"><span data-stu-id="8e17c-102">Classification Matrix Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="8e17c-103">[**分類矩陣**] 索引標籤會顯示 [資料**行對應**] 索引標籤上 [模型] 方格中選取之每個模型的分類矩陣。只有在 [資料**行對應**] 索引標籤中選取的可預測資料行不是連續的情況時，才可以使用分類矩陣。</span><span class="sxs-lookup"><span data-stu-id="8e17c-103">The **Classification Matrix** tab displays a classification matrix for each model selected in the models grid on the **Column Mapping** tab. The classification matrix is only available if the predictable column that is selected in the **Column Mapping** tab is not continuous.</span></span> <span data-ttu-id="8e17c-104">如需 [**分類矩陣**] 索引標籤的詳細描述，請參閱[測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="8e17c-104">For a more detailed description of the **Classification Matrix** tab, see [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e17c-105">選項</span><span class="sxs-lookup"><span data-stu-id="8e17c-105">Options</span></span>  
 <span data-ttu-id="8e17c-106">**複製**</span><span class="sxs-lookup"><span data-stu-id="8e17c-106">**Copy**</span></span>  
 <span data-ttu-id="8e17c-107">將每個分類矩陣的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8e17c-107">Copies the content of each classification matrix to the clipboard.</span></span>  
  
 <span data-ttu-id="8e17c-108">**\<model>的計數\< predictable column>**</span><span class="sxs-lookup"><span data-stu-id="8e17c-108">**Counts for \<model> on \< predictable column>**</span></span>  
 <span data-ttu-id="8e17c-109">顯示採礦結構中之每個採礦模型的分類矩陣。</span><span class="sxs-lookup"><span data-stu-id="8e17c-109">Displays a classification matrix for each mining model in the mining structure.</span></span> <span data-ttu-id="8e17c-110">矩陣包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="8e17c-110">The matrix contains the following columns:</span></span>  
  
|<span data-ttu-id="8e17c-111">值</span><span class="sxs-lookup"><span data-stu-id="8e17c-111">Value</span></span>|<span data-ttu-id="8e17c-112">描述</span><span class="sxs-lookup"><span data-stu-id="8e17c-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e17c-113">**預測的**</span><span class="sxs-lookup"><span data-stu-id="8e17c-113">**Predicted**</span></span>|<span data-ttu-id="8e17c-114">包含可預測資料行之每個狀態的資料列。</span><span class="sxs-lookup"><span data-stu-id="8e17c-114">Contains a row for each state of the predictable column.</span></span>|  
|<span data-ttu-id="8e17c-115">\*\*\<states> (實際) \*\*</span><span class="sxs-lookup"><span data-stu-id="8e17c-115">**\<states> (actual)**</span></span>|<span data-ttu-id="8e17c-116">可預測資料行中之每個狀態的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e17c-116">A column for each state in the predictable column.</span></span> <span data-ttu-id="8e17c-117">如果資料列與資料行的狀態對應，則資料格代表狀態存在於資料庫中的實際次數。</span><span class="sxs-lookup"><span data-stu-id="8e17c-117">If the state of the row and the column correspond, the cell represents the actual number of times the state exists in the database.</span></span> <span data-ttu-id="8e17c-118">如果它們不對應，則資料格代表預測的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e17c-118">If they do not correspond, the cell represents the error of the prediction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e17c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e17c-119">See Also</span></span>  
 <span data-ttu-id="8e17c-120">[&#40;資料採礦&#41;的挖掘精確度圖表設計工具](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8e17c-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="8e17c-121">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8e17c-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="8e17c-122">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="8e17c-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
