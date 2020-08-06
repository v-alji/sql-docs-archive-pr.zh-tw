---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 200997dcfe7bf8a5933b9fce492daabd5baffd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702930"
---
# <a name="mssqlserver_2501"></a><span data-ttu-id="07d4f-102">MSSQLSERVER_2501</span><span class="sxs-lookup"><span data-stu-id="07d4f-102">MSSQLSERVER_2501</span></span>
    
## <a name="details"></a><span data-ttu-id="07d4f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="07d4f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07d4f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="07d4f-104">Product Name</span></span>|<span data-ttu-id="07d4f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="07d4f-105">SQL Server</span></span>|  
|<span data-ttu-id="07d4f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="07d4f-106">Event ID</span></span>|<span data-ttu-id="07d4f-107">2501</span><span class="sxs-lookup"><span data-stu-id="07d4f-107">2501</span></span>|  
|<span data-ttu-id="07d4f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="07d4f-108">Event Source</span></span>|<span data-ttu-id="07d4f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="07d4f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="07d4f-110">元件</span><span class="sxs-lookup"><span data-stu-id="07d4f-110">Component</span></span>|<span data-ttu-id="07d4f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="07d4f-111">SQLEngine</span></span>|  
|<span data-ttu-id="07d4f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="07d4f-112">Symbolic Name</span></span>|<span data-ttu-id="07d4f-113">DBCC_NO_SUCH_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07d4f-113">DBCC_NO_SUCH_TABLE_NAME</span></span>|  
|<span data-ttu-id="07d4f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="07d4f-114">Message Text</span></span>|<span data-ttu-id="07d4f-115">找不到名為 'NAME' 的資料表或物件。</span><span class="sxs-lookup"><span data-stu-id="07d4f-115">Cannot find a table or object with the name 'NAME'.</span></span> <span data-ttu-id="07d4f-116">請檢查系統目錄。</span><span class="sxs-lookup"><span data-stu-id="07d4f-116">Check the system catalog.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="07d4f-117">說明</span><span class="sxs-lookup"><span data-stu-id="07d4f-117">Explanation</span></span>  
 <span data-ttu-id="07d4f-118">找不到指定的物件。</span><span class="sxs-lookup"><span data-stu-id="07d4f-118">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="07d4f-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="07d4f-119">Possible Causes</span></span>  
 <span data-ttu-id="07d4f-120">這項錯誤可能是由於下列其中一個問題所造成：</span><span class="sxs-lookup"><span data-stu-id="07d4f-120">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="07d4f-121">未正確地指定物件。</span><span class="sxs-lookup"><span data-stu-id="07d4f-121">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="07d4f-122">物件不存在，或是在陳述式嘗試使用之前已經卸除物件。</span><span class="sxs-lookup"><span data-stu-id="07d4f-122">The object does not exist, or the object was dropped before a statement tried to use it.</span></span>  
  
-   <span data-ttu-id="07d4f-123">物件可能存在，但是無法向使用者顯示物件。</span><span class="sxs-lookup"><span data-stu-id="07d4f-123">The object might exist, but could not be exposed to the user.</span></span> <span data-ttu-id="07d4f-124">例如，使用者可能沒有物件的權限，或是物件是使用者看不到的內部資料表。</span><span class="sxs-lookup"><span data-stu-id="07d4f-124">For example, the user might not have permissions on the object, or the object is an internal table that could not be seen by a user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="07d4f-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="07d4f-125">User Action</span></span>  
  
-   <span data-ttu-id="07d4f-126">確認目前的資料庫內容是否正確。</span><span class="sxs-lookup"><span data-stu-id="07d4f-126">Verify the current database context is correct.</span></span> <span data-ttu-id="07d4f-127">如需詳細資訊，請參閱 [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="07d4f-127">For more information, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="07d4f-128">確認資料表或物件名稱拚字是否正確。</span><span class="sxs-lookup"><span data-stu-id="07d4f-128">Verify that the table or object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="07d4f-129">驗證包含物件的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="07d4f-129">Verify the schema name that contains the object.</span></span> <span data-ttu-id="07d4f-130">如果物件所屬的結構描述不是預設的結構描述 (**dbo**)，您就必須使用 *schema_name.object_name* 的兩部分格式來指定資料表或物件名稱。</span><span class="sxs-lookup"><span data-stu-id="07d4f-130">If the object belongs to a schema other than the default (**dbo**) schema, you must specify the table or object name by using the two-part format *schema_name.object_name*.</span></span>  
  
-   <span data-ttu-id="07d4f-131">確認物件是否存在系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="07d4f-131">Verify that the object exists in the system tables.</span></span> <span data-ttu-id="07d4f-132">若要確認資料表或其他結構描述範圍物件是否存在，請查詢 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="07d4f-132">To verify whether a table or other schema-scoped object exists, query the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view.</span></span> <span data-ttu-id="07d4f-133">如果物件不在系統資料表中，表示物件已經刪除，或是使用者沒有檢視物件中繼資料的權限。</span><span class="sxs-lookup"><span data-stu-id="07d4f-133">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="07d4f-134">如需如何檢視物件中繼資料的詳細資訊，請參閱[中繼資料可見性組態](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="07d4f-134">For more information about how to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d4f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07d4f-135">See Also</span></span>  
 [<span data-ttu-id="07d4f-136">目錄檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07d4f-136">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
