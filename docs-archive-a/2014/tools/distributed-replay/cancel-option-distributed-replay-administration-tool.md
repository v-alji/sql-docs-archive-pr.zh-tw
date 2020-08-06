---
title: 取消選項 (Distributed Replay 管理工具) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d132fbf5ce541a2bdab82e44dc55e6fc92df536d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596959"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a><span data-ttu-id="95dd9-102">取消選項 (Distributed Replay 管理工具)</span><span class="sxs-lookup"><span data-stu-id="95dd9-102">Cancel Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="95dd9-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是命令列工具，可讓您用來與 Distributed Replay controller 通訊。</span><span class="sxs-lookup"><span data-stu-id="95dd9-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="95dd9-104">此主題描述 **cancel** 命令列選項與對應的語法。</span><span class="sxs-lookup"><span data-stu-id="95dd9-104">This topic describes the **cancel** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="95dd9-105">**cancel** 選項會取消目前正在控制器上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="95dd9-105">The **cancel** option cancels the current operation that is running on the controller.</span></span>

 <span data-ttu-id="95dd9-106">![主題連結圖示](../../database-engine/media/topic-link.gif "主題連結圖示")如需管理工具語法所使用之語法慣例的詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="95dd9-106">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="95dd9-107">語法</span><span class="sxs-lookup"><span data-stu-id="95dd9-107">Syntax</span></span>

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a><span data-ttu-id="95dd9-108">參數</span><span class="sxs-lookup"><span data-stu-id="95dd9-108">Parameters</span></span>
 <span data-ttu-id="95dd9-109">**-m** *controller*控制器的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="95dd9-109">**-m** *controller* The computer name of the controller.</span></span> <span data-ttu-id="95dd9-110">您可以使用 "`localhost`" 或 "`.`" 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="95dd9-110">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="95dd9-111">如果未指定 **-m** 參數，則會使用本機電腦。</span><span class="sxs-lookup"><span data-stu-id="95dd9-111">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="95dd9-112">**-q**無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="95dd9-112">**-q** Quiet mode.</span></span> <span data-ttu-id="95dd9-113">不會提示確認。</span><span class="sxs-lookup"><span data-stu-id="95dd9-113">Does not prompt for confirmation.</span></span>

 <span data-ttu-id="95dd9-114">**-q** 參數是選用的。</span><span class="sxs-lookup"><span data-stu-id="95dd9-114">The **-q** parameter is optional.</span></span>

## <a name="examples"></a><span data-ttu-id="95dd9-115">範例</span><span class="sxs-lookup"><span data-stu-id="95dd9-115">Examples</span></span>
 <span data-ttu-id="95dd9-116">在下列範例中，會以無訊息模式提交取消要求。</span><span class="sxs-lookup"><span data-stu-id="95dd9-116">In the following example, a cancel request is submitted in quiet mode.</span></span> <span data-ttu-id="95dd9-117">`localhost` 值指出控制器服務與管理工具在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="95dd9-117">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span>

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a><span data-ttu-id="95dd9-118">權限</span><span class="sxs-lookup"><span data-stu-id="95dd9-118">Permissions</span></span>
 <span data-ttu-id="95dd9-119">您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="95dd9-119">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="95dd9-120">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="95dd9-120">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="95dd9-121">如需詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="95dd9-121">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95dd9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95dd9-122">See Also</span></span>
 [<span data-ttu-id="95dd9-123">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="95dd9-123">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)


