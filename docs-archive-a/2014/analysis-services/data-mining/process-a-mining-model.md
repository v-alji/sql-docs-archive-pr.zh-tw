---
title: 處理採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
author: minewiskan
ms.author: owend
ms.openlocfilehash: c2fed5d72c677dc175f4c9681096d1859b30d829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703441"
---
# <a name="process-a-mining-model"></a><span data-ttu-id="2014e-102">處理採礦模型</span><span class="sxs-lookup"><span data-stu-id="2014e-102">Process a Mining Model</span></span>
  <span data-ttu-id="2014e-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]資料採礦設計師的 [採礦模型] 索引標籤中，您可以處理與採礦結構相關聯的特定採礦模型，或處理與結構相關聯的所有模型。</span><span class="sxs-lookup"><span data-stu-id="2014e-103">In the Mining Models tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can either process a specific mining model that is associated with a mining structure or you can process all the models that are associated with the structure.</span></span>  
  
 <span data-ttu-id="2014e-104">您可以使用下列工具處理採礦模型：</span><span class="sxs-lookup"><span data-stu-id="2014e-104">You can process a mining model by using the following tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 <span data-ttu-id="2014e-105">您也可以使用 XMLA 處理命令。</span><span class="sxs-lookup"><span data-stu-id="2014e-105">You can also use an XMLA Process command.</span></span> <span data-ttu-id="2014e-106">如需詳細資訊，請參閱[處理 &#40;Analysis Services&#41;的工具和方法](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2014e-106">For more information, see  [Tools and Approaches for Processing &#40;Analysis Services&#41;](../multidimensional-models/tools-and-approaches-for-processing-analysis-services.md).</span></span>  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="2014e-107">使用 SQL Server 資料工具處理單一採礦模型</span><span class="sxs-lookup"><span data-stu-id="2014e-107">Process a single mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="2014e-108">在 [資料採礦設計師] 的 [採礦模型]\*\*\*\* 索引標籤上，從方格中模型的一或多個資料行選取採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2014e-108">On the **Mining Models** tab of Data Mining Designer, select a mining model from the one or more columns of models in the grid.</span></span>  
  
2.  <span data-ttu-id="2014e-109">在 [採礦模型]\*\*\*\* 功能表上，選取 [處理模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2014e-109">On the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="2014e-110">如果您變更了採礦結構，在處理模型之前，會提示您重新部署結構。</span><span class="sxs-lookup"><span data-stu-id="2014e-110">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the model.</span></span> <span data-ttu-id="2014e-111">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="2014e-111">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="2014e-112">在 [**處理採礦模型- \<model> \*\* ] 對話方塊中，按一下 [**執行\*\*]。</span><span class="sxs-lookup"><span data-stu-id="2014e-112">In the **Processing Mining Model - \<model>** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="2014e-113">[處理進度]\*\*\*\* 對話方塊就會開啟，以顯示模型處理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2014e-113">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
4.  <span data-ttu-id="2014e-114">在模型順利完成處理之後，按一下 [處理進度]\*\*\*\* 對話方塊中的 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2014e-114">After the model has successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="2014e-115">在 [**處理採礦模型 \<model> -** ] 對話方塊中，按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="2014e-115">Click **Close** in the **Processing Mining Model - \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="2014e-116">只處理採礦結構和選取的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2014e-116">Only the mining structure and the selected mining model have been processed.</span></span>  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a><span data-ttu-id="2014e-117">處理與採礦結構相關聯的所有採礦模型</span><span class="sxs-lookup"><span data-stu-id="2014e-117">Process all mining models that are associated with a mining structure</span></span>  
  
1.  <span data-ttu-id="2014e-118">在 [資料採礦設計師] 的 [採礦模型]\*\*\*\* 索引標籤上，從 [採礦模型]\*\*\*\* 功能表中選取 [處理採礦結構和所有模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2014e-118">On the **Mining Models** tab of Data Mining Designer, select **Process Mining Structure and All Models** from the **Mining Model** menu.</span></span>  
  
2.  <span data-ttu-id="2014e-119">如果您變更了採礦結構，在處理模型之前，會提示您重新部署結構。</span><span class="sxs-lookup"><span data-stu-id="2014e-119">If you made changes to the mining structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="2014e-120">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="2014e-120">Click **Yes**.</span></span>  
  
3.  <span data-ttu-id="2014e-121">在 [**處理採礦結構- \<structure> \*\* ] 對話方塊中，按一下 [**執行\*\*]。</span><span class="sxs-lookup"><span data-stu-id="2014e-121">In the **Processing Mining Structure - \<structure>** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="2014e-122">[處理進度]\*\*\*\* 對話方塊就會開啟，以顯示模型處理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2014e-122">The **Process Progress** dialog box opens to show the details of model processing.</span></span>  
  
5.  <span data-ttu-id="2014e-123">在模型順利完成處理之後，按一下 [處理進度]\*\*\*\* 對話方塊中的 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2014e-123">After the models have successfully completed processing, click **Close** in the **Process Progress** dialog box.</span></span>  
  
6.  <span data-ttu-id="2014e-124">在 [**處理 \<model> \*\* ] 對話方塊中，按一下 [**關閉\*\*]。</span><span class="sxs-lookup"><span data-stu-id="2014e-124">Click **Close** in the **Processing \<model>** dialog box.</span></span>  
  
 <span data-ttu-id="2014e-125">已處理採礦結構和所有相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2014e-125">The mining structure and all the associated mining models have been processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2014e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2014e-126">See Also</span></span>  
 [<span data-ttu-id="2014e-127">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="2014e-127">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
