---
title: 第1課：建立專案和基本套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a9ddc36ef242cc4e4b146e90dfa9de470e68d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596123"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a><span data-ttu-id="8ccc0-102">第 1 課：建立專案和基本封裝</span><span class="sxs-lookup"><span data-stu-id="8ccc0-102">Lesson 1: Creating the Project and Basic Package</span></span>
  <span data-ttu-id="8ccc0-103">在這一課，您將建立一個從單個一般檔案來源擷取資料的簡易 ETL 封裝，使用兩個查閱轉換元件來轉換資料、將該資料寫入至 **AdventureWorksDW2012** 中的 **FactCurrency**事實資料表。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-103">In this lesson, you will create a simple ETL package that extracts data from a single flat file source, transforms the data using two lookup transformation components, and writes that data to the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span> <span data-ttu-id="8ccc0-104">在這一課，您會學到如何建立新封裝，加入和設定資料來源和目的地連接，以及使用新控制流程和資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-104">As part of this lesson, you will learn how to create new packages, add and configure data source and destination connections, and work with new control flow and data flow components.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ccc0-105">這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-105">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="8ccc0-106">如需安裝和部署**AdventureWorksDW2012**的詳細資訊，請參閱[Microsoft SQL Server 產品範例： Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples)。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-106">For more information on installing and deploying **AdventureWorksDW2012**, see [Microsoft SQL Server Product Samples: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).</span></span>  
  
## <a name="understanding-the-package-requirements"></a><span data-ttu-id="8ccc0-107">了解封裝需求</span><span class="sxs-lookup"><span data-stu-id="8ccc0-107">Understanding the Package Requirements</span></span>  
 <span data-ttu-id="8ccc0-108">這個教學課程需要 Microsoft SQL Server Data Tools。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
  
 <span data-ttu-id="8ccc0-109">如需安裝 SQL Server Data Tools 的詳細資訊，請參閱 [SQL Server Data Tools 下載](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017)。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).</span></span>  
  
 <span data-ttu-id="8ccc0-110">在建立封裝之前，您需要了解來源資料和目的地使用的格式。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-110">Before creating a package, you need a good understanding of the formatting used in both the source data and the destination.</span></span> <span data-ttu-id="8ccc0-111">了解這些資料格式之後，您就可以定義必要的轉換，將來源資料對應至目的地。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-111">Once you understand both of these data formats, you will be ready to define the transformations necessary to map the source data to the destination.</span></span>  
  
### <a name="looking-at-the-source"></a><span data-ttu-id="8ccc0-112">查看來源</span><span class="sxs-lookup"><span data-stu-id="8ccc0-112">Looking at the Source</span></span>  
 <span data-ttu-id="8ccc0-113">在這個教學課程中，來源資料是一般檔案 SampleCurrencyData.txt 中所含的貨幣記錄資料集。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-113">For this tutorial, the source data is a set of historical currency data contained in the flat file, SampleCurrencyData.txt.</span></span> <span data-ttu-id="8ccc0-114">來源資料具有下列四個資料行：貨幣的平均匯率、貨幣索引鍵、日期索引鍵和收盤匯率。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-114">The source data has the following four columns: the average rate of the currency, a currency key, a date key, and the end-of-day rate.</span></span>  
  
 <span data-ttu-id="8ccc0-115">以下是包含在 SampleCurrencyData.txt 檔案中的來源資料範例：</span><span class="sxs-lookup"><span data-stu-id="8ccc0-115">Here is an example of the source data contained in the SampleCurrencyData.txt file:</span></span>  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 <span data-ttu-id="8ccc0-116">使用一般檔案來源資料時，一定要了解一般檔案連接管理員如何解譯一般檔案資料。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-116">When working with flat file source data, it is important to understand how the Flat File connection manager interprets the flat file data.</span></span> <span data-ttu-id="8ccc0-117">如果一般檔案來源是 Unicode，一般檔案連接管理員會將所有資料行定義為 [DT_WSTR]，預設資料行寬度為 50。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-117">If the flat file source is Unicode, the Flat File connection manager defines all columns as [DT_WSTR] with a default column width of 50.</span></span> <span data-ttu-id="8ccc0-118">如果一般檔案來源是以 ANSI 編碼，資料行會定義為 [DT_STR]，且資料行寬度為 50。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-118">If the flat file source is ANSI-encoded, the columns are defined as [DT_STR] with a column width of 50.</span></span> <span data-ttu-id="8ccc0-119">您或許必須變更這些預設值，好讓字串資料行類型更適合您的資料。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-119">You will probably have to change these defaults to make the string column types more appropriate for your data.</span></span> <span data-ttu-id="8ccc0-120">若要這麼做，您必須查看要在其中寫入資料的目的地之資料類型，然後在一般檔案連接管理員內選擇正確類型。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-120">To do this, you will need to look at the data type of the destination where the data will be written to and then choose the correct type within the Flat File connection manager.</span></span>  
  
### <a name="looking-at-the-destination"></a><span data-ttu-id="8ccc0-121">查看目的地</span><span class="sxs-lookup"><span data-stu-id="8ccc0-121">Looking at the Destination</span></span>  
 <span data-ttu-id="8ccc0-122">來源資料的最終目的地是 **AdventureWorksDW** 中的 **FactCurrency**事實資料表。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-122">The ultimate destination for the source data is the **FactCurrency** fact table in **AdventureWorksDW**.</span></span> <span data-ttu-id="8ccc0-123">**FactCurrency** 事實資料表有 4 個資料行，而且與兩個維度資料表之間有關聯性，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-123">The **FactCurrency** fact table has four columns, and has relationships to two dimension tables, as shown in the following table.</span></span>  
  
|<span data-ttu-id="8ccc0-124">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="8ccc0-124">Column Name</span></span>|<span data-ttu-id="8ccc0-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="8ccc0-125">Data Type</span></span>|<span data-ttu-id="8ccc0-126">查閱資料表</span><span class="sxs-lookup"><span data-stu-id="8ccc0-126">Lookup Table</span></span>|<span data-ttu-id="8ccc0-127">「查閱資料行」</span><span class="sxs-lookup"><span data-stu-id="8ccc0-127">Lookup Column</span></span>|  
|-----------------|---------------|------------------|-------------------|  
|<span data-ttu-id="8ccc0-128">AverageRate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-128">AverageRate</span></span>|<span data-ttu-id="8ccc0-129">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8ccc0-129">float</span></span>|<span data-ttu-id="8ccc0-130">無</span><span class="sxs-lookup"><span data-stu-id="8ccc0-130">None</span></span>|<span data-ttu-id="8ccc0-131">無</span><span class="sxs-lookup"><span data-stu-id="8ccc0-131">None</span></span>|  
|<span data-ttu-id="8ccc0-132">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="8ccc0-132">CurrencyKey</span></span>|<span data-ttu-id="8ccc0-133">int (FK)</span><span class="sxs-lookup"><span data-stu-id="8ccc0-133">int (FK)</span></span>|<span data-ttu-id="8ccc0-134">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="8ccc0-134">DimCurrency</span></span>|<span data-ttu-id="8ccc0-135">CurrencyKey (PK)</span><span class="sxs-lookup"><span data-stu-id="8ccc0-135">CurrencyKey (PK)</span></span>|  
|<span data-ttu-id="8ccc0-136">DateKey</span><span class="sxs-lookup"><span data-stu-id="8ccc0-136">DateKey</span></span>|<span data-ttu-id="8ccc0-137">int (FK)</span><span class="sxs-lookup"><span data-stu-id="8ccc0-137">Int (FK)</span></span>|<span data-ttu-id="8ccc0-138">DimDate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-138">DimDate</span></span>|<span data-ttu-id="8ccc0-139">DateKey (PK)</span><span class="sxs-lookup"><span data-stu-id="8ccc0-139">DateKey (PK)</span></span>|  
|<span data-ttu-id="8ccc0-140">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-140">EndOfDayRate</span></span>|<span data-ttu-id="8ccc0-141">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8ccc0-141">float</span></span>|<span data-ttu-id="8ccc0-142">無</span><span class="sxs-lookup"><span data-stu-id="8ccc0-142">None</span></span>|<span data-ttu-id="8ccc0-143">無</span><span class="sxs-lookup"><span data-stu-id="8ccc0-143">None</span></span>|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a><span data-ttu-id="8ccc0-144">對應來源資料以便與目的地相容</span><span class="sxs-lookup"><span data-stu-id="8ccc0-144">Mapping Source Data to be Compatible with the Destination</span></span>  
 <span data-ttu-id="8ccc0-145">來源和目的地資料格式的分析指出 **CurrencyKey** 和 **DateKey** 值可能需要查閱。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-145">Analysis of the source and destination data formats indicates that lookups will be necessary for the **CurrencyKey** and **DateKey** values.</span></span> <span data-ttu-id="8ccc0-146">要執行這些查閱的轉換將使用 **DimCurrency** 和 **DimDate** 維度資料表的替代索引鍵來取得 **CurrencyKey** 和 **DateKey** 值。</span><span class="sxs-lookup"><span data-stu-id="8ccc0-146">The transformations that will perform these lookups will obtain the **CurrencyKey** and **DateKey** values by using the alternate keys from **DimCurrency** and **DimDate** dimension tables.</span></span>  
  
|<span data-ttu-id="8ccc0-147">一般檔案資料行</span><span class="sxs-lookup"><span data-stu-id="8ccc0-147">Flat File Column</span></span>|<span data-ttu-id="8ccc0-148">資料表名稱</span><span class="sxs-lookup"><span data-stu-id="8ccc0-148">Table Name</span></span>|<span data-ttu-id="8ccc0-149">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="8ccc0-149">Column Name</span></span>|<span data-ttu-id="8ccc0-150">資料類型</span><span class="sxs-lookup"><span data-stu-id="8ccc0-150">Data Type</span></span>|  
|----------------------|----------------|-----------------|---------------|  
|<span data-ttu-id="8ccc0-151">0</span><span class="sxs-lookup"><span data-stu-id="8ccc0-151">0</span></span>|<span data-ttu-id="8ccc0-152">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="8ccc0-152">FactCurrency</span></span>|<span data-ttu-id="8ccc0-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-153">AverageRate</span></span>|<span data-ttu-id="8ccc0-154">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8ccc0-154">float</span></span>|  
|<span data-ttu-id="8ccc0-155">1</span><span class="sxs-lookup"><span data-stu-id="8ccc0-155">1</span></span>|<span data-ttu-id="8ccc0-156">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="8ccc0-156">DimCurrency</span></span>|<span data-ttu-id="8ccc0-157">CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="8ccc0-157">CurrencyAlternateKey</span></span>|<span data-ttu-id="8ccc0-158">nchar(3)</span><span class="sxs-lookup"><span data-stu-id="8ccc0-158">nchar (3)</span></span>|  
|<span data-ttu-id="8ccc0-159">2</span><span class="sxs-lookup"><span data-stu-id="8ccc0-159">2</span></span>|<span data-ttu-id="8ccc0-160">DimDate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-160">DimDate</span></span>|<span data-ttu-id="8ccc0-161">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="8ccc0-161">FullDateAlternateKey</span></span>|<span data-ttu-id="8ccc0-162">date</span><span class="sxs-lookup"><span data-stu-id="8ccc0-162">date</span></span>|  
|<span data-ttu-id="8ccc0-163">3</span><span class="sxs-lookup"><span data-stu-id="8ccc0-163">3</span></span>|<span data-ttu-id="8ccc0-164">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="8ccc0-164">FactCurrency</span></span>|<span data-ttu-id="8ccc0-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="8ccc0-165">EndOfDayRate</span></span>|<span data-ttu-id="8ccc0-166">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8ccc0-166">float</span></span>|  
  
## <a name="lesson-tasks"></a><span data-ttu-id="8ccc0-167">課程工作</span><span class="sxs-lookup"><span data-stu-id="8ccc0-167">Lesson Tasks</span></span>  
 <span data-ttu-id="8ccc0-168">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="8ccc0-168">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="8ccc0-169">步驟 1:建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="8ccc0-169">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="8ccc0-170">步驟 2:新增和設定一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="8ccc0-170">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="8ccc0-171">步驟 3：新增和設定 OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="8ccc0-171">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="8ccc0-172">步驟 4：將資料流程工作新增至封裝</span><span class="sxs-lookup"><span data-stu-id="8ccc0-172">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [<span data-ttu-id="8ccc0-173">步驟 5：新增和設定一般檔案來源</span><span class="sxs-lookup"><span data-stu-id="8ccc0-173">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [<span data-ttu-id="8ccc0-174">步驟 6：新增和設定查閱轉換</span><span class="sxs-lookup"><span data-stu-id="8ccc0-174">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [<span data-ttu-id="8ccc0-175">步驟 7：新增和設定 OLE DB 目的地</span><span class="sxs-lookup"><span data-stu-id="8ccc0-175">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [<span data-ttu-id="8ccc0-176">步驟 8：使第 1 課的封裝更容易了解</span><span class="sxs-lookup"><span data-stu-id="8ccc0-176">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [<span data-ttu-id="8ccc0-177">步驟 9：測試第 1 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="8ccc0-177">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="8ccc0-178">開始課程</span><span class="sxs-lookup"><span data-stu-id="8ccc0-178">Start the Lesson</span></span>  
 [<span data-ttu-id="8ccc0-179">步驟 1:建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="8ccc0-179">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
