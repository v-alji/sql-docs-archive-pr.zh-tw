---
title: 新增搜尋屬性清單 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599655"
---
# <a name="new-search-property-list"></a><span data-ttu-id="73ea5-102">新增搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="73ea5-102">New Search Property List</span></span>
  <span data-ttu-id="73ea5-103">使用這個對話方塊來建立搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="73ea5-103">Use this dialog box to create a search property list.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73ea5-104">選項</span><span class="sxs-lookup"><span data-stu-id="73ea5-104">Options</span></span>  
 <span data-ttu-id="73ea5-105">**搜尋屬性清單名稱**</span><span class="sxs-lookup"><span data-stu-id="73ea5-105">**Search property list name**</span></span>  
 <span data-ttu-id="73ea5-106">請輸入搜尋屬性清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="73ea5-106">Enter the name of the search property list.</span></span>  
  
 <span data-ttu-id="73ea5-107">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="73ea5-107">**Owner**</span></span>  
 <span data-ttu-id="73ea5-108">指定搜尋屬性清單的擁有者。</span><span class="sxs-lookup"><span data-stu-id="73ea5-108">Specify the owner of the search property list.</span></span> <span data-ttu-id="73ea5-109">如果您想要將擁有權指派給自己 (亦即，目前的使用者)，請將這個欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="73ea5-109">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span> <span data-ttu-id="73ea5-110">若要指定不同的使用者，請按一下瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="73ea5-110">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-search-property-list-options"></a><span data-ttu-id="73ea5-111">建立搜尋屬性清單選項</span><span class="sxs-lookup"><span data-stu-id="73ea5-111">Create Search Property List Options</span></span>  
 <span data-ttu-id="73ea5-112">請按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="73ea5-112">Click one of the following options:</span></span>  
  
 <span data-ttu-id="73ea5-113">**建立空的搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="73ea5-113">**Create an empty search property list**</span></span>  
 <span data-ttu-id="73ea5-114">建立沒有任何屬性的搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="73ea5-114">Creates a search property list without any properties.</span></span>  
  
 <span data-ttu-id="73ea5-115">**從現有搜尋屬性清單建立**</span><span class="sxs-lookup"><span data-stu-id="73ea5-115">**Create from an existing search property list**</span></span>  
 <span data-ttu-id="73ea5-116">將現有搜尋屬性清單的屬性複製到新的屬性清單中。</span><span class="sxs-lookup"><span data-stu-id="73ea5-116">Copies the properties of an existing search property list into the new property list.</span></span> <span data-ttu-id="73ea5-117">搜尋屬性清單是資料庫物件，所以您必須指定包含要複製之屬性清單的資料庫。</span><span class="sxs-lookup"><span data-stu-id="73ea5-117">Search property lists are database objects, so you must specify the database that contains the property list that you want to copy.</span></span>  
  
 <span data-ttu-id="73ea5-118">**源資料庫**</span><span class="sxs-lookup"><span data-stu-id="73ea5-118">**Source database**</span></span>  
 <span data-ttu-id="73ea5-119">指定現有搜尋屬性清單所屬的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="73ea5-119">Specify the name of the database to which the existing search property list belongs.</span></span> <span data-ttu-id="73ea5-120">系統預設會選取目前的資料庫。</span><span class="sxs-lookup"><span data-stu-id="73ea5-120">The current database is selected by default.</span></span> <span data-ttu-id="73ea5-121">另外，如果目前連接與另一個資料庫中的使用者識別碼相關聯，您也可以選擇使用清單方塊來選取該資料庫。</span><span class="sxs-lookup"><span data-stu-id="73ea5-121">Optionally, you can use the list box to select another database, if your current connection is associated with a user ID in that database.</span></span>  
  
 <span data-ttu-id="73ea5-122">**來源搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="73ea5-122">**Source search property list**</span></span>  
 <span data-ttu-id="73ea5-123">從屬於選取之資料庫的搜尋屬性清單，選取現有的搜尋屬性清單名稱。</span><span class="sxs-lookup"><span data-stu-id="73ea5-123">Select the name of an existing search property list from those belonging to the selected database.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="73ea5-124">權限</span><span class="sxs-lookup"><span data-stu-id="73ea5-124">Permissions</span></span>  
 <span data-ttu-id="73ea5-125">請參閱[&#40;transact-sql&#41;建立搜尋屬性清單](/sql/t-sql/statements/create-search-property-list-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="73ea5-125">See [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="73ea5-126">若要使用 SQL Server Management Studio 管理搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="73ea5-126">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="73ea5-127">如需如何建立、檢視、變更或刪除搜尋屬性清單，以及如何設定全文檢索索引以進行屬性搜尋的詳細資訊，請參閱＜ [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md)＞。</span><span class="sxs-lookup"><span data-stu-id="73ea5-127">For information about how to create, view, change, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ea5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73ea5-128">See Also</span></span>  
 <span data-ttu-id="73ea5-129">[建立搜尋屬性清單 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73ea5-129">[CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="73ea5-130">[使用搜尋屬性清單搜尋文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="73ea5-130">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="73ea5-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="73ea5-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
