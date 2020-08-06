---
title: 將固定的查詢計畫套用至計畫指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687789"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a><span data-ttu-id="04114-102">將固定的查詢計畫套用至計畫指南</span><span class="sxs-lookup"><span data-stu-id="04114-102">Apply a Fixed Query Plan to a Plan Guide</span></span>
  <span data-ttu-id="04114-103">您可以將固定的查詢計畫套用至 OBJECT 或 SQL 類型的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="04114-103">You can apply a fixed query plan to a plan guide of type OBJECT or SQL.</span></span> <span data-ttu-id="04114-104">當您知道現有執行計畫的效能比最佳化工具針對特定查詢所選取的計畫更好時，套用固定查詢計畫的計畫指南就很有用。</span><span class="sxs-lookup"><span data-stu-id="04114-104">Plan guides that apply a fixed query plan are useful when you know about an existing execution plan that performs better than the one selected by the optimizer for a particular query.</span></span>  
  
 <span data-ttu-id="04114-105">下列範例會針對簡單的特定 SQL 陳述式建立計畫指南。</span><span class="sxs-lookup"><span data-stu-id="04114-105">The following example creates a plan guide for a simple ad hoc SQL statement.</span></span> <span data-ttu-id="04114-106">直接以 `@hints` 參數指定查詢的 XML 執行程序表，就可以在計畫指南中提供此陳述式所需的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="04114-106">The desired query plan for this statement is provided in the plan guide by specifying the XML Showplan for the query directly in the `@hints` parameter.</span></span> <span data-ttu-id="04114-107">此範例會先執行 SQL 陳述式以便在計畫快取中產生計畫。</span><span class="sxs-lookup"><span data-stu-id="04114-107">The example first executes the SQL statement to generate a plan in the plan cache.</span></span> <span data-ttu-id="04114-108">基於此範例的目的，假設產生的計畫為所需的計畫，而且不需要額外調整查詢。</span><span class="sxs-lookup"><span data-stu-id="04114-108">For the purposes of this example, it is assumed that the generated plan is the desired plan and no additional query tuning is required.</span></span> <span data-ttu-id="04114-109">查詢的 XML 執行程序表會透過查詢 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`和 `sys.dm_exec_text_query_plan` 動態管理檢視取得，而且會被指派給 `@xml_showplan` 變數。</span><span class="sxs-lookup"><span data-stu-id="04114-109">The XML Showplan for the query is obtained by querying the `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`, and `sys.dm_exec_text_query_plan` dynamic management views and is assigned to the `@xml_showplan` variable.</span></span> <span data-ttu-id="04114-110">然後，系統會將 `@xml_showplan` 變數傳遞到 `sp_create_plan_guide` 參數的 `@hints` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="04114-110">The `@xml_showplan` variable is then passed to the `sp_create_plan_guide` statement in the `@hints` parameter.</span></span> <span data-ttu-id="04114-111">或者，您可以使用 [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) 預存程序，從計畫快取的查詢計劃中建立計劃指南。</span><span class="sxs-lookup"><span data-stu-id="04114-111">Or, you can create a plan guide from a query plan in the plan cache by using the [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
