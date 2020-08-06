---
title: 設定及管理全文檢索搜尋的停用字詞與停用字詞表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 103b5024368c5ca239856580e9b45473aabf6a92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709109"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a><span data-ttu-id="bb9b6-102">設定及管理全文檢索搜尋的停用字詞與停用字詞表</span><span class="sxs-lookup"><span data-stu-id="bb9b6-102">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>
  <span data-ttu-id="bb9b6-103">為精簡全文檢索索引， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 具有一種機制，可捨棄無助於搜尋卻經常出現的字串。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-103">To prevent a full-text index from becoming bloated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a mechanism that discards commonly occurring strings that do not help the search.</span></span> <span data-ttu-id="bb9b6-104">這些捨棄的字串稱為 *「停用字詞」* (Stopword)。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-104">These discarded strings are called *stopwords*.</span></span> <span data-ttu-id="bb9b6-105">在索引建立期間，全文檢索引擎會從全文檢索索引省略停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-105">During index creation, the Full-Text Engine omits stopwords from the full-text index.</span></span> <span data-ttu-id="bb9b6-106">這代表全文檢索查詢不會搜尋停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-106">This means that full-text queries will not search on stopwords.</span></span>  
  
##  <a name="understanding-stopwords-and-stoplists"></a><a name="understand"></a><span data-ttu-id="bb9b6-107">瞭解停用字詞和字詞</span><span class="sxs-lookup"><span data-stu-id="bb9b6-107">Understanding Stopwords and Stoplists</span></span>  
 <span data-ttu-id="bb9b6-108">停用字詞表可以是具有特定語言意義的字詞，或者也可以是不具有語言意義的 *token* 。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-108">A stopword can be a word with meaning in a specific language, or it can be a *token* that does not have linguistic meaning.</span></span> <span data-ttu-id="bb9b6-109">例如，在英文中，"a"、"and"、"is" 及 "the" 等字會排除在全文檢索索引外，因為一般而言這些字都無助於搜尋。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-109">For example, in the English language, words such as "a," "and," "is," and "the" are left out of the full-text index since they are known to be useless to a search.</span></span>  
  
 <span data-ttu-id="bb9b6-110">雖然全文檢索索引會略過包含的停用字詞，但仍會考慮其位置。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-110">Although it ignores the inclusion of stopwords, the full-text index does take into account their position.</span></span> <span data-ttu-id="bb9b6-111">例如，請參考例句 "Instructions are applicable to these Adventure Works Cycles models"。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-111">For example, consider the phrase, "Instructions are applicable to these Adventure Works Cycles models".</span></span> <span data-ttu-id="bb9b6-112">下表說明這些單字在片語中的位置：</span><span class="sxs-lookup"><span data-stu-id="bb9b6-112">The following table depicts the position of the words in the phrase:</span></span>  
  
|<span data-ttu-id="bb9b6-113">Word</span><span class="sxs-lookup"><span data-stu-id="bb9b6-113">Word</span></span>|<span data-ttu-id="bb9b6-114">位置</span><span class="sxs-lookup"><span data-stu-id="bb9b6-114">Position</span></span>|  
|----------|--------------|  
|<span data-ttu-id="bb9b6-115">Instructions</span><span class="sxs-lookup"><span data-stu-id="bb9b6-115">Instructions</span></span>|<span data-ttu-id="bb9b6-116">1</span><span class="sxs-lookup"><span data-stu-id="bb9b6-116">1</span></span>|  
|<span data-ttu-id="bb9b6-117">are</span><span class="sxs-lookup"><span data-stu-id="bb9b6-117">are</span></span>|<span data-ttu-id="bb9b6-118">2</span><span class="sxs-lookup"><span data-stu-id="bb9b6-118">2</span></span>|  
|<span data-ttu-id="bb9b6-119">applicable</span><span class="sxs-lookup"><span data-stu-id="bb9b6-119">applicable</span></span>|<span data-ttu-id="bb9b6-120">3</span><span class="sxs-lookup"><span data-stu-id="bb9b6-120">3</span></span>|  
|<span data-ttu-id="bb9b6-121">to</span><span class="sxs-lookup"><span data-stu-id="bb9b6-121">to</span></span>|<span data-ttu-id="bb9b6-122">4</span><span class="sxs-lookup"><span data-stu-id="bb9b6-122">4</span></span>|  
|<span data-ttu-id="bb9b6-123">these</span><span class="sxs-lookup"><span data-stu-id="bb9b6-123">these</span></span>|<span data-ttu-id="bb9b6-124">5</span><span class="sxs-lookup"><span data-stu-id="bb9b6-124">5</span></span>|  
|<span data-ttu-id="bb9b6-125">Adventure</span><span class="sxs-lookup"><span data-stu-id="bb9b6-125">Adventure</span></span>|<span data-ttu-id="bb9b6-126">6</span><span class="sxs-lookup"><span data-stu-id="bb9b6-126">6</span></span>|  
|<span data-ttu-id="bb9b6-127">Works</span><span class="sxs-lookup"><span data-stu-id="bb9b6-127">Works</span></span>|<span data-ttu-id="bb9b6-128">7</span><span class="sxs-lookup"><span data-stu-id="bb9b6-128">7</span></span>|  
|<span data-ttu-id="bb9b6-129">Cycles</span><span class="sxs-lookup"><span data-stu-id="bb9b6-129">Cycles</span></span>|<span data-ttu-id="bb9b6-130">8</span><span class="sxs-lookup"><span data-stu-id="bb9b6-130">8</span></span>|  
|<span data-ttu-id="bb9b6-131">模型</span><span class="sxs-lookup"><span data-stu-id="bb9b6-131">models</span></span>|<span data-ttu-id="bb9b6-132">9</span><span class="sxs-lookup"><span data-stu-id="bb9b6-132">9</span></span>|  
  
 <span data-ttu-id="bb9b6-133">停用字詞 "are"、"to" 及 "these"，分別為第 2、第 4 及第 5 個字，這些文字都不會包含在全文檢索索引中。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-133">The stopwords "are", "to", and "these" that are in positions 2, 4, and 5 are left out of the full-text index.</span></span> <span data-ttu-id="bb9b6-134">但仍會保留這些文字的位置資訊，使句子中其他文字的位置不受影響。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-134">However, their positional information is maintained, thereby leaving the position of the other words in the phrase unaffected.</span></span>  
  
 <span data-ttu-id="bb9b6-135">資料庫中的停用字詞是使用稱為停用字詞表的物件來管理。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-135">Stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="bb9b6-136">停用*字*詞表是停用字詞的清單，與全文檢索索引相關聯時，會套用至該索引上的全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-136">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span>  
  
  
##  <a name="creating-a-stoplist"></a><a name="creating"></a><span data-ttu-id="bb9b6-137">建立停用字詞表</span><span class="sxs-lookup"><span data-stu-id="bb9b6-137">Creating a Stoplist</span></span>  
 <span data-ttu-id="bb9b6-138">您可以使用下列任一方式建立停用字詞表：</span><span class="sxs-lookup"><span data-stu-id="bb9b6-138">You can create a stoplist in any of the following ways:</span></span>  
  
-   <span data-ttu-id="bb9b6-139">在資料庫中使用系統提供的停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-139">Using the system-supplied stoplist in the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bb9b6-140">隨附一份系統停用字詞表，其中包含每種受支援語言的常用停用字詞，而且適用於預設與給定斷詞工具相關聯的每種語言。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-140">ships with a system stoplist that contains the most commonly used stopwords for each supported language, that is for every language that is associated with given word breakers by default.</span></span> <span data-ttu-id="bb9b6-141">此系統停用字詞表包含所有受支援語言的常見停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-141">The system stoplist contains common stopwords for all supported languages.</span></span>  <span data-ttu-id="bb9b6-142">您可以複製此系統停用字詞表，並且透過加入和移除停用字詞，自訂您的複本。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-142">You can copy the system stoplist, and customize your copy by adding and removing stopwords.</span></span>  
  
     <span data-ttu-id="bb9b6-143">系統停用字詞表是安裝在 [資源](../databases/resource-database.md) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-143">The system stoplist is installed in the [Resource](../databases/resource-database.md) database.</span></span>  
  
-   <span data-ttu-id="bb9b6-144">建立自己的停用字詞表，然後針對您指定的任何語言，在此停用字詞表中加入停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-144">Creating your own stoplist, and then adding stopwords to it for any language that you specify.</span></span> <span data-ttu-id="bb9b6-145">您也可以在必要時從停用字詞表卸除停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-145">You can also drop stopwords from your stoplist when necessary.</span></span>  
  
-   <span data-ttu-id="bb9b6-146">在目前的伺服器執行個體中使用來自任何其他資料庫的現有自訂停用字詞表，然後再視需要加入和卸除停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-146">Using an existing custom stoplist from any other database in the current server instance and then adding and dropping stopwords as necessary.</span></span>  
  
 <span data-ttu-id="bb9b6-147">**若要建立停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-147">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="bb9b6-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a><span data-ttu-id="bb9b6-149">在 Management Studio 中建立全文檢索停用字詞表</span><span class="sxs-lookup"><span data-stu-id="bb9b6-149">To create a full-text stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="bb9b6-150">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-150">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="bb9b6-151">展開 [資料庫]\*\*\*\*，然後展開含有您要建立全文檢索停用字詞表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-151">Expand **Databases**, and then expand the database in which you want to create the full-text stoplist.</span></span>  
  
3.  <span data-ttu-id="bb9b6-152">展開 [儲存體]\*\*\*\*，然後以滑鼠右鍵按一下 [全文檢索停用字詞表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-152">Expand **Storage**, and then right-click **Full-Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="bb9b6-153">選取 [新增全文檢索停用字詞表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-153">Select **New Full-Text Stoplist**.</span></span>  
  
5.  <span data-ttu-id="bb9b6-154">指定停用字詞表名稱。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-154">Specify the stoplist name.</span></span>  
  
6.  <span data-ttu-id="bb9b6-155">選擇將某個其他人指定為停用字詞表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-155">Optionally, specify someone else as the stoplist owner.</span></span>  
  
7.  <span data-ttu-id="bb9b6-156">選取下列建立停用字詞表選項的其中一個：</span><span class="sxs-lookup"><span data-stu-id="bb9b6-156">Select one of the following create stoplist options:</span></span>  
  
    -   <span data-ttu-id="bb9b6-157">**建立空的停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-157">**Create an empty stoplist**</span></span>  
  
    -   <span data-ttu-id="bb9b6-158">**從系統停用字詞表建立**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-158">**Create from the system stoplist**</span></span>  
  
    -   <span data-ttu-id="bb9b6-159">**從現有全文檢索停用字詞表建立**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-159">**Create from an existing full-text stoplist**</span></span>  
  
     <span data-ttu-id="bb9b6-160">如需詳細資訊，請參閱[新增全文檢索停用字詞表 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-160">For more information, see [New Full-Text Stoplist &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="bb9b6-161">**卸除停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-161">**To drop a stoplist**</span></span>  
  
-   [<span data-ttu-id="bb9b6-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="using-a-stoplist-in-full-text-queries"></a><a name="queries"></a><span data-ttu-id="bb9b6-163">在全文檢索查詢中使用停用字詞表</span><span class="sxs-lookup"><span data-stu-id="bb9b6-163">Using a Stoplist in Full-Text Queries</span></span>  
 <span data-ttu-id="bb9b6-164">若要在查詢中使用停用字詞表，您必須將其與全文檢索索引產生關聯。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-164">To make use of a stoplist in queries, you must associate it with a full-text index.</span></span> <span data-ttu-id="bb9b6-165">您可以在建立索引時將停用字詞表附加到全文檢索索引，也可以之後再更改索引以加入停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-165">You can attach a stoplist to a full-text index when you create the index, or you can alter the index later to add a stoplist.</span></span>  
  
 <span data-ttu-id="bb9b6-166">**建立全文檢索索引並讓停用字詞表與其產生關聯**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-166">**To create a full-text index and associate a stoplist with it**</span></span>  
  
-   [<span data-ttu-id="bb9b6-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 <span data-ttu-id="bb9b6-168">**讓停用字詞表與現有的全文檢索索引產生關聯或取消關聯**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-168">**To associate or disassociate a stoplist with an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="bb9b6-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 <span data-ttu-id="bb9b6-170">**如果停用字詞造成全文檢索查詢的布林運算失敗，則抑制錯誤訊息的顯示**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-170">**To suppress an error message if stopwords cause a Boolean operation on a full-text query to fail**</span></span>  
  
-   [<span data-ttu-id="bb9b6-171">轉換非搜尋字伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="bb9b6-171">transform noise words Server Configuration Option</span></span>](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing-stoplists-and-stoplist-metadata"></a><a name="viewing"></a><span data-ttu-id="bb9b6-172">查看字詞和停用字詞表中繼資料</span><span class="sxs-lookup"><span data-stu-id="bb9b6-172">Viewing Stoplists and Stoplist Metadata</span></span>  
 <span data-ttu-id="bb9b6-173">**檢視停用字詞表的所有停用字詞**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-173">**To view all the stopwords of a stoplist**</span></span>  
  
-   [<span data-ttu-id="bb9b6-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="bb9b6-175">**取得有關目前資料庫中所有停用字詞表的詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-175">**To get information about all the stoplists in the current database**</span></span>  
  
-   [<span data-ttu-id="bb9b6-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="bb9b6-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="bb9b6-178">**檢視斷詞工具、同義字及停用字詞表組合的 Token 化結果**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-178">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="bb9b6-179">sys.dm_fts_parser &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-179">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="changing-the-stopwords-in-a-stoplist"></a><a name="change"></a><span data-ttu-id="bb9b6-180">變更停用字詞表中的停用字詞</span><span class="sxs-lookup"><span data-stu-id="bb9b6-180">Changing the Stopwords in a Stoplist</span></span>  
 <span data-ttu-id="bb9b6-181">**在停用字詞表中加入或卸除停用字詞**</span><span class="sxs-lookup"><span data-stu-id="bb9b6-181">**To add or drop stopwords from a stoplist**</span></span>  
  
-   [<span data-ttu-id="bb9b6-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bb9b6-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a><span data-ttu-id="bb9b6-183">在 Management Studio 中變更停用字詞表中的停用字詞</span><span class="sxs-lookup"><span data-stu-id="bb9b6-183">To change the stopwords in a stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="bb9b6-184">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-184">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="bb9b6-185">展開 **[資料庫]**，然後展開此資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-185">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="bb9b6-186">展開 **[儲存體]**，然後選取 **[全文檢索停用字詞表]**。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-186">Expand **Storage**, and then select **Full Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="bb9b6-187">以滑鼠右鍵按一下要變更屬性的停用字詞表，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-187">Right-click the stoplist whose properties you want to change, and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="bb9b6-188">在 [[全文檢索停用字詞表屬性]](../../database-engine/full-text-stoplist-properties.md) 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="bb9b6-188">In the [Full-Text Stoplist Properties](../../database-engine/full-text-stoplist-properties.md) dialog box:</span></span>  
  
    1.  <span data-ttu-id="bb9b6-189">在 **[動作]** 清單方塊中，選取下列其中一個動作： **[加入停用字詞]**、 **[刪除停用字詞]**、 **[刪除所有停用字詞]** 或 **[清除停用字詞表]**。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-189">In the **Action** list box, select one of the following actions: **Add stopword**, **Delete stopword**, **Delete all stopwords**, or **Clear stoplist**.</span></span>  
  
    2.  <span data-ttu-id="bb9b6-190">如果已針對選定動作啟用 **[停用字詞]** 文字方塊，請輸入單一停用字詞。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-190">If the **Stopword** text box is enabled for the selected action, enter a single stopword.</span></span> <span data-ttu-id="bb9b6-191">這個停用字詞必須是唯一的，亦即，尚未存在您所選取之語言的這個停用字詞表中。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-191">This stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
    3.  <span data-ttu-id="bb9b6-192">如果已針對選定動作啟用 [全文檢索語言]\*\*\*\* 清單方塊，請選取語言。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-192">If the **Full-text language** list box is enabled for the selected action, select a language.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrading-noise-words-from-sql-server-2005"></a><a name="upgrade"></a><span data-ttu-id="bb9b6-193">從 SQL Server 2005 升級非搜尋字</span><span class="sxs-lookup"><span data-stu-id="bb9b6-193">Upgrading Noise Words from SQL Server 2005</span></span>  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="bb9b6-194">非搜尋字已經由停用字詞所取代。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-194">noise words have been replaced by stopwords.</span></span> <span data-ttu-id="bb9b6-195">當資料庫從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]升級時，便不再使用非搜尋字檔案。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-195">When a database is upgraded from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the noise-word files are no longer used.</span></span> <span data-ttu-id="bb9b6-196">不過，這些非搜尋字檔案會儲存在 FTDATA\ FTNoiseThesaurusBak 資料夾中，而且您之後可以在更新或建立對應的停用字詞表時使用它們。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-196">However, the noise-word files are stored in the FTDATA\ FTNoiseThesaurusBak folder, and you can use them later when updating or building the corresponding stoplists.</span></span> <span data-ttu-id="bb9b6-197">如需如何將非搜尋字檔案升級為停用字詞表的資訊，請參閱 [升級全文檢索搜尋](upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9b6-197">For information about upgrading noise-word files to stoplists, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
  
  
