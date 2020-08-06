---
title: 在連線到伺服器之後自動啟動追蹤 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2c8cae3e47a6f48014cbafe588dde782c097260
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703585"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a><span data-ttu-id="0228c-102">在連接伺服器之後自動啟動追蹤 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="0228c-102">Start a Trace Automatically after Connecting to a Server (SQL Server Profiler)</span></span>
  <span data-ttu-id="0228c-103">此主題描述如何在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]執行個體之後，自動啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="0228c-103">This topic describes how to start traces automatically after connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a><span data-ttu-id="0228c-104">若要在使用 SQL Server Profiler 連接到伺服器之後自動啟動追蹤</span><span class="sxs-lookup"><span data-stu-id="0228c-104">To start a trace automatically after connecting to a server with SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="0228c-105">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="0228c-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="0228c-106">選取 [進行連接後立即啟動追蹤] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0228c-106">Select the **Start tracing immediately after making a connection** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0228c-107">如果選取 [進行連接後立即啟動追蹤]，將不會顯示 [追蹤屬性] 對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="0228c-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="0228c-108">若要編輯追蹤屬性，您必須先關閉此設定。</span><span class="sxs-lookup"><span data-stu-id="0228c-108">To edit trace properties, you must first turn this setting off.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0228c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0228c-109">See Also</span></span>  
 [<span data-ttu-id="0228c-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0228c-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
