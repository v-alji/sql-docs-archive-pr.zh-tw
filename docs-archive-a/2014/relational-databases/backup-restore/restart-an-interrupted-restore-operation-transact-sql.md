---
title: 重新啟動中斷的還原作業 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6fa09ce66865d61c8f3a86feedc04eaf8deec2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686992"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a><span data-ttu-id="af0e2-102">重新啟動中斷的還原作業 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="af0e2-102">Restart an Interrupted Restore Operation (Transact-SQL)</span></span>
  <span data-ttu-id="af0e2-103">此主題說明如何重新啟動被中斷的還原作業。</span><span class="sxs-lookup"><span data-stu-id="af0e2-103">This topic explains how to restart an interrupted restore operation.</span></span>  
  
### <a name="to-restart-an-interrupted-restore-operation"></a><span data-ttu-id="af0e2-104">若要重新啟動被中斷的還原作業</span><span class="sxs-lookup"><span data-stu-id="af0e2-104">To restart an interrupted restore operation</span></span>  
  
1.  <span data-ttu-id="af0e2-105">再執行一次被中斷的 RESTORE 陳述式，並指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="af0e2-105">Execute the interrupted RESTORE statement again, specifying:</span></span>  
  
    -   <span data-ttu-id="af0e2-106">與原始 RESTORE 陳述式相同的子句。</span><span class="sxs-lookup"><span data-stu-id="af0e2-106">The same clauses used in the original RESTORE statement.</span></span>  
  
    -   <span data-ttu-id="af0e2-107">RESTART 子句。</span><span class="sxs-lookup"><span data-stu-id="af0e2-107">The RESTART clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af0e2-108">範例</span><span class="sxs-lookup"><span data-stu-id="af0e2-108">Example</span></span>  
 <span data-ttu-id="af0e2-109">此範例會重新啟動被中斷的還原作業。</span><span class="sxs-lookup"><span data-stu-id="af0e2-109">This example restarts an interrupted restore operation.</span></span>  
  
```sql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="af0e2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0e2-110">See Also</span></span>  
 <span data-ttu-id="af0e2-111">[完整資料庫還原 &#40;完整復原模式&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="af0e2-111">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="af0e2-112">[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="af0e2-112">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="af0e2-113">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af0e2-113">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
