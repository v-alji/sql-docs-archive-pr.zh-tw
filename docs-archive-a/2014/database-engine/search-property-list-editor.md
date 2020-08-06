---
title: 搜尋屬性清單編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c68ec986e2c6f4f53dfec7f188ba2a120532ae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594671"
---
# <a name="search-property-list-editor"></a><span data-ttu-id="5fadd-102">搜尋屬性清單編輯器</span><span class="sxs-lookup"><span data-stu-id="5fadd-102">Search Property List Editor</span></span>
  <span data-ttu-id="5fadd-103">使用此對話方塊來新增或刪除搜尋屬性清單中的搜尋屬性。</span><span class="sxs-lookup"><span data-stu-id="5fadd-103">Use this dialog box to add or delete search properties in a search property list.</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="5fadd-104">若要使用 SQL Server Management Studio 管理搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="5fadd-104">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="5fadd-105">如需如何建立、查看或刪除搜尋屬性清單，以及如何設定全文檢索索引以進行屬性搜尋的詳細資訊，請參閱[使用搜尋屬性清單搜尋文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="5fadd-105">For information about how to create, view, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5fadd-106">選項</span><span class="sxs-lookup"><span data-stu-id="5fadd-106">Options</span></span>  
 <span data-ttu-id="5fadd-107">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="5fadd-107">**Property Name**</span></span>  
 <span data-ttu-id="5fadd-108">指定要用來識別全文檢索查詢中之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fadd-108">Specify the name to be used to identify the property in full-text queries.</span></span> <span data-ttu-id="5fadd-109">屬性名稱可以包含內部空格。</span><span class="sxs-lookup"><span data-stu-id="5fadd-109">A property name can contain internal spaces.</span></span> <span data-ttu-id="5fadd-110">**[屬性名稱]** 的最大長度為 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="5fadd-110">The maximum length of **Property Name** is 256 characters.</span></span> <span data-ttu-id="5fadd-111">這個名稱可以是使用者易記名稱，例如「作者」或「住家地址」，或者它可以是屬性的 Windows 正式名稱，例如 `System.Author` 或 `System.Contact.HomeAddress`。</span><span class="sxs-lookup"><span data-stu-id="5fadd-111">This name can be a user-friendly name, such as "Author" or "Home Address", or it can be the Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span> <span data-ttu-id="5fadd-112">**[屬性名稱]** 必須唯一識別屬性集內的屬性。</span><span class="sxs-lookup"><span data-stu-id="5fadd-112">**Property Name** must uniquely identify the property within the property set.</span></span>  
  
 <span data-ttu-id="5fadd-113">開發人員使用屬性名稱來識別 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 述詞中的屬性。</span><span class="sxs-lookup"><span data-stu-id="5fadd-113">Developers use the property name to identify the property in the [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate.</span></span> <span data-ttu-id="5fadd-114">因此，在加入屬性時，務必指定可有意義地表示屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5fadd-114">Therefore, when adding a property it is important to specify a value that meaningfully represents the property.</span></span>  
  
 <span data-ttu-id="5fadd-115">**屬性集 GUID**</span><span class="sxs-lookup"><span data-stu-id="5fadd-115">**Property Set GUID**</span></span>  
 <span data-ttu-id="5fadd-116">指定屬性所屬之屬性集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5fadd-116">Specify the identifier of the property set to which the property belongs.</span></span> <span data-ttu-id="5fadd-117">這是全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="5fadd-117">This is a globally unique identifier (GUID).</span></span> <span data-ttu-id="5fadd-118">屬性集是一組邏輯相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="5fadd-118">A property set is a group of logically related properties.</span></span> <span data-ttu-id="5fadd-119">如需有關取得此值的詳細資訊，請參閱本主題稍後的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="5fadd-119">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
 <span data-ttu-id="5fadd-120">**屬性 Int 識別碼**</span><span class="sxs-lookup"><span data-stu-id="5fadd-120">**Property Int ID**</span></span>  
 <span data-ttu-id="5fadd-121">指定屬性的屬性整數識別碼。</span><span class="sxs-lookup"><span data-stu-id="5fadd-121">Specify the property integer identifier of the property.</span></span> <span data-ttu-id="5fadd-122">這個預先指派的值是屬性集內唯一的正整數。</span><span class="sxs-lookup"><span data-stu-id="5fadd-122">This pre-assigned value is a positive integer that is unique within the property set.</span></span> <span data-ttu-id="5fadd-123">如需有關取得此值的詳細資訊，請參閱本主題稍後的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="5fadd-123">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fadd-124">全文檢索搜尋不支援使用字串識別碼的文件屬性。</span><span class="sxs-lookup"><span data-stu-id="5fadd-124">Document properties that use string identifiers are not supported by full-text search.</span></span>  
  
 <span data-ttu-id="5fadd-125">**屬性描述**</span><span class="sxs-lookup"><span data-stu-id="5fadd-125">**Property Description**</span></span>  
 <span data-ttu-id="5fadd-126">選擇性地指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5fadd-126">Optionally, specify a description of the property.</span></span> <span data-ttu-id="5fadd-127">這是最多 512 個字元的字串。</span><span class="sxs-lookup"><span data-stu-id="5fadd-127">This is a string of up to 512 characters.</span></span> <span data-ttu-id="5fadd-128">例如，描述可能包含有關屬性所屬之屬性集的詳細資訊，或有關與其名稱不盡相符之屬性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5fadd-128">For example, a description could contain information about the property set of the property or information about a property that is not evident from its name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fadd-129">備註</span><span class="sxs-lookup"><span data-stu-id="5fadd-129">Remarks</span></span>  
 <span data-ttu-id="5fadd-130">若要將搜尋屬性加入至搜尋屬性清單，您必須指定屬性所屬之屬性集的全域唯一識別碼 (GUID)，以及屬性的屬性整數識別碼。</span><span class="sxs-lookup"><span data-stu-id="5fadd-130">To add a search property to a search property list, you must specify the globally unique identifier (GUID) of the property set to which the property belongs and the property integer identifier of the property.</span></span> <span data-ttu-id="5fadd-131">兩者的指定組合在給定的搜尋屬性清單中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5fadd-131">A given combination of these must be unique in a given search property list.</span></span> <span data-ttu-id="5fadd-132">如果您嘗試加入現有的組合，作業就會失敗並發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="5fadd-132">If you try to add an existing combination, the operation fails and issues an error.</span></span> <span data-ttu-id="5fadd-133">這表示您只能設定給定屬性的一個名稱。</span><span class="sxs-lookup"><span data-stu-id="5fadd-133">This means that you can configure only one name for a given property.</span></span>  
  
 <span data-ttu-id="5fadd-134">屬性描述是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5fadd-134">The property description is optional.</span></span>  
  
 <span data-ttu-id="5fadd-135">**若要設定全文檢索索引的屬性搜尋清單**</span><span class="sxs-lookup"><span data-stu-id="5fadd-135">**To configure a search property list for a full-text index**</span></span>  
  
-   [<span data-ttu-id="5fadd-136">使用搜索屬性清單搜索文件屬性</span><span class="sxs-lookup"><span data-stu-id="5fadd-136">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a><span data-ttu-id="5fadd-137">權限</span><span class="sxs-lookup"><span data-stu-id="5fadd-137">Permissions</span></span>  
 <span data-ttu-id="5fadd-138">請參閱[ALTER SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5fadd-138">See [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fadd-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fadd-139">See Also</span></span>  
 <span data-ttu-id="5fadd-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5fadd-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="5fadd-141">[使用搜尋屬性清單搜尋文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="5fadd-141">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="5fadd-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5fadd-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
