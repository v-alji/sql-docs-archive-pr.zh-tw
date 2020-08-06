---
title: 設定平行索引作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index parallel operations [SQL Server]
- processors [SQL Server], parallel index operations
- max degree of parallelism option
- MAXDOP index option, parallel index operations
- parallel index operations [SQL Server]
ms.assetid: 8ec8c71e-5fc1-443a-92da-136ee3fc7f88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8831aadae15af03a05f4ab03cfe514e54566df1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585385"
---
# <a name="configure-parallel-index-operations"></a><span data-ttu-id="518b7-102">設定平行索引作業</span><span class="sxs-lookup"><span data-stu-id="518b7-102">Configure Parallel Index Operations</span></span>
  <span data-ttu-id="518b7-103">本主題定義平行處理原則的最大程度，並說明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]修改此設定。</span><span class="sxs-lookup"><span data-stu-id="518b7-103">This topic defines max degree of parallelism and explains how to modify this setting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="518b7-104">在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 或更新版本的多處理器電腦上，索引陳述式可能會如同其他查詢般，使用多個處理器來執行與索引陳述式相關聯的掃描、排序和索引作業。</span><span class="sxs-lookup"><span data-stu-id="518b7-104">On multiprocessor computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise or higher, index statements may use multiple processors to perform the scan, sort, and index operations associated with the index statement just like other queries do.</span></span> <span data-ttu-id="518b7-105">執行單一索引陳述式所用的處理器數目，取決於 [平行處理原則的最大程度](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) 組態選項、目前的工作負載以及索引統計資料。</span><span class="sxs-lookup"><span data-stu-id="518b7-105">The number of processors used to run a single index statement is determined by the [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) configuration option, the current workload, and the index statistics.</span></span> <span data-ttu-id="518b7-106">max degree of parallelism 選項會決定用於執行平行計畫的最大處理器數目。</span><span class="sxs-lookup"><span data-stu-id="518b7-106">The max degree of parallelism option determines the maximum number of processors to use in parallel plan execution.</span></span> <span data-ttu-id="518b7-107">如果 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 偵測到系統忙碌中，在陳述式執行開始之前，會先自動降低索引作業之平行處理原則的程度。</span><span class="sxs-lookup"><span data-stu-id="518b7-107">If the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] detects that the system is busy, the degree of parallelism of the index operation is automatically reduced before statement execution starts.</span></span> <span data-ttu-id="518b7-108">如果非資料分割索引的前端索引鍵資料行具有有限的相異值數目，或者每個相異值的頻率具有大幅差異， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 也可能會降低平行處理原則的程度。</span><span class="sxs-lookup"><span data-stu-id="518b7-108">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can also reduce the degree of parallelism if the leading key column of a non-partitioned index has a limited number of distinct values or the frequency of each distinct value varies significantly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="518b7-109">並非所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本都可使用平行索引作業。</span><span class="sxs-lookup"><span data-stu-id="518b7-109">Parallel index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="518b7-110">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="518b7-110">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="518b7-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="518b7-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="518b7-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="518b7-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="518b7-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="518b7-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="518b7-114">安全性</span><span class="sxs-lookup"><span data-stu-id="518b7-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="518b7-115">**若要設定平行處理原則的最大程度，使用：**</span><span class="sxs-lookup"><span data-stu-id="518b7-115">**To set the max degree of parallelism, using:**</span></span>  
  
     [<span data-ttu-id="518b7-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="518b7-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="518b7-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="518b7-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="518b7-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="518b7-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="518b7-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="518b7-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="518b7-120">查詢最佳化工具所使用的處理器數目通常可以提供最佳的效能。</span><span class="sxs-lookup"><span data-stu-id="518b7-120">The number of processors that are used by the query optimizer typically provides optimal performance.</span></span> <span data-ttu-id="518b7-121">然而，諸如建立、重建、卸除非常大的索引都需要大量的資源，並可能在索引作業期間造成其他應用程式和資料庫作業的資源不足。</span><span class="sxs-lookup"><span data-stu-id="518b7-121">However, operations such as creating, rebuilding, or dropping very large indexes are resource intensive and can cause insufficient resources for other applications and database operations for the duration of the index operation.</span></span> <span data-ttu-id="518b7-122">當發生此問題時，您可以限制索引作業要使用的處理器數目，藉以手動設定執行索引陳述式要使用的最大處理器數目。</span><span class="sxs-lookup"><span data-stu-id="518b7-122">When this problem occurs, you can manually configure the maximum number of processors that are used to run the index statement by limiting the number of processors to use for the index operation.</span></span>  
  
-   <span data-ttu-id="518b7-123">MAXDOP 索引選項只會針對指定此選項的查詢來覆寫 max degree of parallelism 組態選項。</span><span class="sxs-lookup"><span data-stu-id="518b7-123">The MAXDOP index option overrides the max degree of parallelism configuration option only for the query specifying this option.</span></span> <span data-ttu-id="518b7-124">下表列出可以使用 max degree of parallelism 組態選項及 MAXDOP 索引選項指定的有效整數值。</span><span class="sxs-lookup"><span data-stu-id="518b7-124">The following table lists the valid integer values that can be specified with the max degree of parallelism configuration option and the MAXDOP index option.</span></span>  
  
    |<span data-ttu-id="518b7-125">值</span><span class="sxs-lookup"><span data-stu-id="518b7-125">Value</span></span>|<span data-ttu-id="518b7-126">描述</span><span class="sxs-lookup"><span data-stu-id="518b7-126">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="518b7-127">0</span><span class="sxs-lookup"><span data-stu-id="518b7-127">0</span></span>|<span data-ttu-id="518b7-128">指定伺服器會根據目前的系統工作負載來決定所使用的 CPU 數目。</span><span class="sxs-lookup"><span data-stu-id="518b7-128">Specifies that the server determines the number of CPUs that are used, depending on the current system workload.</span></span> <span data-ttu-id="518b7-129">這是預設值且為建議的設定。</span><span class="sxs-lookup"><span data-stu-id="518b7-129">This is the default value and recommended setting.</span></span>|  
    |<span data-ttu-id="518b7-130">1</span><span class="sxs-lookup"><span data-stu-id="518b7-130">1</span></span>|<span data-ttu-id="518b7-131">隱藏平行計畫的產生。</span><span class="sxs-lookup"><span data-stu-id="518b7-131">Suppresses parallel plan generation.</span></span> <span data-ttu-id="518b7-132">作業必須循序執行。</span><span class="sxs-lookup"><span data-stu-id="518b7-132">The operation will be executed serially.</span></span>|  
    |<span data-ttu-id="518b7-133">2-64</span><span class="sxs-lookup"><span data-stu-id="518b7-133">2-64</span></span>|<span data-ttu-id="518b7-134">將處理器的數目限制成指定的值。</span><span class="sxs-lookup"><span data-stu-id="518b7-134">Limits the number of processors to the specified value.</span></span> <span data-ttu-id="518b7-135">視目前的工作負載而定來使用較少的處理器。</span><span class="sxs-lookup"><span data-stu-id="518b7-135">Fewer processors may be used depending on the current workload.</span></span> <span data-ttu-id="518b7-136">如果指定的值大於可用的 CPU 個數，就會使用實際可用的 CPU 個數。</span><span class="sxs-lookup"><span data-stu-id="518b7-136">If a value larger than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>|  
  
-   <span data-ttu-id="518b7-137">平行索引執行與 MAXDOP 索引選項適用於下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="518b7-137">Parallel index execution and the MAXDOP index option apply to the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    -   <span data-ttu-id="518b7-138">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="518b7-138">CREATE INDEX</span></span>  
  
    -   <span data-ttu-id="518b7-139">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="518b7-139">ALTER INDEX REBUILD</span></span>  
  
    -   <span data-ttu-id="518b7-140">DROP INDEX (僅適用於叢集索引。)</span><span class="sxs-lookup"><span data-stu-id="518b7-140">DROP INDEX (This applies to clustered indexes only.)</span></span>  
  
    -   <span data-ttu-id="518b7-141">ALTER TABLE ADD (索引) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="518b7-141">ALTER TABLE ADD (index) CONSTRAINT</span></span>  
  
    -   <span data-ttu-id="518b7-142">ALTER TABLE DROP (叢集索引) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="518b7-142">ALTER TABLE DROP (clustered index) CONSTRAINT</span></span>  
  
-   <span data-ttu-id="518b7-143">在 ALTER INDEX REORGANIZE 陳述式中無法指定 MAXDOP 索引選項。</span><span class="sxs-lookup"><span data-stu-id="518b7-143">The MAXDOP index option cannot be specified in the ALTER INDEX REORGANIZE statement.</span></span>  
  
-   <span data-ttu-id="518b7-144">如果查詢最佳化工具將平行處理原則的程度套用至建立作業，則需要排序的資料分割索引作業可能需要更多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="518b7-144">Memory requirements for partitioned index operations that require sorting can be greater if the query optimizer applies degrees of parallelism to the build operation.</span></span> <span data-ttu-id="518b7-145">平行處理原則的程度愈高，所需的記憶體就愈大。</span><span class="sxs-lookup"><span data-stu-id="518b7-145">The higher the degrees of parallelism, the greater the memory requirement is.</span></span> <span data-ttu-id="518b7-146">如需詳細資訊，請參閱＜ [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="518b7-146">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="518b7-147">Security</span><span class="sxs-lookup"><span data-stu-id="518b7-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="518b7-148">權限</span><span class="sxs-lookup"><span data-stu-id="518b7-148">Permissions</span></span>  
 <span data-ttu-id="518b7-149">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="518b7-149">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="518b7-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="518b7-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-index"></a><span data-ttu-id="518b7-151">若要在索引上設定平行處理原則的最大程度</span><span class="sxs-lookup"><span data-stu-id="518b7-151">To set max degree of parallelism on an index</span></span>  
  
1.  <span data-ttu-id="518b7-152">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要設定索引之平行處理原則最大程度的資料表。</span><span class="sxs-lookup"><span data-stu-id="518b7-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to set max degree of parallelism for an index.</span></span>  
  
2.  <span data-ttu-id="518b7-153">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="518b7-153">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="518b7-154">按一下加號展開包含您要設定索引之平行處理原則最大程度的資料表。</span><span class="sxs-lookup"><span data-stu-id="518b7-154">Click the plus sign to expand the table on which you want to set max degree of parallelism for an index.</span></span>  
  
4.  <span data-ttu-id="518b7-155">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="518b7-155">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="518b7-156">以滑鼠右鍵按一下要設定平行處理原則最大程度的索引，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="518b7-156">Right-click the index for which you want to set the max degree of parallelism and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="518b7-157">在 **[選取頁面]** 底下，選取 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="518b7-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="518b7-158">選取 **[平行處理原則的最大程度]** ，然後輸入介於 1 和 64 之間的一些值。</span><span class="sxs-lookup"><span data-stu-id="518b7-158">Select **Maximum degree of parallelism**, and then enter some value between 1 and 64.</span></span>  
  
8.  <span data-ttu-id="518b7-159">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="518b7-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="518b7-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="518b7-160">Using Transact-SQL</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-existing-index"></a><span data-ttu-id="518b7-161">若要在現有索引上設定平行處理原則的最大程度</span><span class="sxs-lookup"><span data-stu-id="518b7-161">To set max degree of parallelism on an existing index</span></span>  
  
1.  <span data-ttu-id="518b7-162">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="518b7-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="518b7-163">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="518b7-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="518b7-164">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="518b7-164">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Alters the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table so that, if the server has eight or more processors, the Database Engine will limit the execution of the index operation to eight or fewer processors.  
    */  
    ALTER INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor  
    REBUILD WITH (MAXDOP=8);   
    GO  
    ```  
  
 <span data-ttu-id="518b7-165">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="518b7-165">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
#### <a name="set-max-degree-of-parallelism-on-a-new-index"></a><span data-ttu-id="518b7-166">在新索引上設定平行處理原則的最大程度</span><span class="sxs-lookup"><span data-stu-id="518b7-166">Set max degree of parallelism on a new index</span></span>  
  
1.  <span data-ttu-id="518b7-167">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="518b7-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="518b7-168">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="518b7-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="518b7-169">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="518b7-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE INDEX IX_ProductVendor_NewVendorID   
    ON Purchasing.ProductVendor (BusinessEntityID)  
    WITH (MAXDOP=8);  
    GO  
    ```  
  
 <span data-ttu-id="518b7-170">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="518b7-170">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
