---
title: SQL Server 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 957e7091-e08f-48d2-9506-872227ae8b20
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34a519c8a291dc351be98316b18a45ade4918579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598231"
---
# <a name="sql-server-connection-type-ssrs"></a><span data-ttu-id="5fa30-102">SQL Server 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5fa30-102">SQL Server Connection Type (SSRS)</span></span>
  <span data-ttu-id="5fa30-103">若要在報表中包含來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料，您必須具有以 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-103">To include data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5fa30-104">此內建資料來源類型是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="5fa30-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data extension.</span></span> <span data-ttu-id="5fa30-105">使用此資料來源類型可連接至目前版本和舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，並從中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="5fa30-105">Use this data source type to connect to and retrieve data from the current version and earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="5fa30-106">此資料延伸模組支援多值參數、伺服器彙總，以及與連接字串分開管理的認證。</span><span class="sxs-lookup"><span data-stu-id="5fa30-106">This data extension supports multivalue parameters, server aggregates, and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="5fa30-107">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="5fa30-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="5fa30-108">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="5fa30-109">連接字串</span><span class="sxs-lookup"><span data-stu-id="5fa30-109">Connection String</span></span>  
 <span data-ttu-id="5fa30-110">當您連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫時，會連接到伺服器上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="5fa30-110">When you connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you are connecting to the database object in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server.</span></span> <span data-ttu-id="5fa30-111">資料庫可能有包含多個資料表、檢視表和預存程序的多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="5fa30-111">The database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="5fa30-112">您會指定在查詢設計工具中使用的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="5fa30-112">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="5fa30-113">如果沒有在連接字串中指定資料庫，則會連接到資料庫管理員指派給您的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="5fa30-113">If you do not specify a database in the connection string, you connect to the default database that the database administrator assigned to you.</span></span>  
  
 <span data-ttu-id="5fa30-114">請洽詢資料庫管理員，以取得用來連接資料來源的連接資訊和認證。</span><span class="sxs-lookup"><span data-stu-id="5fa30-114">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="5fa30-115">下列連接字串範例會在本機用戶端上指定範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="5fa30-115">The following connection string example specifies a sample database on the local client:</span></span>  
  
```  
Data Source=<server>;Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="5fa30-116">如需連接字串範例的詳細資訊，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-116">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="5fa30-117">認證</span><span class="sxs-lookup"><span data-stu-id="5fa30-117">Credentials</span></span>  
 <span data-ttu-id="5fa30-118">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="5fa30-118">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="5fa30-119">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="5fa30-119">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="5fa30-120">報表撰寫用戶端提供下列可用來指定認證的選項：</span><span class="sxs-lookup"><span data-stu-id="5fa30-120">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="5fa30-121">目前的 Windows 使用者 (也稱為整合式安全性)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-121">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="5fa30-122">使用預存的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5fa30-122">Use a stored user name and password.</span></span>  
  
-   <span data-ttu-id="5fa30-123">提示使用者提供認證。</span><span class="sxs-lookup"><span data-stu-id="5fa30-123">Prompt the user for credentials.</span></span> <span data-ttu-id="5fa30-124">此選項只支援 Windows 整合式安全性。</span><span class="sxs-lookup"><span data-stu-id="5fa30-124">This option supports Windows integrated security only.</span></span>  
  
-   <span data-ttu-id="5fa30-125">不需要認證。</span><span class="sxs-lookup"><span data-stu-id="5fa30-125">No credentials are required.</span></span> <span data-ttu-id="5fa30-126">若要使用這個選項，您先前必須在報表伺服器上設定自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="5fa30-126">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="5fa30-127">如需詳細資訊，請參閱 msdn.microsoft.com 上 [Reporting Services 文件](https://go.microsoft.com/fwlink/?linkid=121312)中的[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-127">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="5fa30-128">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-128">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="5fa30-129">查詢</span><span class="sxs-lookup"><span data-stu-id="5fa30-129">Queries</span></span>  
 <span data-ttu-id="5fa30-130">查詢會指定要為報表資料集擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="5fa30-130">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="5fa30-131">查詢結果集中的資料行會填入資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="5fa30-131">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="5fa30-132">報表只會處理查詢擷取的第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-132">A report processes only the first result set that a query retrieves.</span></span>  
  
 <span data-ttu-id="5fa30-133">根據預設，如果您建立新查詢或開啟現有查詢，而查詢可在圖形化查詢設計工具中表示，就可使用關聯式查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="5fa30-133">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="5fa30-134">您可以利用下列方式指定查詢：</span><span class="sxs-lookup"><span data-stu-id="5fa30-134">You can specify a query in the following ways:</span></span>  
  
-   <span data-ttu-id="5fa30-135">以互動方式建立查詢。</span><span class="sxs-lookup"><span data-stu-id="5fa30-135">Build a query interactively.</span></span> <span data-ttu-id="5fa30-136">使用關聯式查詢設計工具，此工具會顯示資料表、檢視表、預存程序和其他資料庫項目的階層式檢視，並且依資料庫結構描述加以組織。</span><span class="sxs-lookup"><span data-stu-id="5fa30-136">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="5fa30-137">從資料表或檢視選取資料行，或者指定預存程序或資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="5fa30-137">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="5fa30-138">藉由指定篩選準則，限制要擷取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="5fa30-138">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="5fa30-139">藉由設定參數選項，在報表執行時自訂篩選器。</span><span class="sxs-lookup"><span data-stu-id="5fa30-139">Customize the filter when the report runs by setting the parameter option.</span></span>  
  
-   <span data-ttu-id="5fa30-140">輸入或貼上查詢。</span><span class="sxs-lookup"><span data-stu-id="5fa30-140">Type or paste a query.</span></span> <span data-ttu-id="5fa30-141">使用以文字為基礎的查詢設計工具直接輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文字、從另一個來源貼上查詢文字、輸入不能利用關聯式查詢設計工具建立的複雜查詢，或是輸入以查詢為基礎的運算式。</span><span class="sxs-lookup"><span data-stu-id="5fa30-141">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>  
  
-   <span data-ttu-id="5fa30-142">從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="5fa30-142">Import an existing query from a file or report.</span></span> <span data-ttu-id="5fa30-143">使用查詢設計工具的 **[匯入查詢]** 按鈕瀏覽至 .sql 檔案或 .rdl 檔案，然後匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="5fa30-143">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>  
  
 <span data-ttu-id="5fa30-144">如需詳細資訊，請參閱[關聯式查詢設計工具使用者介面 &#40;報表產生器&#41;](relational-query-designer-user-interface-report-builder.md) 和[以文字為基礎的查詢設計工具使用者介面 &#40;報表產生器&#41;](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-144">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="5fa30-145">以下為支援的查詢模式：</span><span class="sxs-lookup"><span data-stu-id="5fa30-145">The following query modes are supported:</span></span>  
  
-   <span data-ttu-id="5fa30-146">[文字](#QueryText) ：輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="5fa30-146">[Text](#QueryText) Type in [!INCLUDE[tsql](../../includes/tsql-md.md)] commands.</span></span>  
  
-   <span data-ttu-id="5fa30-147">[預存程序](#QueryStoredProcedure) ：從預存程序清單選擇。</span><span class="sxs-lookup"><span data-stu-id="5fa30-147">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>  
  
###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="5fa30-148">使用 Text 查詢類型</span><span class="sxs-lookup"><span data-stu-id="5fa30-148">Using Query Type Text</span></span>  
 <span data-ttu-id="5fa30-149">在以文字為基礎的查詢設計工具中，您可以輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令來定義資料集內的資料。</span><span class="sxs-lookup"><span data-stu-id="5fa30-149">In the text-based query designer, you can type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="5fa30-150">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢會選取所有行銷助理員工的名字：</span><span class="sxs-lookup"><span data-stu-id="5fa30-150">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 <span data-ttu-id="5fa30-151">按一下工具列上的 **[執行]** 按鈕 ( **!** ) 來執行查詢並顯示結果集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-151">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>  
  
 <span data-ttu-id="5fa30-152">若要將這個查詢參數化，請加入查詢參數。</span><span class="sxs-lookup"><span data-stu-id="5fa30-152">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="5fa30-153">例如，將 WHERE 子句變更為下列：</span><span class="sxs-lookup"><span data-stu-id="5fa30-153">For example, change the WHERE clause to the following:</span></span>  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 <span data-ttu-id="5fa30-154">當您執行查詢時，會自動建立與查詢參數對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="5fa30-154">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="5fa30-155">如需詳細資訊，請參閱本主題稍後的 [查詢參數](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="5fa30-155">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
  
###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a> <span data-ttu-id="5fa30-156">使用 StoredProcedure 查詢類型</span><span class="sxs-lookup"><span data-stu-id="5fa30-156">Using Query Type StoredProcedure</span></span>  
 <span data-ttu-id="5fa30-157">您可以用下列其中一種方式指定資料集查詢的預存程序：</span><span class="sxs-lookup"><span data-stu-id="5fa30-157">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>  
  
-   <span data-ttu-id="5fa30-158">在 **[資料集屬性]** 對話方塊中，設定 **[預存程序]** 選項。</span><span class="sxs-lookup"><span data-stu-id="5fa30-158">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="5fa30-159">從預存程序和資料表值函式的下拉式清單選擇。</span><span class="sxs-lookup"><span data-stu-id="5fa30-159">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>  
  
-   <span data-ttu-id="5fa30-160">在關聯式查詢設計工具的 [資料庫檢視] 窗格中，選取預存程序或資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="5fa30-160">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>  
  
-   <span data-ttu-id="5fa30-161">在以文字為基礎的查詢設計工具中，從工具列選取 **[StoredProcedure]** 。</span><span class="sxs-lookup"><span data-stu-id="5fa30-161">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>  
  
 <span data-ttu-id="5fa30-162">在選取預存程序或資料表值函式後，就可以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="5fa30-162">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="5fa30-163">系統會提示您輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="5fa30-163">You will be prompted for input parameter values.</span></span> <span data-ttu-id="5fa30-164">當您執行查詢時，會自動建立與輸入參數對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="5fa30-164">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="5fa30-165">如需詳細資訊，請參閱本主題稍後的 [查詢參數](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="5fa30-165">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
 <span data-ttu-id="5fa30-166">只支援預存程序所擷取的第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-166">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="5fa30-167">如果預存程序傳回多個結果集，只會使用第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-167">If a stored procedure returns multiple result sets, only the first one is used.</span></span>  
  
 <span data-ttu-id="5fa30-168">如果預存程序的參數有預設值，可以使用 DEFAULT 關鍵字做為參數值來存取該值。</span><span class="sxs-lookup"><span data-stu-id="5fa30-168">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="5fa30-169">如果查詢參數連結到報表參數，使用者可以在報表參數的輸入方塊中輸入或選取 DEFAULT 一字。</span><span class="sxs-lookup"><span data-stu-id="5fa30-169">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>  
  
 <span data-ttu-id="5fa30-170">如需詳細資訊，請參閱 msdn.microsoft.com 上 [SQL Server 線上叢書](https://go.microsoft.com/fwlink/?linkid=98335) 中的＜預存程序 (資料庫引擎)＞。</span><span class="sxs-lookup"><span data-stu-id="5fa30-170">For more information, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="5fa30-171">參數</span><span class="sxs-lookup"><span data-stu-id="5fa30-171">Parameters</span></span>  
 <span data-ttu-id="5fa30-172">當查詢文字包含具有輸入參數的查詢變數或預存程序時，會自動產生資料集的對應查詢參數和報表的報表參數。</span><span class="sxs-lookup"><span data-stu-id="5fa30-172">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="5fa30-173">查詢文字的查詢變數不能包含 DECLARE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5fa30-173">The query text must not include the DECLARE statement for each query variable.</span></span>  
  
 <span data-ttu-id="5fa30-174">例如，下列 SQL 查詢會建立名為 `EmpID` 的報表參數：</span><span class="sxs-lookup"><span data-stu-id="5fa30-174">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 <span data-ttu-id="5fa30-175">報表參數是透過預設屬性值建立，您可能會需要修改這些值。</span><span class="sxs-lookup"><span data-stu-id="5fa30-175">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="5fa30-176">例如：</span><span class="sxs-lookup"><span data-stu-id="5fa30-176">For example:</span></span>  
  
-   <span data-ttu-id="5fa30-177">根據預設，每一個報表參數的資料類型都是 **[文字]** 。</span><span class="sxs-lookup"><span data-stu-id="5fa30-177">By default, each report parameter is data type **Text**.</span></span> <span data-ttu-id="5fa30-178">如果基礎資料是不同的資料類型，則必須變更參數資料類型。</span><span class="sxs-lookup"><span data-stu-id="5fa30-178">If the underlying data is a different data type, you must change the parameter data type.</span></span>  
  
-   <span data-ttu-id="5fa30-179">如果您為多值參數選取此選項，則必須使用 `IN` 運算子手動變更查詢，測試值是否為集合的一部分，例如 `WHERE EmployeeID IN (@EmpID)`。</span><span class="sxs-lookup"><span data-stu-id="5fa30-179">If you select the option for multivalued parameters, you must manually change the query to test whether values are part of a set by using the `IN` operator, for example, `WHERE EmployeeID IN (@EmpID)`.</span></span>  
  
 <span data-ttu-id="5fa30-180">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="5fa30-180">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="5fa30-181">備註</span><span class="sxs-lookup"><span data-stu-id="5fa30-181">Remarks</span></span>  
 <span data-ttu-id="5fa30-182">您也可以使用 OLE DB 或 ODBC 資料來源類型，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫擷取資料。</span><span class="sxs-lookup"><span data-stu-id="5fa30-182">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an OLE DB or ODBC data source type.</span></span> <span data-ttu-id="5fa30-183">如需詳細資訊，請參閱 [OLE DB 連線類型 &#40;SSRS&#41;](ole-db-connection-type-ssrs.md) 或 [ODBC 連線類型 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-183">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md) or [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="5fa30-184">平台和版本資訊</span><span class="sxs-lookup"><span data-stu-id="5fa30-184">Platform and Version Information</span></span>  
 <span data-ttu-id="5fa30-185">如需平台和版本支援的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ 線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-185">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="5fa30-186">如何主題</span><span class="sxs-lookup"><span data-stu-id="5fa30-186">How-To Topics</span></span>  
 <span data-ttu-id="5fa30-187">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="5fa30-187">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="5fa30-188">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-188">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5fa30-189">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-189">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="5fa30-190">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-190">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="5fa30-191">相關章節</span><span class="sxs-lookup"><span data-stu-id="5fa30-191">Related Sections</span></span>  
 <span data-ttu-id="5fa30-192">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="5fa30-192">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="5fa30-193">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-193">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="5fa30-194">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="5fa30-194">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="5fa30-195">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="5fa30-195">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="5fa30-196">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5fa30-196">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="5fa30-197">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-197">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="5fa30-198">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5fa30-198">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="5fa30-199">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-199">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="5fa30-200">提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5fa30-200">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="5fa30-201">《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="5fa30-201">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="5fa30-202">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="5fa30-202">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="5fa30-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fa30-203">See Also</span></span>  
 <span data-ttu-id="5fa30-204">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="5fa30-204">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="5fa30-205">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5fa30-205">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5fa30-206">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5fa30-206">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
