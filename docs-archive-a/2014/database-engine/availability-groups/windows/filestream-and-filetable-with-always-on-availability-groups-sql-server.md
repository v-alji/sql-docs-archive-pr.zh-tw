---
title: 具有 AlwaysOn 可用性群組 (SQL Server) 的 FILESTREAM 和 FileTable |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7de7b4d66890bb5f1fe49799844f666de81f4db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595278"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="f39de-102">FILESTREAM 和 FileTable 與 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f39de-102">FILESTREAM and FileTable with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="f39de-103">本主題包含在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中使用 FILESTREAM 和 FileTable 功能搭配 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f39de-103">This topic contains information about the using the FILESTREAM and FileTable features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="f39de-104">支援所有 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="f39de-104">All FILESTREAM functionality is supported.</span></span> <span data-ttu-id="f39de-105">在容錯移轉之後，可讀取的次要複本以及新的主要複本上的 FILESTREAM 資料皆可供存取。</span><span class="sxs-lookup"><span data-stu-id="f39de-105">After a failover, FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
 <span data-ttu-id="f39de-106">僅部分支援 FileTable 功能。</span><span class="sxs-lookup"><span data-stu-id="f39de-106">FileTable functionality is partially supported.</span></span> <span data-ttu-id="f39de-107">在容錯移轉之後，主要複本上的 FileTable 資料可供存取，但卻無法存取位在可讀取之次要複本上的 FileTable 資料。</span><span class="sxs-lookup"><span data-stu-id="f39de-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
 <span data-ttu-id="f39de-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="f39de-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="f39de-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="f39de-109">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="f39de-110">使用虛擬網路名稱 (VNN) 進行 FILESTREAM 和 FileTable 存取</span><span class="sxs-lookup"><span data-stu-id="f39de-110">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>](#vnn)  
  
-   [<span data-ttu-id="f39de-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="f39de-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="f39de-112">相關內容</span><span class="sxs-lookup"><span data-stu-id="f39de-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f39de-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="f39de-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="f39de-114">將使用 FILESTREAM (包含或不含 FileTable) 的資料庫加入至可用性群組之前，請確定裝載可用性群組之可用性複本的每個伺服器執行個體都啟用了 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="f39de-114">Before adding a database that uses FILESTREAM, with or without FileTable, to an availability group, ensure that FILESTREAM is enabled on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="f39de-115">如需詳細資訊，請參閱 [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="f39de-115">For more information, see [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).</span></span>  
  
##  <a name="using-virtual-network-names-vnns-for-filestream-and-filetable-access"></a><a name="vnn"></a><span data-ttu-id="f39de-116">針對 FILESTREAM 和 FileTable 存取使用虛擬網路名稱 (Vnn) </span><span class="sxs-lookup"><span data-stu-id="f39de-116">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>  
 <span data-ttu-id="f39de-117">當您在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上啟用 FILESTREAM 時，系統就會建立執行個體層級共用，讓您存取 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="f39de-117">When you enable FILESTREAM on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], an instance-level share is created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="f39de-118">您可以依照下列格式使用電腦名稱來存取這個共用：</span><span class="sxs-lookup"><span data-stu-id="f39de-118">You access this share by using the computer name in the following format:</span></span>  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 <span data-ttu-id="f39de-119">不過，在 AlwaysOn 可用性群組中，電腦名稱是使用虛擬網路名稱 (VNN) 來虛擬化。</span><span class="sxs-lookup"><span data-stu-id="f39de-119">In an AlwaysOn availability group, however, the name of the computer is virtualized by using a Virtual Network Name, or VNN.</span></span> <span data-ttu-id="f39de-120">當電腦是可用性群組中的主要複本，而且可用性群組中的資料庫包含 FILESTREAM 資料時，系統也會建立 VNN 範圍的共用，讓您存取 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="f39de-120">When the computer is the primary replica in an availability group, and databases in the availability group contain FILESTREAM data, then a VNN-scoped share is also created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="f39de-121">這並不會影響 FILESTREAM 資料的 Transact-SQL 存取。</span><span class="sxs-lookup"><span data-stu-id="f39de-121">This does not affect Transact-SQL access to FILESTREAM data.</span></span> <span data-ttu-id="f39de-122">不過，使用檔案系統 API 的應用程式必須使用 VNN 範圍的共用，其路徑採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="f39de-122">However applications that use file system APIs have to use the VNN-scoped share, which has a path in the following format:</span></span>  
  
 `\\<VNN>\<filestream_share_name>`  
  
 <span data-ttu-id="f39de-123">發生下列其中一個事件時，系統就會建立這個 VNN 範圍的共用。</span><span class="sxs-lookup"><span data-stu-id="f39de-123">This VNN-scoped share is created when one of the following events occurs.</span></span>  
  
-   <span data-ttu-id="f39de-124">您將包含 FILESTREAM 資料的資料庫加入至主要複本上的 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="f39de-124">You add a database that contains FILESTREAM data to an AlwaysOn availability group on the primary replica.</span></span> <span data-ttu-id="f39de-125">在此情況中， `\\<computer_name>\<filestream_share_name>` 共用已經存在。</span><span class="sxs-lookup"><span data-stu-id="f39de-125">In this case, the share `\\<computer_name>\<filestream_share_name>` already exists.</span></span> <span data-ttu-id="f39de-126">系統會建立 `\\<VNN>\<filestream_share_name>` 共用。</span><span class="sxs-lookup"><span data-stu-id="f39de-126">The share `\\<VNN>\<filestream_share_name>` is created.</span></span>  
  
-   <span data-ttu-id="f39de-127">您在具有可用性群組的主要複本上啟用 FILESTREAM 進行檔案 i/o 資料流存取。</span><span class="sxs-lookup"><span data-stu-id="f39de-127">You enable FILESTREAM for file i/o streaming access on a primary replica that has availability groups.</span></span> <span data-ttu-id="f39de-128">系統會建立下列共用：</span><span class="sxs-lookup"><span data-stu-id="f39de-128">The following shares are created:</span></span>  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  <span data-ttu-id="f39de-129">`\\<VNN1>\<filestream_share_name>` (可用性群組 1)。</span><span class="sxs-lookup"><span data-stu-id="f39de-129">`\\<VNN1>\<filestream_share_name>` for availability group 1.</span></span>  
  
    3.  <span data-ttu-id="f39de-130">`\\<VNN2>\<filestream_share_name>` (可用性群組 2)。</span><span class="sxs-lookup"><span data-stu-id="f39de-130">`\\<VNN2>\<filestream_share_name>` for availability group 2.</span></span>  
  
 <span data-ttu-id="f39de-131">這些 VNN 範圍的共用也會傳播至所有次要複本。</span><span class="sxs-lookup"><span data-stu-id="f39de-131">These VNN-scoped shares are also propagated to all secondary replicas.</span></span>  
  
 <span data-ttu-id="f39de-132">當包含 FILESTREAM 或 FileTable 資料的資料庫屬於 AlwaysOn 可用性群組時：</span><span class="sxs-lookup"><span data-stu-id="f39de-132">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="f39de-133">FILESTREAM 和 FileTable 函數會接受或傳回虛擬網路名稱 (VNN) 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="f39de-133">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="f39de-134">如需有關這些函數的詳細資訊，請參閱 [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql) (Filestream 和 FileTable 函數 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="f39de-134">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="f39de-135">透過檔案系統 API 對 FILESTREAM 或 FileTable 資料進行的所有存取都應該使用 VNN 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="f39de-135">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span>  
  
 <span data-ttu-id="f39de-136">當資料庫屬於可用性群組的一部分時，如果您的應用程式嘗試依照 `\\<computer_name>\<filestream_share_name>` 格式使用電腦名稱來存取共用，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="f39de-136">If your application tries to access the share by using the computer name in the format `\\<computer_name>\<filestream_share_name>` when the database is part of an availability group, then an error is raised.</span></span>  
  
 <span data-ttu-id="f39de-137">當資料庫不屬於可用性群組的一部分時，如果您的應用程式嘗試使用 VNN 範圍的路徑來存取共用，則要求可能會成功。</span><span class="sxs-lookup"><span data-stu-id="f39de-137">If your application tries to access the share by using a VNN-scoped path when the database is not part of an availability group, then the request may succeed.</span></span> <span data-ttu-id="f39de-138">在此情況中，虛擬網路名稱會解析成電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="f39de-138">In this case, the virtual network name is resolved to the computer name.</span></span> <span data-ttu-id="f39de-139">不過，強烈建議您不要使用這種方式，因為如果可用性群組已卸除，VNN 範圍的路徑將會停止運作。</span><span class="sxs-lookup"><span data-stu-id="f39de-139">However this usage is strongly discouraged, since the VNN-scoped path will stop working if the availability group is dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f39de-140">相關工作</span><span class="sxs-lookup"><span data-stu-id="f39de-140">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f39de-141">啟用及設定 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="f39de-141">Enable and Configure FILESTREAM</span></span>](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [<span data-ttu-id="f39de-142">啟用 FileTable 的必要條件</span><span class="sxs-lookup"><span data-stu-id="f39de-142">Enable the Prerequisites for FileTable</span></span>](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f39de-143">相關內容</span><span class="sxs-lookup"><span data-stu-id="f39de-143">Related Content</span></span>  
 <span data-ttu-id="f39de-144">無。</span><span class="sxs-lookup"><span data-stu-id="f39de-144">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39de-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f39de-145">See Also</span></span>  
 [<span data-ttu-id="f39de-146">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="f39de-146">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
