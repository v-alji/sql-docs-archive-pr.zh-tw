---
title: 備份至鏡像媒體集 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596738"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a><span data-ttu-id="860f2-102">備份至鏡像媒體集 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="860f2-102">Back Up to a Mirrored Media Set (Transact-SQL)</span></span>
  <span data-ttu-id="860f2-103">本主題描述在備份資料庫時，如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql)語句來指定鏡像媒體集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="860f2-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="860f2-104">請在 BACKUP 陳述式中，指定 TO 子句中的第一個鏡像。</span><span class="sxs-lookup"><span data-stu-id="860f2-104">In your BACKUP statement, specify the first mirror in the TO clause.</span></span> <span data-ttu-id="860f2-105">然後在鏡像自身的 MIRROR TO 子句中指定每一個鏡像。</span><span class="sxs-lookup"><span data-stu-id="860f2-105">Then, specify each mirror in its own MIRROR TO clause.</span></span> <span data-ttu-id="860f2-106">TO 和 MIRROR TO 子句都必須指定相同的備份裝置數目和類型。</span><span class="sxs-lookup"><span data-stu-id="860f2-106">The TO and MIRROR TO clauses must specify the same number and type of backup devices.</span></span>  
  
## <a name="example"></a><span data-ttu-id="860f2-107">範例</span><span class="sxs-lookup"><span data-stu-id="860f2-107">Example</span></span>  
 <span data-ttu-id="860f2-108">下列範例會建立先前圖表中所闡述的鏡像媒體集，並將 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫備份至兩個鏡像。</span><span class="sxs-lookup"><span data-stu-id="860f2-108">The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to both mirrors.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="860f2-109">相關工作</span><span class="sxs-lookup"><span data-stu-id="860f2-109">Related Tasks</span></span>  
 <span data-ttu-id="860f2-110">**從鏡像備份還原**</span><span class="sxs-lookup"><span data-stu-id="860f2-110">**To restore from a mirrored backup**</span></span>  
  
-   [<span data-ttu-id="860f2-111">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="860f2-111">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="860f2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="860f2-112">See Also</span></span>  
 <span data-ttu-id="860f2-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="860f2-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="860f2-114">鏡像備份媒體集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="860f2-114">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
