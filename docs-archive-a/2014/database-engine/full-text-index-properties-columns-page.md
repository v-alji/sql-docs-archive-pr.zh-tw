---
title: 全文檢索索引屬性 (資料行頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: rothja
ms.author: jroth
ms.openlocfilehash: f947af04463948ef551c6df866d5a306c248c6b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607046"
---
# <a name="full-text-index-properties-columns-page"></a><span data-ttu-id="52198-102">全文檢索索引屬性 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="52198-102">Full-Text Index Properties (Columns Page)</span></span>
  <span data-ttu-id="52198-103">**若要檢視或變更全文檢索索引的屬性**</span><span class="sxs-lookup"><span data-stu-id="52198-103">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="52198-104">管理全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="52198-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="52198-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="52198-105">UI element list</span></span>  
 <span data-ttu-id="52198-106">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="52198-106">**Unique index**</span></span>  
 <span data-ttu-id="52198-107">從下拉式清單中選取索引。</span><span class="sxs-lookup"><span data-stu-id="52198-107">Select an index from the drop down list.</span></span> <span data-ttu-id="52198-108">索引必須是單一索引鍵資料行、唯一的且不可以是 Null 的索引。</span><span class="sxs-lookup"><span data-stu-id="52198-108">The index must be a single-key-column, unique, non-nullable index.</span></span>  
  
 <span data-ttu-id="52198-109">**選取將使用全文檢索索引之適合的資料行**</span><span class="sxs-lookup"><span data-stu-id="52198-109">**Select the eligible columns that will be full-text indexed**</span></span>  
 <span data-ttu-id="52198-110">此方格會顯示可用於這個全文檢索索引的資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="52198-110">The grid displays the table columns that are available for this full-text index.</span></span> <span data-ttu-id="52198-111">目前已建立全文檢索索引的資料行都會處於已核取狀態。</span><span class="sxs-lookup"><span data-stu-id="52198-111">Columns that are currently full-text indexed are checked.</span></span> <span data-ttu-id="52198-112">另外，您可以核取想要建立全文檢索索引的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="52198-112">Optionally, you can check additional columns that you want to be full-text indexed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52198-113">請確定至少核取了一個資料行，然後再按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="52198-113">Ensure that at least one column is checked before you click OK.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52198-114">**可用的資料行**</span><span class="sxs-lookup"><span data-stu-id="52198-114">**Available Columns**</span></span>|<span data-ttu-id="52198-115">資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="52198-115">The column name.</span></span>|  
|<span data-ttu-id="52198-116">**斷詞工具的語言**</span><span class="sxs-lookup"><span data-stu-id="52198-116">**Language for Word Breaker**</span></span>|<span data-ttu-id="52198-117">斷詞工具及字幹分析器會在所有全文檢索索引資料上執行語言分析的語言。</span><span class="sxs-lookup"><span data-stu-id="52198-117">The language whose word breakers and stemmers perform linguistic analysis on all full-text indexed data.</span></span><br /><br /> <span data-ttu-id="52198-118">如需詳細資訊，請參閱[設定及管理搜尋的斷詞工具與字幹分析器](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)和[在建立全文檢索索引時選擇語言](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="52198-118">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) and [Choose a Language When Creating a Full-Text Index](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).</span></span>|  
|<span data-ttu-id="52198-119">**型別**</span><span class="sxs-lookup"><span data-stu-id="52198-119">**Type**</span></span>|<span data-ttu-id="52198-120">資料表資料行的名稱，此資料行會保存已選取之資料行的文件類型。</span><span class="sxs-lookup"><span data-stu-id="52198-120">The name of the table column that holds the document type of the selected column.</span></span> <span data-ttu-id="52198-121">這是一個唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="52198-121">This is a read-only property.</span></span>|  
|<span data-ttu-id="52198-122">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="52198-122">**Statistical Semantics**</span></span>|<span data-ttu-id="52198-123">選取是否要針對選取的資料行啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="52198-123">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="52198-124">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="52198-124">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="52198-125">如果您在選取 **[統計語意]** 之前選取 **[語言]**，而且選取的語言沒有相關聯的語意語言模型，則會停用 **[統計語意]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="52198-125">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="52198-126">如果您在選取 [語言]\*\*\*\* 之前選取 [統計語意]\*\*\*\*，則下拉式方塊中提供的語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="52198-126">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52198-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52198-127">See Also</span></span>  
 [<span data-ttu-id="52198-128">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="52198-128">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
