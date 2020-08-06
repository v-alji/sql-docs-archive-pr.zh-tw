---
title: 原生編譯的預存程序和執行 Set 選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709430"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a><span data-ttu-id="89b4e-102">原生編譯的預存程序和執行 Set 選項</span><span class="sxs-lookup"><span data-stu-id="89b4e-102">Natively Compiled Stored Procedures and Execution Set Options</span></span>
  <span data-ttu-id="89b4e-103">工作階段選項在不可部分完成的區塊內是固定的。</span><span class="sxs-lookup"><span data-stu-id="89b4e-103">Session options are fixed in atomic blocks.</span></span> <span data-ttu-id="89b4e-104">預存程序的執行不會受到工作階段的 SET 選項所影響。</span><span class="sxs-lookup"><span data-stu-id="89b4e-104">A stored procedure's execution is not affected by a session's SET options.</span></span> <span data-ttu-id="89b4e-105">不過，某些 SET 選項 (例如 SET NOEXEC 和 SET SHOWPLAN_XML) 會造成預存程序 (包括原生編譯的預存程序) 不執行。</span><span class="sxs-lookup"><span data-stu-id="89b4e-105">However, certain SET options, such as SET NOEXEC and SET SHOWPLAN_XML, cause stored procedures (including natively compiled stored procedures) to not execute.</span></span>  
  
 <span data-ttu-id="89b4e-106">已開啟任何 STATISTICS 選項執行原生編譯的預存程序時，統計資料是針對整個程序蒐集而非每個陳述式。</span><span class="sxs-lookup"><span data-stu-id="89b4e-106">When a natively compiled stored procedure is executed with any STATISTICS option turned on, statistics are gathered for the procedure as a whole and not per statement.</span></span> <span data-ttu-id="89b4e-107">如需詳細資訊，請參閱 [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql)、[SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql)、[SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) 和 [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="89b4e-107">For more information, see [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql), and [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql).</span></span> <span data-ttu-id="89b4e-108">若要在原生編譯預存程序中，取得每個陳述式層級上的執行統計資料，請在 sp_statement_completed 事件上使用擴充事件工作階段，當預存程序執行中的所有個別查詢完成時，就會開始此事件。</span><span class="sxs-lookup"><span data-stu-id="89b4e-108">To obtain execution statistics on a per-statement level in natively compiled stored procedures, use an Extended Event session on the sp_statement_completed event, which starts when each individual query in a stored procedures execution completes.</span></span> <span data-ttu-id="89b4e-109">如需建立擴充事件工作階段的詳細資訊，請參閱 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="89b4e-109">For more information on creating Extended Event sessions, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
 <span data-ttu-id="89b4e-110">原生編譯預存程序支援 `SHOWPLAN_XML`。</span><span class="sxs-lookup"><span data-stu-id="89b4e-110">`SHOWPLAN_XML` is supported for natively compiled stored procedures.</span></span> <span data-ttu-id="89b4e-111">原生編譯的預存程序不支援 `SHOWPLAN_ALL` 和 `SHOWPLAN_TEXT`。</span><span class="sxs-lookup"><span data-stu-id="89b4e-111">`SHOWPLAN_ALL` and `SHOWPLAN_TEXT` are not supported with natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="89b4e-112">原生編譯的預存程序不支援 `SET FMTONLY`。</span><span class="sxs-lookup"><span data-stu-id="89b4e-112">`SET FMTONLY` in not supported with natively compiled stored procedures.</span></span> <span data-ttu-id="89b4e-113">請改用 [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="89b4e-113">Use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b4e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b4e-114">See Also</span></span>  
 [<span data-ttu-id="89b4e-115">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="89b4e-115">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
