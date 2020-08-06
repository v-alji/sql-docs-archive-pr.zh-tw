---
title: 連結的伺服器 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB, linked servers
- OLE DB provider, linked servers
- server management [SQL Server], linked servers
- linked servers [SQL Server]
- distributed queries [SQL Server], linked servers
- servers [SQL Server], linked
- remote servers [SQL Server], linked servers
- linked servers [SQL Server], about linked servers
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1de70882cdeb87ccc0ae42aa23a9b6c8b3248e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585382"
---
# <a name="linked-servers-database-engine"></a><span data-ttu-id="a4bd0-102">連結的伺服器 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="a4bd0-102">Linked Servers (Database Engine)</span></span>
  <span data-ttu-id="a4bd0-103">設定連結的伺服器，可讓 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體外部的 OLE DB 資料來源執行命令。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-103">Configure a linked server to enable the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to execute commands against OLE DB data sources outside of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4bd0-104">一般會將連結的伺服器設定為可讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，而此陳述式包含另一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體中的資料表或另一個資料庫產品 (例如 Oracle) 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-104">Typically linked servers are configured to enable the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that includes tables in another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or another database product such as Oracle.</span></span> <span data-ttu-id="a4bd0-105">多種 OLE DB 資料來源類型可設定為連結的伺服器，包含 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access 和 Excel。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-105">Many types OLE DB data sources can be configured as linked servers, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access and Excel.</span></span> <span data-ttu-id="a4bd0-106">連結伺服器可提供以下優點：</span><span class="sxs-lookup"><span data-stu-id="a4bd0-106">Linked servers offer the following advantages:</span></span>

-   <span data-ttu-id="a4bd0-107">從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部存取資料的能力。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-107">The ability to access data from outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

-   <span data-ttu-id="a4bd0-108">在企業間的異質資料來源上發出分散式查詢、更新、命令與交易的能力。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-108">The ability to issue distributed queries, updates, commands, and transactions on heterogeneous data sources across the enterprise.</span></span>

-   <span data-ttu-id="a4bd0-109">以類似方式處理不同資料來源的能力。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-109">The ability to address diverse data sources similarly.</span></span>

 <span data-ttu-id="a4bd0-110">您可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或使用 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 陳述式，來設定連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-110">You can configure a linked server by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or by using the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) statement.</span></span> <span data-ttu-id="a4bd0-111">OLE DB 提供者的必要參數類型和數目有極大的不同。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-111">OLE DB providers vary greatly in the type and number of parameters required.</span></span> <span data-ttu-id="a4bd0-112">例如，部分提供者需要您使用 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)執行個體外部的 OLE DB 資料來源執行命令。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-112">For example some providers require you to provide a security context for the connection using [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql).</span></span> <span data-ttu-id="a4bd0-113">部分 OLE DB 提供者允許 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 更新 OLE DB 來源上的資料。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-113">Some OLE DB providers allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to update data on the OLE DB source.</span></span> <span data-ttu-id="a4bd0-114">其他提供者則只提供唯讀資料存取。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-114">Others provide only read-only data access.</span></span> <span data-ttu-id="a4bd0-115">如需有關每個 OLE DB 提供者的詳細資訊，請參閱該 OLE DB 提供者的文件。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-115">For information about each OLE DB provider, consult documentation for that OLE DB provider.</span></span>

## <a name="linked-server-components"></a><span data-ttu-id="a4bd0-116">連結伺服器元件</span><span class="sxs-lookup"><span data-stu-id="a4bd0-116">Linked Server Components</span></span>
 <span data-ttu-id="a4bd0-117">連結伺服器定義會指定下列物件：</span><span class="sxs-lookup"><span data-stu-id="a4bd0-117">A linked server definition specifies the following objects:</span></span>

-   <span data-ttu-id="a4bd0-118">OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="a4bd0-118">An OLE DB provider</span></span>

-   <span data-ttu-id="a4bd0-119">OLE DB 資料來源</span><span class="sxs-lookup"><span data-stu-id="a4bd0-119">An OLE DB data source</span></span>

 <span data-ttu-id="a4bd0-120">「OLE DB 提供者」是一種 DLL，可管理特定資料來源並與其互動。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-120">An *OLE DB provider* is a DLL that manages and interacts with a specific data source.</span></span> <span data-ttu-id="a4bd0-121">「OLE DB 資料來源」則識別可透過 OLE DB 存取的特定資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-121">An *OLE DB data source* identifies the specific database that can be accessed through OLE DB.</span></span> <span data-ttu-id="a4bd0-122">雖然透過連結伺服器定義來查詢的資料來源通常都是資料庫，不過，各種檔案及檔案格式都有 OLE DB 提供者的存在。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-122">Although data sources queried through linked server definitions are ordinarily databases, OLE DB providers exist for a variety of files and file formats.</span></span> <span data-ttu-id="a4bd0-123">其中包括文字檔、工作表資料，以及全文檢索內容搜尋的結果。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-123">These include text files, spreadsheet data, and the results of full-text content searches.</span></span>

 <span data-ttu-id="a4bd0-124">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者 (PROGID： SQLNCLI11) 是的官方 OLE DB 提供者 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider (PROGID: SQLNCLI11) is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a4bd0-125">分散式查詢是專為處理任何實作必要 OLE DB 介面的 OLE DB 提供者而設計；</span><span class="sxs-lookup"><span data-stu-id="a4bd0-125">distributed queries are designed to work with any OLE DB provider that implements the required OLE DB interfaces.</span></span> <span data-ttu-id="a4bd0-126">不過， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 只有針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native OLE DB 提供者以及某些其他提供者測試過。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been tested against only the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider and certain other providers.</span></span>

## <a name="linked-server-details"></a><span data-ttu-id="a4bd0-127">連結伺服器詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4bd0-127">Linked Server Details</span></span>
 <span data-ttu-id="a4bd0-128">下圖說明連結伺服器組態的基本設定。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-128">The following illustration shows the basics of a linked server configuration.</span></span>

 <span data-ttu-id="a4bd0-129">![用戶端層、伺服器層和資料庫伺服器層](../../database-engine/media/lsvr.gif "用戶端層、伺服器層和資料庫伺服器層")</span><span class="sxs-lookup"><span data-stu-id="a4bd0-129">![Client tier, server tier, and database server tier](../../database-engine/media/lsvr.gif "Client tier, server tier, and database server tier")</span></span>

 <span data-ttu-id="a4bd0-130">連結伺服器通常用於處理分散式查詢。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-130">Typically, linked servers are used to handle distributed queries.</span></span> <span data-ttu-id="a4bd0-131">當用戶端應用程式透過連結伺服器來執行分散式查詢時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會剖析命令，並將要求傳送至 OLE DB。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-131">When a client application executes a distributed query through a linked server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] parses the command and sends requests to OLE DB.</span></span> <span data-ttu-id="a4bd0-132">資料列集要求可能是採用對提供者執行查詢的形式，也可能是開啟提供者的基底資料表 (Base Table)。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-132">The rowset request may be in the form of executing a query against the provider or opening a base table from the provider.</span></span>

 <span data-ttu-id="a4bd0-133">若要讓資料來源透過連結伺服器來傳回資料，該資料來源的 OLE DB 提供者 (DLL) 必須與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的執行個體位在同一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-133">For a data source to return data through a linked server, the OLE DB provider (DLL) for that data source must be present on the same server as the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="a4bd0-134">若是使用協力廠商的 OLE DB 提供者，則用來執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務的帳戶，必須要有該提供者安裝位置之目錄及其所有子目錄的讀取和執行權限。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-134">When a third-party OLE DB provider is used, the account under which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service runs must have read and execute permissions for the directory, and all subdirectories, in which the provider is installed.</span></span>

## <a name="managing-providers"></a><span data-ttu-id="a4bd0-135">管理提供者</span><span class="sxs-lookup"><span data-stu-id="a4bd0-135">Managing Providers</span></span>
 <span data-ttu-id="a4bd0-136">有一組選項可用來控制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如何載入及使用登錄中所指定的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-136">There is a set of options that control how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads and uses OLE DB providers that are specified in the registry.</span></span>

## <a name="managing-linked-server-definitions"></a><span data-ttu-id="a4bd0-137">管理連結伺服器定義</span><span class="sxs-lookup"><span data-stu-id="a4bd0-137">Managing Linked Server Definitions</span></span>
 <span data-ttu-id="a4bd0-138">當您設定連結伺服器時，請使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]來註冊連接資訊與資料來源資訊。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-138">When you are setting up a linked server, register the connection information and data source information with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4bd0-139">註冊完成之後，就可以使用單一邏輯名稱來參考這個資料來源。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-139">After registered, that data source can be referred to with a single logical name.</span></span>

 <span data-ttu-id="a4bd0-140">您可以使用預存程序及目錄檢視來管理連結伺服器定義：</span><span class="sxs-lookup"><span data-stu-id="a4bd0-140">You can use stored procedures and catalog views to manage linked server definitions:</span></span>

-   <span data-ttu-id="a4bd0-141">執行 **sp_addlinkedserver**來建立連結伺服器定義。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-141">Create a linked server definition by running **sp_addlinkedserver**.</span></span>

-   <span data-ttu-id="a4bd0-142">針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sys.servers **系統目錄檢視來執行查詢，以檢視在特定** 執行個體中定義的連結伺服器相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-142">View information about the linked servers defined in a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by running a query against the **sys.servers** system catalog views.</span></span>

-   <span data-ttu-id="a4bd0-143">藉由執行 **sp_dropserver**來刪除連結伺服器的定義。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-143">Delete a linked server definition by running **sp_dropserver**.</span></span> <span data-ttu-id="a4bd0-144">您也可以使用這個預存程序來移除遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-144">You can also use this stored procedure to remove a remote server.</span></span>

 <span data-ttu-id="a4bd0-145">您也可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]來定義連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-145">You can also define linked servers by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a4bd0-146">在物件總管中，以滑鼠右鍵按一下 [伺服器物件]，選取 [新增]，然後選取 [連結伺服器]。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-146">In the Object Explorer, right-click **Server Objects**, select **New**, and select **Linked Server**.</span></span> <span data-ttu-id="a4bd0-147">您可以用滑鼠右鍵按一下連結伺服器名稱，並選取 [刪除]，以刪除連結伺服器定義。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-147">You can delete a linked server definition by right-clicking the linked server name and selecting **Delete**.</span></span>

 <span data-ttu-id="a4bd0-148">當您對連結伺服器執行分散式查詢時，所要查詢的每個資料來源均需包含完整的四部分資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-148">When you execute a distributed query against a linked server, include a fully qualified, four-part table name for each data source to query.</span></span> <span data-ttu-id="a4bd0-149">這四部分名稱的格式應為_linked_server_name. catalog_**. _`schema`_ 。**_object_name_。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-149">This four-part name should be in the form _linked_server_name.catalog_**._`schema`_.**_object_name_.</span></span>

> [!NOTE]
>  <span data-ttu-id="a4bd0-150">連結的伺服器可以定義為指回 (回送，Loopback) 到定義它們的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-150">Linked servers can be defined to point back (loop back) to the server on which they are defined.</span></span> <span data-ttu-id="a4bd0-151">回送伺服器最適合用於測試針對單一伺服器網路使用分散式查詢的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-151">Loopback servers are most useful when testing an application that uses distributed queries on a single server network.</span></span> <span data-ttu-id="a4bd0-152">回送連結的伺服器主要用於測試，而且不支援許多作業，例如分散式交易。</span><span class="sxs-lookup"><span data-stu-id="a4bd0-152">Loopback linked servers are intended for testing and are not supported for many operations, such as distributed transactions.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="a4bd0-153">相關工作</span><span class="sxs-lookup"><span data-stu-id="a4bd0-153">Related Tasks</span></span>
 [<span data-ttu-id="a4bd0-154">建立連結的伺服器 &#40;SQL Server Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-154">Create Linked Servers &#40;SQL Server Database Engine&#41;</span></span>](create-linked-servers-sql-server-database-engine.md)

 [<span data-ttu-id="a4bd0-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)

 [<span data-ttu-id="a4bd0-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)

 [<span data-ttu-id="a4bd0-157">sp_dropserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-157">sp_dropserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql)

## <a name="related-content"></a><span data-ttu-id="a4bd0-158">相關內容</span><span class="sxs-lookup"><span data-stu-id="a4bd0-158">Related Content</span></span>
 [<span data-ttu-id="a4bd0-159">sys.servers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-159">sys.servers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)

 [<span data-ttu-id="a4bd0-160">sp_linkedservers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4bd0-160">sp_linkedservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)


