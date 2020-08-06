---
title: 檢視使用者定義函數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.udfproperties.general.f1
- sql12.swb.functionproperties.general.f1
helpviewer_keywords:
- displaying user-defined functions
- viewing user-defined functions
- user-defined functions [SQL Server], viewing
- status information [SQL Server], user-defined functions
ms.assetid: a45dfab5-6384-4311-b935-2e23a70c5c10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5248f75540b72b489a7605b2cca34144dfcfedbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584335"
---
# <a name="view-user-defined-functions"></a><span data-ttu-id="79c2f-102">檢視使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="79c2f-102">View User-defined Functions</span></span>
  <span data-ttu-id="79c2f-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，取得 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使用者定義函數之定義或屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79c2f-103">You can gain information about the definition or properties of a user-defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="79c2f-104">您可能需要查看函數的定義才能了解如何從來源資料表衍生出資料；或是查看函數所定義的資料。</span><span class="sxs-lookup"><span data-stu-id="79c2f-104">You may need to see the definition of the function to understand how its data is derived from the source tables or to see the data defined by the function.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79c2f-105">如果變更函數所參考的物件名稱，就必須修改該函數，使其文字反映新的名稱。</span><span class="sxs-lookup"><span data-stu-id="79c2f-105">If you change the name of an object referenced by a function, you must modify that function so that its text reflects the new name.</span></span> <span data-ttu-id="79c2f-106">因此，在改變物件名稱時，首先要檢視此物件的相依性以了解是否有相關的函數受到影響。</span><span class="sxs-lookup"><span data-stu-id="79c2f-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any functions are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="79c2f-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="79c2f-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="79c2f-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="79c2f-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="79c2f-109">安全性</span><span class="sxs-lookup"><span data-stu-id="79c2f-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="79c2f-110">**使用下列方法取得函數的相關資訊：**</span><span class="sxs-lookup"><span data-stu-id="79c2f-110">**To get information about a function, using:**</span></span>  
  
     [<span data-ttu-id="79c2f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79c2f-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="79c2f-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79c2f-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="79c2f-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="79c2f-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="79c2f-114">Security</span><span class="sxs-lookup"><span data-stu-id="79c2f-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="79c2f-115">權限</span><span class="sxs-lookup"><span data-stu-id="79c2f-115">Permissions</span></span>  
 <span data-ttu-id="79c2f-116">若要使用 **sys.sql_expression_dependencies** 尋找函數的所有相依性，需要資料庫的 VIEW DEFINITION 權限以及資料庫之 **sys.sql_expression_dependencies** 的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="79c2f-116">Using **sys.sql_expression_dependencies** to find all the dependencies on a function requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="79c2f-117">系統物件定義是公開可見的，就像 OBJECT_DEFINITION 中傳回的定義一樣。</span><span class="sxs-lookup"><span data-stu-id="79c2f-117">System object definitions, like the ones returned in OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="79c2f-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="79c2f-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-show-a-user-defined-functions-properties"></a><span data-ttu-id="79c2f-119">顯示使用者定義函數的屬性</span><span class="sxs-lookup"><span data-stu-id="79c2f-119">To show a user-defined function's properties</span></span>  
  
1.  <span data-ttu-id="79c2f-120">在 **[物件總管]** 中，按一下資料庫旁邊的加號，此資料庫包含您要查看其屬性的函數，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="79c2f-120">In **Object Explorer**, click the plus sign next to the database that contains the function to which you want to view the properties, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="79c2f-121">按一下加號展開 **[函數]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="79c2f-121">Click the plus sign to expand the **Functions** folder.</span></span>  
  
3.  <span data-ttu-id="79c2f-122">按一下加號展開包含您要檢視其屬性之函數的資料夾：</span><span class="sxs-lookup"><span data-stu-id="79c2f-122">Click the plus sign to expand the folder that contains the function to which you want to view the properties:</span></span>  
  
    -   <span data-ttu-id="79c2f-123">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="79c2f-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="79c2f-124">純量值函式</span><span class="sxs-lookup"><span data-stu-id="79c2f-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="79c2f-125">彙總函式</span><span class="sxs-lookup"><span data-stu-id="79c2f-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="79c2f-126">以滑鼠右鍵按一下要查看其屬性的函數，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="79c2f-126">Right-click the function of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="79c2f-127">下列屬性會出現在 [函式屬性 - **function_name**]  對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="79c2f-127">The following properties appear in the **Function Properties -** _function_name_ dialog box.</span></span>  
  
     <span data-ttu-id="79c2f-128">**Database**</span><span class="sxs-lookup"><span data-stu-id="79c2f-128">**Database**</span></span>  
     <span data-ttu-id="79c2f-129">包含此函數之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="79c2f-129">The name of the database containing this function.</span></span>  
  
     <span data-ttu-id="79c2f-130">**Server**</span><span class="sxs-lookup"><span data-stu-id="79c2f-130">**Server**</span></span>  
     <span data-ttu-id="79c2f-131">目前伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="79c2f-131">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="79c2f-132">**使用者**</span><span class="sxs-lookup"><span data-stu-id="79c2f-132">**User**</span></span>  
     <span data-ttu-id="79c2f-133">這個連接之使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="79c2f-133">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="79c2f-134">**建立日期**</span><span class="sxs-lookup"><span data-stu-id="79c2f-134">**Created date**</span></span>  
     <span data-ttu-id="79c2f-135">顯示建立函數的日期。</span><span class="sxs-lookup"><span data-stu-id="79c2f-135">Displays the date the function was created.</span></span>  
  
     <span data-ttu-id="79c2f-136">**執行身分**</span><span class="sxs-lookup"><span data-stu-id="79c2f-136">**Execute As**</span></span>  
     <span data-ttu-id="79c2f-137">函數的執行內容。</span><span class="sxs-lookup"><span data-stu-id="79c2f-137">Execution context for the function.</span></span>  
  
     <span data-ttu-id="79c2f-138">**名稱**</span><span class="sxs-lookup"><span data-stu-id="79c2f-138">**Name**</span></span>  
     <span data-ttu-id="79c2f-139">目前函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="79c2f-139">The name of the current function.</span></span>  
  
     <span data-ttu-id="79c2f-140">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="79c2f-140">**Schema**</span></span>  
     <span data-ttu-id="79c2f-141">顯示擁有函數的結構描述。</span><span class="sxs-lookup"><span data-stu-id="79c2f-141">Displays the schema that owns the function.</span></span>  
  
     <span data-ttu-id="79c2f-142">**系統物件**</span><span class="sxs-lookup"><span data-stu-id="79c2f-142">**System object**</span></span>  
     <span data-ttu-id="79c2f-143">指出函數是否為系統物件。</span><span class="sxs-lookup"><span data-stu-id="79c2f-143">Indicates whether the function is a system object.</span></span> <span data-ttu-id="79c2f-144">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="79c2f-144">Values are True and False.</span></span>  
  
     <span data-ttu-id="79c2f-145">**ANSI NULLS**</span><span class="sxs-lookup"><span data-stu-id="79c2f-145">**ANSI NULLs**</span></span>  
     <span data-ttu-id="79c2f-146">指出物件是否使用 ANSI NULLS 選項建立。</span><span class="sxs-lookup"><span data-stu-id="79c2f-146">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="79c2f-147">**已加密**</span><span class="sxs-lookup"><span data-stu-id="79c2f-147">**Encrypted**</span></span>  
     <span data-ttu-id="79c2f-148">指出函數是否加密。</span><span class="sxs-lookup"><span data-stu-id="79c2f-148">Indicates whether the function is encrypted.</span></span> <span data-ttu-id="79c2f-149">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="79c2f-149">Values are True and False.</span></span>  
  
     <span data-ttu-id="79c2f-150">**函數類型**</span><span class="sxs-lookup"><span data-stu-id="79c2f-150">**Function Type**</span></span>  
     <span data-ttu-id="79c2f-151">使用者定義函數的類型。</span><span class="sxs-lookup"><span data-stu-id="79c2f-151">The type of user defined function.</span></span>  
  
     <span data-ttu-id="79c2f-152">**引號識別碼**</span><span class="sxs-lookup"><span data-stu-id="79c2f-152">**Quoted identifier**</span></span>  
     <span data-ttu-id="79c2f-153">指出物件是否使用引號識別碼選項建立。</span><span class="sxs-lookup"><span data-stu-id="79c2f-153">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="79c2f-154">**結構描述繫結**</span><span class="sxs-lookup"><span data-stu-id="79c2f-154">**Schema bound**</span></span>  
     <span data-ttu-id="79c2f-155">指出函數是否為結構描述繫結函數。</span><span class="sxs-lookup"><span data-stu-id="79c2f-155">Indicates whether the function is schema-bound.</span></span> <span data-ttu-id="79c2f-156">值為 True 與 False。</span><span class="sxs-lookup"><span data-stu-id="79c2f-156">Values are True and False.</span></span> <span data-ttu-id="79c2f-157">如需結構描述繫結函數的資訊，請參閱 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) 的＜SCHEMABINDING＞一節。</span><span class="sxs-lookup"><span data-stu-id="79c2f-157">For information about schema-bound functions, see the SCHEMABINDING section of [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="79c2f-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79c2f-158">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-function"></a><span data-ttu-id="79c2f-159">若要取得函數定義和屬性</span><span class="sxs-lookup"><span data-stu-id="79c2f-159">To get the definition and properties of a function</span></span>  
  
1.  <span data-ttu-id="79c2f-160">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="79c2f-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="79c2f-161">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="79c2f-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="79c2f-162">將下列其中一個範例複製並貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="79c2f-162">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the function name, definition, and relevant properties  
    SELECT sm.object_id,   
       OBJECT_NAME(sm.object_id) AS object_name,   
       o.type,   
       o.type_desc,   
       sm.definition,  
       sm.uses_ansi_nulls,  
       sm.uses_quoted_identifier,  
       sm.is_schema_bound,  
       sm.execute_as_principal_id  
    -- using the two system tables sys.sql_modules and sys.objects  
    FROM sys.sql_modules AS sm  
    JOIN sys.objects AS o ON sm.object_id = o.object_id  
    -- from the function 'dbo.ufnGetProductDealerPrice'  
    WHERE sm.object_id = OBJECT_ID('dbo.ufnGetProductDealerPrice')  
    ORDER BY o.type;  
    GO  
  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get the definition of the function dbo.ufnGetProductDealerPrice  
    SELECT OBJECT_DEFINITION (OBJECT_ID('dbo.ufnGetProductDealerPrice')) AS ObjectDefinition;  
    GO  
    ```  
  
 <span data-ttu-id="79c2f-163">如需詳細資訊，請參閱 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 和 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79c2f-163">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) and [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-function"></a><span data-ttu-id="79c2f-164">若要取得函數的相依性</span><span class="sxs-lookup"><span data-stu-id="79c2f-164">To get the dependencies of a function</span></span>  
  
1.  <span data-ttu-id="79c2f-165">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="79c2f-165">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="79c2f-166">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="79c2f-166">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="79c2f-167">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="79c2f-167">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Get all of the dependency information  
    SELECT OBJECT_NAME(sed.referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(sed.referencing_id, sed.referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        sed.referencing_class_desc, sed.referenced_class_desc,  
        sed.referenced_server_name, sed.referenced_database_name, sed.referenced_schema_name,  
        sed.referenced_entity_name,   
        COALESCE(COL_NAME(sed.referenced_id, sed.referenced_minor_id), '(n/a)') AS referenced_column_name,  
        sed.is_caller_dependent, sed.is_ambiguous  
    -- from the two system tables sys.sql_expression_dependencies and sys.object  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    -- on the function dbo.ufnGetProductDealerPrice  
    WHERE sed.referencing_id = OBJECT_ID('dbo.ufnGetProductDealerPrice');  
    GO  
    ```  
  
 <span data-ttu-id="79c2f-168">如需詳細資訊，請參閱 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 和 [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79c2f-168">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
