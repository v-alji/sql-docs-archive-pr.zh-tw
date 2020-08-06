---
title: 使用 DMX 建立鑽取查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
author: minewiskan
ms.author: owend
ms.openlocfilehash: 618732bfe48f7b1fe777f7841d686b07877d10ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598061"
---
# <a name="create-drillthrough-queries-using-dmx"></a><span data-ttu-id="a96e8-102">使用 DMX 建立鑽研查詢</span><span class="sxs-lookup"><span data-stu-id="a96e8-102">Create Drillthrough Queries using DMX</span></span>
  <span data-ttu-id="a96e8-103">對於支援鑽研的所有模型，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或支援 DMX 的任何其他用戶端中建立 DMX 查詢，藉以擷取案例資料和結構資料。</span><span class="sxs-lookup"><span data-stu-id="a96e8-103">For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any other client that supports DMX.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a96e8-104">若要檢視這些資料，必須已啟用鑽研，而且您必須擁有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="a96e8-104">To view the data, drillthrough must have been enabled, and you must have the necessary permissions.</span></span>  
  
## <a name="specifying-drillthrough-options"></a><span data-ttu-id="a96e8-105">指定鑽研選項</span><span class="sxs-lookup"><span data-stu-id="a96e8-105">Specifying Drillthrough Options</span></span>  
 <span data-ttu-id="a96e8-106">擷取模型案例和結構案例的一般語法如下：</span><span class="sxs-lookup"><span data-stu-id="a96e8-106">The general syntax is for retrieving model cases and structure cases is as follows:</span></span>  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 <span data-ttu-id="a96e8-107">如需使用 DMX 查詢來傳回案例資料的詳細資訊，請參閱 [SELECT FROM &#60;模型&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) 和 [SELECT FROM &#60;結構&#62;.CASES](/sql/dmx/select-from-structure-cases)。</span><span class="sxs-lookup"><span data-stu-id="a96e8-107">For additional information about using DMX queries to return case data, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) and [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a96e8-108">範例</span><span class="sxs-lookup"><span data-stu-id="a96e8-108">Examples</span></span>  
 <span data-ttu-id="a96e8-109">下列 DMX 查詢會從時間序列模型中傳回特定產品序列的案例資料。</span><span class="sxs-lookup"><span data-stu-id="a96e8-109">The following DMX query returns the case data for a specific product series, from a time series model.</span></span> <span data-ttu-id="a96e8-110">此查詢也會傳回模型中沒有使用，但採礦結構中有提供的 `Amount` 資料行。</span><span class="sxs-lookup"><span data-stu-id="a96e8-110">The query also returns the column `Amount`, which was not used in the model but is available in the mining structure.</span></span>  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 <span data-ttu-id="a96e8-111">請注意，在這則範例中，別名已用來重新命名結構資料行。</span><span class="sxs-lookup"><span data-stu-id="a96e8-111">Note that in this example, an alias has been used to rename the structure column.</span></span> <span data-ttu-id="a96e8-112">如果您沒有指派別名給結構資料行，就會傳回名為 'Expression' 的資料行。</span><span class="sxs-lookup"><span data-stu-id="a96e8-112">If you do not assign an alias to the structure column, the column is returned with the name 'Expression'.</span></span> <span data-ttu-id="a96e8-113">這是所有未命名資料行的預設行為。</span><span class="sxs-lookup"><span data-stu-id="a96e8-113">This is the default behavior for all unnamed columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96e8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a96e8-114">See Also</span></span>  
 <span data-ttu-id="a96e8-115">[資料採礦&#41;&#40;的鑽取查詢](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a96e8-115">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="a96e8-116">採礦結構的鑽研</span><span class="sxs-lookup"><span data-stu-id="a96e8-116">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
