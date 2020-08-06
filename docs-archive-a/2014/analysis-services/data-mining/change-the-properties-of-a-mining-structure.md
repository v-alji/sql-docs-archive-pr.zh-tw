---
title: 變更採礦結構的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c1e63ad5fada770394e2fc283e0e592319281b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686547"
---
# <a name="change-the-properties-of-a-mining-structure"></a><span data-ttu-id="5340d-102">變更採礦結構的屬性</span><span class="sxs-lookup"><span data-stu-id="5340d-102">Change the Properties of a Mining Structure</span></span>
  <span data-ttu-id="5340d-103">採礦結構有兩種屬性，這兩種屬性都可以修改：</span><span class="sxs-lookup"><span data-stu-id="5340d-103">There are two kinds of properties on a mining structure, both of which can be modified:</span></span>  
  
-   <span data-ttu-id="5340d-104">影響整個採礦結構的採礦結構屬性</span><span class="sxs-lookup"><span data-stu-id="5340d-104">Properties of the mining structure that affect the entire structure</span></span>  
  
-   <span data-ttu-id="5340d-105">採礦結構中個別資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="5340d-105">Properties on individual columns in the structure</span></span>  
  
 <span data-ttu-id="5340d-106">請注意，某些屬性相依於其他屬性設定值。</span><span class="sxs-lookup"><span data-stu-id="5340d-106">Note that some properties are dependent on other property settings.</span></span> <span data-ttu-id="5340d-107">例如，在您將資料行的資料類型設定為 `Discretized` 之前，無法設定控制分類收納行為的屬性 (例如 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 或 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>)。</span><span class="sxs-lookup"><span data-stu-id="5340d-107">For example, you cannot set properties that control binning behavior (such as <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> or <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) until you have set the data type of the column to `Discretized`.</span></span>  
  
 <span data-ttu-id="5340d-108">如需採礦結構屬性的詳細資訊，請參閱 [Mining Structure Columns](mining-structure-columns.md)(採礦結構資料行)。</span><span class="sxs-lookup"><span data-stu-id="5340d-108">For more information about mining structure properties, see [Mining Structure Columns](mining-structure-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a><span data-ttu-id="5340d-109">若要變更採礦結構的屬性</span><span class="sxs-lookup"><span data-stu-id="5340d-109">To change the properties of a mining structure</span></span>  
  
1.  <span data-ttu-id="5340d-110">在資料採礦設計師的 [採礦結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下採礦結構或採礦結構中的資料行，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5340d-110">On the **Mining Structure** tab in Data Mining Designer, right-click either the mining structure or a column in the mining structure, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="5340d-111">如果 **[屬性]** 視窗還沒有出現，則它會在螢幕的右邊開啟。</span><span class="sxs-lookup"><span data-stu-id="5340d-111">The **Properties** window opens on the right side of the screen, if it was not already visible.</span></span>  
  
2.  <span data-ttu-id="5340d-112">在 **[屬性]** 視窗中，選取對應到您要變更之屬性的值，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="5340d-112">In the **Properties** window, select the value that corresponds to the property that you want to change, and then enter the new value.</span></span>  
  
     <span data-ttu-id="5340d-113">您在設計師中選取其他元素時，新值就會生效。</span><span class="sxs-lookup"><span data-stu-id="5340d-113">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5340d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5340d-114">See Also</span></span>  
 [<span data-ttu-id="5340d-115">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="5340d-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
