---
title: 重新命名使用者定義函式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
ms.openlocfilehash: ec923be64cf7819c4018ebda71a472f58b29cf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607321"
---
# <a name="rename-user-defined-functions"></a><span data-ttu-id="e73b7-102">重新命名使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="e73b7-102">Rename User-defined Functions</span></span>
  <span data-ttu-id="e73b7-103">您可以透過使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，重新命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="e73b7-103">You can rename user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e73b7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e73b7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e73b7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e73b7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e73b7-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="e73b7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e73b7-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e73b7-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e73b7-108">**若要使用下列項目重新命名使用者定義函數：**</span><span class="sxs-lookup"><span data-stu-id="e73b7-108">**To rename user-defined functions, using:**</span></span>  
  
     [<span data-ttu-id="e73b7-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e73b7-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e73b7-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e73b7-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e73b7-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="e73b7-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e73b7-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="e73b7-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e73b7-113">函數名稱必須符合 [識別碼](../databases/database-identifiers.md)的規則。</span><span class="sxs-lookup"><span data-stu-id="e73b7-113">Function names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="e73b7-114">重新命名使用者定義函數，不會變更 **sys.sql_modules** 目錄檢視 definition 資料行中對應的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="e73b7-114">Renaming a user-defined function will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="e73b7-115">因此，我們建議您不要重新命名這個物件類型。</span><span class="sxs-lookup"><span data-stu-id="e73b7-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="e73b7-116">相反地，請卸除預存程序，再利用它的新名稱來重新建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="e73b7-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="e73b7-117">變更使用者定義函數的名稱或定義後，若未更新物件來反映對此函數所做的變更，則可能導致依存物件執行失敗。</span><span class="sxs-lookup"><span data-stu-id="e73b7-117">Changing the name or definition of a user-defined function can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e73b7-118">Security</span><span class="sxs-lookup"><span data-stu-id="e73b7-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e73b7-119">權限</span><span class="sxs-lookup"><span data-stu-id="e73b7-119">Permissions</span></span>  
 <span data-ttu-id="e73b7-120">若要卸除函數，需要函數所屬結構描述的 ALTER 權限，或函數的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="e73b7-120">To drop the function, requires either ALTER permission on the schema to which the function belongs or CONTROL permission on the function.</span></span> <span data-ttu-id="e73b7-121">若要重新建立函數，需要資料庫的 CREATE FUNCTION 權限，以及此函數建立所在之結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="e73b7-121">To re-create the function, requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e73b7-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e73b7-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-user-defined-functions"></a><span data-ttu-id="e73b7-123">若要重新命名使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="e73b7-123">To rename user-defined functions</span></span>  
  
1.  <span data-ttu-id="e73b7-124">在 **[物件總管]** 中，按一下資料庫旁邊的加號，此資料庫包含要重新命名的函數。</span><span class="sxs-lookup"><span data-stu-id="e73b7-124">In **Object Explorer**, click the plus sign next to the database that contains the function you wish to rename and then</span></span>  
  
2.  <span data-ttu-id="e73b7-125">按一下 **[可程式性]** 資料夾旁的加號。</span><span class="sxs-lookup"><span data-stu-id="e73b7-125">Click the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="e73b7-126">按一下包含要重新命名之函數的資料夾旁邊的加號：</span><span class="sxs-lookup"><span data-stu-id="e73b7-126">Click the plus sign next to the folder that contains the function you wish to rename:</span></span>  
  
    -   <span data-ttu-id="e73b7-127">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="e73b7-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="e73b7-128">純量值函式</span><span class="sxs-lookup"><span data-stu-id="e73b7-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="e73b7-129">彙總函式</span><span class="sxs-lookup"><span data-stu-id="e73b7-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="e73b7-130">以滑鼠右鍵按一下您要重新命名的函數，然後選取 [重新命名]  。</span><span class="sxs-lookup"><span data-stu-id="e73b7-130">Right-click the function you wish to rename and select **Rename**.</span></span>  
  
5.  <span data-ttu-id="e73b7-131">輸入函式的新名稱。</span><span class="sxs-lookup"><span data-stu-id="e73b7-131">Enter the function's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e73b7-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e73b7-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="e73b7-133">**若要重新命名使用者定義函數**</span><span class="sxs-lookup"><span data-stu-id="e73b7-133">**To rename user-defined functions**</span></span>  
  
 <span data-ttu-id="e73b7-134">您無法使用 Transact-SQL 陳述式來執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="e73b7-134">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="e73b7-135">若要使用 Transact-SQL 來重新命名使用者定義函數，您必須先刪除現有的函數，然後使用新的名稱來重新建立函數。</span><span class="sxs-lookup"><span data-stu-id="e73b7-135">To rename a user-defined function using Transact-SQL, you must first delete the existing function and then re-create it with the new name.</span></span> <span data-ttu-id="e73b7-136">確定使用函式舊名稱的所有程式碼和應用程式現在都使用新名稱。</span><span class="sxs-lookup"><span data-stu-id="e73b7-136">Ensure that all code and applications that used the function's old name now use the new name.</span></span>  
  
 <span data-ttu-id="e73b7-137">如需詳細資訊，請參閱 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) 和 [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e73b7-137">For more information, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) and [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73b7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e73b7-138">See Also</span></span>  
 <span data-ttu-id="e73b7-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e73b7-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span></span>  
 [<span data-ttu-id="e73b7-140">檢視使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="e73b7-140">View User-defined Functions</span></span>](user-defined-functions.md)  
  
  
