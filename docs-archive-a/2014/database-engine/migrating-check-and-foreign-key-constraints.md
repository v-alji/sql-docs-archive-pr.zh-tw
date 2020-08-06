---
title: 遷移 Check 和 Foreign Key 條件約束 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e0a1a1e4-0062-4872-93c3-cd91b7a43c23
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4bacd7a9c5c00fc6abbb763eaa02dca9493fa513
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596880"
---
# <a name="migrating-check-and-foreign-key-constraints"></a><span data-ttu-id="e49d9-102">合併 Check 和外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="e49d9-102">Migrating Check and Foreign Key Constraints</span></span>
  <span data-ttu-id="e49d9-103">中不支援 Check 和 foreign key 條件約束 [!INCLUDE[hek_2](../includes/hek-2-md.md)] [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e49d9-103">Check and foreign key constraints are not supported in [!INCLUDE[hek_2](../includes/hek-2-md.md)] in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e49d9-104">這些結構通常是用來在架構中強制執行邏輯資料完整性，並且對於維護應用程式的功能正確性而言很重要。</span><span class="sxs-lookup"><span data-stu-id="e49d9-104">These constructs are usually used to enforce logical data integrity in the schema and can be important to maintaining the functional correctness of applications.</span></span>  
  
 <span data-ttu-id="e49d9-105">資料表上的邏輯完整性檢查（例如 check 和 foreign key 條件約束）需要額外的交易處理，而且通常應該避免對效能敏感的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e49d9-105">Logical integrity checks on a table such as check and foreign key constraints require additional processing on transactions and should generally be avoided for performance-sensitive applications.</span></span> <span data-ttu-id="e49d9-106">不過，如果這類檢查對您的應用程式很重要，則有兩種因應措施。</span><span class="sxs-lookup"><span data-stu-id="e49d9-106">However, if such checks are crucial to your application, there exist two workarounds.</span></span>  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a><span data-ttu-id="e49d9-107">在插入、更新或刪除作業之後檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="e49d9-107">Checking Constraints After an Insert, Update, or Delete Operation</span></span>  
 <span data-ttu-id="e49d9-108">這個因應措施是開放式的，這是根據大部分變更不違反條件約束的假設。</span><span class="sxs-lookup"><span data-stu-id="e49d9-108">This workaround is optimistic, based on the assumption that the majority of changes do not violate the constraints.</span></span> <span data-ttu-id="e49d9-109">在此解決方法中，會先修改資料，然後才評估條件約束。</span><span class="sxs-lookup"><span data-stu-id="e49d9-109">In this workaround, data is modified first before the constraints are evaluated.</span></span> <span data-ttu-id="e49d9-110">如果違反條件約束，則會偵測到，但不會回復變更。</span><span class="sxs-lookup"><span data-stu-id="e49d9-110">If a constraint is violated, it would be detected, but the change will not be rolled back.</span></span>  
  
 <span data-ttu-id="e49d9-111">這個因應措施的優點是對效能的影響最小，因為資料修改不會受到條件約束檢查封鎖。</span><span class="sxs-lookup"><span data-stu-id="e49d9-111">This workaround has the advantage of having minimal impact on performance because data modification is not blocked by constraint checks.</span></span> <span data-ttu-id="e49d9-112">不過，如果違反一個或多個條件約束的變更發生，則回復該變更的程式可能會花很長的時間。</span><span class="sxs-lookup"><span data-stu-id="e49d9-112">However, if a change that violates one or more constraints does occur, the process to roll back that change could take a long time.</span></span>  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a><span data-ttu-id="e49d9-113">在插入、更新或刪除作業之前強制執行條件約束</span><span class="sxs-lookup"><span data-stu-id="e49d9-113">Enforcing Constraints Before an Insert, Update, or Delete Operation</span></span>  
 <span data-ttu-id="e49d9-114">此解決方法會模擬 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 條件約束的行為。</span><span class="sxs-lookup"><span data-stu-id="e49d9-114">This workaround emulates the behavior of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] constraints.</span></span> <span data-ttu-id="e49d9-115">條件約束會在進行資料修改之前檢查，而且如果檢查失敗，則會終止交易。</span><span class="sxs-lookup"><span data-stu-id="e49d9-115">The constraints are checked before data modification occurs and will terminate the transaction if a check fails.</span></span> <span data-ttu-id="e49d9-116">這個方法會對資料修改產生效能上的負面影響，但會確保資料表內的資料一律符合條件約束。</span><span class="sxs-lookup"><span data-stu-id="e49d9-116">This method incurs a performance penalty on data modifications, but ensures that data inside a table always satisfies the constraints.</span></span>  
  
 <span data-ttu-id="e49d9-117">當邏輯資料完整性對正確性和違反條件約束的修改可能很重要時，請使用此因應措施。</span><span class="sxs-lookup"><span data-stu-id="e49d9-117">Use this workaround when logical data integrity is crucial to correctness and modifications that violate a constraint are likely.</span></span> <span data-ttu-id="e49d9-118">不過，若要保證完整性，所有資料修改都必須透過包含這些實行原則的預存程式進行。</span><span class="sxs-lookup"><span data-stu-id="e49d9-118">However, to guarantee integrity, all data modifications must occur through stored procedures that include these enforcements.</span></span> <span data-ttu-id="e49d9-119">透過臨機操作查詢和其他預存程式的修改將不會強制執行這些條件約束，因此可能會違反它們而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="e49d9-119">Modifications through ad-hoc queries and other stored procedures will not enforce these constraints and therefore may violate them with no warning.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="e49d9-120">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="e49d9-120">Sample Code</span></span>  
 <span data-ttu-id="e49d9-121">下列範例是以 AdventureWorks2012 資料庫為基礎。</span><span class="sxs-lookup"><span data-stu-id="e49d9-121">The following samples are based on the AdventureWorks2012 database.</span></span> <span data-ttu-id="e49d9-122">具體而言，這些範例是以 [Sales] 為基礎。[SalesOrderDetail] 資料表和其相關聯的 check 和 foreign key 條件約束（除了唯一索引以外）。</span><span class="sxs-lookup"><span data-stu-id="e49d9-122">Specifically, these samples are based on the [Sales].[SalesOrderDetail] table and its associated check and foreign key constraints in addition to the unique index.</span></span>  
  
 <span data-ttu-id="e49d9-123">此處指定的預存程式僅適用于內凹作業。</span><span class="sxs-lookup"><span data-stu-id="e49d9-123">The stored procedures specified here are for inset operations only.</span></span> <span data-ttu-id="e49d9-124">Update 和 delete 作業的預存程式應具有類似的結構。</span><span class="sxs-lookup"><span data-stu-id="e49d9-124">Stored procedures for update and delete operations should have similar structures.</span></span>  
  
## <a name="table-definition-for-the-workarounds"></a><span data-ttu-id="e49d9-125">解決方法的資料表定義</span><span class="sxs-lookup"><span data-stu-id="e49d9-125">Table Definition for the Workarounds</span></span>  
 <span data-ttu-id="e49d9-126">轉換成記憶體優化資料表之前，[Sales] 的定義。[SalesOrderDetail] 如下所示：</span><span class="sxs-lookup"><span data-stu-id="e49d9-126">Before converting to a memory-optimized table, the definition for [Sales].[SalesOrderDetail] is as follows:</span></span>  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [LineTotal]  AS (isnull(([UnitPrice]*((1.0)-[UnitPriceDiscount]))*[OrderQty],(0.0))),  
   [rowguid] [uniqueidentifier] ROWGUIDCOL  NOT NULL CONSTRAINT [DF_SalesOrderDetail_rowguid]  DEFAULT (newid()),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
 CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY CLUSTERED   
(  
   [SalesOrderID] ASC,  
   [SalesOrderDetailID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID] FOREIGN KEY([SalesOrderID])  
REFERENCES [Sales].[SalesOrderHeader] ([SalesOrderID])  
ON DELETE CASCADE  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID] FOREIGN KEY([SpecialOfferID], [ProductID])  
REFERENCES [Sales].[SpecialOfferProduct] ([SpecialOfferID], [ProductID])  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_OrderQty] CHECK  (([OrderQty]>(0)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_OrderQty]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPrice] CHECK  (([UnitPrice]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPrice]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount] CHECK  (([UnitPriceDiscount]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount]  
GO  
```  
  
 <span data-ttu-id="e49d9-127">轉換成記憶體優化資料表之後，[Sales] 的定義。[SalesOrderDetail] 如下所示：</span><span class="sxs-lookup"><span data-stu-id="e49d9-127">After converting to a memory-optimized table, the definition for [Sales].[SalesOrderDetail] is as follows:</span></span>  
  
 <span data-ttu-id="e49d9-128">請注意，rowguid 不再是 ROWGUIDCOL，因為不支援此功能 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e49d9-128">Note that rowguid is no longer a ROWGUIDCOL as it is not supported in [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="e49d9-129">已移除資料行。</span><span class="sxs-lookup"><span data-stu-id="e49d9-129">The column has been removed.</span></span> <span data-ttu-id="e49d9-130">此外，LineTotal 是一個計算資料行，而且不在本文的範圍內，因此也已被移除。</span><span class="sxs-lookup"><span data-stu-id="e49d9-130">In addition, LineTotal is a computed column and out of scope for this article, so it also has been removed.</span></span>  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
   CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY NONCLUSTERED   
   (  
      [SalesOrderID] ASC,  
      [SalesOrderDetailID] ASC  
   ),  
   INDEX [AK_SalesOrderDetail_rowguid] NONCLUSTERED HASH ([rowguid]) WITH (BUCKET_COUNT = 1048576),  
   INDEX [IX_SalesOrderDetail_ProductId] NONCLUSTERED ([ProductId] ASC)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
  
GO  
```  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a><span data-ttu-id="e49d9-131">在插入、更新或刪除作業之後檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="e49d9-131">Checking Constraints After an Insert, Update, or Delete Operation</span></span>  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRANSACTION   
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, , @ModifiedDate)   
  
   -- Now handle constraints  
   DECLARE @violations TABLE   
   (   
      ConstraintName sysname,  
      ViolatedValue1 sql_variant,  
      ViolatedValue2 sql_variant  
   )  
  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId AS [Exists] FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID', @SalesOrderId, NULL)  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID', @SpecialOfferId, @ProductId)  
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_OrderQty', @OrderQty, NULL)  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPrice', @UnitPrice, NULL)  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPriceDiscount', @UnitPriceDiscount, NULL)  
  
   -- Return a rowset containing violated constraints. On an item that doesn't violate anything, should return an empty rowset.  
   SELECT ConstraintName, ViolatedValue1, ViolatedValue2 FROM @violations  
   COMMIT TRANSACTION  
END  
```  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a><span data-ttu-id="e49d9-132">在插入、更新或刪除作業之前強制執行條件約束</span><span class="sxs-lookup"><span data-stu-id="e49d9-132">Enforcing Constraints Before an Insert, Update or Delete Operation</span></span>  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRY  
   BEGIN TRANSACTION  
   -- Verify the constraints first.  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      THROW 50547, N'This SalesOrderId does not exist in SalesOrderHeader', 1  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      THROW 50547, N'This combination of SpecialOfferID and ProductID does not exist in SpecialOfferProduct', 1   
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      THROW 50547, N'OrderQty must be greater than zero.', 1  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      THROW 50547, N'UnitPrice cannot be negative.', 1  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      THROW 50547, N'UnitPriceDiscount cannot be negative', 1  
  
   -- All verifications have now passed. Proceed to insert.  
  
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Calculate computed columnn and store it.  
   DECLARE @LineTotal numeric(38, 6)  
   SET @LineTotal = (isnull((@UnitPrice * ((1.0) - @UnitPriceDiscount)) * @OrderQty, (0.0)))  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, @ModifiedDate)  
   COMMIT TRANSACTION  
END TRY  
BEGIN CATCH  
   IF @@TRANCOUNT > 0  
      ROLLBACK TRANSACTION  
      THROW;  
END CATCH  
END  
```  
  
## <a name="see-also"></a><span data-ttu-id="e49d9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e49d9-133">See Also</span></span>  
 [<span data-ttu-id="e49d9-134">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="e49d9-134">Migrating to In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
