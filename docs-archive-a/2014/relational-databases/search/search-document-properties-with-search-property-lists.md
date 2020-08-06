---
title: 使用搜索屬性清單搜索文件屬性 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- full-text search [SQL Server], properties
- search property lists [SQL Server]
- property searching [SQL Server], about
- full-text indexes [SQL Server], search property lists
- search property lists [SQL Server], about
- property searching [SQL Server]
ms.assetid: ffae5914-b1b2-4267-b927-37e8382e0a9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16ab59a9fcdab29c927cb624dabcdfa71eaae1e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704026"
---
# <a name="search-document-properties-with-search-property-lists"></a><span data-ttu-id="85083-102">使用搜索屬性清單搜索文件屬性</span><span class="sxs-lookup"><span data-stu-id="85083-102">Search Document Properties with Search Property Lists</span></span>
  <span data-ttu-id="85083-103">文件屬性的內容與文件本文的內容之間原本無法區別。</span><span class="sxs-lookup"><span data-stu-id="85083-103">The content of document properties was previously indistinguishable from the content of the document body.</span></span> <span data-ttu-id="85083-104">這項限制會將全文檢索查詢限制為整個文件的一般搜尋。</span><span class="sxs-lookup"><span data-stu-id="85083-104">This limitation restricted full-text queries to generic searches on whole documents.</span></span> <span data-ttu-id="85083-105">不過，現在您可以針對 `varbinary`、`varbinary(max)` (包括 `FILESTREAM`) 或 `image` 二進位資料行中支援的文件類型設定全文檢索索引，以便支援特定屬性 (例如 Author 和 Title) 的屬性範圍搜尋作業。</span><span class="sxs-lookup"><span data-stu-id="85083-105">Now, however, you can configure a full-text index to support property-scoped searching on particular properties, such as Author and Title, for supported document types in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` binary data column.</span></span> <span data-ttu-id="85083-106">這種搜尋形式稱為「屬性搜尋」  。</span><span class="sxs-lookup"><span data-stu-id="85083-106">This form of searching is known as *property searching*.</span></span>  
  
 <span data-ttu-id="85083-107">相關聯的 [篩選](configure-and-manage-filters-for-search.md) (IFilter) 會決定是否可對特定文件類型進行屬性搜尋。</span><span class="sxs-lookup"><span data-stu-id="85083-107">The associated [filter](configure-and-manage-filters-for-search.md) (IFilter) determines whether property searching is possible on a specific type of document.</span></span> <span data-ttu-id="85083-108">對於某些文件類型而言，相關聯的 IFilter 會擷取針對該文件類型定義的部分或全部屬性，以及文件本文的內容。</span><span class="sxs-lookup"><span data-stu-id="85083-108">For some document types, the associated IFilter extracts some or all of the properties defined for that type of document, as well as the content of the document body.</span></span> <span data-ttu-id="85083-109">您可以設定全文檢索索引，以便支援針對 IFilter 在建立全文檢索索引期間所擷取的特定屬性進行屬性搜尋。</span><span class="sxs-lookup"><span data-stu-id="85083-109">You can configure a full-text index to support property searching only on properties that are extracted by an IFilter during full-text indexing.</span></span> <span data-ttu-id="85083-110">適用於 .docx、.xlsx 和 .pptx 等 Microsoft Office 文件類型的 IFilter 就是會擷取許多文件屬性的 IFilter。</span><span class="sxs-lookup"><span data-stu-id="85083-110">Among IFilters that extract a number of document properties are the IFilters for Microsoft Office document types (such as .docx, .xlsx, and .pptx).</span></span> <span data-ttu-id="85083-111">另一方面，XML IFilter 不會發出屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-111">On the other hand, the XML IFilter does not emit properties.</span></span>  
  
##  <a name="how-full-text-search-works-with-search-properties"></a><a name="How_FTS_Works_with_search_properties"></a> <span data-ttu-id="85083-112">全文檢索搜尋如何使用搜尋屬性</span><span class="sxs-lookup"><span data-stu-id="85083-112">How Full-Text Search Works with Search Properties</span></span>  
  
### <a name="internal-property-ids"></a><span data-ttu-id="85083-113">內部屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="85083-113">Internal Property IDs</span></span>  
 <span data-ttu-id="85083-114">全文檢索引擎會為每個註冊的屬性任意指派內部屬性識別碼，這個識別碼可在該特定搜尋清單中唯一識別屬性，而且是該搜尋屬性清單特有的。</span><span class="sxs-lookup"><span data-stu-id="85083-114">The Full-Text Engine arbitrarily assigns each registered property an internal property ID, which uniquely identifies the property in that particular search list and which is specific to that search property list.</span></span> <span data-ttu-id="85083-115">因此，如果您將某個屬性加入至多個搜尋屬性清單，不同清單之間的內部屬性識別碼可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="85083-115">Therefore, if a property is added to multiple search property lists, its internal property ID is likely to differ between different lists.</span></span>  
  
 <span data-ttu-id="85083-116">針對搜尋清單註冊屬性時，全文檢索引擎就會將「內部屬性識別碼」  任意指派給屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-116">When a property is registered for a search list, the Full-Text Engine arbitrarily assigns an *internal property ID* to the property.</span></span> <span data-ttu-id="85083-117">內部屬性識別碼是一個整數，可在該搜尋屬性清單中唯一識別屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-117">The internal property ID is an integer that uniquely identifies the property in that search property list.</span></span>  
  
 <span data-ttu-id="85083-118">下圖顯示指定 Title 和 Keywords 這兩個屬性之搜尋屬性清單的邏輯檢視。</span><span class="sxs-lookup"><span data-stu-id="85083-118">The following illustration shows a logical view of a search property list that specifies two properties, Title and Keywords.</span></span> <span data-ttu-id="85083-119">Keywords 的屬性清單名稱為 "Tags"。</span><span class="sxs-lookup"><span data-stu-id="85083-119">The property-list name for Keywords is "Tags".</span></span> <span data-ttu-id="85083-120">這些屬性屬於相同的屬性集，其 GUID 為 F29F85E0-4FF9-1068-AB91-08002B27B3D9。</span><span class="sxs-lookup"><span data-stu-id="85083-120">These properties belong to the same property set, whose GUID is F29F85E0-4FF9-1068-AB91-08002B27B3D9.</span></span> <span data-ttu-id="85083-121">Title 和 Tags (Keywords) 的屬性整數識別碼分別為 2 和 5。</span><span class="sxs-lookup"><span data-stu-id="85083-121">The property integer identifiers are 2 for Title and 5 for Tags (Keywords).</span></span> <span data-ttu-id="85083-122">全文檢索引擎會將每個屬性任意對應至搜尋屬性清單獨有的內部屬性識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-122">The Full-Text Engine arbitrarily maps each property to an internal property ID that is unique to the search property list.</span></span> <span data-ttu-id="85083-123">Title 屬性的內部屬性識別碼為 1，而 Tags 屬性的內部屬性識別碼為 2。</span><span class="sxs-lookup"><span data-stu-id="85083-123">The internal property ID for the Title property is 1, and the internal property ID for the Tags property is 2.</span></span>  
  
 <span data-ttu-id="85083-124">![將搜尋屬性清單對應至內部資料表](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "將搜尋屬性清單對應至內部資料表")</span><span class="sxs-lookup"><span data-stu-id="85083-124">![Mapping of search property list to internal table](../../database-engine/media/ifts-spl-w-title-and-keywords.gif "Mapping of search property list to internal table")</span></span>  
  
 <span data-ttu-id="85083-125">內部屬性識別碼可能會與屬性的屬性整數識別碼不同。</span><span class="sxs-lookup"><span data-stu-id="85083-125">The internal property ID is likely to be different from the property integer identifier of the property.</span></span> <span data-ttu-id="85083-126">如果給定屬性已在多個搜尋屬性清單中註冊，可能會為每個搜尋屬性清單指定不同的內部屬性識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-126">If a given property is registered for multiple search property lists, a different internal property ID might be assigned for each search property list.</span></span> <span data-ttu-id="85083-127">例如，內部屬性識別碼在某個搜尋屬性清單中可能是 4、在另一個清單中可能是 1、在另一個清單中可能是 3，依此類推。</span><span class="sxs-lookup"><span data-stu-id="85083-127">For example, the internal property ID might be 4 in one search property list, 1 in another, 3 in another, and so on.</span></span> <span data-ttu-id="85083-128">反之，屬性整數識別碼是屬性內建的，而且不論該屬性用於何處，它都會維持相同。</span><span class="sxs-lookup"><span data-stu-id="85083-128">In contrast, the property integer identifier is intrinsic to the property, and it remains the same wherever the property is used.</span></span>  
  
  
  
### <a name="indexing-of-registered-properties"></a><span data-ttu-id="85083-129">已註冊屬性的索引</span><span class="sxs-lookup"><span data-stu-id="85083-129">Indexing of Registered Properties</span></span>  
 <span data-ttu-id="85083-130">將全文檢索索引與搜尋屬性清單產生關聯之後，您必須重新擴展索引，以便建立屬性特有搜尋詞彙的索引。</span><span class="sxs-lookup"><span data-stu-id="85083-130">After a full-text index is associated with a search property list, the index must be repopulated to index property-specific search terms.</span></span> <span data-ttu-id="85083-131">建立全文檢索索引期間，所有屬性的內容以及其他內容都會儲存在全文檢索索引中。</span><span class="sxs-lookup"><span data-stu-id="85083-131">During full-text indexing, the contents of all properties are stored in the full-text index along with other content.</span></span> <span data-ttu-id="85083-132">不過，建立在已註冊屬性中找到之搜尋詞彙的索引時，全文檢索索引子也會儲存具有該詞彙的對應內部屬性識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-132">However, when indexing a search term found in a registered property, the full-text indexer also stores the corresponding internal property ID with the term.</span></span> <span data-ttu-id="85083-133">反之，如果屬性尚未註冊，它就會儲存在全文檢索索引中，就如同它屬於文件本文的一部分，而且其內部屬性識別碼的值為零。</span><span class="sxs-lookup"><span data-stu-id="85083-133">In contrast, if a property is not registered, it is stored in the full-text index as if it were part of the document body, and it has a value of zero for the internal property ID.</span></span>  
  
 <span data-ttu-id="85083-134">下圖顯示搜尋詞彙如何顯示在全文檢索索引中的邏輯檢視，該索引與上圖所顯示的搜尋屬性清單相關聯。</span><span class="sxs-lookup"><span data-stu-id="85083-134">The following illustration shows a logical view of how search terms appear in a full-text index that is associated with the search property list shown in the preceding illustration.</span></span> <span data-ttu-id="85083-135">範例文件 Document 1 包含三個屬性 (Title、Author 和 Keywords) 以及文件本文。</span><span class="sxs-lookup"><span data-stu-id="85083-135">A sample document, Document 1 contains three properties-Title, Author, and Keywords-as well as the document body.</span></span> <span data-ttu-id="85083-136">對於在搜尋屬性清單中指定的 Title 和 Keywords 屬性而言，搜尋詞彙會與全文檢索索引中其對應的內部屬性識別碼相關聯。</span><span class="sxs-lookup"><span data-stu-id="85083-136">For the properties Title and Keywords, which are specified in the search property list, search terms are associated with their corresponding internal property IDs in the full-text index.</span></span> <span data-ttu-id="85083-137">反之，Author 屬性的內容會建立索引，就如同它屬於文件本文的一部分。</span><span class="sxs-lookup"><span data-stu-id="85083-137">In contrast, the content of the Author property is indexed as if it were part of the document body.</span></span> <span data-ttu-id="85083-138">這表示，註冊屬性會根據屬性中儲存的內容數量，稍微增加全文檢索索引的大小。</span><span class="sxs-lookup"><span data-stu-id="85083-138">This means registering a property increases the size of the full-text index somewhat, depending on the amount of content stored in the property.</span></span>  
  
 <span data-ttu-id="85083-139">![使用搜尋屬性清單的全文檢索索引](../../database-engine/media/ifts-spl-and-fti.gif "使用搜尋屬性清單的全文檢索索引")</span><span class="sxs-lookup"><span data-stu-id="85083-139">![Full-text index that uses a search property list](../../database-engine/media/ifts-spl-and-fti.gif "Full-text index that uses a search property list")</span></span>  
  
 <span data-ttu-id="85083-140">Title 屬性中的搜尋字詞 ("Favorite"、"Biking" 和 "Trails") 會與針對此索引指派給 Title 的內部屬性識別碼 1 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="85083-140">Search terms in the Title property-"Favorite," "Biking," and "Trails"-are associated with the internal property ID assigned to Title for this index, 1.</span></span> <span data-ttu-id="85083-141">Keywords 屬性中的搜尋字詞 ("biking" 和 "mountain") 會與針對此索引指派給 Tags 的內部屬性識別碼 2 建立關聯。</span><span class="sxs-lookup"><span data-stu-id="85083-141">Search terms in the Keywords property-"biking" and "mountain"-are associated with the internal property ID assigned to Tags for this index, 2.</span></span> <span data-ttu-id="85083-142">若為 Author 屬性中的搜尋字詞 ("Jane" 和 "Doe") 以及文件本文中的搜尋字詞，內部屬性識別碼為 0。</span><span class="sxs-lookup"><span data-stu-id="85083-142">For search terms n the Author property-"Jane" and "Doe"-and search terms in the document body, the internal property ID is 0.</span></span> <span data-ttu-id="85083-143">請注意，詞彙 "biking" 出現在 Title 屬性、Keywords (Tags) 屬性和文件本文中。</span><span class="sxs-lookup"><span data-stu-id="85083-143">Note that the term "biking" occurs in the Title property, in the Keywords (Tags) property, and in the document body.</span></span> <span data-ttu-id="85083-144">Title 或 Keywords (Tags) 屬性中 "biking" 的屬性搜尋會在結果中傳回這份文件。</span><span class="sxs-lookup"><span data-stu-id="85083-144">A property search for "biking" in the Title or Keywords (Tags) property would return this document in the results.</span></span> <span data-ttu-id="85083-145">"biking" 的一般全文檢索查詢也會傳回這份文件，就像是沒有針對屬性搜尋設定索引一樣。</span><span class="sxs-lookup"><span data-stu-id="85083-145">A generic full-text query for "biking" would also return this document, just as if the index were not configured for property searching.</span></span> <span data-ttu-id="85083-146">Author 屬性中 "biking" 的屬性搜尋則不會傳回這份文件。</span><span class="sxs-lookup"><span data-stu-id="85083-146">A property search for "biking" in the Author property would not return this document.</span></span>  
  
 <span data-ttu-id="85083-147">屬性範圍的全文檢索查詢會使用針對全文檢索索引之目前搜尋屬性清單註冊的內部屬性識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-147">A property-scoped full-text query uses the internal property IDs registered for the current search property list of the full-text index.</span></span>  
  
  
  
##  <a name="impact-of-enabling-property-searching"></a><a name="impact"></a> <span data-ttu-id="85083-148">啟用屬性搜索的影響</span><span class="sxs-lookup"><span data-stu-id="85083-148">Impact of Enabling Property Searching</span></span>  
 <span data-ttu-id="85083-149">如果您設定全文檢索索引來支援一個或多個屬性的搜尋，就會根據您在搜尋屬性清單中指定的屬性數目以及每個屬性的內容，稍微增加索引的大小。</span><span class="sxs-lookup"><span data-stu-id="85083-149">Configuring a full-text index to support searching on one or more properties increases the size of the index somewhat, depending on the number of properties you specify in your search property list and on the content of each property.</span></span>  
  
 <span data-ttu-id="85083-150">在測試 Microsoft Word<sup>？？</sup>、Excel<sup>？？</sup>和 PowerPoint 的一般主體嗎<sup>？</sup></span><span class="sxs-lookup"><span data-stu-id="85083-150">In testing typical corpuses of Microsoft Word<sup>??</sup>, Excel<sup>??</sup>, and PowerPoint<sup>??</sup></span></span> <span data-ttu-id="85083-151">檔，我們已設定全文檢索索引來編制一般搜尋屬性的索引。</span><span class="sxs-lookup"><span data-stu-id="85083-151">documents, we configured a full-text index to index typical search properties.</span></span> <span data-ttu-id="85083-152">建立這些屬性的索引大約增加了 5% 的全文檢索索引大小。</span><span class="sxs-lookup"><span data-stu-id="85083-152">Indexing these properties increased the size of the full-text index size by approximately 5 percent.</span></span> <span data-ttu-id="85083-153">我們預期大部分文件主體的這個近似大小增加量應該相同。</span><span class="sxs-lookup"><span data-stu-id="85083-153">We anticipate that this approximate size increase will to be typical for most document corpuses.</span></span> <span data-ttu-id="85083-154">不過，此大小增加量最終將取決於給定文件主體中的屬性資料量相對於整體資料量。</span><span class="sxs-lookup"><span data-stu-id="85083-154">However, ultimately, the size increase will depend on the amount of property data in a given document corpus relative to the amount of overall data.</span></span>  
  
  
  
##  <a name="creating-a-search-property-list-and-enabling-property-search"></a><a name="creating"></a><span data-ttu-id="85083-155">建立搜尋屬性清單和啟用屬性搜尋</span><span class="sxs-lookup"><span data-stu-id="85083-155">Creating a Search Property List and Enabling Property Search</span></span>  
  
###  <a name="creating-a-search-property-list"></a><a name="creating_sub"></a><span data-ttu-id="85083-156">建立搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-156">Creating a Search Property List</span></span>  
 <span data-ttu-id="85083-157">**若要使用 Transact-SQL 建立搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-157">**To create a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="85083-158">使用 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) 陳述式並提供至少一個清單名稱。</span><span class="sxs-lookup"><span data-stu-id="85083-158">Use the [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) statement and provide at least a name the list.</span></span>  
  
##### <a name="to-create-a-search-property-list-in-management-studio"></a><span data-ttu-id="85083-159">在 Management Studio 中建立搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-159">To create a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="85083-160">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="85083-160">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="85083-161">展開 [資料庫]\*\*\*\*，然後展開您想要在其中建立搜尋屬性清單的資料庫。</span><span class="sxs-lookup"><span data-stu-id="85083-161">Expand **Databases**, and then expand the database in which you want to create the search property list.</span></span>  
  
3.  <span data-ttu-id="85083-162">展開 [儲存體]\*\*\*\*，然後以滑鼠右鍵按一下 [搜尋屬性清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-162">Expand **Storage**, and then right-click **Search Property Lists**.</span></span>  
  
4.  <span data-ttu-id="85083-163">選取 [新增搜尋屬性清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-163">Select **New Search Property List**.</span></span>  
  
5.  <span data-ttu-id="85083-164">指定屬性清單名稱。</span><span class="sxs-lookup"><span data-stu-id="85083-164">Specify the property list name.</span></span>  
  
6.  <span data-ttu-id="85083-165">(選擇性) 將某個其他人指定為屬性清單的擁有者。</span><span class="sxs-lookup"><span data-stu-id="85083-165">Optionally, specify someone else as the property list owner.</span></span>  
  
7.  <span data-ttu-id="85083-166">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="85083-166">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="85083-167">**建立空的搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-167">**Create an empty search property list**</span></span>  
  
    -   <span data-ttu-id="85083-168">**從現有搜尋屬性清單建立**</span><span class="sxs-lookup"><span data-stu-id="85083-168">**Create from an existing search property list**</span></span>  
  
     <span data-ttu-id="85083-169">如需詳細資訊，請參閱 [新增搜尋屬性清單](../../database-engine/new-search-property-list.md)。</span><span class="sxs-lookup"><span data-stu-id="85083-169">For more information, see [New Search Property List](../../database-engine/new-search-property-list.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 
  
###  <a name="adding-properties-to-a-search-property-list"></a><a name="adding"></a><span data-ttu-id="85083-170">將屬性加入至搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-170">Adding Properties to a Search Property List</span></span>  
 <span data-ttu-id="85083-171">屬性搜尋需要建立「搜尋屬性清單」\*\*，並指定一個或多個您想要設為可搜尋的屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-171">Property searching requires creating a *search property list* and specifying one or more properties that you want to make searchable.</span></span> <span data-ttu-id="85083-172">當您將某個屬性加入至搜尋屬性清單時，就會針對該特定清單註冊此屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-172">When you add a property to a search property list, the property is registered for that particular list.</span></span> <span data-ttu-id="85083-173">若要將屬性加入至搜尋屬性清單，您需要下列值：</span><span class="sxs-lookup"><span data-stu-id="85083-173">To add a property to a search property list you need the following values:</span></span>  
  
-   <span data-ttu-id="85083-174">屬性集 GUID</span><span class="sxs-lookup"><span data-stu-id="85083-174">Property set GUID</span></span>  
  
     <span data-ttu-id="85083-175">每個搜尋屬性都屬於包含一組相關屬性的單一屬性集。</span><span class="sxs-lookup"><span data-stu-id="85083-175">Each search property belongs to single property set that contains a group of related properties.</span></span> <span data-ttu-id="85083-176">每個屬性集都由全域唯一識別碼 (GUID) 所識別。</span><span class="sxs-lookup"><span data-stu-id="85083-176">Each property set is identified by a globally unique identifier (GUID).</span></span>  
  
-   <span data-ttu-id="85083-177">屬性整數識別碼</span><span class="sxs-lookup"><span data-stu-id="85083-177">Property integer identifier</span></span>  
  
     <span data-ttu-id="85083-178">每個搜尋屬性都會擁有在屬性集中唯一的識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-178">Each search property possesses an identifier that is unique within the property set.</span></span> <span data-ttu-id="85083-179">請注意，若為給定的屬性，此識別碼可能是整數或字串，不過全文檢索搜尋只支援整數識別碼。</span><span class="sxs-lookup"><span data-stu-id="85083-179">Note that for a given property, the identifier could be either an integer or a string, however full-text search supports only integer identifiers.</span></span>  
  
-   <span data-ttu-id="85083-180">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="85083-180">Property name</span></span>  
  
     <span data-ttu-id="85083-181">這是使用者將在全文檢索查詢中指定以搜尋屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="85083-181">This is the name that users will specify in full-text queries to search on the property.</span></span> <span data-ttu-id="85083-182">屬性名稱可以包含內部空格。</span><span class="sxs-lookup"><span data-stu-id="85083-182">A property name can contain internal spaces.</span></span> <span data-ttu-id="85083-183">最大長度是 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="85083-183">The maximum length is 256 characters.</span></span>  
  
     <span data-ttu-id="85083-184">屬性名稱可以是下列任何一個值：</span><span class="sxs-lookup"><span data-stu-id="85083-184">The property name can be any of the following:</span></span>  
  
    -   <span data-ttu-id="85083-185">屬性的 Windows 正式名稱，例如 `System.Author` 或 `System.Contact.HomeAddress`。</span><span class="sxs-lookup"><span data-stu-id="85083-185">The Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span>  
  
    -   <span data-ttu-id="85083-186">使用者易記的名稱，方便使用者記憶。</span><span class="sxs-lookup"><span data-stu-id="85083-186">A user-friendly name that is easy for your users to remember.</span></span> <span data-ttu-id="85083-187">某些屬性會與已知的使用者易記名稱相關聯 (例如「作者」或「住家地址」)，不過您也可以指定最適合使用者使用的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="85083-187">Some properties are associated with a well-known user-friendly name, such as "Author" or "Home Address," but you can specify whatever name is most appropriate to your users.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85083-188">屬性集 GUID 和屬性識別碼的給定組合在給定的搜尋屬性清單中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="85083-188">A given combination of property set GUID and property identifier must be unique in a given search property list.</span></span> <span data-ttu-id="85083-189">這表示，您無法用不同的名稱或描述多次加入相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-189">This means that you cannot add the same property more than once with different names or descriptions.</span></span>  
  
-   <span data-ttu-id="85083-190">屬性描述 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="85083-190">Property description (optional)</span></span>  
  
     <span data-ttu-id="85083-191">將搜尋屬性加入至搜尋屬性清單時，您可以提供選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="85083-191">When adding a search property to a search property list, you can supply an optional description.</span></span> <span data-ttu-id="85083-192">例如，您可能會想要提供有關與其名稱不盡相符之屬性的詳細資訊，或者可能想要描述屬性的屬性集。</span><span class="sxs-lookup"><span data-stu-id="85083-192">For example, you might want to provide information about a property that is not evident from its name, or you might want to describe the property set of the property.</span></span>  
  
 <span data-ttu-id="85083-193">**若要取得搜尋屬性清單的值**</span><span class="sxs-lookup"><span data-stu-id="85083-193">**To obtain values for a search property list**</span></span>  
  
 <span data-ttu-id="85083-194">請參閱 [尋找搜尋屬性的屬性集 GUID 與屬性整數識別碼](find-property-set-guids-and-property-integer-ids-for-search-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="85083-194">See [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="85083-195">**若要使用 Transact-SQL 將屬性加入至搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-195">**To add a property to a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="85083-196">使用 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) 陳述式搭配您使用[尋找搜尋屬性的屬性集 GUID 與屬性整數識別碼](find-property-set-guids-and-property-integer-ids-for-search-properties.md)主題中提及的方法之一取得的值。</span><span class="sxs-lookup"><span data-stu-id="85083-196">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement with the values that you obtained by using one of the methods described in the topic, [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span>  
  
 <span data-ttu-id="85083-197">下列範例會示範將屬性加入至搜尋屬性清單時，這些值的使用方式：</span><span class="sxs-lookup"><span data-stu-id="85083-197">The following example demonstrates the use of these values when adding a property to a search property list:</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST DocumentTablePropertyList  
   ADD 'Title'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
```  
  
 <span data-ttu-id="85083-198">**若要在 Management Studio 中將屬性加入至搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-198">**To add a property to a search property list in Management Studio**</span></span>  
  
 <span data-ttu-id="85083-199">使用 [搜尋屬性清單屬性]\*\*\*\* 對話方塊即可加入或移除搜尋屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-199">Use the **Search Property List Properties** dialog box to add and remove search properties.</span></span> <span data-ttu-id="85083-200">您可以在 [物件總管] 中相關資料庫的 [儲存體]\*\*\*\* 節點底下找到 [搜尋屬性清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-200">You can find **Search Property Lists** in Object Explorer under the **Storage** node of the associated database.</span></span>  
  
  
  
###  <a name="associating-a-search-property-list-with-a-full-text-index"></a><a name="associating"></a> <span data-ttu-id="85083-201">將搜尋屬性清單與全文檢索索引產生關聯</span><span class="sxs-lookup"><span data-stu-id="85083-201">Associating a Search Property List with a Full-Text Index</span></span>  
 <span data-ttu-id="85083-202">若要讓全文檢索索引支援針對已在搜尋屬性清單中註冊的屬性進行屬性搜尋，您必須將搜尋屬性清單與索引產生關聯，然後重新擴展索引。</span><span class="sxs-lookup"><span data-stu-id="85083-202">For a full-text index to support property searching on the properties that are registered for a search property list, you need to associate the search property list with the index and repopulate the index.</span></span> <span data-ttu-id="85083-203">重新擴展全文檢索索引會針對每個註冊屬性中的搜尋詞彙建立屬性特有的索引項目。</span><span class="sxs-lookup"><span data-stu-id="85083-203">Repopulating the full-text index creates property-specific index entries for search terms in each of the registered properties.</span></span>  
  
 <span data-ttu-id="85083-204">只要全文檢索索引與這個搜尋屬性清單維持相關聯的狀態，全文檢索查詢就可以使用 CONTAINS 述詞的 PROPERTY 選項來搜尋已在該搜尋屬性清單中註冊的屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-204">As long as the full-text index remains associated with this search property list, full-text query can use the PROPERTY option of the CONTAINS predicate to search on properties that are registered for that search property list.</span></span>  
  
 <span data-ttu-id="85083-205">如果您變更與全文檢索索引相關聯的搜尋屬性清單，則必須先重建索引，才能讓索引進入一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="85083-205">If you change the search property list associated with a full-text index, then the index must be rebuilt to bring it into a consistent state.</span></span> <span data-ttu-id="85083-206">系統會立即截斷並清空索引，直到完整母體擴展執行為止。</span><span class="sxs-lookup"><span data-stu-id="85083-206">The index is truncated immediately and is empty until the full population runs.</span></span> <span data-ttu-id="85083-207">如需有關何時變更搜尋屬性清單會導致重建索引的詳細資訊，請參閱 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 中的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="85083-207">For more information about when changing the search property list causes rebuilding the index, see "Remarks," in [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="85083-208">**若要使用 Transact-SQL 讓搜尋屬性清單與全文檢索索引產生關聯**</span><span class="sxs-lookup"><span data-stu-id="85083-208">**To associate a search property list with a full-text index with Transact-SQL**</span></span>  
  
 <span data-ttu-id="85083-209">使用 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 陳述式搭配 `SET SEARCH PROPERTY LIST = <property_list_name>` 子句。</span><span class="sxs-lookup"><span data-stu-id="85083-209">Use the [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement with the `SET SEARCH PROPERTY LIST = <property_list_name>` clause.</span></span>  
  
 <span data-ttu-id="85083-210">**若要使用 Management Studio 讓搜尋屬性清單與全文檢索索引產生關聯**</span><span class="sxs-lookup"><span data-stu-id="85083-210">**To associate a search property list with a full-text index with Management Studio**</span></span>  
  
 <span data-ttu-id="85083-211">在 [全文檢索索引屬性]\*\*\*\* 對話方塊的 [一般]\*\*\*\* 頁面上，指定 [搜尋屬性清單]\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="85083-211">Specify a value for **Search Property List** on the **General** page of the **Full-Text Index Properties** dialog box.</span></span>  
  
  
  
##  <a name="querying-search-properties-with-contains"></a><a name="Ov_CONTAINS_using_PROPERTY"></a> <span data-ttu-id="85083-212">使用 CONTAINS 查詢搜索屬性</span><span class="sxs-lookup"><span data-stu-id="85083-212">Querying Search Properties with CONTAINS</span></span>  
 <span data-ttu-id="85083-213">屬性範圍之全文檢索查詢的基本 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 語法如下：</span><span class="sxs-lookup"><span data-stu-id="85083-213">The basic [CONTAINS](/sql/t-sql/queries/contains-transact-sql) syntax for a property-scoped full-text query is as follows:</span></span>  
  
```sql  
SELECT column_name FROM table_name  
  WHERE CONTAINS ( PROPERTY ( column_name, 'property_name' ), '<contains_search_condition>' )  
```  
  
 <span data-ttu-id="85083-214">例如，下列查詢會在 `Title`資料庫之 `Document` 資料表的 `Production.Document` 資料行中搜尋索引屬性 `AdventureWorks` 。</span><span class="sxs-lookup"><span data-stu-id="85083-214">For example, the following query searches on an indexed property, `Title`, in the `Document` column of the `Production.Document` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="85083-215">此查詢只會傳回下列文件：其 `Title` 屬性包含 `Maintenance` 或 `Repair`</span><span class="sxs-lookup"><span data-stu-id="85083-215">The query returns only documents whose `Title` property contains the string `Maintenance` or `Repair`</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT Document FROM Production.Document  
  WHERE CONTAINS ( PROPERTY ( Document, 'Title' ), 'Maintenance OR Repair')  
GO  
```  
  
 <span data-ttu-id="85083-216">此範例假設文件的 IFilter 會擷取其 Title 屬性、Title 屬性會加入至搜尋屬性清單，以及搜尋屬性清單與全文檢索索引相關聯。</span><span class="sxs-lookup"><span data-stu-id="85083-216">This example assumes that the IFilter for the document extracts its Title property, that the Title property is added to the search property list, and that the search property list is associated with the full-text index.</span></span>  
  
  
  
##  <a name="managing-search-property-lists"></a><a name="managing"></a><span data-ttu-id="85083-217">管理搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-217">Managing Search Property Lists</span></span>  
  
###  <a name="viewing-and-changing-a-search-property-list"></a><a name="viewing"></a><span data-ttu-id="85083-218">查看和變更搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-218">Viewing and Changing a Search Property List</span></span>  
 <span data-ttu-id="85083-219">**若要使用 Transact-SQL 變更搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-219">**To change a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="85083-220">使用 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) 陳述式新增或移除搜尋屬性。</span><span class="sxs-lookup"><span data-stu-id="85083-220">Use the [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add or remove search properties.</span></span>  
  
##### <a name="to-view-and-change-a-search-property-list-in-management-studio"></a><span data-ttu-id="85083-221">在 Management Studio 中檢視和變更搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-221">To view and change a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="85083-222">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="85083-222">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="85083-223">展開 **[資料庫]**，然後展開此資料庫。</span><span class="sxs-lookup"><span data-stu-id="85083-223">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="85083-224">展開 [存放裝置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-224">Expand **Storage**.</span></span>  
  
4.  <span data-ttu-id="85083-225">展開 [搜尋屬性清單]\*\*\*\* 顯示搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="85083-225">Expand **Search Property Lists** to display the search property lists.</span></span>  
  
5.  <span data-ttu-id="85083-226">以滑鼠右鍵按一下屬性清單，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-226">Right-click the property list, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="85083-227">在 [搜尋屬性清單編輯器]\*\*\*\* 對話方塊中，使用 [屬性] 方格來加入或移除搜尋屬性：</span><span class="sxs-lookup"><span data-stu-id="85083-227">In the **Search Property List Editor** dialog box, use the Properties grid to add or remove search properties:</span></span>  
  
    1.  <span data-ttu-id="85083-228">若要移除文件屬性，請按一下屬性左邊的資料列標頭，然後按下 DEL 鍵。</span><span class="sxs-lookup"><span data-stu-id="85083-228">To remove a document property, click the row header to the left of the property, and press DEL .</span></span>  
  
    2.  <span data-ttu-id="85083-229">若要加入文件屬性，請按一下清單底部的空白資料列，右邊的 **\*** ，然後輸入新屬性的值。</span><span class="sxs-lookup"><span data-stu-id="85083-229">To add a document property, click in the empty row at the bottom of the list, to the right of the **\***, and enter the values for the new property.</span></span>  
  
         <span data-ttu-id="85083-230">如需這些值的相關資訊，請參閱 [搜尋屬性清單編輯器](../../database-engine/search-property-list-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="85083-230">For information about these values, see [Search Property List Editor](../../database-engine/search-property-list-editor.md).</span></span> <span data-ttu-id="85083-231">如需如何取得 Microsoft 所定義之屬性值的詳細資訊，請參閱 [尋找搜尋屬性的屬性集 GUID 與屬性整數識別碼](find-property-set-guids-and-property-integer-ids-for-search-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="85083-231">For information about how to obtain these values for properties defined by Microsoft, see [Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md).</span></span> <span data-ttu-id="85083-232">如需有關獨立軟體廠商 (ISV) 所定義之屬性的詳細資訊，請參閱該廠商的文件集。</span><span class="sxs-lookup"><span data-stu-id="85083-232">For information about properties defined by an independent software vendor (ISV), see the documentation of that vendor.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
###  <a name="deleting-a-search-property-list"></a><a name="deleting"></a><span data-ttu-id="85083-233">刪除搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-233">Deleting a Search Property List</span></span>  
 <span data-ttu-id="85083-234">當屬性清單與任何全文檢索索引相關聯時，您無法從資料庫中卸除該清單。</span><span class="sxs-lookup"><span data-stu-id="85083-234">You cannot drop a property list from a database while the list is associated with any full-text index.</span></span>  
  
 <span data-ttu-id="85083-235">**若要使用 Transact-SQL 刪除搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="85083-235">**To delete a search property list with Transact-SQL**</span></span>  
  
 <span data-ttu-id="85083-236">使用 [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="85083-236">Use the [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-search-property-list-transact-sql) statement.</span></span>  
  
##### <a name="to-delete-a-search-property-list-in-management-studio"></a><span data-ttu-id="85083-237">在 Management Studio 中刪除搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="85083-237">To delete a search property list in Management Studio</span></span>  
  
1.  <span data-ttu-id="85083-238">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="85083-238">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="85083-239">展開 **[資料庫]**，然後展開此資料庫。</span><span class="sxs-lookup"><span data-stu-id="85083-239">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="85083-240">展開 [儲存體]\*\*\*\*，然後展開 [搜尋屬性清單]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="85083-240">Expand **Storage**, and then expand the **Search Property Lists** node.</span></span>  
  
4.  <span data-ttu-id="85083-241">以滑鼠右鍵按一下您想要刪除的屬性清單，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85083-241">Right-click the property list that you want to delete, and click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

  
## <a name="see-also"></a><span data-ttu-id="85083-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85083-242">See Also</span></span>  
 <span data-ttu-id="85083-243">[尋找搜尋屬性的屬性集 Guid 和屬性整數識別碼](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span><span class="sxs-lookup"><span data-stu-id="85083-243">[Find Property Set GUIDs and Property Integer IDs for Search Properties](find-property-set-guids-and-property-integer-ids-for-search-properties.md) </span></span>  
 [<span data-ttu-id="85083-244">設定及管理搜尋的篩選</span><span class="sxs-lookup"><span data-stu-id="85083-244">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
