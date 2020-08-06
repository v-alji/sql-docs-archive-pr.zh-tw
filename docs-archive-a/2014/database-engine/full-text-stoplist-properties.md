---
title: 全文檢索停用字詞表屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607035"
---
# <a name="full-text-stoplist-properties"></a><span data-ttu-id="8403c-102">全文檢索停用字詞表屬性</span><span class="sxs-lookup"><span data-stu-id="8403c-102">Full-Text Stoplist Properties</span></span>
  <span data-ttu-id="8403c-103">使用此對話方塊可加入或刪除個別停用字詞、刪除特定語言的所有停用字詞，或是清除目前的停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="8403c-103">Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist.</span></span> <span data-ttu-id="8403c-104">停用字詞是停用字詞表內所包含的常用字。</span><span class="sxs-lookup"><span data-stu-id="8403c-104">A stopword is a commonly used word that is included in a stoplist.</span></span> <span data-ttu-id="8403c-105">使用某停用字詞表之資料表的全文檢索索引中會省略該停用字詞表內的停用字詞。</span><span class="sxs-lookup"><span data-stu-id="8403c-105">The stopwords in a stoplist are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="8403c-106">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="8403c-106">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="8403c-107">**使用 SQL Server Management Studio 變更停用字詞表屬性**</span><span class="sxs-lookup"><span data-stu-id="8403c-107">**To use SQL Server Management Studio to change stoplist properties**</span></span>  
  
-   [<span data-ttu-id="8403c-108">設定及管理全文檢索搜尋的停用字詞與停用字詞表</span><span class="sxs-lookup"><span data-stu-id="8403c-108">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="8403c-109">選項</span><span class="sxs-lookup"><span data-stu-id="8403c-109">Options</span></span>  
 <span data-ttu-id="8403c-110">**動作**</span><span class="sxs-lookup"><span data-stu-id="8403c-110">**Action**</span></span>  
 <span data-ttu-id="8403c-111">指定您要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8403c-111">Specifies the action that you want to perform.</span></span>  
  
 <span data-ttu-id="8403c-112">**加入停用字詞**</span><span class="sxs-lookup"><span data-stu-id="8403c-112">**Add stopword**</span></span>  
 <span data-ttu-id="8403c-113">將常用字加入停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="8403c-113">Add a commonly used word to the stoplist.</span></span>  
  
 <span data-ttu-id="8403c-114">**刪除停用字詞**</span><span class="sxs-lookup"><span data-stu-id="8403c-114">**Delete stopword**</span></span>  
 <span data-ttu-id="8403c-115">從停用字詞表中刪除停用字詞。</span><span class="sxs-lookup"><span data-stu-id="8403c-115">Delete a stopword from the stoplist.</span></span>  
  
 <span data-ttu-id="8403c-116">**刪除所有停用字詞**</span><span class="sxs-lookup"><span data-stu-id="8403c-116">**Delete all stopwords**</span></span>  
 <span data-ttu-id="8403c-117">刪除特定語言的所有停用字詞。</span><span class="sxs-lookup"><span data-stu-id="8403c-117">Delete all the stopwords for a specific language.</span></span>  
  
 <span data-ttu-id="8403c-118">**清除停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="8403c-118">**Clear stoplist**</span></span>  
 <span data-ttu-id="8403c-119">刪除所有語言的所有停用字詞來清除停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="8403c-119">Clear the stoplist by deleting all the stopwords for all languages.</span></span>  
  
 <span data-ttu-id="8403c-120">**停用字詞**</span><span class="sxs-lookup"><span data-stu-id="8403c-120">**Stopword**</span></span>  
 <span data-ttu-id="8403c-121">如果您已選取 **[加入停用字詞]** 或 **[刪除停用字詞]**，請在 **[停用字詞]** 欄位中輸入停用字詞。</span><span class="sxs-lookup"><span data-stu-id="8403c-121">If you selected **Add stopword** or **Delete stopword**, enter the stopword in the **Stopword** field.</span></span> <span data-ttu-id="8403c-122">新的停用字詞必須是唯一的，亦即，尚未存在您所選取之語言的這個停用字詞表中。</span><span class="sxs-lookup"><span data-stu-id="8403c-122">A new stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
 <span data-ttu-id="8403c-123">**全文檢索語言**</span><span class="sxs-lookup"><span data-stu-id="8403c-123">**Full-text language**</span></span>  
 <span data-ttu-id="8403c-124">如果您已選取 **[加入停用字詞]**、 **[刪除停用字詞]** 或 **[刪除所有停用字詞]**，請從清單方塊中選取停用字詞的語言。</span><span class="sxs-lookup"><span data-stu-id="8403c-124">If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box.</span></span> <span data-ttu-id="8403c-125">這樣會列出伺服器執行個體支援的所有全文檢索語言。</span><span class="sxs-lookup"><span data-stu-id="8403c-125">This lists all the full-text languages that are supported by the server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8403c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8403c-126">See Also</span></span>  
 <span data-ttu-id="8403c-127">[sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8403c-127">[sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span></span>  
 <span data-ttu-id="8403c-128">[sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8403c-128">[sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span></span>  
 <span data-ttu-id="8403c-129">[設定及管理全文檢索搜尋的停用字詞與停用字詞表](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="8403c-129">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="8403c-130">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8403c-130">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="8403c-131">[建立全文檢索停用字詞表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8403c-131">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 [<span data-ttu-id="8403c-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8403c-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
