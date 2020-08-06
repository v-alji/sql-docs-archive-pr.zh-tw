---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbfb68575c5ffa73276b3bbe1643381c3f0cc412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709158"
---
# <a name="mssql_eng003724"></a><span data-ttu-id="c4093-102">MSSQL_ENG003724</span><span class="sxs-lookup"><span data-stu-id="c4093-102">MSSQL_ENG003724</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c4093-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4093-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4093-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c4093-104">Product Name</span></span>|<span data-ttu-id="c4093-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c4093-105">SQL Server</span></span>|  
|<span data-ttu-id="c4093-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c4093-106">Event ID</span></span>|<span data-ttu-id="c4093-107">3724</span><span class="sxs-lookup"><span data-stu-id="c4093-107">3724</span></span>|  
|<span data-ttu-id="c4093-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c4093-108">Event Source</span></span>|<span data-ttu-id="c4093-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c4093-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c4093-110">元件</span><span class="sxs-lookup"><span data-stu-id="c4093-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c4093-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c4093-111">Symbolic Name</span></span>||  
|<span data-ttu-id="c4093-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c4093-112">Message Text</span></span>|<span data-ttu-id="c4093-113">無法 %S_MSG %S_MSG '%.\*ls'，因為它正用於複寫。</span><span class="sxs-lookup"><span data-stu-id="c4093-113">Cannot %S_MSG the %S_MSG '%.\*ls' because it is being used for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c4093-114">說明</span><span class="sxs-lookup"><span data-stu-id="c4093-114">Explanation</span></span>  
 <span data-ttu-id="c4093-115">複寫資料庫中的物件時，會在系統資料表 **sysarticles** (適用快照集和交易式發行集) 或 **sysmergearticles** (適用合併發行集) 中將它們標記為已複寫。</span><span class="sxs-lookup"><span data-stu-id="c4093-115">When objects in a database are replicated, they are marked as replicated in the system table **sysarticles** (for snapshot and transactional publications) or **sysmergearticles** (for merge publications).</span></span> <span data-ttu-id="c4093-116">如果您嘗試放入已複寫物件，便會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4093-116">If you attempt drop a replicated object, this error is raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c4093-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c4093-117">User Action</span></span>  
 <span data-ttu-id="c4093-118">在放入資料庫物件之前，請先確定它並未複寫。</span><span class="sxs-lookup"><span data-stu-id="c4093-118">Ensure the database object is not replicated before attempting to drop it.</span></span> <span data-ttu-id="c4093-119">例如：</span><span class="sxs-lookup"><span data-stu-id="c4093-119">For example:</span></span>  
  
-   <span data-ttu-id="c4093-120">如果在發行集資料庫中發生錯誤，請在放入該物件之前先從發行集中放入發行項。</span><span class="sxs-lookup"><span data-stu-id="c4093-120">If the error occurs in the publication database, drop the article from the publication before dropping the object.</span></span> <span data-ttu-id="c4093-121">如需詳細資訊，請參閱[在現有發行集中新增和卸除發行項](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c4093-121">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="c4093-122">如果在訂閱資料庫中發生錯誤，請在放入該物件之前先放入訂閱。</span><span class="sxs-lookup"><span data-stu-id="c4093-122">If the error occurs in the subscription database, drop the subscription before dropping the object.</span></span> <span data-ttu-id="c4093-123">如需詳細資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c4093-123">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="c4093-124">針對交易式發行集的訂閱，可以將訂閱放入個別發行項，而非整個發行集。</span><span class="sxs-lookup"><span data-stu-id="c4093-124">For subscriptions to transactional publications, it is possible to drop the subscription to an individual article rather than the entire publication.</span></span> <span data-ttu-id="c4093-125">如需詳細資訊，請參閱 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c4093-125">For more information, see [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span>  
  
 <span data-ttu-id="c4093-126">如果在未複寫的資料庫中發生這個錯誤，請執行 [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以確保資料庫中的物件不會標示為已複寫。</span><span class="sxs-lookup"><span data-stu-id="c4093-126">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4093-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4093-127">See Also</span></span>  
 [<span data-ttu-id="c4093-128">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="c4093-128">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
