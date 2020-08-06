---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d6262f93ef3dbbc9834053f864046b4dca30f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596038"
---
# <a name="mssqlserver_30053"></a><span data-ttu-id="ba567-102">MSSQLSERVER_30053</span><span class="sxs-lookup"><span data-stu-id="ba567-102">MSSQLSERVER_30053</span></span>
    
## <a name="details"></a><span data-ttu-id="ba567-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ba567-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba567-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ba567-104">Product Name</span></span>|<span data-ttu-id="ba567-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ba567-105">SQL Server</span></span>|  
|<span data-ttu-id="ba567-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ba567-106">Event ID</span></span>|<span data-ttu-id="ba567-107">30053</span><span class="sxs-lookup"><span data-stu-id="ba567-107">30053</span></span>|  
|<span data-ttu-id="ba567-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ba567-108">Event Source</span></span>|<span data-ttu-id="ba567-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ba567-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ba567-110">元件</span><span class="sxs-lookup"><span data-stu-id="ba567-110">Component</span></span>|<span data-ttu-id="ba567-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ba567-111">SQLEngine</span></span>|  
|<span data-ttu-id="ba567-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ba567-112">Symbolic Name</span></span>|<span data-ttu-id="ba567-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba567-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span></span>|  
|<span data-ttu-id="ba567-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ba567-114">Message Text</span></span>|<span data-ttu-id="ba567-115">全文檢索查詢字串的斷詞工作逾時。</span><span class="sxs-lookup"><span data-stu-id="ba567-115">Word breaking timed out for the full-text query string.</span></span> <span data-ttu-id="ba567-116">如果斷詞工具處理全文檢索查詢字串的時間太長，或伺服器上有大量查詢正在執行，就可能發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba567-116">This can happen if the wordbreaker took a long time to process the full-text query string, or if a large number of queries are running on the server.</span></span> <span data-ttu-id="ba567-117">請嘗試在負載較輕時再執行一次查詢。</span><span class="sxs-lookup"><span data-stu-id="ba567-117">Try running the query again under a lighter load.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ba567-118">說明</span><span class="sxs-lookup"><span data-stu-id="ba567-118">Explanation</span></span>  
 <span data-ttu-id="ba567-119">斷詞逾時錯誤可能會在下列情況中發生：</span><span class="sxs-lookup"><span data-stu-id="ba567-119">A word-breaking timeout error can occur in the following situations:</span></span>  
  
-   <span data-ttu-id="ba567-120">查詢語言的斷詞工具設定不正確。例如，其登錄設定不正確。</span><span class="sxs-lookup"><span data-stu-id="ba567-120">The word breaker for the query language is configured incorrectly; for example, its registry settings are incorrect.</span></span>  
  
-   <span data-ttu-id="ba567-121">斷詞工具由於特定的查詢字串而無法運作。</span><span class="sxs-lookup"><span data-stu-id="ba567-121">The word breaker malfunctions for a specific query string.</span></span>  
  
-   <span data-ttu-id="ba567-122">斷詞工具針對特定的查詢字串傳回太多資料。</span><span class="sxs-lookup"><span data-stu-id="ba567-122">The word breaker returns too much data for a specific query string.</span></span> <span data-ttu-id="ba567-123">資料過多會被系統視為可能的緩衝區滿溢攻擊，因而關閉主控斷詞服務的篩選背景程式處理序 (fdhost.exe)。</span><span class="sxs-lookup"><span data-stu-id="ba567-123">Excess data is treated as a potential buffer overrun attack, and shuts down the filter daemon process (fdhost.exe), which hosts the word-breaking services.</span></span>  
  
-   <span data-ttu-id="ba567-124">篩選背景程式處理序的組態不正確。</span><span class="sxs-lookup"><span data-stu-id="ba567-124">The filter daemon process configuration is incorrect.</span></span>  
  
     <span data-ttu-id="ba567-125">最常見的組態問題是密碼逾期或讓篩選背景程式帳戶無法登入的網域原則。</span><span class="sxs-lookup"><span data-stu-id="ba567-125">The most common configuration problems are password expiration or a domain policy that prevents the filter daemon account from logging on.</span></span>  
  
-   <span data-ttu-id="ba567-126">伺服器執行個體正在執行非常繁重的查詢工作負載。例如，斷詞工具處理全文檢索查詢字串的時間太長，或伺服器上有大量查詢正在執行。</span><span class="sxs-lookup"><span data-stu-id="ba567-126">A very heavy query workload is running on the server instance; for example, the word-breaker took a long time to process the full-text query string, or a large number of queries are running on the server.</span></span> <span data-ttu-id="ba567-127">請注意，這是可能性最低的原因。</span><span class="sxs-lookup"><span data-stu-id="ba567-127">Note that this is the least likely cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ba567-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ba567-128">User Action</span></span>  
 <span data-ttu-id="ba567-129">請選取適用於逾時可能原因的使用者動作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ba567-129">Select the user action that is appropriate to the probable cause of the timeout, as follows:</span></span>  
  
|<span data-ttu-id="ba567-130">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ba567-130">Probable cause</span></span>|<span data-ttu-id="ba567-131">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ba567-131">User action</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ba567-132">查詢語言的斷詞工具設定不正確。</span><span class="sxs-lookup"><span data-stu-id="ba567-132">The word breaker for the query language is configured incorrectly.</span></span>|<span data-ttu-id="ba567-133">如果您正在使用協力廠商斷詞工具，可能是作業系統的註冊不正確。</span><span class="sxs-lookup"><span data-stu-id="ba567-133">If you are using a third-party word breaker it might be incorrectly registered with the operating system.</span></span> <span data-ttu-id="ba567-134">在此情況下，請重新註冊斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="ba567-134">In this case, re-register the word breaker.</span></span> <span data-ttu-id="ba567-135">如需詳細資訊，請參閱[將搜索所使用的斷詞工具還原為舊版](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)。</span><span class="sxs-lookup"><span data-stu-id="ba567-135">For more information, see [Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).</span></span>|  
|<span data-ttu-id="ba567-136">斷詞工具由於特定的查詢字串而無法運作。</span><span class="sxs-lookup"><span data-stu-id="ba567-136">The word breaker malfunctions for a specific query string.</span></span>|<span data-ttu-id="ba567-137">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援斷詞工具，請連絡 Microsoft 客戶服務及支援中心。</span><span class="sxs-lookup"><span data-stu-id="ba567-137">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="ba567-138">斷詞工具針對特定的查詢字串傳回太多資料。</span><span class="sxs-lookup"><span data-stu-id="ba567-138">The word breaker returns too much data for a specific query string.</span></span>|<span data-ttu-id="ba567-139">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援斷詞工具，請連絡 Microsoft 客戶服務及支援中心。</span><span class="sxs-lookup"><span data-stu-id="ba567-139">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="ba567-140">篩選背景程式處理序的組態不正確。</span><span class="sxs-lookup"><span data-stu-id="ba567-140">The filter daemon process configuration is incorrect.</span></span>|<span data-ttu-id="ba567-141">請確定您使用最新的密碼，而且網域原則並未讓篩選背景程式帳戶無法登入。</span><span class="sxs-lookup"><span data-stu-id="ba567-141">Ensure that you are using the current password and that a domain policy is not preventing the filter daemon account from logging on.</span></span>|  
|<span data-ttu-id="ba567-142">伺服器執行個體正在執行非常繁重的查詢工作負載。</span><span class="sxs-lookup"><span data-stu-id="ba567-142">A very heavy query workload is running on the server instance.</span></span>|<span data-ttu-id="ba567-143">請嘗試在負載較輕時再執行一次查詢。</span><span class="sxs-lookup"><span data-stu-id="ba567-143">Try running the query again under a lighter load.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba567-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba567-144">See Also</span></span>  
 <span data-ttu-id="ba567-145">[設定全文檢索篩選背景程式啟動器的服務帳戶](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="ba567-145">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="ba567-146">[全文檢索搜尋](../search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="ba567-146">[Full-Text Search](../search/full-text-search.md) </span></span>  
 <span data-ttu-id="ba567-147">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba567-147">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="ba567-148">[設定及管理搜尋的斷詞工具與字幹分析器](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="ba567-148">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="ba567-149">設定及管理搜尋的篩選</span><span class="sxs-lookup"><span data-stu-id="ba567-149">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
