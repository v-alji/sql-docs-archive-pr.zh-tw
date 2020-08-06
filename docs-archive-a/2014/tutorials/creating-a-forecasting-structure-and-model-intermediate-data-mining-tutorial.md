---
title: 建立預測結構和模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d77b15a9a8efe9a9c6faec49a2274ee182706992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686570"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="ae2e0-102">建立預測結構和模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="ae2e0-102">Creating a Forecasting Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="ae2e0-103">接下來，您將使用資料採礦精靈，根據您剛建立的資料來源檢視建立新的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-103">Next, you will use the Data Mining Wizard to create a new mining structure and mining model based on the data source view that you just created.</span></span> <span data-ttu-id="ae2e0-104">在這項工作中，您將指定採礦模型應使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-104">In this task you will specify that the mining model should use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
### <a name="to-create-a-forecasting-mining-structure"></a><span data-ttu-id="ae2e0-105">若要建立預測採礦結構</span><span class="sxs-lookup"><span data-stu-id="ae2e0-105">To create a forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="ae2e0-106">在的方案總管中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 [**採礦結構**]，然後選取 [**新增採礦結構**]。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="ae2e0-107">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="ae2e0-108">在 [**選取定義方法**] 頁面上，確認已選取 [**從現有的關係資料庫或資料倉儲**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-108">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ae2e0-109">在 [**建立資料採礦結構**] 頁面上，于 [**您要使用哪一項資料採礦技術？**] 底下，選取 [ **Microsoft 時間序列**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-109">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Time Series**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ae2e0-110">在 [**選取資料來源視圖**] 頁面的 [**可用的資料來源視圖**] 底下，選取 [ **salesbyregion.dsv**]。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-110">On the **Select Data Source View** page, under **Available data source views**, select **SalesByRegion**.</span></span>  
  
6.  <span data-ttu-id="ae2e0-111">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-111">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="ae2e0-112">在 [**指定資料表類型**] 頁面上，確定已選取 [vTimeSeries] 資料表之 [**案例**] 資料行中的核取方塊，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-112">On the **Specify Table Types** page, ensure that the check box in the **Case** column for the vTimeSeries table is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="ae2e0-113">在 [**指定定型資料**] 頁面上，選取 ModelRegion 和 ReportingDate 資料行之 [索引**鍵**] 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-113">On the **Specify the Training Data** page, select the check boxes in the **Key** column for the ModelRegion and ReportingDate columns.</span></span>  
  
     <span data-ttu-id="ae2e0-114">ReportingDate 應該已依預設選取，因為您在建立資料來源檢視時，已將這個資料行指定為邏輯主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-114">ReportingDate should be selected by default, because you specified this column as the logical primary key when you created the data source view.</span></span> <span data-ttu-id="ae2e0-115">加入 ModelRegion 做為第二個索引鍵時，等於要求演算法針對列於此欄位上的各模型與區域組合，建立個別的時間序列。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-115">By adding ModelRegion as a second key, you are telling the algorithm to create a separate time series for each combination of model and region listed in this field.</span></span>  
  
9. <span data-ttu-id="ae2e0-116">在 [數量] 資料行的 [**輸入**] 和 [**可預測**] 資料行中選取核取方塊，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-116">Select the check boxes in the **Input** and **Predictable** columns for the Quantity, column, and then click **Next**.</span></span>  
  
     <span data-ttu-id="ae2e0-117">藉由選取 [**可預測**]，表示您想要對此資料行中的資料建立預測。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-117">By selecting **Predictable**, you indicate that you want to create forecasts on the data in this column.</span></span> <span data-ttu-id="ae2e0-118">不過，由於您要根據過去的資料進行預測，因此您必須加入資料行做為輸入內容。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-118">However, because you want to base the forecasts on past data, you must also add the column as an input.</span></span>  
  
10. <span data-ttu-id="ae2e0-119">在 [**指定欄位的內容和資料類型**] 頁面上，查看選取專案。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-119">On the page **Specify Columns' Content and Data Type**, review the selections.</span></span>  
  
     <span data-ttu-id="ae2e0-120">ModelRegion 資料行會指定為索引**鍵**資料行，而 ReportingDate 資料行則會自動指定為**key Time**資料行。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-120">The ModelRegion column is designated as a **Key** column and the ReportingDate column is automatically designated as a **Key Time** column.</span></span> <span data-ttu-id="ae2e0-121">每一種類型的索引鍵，您只能有一個。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-121">You can have only one of each type of key.</span></span>  
  
11. <span data-ttu-id="ae2e0-122">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-122">Click **Next**.</span></span>  
  
12. <span data-ttu-id="ae2e0-123">在 [**正在完成嚮導]** 頁面上，針對 [**採礦結構名稱**] 輸入 `Forecasting` 。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-123">On the **Completing the Wizard** page, for **Mining structure name**, type `Forecasting`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae2e0-124">在時間序列模型中，不提供啟用鑽研的選項。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-124">The option to enable drillthrough is not available for time series models.</span></span>  
  
13. <span data-ttu-id="ae2e0-125">在 [**採礦模型名稱**] 中，輸入 `Forecasting` ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-125">In **Mining model name**, type `Forecasting`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="ae2e0-126">[資料採礦設計師] 隨即開啟，以顯示 `Forecasting` 您剛建立的「採礦結構」。</span><span class="sxs-lookup"><span data-stu-id="ae2e0-126">Data Mining Designer opens to display the `Forecasting` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ae2e0-127">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="ae2e0-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ae2e0-128">&#40;中繼資料採礦教學課程修改預測結構&#41;</span><span class="sxs-lookup"><span data-stu-id="ae2e0-128">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae2e0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2e0-129">See Also</span></span>  
 <span data-ttu-id="ae2e0-130">[資料採礦設計工具](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="ae2e0-130">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="ae2e0-131">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="ae2e0-131">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
