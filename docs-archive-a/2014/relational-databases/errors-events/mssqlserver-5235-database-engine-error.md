---
title: MSSQLSERVER_5235 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707593"
---
# <a name="mssqlserver_5235"></a><span data-ttu-id="89b6c-102">MSSQLSERVER_5235</span><span class="sxs-lookup"><span data-stu-id="89b6c-102">MSSQLSERVER_5235</span></span>
    
## <a name="details"></a><span data-ttu-id="89b6c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="89b6c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89b6c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="89b6c-104">Product Name</span></span>|<span data-ttu-id="89b6c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="89b6c-105">SQL Server</span></span>|  
|<span data-ttu-id="89b6c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="89b6c-106">Event ID</span></span>|<span data-ttu-id="89b6c-107">5235</span><span class="sxs-lookup"><span data-stu-id="89b6c-107">5235</span></span>|  
|<span data-ttu-id="89b6c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="89b6c-108">Event Source</span></span>|<span data-ttu-id="89b6c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="89b6c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="89b6c-110">元件</span><span class="sxs-lookup"><span data-stu-id="89b6c-110">Component</span></span>|<span data-ttu-id="89b6c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="89b6c-111">SQLEngine</span></span>|  
|<span data-ttu-id="89b6c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="89b6c-112">Symbolic Name</span></span>|<span data-ttu-id="89b6c-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span><span class="sxs-lookup"><span data-stu-id="89b6c-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span></span>|  
|<span data-ttu-id="89b6c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="89b6c-114">Message Text</span></span>|<span data-ttu-id="89b6c-115">USER_NAME 執行的 [EMERGENCY] DBCC DBCC_COMMAND_DETAILS 因為錯誤狀態 ERROR_STATE 而異常結束。</span><span class="sxs-lookup"><span data-stu-id="89b6c-115">[EMERGENCY] DBCC DBCC_COMMAND_DETAILS executed by USER_NAME terminated abnormally due to error state ERROR_STATE.</span></span> <span data-ttu-id="89b6c-116">已耗用時間：HOURS 小時 MINUTES 分 SECONDS 秒。</span><span class="sxs-lookup"><span data-stu-id="89b6c-116">Elapsed time: HOURS hours MINUTES minutes SECONDS seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="89b6c-117">說明</span><span class="sxs-lookup"><span data-stu-id="89b6c-117">Explanation</span></span>  
 <span data-ttu-id="89b6c-118">這是當執行命令時發生非預期終止錯誤時，DBCC 列印到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔的摘要訊息。</span><span class="sxs-lookup"><span data-stu-id="89b6c-118">This is the summary message that DBCC prints to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log when an unexpected termination occurs while the command is running.</span></span> <span data-ttu-id="89b6c-119">訊息中報告的錯誤狀態定義未預期終止的類型。</span><span class="sxs-lookup"><span data-stu-id="89b6c-119">The error state reported in the message defines the type of unexpected termination.</span></span>  
  
 <span data-ttu-id="89b6c-120">下表列出並定義錯誤狀態：</span><span class="sxs-lookup"><span data-stu-id="89b6c-120">The following table lists and defines the error states.</span></span>  
  
|<span data-ttu-id="89b6c-121">錯誤狀態</span><span class="sxs-lookup"><span data-stu-id="89b6c-121">Error state</span></span>|<span data-ttu-id="89b6c-122">定義</span><span class="sxs-lookup"><span data-stu-id="89b6c-122">Definition</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="89b6c-123">狀態 0</span><span class="sxs-lookup"><span data-stu-id="89b6c-123">State 0</span></span>|<span data-ttu-id="89b6c-124">陳述式因為中繼資料嚴重損毀而結束。</span><span class="sxs-lookup"><span data-stu-id="89b6c-124">The statement was terminated because of a fatal metadata corruption.</span></span> <span data-ttu-id="89b6c-125">此訊息將伴隨錯誤 8930 的一或多個執行個體一起出現。</span><span class="sxs-lookup"><span data-stu-id="89b6c-125">This message will be accompanied by one or more instances of error 8930.</span></span>|  
|<span data-ttu-id="89b6c-126">狀態 1</span><span class="sxs-lookup"><span data-stu-id="89b6c-126">State 1</span></span>|<span data-ttu-id="89b6c-127">陳述式因為內部檢查失敗而結束。</span><span class="sxs-lookup"><span data-stu-id="89b6c-127">The statement was terminated because of an internal check failure.</span></span> <span data-ttu-id="89b6c-128">此訊息將伴隨錯誤 8967 的一個或多個執行個體一起出現。</span><span class="sxs-lookup"><span data-stu-id="89b6c-128">This message will be accompanied by one or more instances of error 8967.</span></span>|  
|<span data-ttu-id="89b6c-129">狀態 2</span><span class="sxs-lookup"><span data-stu-id="89b6c-129">State 2</span></span>|<span data-ttu-id="89b6c-130">核心儲存引擎系統資料表的基本系統資料表檢查失敗。</span><span class="sxs-lookup"><span data-stu-id="89b6c-130">Basic system table checks of the core storage engine system tables failed.</span></span> <span data-ttu-id="89b6c-131">此訊息將伴隨錯誤 [7984](mssqlserver-7984-database-engine-error.md)、7985、[7986](mssqlserver-7986-database-engine-error.md)、[7987](mssqlserver-7987-database-engine-error.md) 或 [7988](mssqlserver-7988-database-engine-error.md) 的一或多個執行個體一起出現。</span><span class="sxs-lookup"><span data-stu-id="89b6c-131">This message will be accompanied by one or more instances of error [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md), or [7988](mssqlserver-7988-database-engine-error.md).</span></span>|  
|<span data-ttu-id="89b6c-132">狀態 3</span><span class="sxs-lookup"><span data-stu-id="89b6c-132">State 3</span></span>|<span data-ttu-id="89b6c-133">DBCC 緊急模式修復失敗，因為重建交易記錄檔之後，無法啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="89b6c-133">DBCC emergency-mode repair failed because the database could not be started after rebuilding the transaction log.</span></span> <span data-ttu-id="89b6c-134">此訊息將伴隨錯誤 7909 一起出現。</span><span class="sxs-lookup"><span data-stu-id="89b6c-134">This message will be accompanied by error 7909.</span></span>|  
|<span data-ttu-id="89b6c-135">狀態 4</span><span class="sxs-lookup"><span data-stu-id="89b6c-135">State 4</span></span>|<span data-ttu-id="89b6c-136">命令執行期間發生宣告失敗或存取違規。</span><span class="sxs-lookup"><span data-stu-id="89b6c-136">A failed assertion or access violation occurred during the execution of the command.</span></span>|  
|<span data-ttu-id="89b6c-137">狀態 5</span><span class="sxs-lookup"><span data-stu-id="89b6c-137">State 5</span></span>|<span data-ttu-id="89b6c-138">發生使 DBCC 命令意外終止的未知錯誤。</span><span class="sxs-lookup"><span data-stu-id="89b6c-138">An unknown failure occurred that unexpectedly terminated the DBCC command.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="89b6c-139">使用者動作</span><span class="sxs-lookup"><span data-stu-id="89b6c-139">User Action</span></span>  
 <span data-ttu-id="89b6c-140">下表提供適用於指定之錯誤狀態的使用者動作。</span><span class="sxs-lookup"><span data-stu-id="89b6c-140">The following table provides the user action that is appropriate for the specified error state.</span></span>  
  
|<span data-ttu-id="89b6c-141">錯誤狀態</span><span class="sxs-lookup"><span data-stu-id="89b6c-141">Error state</span></span>|<span data-ttu-id="89b6c-142">使用者動作</span><span class="sxs-lookup"><span data-stu-id="89b6c-142">User action</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="89b6c-143">狀態 0</span><span class="sxs-lookup"><span data-stu-id="89b6c-143">State 0</span></span>|<span data-ttu-id="89b6c-144">從備份還原。</span><span class="sxs-lookup"><span data-stu-id="89b6c-144">Restore from backup.</span></span>|  
|<span data-ttu-id="89b6c-145">狀態 1</span><span class="sxs-lookup"><span data-stu-id="89b6c-145">State 1</span></span>|<span data-ttu-id="89b6c-146">連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="89b6c-146">Contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>|  
|<span data-ttu-id="89b6c-147">狀態 2</span><span class="sxs-lookup"><span data-stu-id="89b6c-147">State 2</span></span>|<span data-ttu-id="89b6c-148">從備份還原。</span><span class="sxs-lookup"><span data-stu-id="89b6c-148">Restore from backup.</span></span>|  
|<span data-ttu-id="89b6c-149">狀態 3</span><span class="sxs-lookup"><span data-stu-id="89b6c-149">State 3</span></span>|<span data-ttu-id="89b6c-150">從備份還原。</span><span class="sxs-lookup"><span data-stu-id="89b6c-150">Restore from backup.</span></span>|  
|<span data-ttu-id="89b6c-151">狀態 4</span><span class="sxs-lookup"><span data-stu-id="89b6c-151">State 4</span></span>|<span data-ttu-id="89b6c-152">連絡 CSS。</span><span class="sxs-lookup"><span data-stu-id="89b6c-152">Contact CSS.</span></span>|  
|<span data-ttu-id="89b6c-153">狀態 5</span><span class="sxs-lookup"><span data-stu-id="89b6c-153">State 5</span></span>|<span data-ttu-id="89b6c-154">重新執行命令。</span><span class="sxs-lookup"><span data-stu-id="89b6c-154">Run the command again.</span></span> <span data-ttu-id="89b6c-155">如果問題仍然存在，請連絡 CSS。</span><span class="sxs-lookup"><span data-stu-id="89b6c-155">If the problem persists, contact CSS.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89b6c-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b6c-156">See Also</span></span>  
 [<span data-ttu-id="89b6c-157">DBCC &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="89b6c-157">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
