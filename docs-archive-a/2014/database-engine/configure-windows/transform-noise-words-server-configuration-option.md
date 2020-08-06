---
title: 轉換非搜尋字伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 49de4a381de3e998073a73c284e3e3e5960f4921
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706705"
---
# <a name="transform-noise-words-server-configuration-option"></a><span data-ttu-id="7394b-102">轉換非搜尋字伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="7394b-102">transform noise words Server Configuration Option</span></span>
  <span data-ttu-id="7394b-103">`transform noise words`如果非搜尋字（[停用字詞](../../relational-databases/search/full-text-search.md)）造成全文檢索查詢的布耳運算傳回零個數據列，請使用伺服器設定選項來隱藏錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7394b-103">Use the `transform noise words` server configuration option to suppress an error message if noise words, that is [stopwords](../../relational-databases/search/full-text-search.md), cause a Boolean operation on a full-text query to return zero rows.</span></span> <span data-ttu-id="7394b-104">若全文檢索查詢使用的 CONTAINS 述詞中，布林運算或 NEAR 運算有包括非搜尋字，則這個選項很有幫助。</span><span class="sxs-lookup"><span data-stu-id="7394b-104">This option is useful for full-text queries that use the CONTAINS predicate in which Boolean operations or NEAR operations include noise words.</span></span> <span data-ttu-id="7394b-105">下表說明可能的值。</span><span class="sxs-lookup"><span data-stu-id="7394b-105">The possible values are described in the following table.</span></span>  
  
|<span data-ttu-id="7394b-106">值</span><span class="sxs-lookup"><span data-stu-id="7394b-106">Value</span></span>|<span data-ttu-id="7394b-107">描述</span><span class="sxs-lookup"><span data-stu-id="7394b-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7394b-108">0</span><span class="sxs-lookup"><span data-stu-id="7394b-108">0</span></span>|<span data-ttu-id="7394b-109">不轉換非搜尋字 (或停用字詞)。</span><span class="sxs-lookup"><span data-stu-id="7394b-109">Noise words (or stopwords) are not transformed.</span></span> <span data-ttu-id="7394b-110">當全文檢索查詢包含非搜尋字時，此查詢會傳回零個資料列，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會引發警告。</span><span class="sxs-lookup"><span data-stu-id="7394b-110">When a full-text query contains noise words, the query returns zero rows, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] raises a warning.</span></span> <span data-ttu-id="7394b-111">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="7394b-111">This is the default behavior.</span></span><br /><br /> <span data-ttu-id="7394b-112">請注意，警告是執行時間的警告。</span><span class="sxs-lookup"><span data-stu-id="7394b-112">Note that the warning is a run-time warning.</span></span> <span data-ttu-id="7394b-113">因此，如果查詢中的全文檢索子句並未執行，就不會引發此警告。</span><span class="sxs-lookup"><span data-stu-id="7394b-113">Therefore, if the full-text clause in the query is not executed, the warning is not raised.</span></span> <span data-ttu-id="7394b-114">若為本機查詢，只會引發一則警告，即使有多個全文檢索查詢子句也一樣。</span><span class="sxs-lookup"><span data-stu-id="7394b-114">For a local query, only one warning is raised, even when there are multiple full-text query clauses.</span></span> <span data-ttu-id="7394b-115">若為遠端查詢，連結的伺服器可能不會轉送錯誤。因此，可能不會引發此警告。</span><span class="sxs-lookup"><span data-stu-id="7394b-115">For a remote query, the linked server might not relay the error; therefore, the warning might not be raised.</span></span>|  
|<span data-ttu-id="7394b-116">1</span><span class="sxs-lookup"><span data-stu-id="7394b-116">1</span></span>|<span data-ttu-id="7394b-117">轉換非搜尋字 (或停用字詞)。</span><span class="sxs-lookup"><span data-stu-id="7394b-117">Noise words (or stopwords) are transformed.</span></span> <span data-ttu-id="7394b-118">忽略這些字，並評估查詢的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="7394b-118">They are ignored, and the rest of the query is evaluated.</span></span><br /><br /> <span data-ttu-id="7394b-119">如果非搜尋字指定在鄰近詞彙中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將其移除。</span><span class="sxs-lookup"><span data-stu-id="7394b-119">If noise words are specified in a proximity term, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] removes them.</span></span> <span data-ttu-id="7394b-120">例如，非搜尋字 `is` 會從 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`中移除，將搜尋查詢轉換為 `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`。</span><span class="sxs-lookup"><span data-stu-id="7394b-120">For example, the noise word `is` is removed from `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, transforming the search query into `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`.</span></span> <span data-ttu-id="7394b-121">請注意， `CONTAINS(<column_name>, 'NEAR(hello,is)')` 只會轉換成 `CONTAINS(<column_name>, hello)` ，因為只有一個有效的搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="7394b-121">Notice that `CONTAINS(<column_name>, 'NEAR(hello,is)')` would be transformed into simply `CONTAINS(<column_name>, hello)` because there is only one valid search term.</span></span>|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a><span data-ttu-id="7394b-122">轉換非搜尋字設定效果</span><span class="sxs-lookup"><span data-stu-id="7394b-122">Effects of the transform noise words Setting</span></span>  
 <span data-ttu-id="7394b-123">這一節將說明包含非搜尋字 "`the`" 的查詢行為 (在 `transform noise words` 的替代設定底下)。</span><span class="sxs-lookup"><span data-stu-id="7394b-123">This section illustrates the behavior of queries containing a noise word, "`the`", under the alternate settings of `transform noise words`.</span></span>  <span data-ttu-id="7394b-124">假設範例全文檢索查詢字串會針對包含下列資料的資料表資料列執行：`[1, "The black cat"]`。</span><span class="sxs-lookup"><span data-stu-id="7394b-124">The sample full-text query strings are assumed to be run against a table row containing the following data: `[1, "The black cat"]`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7394b-125">所有的這類案例都可以產生非搜尋字警告。</span><span class="sxs-lookup"><span data-stu-id="7394b-125">All such scenarios can generate a noise word warning.</span></span>  
  
-   <span data-ttu-id="7394b-126">轉換非搜尋字設為 0：</span><span class="sxs-lookup"><span data-stu-id="7394b-126">With transform noise words set to 0:</span></span>  
  
    |<span data-ttu-id="7394b-127">查詢字串</span><span class="sxs-lookup"><span data-stu-id="7394b-127">Query string</span></span>|<span data-ttu-id="7394b-128">結果</span><span class="sxs-lookup"><span data-stu-id="7394b-128">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="7394b-129">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-129">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="7394b-130">無結果 ("`the`" AND "`cat`" 的行為是相同的)。</span><span class="sxs-lookup"><span data-stu-id="7394b-130">No results (The behavior is the same for "`the`" AND "`cat`".)</span></span>|  
    |<span data-ttu-id="7394b-131">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-131">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="7394b-132">無結果 ("`the`" NEAR "`cat`" 的行為是相同的)。</span><span class="sxs-lookup"><span data-stu-id="7394b-132">No results (The behavior is the same for "`the`" NEAR "`cat`".)</span></span>|  
    |<span data-ttu-id="7394b-133">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="7394b-133">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="7394b-134">搜尋支援</span><span class="sxs-lookup"><span data-stu-id="7394b-134">No results</span></span>|  
    |<span data-ttu-id="7394b-135">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-135">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="7394b-136">搜尋支援</span><span class="sxs-lookup"><span data-stu-id="7394b-136">No results</span></span>|  
  
-   <span data-ttu-id="7394b-137">轉換非搜尋字設為 1：</span><span class="sxs-lookup"><span data-stu-id="7394b-137">With transform noise words set to 1:</span></span>  
  
    |<span data-ttu-id="7394b-138">查詢字串</span><span class="sxs-lookup"><span data-stu-id="7394b-138">Query string</span></span>|<span data-ttu-id="7394b-139">結果</span><span class="sxs-lookup"><span data-stu-id="7394b-139">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="7394b-140">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-140">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="7394b-141">識別碼為 1 之資料列的叫用</span><span class="sxs-lookup"><span data-stu-id="7394b-141">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="7394b-142">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-142">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="7394b-143">識別碼為 1 之資料列的叫用</span><span class="sxs-lookup"><span data-stu-id="7394b-143">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="7394b-144">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="7394b-144">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="7394b-145">搜尋支援</span><span class="sxs-lookup"><span data-stu-id="7394b-145">No results</span></span>|  
    |<span data-ttu-id="7394b-146">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="7394b-146">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="7394b-147">識別碼為 1 之資料列的叫用</span><span class="sxs-lookup"><span data-stu-id="7394b-147">Hit for row with ID 1</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7394b-148">範例</span><span class="sxs-lookup"><span data-stu-id="7394b-148">Example</span></span>  
 <span data-ttu-id="7394b-149">下列範例會將 `transform noise words` 設定為 `1`。</span><span class="sxs-lookup"><span data-stu-id="7394b-149">The following example sets `transform noise words` to `1`.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7394b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7394b-150">See Also</span></span>  
 <span data-ttu-id="7394b-151">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7394b-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="7394b-152">CONTAINS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7394b-152">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
