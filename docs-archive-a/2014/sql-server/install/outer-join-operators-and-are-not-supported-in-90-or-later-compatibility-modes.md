---
title: 90或更新版本的相容性模式中不支援外部聯結運算子 *= 和 =* |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 357c729e6d53cc17f2e4c169dd66613b6cfd2f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704718"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a><span data-ttu-id="4830d-102">在 90 (含) 之後的相容性模式中不支援外部聯結運算 \*= 和 =\*</span><span class="sxs-lookup"><span data-stu-id="4830d-102">Outer join operators \*= and =\* are not supported in 90 or later compatibility modes</span></span>
  <span data-ttu-id="4830d-103">Upgrade Advisor 偵測到使用外部聯結運算子 \* = 和 = \* 。</span><span class="sxs-lookup"><span data-stu-id="4830d-103">Upgrade Advisor detected the use of outer join operators \*= and =\*.</span></span> <span data-ttu-id="4830d-104">在 90 或之後的相容性模式中並不支援這些運算子。</span><span class="sxs-lookup"><span data-stu-id="4830d-104">These operators are not supported in 90 or later compatibility modes.</span></span> <span data-ttu-id="4830d-105">當您升級時，使用者資料庫會維持其相容性模式。</span><span class="sxs-lookup"><span data-stu-id="4830d-105">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="4830d-106">使用這些運算子的陳述式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="4830d-106">Statements that use these operators will fail.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4830d-107">元件</span><span class="sxs-lookup"><span data-stu-id="4830d-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="4830d-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="4830d-108">Corrective Action</span></span>  
 <span data-ttu-id="4830d-109">在您將資料庫相容性模式變更為90或更新版本之前，請修改使用外部聯結運算子 \* = 和 = 的語句， \* 以使用對等的外部聯結關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4830d-109">Before you change the database compatibility mode to 90 or later, modify statements that use the outer join operators \*= and =\* to use equivalent OUTER JOIN keywords.</span></span> <span data-ttu-id="4830d-110">下列範例會顯示使用 `\*=` 運算子的查詢以及使用 `LEFT OUTER JOIN` 關鍵字的對等查詢。</span><span class="sxs-lookup"><span data-stu-id="4830d-110">The following example shows a query that uses the `\*=` operator and an equivalent query that uses the `LEFT OUTER JOIN` keywords.</span></span>  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 <span data-ttu-id="4830d-111">如需有關外部聯結的詳細資訊，請參閱《SQL Server 線上叢書》中的＜使用外部聯結＞。</span><span class="sxs-lookup"><span data-stu-id="4830d-111">For more information about outer joins, see "Using Outer Joins" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4830d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4830d-112">See Also</span></span>  
 <span data-ttu-id="4830d-113">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4830d-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4830d-114">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="4830d-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
