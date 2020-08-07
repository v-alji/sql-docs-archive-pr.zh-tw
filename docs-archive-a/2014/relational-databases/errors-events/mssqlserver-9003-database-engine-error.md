---
title: MSSQLSERVER_9003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6f67e4184ea54be6bcd5c2a74d3c0e0711b702f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597850"
---
# <a name="mssqlserver_9003"></a><span data-ttu-id="c2f6f-102">MSSQLSERVER_9003</span><span class="sxs-lookup"><span data-stu-id="c2f6f-102">MSSQLSERVER_9003</span></span>
    
## <a name="details"></a><span data-ttu-id="c2f6f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c2f6f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2f6f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c2f6f-104">Product Name</span></span>|<span data-ttu-id="c2f6f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c2f6f-105">SQL Server</span></span>|  
|<span data-ttu-id="c2f6f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c2f6f-106">Event ID</span></span>|<span data-ttu-id="c2f6f-107">9003</span><span class="sxs-lookup"><span data-stu-id="c2f6f-107">9003</span></span>|  
|<span data-ttu-id="c2f6f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c2f6f-108">Event Source</span></span>|<span data-ttu-id="c2f6f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c2f6f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c2f6f-110">元件</span><span class="sxs-lookup"><span data-stu-id="c2f6f-110">Component</span></span>|<span data-ttu-id="c2f6f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c2f6f-111">SQLEngine</span></span>|  
|<span data-ttu-id="c2f6f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c2f6f-112">Symbolic Name</span></span>|<span data-ttu-id="c2f6f-113">LOG_INVALID_LSN</span><span class="sxs-lookup"><span data-stu-id="c2f6f-113">LOG_INVALID_LSN</span></span>|  
|<span data-ttu-id="c2f6f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c2f6f-114">Message Text</span></span>|<span data-ttu-id="c2f6f-115">傳遞到資料庫 '%.\*ls' 記錄檔掃描的記錄檔掃描號碼 %S_LSN 無效。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-115">The log scan number %S_LSN passed to log scan in database '%.\*ls' is not valid.</span></span> <span data-ttu-id="c2f6f-116">這個錯誤可能表示資料損毀或記錄檔 (.ldf) 不符合資料檔案 (.mdf)。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-116">This error may indicate data corruption or that the log file (.ldf) does not match the data file (.mdf).</span></span> <span data-ttu-id="c2f6f-117">如果是在複寫期間發生這個錯誤，請重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-117">If this error occurred during replication, re-create the publication.</span></span> <span data-ttu-id="c2f6f-118">否則，若該問題造成啟動失敗，則請從備份進行還原。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-118">Otherwise, restore from backup if the problem results in a failure during startup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2f6f-119">說明</span><span class="sxs-lookup"><span data-stu-id="c2f6f-119">Explanation</span></span>  
 <span data-ttu-id="c2f6f-120">某個元件將無效的記錄序號傳遞給資料庫的記錄檔管理員。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-120">A component passed an invalid log sequence number to the log manager for the database.</span></span> <span data-ttu-id="c2f6f-121">這個問題的原因可能是複寫、損毀或主要資料檔案與記錄檔之間的不一致。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-121">This could be replication, corruption, or an inconsistency between the primary data file and the log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2f6f-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c2f6f-122">User Action</span></span>  
 <span data-ttu-id="c2f6f-123">如果是在複寫期間發生這個錯誤，請重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-123">If this occurred during replication, recreate the publication.</span></span> <span data-ttu-id="c2f6f-124">否則，請從備份進行還原。</span><span class="sxs-lookup"><span data-stu-id="c2f6f-124">Otherwise, restore from backup.</span></span>  
  
  
