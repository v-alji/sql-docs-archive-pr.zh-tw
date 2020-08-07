---
title: 管理工具命令列選項 (Distributed Replay 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506be071f44937d82902585e5a0621212083dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596960"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a><span data-ttu-id="a2985-102">管理工具命令列選項 (Distributed Replay Utility)</span><span class="sxs-lookup"><span data-stu-id="a2985-102">Administration Tool Command-line Options (Distributed Replay Utility)</span></span>
  <span data-ttu-id="a2985-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是命令列工具，可讓您用來與 Distributed Replay controller 通訊。</span><span class="sxs-lookup"><span data-stu-id="a2985-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="a2985-104">您可以使用管理工具來起始、監視及取消控制器上的作業。</span><span class="sxs-lookup"><span data-stu-id="a2985-104">Use the administration tool to initiate, monitor, and cancel operations on the controller.</span></span>  
  
 <span data-ttu-id="a2985-105">![主題連結圖示](../../database-engine/media/topic-link.gif "主題連結圖示")如需與系統管理工具語法搭配使用的語法慣例詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a2985-105">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2985-106">語法</span><span class="sxs-lookup"><span data-stu-id="a2985-106">Syntax</span></span>  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a><span data-ttu-id="a2985-107">備註</span><span class="sxs-lookup"><span data-stu-id="a2985-107">Remarks</span></span>  
 <span data-ttu-id="a2985-108">您可以使用 `DReplay.exe` 發出下列命令列選項：</span><span class="sxs-lookup"><span data-stu-id="a2985-108">You can issue the following command-line options with `DReplay.exe`:</span></span>  
  
 <span data-ttu-id="a2985-109">**preprocess**</span><span class="sxs-lookup"><span data-stu-id="a2985-109">**preprocess**</span></span>  
 <span data-ttu-id="a2985-110">起始前置處理階段。</span><span class="sxs-lookup"><span data-stu-id="a2985-110">Initiates the preprocess stage.</span></span> <span data-ttu-id="a2985-111">控制器會準備輸入追蹤資料 (您從實際執行環境擷取而來)，以便對目標伺服器重新執行。</span><span class="sxs-lookup"><span data-stu-id="a2985-111">The controller prepares the input trace data, which you captured from the production environment, for replay against the target server.</span></span>  
  
 <span data-ttu-id="a2985-112">**replay**</span><span class="sxs-lookup"><span data-stu-id="a2985-112">**replay**</span></span>  
 <span data-ttu-id="a2985-113">起始事件重新執行階段。</span><span class="sxs-lookup"><span data-stu-id="a2985-113">Initiates the event replay stage.</span></span> <span data-ttu-id="a2985-114">控制器會分派重新執行資料給指定的用戶端、啟動分散式重新執行，以及同步處理用戶端。</span><span class="sxs-lookup"><span data-stu-id="a2985-114">The controller dispatches replay data to the specified clients, launches the distributed replay, and synchronizes the clients.</span></span> <span data-ttu-id="a2985-115">另外，每個選取的用戶端會記錄重新執行活動，並在本機上儲存結果追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="a2985-115">Optionally, each client that was selected records the replay activity and saves result trace files locally.</span></span>  
  
 <span data-ttu-id="a2985-116">**status**</span><span class="sxs-lookup"><span data-stu-id="a2985-116">**status**</span></span>  
 <span data-ttu-id="a2985-117">查詢控制器，並顯示目前狀態。</span><span class="sxs-lookup"><span data-stu-id="a2985-117">Queries the controller and displays the current status.</span></span>  
  
 <span data-ttu-id="a2985-118">**cancel**</span><span class="sxs-lookup"><span data-stu-id="a2985-118">**cancel**</span></span>  
 <span data-ttu-id="a2985-119">取消目前正在控制器上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="a2985-119">Cancels the current operation that is running on the controller.</span></span>  
  
 <span data-ttu-id="a2985-120">如需包含命令引數和範例的詳細語法資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a2985-120">For detailed syntax information that includes the command arguments and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a2985-121">前置處理選項 &#40;Distributed Replay 管理工具&#41;</span><span class="sxs-lookup"><span data-stu-id="a2985-121">Preprocess Option &#40;Distributed Replay Administration Tool&#41;</span></span>](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="a2985-122">重新執行選項 &#40;Distributed Replay 管理工具&#41;</span><span class="sxs-lookup"><span data-stu-id="a2985-122">Replay Option &#40;Distributed Replay Administration Tool&#41;</span></span>](replay-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="a2985-123">狀態選項 &#40;Distributed Replay 管理工具&#41;</span><span class="sxs-lookup"><span data-stu-id="a2985-123">Status Option &#40;Distributed Replay Administration Tool&#41;</span></span>](status-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="a2985-124">取消選項 &#40;Distributed Replay 管理工具&#41;</span><span class="sxs-lookup"><span data-stu-id="a2985-124">Cancel Option &#40;Distributed Replay Administration Tool&#41;</span></span>](cancel-option-distributed-replay-administration-tool.md)  
  
 <span data-ttu-id="a2985-125">RPC 以 RPC 形式重新執行，而不是以語言事件的形式重新執行。</span><span class="sxs-lookup"><span data-stu-id="a2985-125">RPCs are replayed as RPCs and not as language events.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="a2985-126">權限</span><span class="sxs-lookup"><span data-stu-id="a2985-126">Permissions</span></span>  
 <span data-ttu-id="a2985-127">您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="a2985-127">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="a2985-128">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="a2985-128">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>  
  
 <span data-ttu-id="a2985-129">如需詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a2985-129">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2985-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2985-130">See Also</span></span>  
 [<span data-ttu-id="a2985-131">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="a2985-131">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)  
  
  
