---
title: 重新編譯預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sp_recompile
- WITH RECOMPILE clause
- recompiling stored procedures
- stored procedures [SQL Server], recompiling
ms.assetid: b90deb27-0099-4fe7-ba60-726af78f7c18
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a9bc0e1d4baecb7f4c66b83b57081ed3131123d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607359"
---
# <a name="recompile-a-stored-procedure"></a><span data-ttu-id="d2ec9-102">重新編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="d2ec9-102">Recompile a Stored Procedure</span></span>
  <span data-ttu-id="d2ec9-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 重新編譯 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-103">This topic describes how to recompile a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d2ec9-104">有三種方式可以執行這項操作： `WITH RECOMPILE` 程序定義中或呼叫程式時的選項、 `RECOMPILE` 個別語句上的查詢提示，或是使用 `sp_recompile` 系統預存程式。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-104">There are three ways to do this: `WITH RECOMPILE` option in the procedure definition or when the procedure is called, the `RECOMPILE` query hint on individual statements, or by using the `sp_recompile` system stored procedure.</span></span> <span data-ttu-id="d2ec9-105">本主題描述在建立程序定義及執行現有程序時使用 WITH RECOMPILE 選項。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-105">This topic describes using the WITH RECOMPILE option when creating a procedure definition and executing an existing procedure.</span></span> <span data-ttu-id="d2ec9-106">另外還會描述使用 sp_recompile 系統預存程序重新編譯現有的程序。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-106">It also describes using the sp_recompile system stored procedure to recompile an existing procedure.</span></span>  
  
 <span data-ttu-id="d2ec9-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d2ec9-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d2ec9-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d2ec9-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d2ec9-109">建議</span><span class="sxs-lookup"><span data-stu-id="d2ec9-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d2ec9-110">安全性</span><span class="sxs-lookup"><span data-stu-id="d2ec9-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d2ec9-111">**使用下列方法重新編譯預存程序：**</span><span class="sxs-lookup"><span data-stu-id="d2ec9-111">**To recompile a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="d2ec9-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d2ec9-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d2ec9-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="d2ec9-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d2ec9-114">建議</span><span class="sxs-lookup"><span data-stu-id="d2ec9-114">Recommendations</span></span>  
  
-   <span data-ttu-id="d2ec9-115">初次編譯或重新編譯程序時，該程序的查詢計劃會針對資料庫及其物件目前狀態最佳化。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-115">When a procedure is compiled for the first time or recompiled, the procedure's query plan is optimized for the current state of the database and its objects.</span></span> <span data-ttu-id="d2ec9-116">如果資料庫的資料或結構經歷大幅變更，則重新編譯程序時，會針對這些變更更新並最佳化程序的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-116">If a database undergoes significant changes to its data or structure, recompiling a procedure updates and optimizes the procedure's query plan for those changes.</span></span> <span data-ttu-id="d2ec9-117">如此可以提高程序的處理效能。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-117">This can improve the procedure's processing performance.</span></span>  
  
-   <span data-ttu-id="d2ec9-118">有時候程序必須強制重新編譯，有時候則會自動重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-118">There are times when procedure recompilation must be forced and other times when it occurs automatically.</span></span> <span data-ttu-id="d2ec9-119">只要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新啟動，自動重新編譯就會發生。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-119">Automatic recompiling occurs whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span> <span data-ttu-id="d2ec9-120">若程序所參考的基礎資料表經過實體設計變更，則也會進行重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-120">It also occurs if an underlying table referenced by the procedure has undergone physical design changes.</span></span>  
  
-   <span data-ttu-id="d2ec9-121">另一個強制程序重新編譯的理由是可以抵制程序編譯的「參數探測」行為。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-121">Another reason to force a procedure to recompile is to counteract the "parameter sniffing" behavior of procedure compilation.</span></span> <span data-ttu-id="d2ec9-122">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行程序時，程序在編譯時所使用的任何參數值都會包含在產生查詢計畫的過程中。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-122">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes procedures, any parameter values that are used by the procedure when it compiles are included as part of generating the query plan.</span></span> <span data-ttu-id="d2ec9-123">如果這些值代表程序後續呼叫的典型值，則程序在每次編譯和執行時都可獲得查詢計劃的好處。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-123">If these values represent the typical ones with which the procedure is subsequently called, then the procedure benefits from the query plan every time that it compiles and executes.</span></span> <span data-ttu-id="d2ec9-124">如果程序上的參數值經常是非典型的，則依據不同參數值強制重新編譯程序及新計畫可改善效能。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-124">If parameter values on the procedure are frequently atypical, forcing a recompile of the procedure and a new plan based on different parameter values can improve performance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d2ec9-125">的特色功能在於程序的陳述式層級重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-125">features statement-level recompilation of procedures.</span></span> <span data-ttu-id="d2ec9-126">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新編譯預存程序時，只會編譯造成重新編譯的陳述式，而不是完整程序。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recompiles stored procedures, only the statement that caused the recompilation is compiled, instead of the complete procedure.</span></span>  
  
-   <span data-ttu-id="d2ec9-127">如果程序中的特定查詢固定使用非典型或暫存值，則可在這些查詢中使用 RECOMPILE 查詢提示來改善程序效能。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-127">If certain queries in a procedure regularly use atypical or temporary values, procedure performance can be improved by using the RECOMPILE query hint inside those queries.</span></span> <span data-ttu-id="d2ec9-128">由於只會重新編譯使用查詢提示的查詢，而非完整程序，因此會模仿 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的陳述式層級重新編譯行為。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-128">Since only the queries using the query hint will be recompiled instead of the complete procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]'s statement-level recompilation behavior is mimicked.</span></span> <span data-ttu-id="d2ec9-129">不過，除了使用程序目前的參數值之外，RECOMPILE 查詢提示也會在您編譯陳述式時，使用預存程序內任何區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-129">But in addition to using the procedure's current parameter values, the RECOMPILE query hint also uses the values of any local variables inside the stored procedure when you compile the statement.</span></span> <span data-ttu-id="d2ec9-130">如需詳細資訊，請參閱 [查詢提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-130">For more information, see [Query Hint (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d2ec9-131">Security</span><span class="sxs-lookup"><span data-stu-id="d2ec9-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d2ec9-132">權限</span><span class="sxs-lookup"><span data-stu-id="d2ec9-132">Permissions</span></span>  
 <span data-ttu-id="d2ec9-133">`WITH RECOMPILE`件</span><span class="sxs-lookup"><span data-stu-id="d2ec9-133">`WITH RECOMPILE` Option</span></span>  
 <span data-ttu-id="d2ec9-134">如果在建立程序定義時使用此選項，則需要資料庫的 CREATE PROCEDURE 權限以及建立程序所在結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-134">If this option is used when the procedure definition is created, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="d2ec9-135">如果在 EXECUTE 陳述式中使用此選項，則需要程序的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-135">If this option is used in an EXECUTE statement, it requires EXECUTE permissions on the procedure.</span></span> <span data-ttu-id="d2ec9-136">EXECUTE 陳述式本身並不需要權限，但是 EXECUTE 陳述式中參考的程序需要執行權限。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-136">Permissions are not required on the EXECUTE statement itself but execute permissions are required on the procedure referenced in the EXECUTE statement.</span></span> <span data-ttu-id="d2ec9-137">如需詳細資訊，請參閱 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-137">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
 <span data-ttu-id="d2ec9-138">`RECOMPILE`查詢提示</span><span class="sxs-lookup"><span data-stu-id="d2ec9-138">`RECOMPILE` Query Hint</span></span>  
 <span data-ttu-id="d2ec9-139">此功能是在建立程序時使用，而且提示會包含在程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-139">This feature is used when the procedure is created and the hint is included in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure.</span></span> <span data-ttu-id="d2ec9-140">因此，它需要資料庫的 CREATE PROCEDURE 權限，以及建立程序所在結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-140">Therefore, it requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
 <span data-ttu-id="d2ec9-141">`sp_recompile`系統預存程式</span><span class="sxs-lookup"><span data-stu-id="d2ec9-141">`sp_recompile` System Stored Procedure</span></span>  
 <span data-ttu-id="d2ec9-142">需要指定之程序的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-142">Requires ALTER permission on the specified procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d2ec9-143">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d2ec9-143">Using Transact-SQL</span></span>  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="d2ec9-144">若要使用 WITH RECOMPILE 選項重新編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="d2ec9-144">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="d2ec9-145">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-145">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d2ec9-146">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-146">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d2ec9-147">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d2ec9-148">此範例會建立程序定義。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-148">This example creates the procedure definition.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
    DROP PROCEDURE dbo.uspProductByVendor;  
GO  
CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
WITH RECOMPILE  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
    FROM Purchasing.Vendor AS v   
    JOIN Purchasing.ProductVendor AS pv   
      ON v.BusinessEntityID = pv.BusinessEntityID   
    JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID  
    WHERE v.Name LIKE @Name;  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a><span data-ttu-id="d2ec9-149">若要使用 WITH RECOMPILE 選項重新編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="d2ec9-149">To recompile a stored procedure by using the WITH RECOMPILE option</span></span>  
  
1.  <span data-ttu-id="d2ec9-150">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-150">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d2ec9-151">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d2ec9-152">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d2ec9-153">此範例所建立的簡單程序會從檢視表傳回所有員工 (所提供的姓氏和名字)、工作職稱及部門名稱。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-153">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="d2ec9-154">接著將第二個程式碼範例複製並貼到查詢視窗中，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-154">And then copy and paste the second code example into the query window and click **Execute**.</span></span> <span data-ttu-id="d2ec9-155">這樣就會執行程序，並重新編譯程序的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-155">This executes the procedure and recompiles the procedure's query plan.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE HumanResources.uspGetAllEmployees WITH RECOMPILE;  
GO  
  
```  
  
#### <a name="to-recompile-a-stored-procedure-by-using-sp_recompile"></a><span data-ttu-id="d2ec9-156">若要使用 sp_recompile 重新編譯預存程序</span><span class="sxs-lookup"><span data-stu-id="d2ec9-156">To recompile a stored procedure by using sp_recompile</span></span>  
  
1.  <span data-ttu-id="d2ec9-157">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-157">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d2ec9-158">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d2ec9-159">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-159">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d2ec9-160">此範例所建立的簡單程序會從檢視表傳回所有員工 (所提供的姓氏和名字)、工作職稱及部門名稱。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-160">This example creates a simple procedure that returns all employees (first and last names supplied), their job titles, and their department names from a view.</span></span>  
  
     <span data-ttu-id="d2ec9-161">接著將下列範例複製並貼到查詢視窗中，並按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-161">Then, copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d2ec9-162">這樣並不會執行程序，但會標示要重新編譯的程序，以便在下一次執行程序時更新其查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="d2ec9-162">This does not execute the procedure but it does mark the procedure to be recompiled so that its query plan is updated the next time that the procedure is executed.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'HumanResources.uspGetAllEmployees';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2ec9-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ec9-163">See Also</span></span>  
 <span data-ttu-id="d2ec9-164">[建立預存程序](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d2ec9-164">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="d2ec9-165">[修改預存程序](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d2ec9-165">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="d2ec9-166">[重新命名預存程序](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d2ec9-166">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="d2ec9-167">[檢視預存程序的定義](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d2ec9-167">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="d2ec9-168">[檢視預存程序的相依性](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d2ec9-168">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="d2ec9-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d2ec9-169">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
