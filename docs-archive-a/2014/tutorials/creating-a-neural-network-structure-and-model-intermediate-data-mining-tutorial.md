---
title: 建立類神經網路結構和模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91c0210213083868eaab36cf34a05d0b7824a654
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585722"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="d7faa-102">建立類神經網路結構和模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="d7faa-102">Creating a Neural Network Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="d7faa-103">若要建立資料採礦模型，您必須先使用「資料採礦精靈」，根據新的資料來源檢視建立新的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="d7faa-103">To create a data mining model, you must first use the Data Mining Wizard to create a new mining structure based on the new data source view.</span></span> <span data-ttu-id="d7faa-104">在這項工作中，您將利用這個精靈來建立採礦結構，並同時根據 [!INCLUDE[msCoName](../includes/msconame-md.md)] 類神經網路演算法來建立關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d7faa-104">In this task you will use the wizard to create a mining structure, and at the same time create an associated mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="d7faa-105">類神經網路相當靈活，可以分析許多輸入和輸出的組合，因此，您應該試驗數種處理資料的方式，以取得最佳的結果。</span><span class="sxs-lookup"><span data-stu-id="d7faa-105">Because neural networks are extremely flexible and can analyze many combinations of inputs and outputs, you should experiment with several ways of processing the data to get the best results.</span></span> <span data-ttu-id="d7faa-106">例如，您可能會想要自訂*分類收納*或分組服務品質的數值目標，以符合特定商務需求的方式。</span><span class="sxs-lookup"><span data-stu-id="d7faa-106">For example, you might want to customize the way that the numerical target for service quality is *binned*, or grouped, to target specific business requirements.</span></span> <span data-ttu-id="d7faa-107">若要這樣做，您將會以不同的方式將新的資料行加入到可分組數值資料的採礦結構中，然後建立一個模型來使用這個新的資料行。</span><span class="sxs-lookup"><span data-stu-id="d7faa-107">To do this, you will add a new column to the mining structure that groups numerical data in a different way, and then create a model that uses the new column.</span></span> <span data-ttu-id="d7faa-108">您將會使用這些採礦模型來執行一些探索。</span><span class="sxs-lookup"><span data-stu-id="d7faa-108">You will use these mining models to do some exploration.</span></span>  
  
 <span data-ttu-id="d7faa-109">最後，當您得知類神經網路模型中哪些因素對於您的商務問題有最大的影響力時，您將會建立個別的模型來進行預測及計分。</span><span class="sxs-lookup"><span data-stu-id="d7faa-109">Finally, when you have learned from the neural network model which factors have the greatest impact for your business question, you will build a separate model for prediction and scoring.</span></span> <span data-ttu-id="d7faa-110">您將會使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 羅吉斯迴歸演算法，此演算法是根據類神經網路模型，但是已經最佳化，可根據特定輸入來尋找方案。</span><span class="sxs-lookup"><span data-stu-id="d7faa-110">You will use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm, which is based on the neural networks model but is optimized for finding a solution based on specific inputs.</span></span>  
  
 <span data-ttu-id="d7faa-111">**步驟**</span><span class="sxs-lookup"><span data-stu-id="d7faa-111">**Steps**</span></span>  
  
 [<span data-ttu-id="d7faa-112">建立預設採礦結構及模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-112">Create the default mining structure and model</span></span>](#bkmk_defaul)  
  
 [<span data-ttu-id="d7faa-113">使用離散化來儲藏可預測的資料行</span><span class="sxs-lookup"><span data-stu-id="d7faa-113">Use discretization to bin the predictable column</span></span>](#bkmk_ColumnCopy)  
  
 [<span data-ttu-id="d7faa-114">複製資料行並變更不同模型的分隔方法</span><span class="sxs-lookup"><span data-stu-id="d7faa-114">Copy the column and change the discretization method for a different model</span></span>](#bkmk_Alias)  
  
 [<span data-ttu-id="d7faa-115">針對可預測的資料行建立別名，以便比較模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-115">Create an alias for the predictable column so that you can compare models</span></span>](#bkmk_Alias2)  
  
 [<span data-ttu-id="d7faa-116">處理所有模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-116">Process all models</span></span>](#bkmk_SeedProcess)  
  
## <a name="create-the-default-call-center-structure"></a><span data-ttu-id="d7faa-117">建立預設的撥置中心結構<a name="bkmk_defaul"></a></span><span class="sxs-lookup"><span data-stu-id="d7faa-117">Create the Default Call Center Structure  <a name="bkmk_defaul"></a></span></span>  
  
1.  <span data-ttu-id="d7faa-118">在的方案總管中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 [**採礦結構**]，然後選取 [**新增採礦結構**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-118">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="d7faa-119">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-119">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="d7faa-120">在 [**選取定義方法**] 頁面上，確認已選取 [**從現有的關係資料庫或資料倉儲**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-120">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="d7faa-121">在 [**建立資料採礦結構**] 頁面上，確認已選取 [**使用採礦模型建立採礦結構**] 選項。</span><span class="sxs-lookup"><span data-stu-id="d7faa-121">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span>  
  
5.  <span data-ttu-id="d7faa-122">按一下 [**您要使用哪一項資料採礦技術？**] 選項的下拉式清單，然後選取 [ **Microsoft 類神經網路**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-122">Click the dropdown list for the option **Which data mining technique do you want to use?**, then select **Microsoft Neural Networks**.</span></span>  
  
     <span data-ttu-id="d7faa-123">羅吉斯迴歸模型是以類神經網路為基礎，因此，您可以重複使用相同的結構，並加入新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d7faa-123">Because the logistic regression models are based on the neural networks, you can reuse the same structure and add a new mining model.</span></span>  
  
6.  <span data-ttu-id="d7faa-124">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-124">Click **Next**.</span></span>  
  
     <span data-ttu-id="d7faa-125">[**選取資料來源視圖**] 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d7faa-125">The **Select Data Source View** page appears.</span></span>  
  
7.  <span data-ttu-id="d7faa-126">在 [**可用的資料來源視圖**] 底下，選取 `Call Center` ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-126">Under **Available data source views**, select `Call Center`, and click **Next**.</span></span>  
  
8.  <span data-ttu-id="d7faa-127">在 [**指定資料表類型**] 頁面上，選取 [ **FactCallCenter** ] 資料表旁的 [**案例**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d7faa-127">On the **Specify Table Types** page, select the **Case** check box next to the **FactCallCenter** table.</span></span> <span data-ttu-id="d7faa-128">請不要選取任何專案進行**DimDate**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-128">Do not select anything for **DimDate**.</span></span> <span data-ttu-id="d7faa-129">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="d7faa-130">在 [**指定定型資料**] 頁面上，選取資料行 FactCallCenterID 旁的 [索引**鍵**] **。**</span><span class="sxs-lookup"><span data-stu-id="d7faa-130">On the **Specify the Training Data** page, select **Key** next to the column **FactCallCenterID.**</span></span>  
  
10. <span data-ttu-id="d7faa-131">選取 [] `Predict` 和 [**輸入**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d7faa-131">Select the `Predict` and **Input** check boxes.</span></span>  
  
11. <span data-ttu-id="d7faa-132">選取 [索引**鍵**]、[**輸入**] 和核取方塊，如下 `Predict` 表所示：</span><span class="sxs-lookup"><span data-stu-id="d7faa-132">Select the **Key**, **Input**, and `Predict` check boxes as shown in the following table:</span></span>  
  
    |<span data-ttu-id="d7faa-133">資料表/資料行</span><span class="sxs-lookup"><span data-stu-id="d7faa-133">Tables/Columns</span></span>|<span data-ttu-id="d7faa-134">索引鍵/輸入/預測</span><span class="sxs-lookup"><span data-stu-id="d7faa-134">Key/Input/Predict</span></span>|  
    |---------------------|-------------------------|  
    |<span data-ttu-id="d7faa-135">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="d7faa-135">AutomaticResponses</span></span>|<span data-ttu-id="d7faa-136">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-136">Input</span></span>|  
    |<span data-ttu-id="d7faa-137">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="d7faa-137">AverageTimePerIssue</span></span>|<span data-ttu-id="d7faa-138">輸入/預測</span><span class="sxs-lookup"><span data-stu-id="d7faa-138">Input/Predict</span></span>|  
    |<span data-ttu-id="d7faa-139">呼叫</span><span class="sxs-lookup"><span data-stu-id="d7faa-139">Calls</span></span>|<span data-ttu-id="d7faa-140">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-140">Input</span></span>|  
    |<span data-ttu-id="d7faa-141">DateKey</span><span class="sxs-lookup"><span data-stu-id="d7faa-141">DateKey</span></span>|<span data-ttu-id="d7faa-142">請勿使用</span><span class="sxs-lookup"><span data-stu-id="d7faa-142">Do not use</span></span>|  
    |<span data-ttu-id="d7faa-143">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="d7faa-143">DayOfWeek</span></span>|<span data-ttu-id="d7faa-144">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-144">Input</span></span>|  
    |<span data-ttu-id="d7faa-145">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="d7faa-145">FactCallCenterID</span></span>|<span data-ttu-id="d7faa-146">Key</span><span class="sxs-lookup"><span data-stu-id="d7faa-146">Key</span></span>|  
    |<span data-ttu-id="d7faa-147">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="d7faa-147">IssuesRaised</span></span>|<span data-ttu-id="d7faa-148">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-148">Input</span></span>|  
    |<span data-ttu-id="d7faa-149">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-149">LevelOneOperators</span></span>|<span data-ttu-id="d7faa-150">輸入/預測</span><span class="sxs-lookup"><span data-stu-id="d7faa-150">Input/Predict</span></span>|  
    |<span data-ttu-id="d7faa-151">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-151">LevelTwoOperators</span></span>|<span data-ttu-id="d7faa-152">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-152">Input</span></span>|  
    |<span data-ttu-id="d7faa-153">訂單</span><span class="sxs-lookup"><span data-stu-id="d7faa-153">Orders</span></span>|<span data-ttu-id="d7faa-154">輸入/預測</span><span class="sxs-lookup"><span data-stu-id="d7faa-154">Input/Predict</span></span>|  
    |<span data-ttu-id="d7faa-155">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="d7faa-155">ServiceGrade</span></span>|<span data-ttu-id="d7faa-156">輸入/預測</span><span class="sxs-lookup"><span data-stu-id="d7faa-156">Input/Predict</span></span>|  
    |<span data-ttu-id="d7faa-157">Shift</span><span class="sxs-lookup"><span data-stu-id="d7faa-157">Shift</span></span>|<span data-ttu-id="d7faa-158">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-158">Input</span></span>|  
    |<span data-ttu-id="d7faa-159">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-159">TotalOperators</span></span>|<span data-ttu-id="d7faa-160">請勿使用</span><span class="sxs-lookup"><span data-stu-id="d7faa-160">Do not use</span></span>|  
    |<span data-ttu-id="d7faa-161">WageType</span><span class="sxs-lookup"><span data-stu-id="d7faa-161">WageType</span></span>|<span data-ttu-id="d7faa-162">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-162">Input</span></span>|  
  
     <span data-ttu-id="d7faa-163">請注意，多個可預測資料行已選取。</span><span class="sxs-lookup"><span data-stu-id="d7faa-163">Note that multiple predictable columns have been selected.</span></span> <span data-ttu-id="d7faa-164">類神經網路演算法的強項之一是，它可以分析所有可能的輸入和輸出屬性組合。</span><span class="sxs-lookup"><span data-stu-id="d7faa-164">One of the strengths of the neural network algorithm is that it can analyze all possible combinations of input and output attributes.</span></span> <span data-ttu-id="d7faa-165">您不想要針對大型資料集執行此動作，因為它可能會以指數方式增加處理時間。</span><span class="sxs-lookup"><span data-stu-id="d7faa-165">You wouldn't want to do this for a large data set, as it could exponentially increase processing time..</span></span>  
  
12. <span data-ttu-id="d7faa-166">在 [**指定欄位的內容和資料類型**] 頁面上，確認方格包含如下表所示的資料行、內容類型和資料類型，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-166">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="d7faa-167">資料行</span><span class="sxs-lookup"><span data-stu-id="d7faa-167">Columns</span></span>|<span data-ttu-id="d7faa-168">內容類型</span><span class="sxs-lookup"><span data-stu-id="d7faa-168">Content Type</span></span>|<span data-ttu-id="d7faa-169">資料類型</span><span class="sxs-lookup"><span data-stu-id="d7faa-169">Data Types</span></span>|  
    |-------------|------------------|----------------|  
    |<span data-ttu-id="d7faa-170">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="d7faa-170">AutomaticResponses</span></span>|<span data-ttu-id="d7faa-171">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-171">Continuous</span></span>|<span data-ttu-id="d7faa-172">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-172">Long</span></span>|  
    |<span data-ttu-id="d7faa-173">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="d7faa-173">AverageTimePerIssue</span></span>|<span data-ttu-id="d7faa-174">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-174">Continuous</span></span>|<span data-ttu-id="d7faa-175">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-175">Long</span></span>|  
    |<span data-ttu-id="d7faa-176">呼叫</span><span class="sxs-lookup"><span data-stu-id="d7faa-176">Calls</span></span>|<span data-ttu-id="d7faa-177">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-177">Continuous</span></span>|<span data-ttu-id="d7faa-178">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-178">Long</span></span>|  
    |<span data-ttu-id="d7faa-179">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="d7faa-179">DayOfWeek</span></span>|<span data-ttu-id="d7faa-180">Discrete</span><span class="sxs-lookup"><span data-stu-id="d7faa-180">Discrete</span></span>|<span data-ttu-id="d7faa-181">Text</span><span class="sxs-lookup"><span data-stu-id="d7faa-181">Text</span></span>|  
    |<span data-ttu-id="d7faa-182">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="d7faa-182">FactCallCenterID</span></span>|<span data-ttu-id="d7faa-183">Key</span><span class="sxs-lookup"><span data-stu-id="d7faa-183">Key</span></span>|<span data-ttu-id="d7faa-184">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-184">Long</span></span>|  
    |<span data-ttu-id="d7faa-185">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="d7faa-185">IssuesRaised</span></span>|<span data-ttu-id="d7faa-186">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-186">Continuous</span></span>|<span data-ttu-id="d7faa-187">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-187">Long</span></span>|  
    |<span data-ttu-id="d7faa-188">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-188">LevelOneOperators</span></span>|<span data-ttu-id="d7faa-189">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-189">Continuous</span></span>|<span data-ttu-id="d7faa-190">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-190">Long</span></span>|  
    |<span data-ttu-id="d7faa-191">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-191">LevelTwoOperators</span></span>|<span data-ttu-id="d7faa-192">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-192">Continuous</span></span>|<span data-ttu-id="d7faa-193">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-193">Long</span></span>|  
    |<span data-ttu-id="d7faa-194">訂單</span><span class="sxs-lookup"><span data-stu-id="d7faa-194">Orders</span></span>|<span data-ttu-id="d7faa-195">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-195">Continuous</span></span>|<span data-ttu-id="d7faa-196">long</span><span class="sxs-lookup"><span data-stu-id="d7faa-196">Long</span></span>|  
    |<span data-ttu-id="d7faa-197">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="d7faa-197">ServiceGrade</span></span>|<span data-ttu-id="d7faa-198">連續</span><span class="sxs-lookup"><span data-stu-id="d7faa-198">Continuous</span></span>|<span data-ttu-id="d7faa-199">Double</span><span class="sxs-lookup"><span data-stu-id="d7faa-199">Double</span></span>|  
    |<span data-ttu-id="d7faa-200">Shift</span><span class="sxs-lookup"><span data-stu-id="d7faa-200">Shift</span></span>|<span data-ttu-id="d7faa-201">Discrete</span><span class="sxs-lookup"><span data-stu-id="d7faa-201">Discrete</span></span>|<span data-ttu-id="d7faa-202">Text</span><span class="sxs-lookup"><span data-stu-id="d7faa-202">Text</span></span>|  
    |<span data-ttu-id="d7faa-203">WageType</span><span class="sxs-lookup"><span data-stu-id="d7faa-203">WageType</span></span>|<span data-ttu-id="d7faa-204">Discrete</span><span class="sxs-lookup"><span data-stu-id="d7faa-204">Discrete</span></span>|<span data-ttu-id="d7faa-205">Text</span><span class="sxs-lookup"><span data-stu-id="d7faa-205">Text</span></span>|  
  
13. <span data-ttu-id="d7faa-206">在 [**建立測試集**] 頁面上，清除 [**要測試的資料的百分比**] 選項的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="d7faa-206">On the **Create testing set** page, clear the text box for the option, **Percentage of data for testing**.</span></span> <span data-ttu-id="d7faa-207">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-207">Click **Next**.</span></span>  
  
14. <span data-ttu-id="d7faa-208">在 [**正在完成嚮導]** 頁面上，針對 [**採礦結構名稱**] 輸入 `Call Center` 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-208">On the **Completing the Wizard** page, for the **Mining structure name**, type `Call Center`.</span></span>  
  
15. <span data-ttu-id="d7faa-209">針對 [**採礦模型名稱**]，輸入 `Call Center Default NN` ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-209">For the **Mining model name**, type `Call Center Default NN`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="d7faa-210">[**允許**流覽] 方塊已停用，因為您無法使用類神經網路模型來流覽至資料。</span><span class="sxs-lookup"><span data-stu-id="d7faa-210">The **Allow drill through** box is disabled because you cannot drill through to data with neural network models.</span></span>  
  
16. <span data-ttu-id="d7faa-211">在方案總管中，以滑鼠右鍵按一下您剛才建立之資料採礦結構的名稱，然後選取 [**處理**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-211">In Solution Explorer, right-click the name of the data mining structure that you just created, and select **Process**.</span></span>  
  
## <a name="use-discretization-to-bin-the-target-column"></a><span data-ttu-id="d7faa-212">使用離散化來儲藏目標資料行</span><span class="sxs-lookup"><span data-stu-id="d7faa-212">Use Discretization to Bin the Target Column</span></span>  
 <span data-ttu-id="d7faa-213">根據預設，當您建立具有數值之可預測屬性的類神經網路模型時，Microsoft 類神經網路演算法會將該屬性視為一個連續數字。</span><span class="sxs-lookup"><span data-stu-id="d7faa-213">By default, when you create a neural network model that has a numeric predictable attribute, the Microsoft Neural Network algorithm treats the attribute as a continuous number.</span></span> <span data-ttu-id="d7faa-214">例如，ServiceGrade 屬性是一個理論上範圍從 0.00 (已接聽所有電話) 到 1.00 (已掛斷所有呼叫端) 的數字。</span><span class="sxs-lookup"><span data-stu-id="d7faa-214">For example, the ServiceGrade attribute is a number that theoretically ranges from 0.00 (all calls are answered) to 1.00 (all callers hang up).</span></span> <span data-ttu-id="d7faa-215">在此資料集中，值的分佈如下：</span><span class="sxs-lookup"><span data-stu-id="d7faa-215">In this data set, the values have the following distribution:</span></span>  
  
 <span data-ttu-id="d7faa-216">![服務等級值的分佈](../../2014/tutorials/media/skt-service-grade-valuesc.gif "服務等級值的分佈")</span><span class="sxs-lookup"><span data-stu-id="d7faa-216">![distribution of service grade values](../../2014/tutorials/media/skt-service-grade-valuesc.gif "distribution of service grade values")</span></span>  
  
 <span data-ttu-id="d7faa-217">因此，當您處理模型時，輸出結果的群組方式可能會和您預期的不同。</span><span class="sxs-lookup"><span data-stu-id="d7faa-217">As a result, when you process the model the outputs might be grouped differently than you expect.</span></span> <span data-ttu-id="d7faa-218">例如，如果您使用群集來識別最佳的值群組，此演算法會將 ServiceGrade 中的值分割為範圍，例如： 0.0748051948-0.09716216215 範圍。</span><span class="sxs-lookup"><span data-stu-id="d7faa-218">For example, if you use clustering to identify the best groups of values, the algorithm divides the values in ServiceGrade into ranges such as this one: 0.0748051948 - 0.09716216215.</span></span> <span data-ttu-id="d7faa-219">雖然這個群組在數學上是正確的，但是這些範圍對商務使用者而言，可能沒有很大的意義。</span><span class="sxs-lookup"><span data-stu-id="d7faa-219">Although this grouping is mathematically accurate, such ranges might not be as meaningful to business users.</span></span>  
  
 <span data-ttu-id="d7faa-220">在此步驟中，若要讓結果更直覺化，您會以不同的方式將數值分組，建立數值資料行的複本。</span><span class="sxs-lookup"><span data-stu-id="d7faa-220">In this step, to make the result more intuitive, you'll group the numerical values differently, creating copies of the numerical data column.</span></span>  
  
### <a name="how-discretization-works"></a><span data-ttu-id="d7faa-221">離散化的運作方式</span><span class="sxs-lookup"><span data-stu-id="d7faa-221">How Discretization Works</span></span>  
 <span data-ttu-id="d7faa-222">Analysis Services 會提供各種方法來分類收納或處理數值資料。</span><span class="sxs-lookup"><span data-stu-id="d7faa-222">Analysis Services provides a variety of methods for binning or processing numerical data.</span></span> <span data-ttu-id="d7faa-223">下表說明當輸出屬性 ServiceGrade 已處理三種不同的方式之後，所產生的結果之間的差異：</span><span class="sxs-lookup"><span data-stu-id="d7faa-223">The following table illustrates the differences between the results when the output attribute ServiceGrade has been processed three different ways:</span></span>  
  
-   <span data-ttu-id="d7faa-224">將其視為連續的數字。</span><span class="sxs-lookup"><span data-stu-id="d7faa-224">Treating it as a continuous number.</span></span>  
  
-   <span data-ttu-id="d7faa-225">讓演算法使用叢集來識別值的最佳排列。</span><span class="sxs-lookup"><span data-stu-id="d7faa-225">Having the algorithm use clustering to identify the best arrangement of values.</span></span>  
  
-   <span data-ttu-id="d7faa-226">指定數字要透過 Equal Areas 方法進行分類收納。</span><span class="sxs-lookup"><span data-stu-id="d7faa-226">Specifying that the numbers be binned by the Equal Areas method.</span></span>  
  
 <span data-ttu-id="d7faa-227">預設模型 (連續)</span><span class="sxs-lookup"><span data-stu-id="d7faa-227">Default model (continuous)</span></span>  
  
|<span data-ttu-id="d7faa-228">值</span><span class="sxs-lookup"><span data-stu-id="d7faa-228">VALUE</span></span>|<span data-ttu-id="d7faa-229">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="d7faa-229">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="d7faa-230">Missing</span><span class="sxs-lookup"><span data-stu-id="d7faa-230">Missing</span></span>|<span data-ttu-id="d7faa-231">0</span><span class="sxs-lookup"><span data-stu-id="d7faa-231">0</span></span>|  
|<span data-ttu-id="d7faa-232">0.09875</span><span class="sxs-lookup"><span data-stu-id="d7faa-232">0.09875</span></span>|<span data-ttu-id="d7faa-233">120</span><span class="sxs-lookup"><span data-stu-id="d7faa-233">120</span></span>|  
  
 <span data-ttu-id="d7faa-234">透過叢集進行分類收納</span><span class="sxs-lookup"><span data-stu-id="d7faa-234">Binned by clustering</span></span>  
  
|<span data-ttu-id="d7faa-235">值</span><span class="sxs-lookup"><span data-stu-id="d7faa-235">VALUE</span></span>|<span data-ttu-id="d7faa-236">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="d7faa-236">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="d7faa-237">\<0.0748051948</span><span class="sxs-lookup"><span data-stu-id="d7faa-237">\< 0.0748051948</span></span>|<span data-ttu-id="d7faa-238">34</span><span class="sxs-lookup"><span data-stu-id="d7faa-238">34</span></span>|  
|<span data-ttu-id="d7faa-239">0.0748051948-0.09716216215 範圍</span><span class="sxs-lookup"><span data-stu-id="d7faa-239">0.0748051948 - 0.09716216215</span></span>|<span data-ttu-id="d7faa-240">27</span><span class="sxs-lookup"><span data-stu-id="d7faa-240">27</span></span>|  
|<span data-ttu-id="d7faa-241">0.09716216215 範圍-0.13297297295</span><span class="sxs-lookup"><span data-stu-id="d7faa-241">0.09716216215 - 0.13297297295</span></span>|<span data-ttu-id="d7faa-242">39</span><span class="sxs-lookup"><span data-stu-id="d7faa-242">39</span></span>|  
|<span data-ttu-id="d7faa-243">0.13297297295 - 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="d7faa-243">0.13297297295 - 0.167499999975</span></span>|<span data-ttu-id="d7faa-244">10</span><span class="sxs-lookup"><span data-stu-id="d7faa-244">10</span></span>|  
|<span data-ttu-id="d7faa-245">>= 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="d7faa-245">>= 0.167499999975</span></span>|<span data-ttu-id="d7faa-246">10</span><span class="sxs-lookup"><span data-stu-id="d7faa-246">10</span></span>|  
  
 <span data-ttu-id="d7faa-247">透過同等區域進行分類收納</span><span class="sxs-lookup"><span data-stu-id="d7faa-247">Binned by equal areas</span></span>  
  
|<span data-ttu-id="d7faa-248">值</span><span class="sxs-lookup"><span data-stu-id="d7faa-248">VALUE</span></span>|<span data-ttu-id="d7faa-249">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="d7faa-249">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="d7faa-250">\<0.07</span><span class="sxs-lookup"><span data-stu-id="d7faa-250">\< 0.07</span></span>|<span data-ttu-id="d7faa-251">26</span><span class="sxs-lookup"><span data-stu-id="d7faa-251">26</span></span>|  
|<span data-ttu-id="d7faa-252">0.07-0.00</span><span class="sxs-lookup"><span data-stu-id="d7faa-252">0.07 - 0.00</span></span>|<span data-ttu-id="d7faa-253">22</span><span class="sxs-lookup"><span data-stu-id="d7faa-253">22</span></span>|  
|<span data-ttu-id="d7faa-254">0.09-0.11</span><span class="sxs-lookup"><span data-stu-id="d7faa-254">0.09 - 0.11</span></span>|<span data-ttu-id="d7faa-255">36</span><span class="sxs-lookup"><span data-stu-id="d7faa-255">36</span></span>|  
|<span data-ttu-id="d7faa-256">>= 0.12</span><span class="sxs-lookup"><span data-stu-id="d7faa-256">>= 0.12</span></span>|<span data-ttu-id="d7faa-257">36</span><span class="sxs-lookup"><span data-stu-id="d7faa-257">36</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d7faa-258">當所有資料都經過處理之後，您就可以從模型的臨界統計資料節點取得這些統計資料。</span><span class="sxs-lookup"><span data-stu-id="d7faa-258">You can obtain these statistics from the marginal statistics node of the model, after all the data has been processed.</span></span> <span data-ttu-id="d7faa-259">如需 [臨界統計資料] 節點的詳細資訊，請參閱類[神經網路模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d7faa-259">For more information about the marginal statistics node, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="d7faa-260">在此表中，VALUE 資料行顯示如何處理 ServiceGrade 的數字。</span><span class="sxs-lookup"><span data-stu-id="d7faa-260">In this table, the VALUE column shows you how the number for ServiceGrade has been handled.</span></span> <span data-ttu-id="d7faa-261">SUPPORT 資料行顯示多少案例有該值，或在該範圍中。</span><span class="sxs-lookup"><span data-stu-id="d7faa-261">The SUPPORT column shows you how many cases had that value, or that fell in that range.</span></span>  
  
-   <span data-ttu-id="d7faa-262">**使用連續的數字 (預設值)**</span><span class="sxs-lookup"><span data-stu-id="d7faa-262">**Use continuous numbers (default)**</span></span>  
  
     <span data-ttu-id="d7faa-263">如果您使用預設方法，演算法會計算 120 個相異值的結果，其平均值為 0.09875。</span><span class="sxs-lookup"><span data-stu-id="d7faa-263">If you used the default method, the algorithm would compute outcomes for 120 distinct values, the mean value of which is 0.09875.</span></span> <span data-ttu-id="d7faa-264">您也可以看到遺漏值的數目。</span><span class="sxs-lookup"><span data-stu-id="d7faa-264">You can also see the number of missing values.</span></span>  
  
-   <span data-ttu-id="d7faa-265">**透過叢集進行分類收納**</span><span class="sxs-lookup"><span data-stu-id="d7faa-265">**Bin by clustering**</span></span>  
  
     <span data-ttu-id="d7faa-266">當您讓 Microsoft 叢集演算法決定值的選擇性群組方式時，演算法會將 ServiceGrade 的值群組為五 (5) 個範圍。</span><span class="sxs-lookup"><span data-stu-id="d7faa-266">When you let the Microsoft Clustering algorithm determine the optional grouping of values, the algorithm would group the values for ServiceGrade into five (5) ranges.</span></span> <span data-ttu-id="d7faa-267">從 SUPPORT 資料行可得知，案例數目未平均分佈在各範圍中。</span><span class="sxs-lookup"><span data-stu-id="d7faa-267">The number of cases in each range is not evenly distributed, as you can see from the support column.</span></span>  
  
-   <span data-ttu-id="d7faa-268">**透過同等區域進行分類收納**</span><span class="sxs-lookup"><span data-stu-id="d7faa-268">**Bin by equal areas**</span></span>  
  
     <span data-ttu-id="d7faa-269">當您選擇此方法時，演算法會強制將值分為相同大小的貯體，這又會變更各範圍的上下限。</span><span class="sxs-lookup"><span data-stu-id="d7faa-269">When you choose this method, the algorithm forces the values into buckets of equal size, which in turn changes the upper and lower bounds of each range.</span></span> <span data-ttu-id="d7faa-270">您可以指定貯體的數目，但要避免貯體中有太少的值。</span><span class="sxs-lookup"><span data-stu-id="d7faa-270">You can specify the number of buckets, but you want to avoid having two few values in any bucket.</span></span>  
  
 <span data-ttu-id="d7faa-271">如需分類收納選項的詳細資訊，請參閱[&#40;資料採礦&#41;的離散化方法](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d7faa-271">For more information about binning options, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span>  
  
 <span data-ttu-id="d7faa-272">或者，您可以新增個別的衍生資料行，將服務等級分類成預先定義的目標範圍，例如**最佳** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05) ，以及不**佳**的 (ServiceGrade >= 0.10) 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-272">Alternatively, rather than using the numeric values, you could add a separate derived column that classifies the service grades into predefined target ranges, such as **Best** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05), and **Poor** (ServiceGrade >= 0.10).</span></span>  
  
###  <a name="create-a-copy-of-a-column-and-change-the-discretization-method"></a><a name="bkmk_newColumn"></a><span data-ttu-id="d7faa-273">建立資料行的複本並變更離散化方法</span><span class="sxs-lookup"><span data-stu-id="d7faa-273">Create a Copy of a Column and Change the Discretization Method</span></span>  
 <span data-ttu-id="d7faa-274">您將建立一個包含目標屬性的「挖掘」資料行複本，ServiceGrade 並變更數位的分組方式。</span><span class="sxs-lookup"><span data-stu-id="d7faa-274">You'll make a copy of the mining column that contains the target attribute, ServiceGrade and change the way the numbers are grouped.</span></span> <span data-ttu-id="d7faa-275">您可以在採礦結構中建立任何資料行的多個複本，包括可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7faa-275">You can create multiple copies of any column in a mining structure, including the predictable attribute.</span></span>  
  
 <span data-ttu-id="d7faa-276">在此教學課程中，您將會使用離散化的 Equal Areas 方法，並指定四個貯體。</span><span class="sxs-lookup"><span data-stu-id="d7faa-276">For this tutorial, you will use the Equal Areas method of discretization, and specify four buckets.</span></span> <span data-ttu-id="d7faa-277">這個方法所產生的群組與商務使用者感興趣的目標值非常接近。</span><span class="sxs-lookup"><span data-stu-id="d7faa-277">The groupings that result from this method are fairly close to the target values of interest to your business users.</span></span>  
  
####  <a name="to-create-a-customized-copy-of-a-column-in-the-mining-structure"></a><a name="bkmk_ColumnCopy"></a><span data-ttu-id="d7faa-278">若要在採礦結構中建立資料行的自訂複本</span><span class="sxs-lookup"><span data-stu-id="d7faa-278">To create a customized copy of a column in the mining structure</span></span>  
  
1.  <span data-ttu-id="d7faa-279">在 [方案總管] 中，按兩下您剛剛建立的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="d7faa-279">In Solution Explorer, double-click the mining structure that you just created.</span></span>  
  
2.  <span data-ttu-id="d7faa-280">在 [採礦結構] 索引標籤中，按一下 [**加入採礦結構資料行**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-280">In the Mining Structure tab, click **Add a mining structure column**.</span></span>  
  
3.  <span data-ttu-id="d7faa-281">在 [**選取資料行**] 對話方塊中，從 [來源資料**行**] 的清單中選取 [ServiceGrade]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-281">In the **Select column** dialog box, select ServiceGrade from the list in **Source column**, then click **OK**.</span></span>  
  
     <span data-ttu-id="d7faa-282">新的資料行就會加入到採礦結構資料行的清單中。</span><span class="sxs-lookup"><span data-stu-id="d7faa-282">A new column is added to the list of mining structure columns.</span></span> <span data-ttu-id="d7faa-283">根據預設，新的採礦資料行與現有資料行同名，但是後面多加了一個數值，例如 ServiceGrade 1。</span><span class="sxs-lookup"><span data-stu-id="d7faa-283">By default, the new mining column has the same name as the existing column, with a numerical postfix: for example, ServiceGrade 1.</span></span> <span data-ttu-id="d7faa-284">您可以變更此資料行的名稱，使名稱更具描述性。</span><span class="sxs-lookup"><span data-stu-id="d7faa-284">You can change the name of this column to be more descriptive.</span></span>  
  
     <span data-ttu-id="d7faa-285">您也將指定離散化方法。</span><span class="sxs-lookup"><span data-stu-id="d7faa-285">You will also specify the discretization method.</span></span>  
  
4.  <span data-ttu-id="d7faa-286">以滑鼠右鍵按一下 [ServiceGrade 1]，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-286">Right-click ServiceGrade 1 and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="d7faa-287">在 [**屬性**] 視窗中，找出 [**名稱**] 屬性，然後將 [名稱] 變更為 [**服務等級分類收納**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-287">In the **Properties** window, locate the **Name** property, and change the name to **Service Grade Binned** .</span></span>  
  
6.  <span data-ttu-id="d7faa-288">隨即出現一個對話方塊，詢問您是否要針對所有相關採礦模型資料行的名稱進行相同的變更。</span><span class="sxs-lookup"><span data-stu-id="d7faa-288">A dialog box appears asking whether you want to make the same change to the name of all related mining model columns.</span></span> <span data-ttu-id="d7faa-289">按一下 **[否]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-289">Click **No**.</span></span>  
  
7.  <span data-ttu-id="d7faa-290">在 [**屬性**] 視窗中，找出 [**資料類型**] 區段，並視需要加以展開。</span><span class="sxs-lookup"><span data-stu-id="d7faa-290">In the **Properties** window, locate the section **Data Type** and expand it if necessary.</span></span>  
  
8.  <span data-ttu-id="d7faa-291">將屬性 `Content` 的值從 `Continuous` 變更為 `Discretized`。</span><span class="sxs-lookup"><span data-stu-id="d7faa-291">Change the value of the property `Content` from `Continuous` to `Discretized`.</span></span>  
  
     <span data-ttu-id="d7faa-292">現在有下列屬性可以使用。</span><span class="sxs-lookup"><span data-stu-id="d7faa-292">The following properties are now available.</span></span> <span data-ttu-id="d7faa-293">變更屬性值，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="d7faa-293">Change the values of the properties as shown in the following table:</span></span>  
  
    |<span data-ttu-id="d7faa-294">屬性</span><span class="sxs-lookup"><span data-stu-id="d7faa-294">Property</span></span>|<span data-ttu-id="d7faa-295">預設值</span><span class="sxs-lookup"><span data-stu-id="d7faa-295">Default value</span></span>|<span data-ttu-id="d7faa-296">新值</span><span class="sxs-lookup"><span data-stu-id="d7faa-296">New value</span></span>|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|<span data-ttu-id="d7faa-297">沒有任何值</span><span class="sxs-lookup"><span data-stu-id="d7faa-297">No value</span></span>|<span data-ttu-id="d7faa-298">4</span><span class="sxs-lookup"><span data-stu-id="d7faa-298">4</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7faa-299"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 的預設值實際上是 0，這表示演算法會自動決定最佳的貯體數目。</span><span class="sxs-lookup"><span data-stu-id="d7faa-299">The default value of <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> is actually 0, which means that the algorithm automatically determines the optimum number of buckets.</span></span> <span data-ttu-id="d7faa-300">因此，如果您想要將此屬性的值重設為其預設值，請輸入 0。</span><span class="sxs-lookup"><span data-stu-id="d7faa-300">Therefore, if you want to reset the value of this property to its default, type 0.</span></span>  
  
9. <span data-ttu-id="d7faa-301">在資料採礦設計工具中，按一下 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d7faa-301">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
     <span data-ttu-id="d7faa-302">請注意，當您加入採礦結構資料行的複本時，此複本的使用旗標會自動設定為 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="d7faa-302">Notice that when you add a copy of a mining structure column, the usage flag for the copy is automatically set to `Ignore`.</span></span> <span data-ttu-id="d7faa-303">通常當您在採礦結構中加入資料行的複本時，您不會搭配原始資料行來使用此複本進行分析，否則演算法將會在兩個資料行之間尋找很強的關聯，這樣可能會遮蔽其他關聯性。</span><span class="sxs-lookup"><span data-stu-id="d7faa-303">Usually, when you add a copy of a column to a mining structure, you would not use the copy for analysis together with the original column, or the algorithm will find a strong correlation between the two columns that might obscure other relationships.</span></span>  
  
##  <a name="add-a-new-mining-model-to-the-mining-structure"></a><a name="bkmk_NewModel"></a><span data-ttu-id="d7faa-304">將新的採礦模型加入至採礦結構</span><span class="sxs-lookup"><span data-stu-id="d7faa-304">Add a New Mining Model to the Mining Structure</span></span>  
 <span data-ttu-id="d7faa-305">現在您已經針對目標屬性建立新的群組，所以需要加入一個新的採礦模型來使用離散化資料行。</span><span class="sxs-lookup"><span data-stu-id="d7faa-305">Now that you have created a new grouping for the target attribute, you need to add a new mining model that uses the discretized column.</span></span> <span data-ttu-id="d7faa-306">當您完成時，CallCenter 採礦結構將會有兩個採礦模型：</span><span class="sxs-lookup"><span data-stu-id="d7faa-306">When you are done, the CallCenter mining structure will have two mining models:</span></span>  
  
-   <span data-ttu-id="d7faa-307">「撥接中心預設 NN」採礦模型會將 ServiceGrade 值當做連續範圍來處理。</span><span class="sxs-lookup"><span data-stu-id="d7faa-307">The mining model, Call Center Default NN, handles the ServiceGrade values as a continuous range.</span></span>  
  
-   <span data-ttu-id="d7faa-308">您將建立新的採礦模型分類收納 NN，其會使用做為其目標結果的 ServiceGrade 資料行值，散發成大小相等的四個 bucket。</span><span class="sxs-lookup"><span data-stu-id="d7faa-308">You will create a new mining model, Call Center Binned NN, that uses as its target outcomes the values of the ServiceGrade column, distributed into four buckets of equal size.</span></span>  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a><span data-ttu-id="d7faa-309">若要根據新的離散化資料行來加入採礦模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-309">To add a mining model based on the new discretized column</span></span>  
  
1.  <span data-ttu-id="d7faa-310">在方案總管中，以滑鼠右鍵按一下您剛才建立的「採礦結構」，然後選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-310">In Solution Explorer, right-click the mining structure that you just created, and select **Open**.</span></span>  
  
2.  <span data-ttu-id="d7faa-311">按一下 **[採礦模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d7faa-311">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="d7faa-312">按一下 [**建立相關的採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-312">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="d7faa-313">在 [**新增採礦模型**] 對話方塊的 [**模型名稱**] 中，輸入 `Call Center Binned NN` 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-313">In the **New Mining Model** dialog box, for **Model name**, type `Call Center Binned NN`.</span></span> <span data-ttu-id="d7faa-314">在 [**演算法名稱**] 下拉式清單中，選取 [ **Microsoft 類神經網路**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-314">In the **Algorithm name** dropdown list, select **Microsoft Neural Network**.</span></span>  
  
5.  <span data-ttu-id="d7faa-315">在新的採礦模型所包含的資料行清單中，尋找 ServiceGrade，然後將使用方式從 `Predict` 變更為 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="d7faa-315">In the list of columns contained in the new mining model, locate ServiceGrade, and change the usage from `Predict` to `Ignore`.</span></span>  
  
6.  <span data-ttu-id="d7faa-316">同樣地，找出 ServiceGrade Binned，然後將使用方式從 `Ignore` 變更為 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="d7faa-316">Similarly, locate ServiceGrade Binned, and change the usage from `Ignore` to `Predict`.</span></span>  
  
##  <a name="create-an-alias-for-the-target-column"></a><a name="bkmk_Alias2"></a><span data-ttu-id="d7faa-317">建立目標資料行的別名</span><span class="sxs-lookup"><span data-stu-id="d7faa-317">Create an Alias for the Target Column</span></span>  
 <span data-ttu-id="d7faa-318">一般來說，您無法比較使用不同可預測屬性的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d7faa-318">Ordinarily you cannot compare mining models that use different predictable attributes.</span></span> <span data-ttu-id="d7faa-319">但是您可以為採礦模型資料行建立別名。</span><span class="sxs-lookup"><span data-stu-id="d7faa-319">However, you can create an alias for a mining model column.</span></span> <span data-ttu-id="d7faa-320">也就是說，您可以在採礦模型內重新命名資料行 ServiceGrade 分類收納，使其與原始資料行具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7faa-320">That is, you can rename the column, ServiceGrade Binned, within the mining model so that it has the same name as the original column.</span></span> <span data-ttu-id="d7faa-321">然後您可以在精確度圖表中直接比較這兩個模型，即使資料是以不同方式離散化也可以。</span><span class="sxs-lookup"><span data-stu-id="d7faa-321">You can then directly compare these two models in an accuracy chart, even though the data is discretized differently.</span></span>  
  
###  <a name="to-add-an-alias-for-a-mining-structure-column-in-a-mining-model"></a><a name="bkmk_Alias"></a><span data-ttu-id="d7faa-322">若要在「採礦模型」中加入「採礦結構」資料行的別名</span><span class="sxs-lookup"><span data-stu-id="d7faa-322">To add an alias for a mining structure column in a mining model</span></span>  
  
1.  <span data-ttu-id="d7faa-323">在 [**採礦模型**] 索引標籤的 [**結構**] 底下，選取 [ServiceGrade 分類收納]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-323">In the **Mining Models** tab, under **Structure**, select ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="d7faa-324">請注意，[**屬性**] 視窗會顯示 [ScalarMiningStructure] 資料行物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7faa-324">Note that the **Properties** window displays the properties of the object, ScalarMiningStructure column.</span></span>  
  
2.  <span data-ttu-id="d7faa-325">在採礦模型的 [ServiceGrade Binned NN] 資料行底下，按一下與 [ServiceGrade Binned] 資料行對應的資料格。</span><span class="sxs-lookup"><span data-stu-id="d7faa-325">Under the column for the mining model, ServiceGrade Binned NN, click the cell corresponding to the column ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="d7faa-326">請注意，現在 [**屬性**] 視窗會顯示物件的屬性 MiningModelColumn。</span><span class="sxs-lookup"><span data-stu-id="d7faa-326">Note that now the **Properties** window displays the properties for the object, MiningModelColumn.</span></span>  
  
3.  <span data-ttu-id="d7faa-327">找出 [**名稱**] 屬性，並將值變更為 `ServiceGrade` 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-327">Locate the **Name** property, and change the value to `ServiceGrade`.</span></span>  
  
4.  <span data-ttu-id="d7faa-328">找出 [**描述**] 屬性，然後輸入**暫存資料行別名**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-328">Locate the **Description** property and type **Temporary column alias**.</span></span>  
  
     <span data-ttu-id="d7faa-329">[**屬性**] 視窗應該包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d7faa-329">The **Properties** window should contain the following information:</span></span>  
  
    |<span data-ttu-id="d7faa-330">屬性</span><span class="sxs-lookup"><span data-stu-id="d7faa-330">Property</span></span>|<span data-ttu-id="d7faa-331">值</span><span class="sxs-lookup"><span data-stu-id="d7faa-331">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d7faa-332">**說明**</span><span class="sxs-lookup"><span data-stu-id="d7faa-332">**Description**</span></span>|<span data-ttu-id="d7faa-333">暫時資料行別名</span><span class="sxs-lookup"><span data-stu-id="d7faa-333">Temporary column alias</span></span>|  
    |<span data-ttu-id="d7faa-334">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="d7faa-334">**ID**</span></span>|<span data-ttu-id="d7faa-335">ServiceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="d7faa-335">ServiceGrade Binned</span></span>|  
    |<span data-ttu-id="d7faa-336">**模型旗標**</span><span class="sxs-lookup"><span data-stu-id="d7faa-336">**Modeling Flags**</span></span>||  
    |<span data-ttu-id="d7faa-337">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d7faa-337">**Name**</span></span>|<span data-ttu-id="d7faa-338">服務等級</span><span class="sxs-lookup"><span data-stu-id="d7faa-338">Service Grade</span></span>|  
    |<span data-ttu-id="d7faa-339">**SourceColumn 識別碼**</span><span class="sxs-lookup"><span data-stu-id="d7faa-339">**SourceColumn ID**</span></span>|<span data-ttu-id="d7faa-340">服務等級 1</span><span class="sxs-lookup"><span data-stu-id="d7faa-340">Service Grade 1</span></span>|  
    |<span data-ttu-id="d7faa-341">**使用量**</span><span class="sxs-lookup"><span data-stu-id="d7faa-341">**Usage**</span></span>|<span data-ttu-id="d7faa-342">Predict</span><span class="sxs-lookup"><span data-stu-id="d7faa-342">Predict</span></span>|  
  
5.  <span data-ttu-id="d7faa-343">按一下 [**採礦模型**] 索引標籤中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d7faa-343">Click anywhere in the **Mining Model** tab.</span></span>  
  
     <span data-ttu-id="d7faa-344">方格會更新，以顯示資料行使用方式旁邊的新暫存資料行別名 `ServiceGrade` 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-344">The grid is updated to show the new temporary column alias, `ServiceGrade`, beside the column usage.</span></span> <span data-ttu-id="d7faa-345">包含採礦結構及兩個採礦模型的方格應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="d7faa-345">The grid containing the mining structure and two mining models should look like the following:</span></span>  
  
    |<span data-ttu-id="d7faa-346">結構</span><span class="sxs-lookup"><span data-stu-id="d7faa-346">Structure</span></span>|<span data-ttu-id="d7faa-347">撥接中心預設 NN</span><span class="sxs-lookup"><span data-stu-id="d7faa-347">Call Center Default NN</span></span>|<span data-ttu-id="d7faa-348">分類收納的撥接中心 NN</span><span class="sxs-lookup"><span data-stu-id="d7faa-348">Call Center Binned NN</span></span>|  
    |---------------|----------------------------|---------------------------|  
    ||<span data-ttu-id="d7faa-349">Microsoft 類神經網路</span><span class="sxs-lookup"><span data-stu-id="d7faa-349">Microsoft Neural Network</span></span>|<span data-ttu-id="d7faa-350">Microsoft 類神經網路</span><span class="sxs-lookup"><span data-stu-id="d7faa-350">Microsoft Neural Network</span></span>|  
    |<span data-ttu-id="d7faa-351">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="d7faa-351">AutomaticResponses</span></span>|<span data-ttu-id="d7faa-352">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-352">Input</span></span>|<span data-ttu-id="d7faa-353">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-353">Input</span></span>|  
    |<span data-ttu-id="d7faa-354">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="d7faa-354">AverageTimePerIssue</span></span>|<span data-ttu-id="d7faa-355">Predict</span><span class="sxs-lookup"><span data-stu-id="d7faa-355">Predict</span></span>|<span data-ttu-id="d7faa-356">Predict</span><span class="sxs-lookup"><span data-stu-id="d7faa-356">Predict</span></span>|  
    |<span data-ttu-id="d7faa-357">呼叫</span><span class="sxs-lookup"><span data-stu-id="d7faa-357">Calls</span></span>|<span data-ttu-id="d7faa-358">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-358">Input</span></span>|<span data-ttu-id="d7faa-359">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-359">Input</span></span>|  
    |<span data-ttu-id="d7faa-360">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="d7faa-360">DayOfWeek</span></span>|<span data-ttu-id="d7faa-361">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-361">Input</span></span>|<span data-ttu-id="d7faa-362">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-362">Input</span></span>|  
    |<span data-ttu-id="d7faa-363">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="d7faa-363">FactCallCenterID</span></span>|<span data-ttu-id="d7faa-364">Key</span><span class="sxs-lookup"><span data-stu-id="d7faa-364">Key</span></span>|<span data-ttu-id="d7faa-365">Key</span><span class="sxs-lookup"><span data-stu-id="d7faa-365">Key</span></span>|  
    |<span data-ttu-id="d7faa-366">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="d7faa-366">IssuesRaised</span></span>|<span data-ttu-id="d7faa-367">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-367">Input</span></span>|<span data-ttu-id="d7faa-368">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-368">Input</span></span>|  
    |<span data-ttu-id="d7faa-369">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-369">LevelOneOperators</span></span>|<span data-ttu-id="d7faa-370">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-370">Input</span></span>|<span data-ttu-id="d7faa-371">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-371">Input</span></span>|  
    |<span data-ttu-id="d7faa-372">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="d7faa-372">LevelTwoOperators</span></span>|<span data-ttu-id="d7faa-373">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-373">Input</span></span>|<span data-ttu-id="d7faa-374">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-374">Input</span></span>|  
    |<span data-ttu-id="d7faa-375">訂單</span><span class="sxs-lookup"><span data-stu-id="d7faa-375">Orders</span></span>|<span data-ttu-id="d7faa-376">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-376">Input</span></span>|<span data-ttu-id="d7faa-377">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-377">Input</span></span>|  
    |<span data-ttu-id="d7faa-378">ServceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="d7faa-378">ServceGrade Binned</span></span>|<span data-ttu-id="d7faa-379">忽略</span><span class="sxs-lookup"><span data-stu-id="d7faa-379">Ignore</span></span>|<span data-ttu-id="d7faa-380">Predict (ServiceGrade)</span><span class="sxs-lookup"><span data-stu-id="d7faa-380">Predict (ServiceGrade)</span></span>|  
    |<span data-ttu-id="d7faa-381">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="d7faa-381">ServiceGrade</span></span>|<span data-ttu-id="d7faa-382">Predict</span><span class="sxs-lookup"><span data-stu-id="d7faa-382">Predict</span></span>|<span data-ttu-id="d7faa-383">忽略</span><span class="sxs-lookup"><span data-stu-id="d7faa-383">Ignore</span></span>|  
    |<span data-ttu-id="d7faa-384">Shift</span><span class="sxs-lookup"><span data-stu-id="d7faa-384">Shift</span></span>|<span data-ttu-id="d7faa-385">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-385">Input</span></span>|<span data-ttu-id="d7faa-386">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-386">Input</span></span>|  
    |<span data-ttu-id="d7faa-387">Total Operators</span><span class="sxs-lookup"><span data-stu-id="d7faa-387">Total Operators</span></span>|<span data-ttu-id="d7faa-388">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-388">Input</span></span>|<span data-ttu-id="d7faa-389">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-389">Input</span></span>|  
    |<span data-ttu-id="d7faa-390">WageType</span><span class="sxs-lookup"><span data-stu-id="d7faa-390">WageType</span></span>|<span data-ttu-id="d7faa-391">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-391">Input</span></span>|<span data-ttu-id="d7faa-392">輸入</span><span class="sxs-lookup"><span data-stu-id="d7faa-392">Input</span></span>|  
  
## <a name="process-all-models"></a><span data-ttu-id="d7faa-393">處理所有模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-393">Process All Models</span></span>  
 <span data-ttu-id="d7faa-394">最後，為了確認您建立的模型可以輕鬆比較，您將會針對預設模型和分類收納模型設定種子參數。</span><span class="sxs-lookup"><span data-stu-id="d7faa-394">Finally, to ensure that the models you have created can be easily compared, you will set the seed parameter for both the default and binned models.</span></span> <span data-ttu-id="d7faa-395">設定初始值可保證每一個模型都會從相同點開始處理資料。</span><span class="sxs-lookup"><span data-stu-id="d7faa-395">Setting a seed value guarantees that each model starts processing the data from the same point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7faa-396">如果您沒有為種子參數指定一個數值，SQL Server Analysis Services 將會根據模型的名稱產生一個種子。</span><span class="sxs-lookup"><span data-stu-id="d7faa-396">If you do not specify a numeric value for the seed parameter, SQL Server Analysis Services will generate a seed based on the name of the model.</span></span> <span data-ttu-id="d7faa-397">因為模型的名稱永遠不同，因此您必須設定一個初始值，以確保它們會以相同順序處理資料。</span><span class="sxs-lookup"><span data-stu-id="d7faa-397">Because the models always have different names, you must set a seed value to ensure that they process data in the same order.</span></span>  
  
###  <a name="to-specify-the-seed-and-process-the-models"></a><a name="bkmk_SeedProcess"></a><span data-ttu-id="d7faa-398">若要指定種子並處理模型</span><span class="sxs-lookup"><span data-stu-id="d7faa-398">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="d7faa-399">在 [**採礦模型**] 索引標籤中，以滑鼠右鍵按一下名為 [撥接中心-LR] 之模型的資料行，然後選取 [**設定演算法參數]**。</span><span class="sxs-lookup"><span data-stu-id="d7faa-399">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="d7faa-400">在 [HOLDOUT_SEED] 參數的資料列中，按一下 [**值**] 底下的空白資料格，然後輸入 `1` 。</span><span class="sxs-lookup"><span data-stu-id="d7faa-400">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="d7faa-401">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7faa-401">Click **OK**.</span></span> <span data-ttu-id="d7faa-402">針對與此結構有關的每一個模型重複這個步驟。</span><span class="sxs-lookup"><span data-stu-id="d7faa-402">Repeat this step for each model associated with the structure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7faa-403">只要您將相同的種子用於所有相關的模型，您選擇做為種子的值就不重要了。</span><span class="sxs-lookup"><span data-stu-id="d7faa-403">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="d7faa-404">在 [**採礦模型**] 功能表中，選取 [**處理採礦結構] 和 [所有模型**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-404">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="d7faa-405">按一下 **[是]** ，將更新的資料採礦專案部署到伺服器。</span><span class="sxs-lookup"><span data-stu-id="d7faa-405">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="d7faa-406">在 [**處理採礦模型**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-406">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="d7faa-407">按一下 [**關閉**] 以關閉 [**處理進度**] 對話方塊，然後在 [**處理採礦模型**] 對話方塊中再次按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="d7faa-407">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="d7faa-408">現在您已經建立兩個相關的採礦模型，您將會瀏覽資料來探索資料的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d7faa-408">Now that you have created the two related mining models, you will explore the data to discover relationships in the data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d7faa-409">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="d7faa-409">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d7faa-410">流覽撥打電話中心模型 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="d7faa-410">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7faa-411">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7faa-411">See Also</span></span>  
 [<span data-ttu-id="d7faa-412">採礦結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="d7faa-412">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
