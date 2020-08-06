---
title: 資料分析工作和檢視器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], about data profiling
- data profiling
- profiling data
ms.assetid: 756840e3-aa09-45cd-9951-1a17af4b5925
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae15d1cc75f8db04c36a830e44d07800c5aecf75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594632"
---
# <a name="data-profiling-task-and-viewer"></a><span data-ttu-id="8fd0b-102">資料分析工作和檢視器</span><span class="sxs-lookup"><span data-stu-id="8fd0b-102">Data Profiling Task and Viewer</span></span>
  <span data-ttu-id="8fd0b-103">「資料分析」工作提供擷取、轉換和載入資料之處理內部的資料分析功能。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-103">The Data Profiling task provides data profiling functionality inside the process of extracting, transforming, and loading data.</span></span> <span data-ttu-id="8fd0b-104">您可以使用「資料分析」工作來獲得下列好處：</span><span class="sxs-lookup"><span data-stu-id="8fd0b-104">By using the Data Profiling task, you can achieve the following benefits:</span></span>  
  
-   <span data-ttu-id="8fd0b-105">更有效率地分析來源資料</span><span class="sxs-lookup"><span data-stu-id="8fd0b-105">Analyze the source data more effectively</span></span>  
  
-   <span data-ttu-id="8fd0b-106">深入了解來源資料</span><span class="sxs-lookup"><span data-stu-id="8fd0b-106">Understand the source data better</span></span>  
  
-   <span data-ttu-id="8fd0b-107">在資料品質問題引進資料倉儲前加以預防。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-107">Prevent data quality problems before they are introduced into the data warehouse.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8fd0b-108">資料分析工作僅用於儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的資料。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-108">The Data Profiling task works only with data that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8fd0b-109">此工作不適用於協力廠商或以檔案為基礎的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-109">It does not work with third-party or file-based data sources.</span></span>  
  
## <a name="data-profiling-overview"></a><span data-ttu-id="8fd0b-110">資料分析概觀</span><span class="sxs-lookup"><span data-stu-id="8fd0b-110">Data Profiling Overview</span></span>  
 <span data-ttu-id="8fd0b-111">資料品質對於每個企業都相當重要。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-111">Data quality is important to every business.</span></span> <span data-ttu-id="8fd0b-112">企業會在其交易系統頂層建立分析和商業智慧系統，因此，關鍵效能指標和資料採礦預測的可靠性完全取決於它們所依據之資料的有效性。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-112">As enterprises build analytical and business intelligence systems on top of their transactional systems, the reliability of key performance indicators and of data mining predictions depends completely on the validity of the data on which they are based.</span></span> <span data-ttu-id="8fd0b-113">雖然商務決策之有效資料的重要性與日遽增，但是確定此資料之有效性的挑戰也日漸重要。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-113">But although the importance of valid data for business decision-making is increasing, the challenge of making sure of this data's validity is also increasing.</span></span> <span data-ttu-id="8fd0b-114">資料會不斷從各種系統和來源以及大量使用者串流到企業。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-114">Data is streaming into the enterprise constantly from diverse systems and sources, and a large numbers of users.</span></span>  
  
 <span data-ttu-id="8fd0b-115">資料品質的標準專屬於網域或應用程式，因此可能難以定義。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-115">Metrics for data quality can be difficult to define because they are specific to the domain or the application.</span></span> <span data-ttu-id="8fd0b-116">定義資料品質的一個常見方式為資料分析。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-116">One common approach to defining data quality is data profiling.</span></span>  
  
 <span data-ttu-id="8fd0b-117">資料分析是有關資料之彙總統計資料的集合，可能包括：</span><span class="sxs-lookup"><span data-stu-id="8fd0b-117">A data profile is a collection of aggregate statistics about data that might include the following:</span></span>  
  
-   <span data-ttu-id="8fd0b-118">Customer 資料表中的資料列數。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-118">The number of rows in the Customer table.</span></span>  
  
-   <span data-ttu-id="8fd0b-119">[州] 資料行中的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-119">The number of distinct values in the State column.</span></span>  
  
-   <span data-ttu-id="8fd0b-120">[郵遞區號] 資料行中的 null 或遺漏值的數目。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-120">The number of null or missing values in the Zip column.</span></span>  
  
-   <span data-ttu-id="8fd0b-121">[城市] 資料行中之值的散發。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-121">The distribution of values in the City column.</span></span>  
  
-   <span data-ttu-id="8fd0b-122">[郵遞區號] 資料行上，[州] 資料行之功能相依性的強度，也就是說，對於給定的郵遞區號值而言，州永遠相同。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-122">The strength of the functional dependency of the State column on the Zip column-that is, the state should always be the same for a given zip value.</span></span>  
  
 <span data-ttu-id="8fd0b-123">資料設定檔所提供的統計資料可提供您所需的資訊，以便將使用來源資料時可能發生的品質問題有效地降到最低。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-123">The statistics that a data profile provides gives you the information that you need in order to effectively minimize the quality issues that might occur from using the source data.</span></span>  
  
## <a name="integration-services-and-data-profiling"></a><span data-ttu-id="8fd0b-124">Integration Services 與資料分析</span><span class="sxs-lookup"><span data-stu-id="8fd0b-124">Integration Services and Data Profiling</span></span>  
 <span data-ttu-id="8fd0b-125">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，資料分析程序由下列步驟所組成：</span><span class="sxs-lookup"><span data-stu-id="8fd0b-125">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the data profiling process consist of the following steps:</span></span>  
  
 <span data-ttu-id="8fd0b-126">**步驟 1：設定資料分析工作**</span><span class="sxs-lookup"><span data-stu-id="8fd0b-126">**Step 1: Setting up the Data Profiling Task**</span></span>  
 <span data-ttu-id="8fd0b-127">「資料分析」工作是一種工作，可用於設定您要計算的設定檔。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-127">The Data Profiling task is a task that you use to configure the profiles that you want to compute.</span></span> <span data-ttu-id="8fd0b-128">然後，您可以執行包含「資料分析」工作的封裝以計算設定檔。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-128">You then run the package that contains the Data Profiling task to compute the profiles.</span></span> <span data-ttu-id="8fd0b-129">此工作會將設定檔輸出以 XML 格式儲存到檔案或封裝變數。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-129">The task saves the profile output in XML format to a file or a package variable.</span></span>  
  
 <span data-ttu-id="8fd0b-130">**如需詳細資訊：＜＞**[資料分析工作的設定](data-profiling-task.md)</span><span class="sxs-lookup"><span data-stu-id="8fd0b-130">**For more information:** [Setup of the Data Profiling Task](data-profiling-task.md)</span></span>  
  
 <span data-ttu-id="8fd0b-131">**步驟 2：檢閱資料分析工作計算的設定檔**</span><span class="sxs-lookup"><span data-stu-id="8fd0b-131">**Step 2: Reviewing the Profiles that the Data Profiling Task Computes**</span></span>  
 <span data-ttu-id="8fd0b-132">若要檢視「資料分析」工作計算的資料設定檔，您可以將輸出傳送到檔案，然後使用「資料設定檔檢視器」即可。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-132">To view the data profiles that the Data Profiling task computes, you send the output to a file, and then you use the Data Profile Viewer.</span></span> <span data-ttu-id="8fd0b-133">這個檢視器是一個獨立的公用程式，可以用摘要和詳細資料格式，顯示具有選擇性向下鑽研能力的設定檔輸出。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-133">This viewer is a stand-alone utility that displays the profile output in both summary and detail format with optional drilldown capability.</span></span>  
  
 <span data-ttu-id="8fd0b-134">**如需詳細資訊：＜＞**[資料設定檔檢視器](data-profile-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="8fd0b-134">**For more information:** [Data Profile Viewer](data-profile-viewer.md)</span></span>  
  
### <a name="addition-of-conditional-logic-to-the-data-profiling-workflow"></a><span data-ttu-id="8fd0b-135">將條件式邏輯加入資料分析工作流程</span><span class="sxs-lookup"><span data-stu-id="8fd0b-135">Addition of Conditional Logic to the Data Profiling Workflow</span></span>  
 <span data-ttu-id="8fd0b-136">「資料分析」工作沒有內建的功能，您無法根據設定檔輸出，使用條件式邏輯將此工作連接到下游工作。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-136">The Data Profiling task does not have built-in features that allow you to use conditional logic to connect this task to downstream tasks based on the profile output.</span></span> <span data-ttu-id="8fd0b-137">不過，您可以利用少量的程式設計，在「指令碼」工作中輕鬆加入這個邏輯。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-137">However, you can easily add this logic, with a small amount of programming, in a Script task.</span></span> <span data-ttu-id="8fd0b-138">例如，「指令碼」工作可以根據「資料分析」工作的輸出檔，執行 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-138">For example, the Script task could perform an XPath query against the output file of the Data Profiling task.</span></span> <span data-ttu-id="8fd0b-139">此查詢可以判斷特定資料行中，null 值的百分比是否超出特定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-139">The query could determine whether the percentage of null values in a particular column exceeds a certain threshold.</span></span> <span data-ttu-id="8fd0b-140">如果百分比超出臨界值，您可以中斷封裝，並解決來源資料中的問題，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-140">If the percentage exceeds the threshold, you could interrupt the package and resolve the problem in the source data before continuing.</span></span> <span data-ttu-id="8fd0b-141">如需詳細資訊，請參閱 [在封裝工作流程中納入資料分析工作](incorporate-a-data-profiling-task-in-package-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd0b-141">For more information, see [Incorporate a Data Profiling Task in Package Workflow](incorporate-a-data-profiling-task-in-package-workflow.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="8fd0b-142">相關內容</span><span class="sxs-lookup"><span data-stu-id="8fd0b-142">Related Content</span></span>  
 [<span data-ttu-id="8fd0b-143">資料分析工具結構描述</span><span class="sxs-lookup"><span data-stu-id="8fd0b-143">Data Profiler Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=251524)  
  
  
