---
title: 變更採礦模型中資料行的離散化 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b20d6428afac5c1492fdc74aafd4d0c010159d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599277"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a><span data-ttu-id="907ba-102">變更採礦模型中的資料行離散化</span><span class="sxs-lookup"><span data-stu-id="907ba-102">Change the Discretization of a Column in a Mining Model</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="907ba-103">自動離散化值-也就是說，它會在某些情況下，將資料在數值資料行中。</span><span class="sxs-lookup"><span data-stu-id="907ba-103">automatically discretizes values-that is to say, it bins data in numeric column-in certain scenarios.</span></span> <span data-ttu-id="907ba-104">例如，如果您的資料包含連續數值資料，而且您要建立決策樹模型，則連續資料的每一個資料行都將會自動分類收納 (視資料的分佈而定)。</span><span class="sxs-lookup"><span data-stu-id="907ba-104">For example, if your data contains continuous numeric data and you create a decision tree model, each column of continuous data will be automatically binned, depending on the distribution of the data.</span></span> <span data-ttu-id="907ba-105">如果您想要控制資料離散化的方式，您必須在採礦結構資料行上，變更可控制資料在模型內之使用方式的屬性。</span><span class="sxs-lookup"><span data-stu-id="907ba-105">If you want to control how the data is discretized, you must change the properties on the mining structure column that control how the data is used in the model.</span></span>  
  
 <span data-ttu-id="907ba-106">如需如何在採礦模型中設定屬性的一般資訊，請參閱 [採礦模型資料行](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="907ba-106">For general information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a><span data-ttu-id="907ba-107">顯示採礦模型資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="907ba-107">To display the properties for a mining model column</span></span>  
  
1.  <span data-ttu-id="907ba-108">在資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下包含採礦模型名稱的資料行標頭，或是方格中包含採礦演算法名稱的資料列，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="907ba-108">In the **Mining Models** tab in Data Mining Designer, right-click the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="907ba-109">**[屬性]** 視窗會顯示在整體上與採礦模型相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="907ba-109">The **Properties** window displays the properties that are associated with the mining model as a whole.</span></span>  
  
2.  <span data-ttu-id="907ba-110">在靠近螢幕左邊的 **[結構]** 資料行中，按一下包含您想要離散化之連續數值資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="907ba-110">In the **Structure** column near the left side of the screen, click the column that contains the continuous numeric data you want to discretize.</span></span>  
  
     <span data-ttu-id="907ba-111">**[屬性]** 視窗會變更，以便只顯示與該資料行有關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="907ba-111">The **Properties** window changes to display just the properties associated with that column.</span></span>  
  
### <a name="to-change-the-discretization-method"></a><span data-ttu-id="907ba-112">變更離散化方法</span><span class="sxs-lookup"><span data-stu-id="907ba-112">To change the discretization method</span></span>  
  
1.  <span data-ttu-id="907ba-113">在 [**挖掘屬性**] 視窗中，按一下 [**內容**] 旁邊的文字方塊，然後 `Discretized` 從下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="907ba-113">In the **Mining Properties** window, click the text box next to **Content**, and select `Discretized` from the dropdown list.</span></span>  
  
     <span data-ttu-id="907ba-114"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 和 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 屬性現在就會啟用。</span><span class="sxs-lookup"><span data-stu-id="907ba-114">The <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> properties are now enabled.</span></span>  
  
2.  <span data-ttu-id="907ba-115">在 [**屬性**] 視窗中，按一下旁邊的文字方塊， <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 然後選取下列其中一個值： `Automatic` 、 `EqualAreas` 或 `Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="907ba-115">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> and select one of the following values: `Automatic`, `EqualAreas`, or `Cluster`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="907ba-116">如果 [資料行使用方式] 設定為，則資料 `Ignore` 行的 [**屬性**] 視窗是空白的。</span><span class="sxs-lookup"><span data-stu-id="907ba-116">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="907ba-117">您在設計師中選取其他元素時，新值就會生效。</span><span class="sxs-lookup"><span data-stu-id="907ba-117">The new value will take effect when you select a different element in the designer.</span></span>  
  
3.  <span data-ttu-id="907ba-118">在 [**屬性**] 視窗中，按一下旁邊的文字方塊 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> ，然後輸入數值。</span><span class="sxs-lookup"><span data-stu-id="907ba-118">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and type a numeric value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="907ba-119">如果您變更這些屬性，就必須重新處理此結構，連同您想要使用新設定的任何模型。</span><span class="sxs-lookup"><span data-stu-id="907ba-119">If you change these properties, the structure must be reprocessed, along with any models that you want to use the new setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907ba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="907ba-120">See Also</span></span>  
 [<span data-ttu-id="907ba-121">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="907ba-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
