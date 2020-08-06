---
title: 表格式模型化 (的艾德作品教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
ms.openlocfilehash: 840e8fe04309486d1583bc46161a4fc66ca7b1bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598530"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a><span data-ttu-id="dbcca-102">表格式模型化 (Adventure Works 教學課程)</span><span class="sxs-lookup"><span data-stu-id="dbcca-102">Tabular Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="dbcca-103">本教學課程提供如何使用 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 建立 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Analysis Services 表格式模型的課程。</span><span class="sxs-lookup"><span data-stu-id="dbcca-103">This tutorial provides lessons on how to create a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services tabular model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="dbcca-104">學習內容</span><span class="sxs-lookup"><span data-stu-id="dbcca-104">What You Will Learn</span></span>  
 <span data-ttu-id="dbcca-105">在這個教學課程進行期間，您將學習下列內容：</span><span class="sxs-lookup"><span data-stu-id="dbcca-105">During the course of this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="dbcca-106">如何在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="dbcca-106">How to create a new tabular model project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="dbcca-107">如何將資料從 SQL Server 關聯式資料庫匯入表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="dbcca-107">How to import data from a SQL Server relational database into a tabular model project.</span></span>  
  
-   <span data-ttu-id="dbcca-108">如何在模型中建立及管理資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="dbcca-108">How to create and manage relationships between tables in the model.</span></span>  
  
-   <span data-ttu-id="dbcca-109">如何建立及管理計算、量值和關鍵效能指標，幫助使用者分析模型資料。</span><span class="sxs-lookup"><span data-stu-id="dbcca-109">How to create and manage calculations, measures, and Key Performance Indicators that help users analyze model data.</span></span>  
  
-   <span data-ttu-id="dbcca-110">如何建立及管理檢視方塊和階層，透過提供業務和應用程式專屬視點的方式幫助使用者更輕鬆地瀏覽模型。</span><span class="sxs-lookup"><span data-stu-id="dbcca-110">How to create and manage perspectives and hierarchies that help users more easily browse model data by providing business and application specific viewpoints.</span></span>  
  
-   <span data-ttu-id="dbcca-111">如何建立分割區，將資料表資料分成較小的邏輯部分，以便讓其他分割區單獨處理。</span><span class="sxs-lookup"><span data-stu-id="dbcca-111">How to create partitions that divide table data into smaller logical parts that can be processed independent from other partitions.</span></span>  
  
-   <span data-ttu-id="dbcca-112">如何透過為使用者成員建立角色的方式保護模型物件和資料的安全。</span><span class="sxs-lookup"><span data-stu-id="dbcca-112">How to secure model objects and data by creating roles with user members.</span></span>  
  
-   <span data-ttu-id="dbcca-113">如何將表格式模型部署到以表格式模式執行之 Analysis Services 的沙箱或實際執行個體中。</span><span class="sxs-lookup"><span data-stu-id="dbcca-113">How to deploy a tabular model to a sandbox or production instance of Analysis Services running in Tabular mode.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="dbcca-114">教學課程案例</span><span class="sxs-lookup"><span data-stu-id="dbcca-114">Tutorial Scenario</span></span>  
 <span data-ttu-id="dbcca-115">這個教學課程是以一家虛構的公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]為基礎。</span><span class="sxs-lookup"><span data-stu-id="dbcca-115">This tutorial is based on [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], a fictitious company.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="dbcca-116">是一家大型跨國製造公司，專門生產及批發金屬和合成器材自行車給北美洲、歐洲和亞洲的商場。</span><span class="sxs-lookup"><span data-stu-id="dbcca-116">is a large, multinational manufacturing company that produces and distributes metal and composite bicycles to commercial markets in North America, Europe, and Asia.</span></span> <span data-ttu-id="dbcca-117">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的總公司在華盛頓 Bothell，該公司雇用 500 位員工。</span><span class="sxs-lookup"><span data-stu-id="dbcca-117">The headquarters for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is in Bothell, Washington, where the company employs 500 workers.</span></span> <span data-ttu-id="dbcca-118">另外， [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 它的市場還雇用了一些地區銷售團隊。</span><span class="sxs-lookup"><span data-stu-id="dbcca-118">Additionally, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] employs several regional sales teams throughout its market base.</span></span>  
  
 <span data-ttu-id="dbcca-119">為了針對銷售和行銷團隊及資深管理階層的資料分析需要提供更佳的支援，您的工作是要建立表格式模型，讓使用者分析 AdventureWorksDW 範例資料庫中的網際網路銷售資料。</span><span class="sxs-lookup"><span data-stu-id="dbcca-119">To better support the data analysis needs of sales and marketing teams and of senior management, you are tasked with creating a tabular model for users to analyze internet sales data in the AdventureWorksDW sample database.</span></span>  
  
 <span data-ttu-id="dbcca-120">為了完成本教學課程及 Adventure Works Internet Sales 表格式模型，您必須完成一系列課程。</span><span class="sxs-lookup"><span data-stu-id="dbcca-120">In order to complete the tutorial, and the Adventure Works Internet Sales tabular model, you must complete a number of lessons.</span></span> <span data-ttu-id="dbcca-121">每個課程有一些工作，必須依序完成每個工作，才能完成本課程。</span><span class="sxs-lookup"><span data-stu-id="dbcca-121">Within each lesson are a number of tasks; completing each task in order is necessary for completing the lesson.</span></span> <span data-ttu-id="dbcca-122">雖然在特定課程中可能有幾項工作會得到類似的結果，但是完成每項工作的方式會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="dbcca-122">While in a particular lesson there may be several tasks that accomplish a similar outcome; however, how you complete each task is slightly different.</span></span> <span data-ttu-id="dbcca-123">主要目的在於說明通常會有多種方式可完成特定工作，並且要求您使用在之前的工作中學到的技巧。</span><span class="sxs-lookup"><span data-stu-id="dbcca-123">This is to show that there is often more than one way to complete a particular task, and to challenge you by using skills you learned in previous tasks.</span></span>  
  
 <span data-ttu-id="dbcca-124">這些課程的目的是引導您藉由使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中的許多功能，來撰寫執行記憶體中模式的基本表格式模型。</span><span class="sxs-lookup"><span data-stu-id="dbcca-124">The purpose of the lessons is to guide you through authoring a basic tabular model running in In-Memory mode by using many of the features included in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="dbcca-125">因為每一課都是以上一課為基礎，所以您應該依序完成課程。</span><span class="sxs-lookup"><span data-stu-id="dbcca-125">Because each lesson builds upon the previous lesson, you should complete the lessons in order.</span></span> <span data-ttu-id="dbcca-126">完成所有課程之後，您就已撰寫並且將 Adventure Works Internet Sales 範例表格式模型部署到 Analysis Services 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="dbcca-126">Once you have completed all of the lessons, you will have authored and deployed the Adventure Works Internet Sales sample tabular model on an Analysis Services server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbcca-127">本教學課程並未提供下列相關課程或資訊：使用 SQL Server Management Studio 管理部署的表格式模型資料庫，或使用報表用戶端應用程式連接到部署的模型以瀏覽模型資料。</span><span class="sxs-lookup"><span data-stu-id="dbcca-127">This tutorial does not provide lessons or information about managing a deployed tabular model database by using SQL Server Management Studio, or using a reporting client application to connect to a deployed model to browse model data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dbcca-128">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="dbcca-128">Prerequisites</span></span>  
 <span data-ttu-id="dbcca-129">您必須安裝下列必要條件，才能完成本教學課程：</span><span class="sxs-lookup"><span data-stu-id="dbcca-129">In order to complete this tutorial, you must have the following prerequisites installed:</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="dbcca-130">Analysis Services 執行個體 (以表格式模式執行)。</span><span class="sxs-lookup"><span data-stu-id="dbcca-130">Analysis Services instance running in Tabular mode.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="dbcca-131">.</span><span class="sxs-lookup"><span data-stu-id="dbcca-131">.</span></span>  
  
-   <span data-ttu-id="dbcca-132">AdventureWorksDW 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="dbcca-132">AdventureWorksDW sample database.</span></span> <span data-ttu-id="dbcca-133">這個範例資料庫包括完成本教學課程所需的資料。</span><span class="sxs-lookup"><span data-stu-id="dbcca-133">This sample database includes the data necessary to complete this tutorial.</span></span> <span data-ttu-id="dbcca-134">若要下載範例資料庫，請參閱 [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="dbcca-134">To download the sample database, see [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="dbcca-135">Excel 2003 或更新版本 (與第 11 課中的 [在 Excel 中進行分析] 功能搭配使用)</span><span class="sxs-lookup"><span data-stu-id="dbcca-135">Excel 2003 or later (for use with the Analyze in Excel feature in lesson 11)</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="dbcca-136">課程</span><span class="sxs-lookup"><span data-stu-id="dbcca-136">Lessons</span></span>  
 <span data-ttu-id="dbcca-137">這個教學課程包括下列課程：</span><span class="sxs-lookup"><span data-stu-id="dbcca-137">This tutorial includes the following lessons:</span></span>  
  
|<span data-ttu-id="dbcca-138">課程</span><span class="sxs-lookup"><span data-stu-id="dbcca-138">Lesson</span></span>|<span data-ttu-id="dbcca-139">預估完成時間</span><span class="sxs-lookup"><span data-stu-id="dbcca-139">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="dbcca-140">第 1 課：建立新的表格式模型專案</span><span class="sxs-lookup"><span data-stu-id="dbcca-140">Lesson 1: Create a New Tabular Model Project</span></span>](lesson-1-create-a-new-tabular-model-project.md)|<span data-ttu-id="dbcca-141">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-141">10 minutes</span></span>|  
|[<span data-ttu-id="dbcca-142">第 2 課：加入資料</span><span class="sxs-lookup"><span data-stu-id="dbcca-142">Lesson 2: Add Data</span></span>](lesson-2-add-data.md)|<span data-ttu-id="dbcca-143">20 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-143">20 minutes</span></span>|  
|[<span data-ttu-id="dbcca-144">第 3 課：重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="dbcca-144">Lesson 3: Rename Columns</span></span>](rename-columns.md)|<span data-ttu-id="dbcca-145">20 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-145">20 minutes</span></span>|  
|[<span data-ttu-id="dbcca-146">第 4 課：標記為日期資料表</span><span class="sxs-lookup"><span data-stu-id="dbcca-146">Lesson 4: Mark as Date Table</span></span>](lesson-3-mark-as-date-table.md)|<span data-ttu-id="dbcca-147">3 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-147">3 minutes</span></span>|  
|[<span data-ttu-id="dbcca-148">第 5 課：建立關聯性</span><span class="sxs-lookup"><span data-stu-id="dbcca-148">Lesson 5: Create Relationships</span></span>](lesson-4-create-relationships.md)|<span data-ttu-id="dbcca-149">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-149">10 minutes</span></span>|  
|[<span data-ttu-id="dbcca-150">第 6 課：建立計算結果欄</span><span class="sxs-lookup"><span data-stu-id="dbcca-150">Lesson 6: Create Calculated Columns</span></span>](lesson-5-create-calculated-columns.md)|<span data-ttu-id="dbcca-151">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-151">15 minutes</span></span>|  
|[<span data-ttu-id="dbcca-152">第 7 課：建立量值</span><span class="sxs-lookup"><span data-stu-id="dbcca-152">Lesson 7: Create Measures</span></span>](lesson-6-create-measures.md)|<span data-ttu-id="dbcca-153">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-153">30 minutes</span></span>|  
|[<span data-ttu-id="dbcca-154">第 8 課：建立關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="dbcca-154">Lesson 8: Create Key Performance Indicators</span></span>](lesson-7-create-key-performance-indicators.md)|<span data-ttu-id="dbcca-155">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-155">15 minutes</span></span>|  
|[<span data-ttu-id="dbcca-156">第 9 課：建立檢視方塊</span><span class="sxs-lookup"><span data-stu-id="dbcca-156">Lesson 9: Create Perspectives</span></span>](lesson-8-create-perspectives.md)|<span data-ttu-id="dbcca-157">5 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-157">5 minutes</span></span>|  
|[<span data-ttu-id="dbcca-158">第 10 課：建立階層</span><span class="sxs-lookup"><span data-stu-id="dbcca-158">Lesson 10: Create Hierarchies</span></span>](lesson-9-create-hierarchies.md)|<span data-ttu-id="dbcca-159">20 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-159">20 minutes</span></span>|  
|[<span data-ttu-id="dbcca-160">第 11 課：建立資料分割</span><span class="sxs-lookup"><span data-stu-id="dbcca-160">Lesson 11: Create Partitions</span></span>](lesson-10-create-partitions.md)|<span data-ttu-id="dbcca-161">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-161">15 minutes</span></span>|  
|[<span data-ttu-id="dbcca-162">第 12 課：建立角色</span><span class="sxs-lookup"><span data-stu-id="dbcca-162">Lesson 12: Create Roles</span></span>](lesson-11-create-roles.md)|<span data-ttu-id="dbcca-163">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-163">15 minutes</span></span>|  
|[<span data-ttu-id="dbcca-164">第 13 課：在 Excel 中進行分析</span><span class="sxs-lookup"><span data-stu-id="dbcca-164">Lesson 13: Analyze in Excel</span></span>](lesson-12-analyze-in-excel.md)|<span data-ttu-id="dbcca-165">20 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-165">20 minutes</span></span>|  
|[<span data-ttu-id="dbcca-166">第 14 課：部署</span><span class="sxs-lookup"><span data-stu-id="dbcca-166">Lesson 14: Deploy</span></span>](lesson-13-deploy.md)|<span data-ttu-id="dbcca-167">5 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-167">5 minutes</span></span>|  
  
## <a name="supplemental-lessons"></a><span data-ttu-id="dbcca-168">補充課程</span><span class="sxs-lookup"><span data-stu-id="dbcca-168">Supplemental Lessons</span></span>  
 <span data-ttu-id="dbcca-169">本教學課程也包含 [補充課程](../tutorials/supplemental-lessons.md)。</span><span class="sxs-lookup"><span data-stu-id="dbcca-169">This tutorial also includes [Supplemental Lessons](../tutorials/supplemental-lessons.md).</span></span> <span data-ttu-id="dbcca-170">本節中的主題並非完成教學課程所必須，但是能幫助您更了解進階表格式模型撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="dbcca-170">Topics in this section are not required to complete the tutorial, but can be helpful in better understanding advanced tabular model authoring features.</span></span>  
  
 <span data-ttu-id="dbcca-171">這個教學課程包括下列補充課程：</span><span class="sxs-lookup"><span data-stu-id="dbcca-171">This tutorial includes the following supplemental lessons:</span></span>  
  
|<span data-ttu-id="dbcca-172">課程</span><span class="sxs-lookup"><span data-stu-id="dbcca-172">Lesson</span></span>|<span data-ttu-id="dbcca-173">預估完成時間</span><span class="sxs-lookup"><span data-stu-id="dbcca-173">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="dbcca-174">使用資料列篩選器實作動態安全性</span><span class="sxs-lookup"><span data-stu-id="dbcca-174">Implement Dynamic Security by Using Row Filters</span></span>](../tutorials/implement-dynamic-security-by-using-row-filters.md)|<span data-ttu-id="dbcca-175">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-175">30 minutes</span></span>|  
|<span data-ttu-id="dbcca-176">[設定 Power View 報表的報表屬性](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)設定 Power View 報表的報表屬性</span><span class="sxs-lookup"><span data-stu-id="dbcca-176">[Configure Reporting Properties for Power View Reports](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Configure Reporting Properties for Power View Reports</span></span>|<span data-ttu-id="dbcca-177">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="dbcca-177">30 minutes</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="dbcca-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dbcca-178">Next Step</span></span>  
 <span data-ttu-id="dbcca-179">若要開始本教學課程，請繼續進行第一課： [第 1 課：建立新的表格式模型專案](lesson-1-create-a-new-tabular-model-project.md)。</span><span class="sxs-lookup"><span data-stu-id="dbcca-179">To begin the tutorial, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
  
