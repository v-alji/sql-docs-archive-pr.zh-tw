---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7dd3c8c5a287e2d123e2a9d1430ecd49b27f29f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595043"
---
# <a name="mssqlserver_905"></a><span data-ttu-id="3a4dd-102">MSSQLSERVER_905</span><span class="sxs-lookup"><span data-stu-id="3a4dd-102">MSSQLSERVER_905</span></span>
    
## <a name="details"></a><span data-ttu-id="3a4dd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a4dd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a4dd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a4dd-104">Product Name</span></span>|<span data-ttu-id="3a4dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3a4dd-105">SQL Server</span></span>|  
|<span data-ttu-id="3a4dd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a4dd-106">Event ID</span></span>|<span data-ttu-id="3a4dd-107">905</span><span class="sxs-lookup"><span data-stu-id="3a4dd-107">905</span></span>|  
|<span data-ttu-id="3a4dd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a4dd-108">Event Source</span></span>|<span data-ttu-id="3a4dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3a4dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3a4dd-110">元件</span><span class="sxs-lookup"><span data-stu-id="3a4dd-110">Component</span></span>|<span data-ttu-id="3a4dd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3a4dd-111">SQLEngine</span></span>|  
|<span data-ttu-id="3a4dd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a4dd-112">Symbolic Name</span></span>|<span data-ttu-id="3a4dd-113">DBSTARTUP_EE_PARTITIONING</span><span class="sxs-lookup"><span data-stu-id="3a4dd-113">DBSTARTUP_EE_PARTITIONING</span></span>|  
|<span data-ttu-id="3a4dd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a4dd-114">Message Text</span></span>|<span data-ttu-id="3a4dd-115">資料庫 '%.\*ls' 無法在此版本的 SQL Server 中啟動，因為它包含資料分割函式 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-115">Database '%.\*ls' cannot be started in this edition of SQL Server because it contains a partition function '%.\*ls'.</span></span> <span data-ttu-id="3a4dd-116">只有 Enterprise Edition 的 SQL Server 才支援分割區。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-116">Only Enterprise edition of SQL Server supports partitioning.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a4dd-117">說明</span><span class="sxs-lookup"><span data-stu-id="3a4dd-117">Explanation</span></span>  
 <span data-ttu-id="3a4dd-118">資料庫包含一個或多個分割的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-118">The database contains one or more partitioned tables or indexes.</span></span> <span data-ttu-id="3a4dd-119">這一版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法使用資料分割。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-119">This edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot use partitioning.</span></span> <span data-ttu-id="3a4dd-120">因此，資料庫無法正確啟動。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-120">Therefore, the database cannot be started correctly.</span></span> <span data-ttu-id="3a4dd-121">並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本都可使用資料分割資料表和索引。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-121">Partitioned tables and indexes are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3a4dd-122">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-122">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a4dd-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a4dd-123">User Action</span></span>  
 <span data-ttu-id="3a4dd-124">使用 sp_detach_db 預存程序來卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-124">Detach the database by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="3a4dd-125">視需要移動檔案，然後將資料庫附加到所支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的執行個體，其方式是搭配 FOR ATTACH 或 FOR ATTACH_REBUILD_LOG 選項使用 CREATE DATABASE。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-125">Move the files if it is needed, and then attach the database to an instance of a supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition by using the CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="3a4dd-126">停用所有資料表上的資料分割，並移除資料分割函數。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-126">Disable partitioning on all tables and remove the partitioning functions.</span></span> <span data-ttu-id="3a4dd-127">再次卸離資料庫，然後將資料庫重新附加到目前的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3a4dd-127">Detach the database again, and reattach the database to the current server.</span></span>  
  
  
