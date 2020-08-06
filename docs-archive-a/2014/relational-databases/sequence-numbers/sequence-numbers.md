---
title: 序號 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sequence number object, overview
- sequence [Database Engine]
- autonumbers, sequences
- sequence numbers [SQL Server]
- sequence number object
ms.assetid: c900e30d-2fd3-4d5f-98ee-7832f37e79d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c65b4df915a85cf0ec7c7c0c8c0ff9f6607ad96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709046"
---
# <a name="sequence-numbers"></a><span data-ttu-id="59954-102">序號</span><span class="sxs-lookup"><span data-stu-id="59954-102">Sequence Numbers</span></span>
  <span data-ttu-id="59954-103">序列是使用者定義的結構描述繫結物件，該物件會根據建立順序所使用的規格產生數值序列。</span><span class="sxs-lookup"><span data-stu-id="59954-103">A sequence is a user-defined schema-bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="59954-104">數值序列是在定義的間隔依照遞增或遞減順序來產生，而且可依照要求循環 (重複)。</span><span class="sxs-lookup"><span data-stu-id="59954-104">The sequence of numeric values is generated in an ascending or descending order at a defined interval and may cycle (repeat) as requested.</span></span> <span data-ttu-id="59954-105">與識別欄位不同的是，順序不會與資料表產生關聯。</span><span class="sxs-lookup"><span data-stu-id="59954-105">Sequences, unlike identity columns, are not associated with tables.</span></span> <span data-ttu-id="59954-106">應用程式會參考順序物件，以擷取它的下一個值。</span><span class="sxs-lookup"><span data-stu-id="59954-106">An application refers to a sequence object to receive its next value.</span></span> <span data-ttu-id="59954-107">順序與資料表之間的關聯性是由應用程式所控制。</span><span class="sxs-lookup"><span data-stu-id="59954-107">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="59954-108">使用者應用程式可以參考順序物件，並協調跨越多個資料列和資料表的值索引鍵。</span><span class="sxs-lookup"><span data-stu-id="59954-108">User applications can reference a sequence object and coordinate the values keys across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="59954-109">順序是使用 **CREATE SEQUENCE** 陳述式所建立，與資料表無關。</span><span class="sxs-lookup"><span data-stu-id="59954-109">A sequence is created independently of the tables by using the **CREATE SEQUENCE** statement.</span></span> <span data-ttu-id="59954-110">有一些選項可讓您控制遞增、最大和最小值、起點、自動重新啟動功能與快取以改善效能。</span><span class="sxs-lookup"><span data-stu-id="59954-110">Options enable you to control the increment, maximum and minimum values, starting point, automatic restarting capability, and caching to improve performance.</span></span> <span data-ttu-id="59954-111">如需有關這些選項的詳細資訊，請參閱 [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="59954-111">For information about the options, see [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
 <span data-ttu-id="59954-112">不同於插入資料列時產生的識別欄位值，應用程式可以藉由呼叫 [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) 函數，在插入資料列之前取得下一個序號。</span><span class="sxs-lookup"><span data-stu-id="59954-112">Unlike identity column values, which are generated when rows are inserted, an application can obtain the next sequence number before inserting the row by calling the [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) function.</span></span> <span data-ttu-id="59954-113">此序號是在呼叫 NEXT VALUE FOR 時配置的，即使該編號從未插入資料表也一樣。</span><span class="sxs-lookup"><span data-stu-id="59954-113">The sequence number is allocated when NEXT VALUE FOR is called even if the number is never inserted into a table.</span></span> <span data-ttu-id="59954-114">NEXT VALUE FOR 函數可當做資料表定義中資料行的預設值使用。</span><span class="sxs-lookup"><span data-stu-id="59954-114">The NEXT VALUE FOR function can be used as the default value for a column in a table definition.</span></span> <span data-ttu-id="59954-115">您可以使用 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 一次取得多個序號範圍。</span><span class="sxs-lookup"><span data-stu-id="59954-115">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get a range of multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="59954-116">順序可以定義為任何整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="59954-116">A sequence can be defined as any integer data type.</span></span> <span data-ttu-id="59954-117">如果沒有指定資料類型，順序就會預設為 `bigint`。</span><span class="sxs-lookup"><span data-stu-id="59954-117">If the data type is not specified, a sequence defaults to `bigint`.</span></span>  
  
## <a name="using-sequences"></a><span data-ttu-id="59954-118">使用順序</span><span class="sxs-lookup"><span data-stu-id="59954-118">Using Sequences</span></span>  
 <span data-ttu-id="59954-119">在下列案例中，您可以使用順序來取代識別欄位：</span><span class="sxs-lookup"><span data-stu-id="59954-119">Use sequences instead of identity columns in the following scenarios:</span></span>  
  
-   <span data-ttu-id="59954-120">進行插入資料表的作業之前，應用程式需要一個編號。</span><span class="sxs-lookup"><span data-stu-id="59954-120">The application requires a number before the insert into the table is made.</span></span>  
  
-   <span data-ttu-id="59954-121">應用程式需要在多個資料表或資料表中多個資料行之間共用單一編號序列。</span><span class="sxs-lookup"><span data-stu-id="59954-121">The application requires sharing a single series of numbers between multiple tables or multiple columns within a table.</span></span>  
  
-   <span data-ttu-id="59954-122">達到指定的編號時，應用程式必須重新啟動編號序列。</span><span class="sxs-lookup"><span data-stu-id="59954-122">The application must restart the number series when a specified number is reached.</span></span> <span data-ttu-id="59954-123">例如，指派 1 到 10 的值之後，應用程式就會再次開始指派 1 到 10 的值。</span><span class="sxs-lookup"><span data-stu-id="59954-123">For example, after assigning values 1 through 10, the application starts assigning values 1 through 10 again.</span></span>  
  
-   <span data-ttu-id="59954-124">應用程式要求依照另一個欄位排序順序值。</span><span class="sxs-lookup"><span data-stu-id="59954-124">The application requires sequence values to be sorted by another field.</span></span> <span data-ttu-id="59954-125">NEXT VALUE FOR 函數可以將 OVER 子句套用至函數呼叫。</span><span class="sxs-lookup"><span data-stu-id="59954-125">The NEXT VALUE FOR function can apply the OVER clause to the function call.</span></span> <span data-ttu-id="59954-126">OVER 子句會確保傳回的值都按照 OVER 子句之 ORDER BY 子句的順序來產生。</span><span class="sxs-lookup"><span data-stu-id="59954-126">The OVER clause guarantees that the values returned are generated in the order of the OVER clause's ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="59954-127">應用程式要求同時指派多個編號。</span><span class="sxs-lookup"><span data-stu-id="59954-127">An application requires multiple numbers to be assigned at the same time.</span></span> <span data-ttu-id="59954-128">例如，應用程式需要保留五個序號。</span><span class="sxs-lookup"><span data-stu-id="59954-128">For example, an application needs to reserve five sequential numbers.</span></span> <span data-ttu-id="59954-129">如果同時針對其他處理序發出編號，要求識別值可能會在序列中產生間距。</span><span class="sxs-lookup"><span data-stu-id="59954-129">Requesting identity values could result in gaps in the series if other processes were simultaneously issued numbers.</span></span> <span data-ttu-id="59954-130">呼叫 sp_sequence_get_range 可以一次擷取順序中的許多編號。</span><span class="sxs-lookup"><span data-stu-id="59954-130">Calling sp_sequence_get_range can retrieve several numbers in the sequence at once.</span></span>  
  
-   <span data-ttu-id="59954-131">您必須變更順序的規格，例如遞增值。</span><span class="sxs-lookup"><span data-stu-id="59954-131">You need to change the specification of the sequence, such as the increment value.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="59954-132">限制</span><span class="sxs-lookup"><span data-stu-id="59954-132">Limitations</span></span>  
 <span data-ttu-id="59954-133">不同於無法變更其值的識別欄位，當順序值插入資料表之後，並不會自動受保護。</span><span class="sxs-lookup"><span data-stu-id="59954-133">Unlike identity columns, whose values cannot be changed, sequence values are not automatically protected after insertion into the table.</span></span> <span data-ttu-id="59954-134">若要防止順序值變更，請在資料表上使用更新觸發程序來回復變更。</span><span class="sxs-lookup"><span data-stu-id="59954-134">To prevent sequence values from being changed, use an update trigger on the table to roll back changes.</span></span>  
  
 <span data-ttu-id="59954-135">系統不會針對順序值自動強制執行唯一性。</span><span class="sxs-lookup"><span data-stu-id="59954-135">Uniqueness is not automatically enforced for sequence values.</span></span> <span data-ttu-id="59954-136">重複使用順序值的能力是依照設計提供的。</span><span class="sxs-lookup"><span data-stu-id="59954-136">The ability to reuse sequence values is by design.</span></span> <span data-ttu-id="59954-137">如果資料表中的順序值都必須是唯一的，請針對資料行建立唯一索引。</span><span class="sxs-lookup"><span data-stu-id="59954-137">If sequence values in a table are required to be unique, create a unique index on the column.</span></span> <span data-ttu-id="59954-138">如果資料表中的順序值在整個資料表群組中必須是唯一的，請建立觸發程序來防止更新陳述式或序號循環所導致的重複項目。</span><span class="sxs-lookup"><span data-stu-id="59954-138">If sequence values in a table are required to be unique throughout a group of tables, create triggers to prevent duplicates caused by update statements or sequence number cycling.</span></span>  
  
 <span data-ttu-id="59954-139">雖然順序物件會根據其定義產生編號，不過順序物件不會控制編號的使用方式。</span><span class="sxs-lookup"><span data-stu-id="59954-139">The sequence object generates numbers according to its definition, but the sequence object does not control how the numbers are used.</span></span> <span data-ttu-id="59954-140">當您回復交易時、當多個資料表共用順序物件時，或者當您配置序號而沒有將它們用於資料表時，插入資料表中的序號可能會產生間距。</span><span class="sxs-lookup"><span data-stu-id="59954-140">Sequence numbers inserted into a table can have gaps when a transaction is rolled back, when a sequence object is shared by multiple tables, or when sequence numbers are allocated without using them in tables.</span></span> <span data-ttu-id="59954-141">以 CACHE 選項建立時，非預期關閉 (例如停電) 可能會失去快取中的序號。</span><span class="sxs-lookup"><span data-stu-id="59954-141">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="59954-142">如果單一 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式具有多個指定相同順序產生器的 `NEXT VALUE FOR` 函數執行個體，所有執行個體都會針對該 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式所處理的給定資料列傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="59954-142">If there are multiple instances of the `NEXT VALUE FOR` function specifying the same sequence generator within a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, all those instances return the same value for a given row processed by that [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="59954-143">這種行為與 ANSI 標準一致。</span><span class="sxs-lookup"><span data-stu-id="59954-143">This behavior is consistent with the ANSI standard.</span></span>  
  
## <a name="typical-use"></a><span data-ttu-id="59954-144">一般用法</span><span class="sxs-lookup"><span data-stu-id="59954-144">Typical Use</span></span>  
 <span data-ttu-id="59954-145">若要建立從 -2,147,483,648 到 2,147,483,647 且遞增量為 1 的整數序號，請使用下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="59954-145">To create an integer sequence number that increments by 1 from -2,147,483,648 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    INCREMENT BY 1 ;  
```  
  
 <span data-ttu-id="59954-146">若要建立從 1 到 2,147,483,647 且遞增量為 1 的整數序號 (類似於識別欄位)，請使用下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="59954-146">To create an integer sequence number similar to an identity column that increments by 1 from 1 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
  
```  
  
## <a name="managing-sequences"></a><span data-ttu-id="59954-147">管理順序</span><span class="sxs-lookup"><span data-stu-id="59954-147">Managing Sequences</span></span>  
 <span data-ttu-id="59954-148">如需有關順序的詳細資訊，請查詢 [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="59954-148">For information about sequences, query [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="59954-149">範例</span><span class="sxs-lookup"><span data-stu-id="59954-149">Examples</span></span>  
 <span data-ttu-id="59954-150">[CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql)、[NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql) 和 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 主題中有其他範例。</span><span class="sxs-lookup"><span data-stu-id="59954-150">There are additional examples in the topics [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql), and [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql).</span></span>  
  
### <a name="a-using-a-sequence-number-in-a-single-table"></a><span data-ttu-id="59954-151">A.</span><span class="sxs-lookup"><span data-stu-id="59954-151">A.</span></span> <span data-ttu-id="59954-152">在單一資料表中使用序號</span><span class="sxs-lookup"><span data-stu-id="59954-152">Using a sequence number in a single table</span></span>  
 <span data-ttu-id="59954-153">下列範例會建立名為 Test 的結構描述、名為 Orders 的資料表，以及名為 CountBy1 的順序，然後使用 NEXT VALUE FOR 函數，將資料列插入資料表。</span><span class="sxs-lookup"><span data-stu-id="59954-153">The following example creates a schema named Test, a table named Orders, and a sequence named CountBy1, and then inserts rows into the table using the NEXT VALUE FOR function.</span></span>  
  
```  
--Create the Test schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Orders  
    (OrderID int PRIMARY KEY,  
    Name varchar(20) NOT NULL,  
    Qty int NOT NULL);  
GO  
  
-- Create a sequence  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
-- Insert three records  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Tire', 2) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Seat', 1) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Brake', 1) ;  
GO  
  
-- View the table  
SELECT * FROM Test.Orders ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `OrderID  Name    Qty`  
  
 `1        Tire    2`  
  
 `2        Seat    1`  
  
 `3        Brake   1`  
  
### <a name="b-calling-next-value-for-before-inserting-a-row"></a><span data-ttu-id="59954-154">B.</span><span class="sxs-lookup"><span data-stu-id="59954-154">B.</span></span> <span data-ttu-id="59954-155">在插入資料列之前呼叫 NEXT VALUE FOR</span><span class="sxs-lookup"><span data-stu-id="59954-155">Calling NEXT VALUE FOR before inserting a row</span></span>  
 <span data-ttu-id="59954-156">下列範例會使用在範例 A 中建立的 `Orders` 資料表來宣告名為 `@nextID`的變數，然後使用 NEXT VALUE FOR 函數，將此變數設定為下一個可用的序號。</span><span class="sxs-lookup"><span data-stu-id="59954-156">Using the `Orders` table created in example A, the following example declares a variable named `@nextID`, and then uses the NEXT VALUE FOR function to set the variable to the next available sequence number.</span></span> <span data-ttu-id="59954-157">應用程式應該會針對訂單進行一些處理，例如為客戶提供其潛在訂單的 `OrderID` 編號，然後驗證訂單。</span><span class="sxs-lookup"><span data-stu-id="59954-157">The application is presumed to do some processing of the order, such as providing the customer with the `OrderID` number of their potential order, and then validates the order.</span></span> <span data-ttu-id="59954-158">不論這項處理可能需要多少時間，或者在處理期間加入其他多少訂單，原始的編號都會保留給這個連接使用。</span><span class="sxs-lookup"><span data-stu-id="59954-158">No matter how long this processing might take, or how many other orders are added during the process, the original number is preserved for use by this connection.</span></span> <span data-ttu-id="59954-159">最後， `INSERT` 陳述式會將訂單加入至 `Orders` 資料表。</span><span class="sxs-lookup"><span data-stu-id="59954-159">Finally, the `INSERT` statement adds the order to the `Orders` table.</span></span>  
  
```  
DECLARE @NextID int ;  
SET @NextID = NEXT VALUE FOR Test.CountBy1;  
-- Some work happens  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (@NextID, 'Rim', 2) ;  
GO  
  
```  
  
### <a name="c-using-a-sequence-number-in-multiple-tables"></a><span data-ttu-id="59954-160">C.</span><span class="sxs-lookup"><span data-stu-id="59954-160">C.</span></span> <span data-ttu-id="59954-161">在多個資料表中使用序號</span><span class="sxs-lookup"><span data-stu-id="59954-161">Using a sequence number in multiple tables</span></span>  
 <span data-ttu-id="59954-162">這個範例會假設生產線監視處理序接收整個工廠所發生之事件的通知。</span><span class="sxs-lookup"><span data-stu-id="59954-162">This example assumes that a production-line monitoring process receives notification of events that occur throughout the workshop.</span></span> <span data-ttu-id="59954-163">每個事件都會接收唯一且單純遞增的 `EventID` 編號。</span><span class="sxs-lookup"><span data-stu-id="59954-163">Each event receives a unique and monotonically increasing `EventID` number.</span></span> <span data-ttu-id="59954-164">所有事件都會使用相同的 `EventID` 序號，讓結合所有事件的報表能夠唯一識別每個事件。</span><span class="sxs-lookup"><span data-stu-id="59954-164">All events use the same `EventID` sequence number so that reports that combine all events can uniquely identify each event.</span></span> <span data-ttu-id="59954-165">不過，事件資料會根據事件的類型儲存在三個不同的資料表中。</span><span class="sxs-lookup"><span data-stu-id="59954-165">However the event data is stored in three different tables, depending on the type of event.</span></span> <span data-ttu-id="59954-166">此程式碼範例會建立名為 `Audit`的結構描述、名為 `EventCounter`的順序，以及三個資料表，而且每個資料表都使用 `EventCounter` 順序作為預設值。</span><span class="sxs-lookup"><span data-stu-id="59954-166">The code example creates a schema named `Audit`, a sequence named `EventCounter`, and three tables which each use the `EventCounter` sequence as a default value.</span></span> <span data-ttu-id="59954-167">然後，此範例會將資料列加入至三個資料表並查詢結果。</span><span class="sxs-lookup"><span data-stu-id="59954-167">Then the example adds rows to the three tables and queries the results.</span></span>  
  
```  
CREATE SCHEMA Audit ;  
GO  
CREATE SEQUENCE Audit.EventCounter  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
CREATE TABLE Audit.ProcessEvents  
(  
    EventID int PRIMARY KEY CLUSTERED   
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EventCode nvarchar(5) NOT NULL,  
    Description nvarchar(300) NULL  
) ;  
GO  
  
CREATE TABLE Audit.ErrorEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NULL,  
    ErrorNumber int NOT NULL,  
    EventDesc nvarchar(256) NULL  
) ;  
GO  
  
CREATE TABLE Audit.StartStopEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NOT NULL,  
    StartOrStop bit NOT NULL  
) ;  
GO  
  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 0) ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (72, 0) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (2735,   
    'Clean room temperature 18 degrees C.') ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (18, 'Spin rate threashold exceeded.') ;  
INSERT Audit.ErrorEvents (EquipmentID, ErrorNumber, EventDesc)   
    VALUES (248, 82, 'Feeder jam') ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 1) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (1841, 'Central feed in bypass mode.') ;  
-- The following statement combines all events, though not all fields.  
SELECT EventID, EventTime, Description FROM Audit.ProcessEvents   
UNION SELECT EventID, EventTime, EventDesc FROM Audit.ErrorEvents   
UNION SELECT EventID, EventTime,   
CASE StartOrStop   
    WHEN 0 THEN 'Start'   
    ELSE 'Stop'  
END   
FROM Audit.StartStopEvents  
ORDER BY EventID ;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `EventID  EventTime                Description`  
  
 `1        2009-11-02 15:00:51.157  Start`  
  
 `2        2009-11-02 15:00:51.160  Start`  
  
 `3        2009-11-02 15:00:51.167  Clean room temperature 18 degrees C.`  
  
 `4        2009-11-02 15:00:51.167  Spin rate threshold exceeded.`  
  
 `5        2009-11-02 15:00:51.173  Feeder jam`  
  
 `6        2009-11-02 15:00:51.177  Stop`  
  
 `7        2009-11-02 15:00:51.180  Central feed in bypass mode.`  
  
### <a name="d-generating-repeating-sequence-numbers-in-a-result-set"></a><span data-ttu-id="59954-168">D.</span><span class="sxs-lookup"><span data-stu-id="59954-168">D.</span></span> <span data-ttu-id="59954-169">在結果集中產生重複的序號</span><span class="sxs-lookup"><span data-stu-id="59954-169">Generating repeating sequence numbers in a result set</span></span>  
 <span data-ttu-id="59954-170">下列範例會示範序號的兩種功能：循環以及在 SELECT 陳述式中使用 `NEXT VALUE FOR` 。</span><span class="sxs-lookup"><span data-stu-id="59954-170">The following example demonstrates two features of sequence numbers: cycling, and using `NEXT VALUE FOR` in a select statement.</span></span>  
  
```  
CREATE SEQUENCE CountBy5  
   AS tinyint  
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 5  
    CYCLE ;  
GO  
  
SELECT NEXT VALUE FOR CountBy5 AS SurveyGroup, Name FROM sys.objects ;  
GO  
```  
  
### <a name="e-generating-sequence-numbers-for-a-result-set-by-using-the-over-clause"></a><span data-ttu-id="59954-171">E.</span><span class="sxs-lookup"><span data-stu-id="59954-171">E.</span></span> <span data-ttu-id="59954-172">使用 OVER 子句來產生結果集的序號</span><span class="sxs-lookup"><span data-stu-id="59954-172">Generating sequence numbers for a result set by using the OVER clause</span></span>  
 <span data-ttu-id="59954-173">下列範例會使用 `OVER` 子句並依照 `Name` 排序結果集，然後再加入序號資料行。</span><span class="sxs-lookup"><span data-stu-id="59954-173">The following example uses the `OVER` clause to sort the result set by `Name` before it adds the sequence number column.</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Samples ;  
GO  
  
CREATE SEQUENCE Samples.IDLabel  
    AS tinyint  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="f-resetting-the-sequence-number"></a><span data-ttu-id="59954-174">F.</span><span class="sxs-lookup"><span data-stu-id="59954-174">F.</span></span> <span data-ttu-id="59954-175">重設序號</span><span class="sxs-lookup"><span data-stu-id="59954-175">Resetting the sequence number</span></span>  
 <span data-ttu-id="59954-176">範例 E 取用了前 79 個 `Samples.IDLabel` 序號 </span><span class="sxs-lookup"><span data-stu-id="59954-176">Example E consumed the first 79 of the `Samples.IDLabel` sequence numbers.</span></span> <span data-ttu-id="59954-177">(您的 `AdventureWorks2012` 版本可能會傳回不同的結果數目)。請執行下列陳述式來取用後續 79 個序號 (80 到 158)。</span><span class="sxs-lookup"><span data-stu-id="59954-177">(Your version of `AdventureWorks2012` may return a different number of results.) Execute the following to consume the next 79 sequence numbers (80 though 158).</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
 <span data-ttu-id="59954-178">請執行下列陳述式來重新啟動 `Samples.IDLabel` 順序。</span><span class="sxs-lookup"><span data-stu-id="59954-178">Execute the following statement to restart the `Samples.IDLabel` sequence.</span></span>  
  
```  
ALTER SEQUENCE Samples.IDLabel  
RESTART WITH 1 ;  
```  
  
 <span data-ttu-id="59954-179">請再次執行 SELECT 陳述式，以便確認 `Samples.IDLabel` 順序從編號 1 重新啟動。</span><span class="sxs-lookup"><span data-stu-id="59954-179">Execute the select statement again to verify that the `Samples.IDLabel` sequence restarted with number 1.</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="g-changing-a-table-from-identity-to-sequence"></a><span data-ttu-id="59954-180">G.</span><span class="sxs-lookup"><span data-stu-id="59954-180">G.</span></span> <span data-ttu-id="59954-181">將資料表從識別變更為順序</span><span class="sxs-lookup"><span data-stu-id="59954-181">Changing a table from identity to sequence</span></span>  
 <span data-ttu-id="59954-182">下列範例會建立結構描述以及包含範例中三個資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="59954-182">The following example creates a schema and table containing three rows for the example.</span></span> <span data-ttu-id="59954-183">然後，此範例會加入新的資料行並卸除舊的資料行。</span><span class="sxs-lookup"><span data-stu-id="59954-183">Then the example adds a new column and drops the old column.</span></span>  
  
```  
-- Create a schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Department  
    (  
        DepartmentID smallint IDENTITY(1,1) NOT NULL,  
        Name nvarchar(100) NOT NULL,  
        GroupName nvarchar(100) NOT NULL  
    CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC)   
    ) ;  
GO  
  
-- Insert three rows into the table  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Engineering', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Tool Design', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Sales', 'Sales and Marketing');  
GO  
  
-- View the table that will be changed  
SELECT * FROM Test.Department ;  
GO  
  
-- End of portion creating a sample table  
--------------------------------------------------------  
-- Add the new column that does not have the IDENTITY property  
ALTER TABLE Test.Department   
    ADD DepartmentIDNew smallint NULL  
GO  
  
-- Copy values from the old column to the new column  
UPDATE Test.Department  
    SET DepartmentIDNew = DepartmentID ;  
GO  
  
-- Drop the primary key constraint on the old column  
ALTER TABLE Test.Department  
    DROP CONSTRAINT [PK_Department_DepartmentID];  
-- Drop the old column  
ALTER TABLE Test.Department  
    DROP COLUMN DepartmentID ;  
GO  
  
-- Rename the new column to the old columns name  
EXEC sp_rename 'Test.Department.DepartmentIDNew',   
    'DepartmentID', 'COLUMN';  
GO  
  
-- Change the new column to NOT NULL  
ALTER TABLE Test.Department  
    ALTER COLUMN DepartmentID smallint NOT NULL ;  
-- Add the unique primary key constraint  
ALTER TABLE Test.Department  
    ADD CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC) ;  
-- Get the highest current value from the DepartmentID column   
-- and create a sequence to use with the column. (Returns 3.)  
SELECT MAX(DepartmentID) FROM Test.Department ;  
-- Use the next desired value (4) as the START WITH VALUE;  
CREATE SEQUENCE Test.DeptSeq  
    AS smallint  
    START WITH 4  
    INCREMENT BY 1 ;  
GO  
  
-- Add a default value for the DepartmentID column  
ALTER TABLE Test.Department  
    ADD CONSTRAINT DefSequence DEFAULT (NEXT VALUE FOR Test.DeptSeq)   
        FOR DepartmentID;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;   
-- Test insert  
INSERT Test.Department (Name, GroupName)  
    VALUES ('Audit', 'Quality Assurance') ;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;  
GO  
  
```  
  
 <span data-ttu-id="59954-184">使用 `SELECT *` 的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式將收到新的資料行做為最後一個資料行，而非第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="59954-184">[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that use `SELECT *` will receive the new column as the last column instead of the first column.</span></span> <span data-ttu-id="59954-185">如果這是無法接受的資料行，您就必須建立全新的資料表、將資料移入其中，然後重新建立新資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="59954-185">If this is not acceptable, then you must create an entirely new table, move the data to it, and then recreate the permissions on the new table.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="59954-186">相關內容</span><span class="sxs-lookup"><span data-stu-id="59954-186">Related Content</span></span>  
 [<span data-ttu-id="59954-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="59954-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-sequence-transact-sql)  
  
 [<span data-ttu-id="59954-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="59954-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-sequence-transact-sql)  
  
 [<span data-ttu-id="59954-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="59954-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-sequence-transact-sql)  
  
 [<span data-ttu-id="59954-190">IDENTITY &#40;屬性&#41; &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="59954-190">IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql-identity-property)  
  
  
