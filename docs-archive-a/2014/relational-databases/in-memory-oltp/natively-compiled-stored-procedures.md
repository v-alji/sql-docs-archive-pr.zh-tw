---
title: 原生編譯的預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8fb7a379c0c08ca357baa1042ebcf51c512c9ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706494"
---
# <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="1396a-102">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="1396a-102">Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="1396a-103">原生編譯預存程序是編譯成可存取記憶體最佳化資料表之機器碼的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1396a-103">Natively compiled stored procedures are [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures compiled to native code that access memory-optimized tables.</span></span> <span data-ttu-id="1396a-104">原生編譯預存程序提供以有效率的方式執行預存程序中的查詢與商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="1396a-104">Natively compiled stored procedures allow for efficient execution of queries and business logic in the stored procedure.</span></span> <span data-ttu-id="1396a-105">如需有關原生編譯程序的詳細資料，請參閱＜ [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1396a-105">For more details about the native compilation process, see [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md).</span></span> <span data-ttu-id="1396a-106">如需將以磁碟為基礎之預存程序移轉至原生編譯預存程序的詳細資訊，請參閱 [原生編譯預存程序的移轉問題](migration-issues-for-natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1396a-106">For more information about migrating disk-based stored procedures to natively compiled stored procedures, see [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1396a-107">解譯 (以磁碟為基礎) 的預存程序與原生編譯的預存程序之間的差異在於，解譯的預存程序是在第一次執行時編譯，而原生編譯的預存程序是在建立時編譯。</span><span class="sxs-lookup"><span data-stu-id="1396a-107">One difference between interpreted (disk-based) stored procedures and natively compiled stored procedures is that an interpreted stored procedure is compiled at first execution whereas a natively compiled stored procedure is compiled when it is created.</span></span> <span data-ttu-id="1396a-108">原生編譯的預存程序於建立時將能偵測出許多錯誤狀況 (算術溢位、類型轉換和一些除以零的狀況)，而這會造成原生編譯的預存程序建立失敗。</span><span class="sxs-lookup"><span data-stu-id="1396a-108">With natively compiled stored procedures, many error conditions (arithmetic overflow, type conversion, and some divide-by-zero conditions) can be detected at create time and will cause creation of the natively compiled stored procedure to fail.</span></span> <span data-ttu-id="1396a-109">若是解譯的預存程序，則這些錯誤狀況通常不會導致預存程序建立失敗，不過所有的執行都將失敗。</span><span class="sxs-lookup"><span data-stu-id="1396a-109">With interpreted stored procedures, these error conditions will typically not cause a failure when the stored procedure is created, but all executions will fail.</span></span>  
  
 <span data-ttu-id="1396a-110">本節主題：</span><span class="sxs-lookup"><span data-stu-id="1396a-110">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="1396a-111">建立原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="1396a-111">Creating Natively Compiled Stored Procedures</span></span>](creating-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1396a-112">不可部分完成的區塊</span><span class="sxs-lookup"><span data-stu-id="1396a-112">Atomic Blocks</span></span>](atomic-blocks-in-native-procedures.md)  
  
-   [<span data-ttu-id="1396a-113">原生編譯的預存程序中支援的建構</span><span class="sxs-lookup"><span data-stu-id="1396a-113">Supported Constructs in Natively Compiled Stored Procedures</span></span>](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="1396a-114">在原生編譯預存程序中使用 Try..Catch</span><span class="sxs-lookup"><span data-stu-id="1396a-114">Using Try..Catch in Natively Compiled Stored Procedures</span></span>](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1396a-115">原生編譯的預存程序上支援的建構</span><span class="sxs-lookup"><span data-stu-id="1396a-115">Supported Constructs on Natively Compiled Stored Procedures</span></span>](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [<span data-ttu-id="1396a-116">原生編譯的預存程序和執行 Set 選項</span><span class="sxs-lookup"><span data-stu-id="1396a-116">Natively Compiled Stored Procedures and Execution Set Options</span></span>](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [<span data-ttu-id="1396a-117">呼叫原生編譯預存程序的最佳作法</span><span class="sxs-lookup"><span data-stu-id="1396a-117">Best Practices for Calling Natively Compiled Stored Procedures</span></span>](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1396a-118">監視原生編譯預存程序的效能</span><span class="sxs-lookup"><span data-stu-id="1396a-118">Monitoring Performance of Natively Compiled Stored Procedures</span></span>](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="1396a-119">從資料存取應用程式呼叫原生編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="1396a-119">Calling Natively Compiled Stored Procedures from Data Access Applications</span></span>](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="1396a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1396a-120">See Also</span></span>  
 [<span data-ttu-id="1396a-121">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="1396a-121">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
