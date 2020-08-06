---
title: 從執行中追蹤衍生範本 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
ms.assetid: 25a3b845-affb-4b2a-a382-198a4bdd9ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72744ce942cc49038129cf6064349e23c3e9a41d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686591"
---
# <a name="derive-a-template-from-a-running-trace-sql-server-profiler"></a><span data-ttu-id="10ab2-102">從執行中追蹤衍生範本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="10ab2-102">Derive a Template from a Running Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="10ab2-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]從現有執行中的追蹤建立追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="10ab2-103">This topic describes how to create a trace template from an existing trace while it is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-derive-a-template-from-a-running-trace"></a><span data-ttu-id="10ab2-104">若要從執行中的追蹤衍生範本</span><span class="sxs-lookup"><span data-stu-id="10ab2-104">To derive a template from a running trace</span></span>  
  
1.  <span data-ttu-id="10ab2-105">視需要切換到包含追蹤的視窗。</span><span class="sxs-lookup"><span data-stu-id="10ab2-105">If necessary, switch to the window that contains the trace.</span></span>  
  
2.  <span data-ttu-id="10ab2-106">在 **[檔案]** 功能表中指向 **[另存新檔]** ，然後按一下 **[追蹤範本]** 。</span><span class="sxs-lookup"><span data-stu-id="10ab2-106">On the **File** menu, point to **Save As**, and then click **Trace Template**.</span></span>  
  
3.  <span data-ttu-id="10ab2-107">輸入一個名稱，或者從清單中選取一個名稱。</span><span class="sxs-lookup"><span data-stu-id="10ab2-107">Type a name or select one from the list.</span></span> <span data-ttu-id="10ab2-108">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="10ab2-108">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10ab2-109">如果您選取現有的範本檔案，系統就會詢問您是否要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="10ab2-109">If you select an existing template file, you are asked if you want to overwrite the file.</span></span> <span data-ttu-id="10ab2-110">您只能夠選取使用者自訂的範本。</span><span class="sxs-lookup"><span data-stu-id="10ab2-110">You can only select a user-defined template.</span></span> <span data-ttu-id="10ab2-111">無法覆寫預先定義的系統追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="10ab2-111">Predefined system trace templates cannot be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ab2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10ab2-112">See Also</span></span>  
 <span data-ttu-id="10ab2-113">[SQL Server Profiler 範本和權限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="10ab2-113">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="10ab2-114">[建立追蹤範本 &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="10ab2-114">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="10ab2-115">[修改追蹤範本 &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="10ab2-115">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="10ab2-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="10ab2-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
