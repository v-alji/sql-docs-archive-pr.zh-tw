---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 592c788b563046e5949217c94006de2d4755f049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697939"
---
# <a name="mssql_eng021286"></a><span data-ttu-id="15092-102">MSSQL_ENG021286</span><span class="sxs-lookup"><span data-stu-id="15092-102">MSSQL_ENG021286</span></span>
    
## <a name="message-details"></a><span data-ttu-id="15092-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="15092-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15092-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="15092-104">Product Name</span></span>|<span data-ttu-id="15092-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="15092-105">SQL Server</span></span>|  
|<span data-ttu-id="15092-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="15092-106">Event ID</span></span>|<span data-ttu-id="15092-107">21286</span><span class="sxs-lookup"><span data-stu-id="15092-107">21286</span></span>|  
|<span data-ttu-id="15092-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="15092-108">Event Source</span></span>|<span data-ttu-id="15092-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="15092-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="15092-110">元件</span><span class="sxs-lookup"><span data-stu-id="15092-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="15092-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="15092-111">Symbolic Name</span></span>||  
|<span data-ttu-id="15092-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="15092-112">Message Text</span></span>|<span data-ttu-id="15092-113">衝突資料表 '%s' 不存在。</span><span class="sxs-lookup"><span data-stu-id="15092-113">Conflict table '%s' does not exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="15092-114">說明</span><span class="sxs-lookup"><span data-stu-id="15092-114">Explanation</span></span>  
 <span data-ttu-id="15092-115">如果 [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) 中所列發行項的衝突資料表實際上不存在，則會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="15092-115">This error is raised if the conflict table for an article listed in [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) does not actually exist.</span></span> <span data-ttu-id="15092-116">嘗試為合併式複寫在已發行資料表中加入資料行，或從其中卸除資料行時，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="15092-116">The error can occur when you attempt to add a column to or drop a column from a table published for merge replication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="15092-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="15092-117">User Action</span></span>  
 <span data-ttu-id="15092-118">在遺失衝突資料表的資料庫上執行 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)，以確認資料沒有不一致的問題。</span><span class="sxs-lookup"><span data-stu-id="15092-118">Execute [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database with the missing conflict table to verify there are no data consistency issues.</span></span>  
  
 <span data-ttu-id="15092-119">如果「訂閱者」上的衝突資料表已遺漏，則卸除訂閱然後重新建立它。</span><span class="sxs-lookup"><span data-stu-id="15092-119">If the conflict table is missing on a Subscriber, drop the subscription and recreate it.</span></span> <span data-ttu-id="15092-120">如果「發行者」上的衝突資料表已遺漏，則卸除所有訂閱，卸除發行集，然後重新建立發行集和所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="15092-120">If the conflict table is missing on a Publisher, drop all subscriptions, drop the publication, and then recreate the publication and all subscriptions.</span></span> <span data-ttu-id="15092-121">如需詳細資訊，請參閱[發行資料和資料庫物件](publish/publish-data-and-database-objects.md)以及[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="15092-121">For more information, see [Publish Data and Database Objects](publish/publish-data-and-database-objects.md) and [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15092-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15092-122">See Also</span></span>  
 [<span data-ttu-id="15092-123">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="15092-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
