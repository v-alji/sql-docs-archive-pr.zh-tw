---
title: 重新執行 Transact-SQL 指令碼 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5abf22a1201ac927f12ef9e4cfdd1f6d3026d00a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705741"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a><span data-ttu-id="814fd-102">重新執行 Transact-SQL 指令碼 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="814fd-102">Replay a Transact-SQL Script (SQL Server Profiler)</span></span>
  <span data-ttu-id="814fd-103">當測試效能問題的可能方案時，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來重新執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，並比較變更前後的效能。</span><span class="sxs-lookup"><span data-stu-id="814fd-103">When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, and compare performance before and after your changes.</span></span>  
  
### <a name="to-replay-a-transact-sql-script"></a><span data-ttu-id="814fd-104">若要重新執行 Transact-SQL 指令碼</span><span class="sxs-lookup"><span data-stu-id="814fd-104">To replay a Transact-SQL script</span></span>  
  
1.  <span data-ttu-id="814fd-105">在 [檔案]  功能表上，指向 [開啟]  ，然後按一下 [指令碼檔案]  。</span><span class="sxs-lookup"><span data-stu-id="814fd-105">On the **File** menu, point to **Open**, and then click **Script File**.</span></span>  
  
2.  <span data-ttu-id="814fd-106">選取您要開啟的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="814fd-106">Select the [!INCLUDE[tsql](../../includes/tsql-md.md)] script file you want to open.</span></span> <span data-ttu-id="814fd-107">確定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼包含重新執行所需的事件。</span><span class="sxs-lookup"><span data-stu-id="814fd-107">Make sure that the [!INCLUDE[tsql](../../includes/tsql-md.md)] script contains events necessary for replay.</span></span> <span data-ttu-id="814fd-108">如需詳細資訊，請參閱 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="814fd-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
3.  <span data-ttu-id="814fd-109">在 [重新執行]  功能表上，按一下 [啟動]  ，然後連接到您要重新執行指令碼的伺服器。</span><span class="sxs-lookup"><span data-stu-id="814fd-109">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.</span></span>  
  
4.  <span data-ttu-id="814fd-110">在 **[重新執行組態]** 對話方塊中確認設定，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="814fd-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814fd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="814fd-111">See Also</span></span>  
 <span data-ttu-id="814fd-112">[重新執行追蹤](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="814fd-112">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="814fd-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="814fd-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
