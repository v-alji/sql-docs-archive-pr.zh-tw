---
title: 在套件工作流程中納入資料分析工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], using output in workflow
ms.assetid: 39a51586-6977-4c45-b80b-0157a54ad510
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd3544586ac99f66b961f7961e4f4af4d9e4a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594631"
---
# <a name="incorporate-a-data-profiling-task-in-package-workflow"></a><span data-ttu-id="85622-102">在封裝工作流程中納入資料分析工作</span><span class="sxs-lookup"><span data-stu-id="85622-102">Incorporate a Data Profiling Task in Package Workflow</span></span>
  <span data-ttu-id="85622-103">在早期階段中，資料分析和清除並非自動化處理序的候選項目。</span><span class="sxs-lookup"><span data-stu-id="85622-103">Data profiling and cleanup are not candidates for an automated process in their early stages.</span></span> <span data-ttu-id="85622-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，資料分析工作的輸出通常需要進行視覺化分析和人為判斷，才能決定報告的違規項目是否有意義，或是否為過度報告。</span><span class="sxs-lookup"><span data-stu-id="85622-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the output of the Data Profiling task usually requires visual analysis and human judgment to determine whether reported violations are meaningful or excessive.</span></span> <span data-ttu-id="85622-105">甚至在辨識出資料品質問題之後，您仍然必須仔細地全盤規劃，尋求最佳的清除方法。</span><span class="sxs-lookup"><span data-stu-id="85622-105">Even after recognizing data quality problems, there still has to be a carefully thought-out plan that addresses the best approach for cleanup.</span></span>  
  
 <span data-ttu-id="85622-106">不過，當資料品質的準則確立之後，您可能會想要自動化資料來源的定期分析與清除作業。</span><span class="sxs-lookup"><span data-stu-id="85622-106">However, after criteria for data quality have been established, you might want to automate a periodic analysis and cleanup of the data source.</span></span> <span data-ttu-id="85622-107">請考慮這些狀況：</span><span class="sxs-lookup"><span data-stu-id="85622-107">Consider these scenarios:</span></span>  
  
-   <span data-ttu-id="85622-108">**在累加式載入之前檢查資料品質**：</span><span class="sxs-lookup"><span data-stu-id="85622-108">**Checking data quality before an incremental load**.</span></span> <span data-ttu-id="85622-109">您可以使用資料分析工作，針對用於 Customers 資料表之 CustomerName 資料行的新資料計算資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-109">Use the Data Profiling task to compute the Column Null Ratio Profile of new data intended for the CustomerName column in a Customers table.</span></span> <span data-ttu-id="85622-110">如果 Null 值的百分比大於 20%，便傳送一則包含設定檔輸出的電子郵件訊息給操作員，然後結束封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-110">If the percentage of null values is greater than 20%, send an e-mail message that contains the profile output to the operator and end the package.</span></span> <span data-ttu-id="85622-111">否則，便繼續累加式載入。</span><span class="sxs-lookup"><span data-stu-id="85622-111">Otherwise, continue the incremental load.</span></span>  
  
-   <span data-ttu-id="85622-112">**符合指定的條件時自動化清除**：</span><span class="sxs-lookup"><span data-stu-id="85622-112">**Automating cleanup when the specified conditions are met**.</span></span> <span data-ttu-id="85622-113">您可以使用資料分析工作，針對 State 資料行 (根據州的查閱資料表) 和 ZIP Code/Postal Code 資料行 (根據郵遞區號的查閱資料表) 計算值包含設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-113">Use the Data Profiling task to compute the Value Inclusion Profile of the State column against a lookup table of states, and of the ZIP Code/Postal Code column against a lookup table of zip codes.</span></span> <span data-ttu-id="85622-114">如果州值的包含強度小於 80%，但是郵遞區號值的包含強度大於 99%，這就代表兩件事。</span><span class="sxs-lookup"><span data-stu-id="85622-114">If the inclusion strength of the state values is less than 80%, but the inclusion strength of the ZIP Code/Postal Code values is greater than 99%, this indicates two things.</span></span> <span data-ttu-id="85622-115">首先，州的資料不正確。</span><span class="sxs-lookup"><span data-stu-id="85622-115">First, the state data is bad.</span></span> <span data-ttu-id="85622-116">其次，郵遞區號的資料是正確的。</span><span class="sxs-lookup"><span data-stu-id="85622-116">Second, the ZIP Code/Postal Code data is good.</span></span> <span data-ttu-id="85622-117">您可以透過根據目前郵遞區號值執行正確州值的查閱，啟動清除州資料的資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="85622-117">Launch a Data Flow task that cleans up the state data by performing a lookup of the correct state value from the current Zip Code/Postal Code value.</span></span>  
  
 <span data-ttu-id="85622-118">在您設有可合併資料流程工作的工作流程之後，就必須了解加入這項工作所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="85622-118">After you have a workflow into which you can incorporate the Data Flow task, you have to understand the steps that are required to add this task.</span></span> <span data-ttu-id="85622-119">下一節將描述合併資料流程工作的一般程序。</span><span class="sxs-lookup"><span data-stu-id="85622-119">The next section describes the general process of incorporating the Data Flow task.</span></span> <span data-ttu-id="85622-120">最後兩節則描述如何將資料流程工作直接連接至資料來源，或連接至資料流程的已轉換資料。</span><span class="sxs-lookup"><span data-stu-id="85622-120">The final two sections describe how to connect the Data Flow task either directly to a data source or to transformed data from the Data Flow.</span></span>  
  
## <a name="defining-a-general-workflow-for-the-data-flow-task"></a><span data-ttu-id="85622-121">定義資料流程工作的一般工作流程</span><span class="sxs-lookup"><span data-stu-id="85622-121">Defining a General Workflow for the Data Flow Task</span></span>  
 <span data-ttu-id="85622-122">下列程序將概述在封裝之工作流程中使用資料分析工作輸出的一般方法。</span><span class="sxs-lookup"><span data-stu-id="85622-122">The following procedure outlines the general approach for using the output of the Data Profiling task in the workflow of a package.</span></span>  
  
#### <a name="to-use-the-output-of-the-data-profiling-task-programmatically-in-a-package"></a><span data-ttu-id="85622-123">以程式設計方式在封裝中使用資料分析工作的輸出</span><span class="sxs-lookup"><span data-stu-id="85622-123">To use the output of the Data Profiling task programmatically in a package</span></span>  
  
1.  <span data-ttu-id="85622-124">加入並設定封裝中的資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-124">Add and configure the Data Profiling task in a package.</span></span>  
  
2.  <span data-ttu-id="85622-125">設定封裝變數，以便保存您想要從設定檔結果中擷取的值。</span><span class="sxs-lookup"><span data-stu-id="85622-125">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
3.  <span data-ttu-id="85622-126">加入並設定指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="85622-126">Add and configure a Script task.</span></span> <span data-ttu-id="85622-127">將指令碼工作連接至資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-127">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="85622-128">在指令碼工作中，撰寫從資料分析工作之輸出檔中讀取所需值並填入封裝變數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="85622-128">In the Script task, write code that reads the desired values from the output file of the Data Profiling task and populates the package variables.</span></span>  
  
4.  <span data-ttu-id="85622-129">在將指令碼工作連接至工作流程中下游分支的優先順序條件約束中，撰寫使用變數值來導向工作流程的運算式。</span><span class="sxs-lookup"><span data-stu-id="85622-129">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
 <span data-ttu-id="85622-130">將資料分析工作併入封裝的工作流程時，請記住此工作的兩個功能：</span><span class="sxs-lookup"><span data-stu-id="85622-130">When incorporating the Data Profiling task into the workflow of a package, keep these two features of the task in mind:</span></span>  
  
-   <span data-ttu-id="85622-131">**工作輸出**：</span><span class="sxs-lookup"><span data-stu-id="85622-131">**Task output**.</span></span> <span data-ttu-id="85622-132">資料分析工作會根據 DataProfile.xsd 結構描述，以 XML 格式將其輸出寫入檔案或封裝變數中。</span><span class="sxs-lookup"><span data-stu-id="85622-132">The Data Profiling task writes its output to a file or a package variable in XML format according to the DataProfile.xsd schema.</span></span> <span data-ttu-id="85622-133">因此，如果您想要在封裝的條件式工作流程中使用設定檔結果，就必須查詢 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-133">Therefore, you have to query the XML output if you want to use the profile results in the conditional workflow of a package.</span></span> <span data-ttu-id="85622-134">您可以輕易地使用 Xpath 查詢語言來查詢這個 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-134">You can easily use the Xpath query language to query this XML output.</span></span> <span data-ttu-id="85622-135">若要研究這個 XML 輸出的結構，您可以開啟範例輸出檔或結構描述本身。</span><span class="sxs-lookup"><span data-stu-id="85622-135">To study the structure of this XML output, you can open a sample output file or the schema itself.</span></span> <span data-ttu-id="85622-136">若要開啟輸出檔案或結構描述，您可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、其他 XML 編輯器或文字編輯器 (例如 [記事本])。</span><span class="sxs-lookup"><span data-stu-id="85622-136">To open the output file or schema, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], another XML editor, or a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85622-137">某些顯示在「資料設定檔檢視器」中的設定檔結果是無法直接在輸出中找到的計算值。</span><span class="sxs-lookup"><span data-stu-id="85622-137">Some of the profile results that are displayed in the Data Profile Viewer are calculated values that are not directly found in the output.</span></span> <span data-ttu-id="85622-138">例如，資料行 Null 比例設定檔的輸出包含了資料列總數以及含有 Null 值的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="85622-138">For example, the output of the Column Null Ratio Profile contains the total number of rows and the number of rows that contain null values.</span></span> <span data-ttu-id="85622-139">您必須查詢這兩個值，然後計算含有 Null 值的資料列百分比，才能取得資料行 Null 比例。</span><span class="sxs-lookup"><span data-stu-id="85622-139">You have to query these two values, and then calculate the percentage of rows that contain null values, to obtain the column null ratio.</span></span>  
  
-   <span data-ttu-id="85622-140">**工作輸入**：</span><span class="sxs-lookup"><span data-stu-id="85622-140">**Task input**.</span></span> <span data-ttu-id="85622-141">資料分析工作會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中讀取其輸入。</span><span class="sxs-lookup"><span data-stu-id="85622-141">The Data Profiling task reads its input from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="85622-142">因此，如果您想要分析已經在資料流程中載入並轉換的資料，就必須將記憶體中的資料儲存至臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="85622-142">Therefore, you have to save data that is in memory to staging tables if you want to profile data that has already been loaded and transformed in the data flow.</span></span>  
  
 <span data-ttu-id="85622-143">下列各節會將這個一般工作流程套用至直接來自外部資料來源或從資料流程工作轉換的分析資料。</span><span class="sxs-lookup"><span data-stu-id="85622-143">The following sections apply this general workflow to profiling data that comes directly from an external data source or that comes transformed from the Data Flow task.</span></span> <span data-ttu-id="85622-144">此外，這些章節也會說明如何處理資料流程工作的輸入和輸出需求。</span><span class="sxs-lookup"><span data-stu-id="85622-144">These sections also show how to handle the input and output requirements of the Data Flow task.</span></span>  
  
## <a name="connecting-the-data-profiling-task-directly-to-an-external-data-source"></a><span data-ttu-id="85622-145">將資料分析工作直接連接至外部資料來源</span><span class="sxs-lookup"><span data-stu-id="85622-145">Connecting the Data Profiling Task Directly to an External Data Source</span></span>  
 <span data-ttu-id="85622-146">資料分析工作可以分析直接來自某個資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="85622-146">The Data Profiling task can profile data that comes directly from a data source.</span></span>  <span data-ttu-id="85622-147">為了說明這項功能，下列範例會使用資料分析工作，針對 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中 Person.Address 資料表的資料行計算資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-147">To illustrate this capability, the following example uses the Data Profiling task to compute a Column Null Ratio Profile on the columns of the Person.Address table in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="85622-148">然後，這則範例會使用指令碼工作，從輸出檔中擷取結果並填入可用來導向工作流程的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="85622-148">Then, this example uses a Script task to retrieve the results from the output file and populate package variables that can be used to direct workflow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85622-149">在這則簡易範例中，我們選取了 AddressLine2 資料行，因為這個資料行包含 Null 值的百分比很高。</span><span class="sxs-lookup"><span data-stu-id="85622-149">The AddressLine2 column was selected for this simple example because this column contains a high percentage of null values.</span></span>  
  
 <span data-ttu-id="85622-150">這個範例包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="85622-150">This example consists of the following steps:</span></span>  
  
-   <span data-ttu-id="85622-151">設定連接管理員，以便連接至外部資料來源以及即將包含設定檔結果的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="85622-151">Configuring the connection managers that connect to the external data source and to the output file that will contain the profile results.</span></span>  
  
-   <span data-ttu-id="85622-152">設定封裝變數，以便保存資料分析工作所需的值。</span><span class="sxs-lookup"><span data-stu-id="85622-152">Configuring the package variables that will hold the values needed by the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="85622-153">設定資料分析工作，以便計算資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-153">Configuring the Data Profiling task to compute the Column Null Ratio Profile.</span></span>  
  
-   <span data-ttu-id="85622-154">設定指令碼工作，以便處理資料分析工作的 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-154">Configuring the Script task to work the XML output from the Data Profiling task.</span></span>  
  
-   <span data-ttu-id="85622-155">設定優先順序條件約束，以便控制工作流程中的哪些下游分支會根據資料分析工作的結果執行。</span><span class="sxs-lookup"><span data-stu-id="85622-155">Configuring the precedence constraints that will control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
### <a name="configure-the-connection-managers"></a><span data-ttu-id="85622-156">設定連接管理員</span><span class="sxs-lookup"><span data-stu-id="85622-156">Configure the Connection Managers</span></span>  
 <span data-ttu-id="85622-157">在這則範例中，我們設有兩個連接管理員：</span><span class="sxs-lookup"><span data-stu-id="85622-157">For this example, there are two connection managers:</span></span>  
  
-   <span data-ttu-id="85622-158">連接至 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 資料庫的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="85622-158">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
-   <span data-ttu-id="85622-159">建立輸出檔以便保存資料分析工作結果的檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="85622-159">A File connection manager that creates the output file that will hold the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="85622-160">設定連接管理員</span><span class="sxs-lookup"><span data-stu-id="85622-160">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="85622-161">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，建立新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-161">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="85622-162">將 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員加入至封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-162">Add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to the package.</span></span> <span data-ttu-id="85622-163">將這個連線管理員設定為使用 NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) 並連接至 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫的可用執行個體。</span><span class="sxs-lookup"><span data-stu-id="85622-163">Configure this connection manager to use the NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) and to connect to an available instance of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span>  
  
     <span data-ttu-id="85622-164">根據預設，此連線管理員具有下列名稱：\<server name>.AdventureWorks1。</span><span class="sxs-lookup"><span data-stu-id="85622-164">By default, the connection manager has the following name: \<server name>.AdventureWorks1.</span></span>  
  
3.  <span data-ttu-id="85622-165">將檔案連接管理員加入至封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-165">Add a File connection manager to the package.</span></span> <span data-ttu-id="85622-166">將這個連接管理員設定為建立資料分析工作的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="85622-166">Configure this connection manager to create the output file for the Data Profiling task.</span></span>  
  
     <span data-ttu-id="85622-167">這個範例會使用檔案名稱 DataProfile1.xml。</span><span class="sxs-lookup"><span data-stu-id="85622-167">This example uses the file name, DataProfile1.xml.</span></span> <span data-ttu-id="85622-168">根據預設，此連接管理員與該檔案具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="85622-168">By default, the connection manager has the same name as the file.</span></span>  
  
### <a name="configure-the-package-variables"></a><span data-ttu-id="85622-169">設定封裝變數</span><span class="sxs-lookup"><span data-stu-id="85622-169">Configure the Package Variables</span></span>  
 <span data-ttu-id="85622-170">這個範例會使用兩個封裝變數：</span><span class="sxs-lookup"><span data-stu-id="85622-170">This example uses two package variables:</span></span>  
  
-   <span data-ttu-id="85622-171">ProfileConnectionName 變數會將檔案連接管理員的名稱傳遞給指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="85622-171">The ProfileConnectionName variable passes the name of the File connection manager to the Script task.</span></span>  
  
-   <span data-ttu-id="85622-172">AddressLine2NullRatio 變數會從指令碼工作將這個資料行的已計算 Null 比例傳遞給封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-172">The AddressLine2NullRatio variable passes the calculated null ratio for this column out of the Script task to the package.</span></span>  
  
##### <a name="to-configure-the-package-variables-that-will-hold-profile-results"></a><span data-ttu-id="85622-173">設定即將保存設定檔結果的封裝變數</span><span class="sxs-lookup"><span data-stu-id="85622-173">To configure the package variables that will hold profile results</span></span>  
  
-   <span data-ttu-id="85622-174">在 **[變數]** 視窗中，加入並設定下列兩個封裝變數：</span><span class="sxs-lookup"><span data-stu-id="85622-174">In the **Variables** window, add and configure the following two package variables:</span></span>  
  
    -   <span data-ttu-id="85622-175">`ProfileConnectionName`為其中一個變數輸入名稱，並將此變數的類型設定為 [**字串**]。</span><span class="sxs-lookup"><span data-stu-id="85622-175">Enter the name, `ProfileConnectionName`, for one of the variables and set the type of this variable to **String**.</span></span>  
  
    -   <span data-ttu-id="85622-176">輸入其他變數的名稱， `AddressLine2NullRatio` 並將此變數的類型設定為**Double**。</span><span class="sxs-lookup"><span data-stu-id="85622-176">Enter the name, `AddressLine2NullRatio`, for the other variable and set the type of this variable to **Double**.</span></span>  
  
### <a name="configure-the-data-profiling-task"></a><span data-ttu-id="85622-177">設定資料分析工作</span><span class="sxs-lookup"><span data-stu-id="85622-177">Configure the Data Profiling Task</span></span>  
 <span data-ttu-id="85622-178">您必須以下列方式來設定資料分析工作：</span><span class="sxs-lookup"><span data-stu-id="85622-178">The Data Profiling task has to be configured in the following way:</span></span>  
  
-   <span data-ttu-id="85622-179">使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員所提供的資料當做輸入。</span><span class="sxs-lookup"><span data-stu-id="85622-179">To use the data that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager supplies as input.</span></span>  
  
-   <span data-ttu-id="85622-180">針對輸入資料執行資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-180">To perform a Column Null Ratio profile on the input data.</span></span>  
  
-   <span data-ttu-id="85622-181">將設定檔結果儲存至與檔案連接管理員相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="85622-181">To save the profile results to the file that is associated with the File connection manager.</span></span>  
  
##### <a name="to-configure-the-data-profiling-task"></a><span data-ttu-id="85622-182">設定資料分析工作</span><span class="sxs-lookup"><span data-stu-id="85622-182">To configure the Data Profiling task</span></span>  
  
1.  <span data-ttu-id="85622-183">針對控制流程，加入資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-183">To the Control Flow, add a Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="85622-184">開啟 **[資料分析工作編輯器]** 以便設定工作。</span><span class="sxs-lookup"><span data-stu-id="85622-184">Open the **Data Profiling Task Editor** to configure the task.</span></span>  
  
3.  <span data-ttu-id="85622-185">在編輯器的 **[一般]** 頁面中，針對 **[目的地]** 選取您先前設定之檔案連接管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="85622-185">On the **General** page of the editor, for **Destination**, select the name of the File connection manager that you have previously configured.</span></span>  
  
4.  <span data-ttu-id="85622-186">在編輯器的 **[設定檔要求]** 頁面中，建立新的資料行 Null 比例設定檔。</span><span class="sxs-lookup"><span data-stu-id="85622-186">On the **Profile Requests** page of the editor, create a new Column Null Ratio Profile.</span></span>  
  
5.  <span data-ttu-id="85622-187">在 **[要求屬性]** 窗格中，針對 **[ConnectionManager]** 選取您先前設定的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="85622-187">In the **Request properties** pane, for **ConnectionManager**, select the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that you have previously configured.</span></span> <span data-ttu-id="85622-188">然後，針對 **[TableOrView]** 選取 Person.Address。</span><span class="sxs-lookup"><span data-stu-id="85622-188">Then, for **TableOrView**, select Person.Address.</span></span>  
  
6.  <span data-ttu-id="85622-189">關閉 [資料分析工作編輯器]。</span><span class="sxs-lookup"><span data-stu-id="85622-189">Close the Data Profiling Task Editor.</span></span>  
  
### <a name="configure-the-script-task"></a><span data-ttu-id="85622-190">設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="85622-190">Configure the Script Task</span></span>  
 <span data-ttu-id="85622-191">您必須設定指令碼工作，以便從輸出檔中擷取結果，然後填入先前設定的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="85622-191">The Script task has to be configured to retrieve the results from the output file and populate the package variables that were previously configured.</span></span>  
  
##### <a name="to-configure-the-script-task"></a><span data-ttu-id="85622-192">設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="85622-192">To configure the Script task</span></span>  
  
1.  <span data-ttu-id="85622-193">針對控制流程，加入指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="85622-193">To the Control Flow, add a Script task.</span></span>  
  
2.  <span data-ttu-id="85622-194">將指令碼工作連接至資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-194">Connect the Script task to the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="85622-195">開啟 **[指令碼工作編輯器]** 以便設定工作。</span><span class="sxs-lookup"><span data-stu-id="85622-195">Open the **Script Task Editor** to configure the task.</span></span>  
  
4.  <span data-ttu-id="85622-196">在 **[指令碼]** 頁面中，選取您慣用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="85622-196">On the **Script** page, select your preferred programming language.</span></span> <span data-ttu-id="85622-197">然後，讓這兩個封裝變數可供指令碼使用：</span><span class="sxs-lookup"><span data-stu-id="85622-197">Then, make the two package variables available to the script:</span></span>  
  
    1.  <span data-ttu-id="85622-198">針對 `ReadOnlyVariables` 選取 [] `ProfileConnectionName` 。</span><span class="sxs-lookup"><span data-stu-id="85622-198">For `ReadOnlyVariables`, select `ProfileConnectionName`.</span></span>  
  
    2.  <span data-ttu-id="85622-199">針對 [ **ReadWriteVariables**]，選取 `AddressLine2NullRatio` 。</span><span class="sxs-lookup"><span data-stu-id="85622-199">For **ReadWriteVariables**, select `AddressLine2NullRatio`.</span></span>  
  
5.  <span data-ttu-id="85622-200">選取 **[編輯指令碼]** 以便開啟指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="85622-200">Select **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="85622-201">加入 System.Xml 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="85622-201">Add a reference to the System.Xml namespace.</span></span>  
  
7.  <span data-ttu-id="85622-202">輸入對應至您程式語言的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="85622-202">Enter the sample code that corresponds to your programming language:</span></span>  
  
    ```vb  
    Imports System  
    Imports Microsoft.SqlServer.Dts.Runtime  
    Imports System.Xml  
  
    Public Class ScriptMain  
  
      Private FILENAME As String = "C:\ TEMP\DataProfile1.xml"  
      Private PROFILE_NAMESPACE_URI As String = "https://schemas.microsoft.com/DataDebugger/"  
      Private NULLCOUNT_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()"  
      Private TABLE_XPATH As String = _  
        "/default:DataProfile/default:DataProfileOutput/default:Profiles" & _  
        "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table"  
  
      Public Sub Main()  
  
        Dim profileConnectionName As String  
        Dim profilePath As String  
        Dim profileOutput As New XmlDocument  
        Dim profileNSM As XmlNamespaceManager  
        Dim nullCountNode As XmlNode  
        Dim nullCount As Integer  
        Dim tableNode As XmlNode  
        Dim rowCount As Integer  
        Dim nullRatio As Double  
  
        ' Open output file.  
        profileConnectionName = Dts.Variables("ProfileConnectionName").Value.ToString()  
        profilePath = Dts.Connections(profileConnectionName).ConnectionString  
        profileOutput.Load(profilePath)  
        profileNSM = New XmlNamespaceManager(profileOutput.NameTable)  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI)  
  
        ' Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM)  
        nullCount = CType(nullCountNode.Value, Integer)  
  
        ' Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM)  
        rowCount = CType(tableNode.Attributes("RowCount").Value, Integer)  
  
        ' Compute and return null ratio.  
        nullRatio = nullCount / rowCount  
        Dts.Variables("AddressLine2NullRatio").Value = nullRatio  
  
        Dts.TaskResult = Dts.Results.Success  
  
      End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SqlServer.Dts.Runtime;  
    using System.Xml;  
  
    public class ScriptMain  
    {  
  
      private string FILENAME = "C:\\ TEMP\\DataProfile1.xml";  
      private string PROFILE_NAMESPACE_URI = "https://schemas.microsoft.com/DataDebugger/";  
      private string NULLCOUNT_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:NullCount/text()";  
      private string TABLE_XPATH = "/default:DataProfile/default:DataProfileOutput/default:Profiles" + "/default:ColumnNullRatioProfile[default:Column[@Name='AddressLine2']]/default:Table";  
  
      public void Main()  
      {  
  
        string profileConnectionName;  
        string profilePath;  
        XmlDocument profileOutput = new XmlDocument();  
        XmlNamespaceManager profileNSM;  
        XmlNode nullCountNode;  
        int nullCount;  
        XmlNode tableNode;  
        int rowCount;  
        double nullRatio;  
  
        // Open output file.  
        profileConnectionName = Dts.Variables["ProfileConnectionName"].Value.ToString();  
        profilePath = Dts.Connections[profileConnectionName].ConnectionString;  
        profileOutput.Load(profilePath);  
        profileNSM = new XmlNamespaceManager(profileOutput.NameTable);  
        profileNSM.AddNamespace("default", PROFILE_NAMESPACE_URI);  
  
        // Get null count for column.  
        nullCountNode = profileOutput.SelectSingleNode(NULLCOUNT_XPATH, profileNSM);  
        nullCount = (int)nullCountNode.Value;  
  
        // Get row count for table.  
        tableNode = profileOutput.SelectSingleNode(TABLE_XPATH, profileNSM);  
        rowCount = (int)tableNode.Attributes["RowCount"].Value;  
  
        // Compute and return null ratio.  
        nullRatio = nullCount / rowCount;  
        Dts.Variables["AddressLine2NullRatio"].Value = nullRatio;  
  
        Dts.TaskResult = Dts.Results.Success;  
  
      }  
  
    }  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="85622-203">這個程序中顯示的範例程式碼會說明如何從檔案載入資料分析工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-203">The sample code shown in this procedure demonstrates how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="85622-204">若要改為從封裝變數載入資料分析工作的輸出，請參閱這個程序後面的替代範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="85622-204">To load the output of the Data Profiling task from a package variable instead, see the alternative sample code that follows this procedure.</span></span>  
  
8.  <span data-ttu-id="85622-205">關閉指令碼開發環境，然後關閉 [指令碼工作編輯器]。</span><span class="sxs-lookup"><span data-stu-id="85622-205">Close the script development environment, and then close the Script Task Editor.</span></span>  
  
#### <a name="alternative-code-reading-the-profile-output-from-a-variable"></a><span data-ttu-id="85622-206">替代程式碼 - 從變數中讀取設定檔輸出</span><span class="sxs-lookup"><span data-stu-id="85622-206">Alternative Code-Reading the Profile Output from a Variable</span></span>  
 <span data-ttu-id="85622-207">上一個程序說明如何從檔案載入資料分析工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-207">The previous procedure shows how to load the output of the Data Profiling task from a file.</span></span> <span data-ttu-id="85622-208">不過，我們提供了替代方法，可從封裝變數載入這個輸出。</span><span class="sxs-lookup"><span data-stu-id="85622-208">However, an alternative method would be to load this output from a package variable.</span></span> <span data-ttu-id="85622-209">若要從變數載入封裝，您必須針對範例程式碼進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="85622-209">To load the output from a variable, you have to make the following changes to the sample code:</span></span>  
  
-   <span data-ttu-id="85622-210">呼叫 `LoadXml` 類別的 `XmlDocument` 方法，而非 `Load` 方法。</span><span class="sxs-lookup"><span data-stu-id="85622-210">Call the `LoadXml` method of the `XmlDocument` class instead of the `Load` method.</span></span>  
  
-   <span data-ttu-id="85622-211">在 [指令碼工作編輯器] 中，將包含設定檔輸出之封裝變數的名稱加入至工作的 `ReadOnlyVariables` 清單。</span><span class="sxs-lookup"><span data-stu-id="85622-211">In the Script Task Editor, add the name of the package variable that contains the profile output to the task's `ReadOnlyVariables` list.</span></span>  
  
-   <span data-ttu-id="85622-212">將變數的字串值傳遞給 `LoadXML` 方法，如下列程式碼範例所示 </span><span class="sxs-lookup"><span data-stu-id="85622-212">Pass the string value of the variable to the `LoadXML` method, as shown in the following code example.</span></span> <span data-ttu-id="85622-213">(這個範例會使用 "ProfileOutput" 當做包含設定檔輸出之封裝變數的名稱)。</span><span class="sxs-lookup"><span data-stu-id="85622-213">(This example uses "ProfileOutput" as the name of the package variable that contains the profile output.)</span></span>  
  
    ```vb  
    Dim outputString As String  
    outputString = Dts.Variables("ProfileOutput").Value.ToString()  
    ...  
    profileOutput.LoadXml(outputString)  
    ```  
  
    ```csharp  
    string outputString;  
    outputString = Dts.Variables["ProfileOutput"].Value.ToString();  
    ...  
    profileOutput.LoadXml(outputString);  
    ```  
  
### <a name="configure-the-precedence-constraints"></a><span data-ttu-id="85622-214">設定優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="85622-214">Configure the Precedence Constraints</span></span>  
 <span data-ttu-id="85622-215">您必須設定優先順序條件約束，以便控制工作流程中的哪些下游分支會根據資料分析工作的結果執行。</span><span class="sxs-lookup"><span data-stu-id="85622-215">The precedence constraints have to be configured to control which downstream branches in the workflow are run based on the results of the Data Profiling task.</span></span>  
  
##### <a name="to-configure-the-precedence-constraints"></a><span data-ttu-id="85622-216">設定優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="85622-216">To configure the precedence constraints</span></span>  
  
-   <span data-ttu-id="85622-217">在將指令碼工作連接至工作流程中下游分支的優先順序條件約束中，撰寫使用變數值來導向工作流程的運算式。</span><span class="sxs-lookup"><span data-stu-id="85622-217">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
     <span data-ttu-id="85622-218">例如，您可能會將優先順序條件約束的 **[評估作業]** 設定為 **[運算式與條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="85622-218">For example, you might set the **Evaluation operation** of the precedence constraint to **Expression and Constraint**.</span></span> <span data-ttu-id="85622-219">然後，您可能會使用 `@AddressLine2NullRatio < .90` 當做運算式的值。</span><span class="sxs-lookup"><span data-stu-id="85622-219">Then, you might use `@AddressLine2NullRatio < .90` as the value of the expression.</span></span> <span data-ttu-id="85622-220">當先前的工作成功，而且選取資料行中 Null 值的百分比小於 90% 時，這樣做會導致工作流程遵循選取的路徑。</span><span class="sxs-lookup"><span data-stu-id="85622-220">This causes the workflow to follow the selected path when the previous tasks succeed, and when the percentage of null values in the selected column is less than 90%.</span></span>  
  
## <a name="connecting-the-data-profiling-task-to-transformed-data-from-the-data-flow"></a><span data-ttu-id="85622-221">將資料分析工作連接至資料流程的已轉換資料</span><span class="sxs-lookup"><span data-stu-id="85622-221">Connecting the Data Profiling Task to Transformed Data from the Data Flow</span></span>  
 <span data-ttu-id="85622-222">除了分析直接來自資料來源的資料以外，您也可以分析已經在資料流程中載入並轉換的資料。</span><span class="sxs-lookup"><span data-stu-id="85622-222">Instead of profiling data directly from a data source, you can profile data that has already been loaded and transformed in the data flow.</span></span> <span data-ttu-id="85622-223">不過，資料分析工作只能針對保存的資料運作，無法針對記憶體中的資料運作。</span><span class="sxs-lookup"><span data-stu-id="85622-223">However, the Data Profiling task works only against persisted data, not against in-memory data.</span></span> <span data-ttu-id="85622-224">因此，您必須先使用目的地元件，將已轉換的資料儲存至臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="85622-224">Therefore, you must first use a destination component to save the transformed data to a staging table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85622-225">設定資料分析工作時，您必須選取現有的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="85622-225">When you configure the Data Profiling task, you have to select existing tables and columns.</span></span> <span data-ttu-id="85622-226">因此，您必須先在設計階段建立臨時資料表，然後才能設定工作。</span><span class="sxs-lookup"><span data-stu-id="85622-226">Therefore, you must create the staging table at design time before you can configure the task.</span></span> <span data-ttu-id="85622-227">換言之，這個狀況不允許您使用在執行階段建立的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="85622-227">In other words, this scenario does not allow you to use a temporary table that is created at run time.</span></span>  
  
 <span data-ttu-id="85622-228">將資料儲存至臨時資料表之後，您就可以進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="85622-228">After saving the data to a staging table, you can do the following actions:</span></span>  
  
-   <span data-ttu-id="85622-229">使用資料分析工作來分析資料。</span><span class="sxs-lookup"><span data-stu-id="85622-229">Use the Data Profiling task to profile the data.</span></span>  
  
-   <span data-ttu-id="85622-230">使用指令碼工作來讀取結果，如本主題前文所述。</span><span class="sxs-lookup"><span data-stu-id="85622-230">Use a Script task to read the results as described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="85622-231">使用這些結果來導向封裝的後續工作流程。</span><span class="sxs-lookup"><span data-stu-id="85622-231">Use those results to direct the subsequent workflow of the package.</span></span>  
  
 <span data-ttu-id="85622-232">下列程序將提供使用資料分析工作來分析已經由資料流程轉換之資料的一般方法。</span><span class="sxs-lookup"><span data-stu-id="85622-232">The following procedure provides the general approach for using the Data Profiling task to profile data that has been transformed by the data flow.</span></span> <span data-ttu-id="85622-233">其中許多步驟都與先前針對分析直接來自外部資料來源之資料所描述的步驟相同。</span><span class="sxs-lookup"><span data-stu-id="85622-233">Many of these steps are similar to the ones described earlier for profiling data that comes directly from an external data source.</span></span> <span data-ttu-id="85622-234">如需有關如何設定各種元件的詳細資訊，您可能會想要檢閱先前的步驟。</span><span class="sxs-lookup"><span data-stu-id="85622-234">You might want to review those earlier steps for more information about how to configure the various components.</span></span>  
  
#### <a name="to-use-the-data-profiling-task-in-the-data-flow"></a><span data-ttu-id="85622-235">在資料流程中使用資料分析工作</span><span class="sxs-lookup"><span data-stu-id="85622-235">To use the Data Profiling task in the data flow</span></span>  
  
1.  <span data-ttu-id="85622-236">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，建立封裝。</span><span class="sxs-lookup"><span data-stu-id="85622-236">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create a package.</span></span>  
  
2.  <span data-ttu-id="85622-237">在資料流程中，加入、設定並連接適當的來源和轉換。</span><span class="sxs-lookup"><span data-stu-id="85622-237">In the Data Flow, add, configure, and connect the appropriate sources and transformations.</span></span>  
  
3.  <span data-ttu-id="85622-238">在資料流程中，加入、設定並連接將已轉換資料儲存至臨時資料表的目的地元件。</span><span class="sxs-lookup"><span data-stu-id="85622-238">In the Data Flow, add, configure, and connect a destination component that saves the transformed data to a staging table.</span></span>  
  
4.  <span data-ttu-id="85622-239">在控制流程中，加入並設定根據臨時資料表中已轉換資料計算所需設定檔的資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-239">In the Control Flow, add and configure a Data Profiling task that computes the desired profiles against the transformed data in the staging table.</span></span> <span data-ttu-id="85622-240">將資料分析工作連接至資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="85622-240">Connect the Data Profiling task to the Data Flow task.</span></span>  
  
5.  <span data-ttu-id="85622-241">設定封裝變數，以便保存您想要從設定檔結果中擷取的值。</span><span class="sxs-lookup"><span data-stu-id="85622-241">Configure package variables to hold the values that you want to retrieve from the profile results.</span></span>  
  
6.  <span data-ttu-id="85622-242">加入並設定指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="85622-242">Add and configure a Script task.</span></span> <span data-ttu-id="85622-243">將指令碼工作連接至資料分析工作。</span><span class="sxs-lookup"><span data-stu-id="85622-243">Connect the Script task to the Data Profiling task.</span></span> <span data-ttu-id="85622-244">在指令碼工作中，撰寫從資料分析工作之輸出中讀取所需值並填入封裝變數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="85622-244">In the Script task, write code that reads the desired values from the output of the Data Profiling task and populates the package variables.</span></span>  
  
7.  <span data-ttu-id="85622-245">在將指令碼工作連接至工作流程中下游分支的優先順序條件約束中，撰寫使用變數值來導向工作流程的運算式。</span><span class="sxs-lookup"><span data-stu-id="85622-245">In the precedence constraints that connect the Script task to downstream branches in the workflow, write expressions that use the values of the variables to direct the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85622-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85622-246">See Also</span></span>  
 <span data-ttu-id="85622-247">[資料分析工作的設定](data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="85622-247">[Setup of the Data Profiling Task](data-profiling-task.md) </span></span>  
 [<span data-ttu-id="85622-248">資料設定檔檢視器</span><span class="sxs-lookup"><span data-stu-id="85622-248">Data Profile Viewer</span></span>](data-profile-viewer.md)  
  
  
