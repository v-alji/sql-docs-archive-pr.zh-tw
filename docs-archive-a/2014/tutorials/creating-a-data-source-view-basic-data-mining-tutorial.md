---
title: 建立資料來源視圖 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4582845c905ef95601cbff2c810633f0cc901e3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594288"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a><span data-ttu-id="80bbf-102">建立資料來源檢視 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="80bbf-102">Creating a Data Source View (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="80bbf-103">資料來源檢視建立在資料來源之上，而且會定義一個資料子集，然後您可以在採礦結構中使用該資料子集。</span><span class="sxs-lookup"><span data-stu-id="80bbf-103">A data source view is built on a data source and defines a subset of the data, which you can then use in your mining structures.</span></span> <span data-ttu-id="80bbf-104">您也可以使用資料來源檢視加入資料行、建立導出資料行與彙總，以及加入具名檢視。</span><span class="sxs-lookup"><span data-stu-id="80bbf-104">You can also use the data source view to add columns, create calculated columns and aggregates, and add named views.</span></span> <span data-ttu-id="80bbf-105">您可以使用資料來源檢視，在不修改原始資料來源的情況下，選取與專案相關的資料、建立資料表之間的關聯性，以及修改資料的結構。</span><span class="sxs-lookup"><span data-stu-id="80bbf-105">By using data source views, you can select the data that relates to your project, establish relationships between tables, and modify the structure of the data, without modifying the original data source.</span></span> <span data-ttu-id="80bbf-106">如需詳細資訊，請參閱 [多維度模型中的資料來源檢視](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)。</span><span class="sxs-lookup"><span data-stu-id="80bbf-106">For more information, see [Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).</span></span>  
  
### <a name="to-create-a-data-source-view"></a><span data-ttu-id="80bbf-107">若要建立資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="80bbf-107">To create a data source view</span></span>  
  
1.  <span data-ttu-id="80bbf-108">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="80bbf-108">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="80bbf-109">在 [歡迎使用資料來源檢視精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80bbf-109">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="80bbf-110">在 [**選取資料來源**] 頁面的 [**關聯式資料來源**] 底下，選取您在上一個工作中建立的 [艾德公司 DW 2012] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="80bbf-110">On the **Select a Data Source** page, under **Relational data sources**, select the Adventure Works DW 2012 data source that you created in the last task.</span></span> <span data-ttu-id="80bbf-111">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80bbf-111">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80bbf-112">如果您想要建立資料來源，請以滑鼠右鍵按一下 [**資料來源**]，然後按一下 [**新增資料來源**]，以啟動 [資料來源嚮導]。</span><span class="sxs-lookup"><span data-stu-id="80bbf-112">If you want to create a data source, right-click **Data Sources** and then click **New Data Source** to start the Data Source Wizard.</span></span>  
  
4.  <span data-ttu-id="80bbf-113">在 [**選取資料表和資料檢視]** 頁面上，選取下列物件，然後按一下向右箭號，將它們包含在 [新資料來源] 視圖中：</span><span class="sxs-lookup"><span data-stu-id="80bbf-113">On the **Select Tables and Views** page, select the following objects, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   <span data-ttu-id="80bbf-114">\*\*ProspectiveBuyer (dbo) \*\* -潛在自行車購買者的資料表</span><span class="sxs-lookup"><span data-stu-id="80bbf-114">**ProspectiveBuyer (dbo)** - table of prospective bike buyers</span></span>  
  
    -   <span data-ttu-id="80bbf-115">\*\*vTargetMail (dbo) \*\*查看過去自行車購買者的歷程記錄資料</span><span class="sxs-lookup"><span data-stu-id="80bbf-115">**vTargetMail (dbo)** - view of historical data about past bike buyers</span></span>  
  
5.  <span data-ttu-id="80bbf-116">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80bbf-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="80bbf-117">根據預設，在 [**正在完成嚮導]** 頁面上，[資料來源] 視圖的名稱為 [艾德作品] [DW 2012]。</span><span class="sxs-lookup"><span data-stu-id="80bbf-117">On the **Completing the Wizard** page, by default the data source view is named Adventure Works DW 2012.</span></span> <span data-ttu-id="80bbf-118">將 [名稱] 變更為 `Targeted Mailing` ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="80bbf-118">Change the name to `Targeted Mailing`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="80bbf-119">新的 [資料來源] 視圖隨即在 **[目標郵寄] [Design]** ] 索引標籤中開啟。</span><span class="sxs-lookup"><span data-stu-id="80bbf-119">The new data source view opens in the **Targeted Mailing.dsv [Design]** tab.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="80bbf-120">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="80bbf-120">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="80bbf-121">建立資料來源 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="80bbf-121">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="80bbf-122">下一課</span><span class="sxs-lookup"><span data-stu-id="80bbf-122">Next Lesson</span></span>  
 [<span data-ttu-id="80bbf-123">第2課：建立目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="80bbf-123">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="80bbf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80bbf-124">See Also</span></span>  
 [<span data-ttu-id="80bbf-125">定義資料來源檢視 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="80bbf-125">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
