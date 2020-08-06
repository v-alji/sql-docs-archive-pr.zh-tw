---
title: 同義字 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synonyms [SQL Server], about synonyms
ms.assetid: 6210e1d5-075f-47e4-ac8d-f84bcf26fbc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3494f4f5b13c422efb8e2a39597e131c10d81ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595879"
---
# <a name="synonyms-database-engine"></a><span data-ttu-id="6b00e-102">同義字 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="6b00e-102">Synonyms (Database Engine)</span></span>
  <span data-ttu-id="6b00e-103">同義字是具有下列用途的資料庫物件：</span><span class="sxs-lookup"><span data-stu-id="6b00e-103">A synonym is a database object that serves the following purposes:</span></span>  
  
-   <span data-ttu-id="6b00e-104">對在本機或遠端伺服器上的另一個資料庫物件 (稱為基底物件) 提供別名。</span><span class="sxs-lookup"><span data-stu-id="6b00e-104">Provides an alternative name for another database object, referred to as the base object, that can exist on a local or remote server.</span></span>  
  
-   <span data-ttu-id="6b00e-105">提供抽象層來保護用戶端應用程式，避免變更基底物件的名稱或位置。</span><span class="sxs-lookup"><span data-stu-id="6b00e-105">Provides a layer of abstraction that protects a client application from changes made to the name or location of the base object.</span></span>  
  
 <span data-ttu-id="6b00e-106">例如，以位於伺服器 **Server1** 上 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]的 **Employee**資料表為例。</span><span class="sxs-lookup"><span data-stu-id="6b00e-106">For example, consider the **Employee** table of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], located on a server named **Server1**.</span></span> <span data-ttu-id="6b00e-107">若要從另一個伺服器 **Server2**參考此資料表，用戶端應用程式使用的名稱必須包含四個部分： **Server1.AdventureWorks.Person.Employee**。</span><span class="sxs-lookup"><span data-stu-id="6b00e-107">To reference this table from another server, **Server2**, a client application would have to use the four-part name **Server1.AdventureWorks.Person.Employee**.</span></span> <span data-ttu-id="6b00e-108">另外，若是資料表的位置已變更 (例如，變更至另一個伺服器)，則必須修改用戶端應用程式以反映該變更。</span><span class="sxs-lookup"><span data-stu-id="6b00e-108">Also, if the location of the table were to change, for example, to another server, the client application would have to be modified to reflect that change.</span></span>  
  
 <span data-ttu-id="6b00e-109">若要解決這些問題，您可以在 **Server2**上建立同義字 **EmpTable** ，來代表 **Server1** 的 **Employee**資料表。</span><span class="sxs-lookup"><span data-stu-id="6b00e-109">To address both these issues, you can create a synonym, **EmpTable**, on **Server2** for the **Employee** table on **Server1**.</span></span> <span data-ttu-id="6b00e-110">現在，用戶端應用程式只需要使用 **EmpTable**單一部分的名稱，即可參考 **Employee** 資料表。</span><span class="sxs-lookup"><span data-stu-id="6b00e-110">Now, the client application only has to use the single-part name, **EmpTable**, to reference the **Employee** table.</span></span> <span data-ttu-id="6b00e-111">此外，如果 **Employee** 資料表的位置變更，您必須修改同義字 **EmpTable**以指向 **Employee** 資料表的新位置。</span><span class="sxs-lookup"><span data-stu-id="6b00e-111">Also, if the location of the **Employee** table changes, you will have to modify the synonym, **EmpTable**, to point to the new location of the **Employee** table.</span></span> <span data-ttu-id="6b00e-112">由於沒有 ALTER SYNONYM 陳述式，因此您必須先卸除同義字 **EmpTable**，再以相同的名稱重新建立同義字，但要將同義字指向 **Employee**的新位置。</span><span class="sxs-lookup"><span data-stu-id="6b00e-112">Because there is no ALTER SYNONYM statement, you first have to drop the synonym, **EmpTable**, and then re-create the synonym with the same name, but point the synonym to the new location of **Employee**.</span></span>  
  
 <span data-ttu-id="6b00e-113">同義字放在結構描述中，如同結構描述中的其他物件一樣，同義字的名稱也必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6b00e-113">A synonym belongs to a schema, and like other objects in a schema, the name of a synonym must be unique.</span></span> <span data-ttu-id="6b00e-114">您可以為下列資料庫物件建立同義字：</span><span class="sxs-lookup"><span data-stu-id="6b00e-114">You can create synonyms for the following database objects:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b00e-115">組件 (CLR) 預存程序</span><span class="sxs-lookup"><span data-stu-id="6b00e-115">Assembly (CLR) stored procedure</span></span>|<span data-ttu-id="6b00e-116">組件 (CLR) 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="6b00e-116">Assembly (CLR) table-valued function</span></span>|  
|<span data-ttu-id="6b00e-117">組件 (CLR) 純量函數</span><span class="sxs-lookup"><span data-stu-id="6b00e-117">Assembly (CLR) scalar function</span></span>|<span data-ttu-id="6b00e-118">組件 (CLR) 彙總函式</span><span class="sxs-lookup"><span data-stu-id="6b00e-118">Assembly (CLR) aggregate functions</span></span>|  
|<span data-ttu-id="6b00e-119">複寫篩選程序</span><span class="sxs-lookup"><span data-stu-id="6b00e-119">Replication-filter-procedure</span></span>|<span data-ttu-id="6b00e-120">擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="6b00e-120">Extended stored procedure</span></span>|  
|<span data-ttu-id="6b00e-121">SQL 純量函數</span><span class="sxs-lookup"><span data-stu-id="6b00e-121">SQL scalar function</span></span>|<span data-ttu-id="6b00e-122">SQL 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="6b00e-122">SQL table-valued function</span></span>|  
|<span data-ttu-id="6b00e-123">SQL 內嵌資料表值函式</span><span class="sxs-lookup"><span data-stu-id="6b00e-123">SQL inline-tabled-valued function</span></span>|<span data-ttu-id="6b00e-124">SQL 預存程序</span><span class="sxs-lookup"><span data-stu-id="6b00e-124">SQL stored procedure</span></span>|  
|<span data-ttu-id="6b00e-125">檢視</span><span class="sxs-lookup"><span data-stu-id="6b00e-125">View</span></span>|<span data-ttu-id="6b00e-126">資料表<sup>1</sup> (使用者定義)</span><span class="sxs-lookup"><span data-stu-id="6b00e-126">Table<sup>1</sup> (User-defined)</span></span>|  
  
 <span data-ttu-id="6b00e-127"><sup>1</sup>包含本機和全域臨時表</span><span class="sxs-lookup"><span data-stu-id="6b00e-127"><sup>1</sup> Includes local and global temporary tables</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b00e-128">不支援函數基底物件的四部份名稱。</span><span class="sxs-lookup"><span data-stu-id="6b00e-128">Four-part names for function base objects are not supported.</span></span>  
  
 <span data-ttu-id="6b00e-129">同義字不可為另一個同義字的基底物件，而且同義字不可以參考使用者自訂的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="6b00e-129">A synonym cannot be the base object for another synonym, and a synonym cannot reference a user-defined aggregate function.</span></span>  
  
 <span data-ttu-id="6b00e-130">同義字和基底物件之間只透過名稱繫結。</span><span class="sxs-lookup"><span data-stu-id="6b00e-130">The binding between a synonym and its base object is by name only.</span></span> <span data-ttu-id="6b00e-131">基底物件的存在性、類型及權限，全部會延遲到執行階段再檢查。</span><span class="sxs-lookup"><span data-stu-id="6b00e-131">All existence, type, and permissions checking on the base object is deferred until run time.</span></span> <span data-ttu-id="6b00e-132">因此，和原始基底物件名稱相同的另一個物件，可以修改、卸除或卸除並取代基底物件。</span><span class="sxs-lookup"><span data-stu-id="6b00e-132">Therefore, the base object can be modified, dropped, or dropped and replaced by another object that has the same name as the original base object.</span></span> <span data-ttu-id="6b00e-133">例如，以同義字 **MyContacts**為例，此同義字參考 **中的** Person.Contact [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]資料表。</span><span class="sxs-lookup"><span data-stu-id="6b00e-133">For example, consider a synonym, **MyContacts**, that references the **Person.Contact** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)].</span></span> <span data-ttu-id="6b00e-134">如果 **Contact** 資料表被卸除並由名稱為 **Person.Contact**的檢視所取代，則 **MyContacts** 會變成參考 **Person.Contact** 檢視。</span><span class="sxs-lookup"><span data-stu-id="6b00e-134">If the **Contact** table is dropped and replaced by a view named **Person.Contact**, **MyContacts** now references the **Person.Contact** view.</span></span>  
  
 <span data-ttu-id="6b00e-135">同義字的參考不受結構描述的約束。</span><span class="sxs-lookup"><span data-stu-id="6b00e-135">References to synonyms are not schema-bound.</span></span> <span data-ttu-id="6b00e-136">因此，隨時可以卸除同義字。</span><span class="sxs-lookup"><span data-stu-id="6b00e-136">Therefore, a synonym can be dropped at any time.</span></span> <span data-ttu-id="6b00e-137">不過，如果卸除同義字，已卸除的同義字有可能會留下懸吊參考。</span><span class="sxs-lookup"><span data-stu-id="6b00e-137">However, by dropping a synonym, you run the risk of leaving dangling references to the synonym that was dropped.</span></span> <span data-ttu-id="6b00e-138">只有等到執行階段才會發現這種參考。</span><span class="sxs-lookup"><span data-stu-id="6b00e-138">These references will only be found at run time.</span></span>  
  
## <a name="synonyms-and-schemas"></a><span data-ttu-id="6b00e-139">同義字和結構描述</span><span class="sxs-lookup"><span data-stu-id="6b00e-139">Synonyms and Schemas</span></span>  
 <span data-ttu-id="6b00e-140">如果預設的結構描述不是由您擁有，但您想要建立同義字，則必須使用您擁有的結構描述名稱來限定同義字名稱。</span><span class="sxs-lookup"><span data-stu-id="6b00e-140">If you have a default schema that you do not own and want to create a synonym, you must qualify the synonym name with the name of a schema that you do own.</span></span> <span data-ttu-id="6b00e-141">例如，如果您擁有結構描述 **x**，但預設結構描述是 **y** ，且您使用 CREATE SYNONYM 陳述式，則必須以結構描述 **x**作為同義字名稱的前置詞，而非使用單一部分的名稱來命名同義字。</span><span class="sxs-lookup"><span data-stu-id="6b00e-141">For example, if you own a schema **x**, but **y** is your default schema and you use the CREATE SYNONYM statement, you must prefix the name of the synonym with the schema **x**, instead of naming the synonym by using a single-part name.</span></span> <span data-ttu-id="6b00e-142">如需如何建立同義字的詳細資訊，請參閱 [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql)資料表為例。</span><span class="sxs-lookup"><span data-stu-id="6b00e-142">For more information about how to create synonyms, see [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql).</span></span>  
  
## <a name="granting-permissions-on-a-synonym"></a><span data-ttu-id="6b00e-143">授與同義字的權限</span><span class="sxs-lookup"><span data-stu-id="6b00e-143">Granting Permissions on a Synonym</span></span>  
 <span data-ttu-id="6b00e-144">只有同義字擁有者、 **db_owner**的成員或 **db_ddladmin** 的成員，才可授與同義字的權限。</span><span class="sxs-lookup"><span data-stu-id="6b00e-144">Only synonym owners, members of **db_owner**, or members of **db_ddladmin** can grant permission on a synonym.</span></span>  
  
 <span data-ttu-id="6b00e-145">您可以 GRANT、DENY、REVOKE 同義字上的任何或所有下列權限：</span><span class="sxs-lookup"><span data-stu-id="6b00e-145">You can GRANT, DENY, REVOKE all or any of the following permissions on a synonym:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b00e-146">CONTROL</span><span class="sxs-lookup"><span data-stu-id="6b00e-146">CONTROL</span></span>|<span data-ttu-id="6b00e-147">刪除</span><span class="sxs-lookup"><span data-stu-id="6b00e-147">DELETE</span></span>|  
|<span data-ttu-id="6b00e-148">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="6b00e-148">EXECUTE</span></span>|<span data-ttu-id="6b00e-149">Insert</span><span class="sxs-lookup"><span data-stu-id="6b00e-149">INSERT</span></span>|  
|<span data-ttu-id="6b00e-150">SELECT</span><span class="sxs-lookup"><span data-stu-id="6b00e-150">SELECT</span></span>|<span data-ttu-id="6b00e-151">TAKE OWNERSHIP</span><span class="sxs-lookup"><span data-stu-id="6b00e-151">TAKE OWNERSHIP</span></span>|  
|<span data-ttu-id="6b00e-152">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6b00e-152">UPDATE</span></span>|<span data-ttu-id="6b00e-153">VIEW DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6b00e-153">VIEW DEFINITION</span></span>|  
  
## <a name="using-synonyms"></a><span data-ttu-id="6b00e-154">使用同義字</span><span class="sxs-lookup"><span data-stu-id="6b00e-154">Using Synonyms</span></span>  
 <span data-ttu-id="6b00e-155">您可以使用同義字在數個 SQL 陳述式和運算式內容中取代其參考的基底物件。</span><span class="sxs-lookup"><span data-stu-id="6b00e-155">You can use synonyms in place of their referenced base object in several SQL statements and expression contexts.</span></span> <span data-ttu-id="6b00e-156">下表包含這些陳述式及運算式內容的清單：</span><span class="sxs-lookup"><span data-stu-id="6b00e-156">The following table contains a list of these statements and expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b00e-157">SELECT</span><span class="sxs-lookup"><span data-stu-id="6b00e-157">SELECT</span></span>|<span data-ttu-id="6b00e-158">Insert</span><span class="sxs-lookup"><span data-stu-id="6b00e-158">INSERT</span></span>|  
|<span data-ttu-id="6b00e-159">UPDATE</span><span class="sxs-lookup"><span data-stu-id="6b00e-159">UPDATE</span></span>|<span data-ttu-id="6b00e-160">刪除</span><span class="sxs-lookup"><span data-stu-id="6b00e-160">DELETE</span></span>|  
|<span data-ttu-id="6b00e-161">執行 CREATE 陳述式之前，請先執行</span><span class="sxs-lookup"><span data-stu-id="6b00e-161">EXECUTE</span></span>|<span data-ttu-id="6b00e-162">子 SELECT</span><span class="sxs-lookup"><span data-stu-id="6b00e-162">Sub-selects</span></span>|  
  
 <span data-ttu-id="6b00e-163">當您正在先前陳述的內容中使用同義字時，基底物件會受影響。</span><span class="sxs-lookup"><span data-stu-id="6b00e-163">When you are working with synonyms in the contexts previously stated, the base object is affected.</span></span> <span data-ttu-id="6b00e-164">例如，如果同義字參考的基底物件是資料表，而且您將資料列插入同義字，則實際上您是將資料列插入參考的資料表。</span><span class="sxs-lookup"><span data-stu-id="6b00e-164">For example, if a synonym references a base object that is a table and you insert a row into the synonym, you are actually inserting a row into the referenced table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b00e-165">您無法參考位於連結伺的服器上的同義字。</span><span class="sxs-lookup"><span data-stu-id="6b00e-165">You cannot reference a synonym that is located on a linked server.</span></span>  
  
 <span data-ttu-id="6b00e-166">您可以使用同義字做為 OBJECT_ID 函數的參數。不過，此函數會傳回同義字的物件識別碼，而非基底物件。</span><span class="sxs-lookup"><span data-stu-id="6b00e-166">You can use a synonym as the parameter for the OBJECT_ID function; however, the function returns the object ID of the synonym, not the base object.</span></span>  
  
 <span data-ttu-id="6b00e-167">您無法在 DDL 陳述式中參考同義字。</span><span class="sxs-lookup"><span data-stu-id="6b00e-167">You cannot reference a synonym in a DDL statement.</span></span> <span data-ttu-id="6b00e-168">例如，下列陳述式 (參考名為 `dbo.MyProduct`的同義字) 會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="6b00e-168">For example, the following statements, which reference a synonym named `dbo.MyProduct`, generate errors:</span></span>  
  
```  
ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null;  
EXEC ('ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null');  
```  
  
 <span data-ttu-id="6b00e-169">下列權限陳述式只與同義字有關聯，但與基底物件無關：</span><span class="sxs-lookup"><span data-stu-id="6b00e-169">The following permission statements are associated only with the synonym and not the base object:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b00e-170">GRANT</span><span class="sxs-lookup"><span data-stu-id="6b00e-170">GRANT</span></span>|<span data-ttu-id="6b00e-171">拒絕</span><span class="sxs-lookup"><span data-stu-id="6b00e-171">DENY</span></span>|  
|<span data-ttu-id="6b00e-172">REVOKE</span><span class="sxs-lookup"><span data-stu-id="6b00e-172">REVOKE</span></span>||  
  
 <span data-ttu-id="6b00e-173">同義字不是結構描述繫結性質，因此，下列結構描述繫結的運算式內容無法參考同義字：</span><span class="sxs-lookup"><span data-stu-id="6b00e-173">Synonyms are not schema-bound and, therefore, cannot be referenced by the following schema-bound expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b00e-174">CHECK 條件約束</span><span class="sxs-lookup"><span data-stu-id="6b00e-174">CHECK constraints</span></span>|<span data-ttu-id="6b00e-175">計算資料行</span><span class="sxs-lookup"><span data-stu-id="6b00e-175">Computed columns</span></span>|  
|<span data-ttu-id="6b00e-176">預設運算式</span><span class="sxs-lookup"><span data-stu-id="6b00e-176">Default expressions</span></span>|<span data-ttu-id="6b00e-177">規則運算式</span><span class="sxs-lookup"><span data-stu-id="6b00e-177">Rule expressions</span></span>|  
|<span data-ttu-id="6b00e-178">結構描述繫結的檢視</span><span class="sxs-lookup"><span data-stu-id="6b00e-178">Schema-bound views</span></span>|<span data-ttu-id="6b00e-179">結構描述繫結的函數</span><span class="sxs-lookup"><span data-stu-id="6b00e-179">Schema-bound functions</span></span>|  
  
 <span data-ttu-id="6b00e-180">如需結構描述繫結函數的詳細資訊，請參閱[建立使用者定義函數 &#40;Database Engine&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="6b00e-180">For more information about schema-bound functions, see [Create User-defined Functions &#40;Database Engine&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md).</span></span>  
  
## <a name="getting-information-about-synonyms"></a><span data-ttu-id="6b00e-181">取得同義字的相關資訊</span><span class="sxs-lookup"><span data-stu-id="6b00e-181">Getting Information About Synonyms</span></span>  
 <span data-ttu-id="6b00e-182">Sys.synonyms 目錄檢視含有一個關於給定資料庫中各個同義字的項目。</span><span class="sxs-lookup"><span data-stu-id="6b00e-182">The sys.synonyms catalog view contains an entry for each synonym in a given database.</span></span> <span data-ttu-id="6b00e-183">此目錄檢視會公開同義字中繼資料，例如同義字的名稱與基底物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b00e-183">This catalog view exposes synonym metadata such as the name of the synonym and the name of the base object.</span></span> <span data-ttu-id="6b00e-184">如需目錄檢視的詳細資訊 `sys.synonyms` ，請參閱[&#40;transact-sql&#41;的 sys.databases ](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b00e-184">For more information about the `sys.synonyms` catalog view, see [sys.synonyms &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql).</span></span>  
  
 <span data-ttu-id="6b00e-185">透過擴充屬性的運用，您可以將描述性或指示性文字、輸入遮罩以及格式化規則新增為同義字的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b00e-185">By using extended properties, you can add descriptive or instructional text, input masks, and formatting rules as properties of a synonym.</span></span> <span data-ttu-id="6b00e-186">由於屬性儲存在資料庫中，因此讀取屬性的所有應用程式都能夠以同樣的方式評估物件。</span><span class="sxs-lookup"><span data-stu-id="6b00e-186">Because the property is stored in the database, all applications that read the property can evaluate the object in the same way.</span></span> <span data-ttu-id="6b00e-187">如需詳細資訊，請參閱 [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b00e-187">For more information, see [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span></span>  
  
 <span data-ttu-id="6b00e-188">若要尋找同義字基底物件的基底類型，請使用 OBJECTPROPERTYEX 函數。</span><span class="sxs-lookup"><span data-stu-id="6b00e-188">To find the base type of the base object of a synonym, use the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="6b00e-189">如需詳細資訊，請參閱 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6b00e-189">For more information, see [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="6b00e-190">範例</span><span class="sxs-lookup"><span data-stu-id="6b00e-190">Examples</span></span>  
 <span data-ttu-id="6b00e-191">以下範例將傳回屬於本機物件之同義字基底物件的基底類型。</span><span class="sxs-lookup"><span data-stu-id="6b00e-191">The following example returns the base type of a synonym's base object that is a local object.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee   
FOR AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyEmployee'), 'BaseType') AS BaseType;  
```  
  
 <span data-ttu-id="6b00e-192">以下範例將傳回屬於遠端物件 (位於 `Server1`伺服器上) 之同義字基底物件的基底類型。</span><span class="sxs-lookup"><span data-stu-id="6b00e-192">The following example returns the base type of a synonym's base object that is a remote object located on a server named `Server1`.</span></span>  
  
```  
EXECUTE sp_addlinkedserver Server1;  
GO  
CREATE SYNONYM MyRemoteEmployee  
FOR Server1.AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyRemoteEmployee'), 'BaseType') AS BaseType;  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="6b00e-193">相關內容</span><span class="sxs-lookup"><span data-stu-id="6b00e-193">Related Content</span></span>  
 [<span data-ttu-id="6b00e-194">建立同義字</span><span class="sxs-lookup"><span data-stu-id="6b00e-194">Create Synonyms</span></span>](create-synonyms.md)  
  
 [<span data-ttu-id="6b00e-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b00e-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
  
 [<span data-ttu-id="6b00e-196">DROP SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b00e-196">DROP SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-synonym-transact-sql)  
  
  
