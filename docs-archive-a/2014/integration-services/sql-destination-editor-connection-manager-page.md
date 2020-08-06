---
title: SQL 目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f3a552968cb297de337e1f0c406b444d95dc5a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594596"
---
# <a name="sql-destination-editor-connection-manager-page"></a><span data-ttu-id="e25ed-102">SQL 目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="e25ed-102">SQL Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="e25ed-103">使用 **[SQL 目的地編輯器]** 對話方塊的 **[連接管理員]** 頁面，即可指定資料來源資訊並預覽結果。</span><span class="sxs-lookup"><span data-stu-id="e25ed-103">Use the **Connection Manager** page of the **SQL Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="e25ed-104">目的地會將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料載入資料庫中的資料表或 views [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e25ed-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination loads data into tables or views in a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="e25ed-105">若要深入了解 SQL Server 目的地，請參閱＜ [SQL Server Destination](data-flow/sql-server-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e25ed-105">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e25ed-106">選項。</span><span class="sxs-lookup"><span data-stu-id="e25ed-106">Options</span></span>  
 <span data-ttu-id="e25ed-107">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="e25ed-107">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="e25ed-108">從清單中選取現有的連接，或按一下 [新增]\*\*\*\* 來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="e25ed-108">Select an existing connection from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e25ed-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="e25ed-109">**New**</span></span>  
 <span data-ttu-id="e25ed-110">使用 [設定 OLE DB 連接管理員]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="e25ed-110">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="e25ed-111">**使用資料表或檢視**</span><span class="sxs-lookup"><span data-stu-id="e25ed-111">**Use a table or view**</span></span>  
 <span data-ttu-id="e25ed-112">從清單中選取現有的資料表或檢視，或按一下 [新增]\*\*\*\* 來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="e25ed-112">Select an existing table or view from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e25ed-113">**新增**</span><span class="sxs-lookup"><span data-stu-id="e25ed-113">**New**</span></span>  
 <span data-ttu-id="e25ed-114">使用 [建立資料表]  對話方塊建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="e25ed-114">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e25ed-115">當您按一下 **[新增]** 時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e25ed-115">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="e25ed-116">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="e25ed-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="e25ed-117">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="e25ed-117">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="e25ed-118">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e25ed-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="e25ed-119">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e25ed-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="e25ed-120">**預覽**</span><span class="sxs-lookup"><span data-stu-id="e25ed-120">**Preview**</span></span>  
 <span data-ttu-id="e25ed-121">使用 [預覽查詢結果]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="e25ed-121">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="e25ed-122">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="e25ed-122">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25ed-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e25ed-123">See Also</span></span>  
 <span data-ttu-id="e25ed-124">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e25ed-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e25ed-125">[[SQL 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="e25ed-125">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="e25ed-126">[[SQL 目的地編輯器] &#40;[Advanced] 頁面&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="e25ed-126">[SQL Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="e25ed-127">使用 SQL Server 目的地來大量載入資料</span><span class="sxs-lookup"><span data-stu-id="e25ed-127">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
