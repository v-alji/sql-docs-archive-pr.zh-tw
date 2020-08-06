---
title: 建立一份採礦模型的複本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: a05eb75210ce9f601aeca515cd299f4204908705
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584848"
---
# <a name="make-a-copy-of-a-mining-model"></a><span data-ttu-id="7afba-102">建立採礦模型的複本</span><span class="sxs-lookup"><span data-stu-id="7afba-102">Make a Copy of a Mining Model</span></span>
  <span data-ttu-id="7afba-103">當您想要快速建立數個以相同資料為基礎的採礦模型時，建立採礦模型的複本很有用。</span><span class="sxs-lookup"><span data-stu-id="7afba-103">Creating a copy of a mining model is useful when you want to quickly create several mining models that are based on the same data.</span></span> <span data-ttu-id="7afba-104">複製模型之後，可以藉由變更參數或新增篩選來編輯新複本。</span><span class="sxs-lookup"><span data-stu-id="7afba-104">After you copy the model, you can then edit the new copy by changing parameters or adding a filter.</span></span>  
  
 <span data-ttu-id="7afba-105">例如，如果您有一個 Customers 資料表與依客戶採購的資料表相連結，則可以建立複本，以針對每個客戶人口統計 (例如年齡或區域等屬性篩選) 建立個別的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7afba-105">For example, if you have a Customers table that is linked to a table of purchases, you could create copies to generate separate mining models for each customer demographic, filtering on attributes such as age or region.</span></span>  
  
 <span data-ttu-id="7afba-106">如需如何將模型內容 (如圖形表示形式或模型模式) 複製到剪貼簿以供其他程式使用的資訊，請參閱 [複製採礦模型的檢視](copy-a-view-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7afba-106">For information about how to copy the content of the model (such as the graphical representation or the model patterns) to the Clipboard for use in other programs, see [Copy a View of a Mining Model](copy-a-view-of-a-mining-model.md).</span></span>  
  
### <a name="to-create-a-related-mining-model"></a><span data-ttu-id="7afba-107">若要建立相關的採礦模型</span><span class="sxs-lookup"><span data-stu-id="7afba-107">To create a related mining model</span></span>  
  
1.  <span data-ttu-id="7afba-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的方案總管中，按一下包含採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="7afba-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model.</span></span>  
  
2.  <span data-ttu-id="7afba-109">按一下 **[採礦模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7afba-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="7afba-110">選擇模型，然後以滑鼠右鍵按一下，開啟快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="7afba-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="7afba-111">-或-</span><span class="sxs-lookup"><span data-stu-id="7afba-111">-or-</span></span>  
  
     <span data-ttu-id="7afba-112">選取此模型。</span><span class="sxs-lookup"><span data-stu-id="7afba-112">Select the model.</span></span> <span data-ttu-id="7afba-113">在 [採礦模型]\*\*\*\* 功能表上，選取 [新增採礦模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7afba-113">On the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="7afba-114">輸入新採礦模型的名稱，然後選取演算法。</span><span class="sxs-lookup"><span data-stu-id="7afba-114">Type a name for the new mining model, and select an algorithm.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a><span data-ttu-id="7afba-115">若要編輯複製採礦模型上的篩選</span><span class="sxs-lookup"><span data-stu-id="7afba-115">To edit the filter on the copied mining model</span></span>  
  
1.  <span data-ttu-id="7afba-116">選取採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7afba-116">Select the mining model.</span></span>  
  
2.  <span data-ttu-id="7afba-117">在 [**屬性**] 視窗中，按一下 [**篩選**] 屬性的文字方塊，然後按一下 [組建\*\* ( ...] ) \*\* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7afba-117">In the **Properties** window, click the text box for the **Filter** property, and the click the build **(...)** button.</span></span>  
  
3.  <span data-ttu-id="7afba-118">變更篩選條件。</span><span class="sxs-lookup"><span data-stu-id="7afba-118">Change the filter conditions.</span></span>  
  
     <span data-ttu-id="7afba-119">如需如何使用篩選編輯器對話方塊的詳細資訊，請參閱 [將篩選套用至採礦模型](apply-a-filter-to-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7afba-119">For more information about how to use the filter editor dialog boxes, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
4.  <span data-ttu-id="7afba-120">在 [**屬性**] 視窗的文字方塊中， `AlgorithmParameters` 按一下 [**設定參數**]，並視需要變更演算法參數。</span><span class="sxs-lookup"><span data-stu-id="7afba-120">In the **Properties** window, in the `AlgorithmParameters` text box, click **Setalgorithm parameters**, and change algorithm parameters, if desired.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7afba-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7afba-121">See Also</span></span>  
 <span data-ttu-id="7afba-122">[&#40;Analysis Services 的採礦模型篩選-資料採礦&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7afba-122">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7afba-123">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7afba-123">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="7afba-124">從採礦模型刪除篩選</span><span class="sxs-lookup"><span data-stu-id="7afba-124">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
