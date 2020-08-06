---
title: MSSQL_REPL020011 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646f25740ebb007f8d04a89690d3b712781efcc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705041"
---
# <a name="mssql_repl020011"></a><span data-ttu-id="5731f-102">MSSQL_REPL020011</span><span class="sxs-lookup"><span data-stu-id="5731f-102">MSSQL_REPL020011</span></span>
    
## <a name="message-details"></a><span data-ttu-id="5731f-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="5731f-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5731f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5731f-104">Product Name</span></span>|<span data-ttu-id="5731f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5731f-105">SQL Server</span></span>|  
|<span data-ttu-id="5731f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5731f-106">Event ID</span></span>|<span data-ttu-id="5731f-107">20011</span><span class="sxs-lookup"><span data-stu-id="5731f-107">20011</span></span>|  
|<span data-ttu-id="5731f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="5731f-108">Event Source</span></span>|<span data-ttu-id="5731f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5731f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5731f-110">元件</span><span class="sxs-lookup"><span data-stu-id="5731f-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="5731f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5731f-111">Symbolic Name</span></span>||  
|<span data-ttu-id="5731f-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5731f-112">Message Text</span></span>|<span data-ttu-id="5731f-113">該處理無法執行 '%1' (在 '%2')。</span><span class="sxs-lookup"><span data-stu-id="5731f-113">The process could not execute '%1' on '%2'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5731f-114">說明</span><span class="sxs-lookup"><span data-stu-id="5731f-114">Explanation</span></span>  
 <span data-ttu-id="5731f-115">在許多情況下，異動複寫處理期間都會出現此錯誤，例如當記錄讀取器代理程式執行 **sp_replcmds** (處理序無法在 \<ServerName> 上執行 'sp_replcmds') 或 **sp_repldone** (處理序無法在 \<ServerName> 上執行 'sp_repldone' ) 時。</span><span class="sxs-lookup"><span data-stu-id="5731f-115">This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp_replcmds** (The process could not execute 'sp_replcmds' on \<ServerName>) or **sp_repldone** (The process could not execute 'sp_repldone' on \<ServerName>).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5731f-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5731f-116">User Action</span></span>  
 <span data-ttu-id="5731f-117">如果在您剛從備份還原的資料庫中發生此錯誤，請務必按照備份與還原文件集中所述的步驟進行操作，包括執行 **sp_replrestart** (如有必要)。</span><span class="sxs-lookup"><span data-stu-id="5731f-117">If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp_replrestart** if appropriate.</span></span> <span data-ttu-id="5731f-118">如需詳細資訊，請參閱 [備份與還原快照式和異動複寫的策略](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="5731f-118">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="5731f-119">此錯誤為內部處理錯誤，如果它在還原以外的情況下出現，通常表示必須移除並重新設定複寫。</span><span class="sxs-lookup"><span data-stu-id="5731f-119">This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured.</span></span> <span data-ttu-id="5731f-120">如果您無法移除複寫，請連絡客戶支援部門尋求幫助。</span><span class="sxs-lookup"><span data-stu-id="5731f-120">If you cannot remove replication, contact customer support for assistance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5731f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5731f-121">See Also</span></span>  
 <span data-ttu-id="5731f-122">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="5731f-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="5731f-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5731f-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span></span>  
 [<span data-ttu-id="5731f-124">sp_repldone &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5731f-124">sp_repldone &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
