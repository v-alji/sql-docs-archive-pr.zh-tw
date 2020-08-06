---
title: 建立 DML 觸發程序以處理多重資料列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple row DML triggers
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- multirow DML triggers [SQL Server]
- INSERT statement [SQL Server], DML triggers
- DML triggers, multirow
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
author: rothja
ms.author: jroth
ms.openlocfilehash: 11ea7aa457a5cdfcafd4a8c4e0ac170ae0e3b9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606144"
---
# <a name="create-dml-triggers-to-handle-multiple-rows-of-data"></a><span data-ttu-id="f1fd8-102">建立 DML 觸發程序以處理多重資料列</span><span class="sxs-lookup"><span data-stu-id="f1fd8-102">Create DML Triggers to Handle Multiple Rows of Data</span></span>
  <span data-ttu-id="f1fd8-103">撰寫 DML 觸發程序的程式碼時，請將造成觸發程序引發的陳述式，視為可影響多個資料列而非只影響單一資料列的單一陳述式。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-103">When you write the code for a DML trigger, consider that the statement that causes the trigger to fire can be a single statement that affects multiple rows of data, instead of a single row.</span></span> <span data-ttu-id="f1fd8-104">此行為對 UPDATE 與 DELETE 觸發程序是常見的，因為這些陳述式經常會影響多個資料列。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-104">This behavior is common for UPDATE and DELETE triggers because these statements frequently affect multiple rows.</span></span> <span data-ttu-id="f1fd8-105">然而該行為對 INSERT 觸發程序較不常見，因為基本 INSERT 陳述式僅會加入單一資料列。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-105">The behavior is less common for INSERT triggers because the basic INSERT statement adds only a single row.</span></span> <span data-ttu-id="f1fd8-106">不過，由於 INSERT 觸發程序可以由 INSERT INTO (*table_name*) SELECT 陳述式引發，所以插入多個資料列也許會造成單一觸發程序引動過程。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-106">However, because an INSERT trigger can be fired by an INSERT INTO (*table_name*) SELECT statement, the insertion of many rows may cause a single trigger invocation.</span></span>  
  
 <span data-ttu-id="f1fd8-107">當 DML 觸發程序執行自動重新計算來自資料表的摘要值，並將計算結果存至另一資料表的功能時，考慮多重資料列所造成的影響就顯得特別地重要。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-107">Multirow considerations are especially important when the function of a DML trigger is to automatically recalculate summary values from one table and store the results in another for ongoing tallies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1fd8-108">我們不建議在觸發程序中使用資料指標，因為這樣可能會減低效能。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-108">We do not recommend using cursors in triggers because they could potentially reduce performance.</span></span> <span data-ttu-id="f1fd8-109">若要設計出可影響多個資料列的觸發程序，請使用資料列集邏輯而非資料指標。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-109">To design a trigger that affects multiple rows, use rowset-based logic instead of cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f1fd8-110">範例</span><span class="sxs-lookup"><span data-stu-id="f1fd8-110">Examples</span></span>  
 <span data-ttu-id="f1fd8-111">在以下範例中，DML 觸發程序是用來將資料行的累計值儲存到 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫中的另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-111">The DML triggers in the following examples are designed to store a running total of a column in another table of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
### <a name="a-storing-a-running-total-for-a-single-row-insert"></a><span data-ttu-id="f1fd8-112">A.</span><span class="sxs-lookup"><span data-stu-id="f1fd8-112">A.</span></span> <span data-ttu-id="f1fd8-113">儲存單一資料列插入的累加值</span><span class="sxs-lookup"><span data-stu-id="f1fd8-113">Storing a running total for a single-row insert</span></span>  
 <span data-ttu-id="f1fd8-114">當一個資料列載入至 `PurchaseOrderDetail` 資料表時，第一種 DML 觸發程序版本非常適用於單一資料列插入。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-114">The first version of the DML trigger works well for a single-row insert when a row of data is loaded into the `PurchaseOrderDetail` table.</span></span> <span data-ttu-id="f1fd8-115">INSERT 陳述式引發 DML 觸發程序，而且在此觸發程序的執行期間，會將新的資料列載入到 **inserted** 資料表。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-115">An INSERT statement fires the DML trigger, and the new row is loaded into the **inserted** table for the duration of the trigger execution.</span></span> <span data-ttu-id="f1fd8-116">`UPDATE` 陳述式為資料列讀取 `LineTotal` 資料行的值，並將此值與 `SubTotal` 資料表中 `PurchaseOrderHeader` 資料行中的現有值加以累計。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-116">The `UPDATE` statement reads the `LineTotal` column value for the row and adds that value to the existing value in the `SubTotal` column in the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="f1fd8-117">`WHERE` 子句確定 `PurchaseOrderDetail` 資料表中已更新的資料列與 `PurchaseOrderID` inserted **資料表中資料列的** 相符。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-117">The `WHERE` clause makes sure that the updated row in the `PurchaseOrderDetail` table matches the `PurchaseOrderID` of the row in the **inserted** table.</span></span>  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### <a name="b-storing-a-running-total-for-a-multirow-or-single-row-insert"></a><span data-ttu-id="f1fd8-118">B.</span><span class="sxs-lookup"><span data-stu-id="f1fd8-118">B.</span></span> <span data-ttu-id="f1fd8-119">儲存多資料列或單一資料列插入的累加值</span><span class="sxs-lookup"><span data-stu-id="f1fd8-119">Storing a running total for a multirow or single-row insert</span></span>  
 <span data-ttu-id="f1fd8-120">若範例 A 中的 DML 觸發程序執行多資料列的插入動作時，極有可能會發生錯誤；在 UPDATE 陳述式中，指派運算式右邊的運算式 (`SubTotal` + `LineTotal`) 只能是單一數值，而不能是一串數值。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-120">For a multirow insert, the DML trigger in example A might not operate correctly; the expression to the right of an assignment expression in an UPDATE statement (`SubTotal` + `LineTotal`) can be only a single value, not a list of values.</span></span> <span data-ttu-id="f1fd8-121">因此，觸發程序的作用是擷取 **inserted** 資料表中任意單一資料列中的值，並針對特定 `SubTotal` 值，將擷取的值與 `PurchaseOrderHeader` 資料表中現有的 `PurchaseOrderID` 值加以累計。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-121">Therefore, the effect of the trigger is to retrieve a value from any single row in the **inserted** table and add that value to the existing `SubTotal` value in the `PurchaseOrderHeader` table for a specific `PurchaseOrderID` value.</span></span> <span data-ttu-id="f1fd8-122">如果 `PurchaseOrderID` inserted **資料表中出現多次** 值，則此計算結果可能不是我們所要的。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-122">This operation might not have the expected effect if a single `PurchaseOrderID` value occurred more than one time in the **inserted** table.</span></span>  
  
 <span data-ttu-id="f1fd8-123">若要正確更新 `PurchaseOrderHeader` 資料表，觸發程序必須允許 **inserted** 資料表中可以有多個資料列。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-123">To correctly update the `PurchaseOrderHeader` table, the trigger must allow for the chance of multiple rows in the **inserted** table.</span></span> <span data-ttu-id="f1fd8-124">只要使用 `SUM` 函數，針對每個 `LineTotal` ，計算出 **inserted** 資料表中一組資料列的 `PurchaseOrderID`總數，就可以完成這個目標。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-124">You can do this by using the `SUM` function that calculates the total `LineTotal` for a group of rows in the **inserted** table for each `PurchaseOrderID`.</span></span> <span data-ttu-id="f1fd8-125">`SUM` 函數包含於相互關聯的子查詢中 (括號內的 `SELECT` 陳述式)。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-125">The `SUM` function is included in a correlated subquery (the `SELECT` statement in parentheses).</span></span> <span data-ttu-id="f1fd8-126">如果 `PurchaseOrderID` inserted **資料表中每個** 與 `PurchaseOrderID` 資料表中的 `PurchaseOrderHeader` 相符或相互關聯，則此子查詢會為每個相符的項目傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-126">This subquery returns a single value for each `PurchaseOrderID` in the **inserted** table that matches or is correlated with a `PurchaseOrderID` in the `PurchaseOrderHeader` table.</span></span>  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 <span data-ttu-id="f1fd8-127">此觸發程序在單一資料列插入中也適用； `LineTotal` 值資料行的總和即單一資料列的總和。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-127">This trigger also works correctly in a single-row insert; the sum of the `LineTotal` value column is the sum of a single row.</span></span> <span data-ttu-id="f1fd8-128">不過，由於此觸發程序， `IN` 子句運算子中使用的相互關聯子查詢與 `WHERE` 運算子需要從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]進行額外的處理。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-128">However, with this trigger the correlated subquery and the `IN` operator that is used in the `WHERE` clause require additional processing from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1fd8-129">這個動作對單一資料列插入是不必要的。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-129">This is unnecessary for a single-row insert.</span></span>  
  
### <a name="c-storing-a-running-total-based-on-the-type-of-insert"></a><span data-ttu-id="f1fd8-130">C.</span><span class="sxs-lookup"><span data-stu-id="f1fd8-130">C.</span></span> <span data-ttu-id="f1fd8-131">根據插入類型儲存累加值</span><span class="sxs-lookup"><span data-stu-id="f1fd8-131">Storing a running total based on the type of insert</span></span>  
 <span data-ttu-id="f1fd8-132">您可以變更觸發程序，使用最適於多個資料列的方法。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-132">You can change the trigger to use the method optimal for the number of rows.</span></span> <span data-ttu-id="f1fd8-133">例如， `@@ROWCOUNT` 函數可以在觸發程序邏輯中使用，以區別單一資料列插入及多資料列插入。</span><span class="sxs-lookup"><span data-stu-id="f1fd8-133">For example, the `@@ROWCOUNT` function can be used in the logic of the trigger to distinguish between a single and a multirow insert.</span></span>  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1fd8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1fd8-134">See Also</span></span>  
 [<span data-ttu-id="f1fd8-135">DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="f1fd8-135">DML Triggers</span></span>](dml-triggers.md)  
  
  
