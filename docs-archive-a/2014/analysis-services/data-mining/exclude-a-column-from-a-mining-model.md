---
title: 從採礦模型中排除資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30affebc143184c6287858f60b5d4f5d089c322a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594275"
---
# <a name="exclude-a-column-from-a-mining-model"></a><span data-ttu-id="9871f-102">從採礦模型排除資料行</span><span class="sxs-lookup"><span data-stu-id="9871f-102">Exclude a Column from a Mining Model</span></span>
  <span data-ttu-id="9871f-103">當您建立新的採礦模型時，可能不想要使用模型做為基礎之採礦結構中已存在的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9871f-103">When you create a new mining model, you may not want to use all the columns that exist in the mining structure on which the model is based.</span></span> <span data-ttu-id="9871f-104">例如，您可能已加入 [客戶名稱] 資料行來進行鑽看，但不想要將它用於模型化。</span><span class="sxs-lookup"><span data-stu-id="9871f-104">For example, you might have added a customer name column for drillthrough, but don't want to use it for modeling.</span></span> <span data-ttu-id="9871f-105">或者，您可能決定為一個資料行建立具有不同離散化的多個複本，並且在每個模型中只使用其中一個複本，而忽略其餘複本。</span><span class="sxs-lookup"><span data-stu-id="9871f-105">Or, you might decide to create multiple copies of a column with different discretizations, and use only one of the copies in each model, and ignore the rest.</span></span> <span data-ttu-id="9871f-106">您還可以選擇性地在多個不同模型中新增輸入資料行，檢查新增的變數如何影響輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="9871f-106">You could also selectively add input columns in several different models to see how the added variable affects the output column.</span></span>  
  
 <span data-ttu-id="9871f-107">您不需要為每個資料行組合都建立新的採礦結構，而是只需將資料行標示為不在特定的模型中使用。</span><span class="sxs-lookup"><span data-stu-id="9871f-107">You do not need to create a new mining structure for each combination of columns; instead, you can simply flag a column as not being used in a particular model.</span></span>  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a><span data-ttu-id="9871f-108">若要從採礦模型排除資料行</span><span class="sxs-lookup"><span data-stu-id="9871f-108">To exclude a column from a mining model</span></span>  
  
1.  <span data-ttu-id="9871f-109">在 **中之資料採礦設計師的** [採礦模型] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]索引標籤中，在適當的採礦模型之下，選取對應至您要排除之資料行的資料格。</span><span class="sxs-lookup"><span data-stu-id="9871f-109">In the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the cell that corresponds to the column you want to exclude, under the appropriate mining model.</span></span>  
  
2.  <span data-ttu-id="9871f-110">從下拉式清單方塊中選取 [忽略]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9871f-110">Select **Ignore** from the drop-down list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9871f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9871f-111">See Also</span></span>  
 [<span data-ttu-id="9871f-112">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="9871f-112">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
