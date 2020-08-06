---
title: 處理時序群集模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a7545fd-37a3-4766-ad59-0946f1bd3524
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9975105fb6779e150e3a498bc87654d21292a1b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704449"
---
# <a name="processing-the-sequence-clustering-model"></a><span data-ttu-id="ba51d-102">處理時序群集模型</span><span class="sxs-lookup"><span data-stu-id="ba51d-102">Processing the Sequence Clustering Model</span></span>
  <span data-ttu-id="ba51d-103">在您建立了新的採礦結構以後，您必須建部署您對資料採礦方案進行的變更，然後處理結構。</span><span class="sxs-lookup"><span data-stu-id="ba51d-103">After you create a new mining structure, you must deploy the changes that you made to the data mining solution, and then process the structure.</span></span> <span data-ttu-id="ba51d-104">處理完新結構和採礦模型兩者後，您就可以瀏覽採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ba51d-104">After processing of both the new structure and the mining model is complete, you can browse the mining model.</span></span>  
  
 <span data-ttu-id="ba51d-105">當您建立新的資料採礦結構時，一定要進行處理。</span><span class="sxs-lookup"><span data-stu-id="ba51d-105">Processing is always required when you create a new data mining structure.</span></span> <span data-ttu-id="ba51d-106">不過，如果您將新的採礦模型加入到現有的結構，您可以只處理採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ba51d-106">However, if you add a new mining model to an existing structure, you can process just the mining model.</span></span> <span data-ttu-id="ba51d-107">在此狀況中，由於您已經建立新的採礦結構和新的採礦模型，所以您必須同時處理這兩者。</span><span class="sxs-lookup"><span data-stu-id="ba51d-107">In this scenario, because you have created a new mining structure and a new mining model, you must process both.</span></span>  
  
### <a name="to-process-the-mining-structure-and-model"></a><span data-ttu-id="ba51d-108">若要處理採礦結構和模型</span><span class="sxs-lookup"><span data-stu-id="ba51d-108">To process the mining structure and model</span></span>  
  
1.  <span data-ttu-id="ba51d-109">在的 [**採礦模型**] 功能表上 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，選取 [**處理採礦結構] 和 [所有模型**]。</span><span class="sxs-lookup"><span data-stu-id="ba51d-109">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="ba51d-110">在詢問您是否要建立及部署專案的警告中，按一下 [**是]**。</span><span class="sxs-lookup"><span data-stu-id="ba51d-110">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="ba51d-111">在 [**以區域處理採礦結構-時序群集**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="ba51d-111">In the **Process Mining Structure - Sequence Clustering with Region** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="ba51d-112">[**處理進度**] 對話方塊隨即開啟，以顯示模型處理的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba51d-112">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="ba51d-113">處理新的結構和模型可能需要花一些時間。</span><span class="sxs-lookup"><span data-stu-id="ba51d-113">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="ba51d-114">處理完成之後，按一下 [**關閉**] 以結束 [**處理進度**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba51d-114">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="ba51d-115">再按一次 [關閉] 以**結束**[**處理常式] [結構-時序群集與區域**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba51d-115">Click **Close** again to exit the **Process Mining Structure - Sequence Clustering with Region** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ba51d-116">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="ba51d-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ba51d-117">探索時序群集模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="ba51d-117">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba51d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba51d-118">See Also</span></span>  
 <span data-ttu-id="ba51d-119">[資料採礦設計工具](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ba51d-119">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 <span data-ttu-id="ba51d-120">[Microsoft 時序群集演算法](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ba51d-120">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="ba51d-121">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="ba51d-121">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
