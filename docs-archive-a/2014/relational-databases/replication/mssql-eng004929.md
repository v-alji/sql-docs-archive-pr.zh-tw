---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b202b28eabe1feb1ed180bda0d58d2e84c7d10d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585312"
---
# <a name="mssql_eng004929"></a><span data-ttu-id="c2b48-102">MSSQL_ENG004929</span><span class="sxs-lookup"><span data-stu-id="c2b48-102">MSSQL_ENG004929</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c2b48-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="c2b48-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2b48-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c2b48-104">Product Name</span></span>|<span data-ttu-id="c2b48-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c2b48-105">SQL Server</span></span>|  
|<span data-ttu-id="c2b48-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c2b48-106">Event ID</span></span>|<span data-ttu-id="c2b48-107">4929</span><span class="sxs-lookup"><span data-stu-id="c2b48-107">4929</span></span>|  
|<span data-ttu-id="c2b48-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c2b48-108">Event Source</span></span>|<span data-ttu-id="c2b48-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c2b48-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c2b48-110">元件</span><span class="sxs-lookup"><span data-stu-id="c2b48-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c2b48-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c2b48-111">Symbolic Name</span></span>||  
|<span data-ttu-id="c2b48-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c2b48-112">Message Text</span></span>|<span data-ttu-id="c2b48-113">無法改變 %S_MSG '%.\*ls'，因為它正在為複寫而發行。</span><span class="sxs-lookup"><span data-stu-id="c2b48-113">Cannot alter the %S_MSG '%.\*ls' because it is being published for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c2b48-114">說明</span><span class="sxs-lookup"><span data-stu-id="c2b48-114">Explanation</span></span>  
 <span data-ttu-id="c2b48-115">這個錯誤通常是在您嘗試在針對異動複寫所發行資料表上卸除主索引鍵條件約束時發生。</span><span class="sxs-lookup"><span data-stu-id="c2b48-115">This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication.</span></span> <span data-ttu-id="c2b48-116">異動複寫的每個已發行資料表都需要主索引鍵，因此不能卸除條件約束。</span><span class="sxs-lookup"><span data-stu-id="c2b48-116">Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c2b48-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c2b48-117">User Action</span></span>  
 <span data-ttu-id="c2b48-118">若要卸除條件約束，請先卸除與資料表關聯的發行項。</span><span class="sxs-lookup"><span data-stu-id="c2b48-118">To drop the constraint, first drop the article associated with the table.</span></span> <span data-ttu-id="c2b48-119">如需詳細資訊，請參閱[在現有發行集中新增和卸除發行項](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b48-119">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span> <span data-ttu-id="c2b48-120">如果在未複寫的資料庫中發生這個錯誤，請執行 [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以確保資料庫中的物件不會標示為已複寫。</span><span class="sxs-lookup"><span data-stu-id="c2b48-120">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b48-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2b48-121">See Also</span></span>  
 [<span data-ttu-id="c2b48-122">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b48-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
