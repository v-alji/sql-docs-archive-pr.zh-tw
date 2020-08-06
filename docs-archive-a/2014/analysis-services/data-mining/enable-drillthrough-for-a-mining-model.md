---
title: 啟用採礦模型的鑽取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6adfc389776f91132e527130f50f61c9783d9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585663"
---
# <a name="enable-drillthrough-for-a-mining-model"></a><span data-ttu-id="2200d-102">針對採礦模型啟用鑽研</span><span class="sxs-lookup"><span data-stu-id="2200d-102">Enable Drillthrough for a Mining Model</span></span>
  <span data-ttu-id="2200d-103">如果您已經啟用採礦模型的鑽研，當您瀏覽此模型時，可以擷取有關用來建立模型之案例的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2200d-103">If you have enabled drillthrough for a mining model, when you browse the model you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="2200d-104">若要檢視這項資訊，您必須擁有必要的權限，而且結構必須已經經過處理。</span><span class="sxs-lookup"><span data-stu-id="2200d-104">To view this information, you must have the necessary permissions, and the structure must have already been processed.</span></span>  
  
 <span data-ttu-id="2200d-105">**權限** ：若要讓使用者鑽研模型資料或結構資料，該使用者必須是針對採礦模型或採礦結構擁有 [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) 權限之角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2200d-105">**Permissions** For a user to drill through to either model data or structure data, the user must be a member of a role that has [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) permissions on the mining model or mining structure.</span></span> <span data-ttu-id="2200d-106">鑽研權限是在結構和模型上分別設定的。</span><span class="sxs-lookup"><span data-stu-id="2200d-106">Drillthrough permissions are set separately on the structure and model.</span></span>  
  
-   <span data-ttu-id="2200d-107">即使您沒有結構的權限，模型的鑽研權限還是可以讓您從模型進行鑽研。</span><span class="sxs-lookup"><span data-stu-id="2200d-107">Drillthrough permissions on the model enable you to drill through from the model, even if you do not have permissions on the structure.</span></span>  
  
-   <span data-ttu-id="2200d-108">結構的鑽研權限可以使用 [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 函數，提供將結構資料行從模型加入到鑽研查詢的額外功能。</span><span class="sxs-lookup"><span data-stu-id="2200d-108">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span> <span data-ttu-id="2200d-109">您也可以使用 [選取 ...] 來查詢結構中的定型和測試案例。從 \<structure> 。案例語法。</span><span class="sxs-lookup"><span data-stu-id="2200d-109">You can also query the training and test cases in the structure by using the SELECT... FROM \<structure>.CASES syntax.</span></span>  
  
 <span data-ttu-id="2200d-110">**快取定型案例** ：鑽研藉由擷取採礦結構中定型案例的相關資訊來運作。</span><span class="sxs-lookup"><span data-stu-id="2200d-110">**Caching of training cases** Drillthrough works by retrieving information about the training cases in the mining structure.</span></span> <span data-ttu-id="2200d-111">這項資訊會在處理結構時快取。</span><span class="sxs-lookup"><span data-stu-id="2200d-111">This information is cached when the structure is processed.</span></span> <span data-ttu-id="2200d-112">因此，如果您選擇將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 `ClearAfterProcessing` 來清除所有快取的資料，鑽研將不會運作。</span><span class="sxs-lookup"><span data-stu-id="2200d-112">Therefore, if you choose to clear all cached data by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2200d-113">如果尚未快取定型案例，您必須將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 **KeepTrainingCases** ，然後在可以檢視案例資料之前，重新處理模型。</span><span class="sxs-lookup"><span data-stu-id="2200d-113">If the training cases have not been cached, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to **KeepTrainingCases** and then reprocess the model before you can view the case data.</span></span>  
  
 <span data-ttu-id="2200d-114">如需詳細資訊，請參閱 [鑽研查詢 &#40;資料採礦&#41;](drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2200d-114">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="2200d-115">針對採礦模型啟用鑽研</span><span class="sxs-lookup"><span data-stu-id="2200d-115">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="2200d-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下您想要啟用鑽研之採礦模型的名稱，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2200d-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the name of the mining model on which you want to enable drillthrough, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2200d-117">在 [**屬性**] 視窗中，按一下 [ **AllowDrillthrough**]，然後選取 [ **True**]。</span><span class="sxs-lookup"><span data-stu-id="2200d-117">In the **Properties** windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="2200d-118">在 [採礦模型]\*\*\*\* 索引標籤中，以滑鼠右鍵按一下模型，然後選取 [處理模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2200d-118">In the **Mining Models** tab, right-click the model, and select **Process Model**.</span></span>  
  
### <a name="to-enable-caching-for-a-mining-structure"></a><span data-ttu-id="2200d-119">針對採礦結構啟用快取</span><span class="sxs-lookup"><span data-stu-id="2200d-119">To enable caching for a mining structure</span></span>  
  
1.  <span data-ttu-id="2200d-120">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下採礦結構的名稱。</span><span class="sxs-lookup"><span data-stu-id="2200d-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Structure** tab of Data Mining Designer, right-click the name of the mining structure.</span></span>  
  
2.  <span data-ttu-id="2200d-121">開啟 [屬性]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="2200d-121">Open the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="2200d-122">在 [屬性]\*\*\*\* 視窗中，找出 **CacheMode** 屬性，然後從清單中選取 [KeepTrainingCases]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2200d-122">In the **Properties** window, locate the **CacheMode** property, and select **KeepTrainingCases** from the list.</span></span>  
  
4.  <span data-ttu-id="2200d-123">在 [資料庫]\*\*\*\* 功能表中，選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2200d-123">On the **Database** menu, select **Process**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2200d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2200d-124">See Also</span></span>  
 [<span data-ttu-id="2200d-125">鑽研查詢 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="2200d-125">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
