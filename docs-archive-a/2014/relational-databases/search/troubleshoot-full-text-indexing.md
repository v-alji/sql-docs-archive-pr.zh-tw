---
title: 針對全文檢索索引進行疑難排解 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eaca5fcf2dfbac57fc6d3ba6178251927d15aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606717"
---
# <a name="troubleshoot-full-text-indexing"></a><span data-ttu-id="553fd-102">疑難排解全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="553fd-102">Troubleshoot Full-Text Indexing</span></span>
     
##  <a name="troubleshoot-full-text-indexing-failures"></a><a name="failure"></a> <span data-ttu-id="553fd-103">疑難排解全文檢索索引失敗</span><span class="sxs-lookup"><span data-stu-id="553fd-103">Troubleshoot Full-Text Indexing Failures</span></span>  
 <span data-ttu-id="553fd-104">擴展或維護全文檢索索引時，全文檢索索引子可能會因為下面所描述的原因而無法對一個或多個資料列進行檢索。</span><span class="sxs-lookup"><span data-stu-id="553fd-104">While populating or maintaining a full-text index, the full-text indexer, for reasons described below, might fail to index one or more rows.</span></span> <span data-ttu-id="553fd-105">這些資料列層級錯誤不會讓母體擴展無法完成。</span><span class="sxs-lookup"><span data-stu-id="553fd-105">These row-level errors do not prevent the population from completing.</span></span> <span data-ttu-id="553fd-106">索引子會略過這些資料列，而這表示您無法查詢這些資料列中所含的內容。</span><span class="sxs-lookup"><span data-stu-id="553fd-106">The indexer skips these rows, which means that you are not able to query for content contained in these rows.</span></span>  
  
 <span data-ttu-id="553fd-107">下列情況可能會發生編製索引失敗：</span><span class="sxs-lookup"><span data-stu-id="553fd-107">Indexing failures can occur when:</span></span>  
  
-   <span data-ttu-id="553fd-108">索引子找不到或無法載入篩選或斷詞工具元件。</span><span class="sxs-lookup"><span data-stu-id="553fd-108">The indexer cannot find or load a filter or word breaker component.</span></span> <span data-ttu-id="553fd-109">如果資料表資料列包含尚未向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體註冊之某個語言的文件格式或內容，會發生此失敗。</span><span class="sxs-lookup"><span data-stu-id="553fd-109">This failure can occur if the table row contains a document format or content in a language that has not been registered with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="553fd-110">在載入已註冊的斷詞工具或篩選元件時，如果該元件尚未進行簽署或無法進行簽章驗證，也會發生此失敗。</span><span class="sxs-lookup"><span data-stu-id="553fd-110">This failure can also happen if the registered word breaker or filter component was not signed or failed signature verification when it was being loaded.</span></span>  
  
-   <span data-ttu-id="553fd-111">元件 (例如斷詞工具或篩選) 失敗，並將錯誤傳回給索引子。</span><span class="sxs-lookup"><span data-stu-id="553fd-111">A component, such as a word breaker or filter, fails and returns an error to the indexer.</span></span> <span data-ttu-id="553fd-112">如果正在進行檢索的文件損毀，且篩選無法從文件中擷取文字，則會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="553fd-112">This can happen if the document being indexed is corrupt and the filter is unable to extract text from the document.</span></span> <span data-ttu-id="553fd-113">當元件無法處理超過特定大小之單一資料列的內容時 (因全文檢索篩選背景程式主機 (fdhost.exe) 的記憶體限制)，也可能發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="553fd-113">This can also occur when a component is unable to handle the content of a single row above a certain size, due to memory limits on the full-text filter daemon host (fdhost.exe).</span></span>  
  
 <span data-ttu-id="553fd-114">搜耙記錄檔會包含每個資料列層級失敗原因的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="553fd-114">For each row-level failure, the crawl log contains details on the reason for the failure.</span></span> <span data-ttu-id="553fd-115">且會在完整或累加母體擴展結束時彙總說明錯誤計數。</span><span class="sxs-lookup"><span data-stu-id="553fd-115">The error counts are summarized at the end of a full or incremental population.</span></span>  
  
 <span data-ttu-id="553fd-116">其他失敗也會影響編製索引處理序本身，並讓母體擴展無法完成。</span><span class="sxs-lookup"><span data-stu-id="553fd-116">There are other failures that can impact the indexing process itself and prevent the population from completing:</span></span>  
  
-   <span data-ttu-id="553fd-117">全文檢索索引超出全文檢索目錄中可含之資料列數的限制。</span><span class="sxs-lookup"><span data-stu-id="553fd-117">The full-text index exceeds the limit for the number of rows that can be contained in a full-text catalog.</span></span>  
  
-   <span data-ttu-id="553fd-118">變更、捨棄或重建正在檢索之資料表上的叢集索引或全文檢索索引鍵索引。</span><span class="sxs-lookup"><span data-stu-id="553fd-118">A clustered index or full-text key index on the table being indexed gets altered, dropped, or rebuilt.</span></span>  
  
-   <span data-ttu-id="553fd-119">硬體故障或磁碟損毀導致全文檢索目錄損毀。</span><span class="sxs-lookup"><span data-stu-id="553fd-119">A hardware failure or disk corruption results in the corruption of the full-text catalog.</span></span>  
  
-   <span data-ttu-id="553fd-120">內含在進行全文檢索索引之資料表的檔案群組離線或變成唯讀。</span><span class="sxs-lookup"><span data-stu-id="553fd-120">A file group that contains the table being full-text indexed goes offline, or is made read-only.</span></span>  
  
 <span data-ttu-id="553fd-121">您應該在結束任何大量全文檢索索引母體擴展作業時，或發現母體擴展未完成時，檢視搜耙記錄檔。</span><span class="sxs-lookup"><span data-stu-id="553fd-121">You should view the crawl log at the end of any significant full-text index population operation, or when you find that a population did not complete.</span></span>  
  
### <a name="unsigned-components"></a><span data-ttu-id="553fd-122">未簽署的元件</span><span class="sxs-lookup"><span data-stu-id="553fd-122">Unsigned Components</span></span>  
 <span data-ttu-id="553fd-123">依預設，全文檢索索引子需要有它可載入以進行簽署的篩選和斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="553fd-123">By default, the full-text indexer requires the filters and word breakers that it loads to be signed.</span></span> <span data-ttu-id="553fd-124">如果這些元件未進行簽署，則有時安裝自訂元件時，您必須設定全文檢索索引子以略過簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="553fd-124">If they are not signed, which is the case sometimes when custom components are installed, you must configure the full-text indexer to ignore signature verification.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="553fd-125">略過簽章驗證會讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體變得較不安全。</span><span class="sxs-lookup"><span data-stu-id="553fd-125">Ignoring signature verification makes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] less secure.</span></span> <span data-ttu-id="553fd-126">建議您簽署任何所實作的元件，或確定所取得的任何元件都已進行簽署。</span><span class="sxs-lookup"><span data-stu-id="553fd-126">We recommend that you sign any components that you implement or ensure that any components that you acquire are signed.</span></span> <span data-ttu-id="553fd-127">如需簽署元件的資訊，請參閱 [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="553fd-127">For information about signing components, see [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  

  
##  <a name="full-text-index-in-inconsistent-state-after-transaction-log-restored"></a><a name="state"></a> <span data-ttu-id="553fd-128">全文檢索索引在還原交易記錄之後處於不一致的狀態</span><span class="sxs-lookup"><span data-stu-id="553fd-128">Full-Text Index in Inconsistent State after Transaction Log Restored</span></span>  
 <span data-ttu-id="553fd-129">當復原資料庫的交易記錄時，您會看到一個警告，指出全文檢索索引處於不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="553fd-129">When restoring the transaction log of a database, you might see a warning indicating that the full-text index is not in a consistent state.</span></span> <span data-ttu-id="553fd-130">原因是備份資料庫後，資料表的全文檢索索引已發生變更。</span><span class="sxs-lookup"><span data-stu-id="553fd-130">The reason for this is that the full-text index on a table was modified after the database was backed up.</span></span> <span data-ttu-id="553fd-131">若要讓全文檢索索引的狀態一致，您必須在資料表上執行完整母體擴展 (搜耙)。</span><span class="sxs-lookup"><span data-stu-id="553fd-131">To bring the full-text index to a consistent state, you must run a full population (crawl) on the table.</span></span> <span data-ttu-id="553fd-132">如需詳細資訊，請參閱 [擴展全文檢索索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="553fd-132">For more information, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="553fd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="553fd-133">See Also</span></span>  
 <span data-ttu-id="553fd-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="553fd-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="553fd-135">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="553fd-135">Populate Full-Text Indexes</span></span>](../indexes/indexes.md)  
  
  
