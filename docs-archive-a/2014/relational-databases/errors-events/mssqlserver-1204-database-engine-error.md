---
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ca03c19552b88e391d2de053193a70531571ece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595082"
---
# <a name="mssqlserver_1204"></a><span data-ttu-id="4f4c3-102">MSSQLSERVER_1204</span><span class="sxs-lookup"><span data-stu-id="4f4c3-102">MSSQLSERVER_1204</span></span>
    
## <a name="details"></a><span data-ttu-id="4f4c3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f4c3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f4c3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4f4c3-104">Product Name</span></span>|<span data-ttu-id="4f4c3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4f4c3-105">SQL Server</span></span>|  
|<span data-ttu-id="4f4c3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4f4c3-106">Event ID</span></span>|<span data-ttu-id="4f4c3-107">1204</span><span class="sxs-lookup"><span data-stu-id="4f4c3-107">1204</span></span>|  
|<span data-ttu-id="4f4c3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="4f4c3-108">Event Source</span></span>|<span data-ttu-id="4f4c3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4f4c3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4f4c3-110">元件</span><span class="sxs-lookup"><span data-stu-id="4f4c3-110">Component</span></span>|<span data-ttu-id="4f4c3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4f4c3-111">SQLEngine</span></span>|  
|<span data-ttu-id="4f4c3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4f4c3-112">Symbolic Name</span></span>|<span data-ttu-id="4f4c3-113">LK_OUTOF</span><span class="sxs-lookup"><span data-stu-id="4f4c3-113">LK_OUTOF</span></span>|  
|<span data-ttu-id="4f4c3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4f4c3-114">Message Text</span></span>|<span data-ttu-id="4f4c3-115">SQL Server Database Engine 的執行個體目前無法取得 LOCK 資源。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-115">The instance of the SQL Server Database Engine cannot obtain a LOCK resource at this time.</span></span> <span data-ttu-id="4f4c3-116">請在使用中使用者較少時重新執行您的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-116">Rerun your statement when there are fewer active users.</span></span> <span data-ttu-id="4f4c3-117">要求資料庫管理員檢查這個執行個體的鎖定與記憶體組態，或者檢查長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-117">Ask the database administrator to check the lock and memory configuration for this instance, or to check for long-running transactions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f4c3-118">說明</span><span class="sxs-lookup"><span data-stu-id="4f4c3-118">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4f4c3-119">無法取得鎖定資源。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-119">cannot obtain a lock resource.</span></span> <span data-ttu-id="4f4c3-120">這項錯誤可能是由於下列其中一個原因所造成：</span><span class="sxs-lookup"><span data-stu-id="4f4c3-120">This can be caused by either of the following reasons:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4f4c3-121">無法從作業系統配置更多記憶體，原因可能是其他處理序正在使用作業系統，或是因為伺服器正在運作，而且已經設定 **max server memory** 選項。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-121">cannot allocate more memory from the operating system, either because other processes are using it, or because the server is operating with the **max server memory** option configured.</span></span>  
  
-   <span data-ttu-id="4f4c3-122">鎖定管理員不會使用超過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可用記憶體的 60%。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-122">The lock manager will not use more than 60 percent of the memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f4c3-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4f4c3-123">User Action</span></span>  
 <span data-ttu-id="4f4c3-124">如果您懷疑 SQL Server 無法配置足夠的記憶體，請嘗試下列方法：</span><span class="sxs-lookup"><span data-stu-id="4f4c3-124">If you suspect that SQL Server cannot allocate sufficient memory, try the following:</span></span>  
  
-   <span data-ttu-id="4f4c3-125">如果有 SQL Server 以外的應用程式正在耗用資源，請嘗試停止這些應用程式或考慮在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-125">If applications besides SQL Server are consuming resources, try stopping these applications or consider running them on a separate server.</span></span> <span data-ttu-id="4f4c3-126">這個動作可以從 SQL Server 的其他處理序釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-126">This will remove release memory from other processes for SQL Server.</span></span>  
  
-   <span data-ttu-id="4f4c3-127">如果您已經設定 max server memory，請增加 max server memory 的設定值。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-127">If you have configured max server memory, increase max server memory setting.</span></span>  
  
 <span data-ttu-id="4f4c3-128">如果您懷疑鎖定管理員已經使用最大的可用記憶體容量，請找出擁有最大鎖定數量的交易，並結束該筆交易。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-128">If you suspect that the lock manager has used the maximum amount of available memory identify the transaction that is holding the most locks and terminate it.</span></span> <span data-ttu-id="4f4c3-129">下列指令碼會找出擁有最大鎖定數量的交易：</span><span class="sxs-lookup"><span data-stu-id="4f4c3-129">The following script will identify the transaction with the most locks:</span></span>  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 <span data-ttu-id="4f4c3-130">取得最高的工作階段識別碼，並使用 KILL 命令結束該工作階段。</span><span class="sxs-lookup"><span data-stu-id="4f4c3-130">Take the highest session id, and terminate it using the KILL command.</span></span>  
  
  
