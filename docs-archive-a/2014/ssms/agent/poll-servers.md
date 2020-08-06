---
title: 輪詢伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6370e53083d2cf818e8c8b09752d49e092755a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597538"
---
# <a name="poll-servers"></a><span data-ttu-id="da4f9-102">輪詢伺服器</span><span class="sxs-lookup"><span data-stu-id="da4f9-102">Poll Servers</span></span>
  <span data-ttu-id="da4f9-103">在實作多伺服器管理時，目標伺服器會定期連絡主要伺服器，來上傳已執行作業的相關資訊，並下載新的作業。</span><span class="sxs-lookup"><span data-stu-id="da4f9-103">When multiserver administration is implemented, target servers periodically contact the master server to upload information on jobs that have been executed, and download new jobs.</span></span> <span data-ttu-id="da4f9-104">連絡主要伺服器的程序稱為「伺服器輪詢」**，它會以定期的「輪詢間隔」** 來進行。</span><span class="sxs-lookup"><span data-stu-id="da4f9-104">The process of contacting the master server is called *server polling,* which takes place at regular *polling intervals.*</span></span>  
  
## <a name="polling-intervals"></a><span data-ttu-id="da4f9-105">輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="da4f9-105">Polling Intervals</span></span>  
 <span data-ttu-id="da4f9-106">輪詢間隔 (預設值為一分鐘) 可控制目標伺服器連接到主要伺服器，以下載指示與上傳作業執行結果的頻率。</span><span class="sxs-lookup"><span data-stu-id="da4f9-106">The polling interval (one minute by default) controls how frequently the target server connects to the master server to download instructions and upload the results of job execution.</span></span>  
  
 <span data-ttu-id="da4f9-107">當目標伺服器輪詢主要伺服器時，它會從 **msdb** 資料庫中的 **sysdownloadlist** 資料表讀取指派給目標伺服器的作業。</span><span class="sxs-lookup"><span data-stu-id="da4f9-107">When a target server polls the master server, it reads the operations assigned to the target server from the **sysdownloadlist** table in the **msdb** database.</span></span> <span data-ttu-id="da4f9-108">這些作業控制了多伺服器作業與目標伺服器各種不同方面的行為。</span><span class="sxs-lookup"><span data-stu-id="da4f9-108">These operations control multiserver jobs and various aspects of the behavior of a target server.</span></span> <span data-ttu-id="da4f9-109">作業的範例包括刪除作業、插入作業、啟動作業與更新目標伺服器的輪詢時間間隔。</span><span class="sxs-lookup"><span data-stu-id="da4f9-109">Examples of operations include deleting a job, inserting a job, starting a job, and updating the polling interval of a target server.</span></span>  
  
 <span data-ttu-id="da4f9-110">作業是以下列兩種方法之一傳送到 **sysdownloadlist** 資料表：</span><span class="sxs-lookup"><span data-stu-id="da4f9-110">Operations are posted to the **sysdownloadlist** table in either of the following ways:</span></span>  
  
-   <span data-ttu-id="da4f9-111">使用 **sp_post_msx_operation** 預存程序直接傳送。</span><span class="sxs-lookup"><span data-stu-id="da4f9-111">Explicitly by using the **sp_post_msx_operation** stored procedure.</span></span>  
  
-   <span data-ttu-id="da4f9-112">使用其他的作業預存程序間接傳送。</span><span class="sxs-lookup"><span data-stu-id="da4f9-112">Implicitly by using other job stored procedures.</span></span>  
  
 <span data-ttu-id="da4f9-113">如果您使用作業預存程序來修改多伺服器作業排程或作業步驟，或使用 SQL Distributed Management Objects (SQL-DMO) 來控制多伺服器作業，請在修改多伺服器作業的步驟或排程後，發出下列命令：</span><span class="sxs-lookup"><span data-stu-id="da4f9-113">If you use job stored procedures to modify multiserver job schedules or job steps, or SQL Distributed Management Objects (SQL-DMO) to control multiserver jobs, issue the following command after modifying a multiserver job's steps or schedules:</span></span>  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="da4f9-114">發出此命令可確保同步處理目標伺服器與目前的作業定義。</span><span class="sxs-lookup"><span data-stu-id="da4f9-114">Issue this command keeps the target servers synchronized with the current job definition.</span></span>  
  
 <span data-ttu-id="da4f9-115">如果使用下列項目，則不需要直接公佈作業：</span><span class="sxs-lookup"><span data-stu-id="da4f9-115">You do not have to post operations explicitly if you use the following:</span></span>  
  
-   <span data-ttu-id="da4f9-116">可控制多伺服器作業的 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="da4f9-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to control multiserver jobs.</span></span>  
  
-   <span data-ttu-id="da4f9-117">不會修改作業排程或作業步驟的作業預存程序。</span><span class="sxs-lookup"><span data-stu-id="da4f9-117">Job stored procedures that do not modify job schedules or job steps.</span></span>  
  
 <span data-ttu-id="da4f9-118">**若要強制目標伺服器輪詢主要伺服器**</span><span class="sxs-lookup"><span data-stu-id="da4f9-118">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="da4f9-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da4f9-119">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="da4f9-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="da4f9-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="da4f9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da4f9-121">See Also</span></span>  
 [<span data-ttu-id="da4f9-122">管理事件</span><span class="sxs-lookup"><span data-stu-id="da4f9-122">Manage Events</span></span>](manage-events.md)  
  
  
