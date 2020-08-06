---
title: 新的全文檢索停用字詞表 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: rothja
ms.author: jroth
ms.openlocfilehash: a6272fb570b85989f38c8187e29712966862710d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599669"
---
# <a name="new-full-text-stoplist-general-page"></a><span data-ttu-id="88480-102">新增全文檢索停用字詞表 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="88480-102">New Full-Text Stoplist (General Page)</span></span>
  <span data-ttu-id="88480-103">使用這個對話方塊，即可建立全文檢索停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="88480-103">Use this dialog box to create a full-text stoplist.</span></span> <span data-ttu-id="88480-104">*「停用字詞表」* (Stoplist) 是指一組稱為 *「停用字詞」*(Stopword) 的常用字，而使用該停用字詞表之資料表的全文檢索索引會省略這些字。</span><span class="sxs-lookup"><span data-stu-id="88480-104">A *stoplist* is a set of commonly used words, called *stopwords*, that are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="88480-105">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="88480-105">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="88480-106">**使用 SQL Server Management Studio 來建立停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="88480-106">**To use SQL Server Management Studio to create a stoplist**</span></span>  
  
-   [<span data-ttu-id="88480-107">設定及管理全文檢索搜尋的停用字詞與停用字詞表</span><span class="sxs-lookup"><span data-stu-id="88480-107">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="88480-108">選項</span><span class="sxs-lookup"><span data-stu-id="88480-108">Options</span></span>  
 <span data-ttu-id="88480-109">**全文檢索停用字詞表名稱**</span><span class="sxs-lookup"><span data-stu-id="88480-109">**Full-text stoplist name**</span></span>  
 <span data-ttu-id="88480-110">輸入全文檢索停用字詞表的名稱。</span><span class="sxs-lookup"><span data-stu-id="88480-110">Enter the name of the full-text stoplist.</span></span>  
  
 <span data-ttu-id="88480-111">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="88480-111">**Owner**</span></span>  
 <span data-ttu-id="88480-112">指定全文檢索停用字詞表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="88480-112">Specify the owner of the full-text stoplist.</span></span> <span data-ttu-id="88480-113">如果您想要將擁有權指派給自己 (亦即，目前的使用者)，請將這個欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="88480-113">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span>  
  
 <span data-ttu-id="88480-114">若要指定不同的使用者，請按一下瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="88480-114">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-stoplist-options"></a><span data-ttu-id="88480-115">建立停用字詞表選項</span><span class="sxs-lookup"><span data-stu-id="88480-115">Create stoplist options</span></span>  
 <span data-ttu-id="88480-116">按一下下列其中一個建立選項：</span><span class="sxs-lookup"><span data-stu-id="88480-116">Click one of the following create options:</span></span>  
  
 <span data-ttu-id="88480-117">**建立空的停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="88480-117">**Create an empty stoplist**</span></span>  
 <span data-ttu-id="88480-118">新的停用字詞表將不會包含任何停用字詞。</span><span class="sxs-lookup"><span data-stu-id="88480-118">The new stoplist will not contain any stopwords.</span></span>  
  
 <span data-ttu-id="88480-119">**從系統停用字詞表建立**</span><span class="sxs-lookup"><span data-stu-id="88480-119">**Create from the system stoplist**</span></span>  
 <span data-ttu-id="88480-120">新的停用字詞表是從預設存在於 [Resource 資料庫](../relational-databases/databases/resource-database.md)中的停用字詞表所建立。</span><span class="sxs-lookup"><span data-stu-id="88480-120">The new stoplist is created from the stoplist that exists by default in the [Resource database](../relational-databases/databases/resource-database.md).</span></span>  
  
 <span data-ttu-id="88480-121">**從現有全文檢索停用字詞表建立**</span><span class="sxs-lookup"><span data-stu-id="88480-121">**Create from an existing full-text stoplist**</span></span>  
 <span data-ttu-id="88480-122">新的停用字詞表是藉由複製現有的停用字詞表所建立。</span><span class="sxs-lookup"><span data-stu-id="88480-122">The new stoplist is created by copying an existing stoplist.</span></span>  
  
 <span data-ttu-id="88480-123">**源資料庫**</span><span class="sxs-lookup"><span data-stu-id="88480-123">**Source database**</span></span>  
 <span data-ttu-id="88480-124">指定現有停用字詞表所屬的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="88480-124">Specifies the name of the database to which the existing stoplist belongs.</span></span> <span data-ttu-id="88480-125">系統預設會選取目前的資料庫。</span><span class="sxs-lookup"><span data-stu-id="88480-125">The current database is selected by default.</span></span> <span data-ttu-id="88480-126">(選擇性) 請從清單方塊中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="88480-126">Optionally, select a different database from the list box.</span></span>  
  
 <span data-ttu-id="88480-127">**來源停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="88480-127">**Source stoplist**</span></span>  
 <span data-ttu-id="88480-128">指定現有停用字詞表的名稱。</span><span class="sxs-lookup"><span data-stu-id="88480-128">Specifies the name of an existing stoplist.</span></span> <span data-ttu-id="88480-129">從可用停用字詞表的清單中，選取要當做來源使用的停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="88480-129">From the list of available stoplists, select the one to use as the source.</span></span> <span data-ttu-id="88480-130">可用的停用字詞表會按照它們顯示在 [物件總管] 中的順序列出。</span><span class="sxs-lookup"><span data-stu-id="88480-130">The available stoplists are listed in the order in which they appear in Object Explorer.</span></span>  
  
 <span data-ttu-id="88480-131">如果來源停用字詞表中停用字詞內指定的任何語言未在目前資料庫中註冊，則 CREATE FULLTEXT STOPLIST 會成功，但是會傳回警告，而且不會加入對應的停用字詞。</span><span class="sxs-lookup"><span data-stu-id="88480-131">If any languages specified in the stop words of the source stoplist are not registered in the current database, CREATE FULLTEXT STOPLIST succeeds, but warning(s) are returned and the corresponding stop words are not added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88480-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88480-132">See Also</span></span>  
 <span data-ttu-id="88480-133">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88480-133">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="88480-134">[建立全文檢索停用字詞表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88480-134">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="88480-135">[DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88480-135">[DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="88480-136">[設定及管理全文檢索搜尋的停用字詞與停用字詞表](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="88480-136">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 [<span data-ttu-id="88480-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="88480-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
