---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0b9c71ea620174f993ae87befed8a21bb3d0bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596033"
---
# <a name="mssqlserver_30089"></a><span data-ttu-id="69896-102">MSSQLSERVER_30089</span><span class="sxs-lookup"><span data-stu-id="69896-102">MSSQLSERVER_30089</span></span>
    
## <a name="details"></a><span data-ttu-id="69896-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="69896-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69896-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="69896-104">Product Name</span></span>|<span data-ttu-id="69896-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="69896-105">SQL Server</span></span>|  
|<span data-ttu-id="69896-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="69896-106">Event ID</span></span>|<span data-ttu-id="69896-107">30089</span><span class="sxs-lookup"><span data-stu-id="69896-107">30089</span></span>|  
|<span data-ttu-id="69896-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="69896-108">Event Source</span></span>|<span data-ttu-id="69896-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69896-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69896-110">元件</span><span class="sxs-lookup"><span data-stu-id="69896-110">Component</span></span>|<span data-ttu-id="69896-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="69896-111">SQLEngine</span></span>|  
|<span data-ttu-id="69896-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="69896-112">Symbolic Name</span></span>|<span data-ttu-id="69896-113">IFTS_FDHOST_TERMINATEDABNORMAL</span><span class="sxs-lookup"><span data-stu-id="69896-113">IFTS_FDHOST_TERMINATEDABNORMAL</span></span>|  
|<span data-ttu-id="69896-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="69896-114">Message Text</span></span>|<span data-ttu-id="69896-115">全文檢索篩選背景程式主機 (FDHost) 處理序已異常停止。</span><span class="sxs-lookup"><span data-stu-id="69896-115">The fulltext filter daemon host (FDHost) process has stopped abnormally.</span></span> <span data-ttu-id="69896-116">如果設定錯誤或故障的語言元件 (例如斷字工具、字幹分析器或篩選器) 在全文檢索索引或查詢處理過程中造成無法復原的錯誤，就可能發生這種錯誤。</span><span class="sxs-lookup"><span data-stu-id="69896-116">This can occur if an incorrectly configured or malfunctioning linguistic component, such as a wordbreaker, stemmer or filter has caused an irrecoverable error during full-text indexing or query processing.</span></span> <span data-ttu-id="69896-117">處理序將自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="69896-117">The process will be restarted automatically.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69896-118">說明</span><span class="sxs-lookup"><span data-stu-id="69896-118">Explanation</span></span>  
 <span data-ttu-id="69896-119">全文檢索篩選背景程式主機遇到某個強制它異常停止的問題。</span><span class="sxs-lookup"><span data-stu-id="69896-119">The full-text filter daemon host has encountered some problem that has forced it to stop abnormally.</span></span> <span data-ttu-id="69896-120">導致此問題發生的原因可能是格式不正確的文件、篩選或斷字工具中的錯誤，或篩選背景程式中的問題。</span><span class="sxs-lookup"><span data-stu-id="69896-120">The cause of the problem could be a badly formatted document, a bug in the filter or word-breaker, or a problem in filter daemon.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69896-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="69896-121">User Action</span></span>  
 <span data-ttu-id="69896-122">一般而言，背景程式會從錯誤中復原。</span><span class="sxs-lookup"><span data-stu-id="69896-122">Typically, the daemon will recover from the error.</span></span> <span data-ttu-id="69896-123">但是，如果它一直失敗，您就必須進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="69896-123">If it is consistently failing, troubleshooting is necessary.</span></span> <span data-ttu-id="69896-124">請嘗試下列步驟來隔離問題：</span><span class="sxs-lookup"><span data-stu-id="69896-124">Try the following to isolate the issue:</span></span>  
  
1.  <span data-ttu-id="69896-125">如果您最近安裝過新的語言元件，請從系統中移除該元件。</span><span class="sxs-lookup"><span data-stu-id="69896-125">If a new linguistic component has been installed recently, remove it from the system.</span></span>  
  
2.  <span data-ttu-id="69896-126">查看搜耙記錄檔，以便識別無法進行全文檢索索引的任何新文件，然後移除該文件。</span><span class="sxs-lookup"><span data-stu-id="69896-126">Look at the crawl log to identify any new document that failed to be full-text indexed, and remove it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69896-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69896-127">See Also</span></span>  
 <span data-ttu-id="69896-128">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69896-128">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="69896-129">[設定及管理搜尋的斷詞工具與字幹分析器](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="69896-129">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="69896-130">設定及管理搜尋的篩選</span><span class="sxs-lookup"><span data-stu-id="69896-130">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
