---
title: 使用計畫指南指定查詢參數化行為 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f595b9f0e0a6d7bceffc5cb283c60b6f40e025b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606806"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a><span data-ttu-id="7bba5-102">使用計畫指南指定查詢參數化行為</span><span class="sxs-lookup"><span data-stu-id="7bba5-102">Specify Query Parameterization Behavior by Using Plan Guides</span></span>
  <span data-ttu-id="7bba5-103">當 PARAMETERIZATION 資料庫選項設定為 SIMPLE 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢最佳化工具可能會選擇將查詢參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-103">When the PARAMETERIZATION database option is set to SIMPLE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer may choose to parameterize the queries.</span></span> <span data-ttu-id="7bba5-104">這意謂著任何包含在查詢中的常值將會以參數替代。</span><span class="sxs-lookup"><span data-stu-id="7bba5-104">This means that any literal values that are contained in a query are substituted with parameters.</span></span> <span data-ttu-id="7bba5-105">此處理序稱為簡易參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-105">This process is referred to as simple parameterization.</span></span> <span data-ttu-id="7bba5-106">當 SIMPLE 參數化生效時，您無法控制哪些查詢要參數化以及哪些查詢不要參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-106">When SIMPLE parameterization is in effect, you cannot control which queries are parameterized and which queries are not.</span></span> <span data-ttu-id="7bba5-107">但是，您可以將 PARAMETERIZATION 資料庫選項設定為 FORCED，藉以指定要參數化資料庫中的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="7bba5-107">However, you can specify that all queries in a database be parameterized by setting the PARAMETERIZATION database option to FORCED.</span></span> <span data-ttu-id="7bba5-108">此處理序稱為強制參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-108">This process is referred to as forced parameterization.</span></span>  
  
 <span data-ttu-id="7bba5-109">您可以透過下列方式使用計畫指南來覆寫資料庫的參數化行為：</span><span class="sxs-lookup"><span data-stu-id="7bba5-109">You can override the parameterization behavior of a database by using plan guides in the following ways:</span></span>  
  
-   <span data-ttu-id="7bba5-110">當 PARAMETERIZATION 資料庫選項設定為 SIMPLE 時，您可以指定在特定的查詢類別強制參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-110">When the PARAMETERIZATION database option is set to SIMPLE, you can specify that forced parameterization is attempted on a certain class of queries.</span></span> <span data-ttu-id="7bba5-111">作法是在查詢的參數化表單上建立 TEMPLATE 計畫指南，並在 [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 預存程序中指定 PARAMETERIZATION FORCED 查詢提示。</span><span class="sxs-lookup"><span data-stu-id="7bba5-111">You do this by creating a TEMPLATE plan guide on the parameterized form of the query, and specifying the PARAMETERIZATION FORCED query hint in the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure.</span></span> <span data-ttu-id="7bba5-112">您可以考慮將此類的計畫指南做為只在某類別的查詢 (而不是所有的查詢) 中啟用強制參數化的方式。</span><span class="sxs-lookup"><span data-stu-id="7bba5-112">You can consider this kind of plan guide as a way to enable forced parameterization only on a certain class of queries, instead of all queries.</span></span>  
  
-   <span data-ttu-id="7bba5-113">當 PARAMETERIZATION 資料庫選項設定為 FORCED 時，您可以指定在特定的查詢類別只嘗試簡單參數化，但不嘗試強制參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-113">When the PARAMETERIZATION database option is set to FORCED, you can specify that for a certain class of queries, only simple parameterization is attempted, not forced parameterization.</span></span> <span data-ttu-id="7bba5-114">作法是在查詢的強制參數化表單上建立 TEMPLATE 計畫指南，並在 **sp_create_plan_guide**中指定 PARAMETERIZATION SIMPLE 查詢提示。</span><span class="sxs-lookup"><span data-stu-id="7bba5-114">You do this by creating a TEMPLATE plan guide on the force-parameterized form of the query, and specifying the PARAMETERIZATION SIMPLE query hint in **sp_create_plan_guide**.</span></span>  
  
 <span data-ttu-id="7bba5-115">請考慮在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的下列查詢：</span><span class="sxs-lookup"><span data-stu-id="7bba5-115">Consider the following query on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 <span data-ttu-id="7bba5-116">身為資料庫管理員，您已決定不要啟用資料庫中所有查詢的強制參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-116">As a database administrator, you have determined that you do not want to enable forced parameterization on all queries in the database.</span></span> <span data-ttu-id="7bba5-117">不過，您想要對在語法上與上一個查詢相等，但僅其常值不同的所有查詢，省下其編譯成本。</span><span class="sxs-lookup"><span data-stu-id="7bba5-117">However, you do want to avoid compilation costs on all queries that are syntactically equivalent to the previous query, but differ only in their constant literal values.</span></span> <span data-ttu-id="7bba5-118">換句話說，您想要參數化查詢，這樣才能拒絕這類的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="7bba5-118">In other words, you want the query to be parameterized so that a query plan for this kind of query is reused.</span></span> <span data-ttu-id="7bba5-119">在此情況下，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7bba5-119">In this case, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="7bba5-120">擷取查詢的參數化格式。</span><span class="sxs-lookup"><span data-stu-id="7bba5-120">Retrieve the parameterized form of the query.</span></span> <span data-ttu-id="7bba5-121">取得這個值供 **sp_create_plan_guide** 使用的唯一安全方法，是使用 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="7bba5-121">The only safe way to obtain this value for use in **sp_create_plan_guide** is by using the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span>  
  
2.  <span data-ttu-id="7bba5-122">在查詢的參數化格式上建立計畫指南，以指定 PARAMETERIZATION FORCED 查詢提示。</span><span class="sxs-lookup"><span data-stu-id="7bba5-122">Create the plan guide on the parameterized form of the query, specifying the PARAMETERIZATION FORCED query hint.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7bba5-123">在參數化查詢時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會指派資料類型給取代常值的參數，端視常值的值與大小而定。</span><span class="sxs-lookup"><span data-stu-id="7bba5-123">As part of parameterizing a query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns a data type to the parameters that replace the literal values, depending on the value and size of the literal.</span></span> <span data-ttu-id="7bba5-124">相同的程式會發生在傳遞至 sp_get_query_template 之輸出參數的常數常值 **@stmt** 。 **sp_get_query_template**</span><span class="sxs-lookup"><span data-stu-id="7bba5-124">The same process occurs to the value of the constant literals passed to the **@stmt** output parameter of **sp_get_query_template**.</span></span> <span data-ttu-id="7bba5-125">因為在 sp_create_plan_guide 的引數中指定的資料類型 **@params** 必須符合參數化時的查詢，所以**sp_create_plan_guide** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您可能必須建立一個以上的計劃指南，以涵蓋查詢的可能參數值的完整範圍。</span><span class="sxs-lookup"><span data-stu-id="7bba5-125">Because the data type specified in the **@params** argument of **sp_create_plan_guide** must match that of the query as it is parameterized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you may have to create more than one plan guide to cover the complete range of possible parameter values for the query.</span></span>  
  
 <span data-ttu-id="7bba5-126">下列指令碼可用以擷取參數化查詢，並在該查詢上建立計畫指南：</span><span class="sxs-lookup"><span data-stu-id="7bba5-126">The following script can be used both to obtain the parameterized query and then create a plan guide on it:</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="7bba5-127">相同的，在已經啟用強制參數化的資料庫中，您可以確定讓範例查詢以及其他句法相同的項目 (常數常值除外)，都根據簡單參數化規則加以參數化。</span><span class="sxs-lookup"><span data-stu-id="7bba5-127">Similarly, in a database in which forced parameterization is already enabled, you can make sure that the sample query, and others that are syntactically equivalent, except for their constant literal values, are parameterized according to the rules of simple parameterization.</span></span> <span data-ttu-id="7bba5-128">作法是指定 OPTION 子句中的 PARAMETERIZATION SIMPLE，而不是 PARAMETERIZATION FORCED。</span><span class="sxs-lookup"><span data-stu-id="7bba5-128">To do this, specify PARAMETERIZATION SIMPLE instead of PARAMETERIZATION FORCED in the OPTION clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bba5-129">TEMPLATE 計畫指南可使陳述式配合僅由單一陳述式組成的批次中所提交的查詢。</span><span class="sxs-lookup"><span data-stu-id="7bba5-129">TEMPLATE plan guides match statements to queries submitted in batches that consist of a single statement only.</span></span> <span data-ttu-id="7bba5-130">TEMPLATE 計畫指南無法配合多重陳述式批次中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bba5-130">Statements inside multistatement batches are not eligible to be matched by TEMPLATE plan guides.</span></span>  
  
  
