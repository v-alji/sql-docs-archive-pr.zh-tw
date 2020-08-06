---
title: 建立參數化查詢的計畫指南 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 565610826f704274724ea05d821205a5b3391060
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606814"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a><span data-ttu-id="2745a-102">建立參數化查詢的計畫指南</span><span class="sxs-lookup"><span data-stu-id="2745a-102">Create a Plan Guide for Parameterized Queries</span></span>
  <span data-ttu-id="2745a-103">TEMPLATE 計畫指南可搭配參數化為指定形式的獨立查詢。</span><span class="sxs-lookup"><span data-stu-id="2745a-103">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span>  
  
 <span data-ttu-id="2745a-104">下列範例會建立與參數化為特定格式的任何查詢相符的計畫指南，並導引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以強制執行查詢的參數化作業。</span><span class="sxs-lookup"><span data-stu-id="2745a-104">The following example creates a plan guide that matches any query that parameterizes to a specified form, and directs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to force parameterization of the query.</span></span> <span data-ttu-id="2745a-105">下列兩項查詢在語法上相同，不同的只是兩者的常數值。</span><span class="sxs-lookup"><span data-stu-id="2745a-105">The following two queries are syntactically equivalent, but differ only in their constant literal values.</span></span>  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 <span data-ttu-id="2745a-106">以下是參數化格式查詢的計畫指南：</span><span class="sxs-lookup"><span data-stu-id="2745a-106">Here is the plan guide on the parameterized form of the query:</span></span>  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="2745a-107">在前一個範例中， `@stmt` 參數的值是參數化格式的查詢。</span><span class="sxs-lookup"><span data-stu-id="2745a-107">In the previous example, the value for the `@stmt` parameter is the parameterized form of the query.</span></span> <span data-ttu-id="2745a-108">取得這個值以便於 sp_create_plan_guide 中使用的唯一可靠方法，是利用 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="2745a-108">The only reliable way to obtain this value for use in sp_create_plan_guide is to use the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span> <span data-ttu-id="2745a-109">下列指令碼可以用來取得參數化查詢，之後再建立參數化查詢的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="2745a-109">The following script can be used both to obtain the parameterized query and then create a plan guide on it.</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2745a-110">傳送到 `@stmt` 之 `sp_get_query_template` 參數中的常數常值，可能會影響針對取代常值的參數所選擇的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2745a-110">The value of the constant literals in the `@stmt` parameter passed to `sp_get_query_template` might affect the data type that is chosen for the parameter that replaces the literal.</span></span> <span data-ttu-id="2745a-111">這會影響計畫指南的比對作業。</span><span class="sxs-lookup"><span data-stu-id="2745a-111">This will affect plan guide matching.</span></span> <span data-ttu-id="2745a-112">您可能需要建立一份以上的計畫指南，來處理不同的參數值範圍。</span><span class="sxs-lookup"><span data-stu-id="2745a-112">You may have to create more than one plan guide to handle different parameter value ranges.</span></span>  
  
 <span data-ttu-id="2745a-113">您也可以同時使用 TEMPLATE 計畫指南與 SQL 計畫指南。</span><span class="sxs-lookup"><span data-stu-id="2745a-113">You can also use TEMPLATE plan guides together with SQL plan guides.</span></span> <span data-ttu-id="2745a-114">例如，您可以建立 TEMPLATE 計畫指南以確定參數化查詢類別。</span><span class="sxs-lookup"><span data-stu-id="2745a-114">For example, you can create a TEMPLATE plan guide to make sure that a class of queries is parameterized.</span></span> <span data-ttu-id="2745a-115">接著就可以在該查詢的參數化形式上建立 SQL 計畫指南。</span><span class="sxs-lookup"><span data-stu-id="2745a-115">You can then create an SQL plan guide on the parameterized form of that query.</span></span>  
  
  
