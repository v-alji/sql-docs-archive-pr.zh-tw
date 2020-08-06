---
title: SSIS 教學課程：建立簡易 ETL 套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 780b008052a2ff64aa75b2036aa7202128f95ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703150"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a><span data-ttu-id="ab5e1-102">SSIS 教學課程：建立簡易 ETL 封裝</span><span class="sxs-lookup"><span data-stu-id="ab5e1-102">SSIS Tutorial: Creating a Simple ETL Package</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="ab5e1-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) 是用來建立高效能資料整合解決方案的平臺，包括資料倉儲的擷取、轉換和下載 (ETL) 封裝。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) is a platform for building high performance data integration solutions, including extraction, transformation, and load (ETL) packages for data warehousing.</span></span> <span data-ttu-id="ab5e1-104">SSIS 包含建立和偵錯封裝的圖形工具及精靈；執行工作流程功能 (例如 FTP 作業、執行 SQL 陳述式和傳送電子郵件訊息) 的工作；擷取和載入資料的資料來源和目的地；清除、彙總、合併和複製資料的轉換；管理封裝執行和儲存的管理服務 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ；以及設計 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件模型之程式的應用程式開發介面 (API)。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-104">SSIS includes graphical tools and wizards for building and debugging packages; tasks for performing workflow functions such as FTP operations, executing SQL statements, and sending e-mail messages; data sources and destinations for extracting and loading data; transformations for cleaning, aggregating, merging, and copying data; a management service, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for administering package execution and storage; and application programming interfaces (APIs) for programming the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="ab5e1-105">在本教學課程中，您將瞭解如何使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師來建立簡單的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-105">In this tutorial, you will learn how to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="ab5e1-106">您建立的封裝會從一般檔案取用資料，重新格式化資料，然後將重新格式化之後的資料插入到事實資料表中。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-106">The package that you create takes data from a flat file, reformats the data, and then inserts the reformatted data into a fact table.</span></span> <span data-ttu-id="ab5e1-107">在下列課程中，將會擴充封裝來示範迴圈、封裝組態、記錄和錯誤流程。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-107">In following lessons, the package is expanded to demonstrate looping, package configurations, logging and error flow.</span></span>  
  
 <span data-ttu-id="ab5e1-108">當您安裝教學課程使用的範例資料時，也會安裝您將在教學課程每一課所建立之封裝的完整版本。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-108">When you install the sample data that the tutorial uses, you also install the completed versions of the packages that you will create in each lesson of the tutorial.</span></span> <span data-ttu-id="ab5e1-109">利用完整封裝，您可以三級跳，從教學課程後面的課程開始。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-109">By using the completed packages, you can skip ahead and begin the tutorial at a later lesson if you like.</span></span> <span data-ttu-id="ab5e1-110">如果這是您第一次使用封裝或新的開發環境，我們建議您從第 1 課開始。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-110">If this is your first time working with packages or the new development environment, we recommend that you begin with Lesson1.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="ab5e1-111">學習內容</span><span class="sxs-lookup"><span data-stu-id="ab5e1-111">What You Will Learn</span></span>  
 <span data-ttu-id="ab5e1-112">若要熟悉中可用的新工具、控制項和功能，最好的方法 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 就是使用它們。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-112">The best way to become acquainted with the new tools, controls and features available in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to use them.</span></span> <span data-ttu-id="ab5e1-113">這個教學課程引導您使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師來建立簡單的 ETL 封裝，包括迴圈、組態、錯誤流程邏輯和記錄。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-113">This tutorial walks you through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple ETL package that includes looping, configurations, error flow logic and logging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5e1-114">需求</span><span class="sxs-lookup"><span data-stu-id="ab5e1-114">Requirements</span></span>  
 <span data-ttu-id="ab5e1-115">本教學課程的主要物件是熟悉基本資料庫作業，但對提供的新功能有所限制的使用者 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-115">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to the new features available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ab5e1-116">若要使用這個教學課程，系統上必須已安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="ab5e1-116">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ab5e1-117">資料庫的 **資料庫的** 。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-117">with the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="ab5e1-118">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-118">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="ab5e1-119">若要下載 **AdventureWorksDW2012** 資料庫，請參閱 [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026)。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-119">To download the **AdventureWorksDW2012** database, see [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ab5e1-120">當您附加資料庫 (\*.mdf 檔案) 時， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 預設會搜尋 .ldf 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-120">When you attach the database (\*.mdf file), [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] will by default search for an .ldf file.</span></span> <span data-ttu-id="ab5e1-121">您必須先手動移除 .ldf 檔案，然後再按一下 **[附加資料庫]** 對話方塊中的 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-121">You must manually remove the .ldf file before clicking OK in the **Attach Databases** dialog box.</span></span>  
    >   
    >  <span data-ttu-id="ab5e1-122">如需有關附加資料庫的詳細資訊，請參閱＜ [Attach a Database](../relational-databases/databases/attach-a-database.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-122">For more information about attaching databases, see [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
-   <span data-ttu-id="ab5e1-123">範例資料。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-123">Sample data.</span></span> <span data-ttu-id="ab5e1-124">範例資料隨附在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 課程封裝中。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-124">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="ab5e1-125">若要下載範例資料和課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-125">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="ab5e1-126">導覽至 [Integration Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=275027)</span><span class="sxs-lookup"><span data-stu-id="ab5e1-126">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="ab5e1-127">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-127">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="ab5e1-128">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-128">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="ab5e1-129">本教學課程中的課程</span><span class="sxs-lookup"><span data-stu-id="ab5e1-129">Lessons in This Tutorial</span></span>  
 [<span data-ttu-id="ab5e1-130">第 1 課：建立專案和基本封裝</span><span class="sxs-lookup"><span data-stu-id="ab5e1-130">Lesson 1: Creating the Project and Basic Package</span></span>](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 <span data-ttu-id="ab5e1-131">在這一課，您將建立一個從單個一般檔案擷取資料的簡易 ETL 封裝，使用查閱轉換元件來轉換資料，最後將結果載入至事實資料表目的地。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-131">In this lesson, you will create a simple ETL package that extracts data from a single flat file, transforms the data using lookup transformations and finally loads the result into a fact table destination.</span></span>  
  
 [<span data-ttu-id="ab5e1-132">第 2 課：新增迴圈</span><span class="sxs-lookup"><span data-stu-id="ab5e1-132">Lesson 2: Adding Looping</span></span>](lesson-2-adding-looping-with-ssis.md)  
 <span data-ttu-id="ab5e1-133">在這一課，您將擴充在第 1 課建立的封裝，利用新的迴圈功能，將多個一般檔案擷取到單一資料流程處理序中。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-133">In this lesson, you will expand the package you created in Lesson 1 to take advantage of new looping features to extract multiple flat files into a single data flow process.</span></span>  
  
 [<span data-ttu-id="ab5e1-134">第 3 課：新增記錄</span><span class="sxs-lookup"><span data-stu-id="ab5e1-134">Lesson 3: Adding Logging</span></span>](lesson-3-add-logging-with-ssis.md)  
 <span data-ttu-id="ab5e1-135">在這一課，您將擴充在第 2 課建立的封裝，來利用新的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-135">In this lesson, you will expand the package you created in Lesson 2 to take advantage of new logging features.</span></span>  
  
 [<span data-ttu-id="ab5e1-136">第 4 課：新增錯誤流程重新導向</span><span class="sxs-lookup"><span data-stu-id="ab5e1-136">Lesson 4: Adding Error Flow Redirection</span></span>](lesson-4-add-error-flow-redirection-with-ssis.md)  
 <span data-ttu-id="ab5e1-137">在這一課，您將擴充在第 3 課建立的封裝，來利用新的錯誤輸出組態。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-137">In this lesson, you will expand the package you created in lesson 3 to take advantage of new error output configurations.</span></span>  
  
 [<span data-ttu-id="ab5e1-138">第 5 課：新增封裝部署模型的封裝組態</span><span class="sxs-lookup"><span data-stu-id="ab5e1-138">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 <span data-ttu-id="ab5e1-139">在這一課，您將擴充在第 4 課建立的封裝，來利用新的封裝組態選項。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-139">In this lesson, you will expand the package you created in Lesson 4 to take advantage of new package configuration options.</span></span>  
  
 [<span data-ttu-id="ab5e1-140">第 6 課：搭配專案部署模型使用參數</span><span class="sxs-lookup"><span data-stu-id="ab5e1-140">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 <span data-ttu-id="ab5e1-141">在這一課，您將擴充在第 5 課建立的封裝，以充分搭配專案部署模型來使用新的參數。</span><span class="sxs-lookup"><span data-stu-id="ab5e1-141">In this lesson, you will expand the package you created in Lesson 5 to take advantage of using new parameters with the project deployment model.</span></span>  
  
  
