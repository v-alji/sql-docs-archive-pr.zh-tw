---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f77e39c71901166085d011d6d00f9a4a379bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687946"
---
# <a name="mssqlserver_17300"></a><span data-ttu-id="d7aa8-102">MSSQLSERVER_17300</span><span class="sxs-lookup"><span data-stu-id="d7aa8-102">MSSQLSERVER_17300</span></span>
    
## <a name="details"></a><span data-ttu-id="d7aa8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7aa8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7aa8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d7aa8-104">Product Name</span></span>|<span data-ttu-id="d7aa8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7aa8-105">SQL Server</span></span>|  
|<span data-ttu-id="d7aa8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d7aa8-106">Event ID</span></span>|<span data-ttu-id="d7aa8-107">17300</span><span class="sxs-lookup"><span data-stu-id="d7aa8-107">17300</span></span>|  
|<span data-ttu-id="d7aa8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d7aa8-108">Event Source</span></span>|<span data-ttu-id="d7aa8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7aa8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7aa8-110">元件</span><span class="sxs-lookup"><span data-stu-id="d7aa8-110">Component</span></span>|<span data-ttu-id="d7aa8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7aa8-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7aa8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d7aa8-112">Symbolic Name</span></span>|<span data-ttu-id="d7aa8-113">PROC_OUT_OF_SYSTASK_SESSIONS</span><span class="sxs-lookup"><span data-stu-id="d7aa8-113">PROC_OUT_OF_SYSTASK_SESSIONS</span></span>|  
|<span data-ttu-id="d7aa8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d7aa8-114">Message Text</span></span>|<span data-ttu-id="d7aa8-115">由於記憶體不足或設定的工作階段數目超過伺服器的容許最大值，使 SQL Server 無法執行新的系統工作。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-115">SQL Server was unable to run a new system task, either because there is insufficient memory or the number of configured sessions exceeds the maximum allowed in the server.</span></span> <span data-ttu-id="d7aa8-116">請確認伺服器是否有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-116">Verify that the server has adequate memory.</span></span> <span data-ttu-id="d7aa8-117">使用 sp_configure 搭配 'user connections' 選項來檢查允許的最大使用者連接數目。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-117">Use sp_configure with option 'user connections' to check the maximum number of user connections allowed.</span></span> <span data-ttu-id="d7aa8-118">使用 sys.dm_exec_sessions 來檢查目前的工作階段數目，包括使用者處理。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-118">Use sys.dm_exec_sessions to check the current number of sessions, including user processes.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7aa8-119">說明</span><span class="sxs-lookup"><span data-stu-id="d7aa8-119">Explanation</span></span>  
 <span data-ttu-id="d7aa8-120">嘗試執行新系統工作的行為失敗，因為記憶體不足，或者超過了伺服器的已設定工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-120">An attempt to run a new system task failed because of insufficient memory or because the number of configured sessions in the server was exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7aa8-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d7aa8-121">User Action</span></span>  
 <span data-ttu-id="d7aa8-122">請確認伺服器擁有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-122">Verify that the server has enough memory.</span></span> <span data-ttu-id="d7aa8-123">請使用 sys.dm_exec_sessions 來確認目前的系統工作數目，並且使用 sp_configure 來確認最大使用者連接的設定值。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-123">Verify the current number of system tasks by using sys.dm_exec_sessions, and verify the configured value of maximum user connections by using sp_configure.</span></span>  
  
 <span data-ttu-id="d7aa8-124">依照需要執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d7aa8-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="d7aa8-125">為伺服器增加更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-125">Add more memory to the server.</span></span>  
  
-   <span data-ttu-id="d7aa8-126">結束一個或多個工作階段。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-126">Terminate one or more sessions.</span></span>  
  
-   <span data-ttu-id="d7aa8-127">增加伺服器允許的最大使用者連接數目。</span><span class="sxs-lookup"><span data-stu-id="d7aa8-127">Increase the maximum number of user connections allowed on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7aa8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7aa8-128">See Also</span></span>  
 <span data-ttu-id="d7aa8-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d7aa8-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="d7aa8-130">[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d7aa8-130">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="d7aa8-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d7aa8-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span></span>  
 <span data-ttu-id="d7aa8-132">[設定 user connections 伺服器設定選項](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="d7aa8-132">[Configure the user connections Server Configuration Option](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="d7aa8-133">KILL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d7aa8-133">KILL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
