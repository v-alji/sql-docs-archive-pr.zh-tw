---
title: 執行使用者定義函式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4446f3b3a132488fdac6e859f30abaca40a193d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607324"
---
# <a name="execute-user-defined-functions"></a><span data-ttu-id="0bd1a-102">執行使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="0bd1a-102">Execute User-defined Functions</span></span>
  <span data-ttu-id="0bd1a-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中執行使用者定義的函數。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-103">You can execute a user defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0bd1a-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0bd1a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0bd1a-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0bd1a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0bd1a-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="0bd1a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0bd1a-107">安全性</span><span class="sxs-lookup"><span data-stu-id="0bd1a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0bd1a-108">**若要執行使用者定義函數，使用：**</span><span class="sxs-lookup"><span data-stu-id="0bd1a-108">**To execute a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="0bd1a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0bd1a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0bd1a-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="0bd1a-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0bd1a-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="0bd1a-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0bd1a-112">在 Transact-SQL 中，您可以使用 *value* 或 @*parameter_name*=*value*來提供參數。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-112">In Transact-SQL, parameters can be supplied either by using *value* or by using @*parameter_name*=*value.*</span></span> <span data-ttu-id="0bd1a-113">來提供參數。參數不是交易的一部分；因此，如果交易中的參數變更之後再回復，參數值並不會還原為之前的值。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-113">A parameter is not part of a transaction; therefore, if a parameter is changed in a transaction that is later rolled back, the value of the parameter does not revert to its previous value.</span></span> <span data-ttu-id="0bd1a-114">傳回呼叫端的值一定是模組傳回時的值。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-114">The value returned to the caller is always the value at the time the module returns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0bd1a-115">Security</span><span class="sxs-lookup"><span data-stu-id="0bd1a-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0bd1a-116">權限</span><span class="sxs-lookup"><span data-stu-id="0bd1a-116">Permissions</span></span>  
 <span data-ttu-id="0bd1a-117">執行 EXECUTE 陳述式不需要任何權限。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-117">Permissions are not required to run the EXECUTE statement.</span></span> <span data-ttu-id="0bd1a-118">不過，您必須對 EXECUTE 字串內所參考的安全性實體具備權限。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-118">However, permissions are required on the securables that are referenced within the EXECUTE string.</span></span> <span data-ttu-id="0bd1a-119">例如，如果字串包含 INSERT 陳述式，EXECUTE 陳述式的呼叫端就必須有目標資料表的 INSERT 權限。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-119">For example, if the string contains an INSERT statement, the caller of the EXECUTE statement must have INSERT permission on the target table.</span></span> <span data-ttu-id="0bd1a-120">遇到 EXECUTE 陳述式時會檢查權限，即使模組內包含 EXECUTE 陳述式也一樣。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-120">Permissions are checked at the time EXECUTE statement is encountered, even if the EXECUTE statement is included within a module.</span></span> <span data-ttu-id="0bd1a-121">如需詳細資訊，請參閱[EXECUTE &#40;transact-sql&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="0bd1a-121">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0bd1a-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0bd1a-122">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-user-defined-function"></a><span data-ttu-id="0bd1a-123">若要執行使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="0bd1a-123">To execute a user-defined function</span></span>  
  
1.  <span data-ttu-id="0bd1a-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0bd1a-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0bd1a-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 <span data-ttu-id="0bd1a-127">如需詳細資訊，請參閱 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0bd1a-127">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
  
