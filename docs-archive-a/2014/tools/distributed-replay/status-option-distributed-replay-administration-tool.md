---
title: 狀態選項 (Distributed Replay 管理工具) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ce3d07bc357c5f3788fb6f995a43399021b3553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686646"
---
# <a name="status-option-distributed-replay-administration-tool"></a><span data-ttu-id="3f54e-102">狀態選項 (Distributed Replay 管理工具)</span><span class="sxs-lookup"><span data-stu-id="3f54e-102">Status Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="3f54e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是命令列工具，可讓您用來與 Distributed Replay controller 通訊。</span><span class="sxs-lookup"><span data-stu-id="3f54e-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="3f54e-104">此主題描述 **status** 命令列選項與對應的語法。</span><span class="sxs-lookup"><span data-stu-id="3f54e-104">This topic describes the **status** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="3f54e-105">**status** 選項會查詢控制器，並顯示目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="3f54e-105">The **status** option queries the controller and displays the current status.</span></span>

 <span data-ttu-id="3f54e-106">![主題連結圖示](../../database-engine/media/topic-link.gif "主題連結圖示") 如需搭配系統管理工具語法使用的語法慣例詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3f54e-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="3f54e-107">語法</span><span class="sxs-lookup"><span data-stu-id="3f54e-107">Syntax</span></span>

```

dreplay status [-mcontroller] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="3f54e-108">參數</span><span class="sxs-lookup"><span data-stu-id="3f54e-108">Parameters</span></span>
 <span data-ttu-id="3f54e-109">**-m** *控制器*指定控制器的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="3f54e-109">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="3f54e-110">您可以使用 "`localhost`" 或 "`.`" 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="3f54e-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="3f54e-111">如果未指定 **-m** 參數，則會使用本機電腦。</span><span class="sxs-lookup"><span data-stu-id="3f54e-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="3f54e-112">**-f** *status_interval*指定顯示狀態 (的頻率（以秒為單位）) 。</span><span class="sxs-lookup"><span data-stu-id="3f54e-112">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="3f54e-113">如果未指定 **-f** 參數，預設間隔為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="3f54e-113">If the **-f** parameter is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="3f54e-114">範例</span><span class="sxs-lookup"><span data-stu-id="3f54e-114">Examples</span></span>
 <span data-ttu-id="3f54e-115">在下列範例中，每隔 60 秒顯示目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3f54e-115">In the following example, the current status is displayed every 60 seconds.</span></span> <span data-ttu-id="3f54e-116">`localhost` 值指出控制器服務與管理工具在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="3f54e-116">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay status -m localhost -f 60
```

## <a name="permissions"></a><span data-ttu-id="3f54e-117">權限</span><span class="sxs-lookup"><span data-stu-id="3f54e-117">Permissions</span></span>
 <span data-ttu-id="3f54e-118">您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="3f54e-118">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="3f54e-119">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="3f54e-119">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="3f54e-120">如需詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="3f54e-120">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f54e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f54e-121">See Also</span></span>
 <span data-ttu-id="3f54e-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [transact-sql 偵錯工具](../../relational-databases/scripting/transact-sql-debugger.md)</span><span class="sxs-lookup"><span data-stu-id="3f54e-122">[SQL Server Distributed Replay](sql-server-distributed-replay.md) [Transact-SQL Debugger](../../relational-databases/scripting/transact-sql-debugger.md)</span></span>


