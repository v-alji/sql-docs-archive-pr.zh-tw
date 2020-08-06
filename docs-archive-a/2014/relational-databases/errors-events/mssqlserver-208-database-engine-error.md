---
title: MSSQLSERVER_208 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 97ab3eb220c03c3de0c95251861f3b947890b090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585476"
---
# <a name="mssqlserver_208"></a><span data-ttu-id="d945f-102">MSSQLSERVER_208</span><span class="sxs-lookup"><span data-stu-id="d945f-102">MSSQLSERVER_208</span></span>
    
## <a name="details"></a><span data-ttu-id="d945f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d945f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d945f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d945f-104">Product Name</span></span>|<span data-ttu-id="d945f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d945f-105">SQL Server</span></span>|  
|<span data-ttu-id="d945f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d945f-106">Event ID</span></span>|<span data-ttu-id="d945f-107">208</span><span class="sxs-lookup"><span data-stu-id="d945f-107">208</span></span>|  
|<span data-ttu-id="d945f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d945f-108">Event Source</span></span>|<span data-ttu-id="d945f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d945f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d945f-110">元件</span><span class="sxs-lookup"><span data-stu-id="d945f-110">Component</span></span>|<span data-ttu-id="d945f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d945f-111">SQLEngine</span></span>|  
|<span data-ttu-id="d945f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d945f-112">Symbolic Name</span></span>|<span data-ttu-id="d945f-113">SQ_BADOBJECT</span><span class="sxs-lookup"><span data-stu-id="d945f-113">SQ_BADOBJECT</span></span>|  
|<span data-ttu-id="d945f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d945f-114">Message Text</span></span>|<span data-ttu-id="d945f-115">無效的物件名稱 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="d945f-115">Invalid object name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d945f-116">說明</span><span class="sxs-lookup"><span data-stu-id="d945f-116">Explanation</span></span>  
 <span data-ttu-id="d945f-117">找不到指定的物件。</span><span class="sxs-lookup"><span data-stu-id="d945f-117">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="d945f-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="d945f-118">Possible Causes</span></span>  
 <span data-ttu-id="d945f-119">這項錯誤可能是由於下列其中一個問題所造成：</span><span class="sxs-lookup"><span data-stu-id="d945f-119">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="d945f-120">未正確地指定物件。</span><span class="sxs-lookup"><span data-stu-id="d945f-120">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="d945f-121">物件不存在目前的資料庫或指定的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d945f-121">The object does not exist in the current database or in the specified database.</span></span>  
  
-   <span data-ttu-id="d945f-122">雖然物件存在，但是無法向使用者公開此物件。</span><span class="sxs-lookup"><span data-stu-id="d945f-122">The object exists, but could not be exposed to the user.</span></span> <span data-ttu-id="d945f-123">例如，使用者可能沒有此物件的權限，或者此物件是在 EXECUTE 陳述式內部建立，但是卻在 EXECUTE 陳述式範圍的外部存取此物件。</span><span class="sxs-lookup"><span data-stu-id="d945f-123">For example, the user might not have permissions on the object or the object is created within an EXECUTE statement but accessed outside the scope of the EXECUTE statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d945f-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d945f-124">User Action</span></span>  
 <span data-ttu-id="d945f-125">請確認下列資訊並依適當情況更正陳述式。</span><span class="sxs-lookup"><span data-stu-id="d945f-125">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="d945f-126">物件名稱的拼字是否正確。</span><span class="sxs-lookup"><span data-stu-id="d945f-126">The object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="d945f-127">目前的資料庫內容是否正確。</span><span class="sxs-lookup"><span data-stu-id="d945f-127">The current database context is correct.</span></span> <span data-ttu-id="d945f-128">如果您沒有指定物件的資料庫名稱，此物件就必須存在目前的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d945f-128">If a database name for the object is not specified, the object must exist in the current database.</span></span> <span data-ttu-id="d945f-129">如需設定資料庫內容的詳細資訊，請參閱 [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d945f-129">For more information about setting the database context, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="d945f-130">物件是否存在系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="d945f-130">The object exists in the system tables.</span></span> <span data-ttu-id="d945f-131">若要確認資料表或其他結構描述範圍物件是否存在，請查詢 **sys.objects** 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="d945f-131">To verify whether a table or other schema-scoped object exists, query the **sys.objects** catalog view.</span></span> <span data-ttu-id="d945f-132">如果物件不在系統資料表中，表示物件已經刪除，或是使用者沒有檢視物件中繼資料的權限。</span><span class="sxs-lookup"><span data-stu-id="d945f-132">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="d945f-133">如需物件中繼資料的檢視權限詳細資訊，請參閱[中繼資料可見性組態](../security/metadata-visibility-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="d945f-133">For more information about permissions to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
-   <span data-ttu-id="d945f-134">物件是否包含在使用者的預設結構描述中。</span><span class="sxs-lookup"><span data-stu-id="d945f-134">The object is contained in the default schema of the user.</span></span> <span data-ttu-id="d945f-135">如果沒有，您就必須使用 *schema_name.object_name* 的兩部分格式來指定此物件。</span><span class="sxs-lookup"><span data-stu-id="d945f-135">If it is not, the object must be specified using the two-part format *schema_name.object_name*.</span></span> <span data-ttu-id="d945f-136">請注意，叫用純量值函式至少必須使用兩部分名稱。</span><span class="sxs-lookup"><span data-stu-id="d945f-136">Note that scalar-valued functions must always be invoked by using at least a two-part name.</span></span>  
  
-   <span data-ttu-id="d945f-137">資料庫定序是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d945f-137">The case sensitivity of the database collation.</span></span>  
  
     <span data-ttu-id="d945f-138">當資料庫使用區分大小寫的定序時，物件名稱就必須與資料庫中物件的大小寫相符。</span><span class="sxs-lookup"><span data-stu-id="d945f-138">When a database uses a case-sensitive collation, the object name must match the case of the object in the database.</span></span> <span data-ttu-id="d945f-139">例如，如果資料庫中含有區分大小寫的定序，當物件指定為 **MyTable** 時，以 **mytable** 或 **Mytable** 的形式查詢此物件會導致系統傳回錯誤 208，因為物件名稱不符。</span><span class="sxs-lookup"><span data-stu-id="d945f-139">For example, when an object is specified as **MyTable** in a database with a case sensitive collation, queries that refer to the object as **mytable** or **Mytable** will cause error 208 to return because the object names do not match.</span></span>  
  
     <span data-ttu-id="d945f-140">您可以執行下列陳述式來確認資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="d945f-140">You can verify the database collation by running the following statement.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="d945f-141">定序名稱中的縮寫 CS 表示定序會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d945f-141">The abbreviation CS in the collation name indicates the collation is case sensitive.</span></span> <span data-ttu-id="d945f-142">例如，Latin1_General_CS_AS 是區分大小寫而且區分腔調字的定序。</span><span class="sxs-lookup"><span data-stu-id="d945f-142">For example, Latin1_General_CS_AS is a case sensitive, accent sensitive collation.</span></span> <span data-ttu-id="d945f-143">CI 則表示不區分大小寫的定序。</span><span class="sxs-lookup"><span data-stu-id="d945f-143">CI indicates a case insensitive collation.</span></span>  
  
-   <span data-ttu-id="d945f-144">使用者是否擁有存取物件的權限。</span><span class="sxs-lookup"><span data-stu-id="d945f-144">The user has permission to access the object.</span></span> <span data-ttu-id="d945f-145">若要確認使用者對物件擁有的權限，請使用 **Has_Perms_By_Name** 系統函數。</span><span class="sxs-lookup"><span data-stu-id="d945f-145">To verify the permissions the user has on the object, use the **Has_Perms_By_Name** system function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d945f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d945f-146">See Also</span></span>  
 <span data-ttu-id="d945f-147">[使用 &#40;Transact-sql&#41;](/sql/t-sql/language-elements/use-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d945f-147">[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql) </span></span>  
 <span data-ttu-id="d945f-148">[中繼資料可見度設定](../security/metadata-visibility-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d945f-148">[Metadata Visibility Configuration](../security/metadata-visibility-configuration.md) </span></span>  
 [<span data-ttu-id="d945f-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d945f-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  
