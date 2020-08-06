---
title: System_function_schema 中不允許使用者定義函數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7242f9fda74288a2b7354ac0550ff4966e05c555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710121"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a><span data-ttu-id="06587-102">system_function_schema 中不允許有使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="06587-102">User-defined functions are not allowed in system_function_schema</span></span>
  <span data-ttu-id="06587-103">Upgrade Advisor 偵測到使用者定義的函數，這些函式是由未記載的使用者**system_function_schema**所擁有。</span><span class="sxs-lookup"><span data-stu-id="06587-103">The Upgrade Advisor detected user-defined functions that are owned by the undocumented user **system_function_schema**.</span></span> <span data-ttu-id="06587-104">您無法藉由指定這個使用者建立使用者定義的系統函數。</span><span class="sxs-lookup"><span data-stu-id="06587-104">You cannot create a user-defined system function by specifying this user.</span></span> <span data-ttu-id="06587-105">**System_function_schema**的使用者名稱不存在，而且與此名稱相關聯的使用者識別碼 (UID = 4) 會保留給**sys**架構，而且僅限於內部使用。</span><span class="sxs-lookup"><span data-stu-id="06587-105">The **system_function_schema** user name does not exist, and the user ID that is associated with this name (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
## <a name="component"></a><span data-ttu-id="06587-106">元件</span><span class="sxs-lookup"><span data-stu-id="06587-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="06587-107">描述</span><span class="sxs-lookup"><span data-stu-id="06587-107">Description</span></span>  
 <span data-ttu-id="06587-108">系統物件儲存和存取已發生下列方式的變更：</span><span class="sxs-lookup"><span data-stu-id="06587-108">System object storage and access has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="06587-109">系統物件會儲存在唯讀的**Resource**資料庫中，而且不允許直接系統物件更新。</span><span class="sxs-lookup"><span data-stu-id="06587-109">System objects are stored in the read-only **Resource** database, and direct system object updates are not permitted.</span></span>  
  
     <span data-ttu-id="06587-110">系統物件在邏輯上會出現在每個資料庫的**sys**架構中。</span><span class="sxs-lookup"><span data-stu-id="06587-110">System objects logically appear in the **sys** schema of every database.</span></span> <span data-ttu-id="06587-111">這可藉由指定單部分函數名稱，維持從任何資料庫叫用系統函數的能力。</span><span class="sxs-lookup"><span data-stu-id="06587-111">This maintains the ability to invoke system functions from any database by specifying a one-part function name.</span></span> <span data-ttu-id="06587-112">例如，可以從任何資料庫執行 `SELECT * FROM fn_helpcollations()` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="06587-112">For example, the statement `SELECT * FROM fn_helpcollations()` can be run from any database.</span></span>  
  
-   <span data-ttu-id="06587-113">已移除未記載的使用者**system_function_schema** 。</span><span class="sxs-lookup"><span data-stu-id="06587-113">The undocumented user **system_function_schema** has been removed.</span></span>  
  
-   <span data-ttu-id="06587-114">與**system_function_schema**相關聯的使用者識別碼 (UID = 4) 會保留給**sys**架構，而且僅限於內部使用。</span><span class="sxs-lookup"><span data-stu-id="06587-114">The user ID associated with **system_function_schema** (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
 <span data-ttu-id="06587-115">這些變更對於使用者自訂系統函數具有下列影響：</span><span class="sxs-lookup"><span data-stu-id="06587-115">These changes have the following effect on user-defined system functions:</span></span>  
  
-   <span data-ttu-id="06587-116">參考**system_function_schema**的資料定義語言 (DDL) 語句將會失敗。</span><span class="sxs-lookup"><span data-stu-id="06587-116">Data Definition Language (DDL) statements that reference **system_function_schema** will fail.</span></span> <span data-ttu-id="06587-117">例如，語句 `CREATE FUNCTION system` _ `function` \_ `schema.fn` \_ `MySystemFunction` .。。將不會成功。</span><span class="sxs-lookup"><span data-stu-id="06587-117">For example, the statement `CREATE FUNCTION system`_`function`\_`schema.fn`\_`MySystemFunction` ... will not succeed.</span></span>  
  
-   <span data-ttu-id="06587-118">升級至之後 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ， **system_function_schema**所擁有的現有物件只會包含在**master**資料庫的**sys**架構中。</span><span class="sxs-lookup"><span data-stu-id="06587-118">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], existing objects that are owned by **system_function_schema** are contained only in the **sys** schema of the **master** database.</span></span> <span data-ttu-id="06587-119">由於無法修改系統物件，因此這些函數永遠不會變更或從**master**資料庫中卸載。</span><span class="sxs-lookup"><span data-stu-id="06587-119">Because system objects cannot be modified, these functions can never be changed or dropped from the **master** database.</span></span> <span data-ttu-id="06587-120">此外，您無法透過只指定單部分函數名稱，從其他資料庫叫用這些函數。</span><span class="sxs-lookup"><span data-stu-id="06587-120">Additionally, these functions cannot be invoked from other databases by specifying only a one-part function name.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="06587-121">更正動作</span><span class="sxs-lookup"><span data-stu-id="06587-121">Corrective Action</span></span>  
 <span data-ttu-id="06587-122">在升級之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="06587-122">Before you upgrade , complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="06587-123">使用**sp_changeobjectowner**系統預存程式，將現有使用者定義函數的擁有權變更為**dbo** 。</span><span class="sxs-lookup"><span data-stu-id="06587-123">Change the ownership of existing user-defined functions to **dbo** by using the **sp_changeobjectowner** system stored procedure.</span></span>  
  
2.  <span data-ttu-id="06587-124">請考慮重新命名函數，讓它不會使用前置詞 'fn_'。</span><span class="sxs-lookup"><span data-stu-id="06587-124">Consider renaming the function so that is does not use the prefix 'fn_'.</span></span> <span data-ttu-id="06587-125">這可避免與目前或未來的系統函數發生可能的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="06587-125">This will avoid potential name conflicts with current or future system functions.</span></span>  
  
3.  <span data-ttu-id="06587-126">在每個使用已修改之函數的資料庫中，加入這些函數的副本。</span><span class="sxs-lookup"><span data-stu-id="06587-126">Add a copy of the modified functions in every database that uses them.</span></span>  
  
4.  <span data-ttu-id="06587-127">在包含使用者定義函數 DDL 語句的所有腳本中，以**dbo**取代**system_function_schema**的參考。</span><span class="sxs-lookup"><span data-stu-id="06587-127">Replace references to **system_function_schema** with **dbo** in all scripts that contain user-defined function DDL statements.</span></span>  
  
5.  <span data-ttu-id="06587-128">修改用來叫用這些函式的腳本，以使用兩部分名稱 dbo **。**_function_name_，或三部分名稱_database_name_**。** 供.*function_name*。</span><span class="sxs-lookup"><span data-stu-id="06587-128">Modify scripts that invoke these functions to use either the two-part name dbo **.**_function_name_, or the three-part name _database_name_**.** dbo.*function_name*.</span></span>  
  
 <span data-ttu-id="06587-129">如需詳細資訊，請參閱《SQL Server 線上叢書》中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="06587-129">For more information, see the following topics in SQL Server Books Online:</span></span>  
  
-   <span data-ttu-id="06587-130">＜sp_changeobjectowner＞</span><span class="sxs-lookup"><span data-stu-id="06587-130">"sp_changeobjectowner"</span></span>  
  
-   <span data-ttu-id="06587-131">＜使用者結構描述分隔＞</span><span class="sxs-lookup"><span data-stu-id="06587-131">"User-schema Separation"</span></span>  
  
-   <span data-ttu-id="06587-132">＜資源資料庫＞</span><span class="sxs-lookup"><span data-stu-id="06587-132">"Resource Database"</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06587-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06587-133">See Also</span></span>  
 <span data-ttu-id="06587-134">[SQL Server 2014 Upgrade Advisor &#91;新的&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="06587-134">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="06587-135">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="06587-135">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 <span data-ttu-id="06587-136">[移除修改系統物件的語句](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span><span class="sxs-lookup"><span data-stu-id="06587-136">[Remove statements that modify system objects](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span></span>  
 [<span data-ttu-id="06587-137">移除卸除系統物件的陳述式</span><span class="sxs-lookup"><span data-stu-id="06587-137">Remove statements that drop system objects</span></span>](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
