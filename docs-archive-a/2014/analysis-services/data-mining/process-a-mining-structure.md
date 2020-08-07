---
title: 處理採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d25a927ae61ee5ffadf4ca21073a1c04cdb542
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703446"
---
# <a name="process-a-mining-structure"></a><span data-ttu-id="76e3d-102">處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="76e3d-102">Process a Mining Structure</span></span>
  <span data-ttu-id="76e3d-103">在您可以瀏覽或使用與採礦結構相關聯的採礦模型之前，必須部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案並處理採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="76e3d-103">Before you can browse or work with the mining models that are associated with a mining structure, you have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span> <span data-ttu-id="76e3d-104">此外，如果您變更採礦結構或採礦模型，會提示您重新部署和處理它們。</span><span class="sxs-lookup"><span data-stu-id="76e3d-104">Also, if you make a change to the mining structure or mining models, you will be prompted to redeploy and process them.</span></span> <span data-ttu-id="76e3d-105">在 **中之資料採礦設計師的** [採礦結構] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 索引標籤中處理結構時，會處理所有相關聯的模型。</span><span class="sxs-lookup"><span data-stu-id="76e3d-105">Processing the structure in the **Mining Structure** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] processes all the associated models.</span></span>  
  
 <span data-ttu-id="76e3d-106">您可以使用下列工具來處理採礦結構：</span><span class="sxs-lookup"><span data-stu-id="76e3d-106">You can process a mining structure by using these tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   <span data-ttu-id="76e3d-107">XMLA：處理命令</span><span class="sxs-lookup"><span data-stu-id="76e3d-107">XMLA: Process command</span></span>  
  
 <span data-ttu-id="76e3d-108">如需如何處理個別模型的資訊，請參閱 [處理採礦模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="76e3d-108">For information about how to process individual models, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a><span data-ttu-id="76e3d-109">若要使用 SQL Server 資料工具來處理採礦結構和所有相關聯的採礦模型</span><span class="sxs-lookup"><span data-stu-id="76e3d-109">To process a mining structure and all associated mining models using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="76e3d-110">從 **中的** [採礦模型] **功能表項目選取** [處理採礦結構和所有模型] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76e3d-110">Select **Process Mining Structure and All Models** from the **Mining Model** menu item in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
     <span data-ttu-id="76e3d-111">如果您變更了結構，在處理模型之前，會提示您重新部署結構。</span><span class="sxs-lookup"><span data-stu-id="76e3d-111">If you made changes to the structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="76e3d-112">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="76e3d-112">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="76e3d-113">按一下 [**處理採礦結構 \<structure> -** ] 對話方塊中的 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="76e3d-113">Click **Run** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
     <span data-ttu-id="76e3d-114">隨即開啟 **[處理進度]** 對話方塊，以顯示模型處理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="76e3d-114">The **Process Progress** dialog box opens to display the details of model processing.</span></span>  
  
3.  <span data-ttu-id="76e3d-115">在模型完成處理之後，按一下 **[處理進度]** 對話方塊中的 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="76e3d-115">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="76e3d-116">在 [**處理採礦結構 \<structure> -** ] 對話方塊中，按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="76e3d-116">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e3d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76e3d-117">See Also</span></span>  
 [<span data-ttu-id="76e3d-118">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="76e3d-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
