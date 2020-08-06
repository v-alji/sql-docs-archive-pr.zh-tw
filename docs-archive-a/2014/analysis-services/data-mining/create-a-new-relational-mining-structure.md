---
title: 建立新的關聯式採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b41dd3ac2e6144011c1b3acde27c4b5829a1661
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592338"
---
# <a name="create-a-new-relational-mining-structure"></a><span data-ttu-id="81e7a-102">建立新的關聯式採礦結構</span><span class="sxs-lookup"><span data-stu-id="81e7a-102">Create a New Relational Mining Structure</span></span>
  <span data-ttu-id="81e7a-103">使用資料採礦嚮導來建立新的採礦結構、使用關係資料庫或其他來源中的資料，然後將結構和任何相關模型儲存至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="81e7a-103">Use the Data Mining Wizard to create a new mining structure, using data from a relational database or other source, and then save the structure and any related models to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="to-create-a-relational-mining-structure"></a><span data-ttu-id="81e7a-104">若要建立關聯式採礦結構</span><span class="sxs-lookup"><span data-stu-id="81e7a-104">To create a relational mining structure</span></span>  
  
1.  <span data-ttu-id="81e7a-105">在方案總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中的 [採礦結構]\*\*\*\* 資料夾，然後按一下 [新增採礦結構]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-105">In Solution Explorer, right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure**.</span></span>  
  
     <span data-ttu-id="81e7a-106">就會開啟資料採礦精靈。</span><span class="sxs-lookup"><span data-stu-id="81e7a-106">The Data Mining Wizard opens.</span></span>  
  
2.  <span data-ttu-id="81e7a-107">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="81e7a-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="81e7a-108">在 [選取定義方法]\*\*\*\* 頁面上，選取 [從現有的關聯式資料庫或資料倉儲]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-108">On the **Select the Definition Method** page, select **From existing relational database or data warehouse**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="81e7a-109">在 [選取資料採礦技術]\*\*\*\* 頁面上，選取您要使用的資料採礦演算法，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-109">On the **Select the Data Mining Technique** page, select the data mining algorithm that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="81e7a-110">如需資料採礦演算法的詳細資訊，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="81e7a-110">For more information about data mining algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="81e7a-111">在 [選取資料來源檢視]\*\*\*\* 頁面上，在 [可用的資料來源檢視]\*\*\*\* 之下，按一下您要使用的資料來源檢視，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-111">On the **Select Data Source View** page, under **Available data source views**, click the data source view that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="81e7a-112">如需建立資料來源檢視的詳細資訊，請參閱 [多維度模型中的資料來源檢視](../multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="81e7a-112">For more information about creating a data source view, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
6.  <span data-ttu-id="81e7a-113">在 [指定資料表類型]\*\*\*\* 頁面上，[輸入資料表]\*\*\*\* 之下，選取案例資料表和巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="81e7a-113">On the **Specify Table Types** page, under **Input tables**, select a case table and a nested table.</span></span>  
  
7.  <span data-ttu-id="81e7a-114">在 [指定培訓資料]\*\*\*\* 頁面上，[採礦模型結構]\*\*\*\* 之下，選取索引鍵、輸入和可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="81e7a-114">On the **Specify the Training Data** page, under **Mining model structure**, select the key, input, and predictable columns.</span></span>  
  
     <span data-ttu-id="81e7a-115">在選取可預測資料行之後，您可以按一下 [建議]\*\*\*\* 按鈕來開啟 [建議相關資料行]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="81e7a-115">After you select the predictable column, you can click the **Suggest** button to open the **Suggest Related Columns** dialog box.</span></span> <span data-ttu-id="81e7a-116">您可以按一下此對話方塊中的 [確定]\*\*\*\* 來接受建議的資料行，在採礦結構中包含選取的資料行，或先在 [輸入]\*\*\*\* 資料行中變更選擇，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-116">You can accept the suggested columns by clicking **OK** in this dialog box to include the selected columns in the mining structure, or you can change the selections in the **Input** column first, and then click **OK**.</span></span> <span data-ttu-id="81e7a-117">若要忽略建議，請按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-117">To ignore the suggestions, click **Cancel**.</span></span>  
  
8.  <span data-ttu-id="81e7a-118">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="81e7a-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="81e7a-119">在 [指定資料行的內容和資料類型]\*\*\*\* 頁面上，在 [採礦模型結構]\*\*\*\* 之下，您可以調整每一個資料行的內容類型和資料類型。</span><span class="sxs-lookup"><span data-stu-id="81e7a-119">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, you can adjust the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81e7a-120">您可以按一下 [偵測]\*\*\*\*，來自動偵測資料行是包含連續或分隔資料。</span><span class="sxs-lookup"><span data-stu-id="81e7a-120">You can click **Detect** to automatically detect whether a column contains continuous or discrete data.</span></span> <span data-ttu-id="81e7a-121">按一下此按鈕之後，資料行內容和資料類型將在 [內容類型]\*\*\*\* 和 [資料類型]\*\*\*\* 資料行中更新。</span><span class="sxs-lookup"><span data-stu-id="81e7a-121">After you click this button, the column content and data types will be updated in the **Content Type** and **Data Type** columns.</span></span> <span data-ttu-id="81e7a-122">如需內容類型及資料類型的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md) 和[資料類型 &#40;資料採礦&#41;](data-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="81e7a-122">For more information about content types and data types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md) and [Data Types &#40;Data Mining&#41;](data-types-data-mining.md).</span></span>  
  
10. <span data-ttu-id="81e7a-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="81e7a-123">Click **Next**.</span></span>  
  
11. <span data-ttu-id="81e7a-124">在 [正在完成精靈]\*\*\*\* 頁面上，提供採礦結構的名稱和要建立的相關初始採礦模型，然後按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81e7a-124">On the **Completing the Wizard** page, provide a name for the mining structure and the related initial mining model that will be created, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e7a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e7a-125">See Also</span></span>  
 [<span data-ttu-id="81e7a-126">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="81e7a-126">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
