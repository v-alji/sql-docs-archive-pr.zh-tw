---
title: ADO NET 目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78851d5bbad18d2d1076eaa87200dd73e6962a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584697"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a><span data-ttu-id="c2801-102">ADO NET 目的地編輯器 (連線管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="c2801-102">ADO NET Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="c2801-103">使用 [ADO NET 目的地編輯器]  對話方塊的 [連線管理員]  頁面，即可選取目的地的 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 連線。</span><span class="sxs-lookup"><span data-stu-id="c2801-103">Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection for the destination.</span></span> <span data-ttu-id="c2801-104">這個頁面也可以讓您從資料庫中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="c2801-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="c2801-105">若要深入了解 ADO NET 目的地，請參閱＜ [ADO NET Destination](data-flow/ado-net-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c2801-105">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="c2801-106">**開啟連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="c2801-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="c2801-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 目的地的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="c2801-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="c2801-108">在 [資料流程]  索引標籤中，按兩下 ADO NET 目的地。</span><span class="sxs-lookup"><span data-stu-id="c2801-108">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="c2801-109">在 [ADO NET 目的地編輯器]  中，按一下 [連線管理員]  。</span><span class="sxs-lookup"><span data-stu-id="c2801-109">In the **ADO NET Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="c2801-110">靜態選項</span><span class="sxs-lookup"><span data-stu-id="c2801-110">Static Options</span></span>  
 <span data-ttu-id="c2801-111">**[ODBC 目的地編輯器]**</span><span class="sxs-lookup"><span data-stu-id="c2801-111">**Connection manager**</span></span>  
 <span data-ttu-id="c2801-112">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="c2801-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="c2801-113">**新增**</span><span class="sxs-lookup"><span data-stu-id="c2801-113">**New**</span></span>  
 <span data-ttu-id="c2801-114">使用 [設定 ADO.NET 連線管理員]  對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c2801-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="c2801-115">**使用資料表或檢視**</span><span class="sxs-lookup"><span data-stu-id="c2801-115">**Use a table or view**</span></span>  
 <span data-ttu-id="c2801-116">從清單中選取現有的資料表或檢視，或按一下 [新增]  來建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="c2801-116">Select an existing table or view from the list, or create a new table by clicking **New**..</span></span>  
  
 <span data-ttu-id="c2801-117">**新增**</span><span class="sxs-lookup"><span data-stu-id="c2801-117">**New**</span></span>  
 <span data-ttu-id="c2801-118">使用 [建立資料表]  對話方塊來建立新的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="c2801-118">Create a new table or view by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2801-119">當您按一下 **[新增]** 時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2801-119">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="c2801-120">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="c2801-120">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="c2801-121">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="c2801-121">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="c2801-122">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2801-122">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="c2801-123">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c2801-123">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="c2801-124">**預覽**</span><span class="sxs-lookup"><span data-stu-id="c2801-124">**Preview**</span></span>  
 <span data-ttu-id="c2801-125">使用 [預覽查詢結果]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="c2801-125">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="c2801-126">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="c2801-126">Preview can display up to 200 rows.</span></span>  
  
 <span data-ttu-id="c2801-127">**在可用時使用大量插入**</span><span class="sxs-lookup"><span data-stu-id="c2801-127">**Use bulk insert when available**</span></span>  
 <span data-ttu-id="c2801-128">指定是否要使用 <xref:System.Data.SqlClient.SqlBulkCopy> 介面來改善大量插入作業的效能。</span><span class="sxs-lookup"><span data-stu-id="c2801-128">Specify whether to use the <xref:System.Data.SqlClient.SqlBulkCopy> interface to improve the performance of bulk insert operations.</span></span>  
  
 <span data-ttu-id="c2801-129">只有傳回 <xref:System.Data.SqlClient.SqlConnection> 物件的 ADO.NET 提供者才支援使用 <xref:System.Data.SqlClient.SqlBulkCopy> 介面。</span><span class="sxs-lookup"><span data-stu-id="c2801-129">Only ADO.NET providers that return a <xref:System.Data.SqlClient.SqlConnection> object support the use of the <xref:System.Data.SqlClient.SqlBulkCopy> interface.</span></span> <span data-ttu-id="c2801-130">.NET Data Provider for SQL Server (SqlClient) 會傳回 <xref:System.Data.SqlClient.SqlConnection> 物件，而自訂提供者則可能傳回 <xref:System.Data.SqlClient.SqlConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="c2801-130">The .NET Data Provider for SQL Server (SqlClient) returns a <xref:System.Data.SqlClient.SqlConnection> object, and a custom provider may return a <xref:System.Data.SqlClient.SqlConnection> object.</span></span>  
  
 <span data-ttu-id="c2801-131">您可以使用 .NET Data Provider for SQL Server (SqlClient) 連接到 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2801-131">You can use the .NET Data Provider for SQL Server (SqlClient) to connect to [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span>  
  
 <span data-ttu-id="c2801-132">如果您選取 [盡可能使用大量插入]  ，並將 [錯誤]  選項設定為 [重新導向資料列]  ，目的地重新導向至錯誤輸出的資料批次可能會包含良好的資料列。如需處理大量作業中錯誤的詳細資訊，請參閱[處理資料中的錯誤](data-flow/error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c2801-132">If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span> <span data-ttu-id="c2801-133">如需 [錯誤]  選項的詳細資訊，請參閱 [ADO NET 目的地編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c2801-133">For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2801-134">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 Sybase 來源資料表包含識別欄位，您就必須使用「執行 SQL」工作，在 ADO NET 目的地前後執行 SET IDENTITY_INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2801-134">If a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY_INSERT statement before and after the ADO NET destination.</span></span> <span data-ttu-id="c2801-135">識別欄位屬性會指定資料行的累加值。</span><span class="sxs-lookup"><span data-stu-id="c2801-135">The identity column property specifies an incremental value for the column.</span></span> <span data-ttu-id="c2801-136">SET IDENTITY_INSERT 陳述式可讓明確值插入識別欄位中。</span><span class="sxs-lookup"><span data-stu-id="c2801-136">The SET IDENTITY_INSERT statement enables explicit values to be inserted into the identity column.</span></span> <span data-ttu-id="c2801-137">若要在相同的資料庫連接上執行 CREATE TABLE 和 SET IDENTITY 陳述式，請將 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 連接管理員的 `RetainSameConnection` 屬性設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="c2801-137">To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the `RetainSameConnection` property of the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager to `True`.</span></span> <span data-ttu-id="c2801-138">此外，您可以針對「執行 SQL」工作和 ADO NET 目的地使用相同的 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c2801-138">Also, use the same [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.</span></span>  
>   
>  <span data-ttu-id="c2801-139">如需詳細資訊，請參閱 [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) 和 [IDENTITY &#40;屬性&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property)。</span><span class="sxs-lookup"><span data-stu-id="c2801-139">For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="c2801-140">外部資源</span><span class="sxs-lookup"><span data-stu-id="c2801-140">External Resources</span></span>  
 <span data-ttu-id="c2801-141">sqlcat.com 上的技術文件：[快速將資料載入 Azure SQL Database 的方式](https://go.microsoft.com/fwlink/?LinkId=244333) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="c2801-141">Technical article, [Loading data to Azure SQL Database the fast way](https://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2801-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2801-142">See Also</span></span>  
 <span data-ttu-id="c2801-143">[ADO NET 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="c2801-143">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="c2801-144">[ADO NET 目的地編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="c2801-144">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="c2801-145">[ADO.NET 連線管理員](connection-manager/ado-net-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c2801-145">[ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md) </span></span>  
 [<span data-ttu-id="c2801-146">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="c2801-146">Execute SQL Task</span></span>](control-flow/execute-sql-task.md)  
  
  
