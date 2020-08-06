---
title: 操作 UDT 資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
author: rothja
ms.author: jroth
ms.openlocfilehash: 75810a2ffd92130e45025f742d43ba7917d73992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698308"
---
# <a name="manipulating-udt-data"></a><span data-ttu-id="22dd8-102">操作 UDT 資料</span><span class="sxs-lookup"><span data-stu-id="22dd8-102">Manipulating UDT Data</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="22dd8-103">在修改使用者定義型別 (UDT) 資料行中的資料時，不會提供 INSERT、UPDATE 或 DELETE 陳述式的特定語法。</span><span class="sxs-lookup"><span data-stu-id="22dd8-103">provides no specialized syntax for INSERT, UPDATE, or DELETE statements when modifying data in user-defined type (UDT) columns.</span></span> <span data-ttu-id="22dd8-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 或 CONVERT 函數可用來將原生資料類型轉換為 UDT 類型。</span><span class="sxs-lookup"><span data-stu-id="22dd8-104">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions are used to cast native data types to the UDT type.</span></span>  
  
## <a name="inserting-data-in-a-udt-column"></a><span data-ttu-id="22dd8-105">將資料插入 UDT 資料行</span><span class="sxs-lookup"><span data-stu-id="22dd8-105">Inserting Data in a UDT Column</span></span>  
 <span data-ttu-id="22dd8-106">下列語句會將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 三個範例資料列插入至**Points**資料表。</span><span class="sxs-lookup"><span data-stu-id="22dd8-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements insert three rows of sample data into the **Points** table.</span></span> <span data-ttu-id="22dd8-107">**Point**資料類型是由會公開為 UDT 屬性的 X 和 Y 整數值所組成。</span><span class="sxs-lookup"><span data-stu-id="22dd8-107">The **Point** data type consists of X and Y integer values that are exposed as properties of the UDT.</span></span> <span data-ttu-id="22dd8-108">您必須使用 CAST 或 CONVERT 函數，將以逗號分隔的 X 和 Y 值轉換為**Point**類型。</span><span class="sxs-lookup"><span data-stu-id="22dd8-108">You must use either the CAST or CONVERT function to cast the comma-delimited X and Y values to the **Point** type.</span></span> <span data-ttu-id="22dd8-109">前兩個語句使用 CONVERT 函式，將字串值轉換為**Point**類型，而第三個語句則使用 CAST 函數：</span><span class="sxs-lookup"><span data-stu-id="22dd8-109">The first two statements use the CONVERT function to convert a string value to the **Point** type, and the third statement uses the CAST function:</span></span>  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a><span data-ttu-id="22dd8-110">選取資料</span><span class="sxs-lookup"><span data-stu-id="22dd8-110">Selecting Data</span></span>  
 <span data-ttu-id="22dd8-111">下列 SELECT 陳述式選取 UDT 的二進位值。</span><span class="sxs-lookup"><span data-stu-id="22dd8-111">The following SELECT statement selects the binary value of the UDT.</span></span>  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 <span data-ttu-id="22dd8-112">若要查看以可讀取格式顯示的輸出，請呼叫 `ToString` **Point** UDT 的方法，將值轉換為其字串表示。</span><span class="sxs-lookup"><span data-stu-id="22dd8-112">To see the output displayed in a readable format, call the `ToString` method of the **Point** UDT, which converts the value to its string representation.</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="22dd8-113">如此會產生下列結果。</span><span class="sxs-lookup"><span data-stu-id="22dd8-113">This produces the following results.</span></span>  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 <span data-ttu-id="22dd8-114">您還可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 及 CONVERT 函數，以取得相同的結果。</span><span class="sxs-lookup"><span data-stu-id="22dd8-114">You can also use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST and CONVERT functions to achieve the same results.</span></span>  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="22dd8-115">**Point** UDT 會將其 X 和 Y 座標公開為屬性，然後您就可以個別選取。</span><span class="sxs-lookup"><span data-stu-id="22dd8-115">The **Point** UDT exposes its X and Y coordinates as properties, which you can then select individually.</span></span> <span data-ttu-id="22dd8-116">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式分別選取 X 及 Y 座標：</span><span class="sxs-lookup"><span data-stu-id="22dd8-116">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects the X and Y coordinates separately:</span></span>  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="22dd8-117">X 及 Y 屬性傳回的整數值將顯示在結果集中。</span><span class="sxs-lookup"><span data-stu-id="22dd8-117">The X and Y properties return an integer value, which is displayed in the result set.</span></span>  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a><span data-ttu-id="22dd8-118">使用變數</span><span class="sxs-lookup"><span data-stu-id="22dd8-118">Working with Variables</span></span>  
 <span data-ttu-id="22dd8-119">使用變數時，可利用 DECLARE 陳述式將變數指派給 UDT 類型。</span><span class="sxs-lookup"><span data-stu-id="22dd8-119">You can work with variables using the DECLARE statement to assign a variable to a UDT type.</span></span> <span data-ttu-id="22dd8-120">下列陳述式使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] SET 陳述式指派值，並在變數上呼叫 UDT 的 `ToString` 方法以顯示結果。</span><span class="sxs-lookup"><span data-stu-id="22dd8-120">The following statements assign a value using the [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement and display the results by calling the UDT's `ToString` method on the variable:</span></span>  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="22dd8-121">結果集顯示變數值：</span><span class="sxs-lookup"><span data-stu-id="22dd8-121">The result set displays the variable value:</span></span>  
  
```  
PointValue  
----------  
-1,5  
```  
  
 <span data-ttu-id="22dd8-122">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式使用 SELECT (而非 SET) 進行變數指派時，可取得同樣的結果：</span><span class="sxs-lookup"><span data-stu-id="22dd8-122">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements achieve the same result using SELECT rather than SET for the variable assignment:</span></span>  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="22dd8-123">使用 SELECT 與 SET 進行變數指派的差異在於，SELECT 可讓您在一個 SELECT 陳述式中指派多個變數，而 SET 語法要求每個變數指派都具有自己的 SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="22dd8-123">The difference between using SELECT and SET for variable assignment is that SELECT allows you to assign multiple variables in one SELECT statement, whereas the SET syntax requires each variable assignment to have its own SET statement.</span></span>  
  
## <a name="comparing-data"></a><span data-ttu-id="22dd8-124">比較資料</span><span class="sxs-lookup"><span data-stu-id="22dd8-124">Comparing Data</span></span>  
 <span data-ttu-id="22dd8-125">定義類別時如果已將 `IsByteOrdered` 屬性設為 `true`，則可使用比較運算子比較 UDT 中的值。</span><span class="sxs-lookup"><span data-stu-id="22dd8-125">You can use comparison operators to compare values in your UDT if you have set the `IsByteOrdered` property to `true` when defining the class.</span></span> <span data-ttu-id="22dd8-126">如需詳細資訊，請參閱[建立使用者定義型](creating-user-defined-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="22dd8-126">For more information, see [Creating a User-Defined Type](creating-user-defined-types.md).</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 <span data-ttu-id="22dd8-127">如果值本身可比較，則可以比較 UDT 的內部值，無論 `IsByteOrdered` 設定為何。</span><span class="sxs-lookup"><span data-stu-id="22dd8-127">You can compare internal values of the UDT regardless of the `IsByteOrdered` setting if the values themselves are comparable.</span></span> <span data-ttu-id="22dd8-128">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式選取 X 大於 Y 的資料列：</span><span class="sxs-lookup"><span data-stu-id="22dd8-128">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects rows where X is greater than Y:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 <span data-ttu-id="22dd8-129">如這個搜尋相符 PointValue 的查詢所示，您還可以將變數與比較運算子搭配使用。</span><span class="sxs-lookup"><span data-stu-id="22dd8-129">You can also use comparison operators with variables, as shown in this query that searches for a matching PointValue.</span></span>  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a><span data-ttu-id="22dd8-130">叫用 UDT 方法</span><span class="sxs-lookup"><span data-stu-id="22dd8-130">Invoking UDT Methods</span></span>  
 <span data-ttu-id="22dd8-131">您也可在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中叫用 UDT 中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="22dd8-131">You can also invoke methods that are defined in your UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="22dd8-132">**Point**類別包含三個方法： `Distance` 、 `DistanceFrom` 和 `DistanceFromXY` 。</span><span class="sxs-lookup"><span data-stu-id="22dd8-132">The **Point** class contains three methods, `Distance`, `DistanceFrom`, and `DistanceFromXY`.</span></span> <span data-ttu-id="22dd8-133">如需定義這三種方法的程式代碼清單，請參閱[編碼使用者定義類型](creating-user-defined-types-coding.md)。</span><span class="sxs-lookup"><span data-stu-id="22dd8-133">For the code listings defining these three methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
 <span data-ttu-id="22dd8-134">下列的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會呼叫 `PointValue.Distance` 方法：</span><span class="sxs-lookup"><span data-stu-id="22dd8-134">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement calls the `PointValue.Distance` method:</span></span>  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="22dd8-135">結果會顯示在資料 `Distance` 行中：</span><span class="sxs-lookup"><span data-stu-id="22dd8-135">The results are displayed in the `Distance` column:</span></span>  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 <span data-ttu-id="22dd8-136">`DistanceFrom`方法接受**Point**資料類型的引數，並顯示從指定點到 PointValue 的距離：</span><span class="sxs-lookup"><span data-stu-id="22dd8-136">The `DistanceFrom` method takes an argument of **Point** data type, and displays the distance from the specified point to the PointValue:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 <span data-ttu-id="22dd8-137">結果顯示資料表中每個資料列之 `DistanceFrom` 方法的結果：</span><span class="sxs-lookup"><span data-stu-id="22dd8-137">The results display the results of the `DistanceFrom` method for each row in the table:</span></span>  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 <span data-ttu-id="22dd8-138">`DistanceFromXY` 方法將個別點視為引數：</span><span class="sxs-lookup"><span data-stu-id="22dd8-138">The `DistanceFromXY` method takes the points individually as arguments:</span></span>  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 <span data-ttu-id="22dd8-139">結果集與 `DistanceFrom` 方法相同。</span><span class="sxs-lookup"><span data-stu-id="22dd8-139">The result set is the same as the `DistanceFrom` method.</span></span>  
  
## <a name="updating-data-in-a-udt-column"></a><span data-ttu-id="22dd8-140">更新 UDT 資料行中的資料</span><span class="sxs-lookup"><span data-stu-id="22dd8-140">Updating Data in a UDT Column</span></span>  
 <span data-ttu-id="22dd8-141">若要更新 UDT 資料行中的資料，請使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="22dd8-141">To update data in a UDT column, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement.</span></span> <span data-ttu-id="22dd8-142">您還可以使用 UDT 的方法，以更新物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="22dd8-142">You can also use a method of the UDT to update the state of the object.</span></span> <span data-ttu-id="22dd8-143">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會更新資料表中的單一資料列：</span><span class="sxs-lookup"><span data-stu-id="22dd8-143">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates a single row in the table:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 <span data-ttu-id="22dd8-144">您也可個別更新 UDT 項目。</span><span class="sxs-lookup"><span data-stu-id="22dd8-144">You can also update UDT elements separately.</span></span> <span data-ttu-id="22dd8-145">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式僅更新 Y 座標：</span><span class="sxs-lookup"><span data-stu-id="22dd8-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates only the Y coordinate:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="22dd8-146">如果已定義位元組順序的 UDT 設為 `true`，則 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可以評估 WHERE 子句中的 UDT 資料行。</span><span class="sxs-lookup"><span data-stu-id="22dd8-146">If the UDT has been defined with byte ordering set to `true`, [!INCLUDE[tsql](../../includes/tsql-md.md)] can evaluate the UDT column in a WHERE clause.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a><span data-ttu-id="22dd8-147">更新限制</span><span class="sxs-lookup"><span data-stu-id="22dd8-147">Updating Limitations</span></span>  
 <span data-ttu-id="22dd8-148">不可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 一次更新多個屬性。</span><span class="sxs-lookup"><span data-stu-id="22dd8-148">You cannot update multiple properties at once using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="22dd8-149">例如，下列 UPDATE 陳述式失敗並發生錯誤，因為同一資料行名稱不可在一個 UPDATE 陳述式中使用兩次。</span><span class="sxs-lookup"><span data-stu-id="22dd8-149">For example, the following UPDATE statement fails with an error because you cannot use the same column name twice in one UDATE statement.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="22dd8-150">若要個別更新每個點，您需要在 Point UDT 組件中建立 Mutator 方法。</span><span class="sxs-lookup"><span data-stu-id="22dd8-150">To update each point individually, you would need to create a mutator method in the Point UDT assembly.</span></span> <span data-ttu-id="22dd8-151">然後，可以叫用 Mutator 方法，以更新 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 陳述式中的物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="22dd8-151">You can then invoke the mutator method to update the object in a [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement, as in the following:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a><span data-ttu-id="22dd8-152">刪除 UDT 資料行中的資料</span><span class="sxs-lookup"><span data-stu-id="22dd8-152">Deleting Data in a UDT Column</span></span>  
 <span data-ttu-id="22dd8-153">若要刪除 UDT 中的資料，請使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="22dd8-153">To delete data in a UDT, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span> <span data-ttu-id="22dd8-154">下列陳述式會刪除資料表中符合 WHERE 子句中所指定準則的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="22dd8-154">The following statement deletes all rows in the table that match the criteria specified in the WHERE clause.</span></span> <span data-ttu-id="22dd8-155">如果在 DELETE 陳述式中省略 WHERE 子句，將刪除資料表中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="22dd8-155">If you omit the WHERE clause in a DELETE statement, all rows in the table will be deleted.</span></span>  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 <span data-ttu-id="22dd8-156">若要移除 UDT 資料行中的值，同時又不變更其他資料列值，請使用 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="22dd8-156">Use the UPDATE statement if you want to remove the values in a UDT column while leaving other row values intact.</span></span> <span data-ttu-id="22dd8-157">此範例將 PointValue 設為 Null。</span><span class="sxs-lookup"><span data-stu-id="22dd8-157">This example sets the PointValue to null.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a><span data-ttu-id="22dd8-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22dd8-158">See Also</span></span>  
 [<span data-ttu-id="22dd8-159">在 SQL Server 中使用使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="22dd8-159">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
