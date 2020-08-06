---
title: 檢視已儲存的追蹤 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b67760d575b651b089a6936adc945d74a1c62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710502"
---
# <a name="view-a-saved-trace-transact-sql"></a><span data-ttu-id="aefa4-102">檢視已儲存的追蹤 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aefa4-102">View a Saved Trace (Transact-SQL)</span></span>
  <span data-ttu-id="aefa4-103">此主題描述如何使用內建函數來檢視已儲存的追蹤。</span><span class="sxs-lookup"><span data-stu-id="aefa4-103">This topic describes how to use built-in functions to view a saved trace.</span></span>  
  
### <a name="to-view-a-specific-trace"></a><span data-ttu-id="aefa4-104">若要檢視特定追蹤</span><span class="sxs-lookup"><span data-stu-id="aefa4-104">To view a specific trace</span></span>  
  
1.  <span data-ttu-id="aefa4-105">執行 **fn_trace_getinfo** ，並指定需要其資訊的追蹤識別碼。</span><span class="sxs-lookup"><span data-stu-id="aefa4-105">Execute **fn_trace_getinfo** by specifying the ID of the trace about which information is needed.</span></span> <span data-ttu-id="aefa4-106">此函數會傳回資料表，其中列出追蹤、追蹤屬性和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="aefa4-106">This function returns a table that lists the trace, trace property, and information about the property.</span></span>  
  
     <span data-ttu-id="aefa4-107">以下列方式叫用函數：</span><span class="sxs-lookup"><span data-stu-id="aefa4-107">Invoke the function this way:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a><span data-ttu-id="aefa4-108">若要檢視現有的所有追蹤</span><span class="sxs-lookup"><span data-stu-id="aefa4-108">To view all existing traces</span></span>  
  
1.  <span data-ttu-id="aefa4-109">執行 **fn_trace_getinfo** ，並指定 `0` 或 `default`。</span><span class="sxs-lookup"><span data-stu-id="aefa4-109">Execute **fn_trace_getinfo** by specifying `0` or `default`.</span></span> <span data-ttu-id="aefa4-110">此函數會傳回資料表，其中列出所有追蹤、追蹤屬性和這些屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="aefa4-110">This function returns a table that lists all the traces, their properties, and information about these properties.</span></span>  
  
     <span data-ttu-id="aefa4-111">以下列方式叫用函數：</span><span class="sxs-lookup"><span data-stu-id="aefa4-111">Invoke the function as follows:</span></span>  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a><span data-ttu-id="aefa4-112">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="aefa4-112">.NET Framework Security</span></span>  
 <span data-ttu-id="aefa4-113">若要執行內建函數 **fn_trace_getinfo**，使用者需要下列權限：</span><span class="sxs-lookup"><span data-stu-id="aefa4-113">To run the built-in function **fn_trace_getinfo**, the user needs the following permission:</span></span>  
  
 <span data-ttu-id="aefa4-114">伺服器上的 ALTER TRACE。</span><span class="sxs-lookup"><span data-stu-id="aefa4-114">ALTER TRACE on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefa4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aefa4-115">See Also</span></span>  
 <span data-ttu-id="aefa4-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aefa4-116">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 [<span data-ttu-id="aefa4-117">使用 SQL Server Profiler 檢視和分析追蹤</span><span class="sxs-lookup"><span data-stu-id="aefa4-117">View and Analyze Traces with SQL Server Profiler</span></span>](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
