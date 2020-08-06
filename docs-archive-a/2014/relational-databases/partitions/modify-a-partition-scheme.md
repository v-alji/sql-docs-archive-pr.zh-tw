---
title: 修改資料分割配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 515de63f-dfc5-434d-9adb-f3b5992f745a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d57984228e23143d2061df6bf447f978f9bd3c46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597792"
---
# <a name="modify-a-partition-scheme"></a><span data-ttu-id="8f90a-102">修改資料分割配置</span><span class="sxs-lookup"><span data-stu-id="8f90a-102">Modify a Partition Scheme</span></span>
  <span data-ttu-id="8f90a-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來指定檔案群組以保存下一個要加入資料分割資料表的資料分割，藉此在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="8f90a-103">You can modify a partition scheme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by designating a filegroup to hold the next partition that is added to a partitioned table using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8f90a-104">作法是，將 NEXT USED 屬性指派給檔案群組。</span><span class="sxs-lookup"><span data-stu-id="8f90a-104">You do this by assigning the NEXT USED property to a filegroup.</span></span> <span data-ttu-id="8f90a-105">NEXT USED 屬性可以指派給空的檔案群組或已保存資料分割的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="8f90a-105">You can assign the NEXT USED property to an empty filegroup or to one that already holds a partition.</span></span> <span data-ttu-id="8f90a-106">換句話說，檔案群組可以保存一個以上的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8f90a-106">In other words, a filegroup can hold more than one partition.</span></span>  
  
 <span data-ttu-id="8f90a-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8f90a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8f90a-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8f90a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8f90a-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="8f90a-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8f90a-110">安全性</span><span class="sxs-lookup"><span data-stu-id="8f90a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8f90a-111">**使用下列方法建立分割區資料表或索引：**</span><span class="sxs-lookup"><span data-stu-id="8f90a-111">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="8f90a-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8f90a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8f90a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8f90a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8f90a-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="8f90a-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8f90a-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="8f90a-115">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8f90a-116">只要是 ALTER PARTITION SCHEME 影響所及的檔案群組都必須在線上。</span><span class="sxs-lookup"><span data-stu-id="8f90a-116">Any filegroup affected by ALTER PARTITION SCHEME must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8f90a-117">Security</span><span class="sxs-lookup"><span data-stu-id="8f90a-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8f90a-118">權限</span><span class="sxs-lookup"><span data-stu-id="8f90a-118">Permissions</span></span>  
 <span data-ttu-id="8f90a-119">您可以使用下列權限來執行 ALTER PARTITION SCHEME：</span><span class="sxs-lookup"><span data-stu-id="8f90a-119">The following permissions can be used to execute ALTER PARTITION SCHEME:</span></span>  
  
-   <span data-ttu-id="8f90a-120">ALTER ANY DATASPACE 權限。</span><span class="sxs-lookup"><span data-stu-id="8f90a-120">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="8f90a-121">這個權限預設會授與 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_ddladmin** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="8f90a-121">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="8f90a-122">建立資料分割結構描述之資料庫的 CONTROL 或 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="8f90a-122">CONTROL or ALTER permission on the database in which the partition scheme was created.</span></span>  
  
-   <span data-ttu-id="8f90a-123">在建立資料分割結構描述的資料庫中，其伺服器的 CONTROL SERVER 或 ALTER ANY DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="8f90a-123">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition scheme was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8f90a-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8f90a-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8f90a-125">**若要修改資料分割配置：**</span><span class="sxs-lookup"><span data-stu-id="8f90a-125">**To modify a partition scheme:**</span></span>  
  
 <span data-ttu-id="8f90a-126">您無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來執行這項特定動作。</span><span class="sxs-lookup"><span data-stu-id="8f90a-126">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="8f90a-127">若要修改資料分割配置，您必須先刪除此配置，然後再使用 [建立資料分割精靈] 來建立具有所需屬性的新配置。</span><span class="sxs-lookup"><span data-stu-id="8f90a-127">In order to modify a partition scheme, you must first delete the scheme and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="8f90a-128">如需詳細資訊，請參閱**create 資料分割資料表和索引**底下的[使用 SQL Server Management Studio 建立資料分割資料表和索引](create-partitioned-tables-and-indexes.md#SSMSProcedure)。</span><span class="sxs-lookup"><span data-stu-id="8f90a-128">For more information, see [Create Partitioned Tables and Indexes Using SQL Server Management Studio](create-partitioned-tables-and-indexes.md#SSMSProcedure) under **Create Partitioned Tables and Indexes**.</span></span>  
  
#### <a name="to-delete-a-partition-scheme"></a><span data-ttu-id="8f90a-129">若要刪除資料分割配置</span><span class="sxs-lookup"><span data-stu-id="8f90a-129">To delete a partition scheme</span></span>  
  
1.  <span data-ttu-id="8f90a-130">按一下加號，展開您想要在其中刪除資料分割配置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f90a-130">Click the plus sign to expand the database where you want to delete the partition scheme.</span></span>  
  
2.  <span data-ttu-id="8f90a-131">按一下加號展開 **[儲存體]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f90a-131">Click the plus sign to expand the **Storage** folder.</span></span>  
  
3.  <span data-ttu-id="8f90a-132">按一下加號展開 **[資料分割配置]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f90a-132">Click the plus sign to expand the **Partition Schemes** folder.</span></span>  
  
4.  <span data-ttu-id="8f90a-133">以滑鼠右鍵按一下您想要刪除的資料分割配置，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="8f90a-133">Right-click the partition scheme you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="8f90a-134">在 **[刪除物件]** 對話方塊中，確定已選取正確的資料分割配置，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8f90a-134">In the **Delete Object** dialog box, ensure that the correct partition scheme is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8f90a-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8f90a-135">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-partition-scheme"></a><span data-ttu-id="8f90a-136">若要修改資料分割配置</span><span class="sxs-lookup"><span data-stu-id="8f90a-136">To modify a partition scheme</span></span>  
  
1.  <span data-ttu-id="8f90a-137">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f90a-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8f90a-138">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8f90a-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8f90a-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8f90a-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- add five new filegroups to the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test1fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test4fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test5fg;  
    GO  
    -- if the "myRangePF1" partition function and the "myRangePS1" partition scheme exist,  
    -- drop them from the AdventureWorks2012 database  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
    DROP PARTITION FUNCTION myRangePF1;  
    GO  
    IF EXISTS (SELECT * FROM sys.partition_schemes  
        WHERE name = 'myRangePS1')  
    DROP PARTITION SCHEME myRangePS1;  
    GO  
    -- create the new partition function "myRangePF1" with four partition groups  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    -- create the new partition scheme "myRangePS1"that will use   
    -- the "myRangePF1" partition function with five file groups.  
    -- The last filegroup, "test5fg," will be kept empty but marked  
    -- as the next used filegroup in the partition scheme.  
    CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg, test5fg);  
    GO  
    --Split "myRangePS1" between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    GO  
    -- Allow the "myRangePS1" partition scheme to use the filegroup "test5fg"  
    -- for the partition with boundary_values of 100 and 500  
    ALTER PARTITION SCHEME myRangePS1  
    NEXT USED test5fg;  
    GO  
    ```  
  
 <span data-ttu-id="8f90a-140">如需詳細資訊，請參閱 [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-scheme-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8f90a-140">For more information, see [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-scheme-transact-sql).</span></span>  
  
  
