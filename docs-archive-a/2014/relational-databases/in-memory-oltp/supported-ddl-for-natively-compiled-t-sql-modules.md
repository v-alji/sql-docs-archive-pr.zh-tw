---
title: 原生編譯預存程式上支援的結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bc7e28fa2a868ac39c6adbb2dea3cc5c3ace73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594554"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a><span data-ttu-id="fc88a-102">原生編譯的預存程序上支援的建構</span><span class="sxs-lookup"><span data-stu-id="fc88a-102">Supported Constructs on Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="fc88a-103">本主題列出原生編譯預存程序所支援的建構。</span><span class="sxs-lookup"><span data-stu-id="fc88a-103">This topic lists the supported constructs on natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="fc88a-104">如需不受支援建構的相關資訊，請參閱 [記憶體中的 OLTP 不支援 Transact-SQL 建構](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="fc88a-104">For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="procedure-ddl"></a><span data-ttu-id="fc88a-105">程序 DDL</span><span class="sxs-lookup"><span data-stu-id="fc88a-105">Procedure DDL</span></span>  
 <span data-ttu-id="fc88a-106">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="fc88a-106">The following are supported:</span></span>  
  
-   <span data-ttu-id="fc88a-107">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="fc88a-107">CREATE PROCEDURE</span></span>  
  
-   <span data-ttu-id="fc88a-108">DROP PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="fc88a-108">DROP PROCEDURE</span></span>  
  
-   <span data-ttu-id="fc88a-109">SCHEMABINDING (原生編譯預存程序所需的)</span><span class="sxs-lookup"><span data-stu-id="fc88a-109">SCHEMABINDING (required for natively compiled stored procedures)</span></span>  
  
-   <span data-ttu-id="fc88a-110">NATIVE_COMPILATION</span><span class="sxs-lookup"><span data-stu-id="fc88a-110">NATIVE_COMPILATION</span></span>  
  
-   <span data-ttu-id="fc88a-111">參數可以宣告為 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="fc88a-111">Parameters can be declared as NOT NULL.</span></span>  
  
-   <span data-ttu-id="fc88a-112">資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="fc88a-112">Table-valued parameters.</span></span>  
  
## <a name="security"></a><span data-ttu-id="fc88a-113">安全性</span><span class="sxs-lookup"><span data-stu-id="fc88a-113">Security</span></span>  
 <span data-ttu-id="fc88a-114">支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="fc88a-114">The following are supported:</span></span>  
  
-   <span data-ttu-id="fc88a-115">針對程序：EXECUTE AS OWNER、SELF 和使用者。</span><span class="sxs-lookup"><span data-stu-id="fc88a-115">For procedures: EXECUTE AS OWNER, SELF, and user.</span></span>  
  
-   <span data-ttu-id="fc88a-116">資料表和程序的 GRANT 和 DENY 權限。</span><span class="sxs-lookup"><span data-stu-id="fc88a-116">GRANT and DENY permissions on tables and procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc88a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc88a-117">See Also</span></span>  
 [<span data-ttu-id="fc88a-118">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="fc88a-118">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
