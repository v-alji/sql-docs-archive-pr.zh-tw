---
title: 建立資料表 (教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating tables
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c772f2527bd5ddb8a6759cbaa72d8aed9277f5cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597483"
---
# <a name="creating-a-table-tutorial"></a><span data-ttu-id="9690d-102">建立資料表 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="9690d-102">Creating a Table (Tutorial)</span></span>
  <span data-ttu-id="9690d-103">若要建立資料表，您必須提供資料表的名稱，以及資料表中各資料行的名稱和資料類型，</span><span class="sxs-lookup"><span data-stu-id="9690d-103">To create a table, you must provide a name for the table, and the names and data types of each column in the table.</span></span> <span data-ttu-id="9690d-104">最好也能指出各資料行中是否允許有 Null 值。</span><span class="sxs-lookup"><span data-stu-id="9690d-104">It is also a good practice to indicate whether null values are allowed in each column.</span></span>  
  
 <span data-ttu-id="9690d-105">大多數資料表都具有由資料表中一或多個資料行組成的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9690d-105">Most tables have a primary key, made up of one or more columns of the table.</span></span> <span data-ttu-id="9690d-106">主索引鍵一定是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9690d-106">A primary key is always unique.</span></span> <span data-ttu-id="9690d-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] 會強制限制資料表中的所有主索引鍵值都不能重複。</span><span class="sxs-lookup"><span data-stu-id="9690d-107">The [!INCLUDE[ssDE](../includes/ssde-md.md)] will enforce the restriction that any primary key value cannot be repeated in the table.</span></span>  
  
 <span data-ttu-id="9690d-108">如需資料類型以及各資料類型之描述連結的清單，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9690d-108">For a list of data types and links for a description of each, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9690d-109">[!INCLUDE[ssDE](../includes/ssde-md.md)] 可以安裝為區分大小寫或不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9690d-109">The [!INCLUDE[ssDE](../includes/ssde-md.md)] can be installed as case sensitive or non-case sensitive.</span></span> <span data-ttu-id="9690d-110">如果將 [!INCLUDE[ssDE](../includes/ssde-md.md)] 安裝為區分大小寫，則物件名稱的大小寫一定要完全相同。</span><span class="sxs-lookup"><span data-stu-id="9690d-110">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as case sensitive, object names must always have the same case.</span></span> <span data-ttu-id="9690d-111">例如，名稱為 OrderData 的資料表與名稱為 ORDERDATA 的資料表會代表不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="9690d-111">For example, a table named OrderData is a different table from a table named ORDERDATA.</span></span> <span data-ttu-id="9690d-112">如果將 [!INCLUDE[ssDE](../includes/ssde-md.md)] 安裝為不區分大小寫，則會將這兩個資料表名稱視為代表同一個資料表，而且該名稱只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="9690d-112">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as non-case sensitive, those two table names are considered to be the same table, and that name can only be used one time.</span></span>  
  
### <a name="to-create-a-database-to-contain-the-new-table"></a><span data-ttu-id="9690d-113">若要建立包含新資料表的資料庫</span><span class="sxs-lookup"><span data-stu-id="9690d-113">To create a database to contain the new table</span></span>  
  
-   <span data-ttu-id="9690d-114">將下列程式碼輸入 [查詢編輯器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="9690d-114">Enter the following code into a Query Editor window.</span></span>  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a><span data-ttu-id="9690d-115">將查詢編輯器連接切換到 TestData 資料庫</span><span class="sxs-lookup"><span data-stu-id="9690d-115">Switch the Query Editor connection to the TestData database</span></span>  
  
-   <span data-ttu-id="9690d-116">在 [查詢編輯器] 視窗中，輸入並執行下列程式碼，將連接變更為 `TestData` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9690d-116">In a Query Editor window, type and execute the following code to change your connection to the `TestData` database.</span></span>  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### <a name="to-create-a-table"></a><span data-ttu-id="9690d-117">若要建立資料表</span><span class="sxs-lookup"><span data-stu-id="9690d-117">To create a table</span></span>  
  
-   <span data-ttu-id="9690d-118">在 [查詢編輯器] 視窗中，輸入並執行下列程式碼，建立名稱為 `Products`的簡單資料表。</span><span class="sxs-lookup"><span data-stu-id="9690d-118">In a Query Editor window, type and execute the following code to create a simple table named `Products`.</span></span> <span data-ttu-id="9690d-119">此資料表中的資料行名稱分別為 `ProductID`、 `ProductName`、 `Price`和 `ProductDescription`。</span><span class="sxs-lookup"><span data-stu-id="9690d-119">The columns in the table are named `ProductID`, `ProductName`, `Price`, and `ProductDescription`.</span></span> <span data-ttu-id="9690d-120">`ProductID` 資料行是此資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9690d-120">The `ProductID` column is the primary key of the table.</span></span> <span data-ttu-id="9690d-121">`int`、 `varchar(25)`、 `money`和 `text` 全部都是資料類型。</span><span class="sxs-lookup"><span data-stu-id="9690d-121">`int`, `varchar(25)`, `money`, and `text` are all data types.</span></span> <span data-ttu-id="9690d-122">在插入或變更資料列時，只有 `Price` 和 `ProductionDescription` 資料行可以不含任何資料。</span><span class="sxs-lookup"><span data-stu-id="9690d-122">Only the `Price` and `ProductionDescription` columns can have no data when a row is inserted or changed.</span></span> <span data-ttu-id="9690d-123">這個陳述式包含一個選擇性的元素 (`dbo.`)，稱為「結構描述」。</span><span class="sxs-lookup"><span data-stu-id="9690d-123">This statement contains an optional element (`dbo.`) called a schema.</span></span> <span data-ttu-id="9690d-124">結構描述就是擁有資料表的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="9690d-124">The schema is the database object that owns the table.</span></span> <span data-ttu-id="9690d-125">如果您是系統管理員，則 `dbo` 是預設的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9690d-125">If you are an administrator, `dbo` is the default schema.</span></span> <span data-ttu-id="9690d-126">`dbo` 代表資料庫擁有者。</span><span class="sxs-lookup"><span data-stu-id="9690d-126">`dbo` stands for database owner.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9690d-127">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="9690d-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9690d-128">在資料表中插入及更新資料 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9690d-128">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](../t-sql/lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="9690d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9690d-129">See Also</span></span>  
 [<span data-ttu-id="9690d-130">CREATE TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9690d-130">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
