---
title: " (中繼資料採礦教學課程修改預測結構) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9acf410fe04c53493e559257832e5e21727bc45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584906"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="3125f-102">修改預測結構 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="3125f-102">Modifying the Forecasting Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="3125f-103">上一項工作所建立的採礦結構包含單一預測模型。</span><span class="sxs-lookup"><span data-stu-id="3125f-103">The mining structure that you created in the previous task contains a single forecasting model.</span></span> <span data-ttu-id="3125f-104">在處理和瀏覽這個模型之前，您必須先稍微變更它的結構，並修改其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="3125f-104">Before you process and explore the model, you must change its structure slightly and modify one of its properties.</span></span>  
  
## <a name="modifying-the-mining-structure"></a><span data-ttu-id="3125f-105">修改採礦結構</span><span class="sxs-lookup"><span data-stu-id="3125f-105">Modifying the Mining Structure</span></span>  
 <span data-ttu-id="3125f-106">您可以使用資料採礦設計師的 [**採礦結構**] 索引標籤來變更此採礦結構。</span><span class="sxs-lookup"><span data-stu-id="3125f-106">You can change the mining structure by using the **Mining Structure** tab of Data Mining Designer.</span></span> <span data-ttu-id="3125f-107">當您使用資料採礦精靈建立此模型時，會使用三個資料行：ReportingDate、ModelRegion 和 Quantity。</span><span class="sxs-lookup"><span data-stu-id="3125f-107">When you created the model with the Data Mining Wizard, you used three columns: ReportingDate, ModelRegion, and Quantity.</span></span> <span data-ttu-id="3125f-108">不過，[**預測**] 資料表也包含 [金額] 資料行，您可以用來預測銷售金額。</span><span class="sxs-lookup"><span data-stu-id="3125f-108">However, the **Forecasting** table also contains an Amount column, which you can use to forecast the amount of sales.</span></span> <span data-ttu-id="3125f-109">藉由使用 [**採礦結構**] 索引標籤，您可以將此資料行從 [資料來源] 視圖加入至 [採礦結構]。</span><span class="sxs-lookup"><span data-stu-id="3125f-109">By using the **Mining Structure** tab, you can add this column from the data source view to the mining structure.</span></span>  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a><span data-ttu-id="3125f-110">若要將 [金額] 資料行加入預測採礦結構中</span><span class="sxs-lookup"><span data-stu-id="3125f-110">To add the Amount column to the Forecasting mining structure</span></span>  
  
1.  <span data-ttu-id="3125f-111">在資料採礦設計師的 [**採礦結構**] 索引標籤上，于 [**資料來源視圖**] 窗格中，選取 [vTimeSeries] 資料表中的 [金額] 資料行。</span><span class="sxs-lookup"><span data-stu-id="3125f-111">On the **Mining Structure** tab of Data Mining Designer, in the **Data Source View** pane, select the Amount column in the vTimeSeries table.</span></span>  
  
2.  <span data-ttu-id="3125f-112">從 [**資料來源視圖**] 窗格中，將 [金額] 資料行拖曳至**預測**結構的資料行清單中。</span><span class="sxs-lookup"><span data-stu-id="3125f-112">Drag the Amount column from the **Data Source View** pane into the list of columns for the **Forecasting** structure.</span></span>  
  
     <span data-ttu-id="3125f-113">[金額] 資料行現在已包含在**預測**採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="3125f-113">The Amount column is now included in the **Forecasting** mining structure.</span></span>  
  
## <a name="modifying-the-columns-in-the-mining-model"></a><span data-ttu-id="3125f-114">修改採礦模型中的資料行</span><span class="sxs-lookup"><span data-stu-id="3125f-114">Modifying the Columns in the Mining Model</span></span>  
 <span data-ttu-id="3125f-115">由於您在結構中加入了新的資料行，因此，您必須定義模型使用這個資料行的方式。</span><span class="sxs-lookup"><span data-stu-id="3125f-115">Because you added a new column to the structure, you must define how the model will use the column.</span></span> <span data-ttu-id="3125f-116">您可以在資料採礦設計師的 [**採礦模型**] 索引標籤上，指定資料行的使用方式。</span><span class="sxs-lookup"><span data-stu-id="3125f-116">You can specify how the column will be used on the **Mining Models** tab of Data Mining Designer.</span></span>  
  
 <span data-ttu-id="3125f-117">[**採礦模型**] 索引標籤會在方格的 [**結構**] 資料行中列出採礦結構所包含的資料行，並在具有模型名稱的資料行中列出該採礦模型所包含的資料行（在此案例中為**預測**）。</span><span class="sxs-lookup"><span data-stu-id="3125f-117">The **Mining Models** tab lists the columns that the mining structure contains in the **Structure** column of the grid, and lists the columns that the mining model contains in the column that has the name of the model, in this case **Forecasting**.</span></span> <span data-ttu-id="3125f-118">請按一下資料行的名稱來加以修改。</span><span class="sxs-lookup"><span data-stu-id="3125f-118">Click the names of the columns to make modifications.</span></span> <span data-ttu-id="3125f-119">在 [**預測**] 採礦模型中，[金額] 資料行會當做輸入資料行使用，也可用來預測未來的銷售。</span><span class="sxs-lookup"><span data-stu-id="3125f-119">In the **Forecasting** mining model, the Amount column is used as an input column and is also used to forecast future sales.</span></span> <span data-ttu-id="3125f-120">因此，您必須設定資料行的屬性，使它既能做為輸入資料行，也能做為可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="3125f-120">Therefore, you must set the properties of the column so that it can be used as both an input column and a predictable column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3125f-121">在 [**採礦模型**] 索引標籤中，您也可以建立以相同結構為基礎的新模型，而且您可以調整每個模型的演算法和資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="3125f-121">In the **Mining Models** tab, you can also create new models based on the same structure, and you can adjust the algorithm and column properties for each model.</span></span> <span data-ttu-id="3125f-122">不過，您必須先處理模型，然後這些變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="3125f-122">However, you must process the model before these changes take effect.</span></span>  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a><span data-ttu-id="3125f-123">若要定義 [金額] 資料行的使用方式</span><span class="sxs-lookup"><span data-stu-id="3125f-123">To define how the Amount column will be used</span></span>  
  
1.  <span data-ttu-id="3125f-124">在 [**採礦模型**] 索引標籤上方格的 [**預測**] 資料行中，按一下 [金額] 資料列中的資料格。</span><span class="sxs-lookup"><span data-stu-id="3125f-124">In the **Forecasting** column of the grid on the **Mining Models** tab, click the cell in the Amount row.</span></span>  
  
2.  <span data-ttu-id="3125f-125">從清單中選取 [**預測**]。</span><span class="sxs-lookup"><span data-stu-id="3125f-125">Select **Predict** from the list.</span></span>  
  
     <span data-ttu-id="3125f-126">現在，Amount 資料行既是輸入資料行，也是可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="3125f-126">The Amount column is now both an input column and a predictable column.</span></span>  
  
 <span data-ttu-id="3125f-127">您也可以選取資料行並開啟 [**屬性**] 視窗，以變更個別資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="3125f-127">You can also change the properties of individual columns by selecting the column and opening the **Properties** window.</span></span> <span data-ttu-id="3125f-128">若要開啟 [**屬性**] 視窗，請以滑鼠右鍵按一下資料行名稱，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="3125f-128">To open the **Properties** window, right-click the column name, and then select **Properties**.</span></span> <span data-ttu-id="3125f-129">如果您變更個別模型的資料行屬性，您只能變更這個模型的屬性。</span><span class="sxs-lookup"><span data-stu-id="3125f-129">If you change a property within the column for an individual model, you can change the properties only for that model.</span></span> <span data-ttu-id="3125f-130">不過，當您變更 [**結構**] 資料行中的屬性時，變更會影響與該結構相關聯的每個模型。</span><span class="sxs-lookup"><span data-stu-id="3125f-130">However, when you change a property within the **Structure** column, the change affects every model that is associated with the structure.</span></span> <span data-ttu-id="3125f-131">每當變更模型或結構之後，都必須重新處理才能讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="3125f-131">Whenever you make changes to the model or structure, you must reprocess to see the effects.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3125f-132">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="3125f-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3125f-133">自訂及處理預測模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="3125f-133">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="3125f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3125f-134">See Also</span></span>  
 <span data-ttu-id="3125f-135">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3125f-135">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="3125f-136">採礦模型 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="3125f-136">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
