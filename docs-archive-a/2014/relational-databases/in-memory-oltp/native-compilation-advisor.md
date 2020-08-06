---
title: 原生編譯 Advisor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: b2182d89489af5da8bc3b85b89484fbbf72e4dfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709425"
---
# <a name="native-compilation-advisor"></a><span data-ttu-id="e249e-102">原生編譯 Advisor</span><span class="sxs-lookup"><span data-stu-id="e249e-102">Native Compilation Advisor</span></span>
  <span data-ttu-id="e249e-103">交易效能報告工具 (參閱[判斷是否應將資料表或預存程式移植到記憶體內部 OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) 會通知您，資料庫中哪些已轉譯的預存程式在移植為使用原生編譯時會有好處。</span><span class="sxs-lookup"><span data-stu-id="e249e-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which interpreted stored procedures in your database will benefit if ported to use native compilation.</span></span> <span data-ttu-id="e249e-104">識別您要匯出使用原生編譯的預存程序之後，即可使用原生編譯 Advisor 協助您將解譯的預存程序移轉到原生編譯。</span><span class="sxs-lookup"><span data-stu-id="e249e-104">After you identify a stored procedure that you would like to port to use native compilation, you can use the native compilation advisor to help you migrate the interpreted stored procedure to native compilation.</span></span> <span data-ttu-id="e249e-105">如需原生編譯的預存程序的詳細資訊，請參閱 [原生編譯的預存程序](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e249e-105">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="e249e-106">開始時，請先連接至執行個體，其中包含解譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="e249e-106">To begin, connect to the instance that contains the interpreted stored procedure.</span></span> <span data-ttu-id="e249e-107">您可以連接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e249e-107">You can connect to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="e249e-108">不過，如果您想要使用 Advisor 執行移轉作業，則必須連接到已啟用 In-Memory OLTP 功能的 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e249e-108">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="e249e-109">如需有關記憶體中 OLTP 需求的詳細資訊，請參閱＜ [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e249e-109">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="e249e-110">如需移轉方法的資訊，請參閱 [In-Memory OLTP - 一般工作負載模式和移轉考量](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e249e-110">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a><span data-ttu-id="e249e-111">使用原生編譯 Advisor 的逐步解說</span><span class="sxs-lookup"><span data-stu-id="e249e-111">Walkthrough Using the Native Compilation Advisor</span></span>  
 <span data-ttu-id="e249e-112">在 [物件總管] 中，以滑鼠右鍵按一下您想要轉換的預存程序，然後選取 [原生編譯 Advisor]。</span><span class="sxs-lookup"><span data-stu-id="e249e-112">In **Object Explorer**, right click the stored procedure you want to convert, and select **Native Compilation Advisor**.</span></span> <span data-ttu-id="e249e-113">隨即顯示 [預存程序原生編譯 Advisor] 的歡迎頁面。</span><span class="sxs-lookup"><span data-stu-id="e249e-113">This will display the welcome page for the **Stored Procedure Native Compilation Advisor**.</span></span> <span data-ttu-id="e249e-114">選取 [下一步] 以繼續操作。</span><span class="sxs-lookup"><span data-stu-id="e249e-114">Click **Next** to continue.</span></span>  
  
### <a name="stored-procedure-validation"></a><span data-ttu-id="e249e-115">預存程序驗證</span><span class="sxs-lookup"><span data-stu-id="e249e-115">Stored Procedure Validation</span></span>  
 <span data-ttu-id="e249e-116">此頁面將會回報預存程序是否使用任何與原生編譯不相容的建構。</span><span class="sxs-lookup"><span data-stu-id="e249e-116">This page will report if the stored procedure uses any constructs that are not compatible with native compilation.</span></span> <span data-ttu-id="e249e-117">您可以按 [下一步] 查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e249e-117">You can click **Next** to see details.</span></span> <span data-ttu-id="e249e-118">如果有與原生編譯不相容的建構，您可以按 [下一步] 查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e249e-118">If there are constructs that are not compatible with native compilation, you can click **Next** to see details.</span></span>  
  
### <a name="stored-procedure-validation-result"></a><span data-ttu-id="e249e-119">預存程序驗證結果</span><span class="sxs-lookup"><span data-stu-id="e249e-119">Stored Procedure Validation Result</span></span>  
 <span data-ttu-id="e249e-120">如果有與原生編譯不相容的建構，[預存程序驗證結果] 頁面會顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e249e-120">If there are constructs that are not compatible with native compilation, the **Stored Procedure Validation Result** page will display details.</span></span> <span data-ttu-id="e249e-121">您可以產生報表 (按一下 [產生報表])、結束 [原生編譯 Advisor]，並更新您的程式碼，使其與原生編譯相容。</span><span class="sxs-lookup"><span data-stu-id="e249e-121">You can generate a report (click **Generate Report**), exit the **Native Compilation Advisor**, and update your code so that it is compatible with native compilation.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="e249e-122">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e249e-122">Code Sample</span></span>  
 <span data-ttu-id="e249e-123">下列範例顯示解譯的預存程序及原生編譯的對等預存程序。</span><span class="sxs-lookup"><span data-stu-id="e249e-123">The following sample shows an interpreted stored procedure and the equivalent stored procedure for native compilation.</span></span> <span data-ttu-id="e249e-124">該範例假設目錄名為 c:\data。</span><span class="sxs-lookup"><span data-stu-id="e249e-124">The sample assumes a directory called c:\data.</span></span>  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="e249e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e249e-125">See Also</span></span>  
 [<span data-ttu-id="e249e-126">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="e249e-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
