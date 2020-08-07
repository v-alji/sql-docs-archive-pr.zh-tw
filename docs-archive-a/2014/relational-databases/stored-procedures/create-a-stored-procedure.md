---
title: 建立預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6781840e6a6c84773f40a6cd0557ccb79b676eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599401"
---
# <a name="create-a-stored-procedure"></a><span data-ttu-id="fadc8-102">建立預存程序</span><span class="sxs-lookup"><span data-stu-id="fadc8-102">Create a Stored Procedure</span></span>
  <span data-ttu-id="fadc8-103">此主題描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 及 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE PROCEDURE 陳述式來建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。</span><span class="sxs-lookup"><span data-stu-id="fadc8-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE statement.</span></span>  
  
##  <a name="Top"></a>   
-   <span data-ttu-id="fadc8-104">**開始之前：** [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="fadc8-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="fadc8-105">**使用以下方式建立程序：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="fadc8-105">**To create a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fadc8-106">權限</span><span class="sxs-lookup"><span data-stu-id="fadc8-106">Permissions</span></span>  
 <span data-ttu-id="fadc8-107">需要在資料庫中的 CREATE PROCEDURE 權限，以及在建立程序時所在的結構描述上的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="fadc8-107">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
##  <a name="how-to-create-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="fadc8-108">如何建立預存程序</span><span class="sxs-lookup"><span data-stu-id="fadc8-108">How to Create a Stored Procedure</span></span>  
 <span data-ttu-id="fadc8-109">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fadc8-109">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="fadc8-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fadc8-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="fadc8-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fadc8-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fadc8-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fadc8-112">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="fadc8-113">**在 [物件總管] 中建立程序**</span><span class="sxs-lookup"><span data-stu-id="fadc8-113">**To create a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="fadc8-114">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="fadc8-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="fadc8-115">依序展開 **[資料庫]** 、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫，以及 **[Programmability]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="fadc8-116">以滑鼠右鍵按一下 [預存程序]，然後按一下 [新增預存程序]。</span><span class="sxs-lookup"><span data-stu-id="fadc8-116">Right-click **Stored Procedures**, and then click **New Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="fadc8-117">在 **[查詢]** 功能表上，按一下 **[指定範本參數的值]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="fadc8-118">在 **[指定範本參數的值]** 對話方塊中，為顯示的參數輸入下列值。</span><span class="sxs-lookup"><span data-stu-id="fadc8-118">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="fadc8-119">參數</span><span class="sxs-lookup"><span data-stu-id="fadc8-119">Parameter</span></span>|<span data-ttu-id="fadc8-120">值</span><span class="sxs-lookup"><span data-stu-id="fadc8-120">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="fadc8-121">作者</span><span class="sxs-lookup"><span data-stu-id="fadc8-121">Author</span></span>|<span data-ttu-id="fadc8-122">*您的名字*</span><span class="sxs-lookup"><span data-stu-id="fadc8-122">*Your name*</span></span>|  
    |<span data-ttu-id="fadc8-123">建立日期</span><span class="sxs-lookup"><span data-stu-id="fadc8-123">Create Date</span></span>|<span data-ttu-id="fadc8-124">*今天的日期*</span><span class="sxs-lookup"><span data-stu-id="fadc8-124">*Today's date*</span></span>|  
    |<span data-ttu-id="fadc8-125">描述</span><span class="sxs-lookup"><span data-stu-id="fadc8-125">Description</span></span>|<span data-ttu-id="fadc8-126">傳回員工資料。</span><span class="sxs-lookup"><span data-stu-id="fadc8-126">Returns employee data.</span></span>|  
    |<span data-ttu-id="fadc8-127">Procedure_name</span><span class="sxs-lookup"><span data-stu-id="fadc8-127">Procedure_name</span></span>|<span data-ttu-id="fadc8-128">HumanResources.uspGetEmployeesTest</span><span class="sxs-lookup"><span data-stu-id="fadc8-128">HumanResources.uspGetEmployeesTest</span></span>|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|<span data-ttu-id="fadc8-129">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="fadc8-129">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="fadc8-130">Default_Value_For_Param1</span><span class="sxs-lookup"><span data-stu-id="fadc8-130">Default_Value_For_Param1</span></span>|<span data-ttu-id="fadc8-131">NULL</span><span class="sxs-lookup"><span data-stu-id="fadc8-131">NULL</span></span>|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|<span data-ttu-id="fadc8-132">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="fadc8-132">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="fadc8-133">Default_Value_For_Param2</span><span class="sxs-lookup"><span data-stu-id="fadc8-133">Default_Value_For_Param2</span></span>|<span data-ttu-id="fadc8-134">NULL</span><span class="sxs-lookup"><span data-stu-id="fadc8-134">NULL</span></span>|  
  
6.  <span data-ttu-id="fadc8-135">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fadc8-135">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="fadc8-136">在 **[查詢編輯器]** 中，以下列陳述式取代 SELECT 陳述式：</span><span class="sxs-lookup"><span data-stu-id="fadc8-136">In the **Query Editor**, replace the SELECT statement with the following statement:</span></span>  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  <span data-ttu-id="fadc8-137">若要測試語法，請在 **[查詢]** 功能表上按一下 **[剖析]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-137">To test the syntax, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="fadc8-138">如果傳回錯誤訊息，請比較陳述式與上列資訊，並視需要進行更正。</span><span class="sxs-lookup"><span data-stu-id="fadc8-138">If an error message is returned, compare the statements with the information above and correct as needed.</span></span>  
  
9. <span data-ttu-id="fadc8-139">若要建立程序，請在 **[查詢]** 功能表中，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-139">To create the procedure, from  the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="fadc8-140">程序也可建立為資料庫中的物件。</span><span class="sxs-lookup"><span data-stu-id="fadc8-140">The procedure is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="fadc8-141">若要查看物件總管中所列的程序，請以滑鼠右鍵按一下 [預存程序]，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="fadc8-141">To see the procedure listed in Object Explorer, right-click **Stored Procedures** and select **Refresh**.</span></span>  
  
11. <span data-ttu-id="fadc8-142">若要執行程序，請在物件總管中，以滑鼠右鍵按一下預存程序名稱 **HumanResources.uspGetEmployeesTest**，然後選取 [執行預存程序]。</span><span class="sxs-lookup"><span data-stu-id="fadc8-142">To run the procedure, in Object Explorer, right-click the stored procedure name **HumanResources.uspGetEmployeesTest** and select **Execute Stored Procedure**.</span></span>  
  
12. <span data-ttu-id="fadc8-143">在 [執行程序] 視窗中，輸入 Margheim 以作為 @LastName 參數值，然後輸入 Diane 值以作為 @FirstName 參數值。</span><span class="sxs-lookup"><span data-stu-id="fadc8-143">In the **Execute Procedure** window, enter Margheim as the value for the parameter @LastName and enter the value Diane as the value for the parameter @FirstName.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fadc8-144">驗證所有使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="fadc8-144">Validate all user input.</span></span> <span data-ttu-id="fadc8-145">在使用者輸入完成驗證前，請勿加以串連。</span><span class="sxs-lookup"><span data-stu-id="fadc8-145">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="fadc8-146">請勿執行由未經驗證之使用者輸入所建構的命令。</span><span class="sxs-lookup"><span data-stu-id="fadc8-146">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fadc8-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fadc8-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="fadc8-148">**若要在查詢編輯器中建立程序**</span><span class="sxs-lookup"><span data-stu-id="fadc8-148">**To create a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="fadc8-149">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fadc8-149">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fadc8-150">在 **[檔案]** 功能表中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-150">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fadc8-151">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="fadc8-152">此範例會使用不同的程序名稱建立與上述相同的預存程序。</span><span class="sxs-lookup"><span data-stu-id="fadc8-152">This example creates the same stored procedure as above using a different procedure name.</span></span>  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  <span data-ttu-id="fadc8-153">若要執行程序，請將下列範例複製並貼到新的查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fadc8-153">To run the procedure, copy and paste the following example into a new query window and click **Execute**.</span></span> <span data-ttu-id="fadc8-154">請注意，此處顯示指定參數值的不同方法。</span><span class="sxs-lookup"><span data-stu-id="fadc8-154">Notice that different methods of specifying the parameter values are shown.</span></span>  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fadc8-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fadc8-155">See Also</span></span>  
 [<span data-ttu-id="fadc8-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fadc8-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  