---
title: SQL Azure 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c84def6c-e8cf-43d9-9912-098171a7ce79
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2c3d3e75117996f088cff96b2b7a8d4cd504127
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598233"
---
# <a name="sql-azure-connection-type-ssrs"></a><span data-ttu-id="dcb28-102">SQL Azure 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="dcb28-102">SQL Azure Connection Type (SSRS)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="dcb28-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]是以技術為基礎的雲端託管關係資料庫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dcb28-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] is a cloud-based, hosted relational database built on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies.</span></span> <span data-ttu-id="dcb28-104">若要在報表中包含來自 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的資料，您必須具有以 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-104">To include data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span> <span data-ttu-id="dcb28-105">此內建資料來源類型是以 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 資料延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="dcb28-105">This built-in data source type is based on the [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data extension.</span></span> <span data-ttu-id="dcb28-106">使用此資料來源類型可連接至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]並從中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="dcb28-106">Use this data source type to connect to and retrieve data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="dcb28-107">此資料延伸模組支援多值參數、伺服器彙總，以及與連接字串分開管理的認證。</span><span class="sxs-lookup"><span data-stu-id="dcb28-107">This data extension supports multivalued parameters, server aggregates, and credentials managed separately from the connection string.</span></span>

 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="dcb28-108">類似於內部部署的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，而從 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 取得資料的方式與從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]取得資料的方式相同，只有少數例外。</span><span class="sxs-lookup"><span data-stu-id="dcb28-108">is similar to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your premises and getting data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] is, with a few exceptions, identical to getting data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="dcb28-109">當開啟 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]的連接時，請將連接逾時設定為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="dcb28-109">When opening a connection to a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], set the connection timeout to 30 seconds.</span></span>

 <span data-ttu-id="dcb28-110">如需詳細資訊，請參閱 [Azure SQL Database 檔](https://docs.microsoft.com/azure/sql-database/)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-110">For more information, see [Azure SQL Database Documentation](https://docs.microsoft.com/azure/sql-database/).</span></span>

 <span data-ttu-id="dcb28-111">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="dcb28-111">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="dcb28-112">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-112">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>

##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="dcb28-113">連接字串</span><span class="sxs-lookup"><span data-stu-id="dcb28-113">Connection String</span></span>
 <span data-ttu-id="dcb28-114">當您連接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]時，是連接到雲端的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="dcb28-114">When you connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you are connecting to a database object in the cloud.</span></span> <span data-ttu-id="dcb28-115">就像現場的資料庫一般，主控資料庫可能有包含多個資料表、檢視和預存程序的多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="dcb28-115">Just like onsite databases, the hosted database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="dcb28-116">您會指定在查詢設計工具中使用的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="dcb28-116">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="dcb28-117">如果您未在連接字串中指定資料庫，則會連接到管理員指派給您的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcb28-117">If you do not specify a database in the connection string, you connect to the default database that the administrator assigned to you.</span></span>

 <span data-ttu-id="dcb28-118">請洽詢資料庫管理員，以取得用來連接資料來源的連接資訊和認證。</span><span class="sxs-lookup"><span data-stu-id="dcb28-118">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="dcb28-119">下列連接字串範例會指定名為 AdventureWorks 的主控範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcb28-119">The following connection string example specifies a hosted sample database named AdventureWorks.</span></span>

```
Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True;
```

 <span data-ttu-id="dcb28-120">此外，您會使用 **[資料來源屬性]** 對話方塊提供認證，例如使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="dcb28-120">In addition, you use the **Data Sources Properties** dialog box to provide credentials such as user name and password.</span></span> <span data-ttu-id="dcb28-121">`User Id` 和 `Password` 選項會自動附加至連接字串；您不需要隨連接字串輸入這些選項。</span><span class="sxs-lookup"><span data-stu-id="dcb28-121">The `User Id` and `Password` options are automatically appended to the connection string; you do not need to type them as part of the connection string.</span></span>

 <span data-ttu-id="dcb28-122">如需連接字串範例的詳細資訊，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-122">For more information and connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>

##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="dcb28-123">認證</span><span class="sxs-lookup"><span data-stu-id="dcb28-123">Credentials</span></span>
 <span data-ttu-id="dcb28-124">不支援 Windows 驗證 (整合式安全性)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-124">Windows Authentication (integrated security) is not supported.</span></span> <span data-ttu-id="dcb28-125">如果您嘗試使用 Windows 驗證連接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcb28-125">If you attempt to connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] using Windows Authentication an error occurs.</span></span> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="dcb28-126">僅支援 SQL Server 驗證 (使用者名稱和密碼)，而且使用者必須在每次連接至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]時提供認證 (登入和密碼)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-126">supports only SQL Server Authentication (user name and password) and users must provide credentials (login and password) every time they connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="dcb28-127">您必須有足夠的認證才能存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcb28-127">Credentials must be sufficient to access the database.</span></span> <span data-ttu-id="dcb28-128">根據查詢而定，您可能還需要其他權限，例如執行預存程序和存取資料表和檢視的足夠權限。</span><span class="sxs-lookup"><span data-stu-id="dcb28-128">Depending on your query, you might need other permissions, such as sufficient permissions to run stored procedures and access tables and views.</span></span> <span data-ttu-id="dcb28-129">外部資料來源的擁有者必須設定認證，而這些認證必須足以提供您所需資料庫物件的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="dcb28-129">The owner of the external data source must configure credentials that are sufficient to provide read-only access to the database objects that you need.</span></span>

 <span data-ttu-id="dcb28-130">報表撰寫用戶端提供下列可用來指定認證的選項：</span><span class="sxs-lookup"><span data-stu-id="dcb28-130">From a report authoring client, the following options are available to specify credentials:</span></span>

-   <span data-ttu-id="dcb28-131">使用預存的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="dcb28-131">Use a stored user name and password.</span></span> <span data-ttu-id="dcb28-132">為了交涉在資料庫包含的報表資料不同於報表伺服器時發生的雙躍點，請選取使用認證做為 Windows 認證的選項。</span><span class="sxs-lookup"><span data-stu-id="dcb28-132">To negotiate the double hop that occurs when the database that contains the report data is different than the report server, select options to use credentials as Windows credentials.</span></span> <span data-ttu-id="dcb28-133">您也可以選擇在連接到資料來源之後模擬已驗證的使用者。</span><span class="sxs-lookup"><span data-stu-id="dcb28-133">You can also chose to impersonate the authenticated user after connecting to the data source.</span></span>

-   <span data-ttu-id="dcb28-134">不需要認證。</span><span class="sxs-lookup"><span data-stu-id="dcb28-134">No credentials are required.</span></span> <span data-ttu-id="dcb28-135">若要使用這個選項，您先前必須在報表伺服器上設定自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="dcb28-135">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="dcb28-136">如需詳細資訊，請參閱 msdn.microsoft.com 上 [Reporting Services 文件](https://go.microsoft.com/fwlink/?linkid=121312)中的[設定自動執行帳戶 &#40;SSRS 設定管理員&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-136">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>

 <span data-ttu-id="dcb28-137">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-137">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>

 

##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="dcb28-138">查詢</span><span class="sxs-lookup"><span data-stu-id="dcb28-138">Queries</span></span>
 <span data-ttu-id="dcb28-139">查詢會指定要為報表資料集擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="dcb28-139">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="dcb28-140">查詢結果集中的資料行會填入資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="dcb28-140">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="dcb28-141">如果查詢傳回多個結果集，報表只會處理查詢擷取的第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-141">If the query returns multiple result sets, the report processes only the first result set that the query retrieves.</span></span> <span data-ttu-id="dcb28-142">雖然 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]之間有些許差異 (例如支援的資料庫大小)，但是依據 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]撰寫查詢的方式類似於依據 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫撰寫查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-142">Although there are some differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s such as the sizes of databases supported, writing queries against [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s is similar to writing queries against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="dcb28-143">[!INCLUDE[tsql](../../includes/tsql-md.md)] 中不支援部分 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]陳述式 (例如 BACKUP)，但是這些不是您在報表查詢中使用的陳述式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-143">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements such as BACKUP are not supported in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], but they are not ones that you use in report queries.</span></span> <span data-ttu-id="dcb28-144">如需詳細資訊，請參閱 [SQL Server 連接類型 &#40;SSRS&#41;](sql-server-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-144">For more information, see [SQL Server Connection Type &#40;SSRS&#41;](sql-server-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="dcb28-145">根據預設，如果您建立新查詢或開啟現有查詢，而查詢可在圖形化查詢設計工具中表示，就可使用關聯式查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="dcb28-145">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="dcb28-146">您可以利用下列方式指定查詢：</span><span class="sxs-lookup"><span data-stu-id="dcb28-146">You can specify a query in the following ways:</span></span>

-   <span data-ttu-id="dcb28-147">以互動方式建立查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-147">Build a query interactively.</span></span> <span data-ttu-id="dcb28-148">使用關聯式查詢設計工具，此工具會顯示資料表、檢視表、預存程序和其他資料庫項目的階層式檢視，並且依資料庫結構描述加以組織。</span><span class="sxs-lookup"><span data-stu-id="dcb28-148">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="dcb28-149">從資料表或檢視選取資料行，或者指定預存程序或資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-149">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="dcb28-150">藉由指定篩選準則，限制要擷取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="dcb28-150">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="dcb28-151">藉由設定參數選項，在報表執行時自訂篩選器。</span><span class="sxs-lookup"><span data-stu-id="dcb28-151">Customize the filter when the report runs by setting the parameter option.</span></span>

-   <span data-ttu-id="dcb28-152">輸入或貼上查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-152">Type or paste a query.</span></span> <span data-ttu-id="dcb28-153">使用以文字為基礎的查詢設計工具直接輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文字、從另一個來源貼上查詢文字、輸入不能利用關聯式查詢設計工具建立的複雜查詢，或是輸入以查詢為基礎的運算式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-153">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>

-   <span data-ttu-id="dcb28-154">從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-154">Import an existing query from a file or report.</span></span> <span data-ttu-id="dcb28-155">使用查詢設計工具的 **[匯入查詢]** 按鈕瀏覽至 .sql 檔案或 .rdl 檔案，然後匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-155">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>

 <span data-ttu-id="dcb28-156">以文字為基礎的查詢設計工具支援以下兩種模式：</span><span class="sxs-lookup"><span data-stu-id="dcb28-156">The text-based query designer supports the following two modes:</span></span>

-   <span data-ttu-id="dcb28-157">[文字](#QueryText) ：輸入從資料來源選取資料的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="dcb28-157">[Text](#QueryText) Type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands that select data from the data source.</span></span>

-   <span data-ttu-id="dcb28-158">[預存程序](#QueryStoredProcedure) ：從預存程序清單選擇。</span><span class="sxs-lookup"><span data-stu-id="dcb28-158">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>

 <span data-ttu-id="dcb28-159">如需詳細資訊，請參閱[關聯式查詢設計工具使用者介面 &#40;報表產生器&#41;](relational-query-designer-user-interface-report-builder.md) 和[以文字為基礎的查詢設計工具使用者介面 &#40;報表產生器&#41;](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-159">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>

 <span data-ttu-id="dcb28-160">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 使用的圖形化查詢設計工具會為群組和彙總提供內建的支援，幫助您撰寫僅擷取摘要資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-160">The graphical query designer that [!INCLUDE[ssSDS](../../includes/sssds-md.md)] uses provides built-in support for grouping and aggregates to help you write queries that retrieve only summary data.</span></span> <span data-ttu-id="dcb28-161">[!INCLUDE[tsql](../../includes/tsql-md.md)] 語言功能包括 GROUP BY 子句、DISTINCT 關鍵字以及如 SUM 和 COUNT 等彙總。</span><span class="sxs-lookup"><span data-stu-id="dcb28-161">The [!INCLUDE[tsql](../../includes/tsql-md.md)] language features are: the GROUP BY clause, DISTINCT keyword, and aggregates such as SUM and COUNT.</span></span> <span data-ttu-id="dcb28-162">以文字為基礎的查詢設計工具提供 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語言的完整支援，包括群組和彙總。</span><span class="sxs-lookup"><span data-stu-id="dcb28-162">The text-based query designer provides full support for the [!INCLUDE[tsql](../../includes/tsql-md.md)] language, including grouping and aggregates.</span></span> <span data-ttu-id="dcb28-163">如需 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的詳細資訊，請參閱 msdn.microsoft.com 上《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?LinkId=141687)中的 [Transact-SQL 參考 &#40;資料庫引擎&#41;](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-163">For more information about [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=141687) on msdn.microsoft.com.</span></span>

###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="dcb28-164">使用 Text 查詢類型</span><span class="sxs-lookup"><span data-stu-id="dcb28-164">Using Query Type Text</span></span>
 <span data-ttu-id="dcb28-165">在以文字為基礎的查詢設計工具中，您可以輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令來定義資料集內的資料。</span><span class="sxs-lookup"><span data-stu-id="dcb28-165">In the text-based query designer, you type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="dcb28-166">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢會選取所有行銷助理員工的名字：</span><span class="sxs-lookup"><span data-stu-id="dcb28-166">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>

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

 <span data-ttu-id="dcb28-167">按一下工具列上的 **[執行]** 按鈕 ( **!** ) 來執行查詢並顯示結果集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-167">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>

 <span data-ttu-id="dcb28-168">若要將這個查詢參數化，請加入查詢參數。</span><span class="sxs-lookup"><span data-stu-id="dcb28-168">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="dcb28-169">例如，將 WHERE 子句變更為下列：</span><span class="sxs-lookup"><span data-stu-id="dcb28-169">For example, change the WHERE clause to the following:</span></span>

```
WHERE HumanResources.Employee.JobTitle = (@JobTitle)
```

 <span data-ttu-id="dcb28-170">當您執行查詢時，會自動建立與查詢參數對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="dcb28-170">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="dcb28-171">如需詳細資訊，請參閱本主題稍後的 [查詢參數](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="dcb28-171">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>



###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a> <span data-ttu-id="dcb28-172">使用 StoredProcedure 查詢類型</span><span class="sxs-lookup"><span data-stu-id="dcb28-172">Using Query Type StoredProcedure</span></span>
 <span data-ttu-id="dcb28-173">您可以用下列其中一種方式指定資料集查詢的預存程序：</span><span class="sxs-lookup"><span data-stu-id="dcb28-173">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>

-   <span data-ttu-id="dcb28-174">在 **[資料集屬性]** 對話方塊中，設定 **[預存程序]** 選項。</span><span class="sxs-lookup"><span data-stu-id="dcb28-174">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="dcb28-175">從預存程序和資料表值函式的下拉式清單選擇。</span><span class="sxs-lookup"><span data-stu-id="dcb28-175">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>

-   <span data-ttu-id="dcb28-176">在關聯式查詢設計工具的 [資料庫檢視] 窗格中，選取預存程序或資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-176">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>

-   <span data-ttu-id="dcb28-177">在以文字為基礎的查詢設計工具中，從工具列選取 **[StoredProcedure]** 。</span><span class="sxs-lookup"><span data-stu-id="dcb28-177">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>

 <span data-ttu-id="dcb28-178">在選取預存程序或資料表值函式後，就可以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="dcb28-178">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="dcb28-179">系統會提示您輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="dcb28-179">You will be prompted for input parameter values.</span></span> <span data-ttu-id="dcb28-180">當您執行查詢時，會自動建立與輸入參數對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="dcb28-180">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="dcb28-181">如需詳細資訊，請參閱本主題稍後的 [查詢參數](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="dcb28-181">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>

 <span data-ttu-id="dcb28-182">只支援預存程序所擷取的第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-182">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="dcb28-183">如果預存程序傳回多個結果集，只會使用第一個結果集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-183">If a stored procedure returns multiple result sets, only the first one is used.</span></span>

 <span data-ttu-id="dcb28-184">如果預存程序的參數有預設值，可以使用 DEFAULT 關鍵字做為參數值來存取該值。</span><span class="sxs-lookup"><span data-stu-id="dcb28-184">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="dcb28-185">如果查詢參數連結到報表參數，使用者可以在報表參數的輸入方塊中輸入或選取 DEFAULT 一字。</span><span class="sxs-lookup"><span data-stu-id="dcb28-185">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>

 <span data-ttu-id="dcb28-186">如需預存程序的詳細資訊，請參閱 msdn.microsoft.com 上《 [SQL Server 線上叢書》](https://go.microsoft.com/fwlink/?linkid=98335) 中的＜預存程序 (資料庫引擎)＞。</span><span class="sxs-lookup"><span data-stu-id="dcb28-186">For more information about stored procedures, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>



##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="dcb28-187">參數</span><span class="sxs-lookup"><span data-stu-id="dcb28-187">Parameters</span></span>
 <span data-ttu-id="dcb28-188">當查詢文字包含具有輸入參數的查詢變數或預存程序時，會自動產生資料集的對應查詢參數和報表的報表參數。</span><span class="sxs-lookup"><span data-stu-id="dcb28-188">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="dcb28-189">查詢文字的查詢變數不能包含 DECLARE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dcb28-189">The query text must not include the DECLARE statement for each query variable.</span></span>

 <span data-ttu-id="dcb28-190">例如，下列 SQL 查詢會建立名為 `EmpID` 的報表參數：</span><span class="sxs-lookup"><span data-stu-id="dcb28-190">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>

```
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN
       Person.Contact C ON  E.ContactID=C.ContactID 
WHERE EmployeeID = (@EmpID)
```

 <span data-ttu-id="dcb28-191">根據預設，每個報表參數的資料類型為 Text，並具有自動建立的資料集，以提供可用值的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="dcb28-191">By default, each report parameter has data type Text and an automatically created dataset to provide a drop-down list of available values.</span></span> <span data-ttu-id="dcb28-192">建立報表參數後，您可能必須變更預設值。</span><span class="sxs-lookup"><span data-stu-id="dcb28-192">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="dcb28-193">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="dcb28-193">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>



##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="dcb28-194">備註</span><span class="sxs-lookup"><span data-stu-id="dcb28-194">Remarks</span></span>

###### <a name="alternate-data-extensions"></a><span data-ttu-id="dcb28-195">替代資料延伸模組</span><span class="sxs-lookup"><span data-stu-id="dcb28-195">Alternate Data Extensions</span></span>
 <span data-ttu-id="dcb28-196">您也可以使用 ODBC 資料來源類型，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫擷取資料。</span><span class="sxs-lookup"><span data-stu-id="dcb28-196">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an ODBC data source type.</span></span> <span data-ttu-id="dcb28-197">不過，不支援使用 OLE DB 連接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dcb28-197">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span>

 <span data-ttu-id="dcb28-198">如需詳細資訊，請參閱 [ODBC 連線類型 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-198">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>

###### <a name="platform-and-version-information"></a><span data-ttu-id="dcb28-199">平台和版本資訊</span><span class="sxs-lookup"><span data-stu-id="dcb28-199">Platform and Version Information</span></span>
 <span data-ttu-id="dcb28-200">如需平台和版本支援的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ 線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services &#40;SSRS&#41; 支援的資料來源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-200">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>



##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="dcb28-201">如何主題</span><span class="sxs-lookup"><span data-stu-id="dcb28-201">How-To Topics</span></span>
 <span data-ttu-id="dcb28-202">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="dcb28-202">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>

 [<span data-ttu-id="dcb28-203">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb28-203">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)

 [<span data-ttu-id="dcb28-204">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb28-204">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)

 [<span data-ttu-id="dcb28-205">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb28-205">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)



##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="dcb28-206">相關章節</span><span class="sxs-lookup"><span data-stu-id="dcb28-206">Related Sections</span></span>
 <span data-ttu-id="dcb28-207">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="dcb28-207">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>

 <span data-ttu-id="dcb28-208">[將資料加入至報表 &#40;Report Builder 和 SSRS&#41;](report-datasets-ssrs.md) 提供存取報表資料的總覽。</span><span class="sxs-lookup"><span data-stu-id="dcb28-208">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) Provides an overview of accessing data for your report.</span></span>

 <span data-ttu-id="dcb28-209">[Report Builder 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md) 提供資料連線和資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dcb28-209">[Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) Provides information about data connections and data sources.</span></span>

 <span data-ttu-id="dcb28-210">[報表內嵌資料集和共用資料集 &#40;Report Builder 和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) 提供內嵌和共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dcb28-210">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) Provides information about embedded and shared datasets.</span></span>

 <span data-ttu-id="dcb28-211">[資料集欄位集合 &#40;Report Builder 和 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) 提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dcb28-211">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) Provides information about the dataset field collection generated by the query.</span></span>

 <span data-ttu-id="dcb28-212">《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文件的 [Reporting Services 支援的資料來源 &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb28-212">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>
<span data-ttu-id="dcb28-213">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="dcb28-213">Provides in-depth information about platform and version support for each data extension.</span></span>



## <a name="see-also"></a><span data-ttu-id="dcb28-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcb28-214">See Also</span></span>
 <span data-ttu-id="dcb28-215">[報表參數 &#40;Report Builder 和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [篩選、分組和排序資料 &#40;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) Report Builder 和 ssrs&#41;運算式 &#40;Report Builder[和 ssrs](../report-design/expressions-report-builder-and-ssrs.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb28-215">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)</span></span>


