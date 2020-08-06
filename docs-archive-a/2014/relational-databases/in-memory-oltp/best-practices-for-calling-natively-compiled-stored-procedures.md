---
title: 呼叫原生編譯預存程序的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d07d0e290d1fbd9b324235e64734a399bf7801d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592005"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a><span data-ttu-id="18a08-102">呼叫原生編譯預存程序的最佳作法</span><span class="sxs-lookup"><span data-stu-id="18a08-102">Best Practices for Calling Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="18a08-103">原生編譯預存程序：</span><span class="sxs-lookup"><span data-stu-id="18a08-103">Natively compiled stored procedures are:</span></span>  
  
-   <span data-ttu-id="18a08-104">通常用於應用程式的關鍵性效能組件中。</span><span class="sxs-lookup"><span data-stu-id="18a08-104">Used typically in performance-critical parts of an application.</span></span>  
  
-   <span data-ttu-id="18a08-105">經常執行。</span><span class="sxs-lookup"><span data-stu-id="18a08-105">Frequently executed.</span></span>  
  
-   <span data-ttu-id="18a08-106">預期非常快速。</span><span class="sxs-lookup"><span data-stu-id="18a08-106">Expected to be very fast.</span></span>  
  
 <span data-ttu-id="18a08-107">使用原生編譯預存程序的效能優勢，會隨程序所處理的資料列數目和邏輯數量增多而提升。</span><span class="sxs-lookup"><span data-stu-id="18a08-107">The performance benefit of using a natively compiled stored procedure increases with the number of rows and the amount of logic that is processed by the procedure.</span></span> <span data-ttu-id="18a08-108">例如，如果原生編譯預存程序使用下列一個或多個項目，則會展現更佳的效能：</span><span class="sxs-lookup"><span data-stu-id="18a08-108">For example, a natively compiled stored procedure will exhibit better performance if it uses one or more of the following:</span></span>  
  
-   <span data-ttu-id="18a08-109">彙總：</span><span class="sxs-lookup"><span data-stu-id="18a08-109">Aggregation.</span></span>  
  
-   <span data-ttu-id="18a08-110">巢狀迴圈聯結。</span><span class="sxs-lookup"><span data-stu-id="18a08-110">Nested-loops joins.</span></span>  
  
-   <span data-ttu-id="18a08-111">多重陳述式選取、插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="18a08-111">Multi-statement select, insert, update, and delete operations.</span></span>  
  
-   <span data-ttu-id="18a08-112">複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="18a08-112">Complex expressions.</span></span>  
  
-   <span data-ttu-id="18a08-113">程序邏輯，例如條件陳述式和迴圈。</span><span class="sxs-lookup"><span data-stu-id="18a08-113">Procedural logic, such as conditional statements and loops.</span></span>  
  
 <span data-ttu-id="18a08-114">如果您只需要處理一個資料列，使用原生編譯預存程序可能不會提供效能優勢。</span><span class="sxs-lookup"><span data-stu-id="18a08-114">If you need to process only a single row, using a natively compiled stored procedure may not provide a performance benefit.</span></span>  
  
 <span data-ttu-id="18a08-115">若要避免伺服器必須對應參數名稱和轉換類型：</span><span class="sxs-lookup"><span data-stu-id="18a08-115">To avoid the server having to map parameter names and convert types:</span></span>  
  
-   <span data-ttu-id="18a08-116">讓傳遞至程序的參數類型與程序定義中的類型相符。</span><span class="sxs-lookup"><span data-stu-id="18a08-116">Match the types of the parameters passed to the procedure with the types in the procedure definition.</span></span>  
  
-   <span data-ttu-id="18a08-117">當呼叫原生編譯預存程序時，請使用序數 (無名) 參數。</span><span class="sxs-lookup"><span data-stu-id="18a08-117">Use ordinal (nameless) parameters when calling natively compiled stored procedures.</span></span> <span data-ttu-id="18a08-118">若要以最有效率方式執行，請勿使用具名參數。</span><span class="sxs-lookup"><span data-stu-id="18a08-118">For the most efficient execution, do not use named parameters.</span></span>  
  
 <span data-ttu-id="18a08-119">透過 XEvent `hekaton_slow_parameter_passing` 與 `reason=named_parameters`，可偵測到 (無效率的) 具名參數與原生編譯預存程序的使用方式。</span><span class="sxs-lookup"><span data-stu-id="18a08-119">Use of (inefficient) named parameters with natively compiled stored procedures can be detected through the XEvent `hekaton_slow_parameter_passing`, with `reason=named_parameters`.</span></span>  
  
 <span data-ttu-id="18a08-120">同樣地，您可以透過相同的 XEvent `hekaton_slow_parameter_passing` 與 `reason=parameter_conversion`，偵測到不相符類型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="18a08-120">Similarly, you can detect use of mismatched types through the same XEvent `hekaton_slow_parameter_passing`, with `reason=parameter_conversion`.</span></span>  
  
 <span data-ttu-id="18a08-121">因為在使用記憶體最佳化資料表時必須實作重試邏輯 (在許多案例中)，而且因為您必須避開某些功能限制，所以您可能會想要建立包裝函式解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。</span><span class="sxs-lookup"><span data-stu-id="18a08-121">Because you will need to implement retry logic when using memory-optimized tables (in many scenarios), and because you will need to work around certain feature limitations, you may want to create a wrapper interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.</span></span> <span data-ttu-id="18a08-122">如需範例，請參閱[記憶體優化資料表上交易的重試邏輯方針](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="18a08-122">For an example, see [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a08-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a08-123">See Also</span></span>  
 [<span data-ttu-id="18a08-124">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="18a08-124">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
