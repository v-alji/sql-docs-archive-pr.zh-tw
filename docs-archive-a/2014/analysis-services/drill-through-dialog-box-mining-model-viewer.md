---
title: '[向下切入] 對話方塊 () 的 [採礦模型檢視器] |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b00c62017de5a26c4507a04aeaf59aba7522146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599249"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a><span data-ttu-id="910ab-102">鑽研對話方塊 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="910ab-102">Drill Through Dialog Box (Mining Model Viewer)</span></span>
  <span data-ttu-id="910ab-103">當您使用「資料採礦設計師」的 **[採礦模型檢視器]** 索引標籤檢視採礦模型時，假設該模型已啟用鑽研，您就可以鑽研到案例資料的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="910ab-103">When you view a mining model by using the **Mining Model Viewer** tab of Data Mining Designer, you can drill through into details about the case data, provided the model has drillthrough enabled.</span></span> <span data-ttu-id="910ab-104">此外，如果基礎採礦結構已啟用鑽研，您也可以看到採礦結構中的資料行 (即使這些資料行不包含在採礦模型中)。</span><span class="sxs-lookup"><span data-stu-id="910ab-104">Moreover, if the underlying mining structure has drillthrough enabled, you can also see columns in the mining structure, even if those columns were not included in the mining model.</span></span> <span data-ttu-id="910ab-105">在資料行清單中，結構資料行的前面會加上 "Structure."</span><span class="sxs-lookup"><span data-stu-id="910ab-105">In the column list, the structure columns are prefixed by the "Structure."</span></span> <span data-ttu-id="910ab-106">標籤。</span><span class="sxs-lookup"><span data-stu-id="910ab-106">label.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="910ab-107">您無法針對現有的採礦結構啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="910ab-107">You cannot enable drillthrough on an existing mining structure.</span></span> <span data-ttu-id="910ab-108">而必須重新建立採礦結構，然後在建立程序期間啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="910ab-108">Instead, you must re-create the mining structure and enable drillthrough during the creation process.</span></span>  
  
 <span data-ttu-id="910ab-109">如需如何從每個支援鑽取的「採礦模型檢視器」存取案例資料的詳細資訊，**請參閱**[向下切入至從採礦模型的案例資料](data-mining/drill-through-to-case-data-from-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="910ab-109">For information about how to access case data from each of the mining model viewers that support drillthrough, **see** [Drill Through to Case Data from a Mining Model](data-mining/drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="910ab-110">選項</span><span class="sxs-lookup"><span data-stu-id="910ab-110">Options</span></span>  
 <span data-ttu-id="910ab-111">**案例分類為**</span><span class="sxs-lookup"><span data-stu-id="910ab-111">**Cases Classified To**</span></span>  
 <span data-ttu-id="910ab-112">顯示所選節點中所包含之規則、項目集和叢集的定義。</span><span class="sxs-lookup"><span data-stu-id="910ab-112">Displays the definition of the rule, itemset, and cluster that are contained in the selected node.</span></span>  
  
 <span data-ttu-id="910ab-113">**資料行清單**</span><span class="sxs-lookup"><span data-stu-id="910ab-113">**Column list**</span></span>  
 <span data-ttu-id="910ab-114">顯示模型中的資料行，後面接著結構資料行。</span><span class="sxs-lookup"><span data-stu-id="910ab-114">Displays the columns in the model, followed by the structure columns.</span></span>  
  
 <span data-ttu-id="910ab-115">**注意** —只有在採礦結構上啟用鑽研，而且選取 **[模型和結構資料行]** 選項時，才會顯示結構資料行。</span><span class="sxs-lookup"><span data-stu-id="910ab-115">**Note** Structure columns are displayed only if drillthrough is enabled on the mining structure, and if you selected the option, **Model and Structure Columns**.</span></span> <span data-ttu-id="910ab-116">此外，您必須同時擁有採礦模型和採礦結構的鑽研權限，才能檢視資料行。</span><span class="sxs-lookup"><span data-stu-id="910ab-116">Moreover, you must have drillthrough permissions on both the mining model and the mining structure to view the columns.</span></span>  
  
 <span data-ttu-id="910ab-117">不包含在模型中的結構資料行會顯示為 [\*\*結構 \<column name> \*\*]。</span><span class="sxs-lookup"><span data-stu-id="910ab-117">Structure columns that are not included in the model appear as **Structure.\<column name>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="910ab-118">您可以以滑鼠右鍵按一下詳細資料方格中的任意位置，然後選取 [全部複製]\*\*\*\*，以 Tab 分隔的格式，將鑽研資料複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="910ab-118">You can right-click anywhere in the column grid and select **Copy All** to copy the drillthrough data, in tab-delimited format, to the Clipboard.</span></span> <span data-ttu-id="910ab-119">複製的資料僅包含案例資料，而不包含節點定義。</span><span class="sxs-lookup"><span data-stu-id="910ab-119">The copied data includes only the case data, not the node definition.</span></span>  
  
 <span data-ttu-id="910ab-120">**播放**</span><span class="sxs-lookup"><span data-stu-id="910ab-120">**Play**</span></span>  
 <span data-ttu-id="910ab-121">按一下綠色箭頭按鈕可重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="910ab-121">Click the green arrow button to refresh the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910ab-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="910ab-122">See Also</span></span>  
 <span data-ttu-id="910ab-123">[資料採礦&#41;&#40;的鑽取查詢](data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="910ab-123">[Drillthrough Queries &#40;Data Mining&#41;](data-mining/drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="910ab-124">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="910ab-124">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="910ab-125">採礦模型檢視器工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="910ab-125">Mining Model Viewer Tasks and How-tos</span></span>](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
