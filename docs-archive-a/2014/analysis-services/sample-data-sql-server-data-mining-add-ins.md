---
title: SQL Server 資料採礦增益集的範例資料 () |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17da9a42f4d76f5c271d5b225cf897a8ac2e97ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592929"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="f4740-102">取樣資料 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="f4740-102">Sample Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="f4740-103">![資料採礦功能區中的分割資料精靈](media/dmc-partition.gif "資料採礦功能區中的分割資料精靈")</span><span class="sxs-lookup"><span data-stu-id="f4740-103">![Partition Data wizard in Data Mining ribbon](media/dmc-partition.gif "Partition Data wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="f4740-104">**範例資料**嚮導可讓您輕鬆地將來源資料分割成兩個集合，一個用於建立 (定型) 模型，另一個用於測試模型。</span><span class="sxs-lookup"><span data-stu-id="f4740-104">The **Sample Data** wizard makes it easy to divide your source data into two sets, one for building (training) the model and one for testing the model.</span></span> <span data-ttu-id="f4740-105">此精靈也提供一個重新進行資料取樣的選項，藉以建立一個更能代表您目標的新資料集。</span><span class="sxs-lookup"><span data-stu-id="f4740-105">This wizard also provides an option for resampling the data to build a new data set that better represents your target.</span></span>  
  
 <span data-ttu-id="f4740-106">為定型和測試模型而建立正確類型的資料是資料採礦的一個重要部分，但是如果沒有正確的工具，也是會乏味無趣。</span><span class="sxs-lookup"><span data-stu-id="f4740-106">Creating the right kind of data for training and testing your models is an important part of data mining, but one that can be tedious without the right tools.</span></span> <span data-ttu-id="f4740-107">精靈會執行分層取樣，確保訓練和測試集之間對稱。</span><span class="sxs-lookup"><span data-stu-id="f4740-107">The wizard performs stratified sampling to make sure that training and testing sets are well balanced.</span></span>  
  
## <a name="random-sampling-and-oversampling"></a><span data-ttu-id="f4740-108">隨機取樣與超取樣</span><span class="sxs-lookup"><span data-stu-id="f4740-108">Random Sampling and Oversampling</span></span>  
 <span data-ttu-id="f4740-109">.</span><span class="sxs-lookup"><span data-stu-id="f4740-109">.</span></span> <span data-ttu-id="f4740-110">隨機取樣是確保您用於測試模型的資料能夠清楚代表您用於建立模型之資料的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="f4740-110">Random sampling is the best way to ensure that the data you use for testing a model fairly represents the data that you use for creating the model.</span></span> <span data-ttu-id="f4740-111">您可以隨機取樣存放在 Excel 中或外部資料來源中的資料</span><span class="sxs-lookup"><span data-stu-id="f4740-111">You can randomly sample data that is stored in Excel or in an external data source</span></span>  
  
 <span data-ttu-id="f4740-112">如果您使用隨機取樣選項，**範例資料**wizard 會自動建立定型和測試資料集，並將其輸出到個別的 Excel 工作表，以供日後參考。</span><span class="sxs-lookup"><span data-stu-id="f4740-112">If you use the random sampling option, the **Sample Data** wizard automatically creates training and test data sets and outputs them into separate Excel worksheets for later reference.</span></span>  
  
 <span data-ttu-id="f4740-113">如果您的資料儲存在 Excel 活頁簿中，而不是外部資料源，則您也可以選擇使用*超取樣*。</span><span class="sxs-lookup"><span data-stu-id="f4740-113">If your data is stored in an Excel workbook, and not an external data source, you also have the option to use *oversampling*.</span></span> <span data-ttu-id="f4740-114">使用此選項時，您會指定一個在資料中可能很少見的目標值，精靈將會收集包含較多目標值的對稱集。</span><span class="sxs-lookup"><span data-stu-id="f4740-114">With this option, you specify a target value that might be scarce in your data, and the wizard will collect a balanced set that includes more of the target value.</span></span> <span data-ttu-id="f4740-115">您可以導引精靈達成目標百分比，或建立特定數目的資料列。</span><span class="sxs-lookup"><span data-stu-id="f4740-115">You can direct the wizard to achieve a targeted percentage, or to create a certain number of rows.</span></span>  
  
 <span data-ttu-id="f4740-116">如果您使用超取樣選項，**範例資料**wizard 會建立新的工作表，其中包含新平衡的範例資料。</span><span class="sxs-lookup"><span data-stu-id="f4740-116">If you use the oversampling option, the **Sample Data** wizard creates a new worksheet that contains the newly balanced sample data.</span></span>  
  
## <a name="using-the-sample-data-wizard"></a><span data-ttu-id="f4740-117">使用取樣資料精靈</span><span class="sxs-lookup"><span data-stu-id="f4740-117">Using the Sample Data Wizard</span></span>  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a><span data-ttu-id="f4740-118">將分割區為定型集和測試集</span><span class="sxs-lookup"><span data-stu-id="f4740-118">To separate data into training and testing sets</span></span>  
  
1.  <span data-ttu-id="f4740-119">在 [**資料採礦**] 功能區中，按一下 [**範例資料**]。</span><span class="sxs-lookup"><span data-stu-id="f4740-119">In the **Data Mining** ribbon, click **Sample Data**.</span></span>  
  
2.  <span data-ttu-id="f4740-120">在 [**選取來源資料**] 頁面上，指定您要分割的**資料**是在 Excel 範圍或資料表中，或是在外部資料源中。</span><span class="sxs-lookup"><span data-stu-id="f4740-120">On the **Select Source Data** page, specify whether the **data** that you want to partition is in an Excel range or table, or in an external data source.</span></span>  
  
3.  <span data-ttu-id="f4740-121">在 [**選取取樣類型**] 頁面上，指定是否要透過隨機取樣來建立定型和測試資料集，或依超取樣建立新的資料集。</span><span class="sxs-lookup"><span data-stu-id="f4740-121">On the **Select Sampling Type** page, specify whether you want to create training and test data sets by random sampling, or create a new data set by oversampling.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4740-122">如果您使用的是外部資料來源，則僅能使用隨機取樣選項。</span><span class="sxs-lookup"><span data-stu-id="f4740-122">If you are using an external data source, only the random sampling option is available.</span></span> <span data-ttu-id="f4740-123">如果想到搭配外部資料使用超取樣，您可以使用 Excel 資料連接，將資料匯入到 Excel 活頁簿，然後再使用 [取樣資料精靈]。</span><span class="sxs-lookup"><span data-stu-id="f4740-123">If you want to use oversampling with external data, you can import the data to an Excel workbook by using an Excel data connection, and then use the Sample Data wizard.</span></span>  
  
4.  <span data-ttu-id="f4740-124">設定所選取樣方法的特定選項。</span><span class="sxs-lookup"><span data-stu-id="f4740-124">Set options specific to the sampling method that you selected.</span></span>  
  
    -   <span data-ttu-id="f4740-125">若是隨機取樣，指定要用於測試之原始資料的百分比，或是要在測試資料集中使用之資料列的總數。</span><span class="sxs-lookup"><span data-stu-id="f4740-125">For random sampling, specify either a percentage of the original data to use for testing, or the total number of rows to use in the test data set.</span></span>  
  
    -   <span data-ttu-id="f4740-126">若是超取樣，則選取您要強調的資料行和值。</span><span class="sxs-lookup"><span data-stu-id="f4740-126">For oversampling, select the column and value that you want to emphasize.</span></span> <span data-ttu-id="f4740-127">然後，在新資料集中指定資料列的總數，以及在新資料集中，應該包含目標值之資料列的百分比。</span><span class="sxs-lookup"><span data-stu-id="f4740-127">Then, specify the total number of rows in the new data set, and the percentage of rows in the new data set that should include the target value.</span></span>  
  
         <span data-ttu-id="f4740-128">超取樣的目標值必須是離散值；您無法超取樣連續數值資料。</span><span class="sxs-lookup"><span data-stu-id="f4740-128">The target value for oversampling must be a discrete value; you cannot oversample continuous numeric data.</span></span>  
  
5.  <span data-ttu-id="f4740-129">在 [**完成] 頁面**上，接受新資料集的預設名稱，或輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4740-129">On the **Finish page**, accept the default names for the new data sets, or type a new name.</span></span>  
  
     <span data-ttu-id="f4740-130">此精靈會為每個資料集建立新的工作表。</span><span class="sxs-lookup"><span data-stu-id="f4740-130">The wizard creates new worksheets for each set of data.</span></span>  
  
 <span data-ttu-id="f4740-131">適用於 Excel 的資料採礦用戶端中大部分的精靈也提供將資料隨機分割為定型與測試資料集的選項。</span><span class="sxs-lookup"><span data-stu-id="f4740-131">Most of the wizards in the Data Mining Client for Excel also provide an option to randomly separate your data into training and testing sets.</span></span> <span data-ttu-id="f4740-132">但是，如果您使用這些精靈，您的資料會保留在相同的工作表 (或其他資料來源) 中，而關於特定資料列為測試案例或定型案例的相關資訊，則會儲存在內部。</span><span class="sxs-lookup"><span data-stu-id="f4740-132">However, if you use the wizards, your data stays in the same worksheet (or other data source), and the information about whether a particular row is a test case or training case is stored internally.</span></span> <span data-ttu-id="f4740-133">相反地，當您使用「**範例資料**」 wizard 時，測試和定型資料會輸出到不同的工作表，以方便參考。</span><span class="sxs-lookup"><span data-stu-id="f4740-133">In contrast, when you use the **Sample Data** wizard, the testing and training data are output to separate worksheets for easy reference.</span></span>  
  
## <a name="related-options"></a><span data-ttu-id="f4740-134">相關的選項</span><span class="sxs-lookup"><span data-stu-id="f4740-134">Related Options</span></span>  
 <span data-ttu-id="f4740-135">當您逐步進行精靈時，會有下列選項：</span><span class="sxs-lookup"><span data-stu-id="f4740-135">As you progress through the wizard, you will have these options:</span></span>  
  
|<span data-ttu-id="f4740-136">選項</span><span class="sxs-lookup"><span data-stu-id="f4740-136">Options</span></span>|<span data-ttu-id="f4740-137">註解</span><span class="sxs-lookup"><span data-stu-id="f4740-137">Comments</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f4740-138">選取來源資料對話方塊 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="f4740-138">Select Source Data Dialog Box (Data Mining Client for Excel)</span></span>|<span data-ttu-id="f4740-139">選取包含資料的 Excel 範圍或資料表。</span><span class="sxs-lookup"><span data-stu-id="f4740-139">Select an Excel range or table that contains the data.</span></span> <span data-ttu-id="f4740-140">如果您要使用外部資料，可以使用關聯式資料，不過資料必須包含在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源中。</span><span class="sxs-lookup"><span data-stu-id="f4740-140">If you want to use external data, the data can be relational, but it must be included in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="f4740-141">T</span><span class="sxs-lookup"><span data-stu-id="f4740-141">T</span></span>|  
|<span data-ttu-id="f4740-142">選取取樣類型頁面 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="f4740-142">Select Sampling Type Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="f4740-143">如果您使用外部資料來源，則僅能使用隨機取樣選項。</span><span class="sxs-lookup"><span data-stu-id="f4740-143">If you use an external data source, you are limited to using the random sampling option.</span></span> <span data-ttu-id="f4740-144">此外，您必須使用 [資料**列計數**] 選項，指定要在最後一個資料集中建立的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="f4740-144">Also, you must specify the number of rows to create in the final data set, by using the **Row count** option.</span></span> <span data-ttu-id="f4740-145">您無法指定來源資料的百分比。</span><span class="sxs-lookup"><span data-stu-id="f4740-145">You cannot specify a percentage of the source data.</span></span>|  
|<span data-ttu-id="f4740-146">隨機取樣頁面 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="f4740-146">Random Sampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="f4740-147">您可以從來源複製某個百分比的資料列，或特定資料列數目。</span><span class="sxs-lookup"><span data-stu-id="f4740-147">You can copy a percentage of rows from the source, or a specific number of rows.</span></span>|  
|<span data-ttu-id="f4740-148">超取樣頁面 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="f4740-148">Oversampling Page (Data Mining Client for Excel)</span></span>|<span data-ttu-id="f4740-149">**目標狀態**</span><span class="sxs-lookup"><span data-stu-id="f4740-149">**Target state**</span></span><br /><br /> <span data-ttu-id="f4740-150">從清單選取原始資料集中低於適當比例的值。</span><span class="sxs-lookup"><span data-stu-id="f4740-150">Select a value from the list that is underrepresented in the original data set.</span></span> <span data-ttu-id="f4740-151">超取樣將會增加包含此狀態之資料列的比例。</span><span class="sxs-lookup"><span data-stu-id="f4740-151">Oversampling will increase the proportion of data rows that include this state.</span></span><br /><br /> <span data-ttu-id="f4740-152">**取樣大小**</span><span class="sxs-lookup"><span data-stu-id="f4740-152">**Sample size**</span></span><br /><br /> <span data-ttu-id="f4740-153">選取要擷取的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="f4740-153">Select the total number of rows to extract.</span></span> <span data-ttu-id="f4740-154">這個值代表最終資料集的大小。</span><span class="sxs-lookup"><span data-stu-id="f4740-154">This value represents the size of the final data set.</span></span>|  
  
## <a name="other-sampling-options"></a><span data-ttu-id="f4740-155">其他取樣選項</span><span class="sxs-lookup"><span data-stu-id="f4740-155">Other Sampling Options</span></span>  
 <span data-ttu-id="f4740-156">如果此精靈中的取樣選項不符合您的需要，您可以使用 SQL Server Integration Services (SSIS) 中的取樣轉換來取樣多個資料來源的資料列。</span><span class="sxs-lookup"><span data-stu-id="f4740-156">If the sampling options in this wizard do not meet your needs, you can use the sampling transformation in SQL Server Integration Services (SSIS) to sample rows from multiple data sources.</span></span>  
  
 <span data-ttu-id="f4740-157">如需詳細資訊，請參閱資料[列取樣轉換](../integration-services/data-flow/transformations/row-sampling-transformation.md)和[百分比取樣轉換](../integration-services/data-flow/transformations/percentage-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="f4740-157">For more information, see [Row Sampling Transformation](../integration-services/data-flow/transformations/row-sampling-transformation.md) and [Percentage Sampling Transformation](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4740-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4740-158">See Also</span></span>  
 [<span data-ttu-id="f4740-159">資料採礦準備檢查清單</span><span class="sxs-lookup"><span data-stu-id="f4740-159">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
