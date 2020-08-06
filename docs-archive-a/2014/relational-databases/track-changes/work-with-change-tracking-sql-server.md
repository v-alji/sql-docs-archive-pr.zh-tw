---
title: 使用變更追蹤 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], making changes
- change tracking [SQL Server], troubleshooting
- updating data [SQL Server]
- troubleshooting [SQL Server], change tracking
- data changes [SQL Server]
- tracking data changes [SQL Server]
- data [SQL Server], changing
- change tracking [SQL Server], data restore
- change tracking [SQL Server], ensuring consistent results
- change tracking [SQL Server], handling changes
ms.assetid: 5aec22ce-ae6f-4048-8a45-59ed05f04dc5
author: rothja
ms.author: jroth
ms.openlocfilehash: bdb8205a789894caf8c8e2d3c3f491751757bab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606157"
---
# <a name="work-with-change-tracking-sql-server"></a><span data-ttu-id="526ad-102">使用變更追蹤 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="526ad-102">Work with Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="526ad-103">使用變更追蹤的應用程式必須能夠取得追蹤變更、將這些變更套用至另一個資料存放區，以及更新來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="526ad-103">Applications that use change tracking must be able to obtain tracked changes, apply these changes to another data store, and update the source database.</span></span> <span data-ttu-id="526ad-104">此主題描述如何執行這些工作，以及在進行容錯移轉而且必須從備份還原資料庫時，變更追蹤所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="526ad-104">This topic describes how to perform these tasks, and also the role change tracking plays when a failover occurs and a database must be restored from a backup.</span></span>  
  
##  <a name="obtain-changes-by-using-change-tracking-functions"></a><a name="Obtain"></a> <span data-ttu-id="526ad-105">使用變更追蹤函數來取得變更</span><span class="sxs-lookup"><span data-stu-id="526ad-105">Obtain Changes by Using Change Tracking Functions</span></span>  
 <span data-ttu-id="526ad-106">描述如何使用變更追蹤函數來取得變更以及對資料庫所做變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-106">Describes how to use the change tracking functions to obtain changes and information about the changes that were made to a database.</span></span>  
  
### <a name="about-the-change-tracking-functions"></a><span data-ttu-id="526ad-107">關於變更追蹤函數</span><span class="sxs-lookup"><span data-stu-id="526ad-107">About the Change Tracking Functions</span></span>  
 <span data-ttu-id="526ad-108">應用程式可以使用下列函數來取得在資料庫中所做的變更和這些變更的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="526ad-108">Applications can use the following functions to obtain the changes that are made in a database and information about the changes:</span></span>  
  
 <span data-ttu-id="526ad-109">CHANGETABLE(CHANGES ...) 函式</span><span class="sxs-lookup"><span data-stu-id="526ad-109">CHANGETABLE(CHANGES ...) function</span></span>  
 <span data-ttu-id="526ad-110">這個資料列集函數是用於查詢是否有變更資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-110">This rowset function is used to query for change information.</span></span> <span data-ttu-id="526ad-111">此函數會查詢儲存在內部變更追蹤資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-111">The function queries the data stored in the internal change tracking tables.</span></span> <span data-ttu-id="526ad-112">此函數會傳回結果集，其中包含已變更之資料列的主索引鍵，以及其他變更資訊，例如作業、更新的資料行及此資料列的版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-112">The function returns a results set that contains the primary keys of rows that have changed together with other change information such as the operation, columns updated and version for the row.</span></span>  
  
 <span data-ttu-id="526ad-113">CHANGETABLE(CHANGES ...) 會將上一次同步處理版本當做引數。</span><span class="sxs-lookup"><span data-stu-id="526ad-113">CHANGETABLE(CHANGES ...) takes a last synchronization version as an argument.</span></span> <span data-ttu-id="526ad-114">上一次同步處理版本是使用 `@last_synchronization_version` 變數來取得。</span><span class="sxs-lookup"><span data-stu-id="526ad-114">The last sychronization version is obtained using the `@last_synchronization_version` variable.</span></span> <span data-ttu-id="526ad-115">上一次同步處理版本的語意如下：</span><span class="sxs-lookup"><span data-stu-id="526ad-115">The semantics of the last synchronization version are as follows:</span></span>  
  
-   <span data-ttu-id="526ad-116">呼叫的用戶端已取得變更並了解到上一次同步處理版本為止的所有變更 (包括此版本)。</span><span class="sxs-lookup"><span data-stu-id="526ad-116">The calling client has obtained changes and knows about all changes up to and including the last synchronization version.</span></span>  
  
-   <span data-ttu-id="526ad-117">CHANGETABLE(CHANGES ...) 因此會傳回上一次同步處理版本之後發生的所有變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-117">CHANGETABLE(CHANGES ...) will therefore return all changes that have occurred after the last synchronization version.</span></span>  
  
     <span data-ttu-id="526ad-118">下圖將說明 CHANGETABLE(CHANGES ...) 如何用於取得變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-118">The following illustration shows how CHANGETABLE(CHANGES ...) is used to obtain changes.</span></span>  
  
     <span data-ttu-id="526ad-119">![變更追蹤查詢輸出的範例](../../database-engine/media/queryoutput.gif "變更追蹤查詢輸出的範例")</span><span class="sxs-lookup"><span data-stu-id="526ad-119">![Example of change tracking query output](../../database-engine/media/queryoutput.gif "Example of change tracking query output")</span></span>  
  
 <span data-ttu-id="526ad-120">CHANGE_TRACKING_CURRENT_VERSION() 函數</span><span class="sxs-lookup"><span data-stu-id="526ad-120">CHANGE_TRACKING_CURRENT_VERSION() function</span></span>  
 <span data-ttu-id="526ad-121">這是用於取得下一次查詢變更時將使用的目前版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-121">Is used to obtain the current version that will be used the next time when querying changes.</span></span> <span data-ttu-id="526ad-122">此版本代表上一次認可的交易版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-122">This version represents the version of the last committed transaction.</span></span>  
  
 <span data-ttu-id="526ad-123">CHANGE_TRACKING_MIN_VALID_VERSION() 函數</span><span class="sxs-lookup"><span data-stu-id="526ad-123">CHANGE_TRACKING_MIN_VALID_VERSION()function</span></span>  
 <span data-ttu-id="526ad-124">這是用於取得用戶端可以擁有，並仍然可從 CHANGETABLE() 取得有效結果的最小有效版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-124">Is used to obtain the minimum valid version that a client can have and still obtain valid results from CHANGETABLE().</span></span> <span data-ttu-id="526ad-125">用戶端應該針對此函數所傳回的值，檢查上一次同步處理版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-125">The client should check the last synchronization version against the value thatis returned by this function.</span></span> <span data-ttu-id="526ad-126">如果上一次同步處理版本小於此函數所傳回的版本，用戶端將無法從 CHANGETABLE() 取得有效結果，而且必須重新初始化。</span><span class="sxs-lookup"><span data-stu-id="526ad-126">If the last synchronization version is less than the version returned by this function, the client will be unable to obtain valid results from CHANGETABLE() and will have to reinitialize.</span></span>  
  
### <a name="obtaining-initial-data"></a><span data-ttu-id="526ad-127">取得初始資料</span><span class="sxs-lookup"><span data-stu-id="526ad-127">Obtaining Initial Data</span></span>  
 <span data-ttu-id="526ad-128">在應用程式首次取得變更之前，應用程式必須先傳送查詢，以便取得初始資料和同步處理版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-128">Before an application can obtain changes for the first time, the application must send a query to obtain the initial data and the synchronization version.</span></span> <span data-ttu-id="526ad-129">應用程式必須直接從資料表中取得適當的資料，然後使用 CHANGE_TRACKING_CURRENT_VERSION() 來取得初始版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-129">The application must obtain the appropriate data directly from the table, and then use CHANGE_TRACKING_CURRENT_VERSION() to obtain the initial version.</span></span> <span data-ttu-id="526ad-130">這個版本將在首次取得變更時傳遞給 CHANGETABLE(CHANGES ...)。</span><span class="sxs-lookup"><span data-stu-id="526ad-130">This version will be passed to CHANGETABLE(CHANGES ...) the first time that changes are obtained.</span></span>  
  
 <span data-ttu-id="526ad-131">下列範例將說明如何取得初始同步處理版本和初始資料集。</span><span class="sxs-lookup"><span data-stu-id="526ad-131">The following example shows how to obtain the initial synchronization version and the initial data set.</span></span>  
  
```sql  
    -- Obtain the current synchronization version. This will be used next time that changes are obtained.  
    SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
    -- Obtain initial data set.  
    SELECT  
        P.ProductID, P.Name, P.ListPrice  
    FROM  
        SalesLT.Product AS P  
```  
  
### <a name="using-the-change-tracking-functions-to-obtain-changes"></a><span data-ttu-id="526ad-132">使用變更追蹤函數來取得變更</span><span class="sxs-lookup"><span data-stu-id="526ad-132">Using the Change Tracking Functions to Obtain Changes</span></span>  
 <span data-ttu-id="526ad-133">若要取得資料表的變更資料列和這些變更的相關資訊，請使用 CHANGETABLE(CHANGES...)。例如，下列查詢會取得 `SalesLT.Product` 資料表的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-133">To obtain the changed rows for a table and information about the changes, use CHANGETABLE(CHANGES...). For example, the following query obtains changes for the `SalesLT.Product` table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, CT.SYS_CHANGE_OPERATION,  
    CT.SYS_CHANGE_COLUMNS, CT.SYS_CHANGE_CONTEXT  
FROM  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
  
```  
  
 <span data-ttu-id="526ad-134">一般而言，用戶端會想要取得資料列的最新資料，而非只有該資料列的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="526ad-134">Usually, a client will want to obtain the latest data for a row instead of only the primary keys for the row.</span></span> <span data-ttu-id="526ad-135">因此，應用程式會讓 CHANGETABLE(CHANGES ...) 的結果與使用者資料表中的資料聯結。</span><span class="sxs-lookup"><span data-stu-id="526ad-135">Therefore, an application would join the results from CHANGETABLE(CHANGES ...) with the data in the user table.</span></span> <span data-ttu-id="526ad-136">例如，下列查詢會與 `SalesLT.Product` 資料表聯結，以便取得 `Name` 和 `ListPrice` 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="526ad-136">For example, the following query joins with the `SalesLT.Product` table to obtain the values for the `Name` and `ListPrice` columns.</span></span> <span data-ttu-id="526ad-137">請注意 `OUTER JOIN`的用法。</span><span class="sxs-lookup"><span data-stu-id="526ad-137">Note the use of `OUTER JOIN`.</span></span> <span data-ttu-id="526ad-138">這是確保系統會針對已經從使用者資料表中刪除的這些資料列傳回變更資訊的必要條件。</span><span class="sxs-lookup"><span data-stu-id="526ad-138">This is required to make sure that the change information is returned for those rows that have been deleted from the user table.</span></span>  
  
```sql  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
 <span data-ttu-id="526ad-139">若要取得可在下一次變更列舉中使用的版本，請使用 CHANGE_TRACKING_CURRENT_VERSION()，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="526ad-139">To obtain the version for use in the next change enumeration, use CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION()  
```  
  
 <span data-ttu-id="526ad-140">當應用程式取得變更時，它必須同時使用 CHANGETABLE(CHANGES...) 和 CHANGE_TRACKING_CURRENT_VERSION()，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="526ad-140">When an application obtains changes, it must use both CHANGETABLE(CHANGES...) and CHANGE_TRACKING_CURRENT_VERSION(), as shown in the following example.</span></span>  
  
```sql  
-- Obtain the current synchronization version. This will be used the next time CHANGETABLE(CHANGES...) is called.  
SET @synchronization_version = CHANGE_TRACKING_CURRENT_VERSION();  
  
-- Obtain incremental changes by using the synchronization version obtained the last time the data was synchronized.  
SELECT  
    CT.ProductID, P.Name, P.ListPrice,  
    CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
    CT.SYS_CHANGE_CONTEXT  
FROM  
    SalesLT.Product AS P  
RIGHT OUTER JOIN  
    CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
    P.ProductID = CT.ProductID  
```  
  
### <a name="version-numbers"></a><span data-ttu-id="526ad-141">版本號碼</span><span class="sxs-lookup"><span data-stu-id="526ad-141">Version Numbers</span></span>  
 <span data-ttu-id="526ad-142">啟用變更追蹤的資料庫所具有的版本計數器，會隨著變更追蹤資料表所做的變更而增加。</span><span class="sxs-lookup"><span data-stu-id="526ad-142">A database that has change tracking enabled has a version counter that increases as changes are made to change tracked tables.</span></span> <span data-ttu-id="526ad-143">每一個變更的資料列都有與它相關聯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="526ad-143">Each changed row has a version number that is associated with it.</span></span> <span data-ttu-id="526ad-144">當某個要求傳送至應用程式，以便查詢是否有變更時，系統就會呼叫提供版本號碼的函數。</span><span class="sxs-lookup"><span data-stu-id="526ad-144">When a request is sent to an application to query for changes, a function is called that supplies a version number.</span></span> <span data-ttu-id="526ad-145">此函數會傳回自從該版本以來已經進行之所有變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-145">The function returns information about all the changes that have been made since that version.</span></span> <span data-ttu-id="526ad-146">變更追蹤版本在某些方面與 `rowversion` 資料類型的概念很相似。</span><span class="sxs-lookup"><span data-stu-id="526ad-146">In some ways, change tracking version is similar in concept to the `rowversion` data type.</span></span>  
  
### <a name="validating-the-last-synchronized-version"></a><span data-ttu-id="526ad-147">驗證上一次同步處理的版本</span><span class="sxs-lookup"><span data-stu-id="526ad-147">Validating the Last Synchronized Version</span></span>  
 <span data-ttu-id="526ad-148">變更的相關資訊會保留一段有限的時間。</span><span class="sxs-lookup"><span data-stu-id="526ad-148">Information about changes is maintained for a limited time.</span></span> <span data-ttu-id="526ad-149">此時間長度是由可指定為 ALTER DATABASE 一部分的 CHANGE_RETENTION 參數所控制。</span><span class="sxs-lookup"><span data-stu-id="526ad-149">The length of time is controlled by the CHANGE_RETENTION parameter that can be specified as part of the ALTER DATABASE.</span></span>  
  
 <span data-ttu-id="526ad-150">請注意，針對 CHANGE_RETENTION 所指定的時間會決定所有應用程式必須向資料庫要求變更的頻率。</span><span class="sxs-lookup"><span data-stu-id="526ad-150">Be aware that the time specified for CHANGE_RETENTION determines how frequently all applications must request changes from the database.</span></span> <span data-ttu-id="526ad-151">如果某個應用程式的 *last_synchronization_version* 值早於資料表的最小有效同步處理版本，該應用程式就無法執行有效的變更列舉。</span><span class="sxs-lookup"><span data-stu-id="526ad-151">If an application has a value for *last_synchronization_version* that is older than the minimum valid synchronization version for a table, that application cannot perform valid change enumeration.</span></span> <span data-ttu-id="526ad-152">這是因為某些變更資訊可能已經清除了。</span><span class="sxs-lookup"><span data-stu-id="526ad-152">This is because some change information might have been cleaned up.</span></span> <span data-ttu-id="526ad-153">在應用程式使用 CHANGETABLE(CHANGES ...) 來取得變更之前，此應用程式必須先驗證它計劃傳遞給 CHANGETABLE(CHANGES ...) 的 *last_synchronization_version* 值。如果 *last_synchronization_version* 的值無效，該應用程式就必須重新初始化所有資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-153">Before an application obtains changes by using CHANGETABLE(CHANGES ...), the application must validate the value for *last_synchronization_version* that it plans to pass to CHANGETABLE(CHANGES ...). If the value of *last_synchronization_version* is not valid, that application must reinitialize all the data.</span></span>  
  
 <span data-ttu-id="526ad-154">下列範例將說明如何針對每份資料表驗證 `last_synchronization_version` 的值是否有效。</span><span class="sxs-lookup"><span data-stu-id="526ad-154">The following example shows how to verify the validity of the value of `last_synchronization_version` for each table.</span></span>  
  
```sql  
-- Check individual table.  
IF (@last_synchronization_version < CHANGE_TRACKING_MIN_VALID_VERSION(  
                                   OBJECT_ID('SalesLT.Product')))  
BEGIN  
  -- Handle invalid version and do not enumerate changes.  
  -- Client must be reinitialized.  
END  
```  
  
 <span data-ttu-id="526ad-155">如下列範例所示，您可以針對資料庫中的所有資料表，驗證 `last_synchronization_version` 的值是否有效。</span><span class="sxs-lookup"><span data-stu-id="526ad-155">As the following example shows, the validity of the value of `last_synchronization_version` can be checked against all tables in the database.</span></span>  
  
```sql  
-- Check all tables with change tracking enabled  
IF EXISTS (  
  SELECT COUNT(*) FROM sys.change_tracking_tables  
  WHERE min_valid_version > @last_synchronization_version )  
BEGIN  
  -- Handle invalid version & do not enumerate changes  
  -- Client must be reinitialized  
END  
```  
  
### <a name="using-column-tracking"></a><span data-ttu-id="526ad-156">使用資料行追蹤</span><span class="sxs-lookup"><span data-stu-id="526ad-156">Using Column Tracking</span></span>  
 <span data-ttu-id="526ad-157">資料行追蹤可讓應用程式僅針對已經變更的資料行 (而非整個資料列) 取得資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-157">Column tracking enables applications to obtain the data for only the columns that have changed instead of the whole row.</span></span> <span data-ttu-id="526ad-158">例如，假設某份資料表具有一個或多個龐大但很少變更的資料行，而且具有其他經常變更的資料行。</span><span class="sxs-lookup"><span data-stu-id="526ad-158">For example, consider the scenario in which a table has one or more columns that are large, but rarely change; and also has other columns that frequently change.</span></span> <span data-ttu-id="526ad-159">如果沒有使用資料行追蹤，應用程式只能判斷出某個資料列已經變更，而且必須同步處理所有資料，包括大型資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-159">Without column tracking, an application can only determine that a row has changed and would have to synchronize all the data that includes the large column data.</span></span> <span data-ttu-id="526ad-160">不過，透過資料行追蹤，應用程式就可以判斷出大型資料行的資料是否已變更，而且僅同步處理該項資料 (如果已經變更的話)。</span><span class="sxs-lookup"><span data-stu-id="526ad-160">However, by using column tracking, an application can determine whether the large column data changed and only synchronize the data if it has changed.</span></span>  
  
 <span data-ttu-id="526ad-161">資料行追蹤資訊會顯示在 CHANGETABLE(CHANGES ...) 函式所傳回的 SYS_CHANGE_COLUMNS 資料行中。</span><span class="sxs-lookup"><span data-stu-id="526ad-161">Column tracking information appears in the SYS_CHANGE_COLUMNS column that is returned by the CHANGETABLE(CHANGES ...) function.</span></span>  
  
 <span data-ttu-id="526ad-162">您可以使用資料行追蹤，以便針對尚未變更的資料行傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="526ad-162">Column tracking can be used so that NULL is returned for a column that has not changed.</span></span> <span data-ttu-id="526ad-163">如果資料行可以變更為 NULL，就必須傳回個別的資料行，以便指出資料行是否變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-163">If the column can be changed to NULL, a separate column must be returned to indicate whether the column changed.</span></span>  
  
 <span data-ttu-id="526ad-164">在下列範例中，如果 `CT_ThumbnailPhoto` 資料行並未變更，該資料行將成為 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="526ad-164">In the following example, the `CT_ThumbnailPhoto` column will be `NULL` if that column did not change.</span></span> <span data-ttu-id="526ad-165">此資料行也可能是 `NULL` ，因為它已變更為 `NULL` 。應用程式可以使用 `CT_ThumbNailPhoto_Changed` 資料行來判斷此資料行是否變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-165">This column could also be `NULL` because it was changed to `NULL` - the application can use the `CT_ThumbNailPhoto_Changed` column to determine whether the column changed.</span></span>  
  
```sql  
DECLARE @PhotoColumnId int = COLUMNPROPERTY(  
    OBJECT_ID('SalesLT.Product'),'ThumbNailPhoto', 'ColumnId')  
  
SELECT  
    CT.ProductID, P.Name, P.ListPrice, -- Always obtain values.  
    CASE  
           WHEN CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) = 1  
            THEN ThumbNailPhoto  
            ELSE NULL  
      END AS CT_ThumbNailPhoto,  
      CHANGE_TRACKING_IS_COLUMN_IN_MASK(  
                     @PhotoColumnId, CT.SYS_CHANGE_COLUMNS) AS  
                                   CT_ThumbNailPhoto_Changed  
     CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS,  
     CT.SYS_CHANGE_CONTEXT  
FROM  
     SalesLT.Product AS P  
INNER JOIN  
     CHANGETABLE(CHANGES SalesLT.Product, @last_synchronization_version) AS CT  
ON  
     P.ProductID = CT.ProductID AND  
     CT.SYS_CHANGE_OPERATION = 'U'  
```  
  
### <a name="obtaining-consistent-and-correct-results"></a><span data-ttu-id="526ad-166">取得一致且正確的結果</span><span class="sxs-lookup"><span data-stu-id="526ad-166">Obtaining Consistent and Correct Results</span></span>  
 <span data-ttu-id="526ad-167">取得資料表的變更資料需要進行多項步驟。</span><span class="sxs-lookup"><span data-stu-id="526ad-167">Obtaining the changed data for a table requires multiple steps.</span></span> <span data-ttu-id="526ad-168">請注意，如果您沒有考慮並處理特定問題，就可能會傳回不一致或不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="526ad-168">Be aware that inconsistent or incorrect results could be returned if certain issues are not considered and handled.</span></span>  
  
 <span data-ttu-id="526ad-169">例如，若要取得已經對 Sales 資料表和 SalesOrders 資料表所做的變更，應用程式會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="526ad-169">For example, to obtain the changes that were made to a Sales table and SalesOrders table, an application would perform the following steps:</span></span>  
  
1.  <span data-ttu-id="526ad-170">使用 CHANGE_TRACKING_MIN_VALID_VERSION() 來驗證上一次同步處理的版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-170">Validate the last synchronized version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
2.  <span data-ttu-id="526ad-171">使用 CHANGE_TRACKING_CURRENT_VERSION() 來取得下一次可用於取得變更的版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-171">Obtain the version that can be used to obtain change the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
3.  <span data-ttu-id="526ad-172">使用 CHANGETABLE(CHANGES ...) 來取得 Sales 資料表的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-172">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...).</span></span>  
  
4.  <span data-ttu-id="526ad-173">使用 CHANGETABLE(CHANGES ...) 來取得 Salesorders 資料表的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-173">Obtain the changes for the SalesOrders table by using CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="526ad-174">在資料庫中進行的兩個處理序可能會影響先前步驟所傳回的結果：</span><span class="sxs-lookup"><span data-stu-id="526ad-174">Two processes are occurring in the database that can affect the results that are returned by the previous steps:</span></span>  
  
-   <span data-ttu-id="526ad-175">清除處理序會在背景執行而且會移除早於指定之保留週期的變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-175">The cleanup process runs in the background and removes change tracking information that is older than the specified retention period.</span></span>  
  
     <span data-ttu-id="526ad-176">清除處理序是個別的背景處理序，它會使用您針對資料庫設定變更追蹤時指定的保留週期。</span><span class="sxs-lookup"><span data-stu-id="526ad-176">The cleanup process is a separate background process that uses the retention period that is specified when you configure change tracking for the database.</span></span> <span data-ttu-id="526ad-177">其問題在於，此清除處理序可能會在驗證上一次同步處理版本與呼叫 CHANGETABLE(CHANGES...) 之間的時間內進行。</span><span class="sxs-lookup"><span data-stu-id="526ad-177">The issue is that the cleanup process can occur in the time between when the last synchronization version was validated and when the call to CHANGETABLE(CHANGES...) is made.</span></span> <span data-ttu-id="526ad-178">原本有效的上一次同步處理版本可能會在取得變更時不再有效。</span><span class="sxs-lookup"><span data-stu-id="526ad-178">A last synchronization version that was just valid might no longer be valid by the time the changes are obtained.</span></span> <span data-ttu-id="526ad-179">因此，可能會傳回不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="526ad-179">Therefore, incorrect results might be returned.</span></span>  
  
-   <span data-ttu-id="526ad-180">持續進行的 DML 作業會在 Sales 和 SalesOrders 資料表中進行，例如下列作業：</span><span class="sxs-lookup"><span data-stu-id="526ad-180">Ongoing DML operations are occurring in the Sales and SalesOrders tables, such as the following operations:</span></span>  
  
    -   <span data-ttu-id="526ad-181">已經使用 CHANGE_TRACKING_CURRENT_VERSION() 取得下一次的版本之後，可能會對資料表進行變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-181">Changes can be made to the tables after the version for next time has been obtained by using CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="526ad-182">因此，可能會傳回比預期更多的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-182">Therefore, more changes can be returned than expected.</span></span>  
  
    -   <span data-ttu-id="526ad-183">交易可能會在從 Sales 資料表中取得變更的呼叫與從 SalesOrders 資料表中取得變更的呼叫之間的時間內認可。</span><span class="sxs-lookup"><span data-stu-id="526ad-183">A transaction could commit in the time between the call to obtain changes from the Sales table and the call to obtain changes from the SalesOrders table.</span></span> <span data-ttu-id="526ad-184">因此，SalesOrder 資料表的結果可能會具有不存在 Sales 資料表中的外部索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="526ad-184">Therefore, the results for the SalesOrder table could have foreign key value that does not exist in the Sales table.</span></span>  
  
 <span data-ttu-id="526ad-185">若要克服先前列出的挑戰，我們建議您使用快照集隔離。</span><span class="sxs-lookup"><span data-stu-id="526ad-185">To overcome the previously listed challenges, we recommend that you use snapshot isolation.</span></span> <span data-ttu-id="526ad-186">這樣做有助於確保變更資訊的一致性，並且避免發生與背景清除工作有關的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="526ad-186">This will help to ensure consistency of change information and avoid race conditions that are related to the background cleanup task.</span></span> <span data-ttu-id="526ad-187">如果您沒有使用快照集交易，則開發使用變更追蹤的應用程式時，可能需要投入相當多的心力。</span><span class="sxs-lookup"><span data-stu-id="526ad-187">If you do not use snapshot transactions, developing an application that uses change tracking could require significantly more effort.</span></span>  
  
#### <a name="using-snapshot-isolation"></a><span data-ttu-id="526ad-188">使用快照集隔離</span><span class="sxs-lookup"><span data-stu-id="526ad-188">Using Snapshot Isolation</span></span>  
 <span data-ttu-id="526ad-189">變更追蹤已經設計成可搭配快照集隔離順利運作。</span><span class="sxs-lookup"><span data-stu-id="526ad-189">Change tracking has been designed to work well with snapshot isolation.</span></span> <span data-ttu-id="526ad-190">您必須針對資料庫啟用快照集隔離。</span><span class="sxs-lookup"><span data-stu-id="526ad-190">Snapshot isolation must be enabled for the database.</span></span> <span data-ttu-id="526ad-191">取得變更所需的所有步驟都必須包含在快照集交易內部。</span><span class="sxs-lookup"><span data-stu-id="526ad-191">All the steps that are required to obtain changes must be included inside a snapshot transaction.</span></span> <span data-ttu-id="526ad-192">這樣做可確保取得變更時，快照集交易內部的查詢看不到對資料所做的所有變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-192">This will ensure that all changes that are made to data while obtaining changes will not be visible to the queries inside the snapshot transaction.</span></span>  
  
 <span data-ttu-id="526ad-193">若要取得快照集交易內部的資料，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="526ad-193">To obtain data inside a snapshot transaction, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="526ad-194">將交易隔離等級設定為快照集並開始交易。</span><span class="sxs-lookup"><span data-stu-id="526ad-194">Set the transaction isolation level to snapshot and start a transaction.</span></span>  
  
2.  <span data-ttu-id="526ad-195">使用 CHANGE_TRACKING_MIN_VALID_VERSION() 來驗證上一次同步處理版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-195">Validate the last synchronization version by using CHANGE_TRACKING_MIN_VALID_VERSION().</span></span>  
  
3.  <span data-ttu-id="526ad-196">使用 CHANGE_TRACKING_CURRENT_VERSION() 來取得下一次使用的版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-196">Obtain the version to be used the next time by using CHANGE_TRACKING_CURRENT_VERSION().</span></span>  
  
4.  <span data-ttu-id="526ad-197">使用 CHANGETABLE(CHANGES ...) 來取得 Sales 資料表的變更</span><span class="sxs-lookup"><span data-stu-id="526ad-197">Obtain the changes for the Sales table by using CHANGETABLE(CHANGES ...)</span></span>  
  
5.  <span data-ttu-id="526ad-198">使用 CHANGETABLE(CHANGES ...) 來取得 Salesorders 資料表的變更</span><span class="sxs-lookup"><span data-stu-id="526ad-198">Obtain the changes for the Salesorders table by using CHANGETABLE(CHANGES ...)</span></span>  
  
6.  <span data-ttu-id="526ad-199">認可交易。</span><span class="sxs-lookup"><span data-stu-id="526ad-199">Commit the transaction.</span></span>  
  
 <span data-ttu-id="526ad-200">請記住一些重點，因為取得變更的所有步驟都在快照集交易內部：</span><span class="sxs-lookup"><span data-stu-id="526ad-200">Some points to remember as all steps to obtain changes are inside a snapshot transaction:</span></span>  
  
-   <span data-ttu-id="526ad-201">如果清除在驗證上一次同步處理版本之後進行，CHANGETABLE(CHANGES ...) 的結果仍然有效，因為在交易內部看不到清除所執行的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="526ad-201">If cleanup occurs after the last synchronization version is validated, the results from CHANGETABLE(CHANGES ...) will still be valid as the delete operations performed by cleanup will not be visible inside the transaction.</span></span>  
  
-   <span data-ttu-id="526ad-202">取得下一次同步處理版本之後，看不到對 Sales 資料表或 SalesOrders 資料表所做的任何變更，而且對 CHANGETABLE(CHANGES ...) 的呼叫永遠不會傳回版本晚於 CHANGE_TRACKING_CURRENT_VERSION() 所傳回的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-202">Any changes that are made to the Sales table or the SalesOrders table after the next synchronization version is obtained will not be visible, and the calls to CHANGETABLE(CHANGES ...) will never return changes with a version later than that returned by CHANGE_TRACKING_CURRENT_VERSION().</span></span> <span data-ttu-id="526ad-203">此外，Sales 資料表與 SalesOrders 資料表之間的一致性也會保留下來，因為看不到在呼叫 CHANGETABLE(CHANGES ...) 之間的時間內認可的交易。</span><span class="sxs-lookup"><span data-stu-id="526ad-203">Consistency between the Sales table and the SalesOrders table will also be maintained, because the transactions that were committed in the time between calls to CHANGETABLE(CHANGES ...) will not be visible.</span></span>  
  
 <span data-ttu-id="526ad-204">下列範例將說明如何針對資料庫啟用快照集隔離。</span><span class="sxs-lookup"><span data-stu-id="526ad-204">The following example shows how snapshot isolation is enabled for a database.</span></span>  
  
```sql  
-- The database must be configured to enable snapshot isolation.  
ALTER DATABASE AdventureWorksLT  
    SET ALLOW_SNAPSHOT_ISOLATION ON;  
```  
  
 <span data-ttu-id="526ad-205">快照集交易的使用方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="526ad-205">A snapshot transaction is used as follows:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
  -- Verify that version of the previous synchronization is valid.  
  -- Obtain the version to use next time.  
  -- Obtain changes.  
COMMIT TRAN  
```  
  
 <span data-ttu-id="526ad-206">如需快照集交易的詳細資訊，請參閱 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="526ad-206">For more information about snapshot transactions, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
#### <a name="alternatives-to-using-snapshot-isolation"></a><span data-ttu-id="526ad-207">使用快照集隔離的替代方案</span><span class="sxs-lookup"><span data-stu-id="526ad-207">Alternatives to Using Snapshot Isolation</span></span>  
 <span data-ttu-id="526ad-208">雖然我們提供了使用快照集隔離的替代方案，但是這些替代方案需要進行更多工作，才能確保符合所有應用程式需求。</span><span class="sxs-lookup"><span data-stu-id="526ad-208">There are alternatives to using snapshot isolation, but they require more work to make sure all application requirements are met.</span></span> <span data-ttu-id="526ad-209">若要確保 *last_synchronization_version* 有效，而且清除處理序不會在取得變更之前移除資料，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="526ad-209">To make sure the *last_synchronization_version* is valid and data is not removed by the cleanup process before changes are obtained, do the following:</span></span>  
  
1.  <span data-ttu-id="526ad-210">在呼叫 CHANGETABLE() 之後檢查 *last_synchronization_version* 。</span><span class="sxs-lookup"><span data-stu-id="526ad-210">Check *last_synchronization_version* after the calls to CHANGETABLE().</span></span>  
  
2.  <span data-ttu-id="526ad-211">在使用 CHANGETABLE() 來取得變更的每個查詢中檢查 *last_synchronization_version* 。</span><span class="sxs-lookup"><span data-stu-id="526ad-211">Check *last_synchronization_version* as part of each query to obtain changes by using CHANGETABLE().</span></span>  
  
 <span data-ttu-id="526ad-212">已經取得下一次列舉的同步處理版本之後，可能會發生變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-212">Changes can occur after the synchronization version for the next enumeration has been obtained.</span></span> <span data-ttu-id="526ad-213">有兩種方式可以處理此情況。</span><span class="sxs-lookup"><span data-stu-id="526ad-213">There are two ways to handle this situation.</span></span> <span data-ttu-id="526ad-214">所使用的選項會因應用程式以及它如何處理每個方法的副作用而定：</span><span class="sxs-lookup"><span data-stu-id="526ad-214">The option that is used depends on the application and how it can handle the side-effects of each approach:</span></span>  
  
-   <span data-ttu-id="526ad-215">忽略版本大於新同步處理版本的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-215">Ignore changes that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="526ad-216">這種方法的副作用是，如果全新或更新的資料列是在新同步處理版本之前建立或更新，但是之後再更新，系統就會略過此資料列。</span><span class="sxs-lookup"><span data-stu-id="526ad-216">This approach has the side effect that a new or updated row would be skipped if it was created or updated before the new synchronization version, but then updated afterward.</span></span> <span data-ttu-id="526ad-217">如果有一個全新的資料列，而且在另一份資料表中建立了參考已略過資料列的資料列，可能會發生參考完整性問題。</span><span class="sxs-lookup"><span data-stu-id="526ad-217">If there is a new row, a referential integrity problem might occur if there was a row in another table that was created that referenced the skipped row.</span></span> <span data-ttu-id="526ad-218">如果有一個更新的現有資料列，系統就會略過此資料列，而且下一次之前不會進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="526ad-218">If there is an updated existing row, the row will be skipped and not synchronized until the next time.</span></span>  
  
-   <span data-ttu-id="526ad-219">包含所有變更，即使版本大於新同步處理版本的變更也一樣。</span><span class="sxs-lookup"><span data-stu-id="526ad-219">Include all changes, even those that have a version larger than the new synchronization version.</span></span>  
  
     <span data-ttu-id="526ad-220">下一次同步處理時，將再次取得版本大於新同步處理版本的資料列。</span><span class="sxs-lookup"><span data-stu-id="526ad-220">The rows that have a version larger than the new synchronization version will be obtained again on the next synchronization.</span></span> <span data-ttu-id="526ad-221">應用程式必須預期並處理這點。</span><span class="sxs-lookup"><span data-stu-id="526ad-221">This must be expected and handled by the application.</span></span>  
  
 <span data-ttu-id="526ad-222">除了上述兩個選項以外，您可以根據作業，設計出結合這兩個選項的方法。</span><span class="sxs-lookup"><span data-stu-id="526ad-222">In addition to the previous two options, you can devise approach that combines both options, depending on the operation.</span></span> <span data-ttu-id="526ad-223">例如，您可能會想要最好能忽略比下一個同步處理版本 (其中有資料列建立或刪除) 更新的變更，但是不忽略更新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="526ad-223">For example, you might want an application for which it is best to ignore changes newer than the next synchronization version in which the row was created or deleted, but updates are not ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="526ad-224">當您使用變更追蹤 (或任何自訂追蹤機制) 時，選擇適用於應用程式的方法需要進行大量分析。</span><span class="sxs-lookup"><span data-stu-id="526ad-224">Choosing the approach that will work for the application when you are using change tracking (or any custom tracking mechanism), requires significant analysis.</span></span> <span data-ttu-id="526ad-225">因此，使用快照集隔離就簡單多了。</span><span class="sxs-lookup"><span data-stu-id="526ad-225">Therefore, it is much simpler to use snapshot isolation.</span></span>  
  
##  <a name="how-change-tracking-handles-changes-to-a-database"></a><a name="Handles"></a><span data-ttu-id="526ad-226">變更追蹤如何處理資料庫的變更</span><span class="sxs-lookup"><span data-stu-id="526ad-226">How Change Tracking Handles Changes to a Database</span></span>  
 <span data-ttu-id="526ad-227">某些使用變更追蹤的應用程式會使用另一個資料存放區來執行雙向同步處理。</span><span class="sxs-lookup"><span data-stu-id="526ad-227">Some applications that use change tracking perform two-way synchronization with another data store.</span></span> <span data-ttu-id="526ad-228">也就是說，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中進行的變更會在其他資料存放區中更新，而在其他存放區中進行的變更則會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中更新。</span><span class="sxs-lookup"><span data-stu-id="526ad-228">That is, changes that are made in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database are updated in the other data store, and changes that are made in the other store are updated in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="526ad-229">當某個應用程式使用另一個資料存放區的更新來更新本機資料庫時，此應用程式就必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="526ad-229">When an application updates the local database with changes from another data store, the application must perform the following operations:</span></span>  
  
-   <span data-ttu-id="526ad-230">檢查是否有衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-230">Check for conflicts.</span></span>  
  
     <span data-ttu-id="526ad-231">如果兩個資料存放區中的相同資料同時變更，就會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-231">A conflict occurs when the same data is changed at the same time in both data stores.</span></span> <span data-ttu-id="526ad-232">應用程式必須能夠檢查是否有衝突，而且取得足夠的資訊來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-232">The application must be able to check for a conflict and obtain enough information to enable the conflict to be resolved.</span></span>  
  
-   <span data-ttu-id="526ad-233">儲存應用程式內容資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-233">Store application context information.</span></span>  
  
     <span data-ttu-id="526ad-234">應用程式會儲存具有變更追蹤資訊的資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-234">The application stores data that has the change tracking information.</span></span> <span data-ttu-id="526ad-235">從本機資料庫中取得變更時，就可以使用這項資訊以及其他變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-235">This information would be available together with other change tracking information when changes were obtained from the local database.</span></span> <span data-ttu-id="526ad-236">這個內容資訊的常見範例是屬於變更來源之資料存放區的識別碼。</span><span class="sxs-lookup"><span data-stu-id="526ad-236">A common example of this contextual information is an identifier for the data store that was the source of the change.</span></span>  
  
 <span data-ttu-id="526ad-237">若要執行上述作業，同步處理應用程式可以使用下列函數：</span><span class="sxs-lookup"><span data-stu-id="526ad-237">To perform the previous operations, a synchronization application can use the following functions:</span></span>  
  
-   <span data-ttu-id="526ad-238">CHANGETABLE(VERSION...)</span><span class="sxs-lookup"><span data-stu-id="526ad-238">CHANGETABLE(VERSION...)</span></span>  
  
     <span data-ttu-id="526ad-239">當應用程式正在進行變更時，它可以使用此函數來檢查是否有衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-239">When an application is making changes, it can use this function to check for conflicts.</span></span> <span data-ttu-id="526ad-240">這個函數會針對變更追蹤資料表中的指定資料列，取得最新變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-240">The function obtains the latest change tracking information for a specified row in a change tracked table.</span></span> <span data-ttu-id="526ad-241">此變更追蹤資訊包括上一次變更的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="526ad-241">The change tracking information includes the version of the row that was last changed.</span></span> <span data-ttu-id="526ad-242">這項資訊可讓應用程式判斷，此資料列在上一次應用程式同步處理之後是否已變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-242">This information enables an application to determine whether the row was changed after the last time that the application was synchronized.</span></span>  
  
-   <span data-ttu-id="526ad-243">WITH CHANGE_TRACKING_CONTEXT</span><span class="sxs-lookup"><span data-stu-id="526ad-243">WITH CHANGE_TRACKING_CONTEXT</span></span>  
  
     <span data-ttu-id="526ad-244">應用程式可以使用這個子句來儲存內容資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-244">An application can use this clause to store context data.</span></span>  
  
### <a name="checking-for-conflicts"></a><span data-ttu-id="526ad-245">檢查是否有衝突</span><span class="sxs-lookup"><span data-stu-id="526ad-245">Checking for Conflicts</span></span>  
 <span data-ttu-id="526ad-246">在雙向同步處理狀況中，用戶端應用程式必須判斷自從應用程式上一次取得變更以來，某個資料列是否尚未更新。</span><span class="sxs-lookup"><span data-stu-id="526ad-246">In a two-way synchronization scenario, the client application must determine whether a row has not been updated since the application last obtained the changes.</span></span>  
  
 <span data-ttu-id="526ad-247">下列範例將示範如何使用 CHANGETABLE(VERSION ...) 函式，以最有效率的方式 (不需要個別查詢) 檢查是否有衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-247">The following example shows how to use the CHANGETABLE(VERSION ...) function to check for conflicts in the most efficient way, without a separate query.</span></span> <span data-ttu-id="526ad-248">在此範例中， `CHANGETABLE(VERSION ...)` 會針對 `SYS_CHANGE_VERSION` 所指定的資料列，判斷 `@product id`。</span><span class="sxs-lookup"><span data-stu-id="526ad-248">In the example, `CHANGETABLE(VERSION ...)` determines the `SYS_CHANGE_VERSION` for the row specified by `@product id`.</span></span> <span data-ttu-id="526ad-249">`CHANGETABLE(CHANGES ...)` 可以取得相同的資訊，但是這樣做比較沒有效率。</span><span class="sxs-lookup"><span data-stu-id="526ad-249">`CHANGETABLE(CHANGES ...)` can obtain the same information, but that would be less efficient.</span></span> <span data-ttu-id="526ad-250">如果資料列的 `SYS_CHANGE_VERSION` 值大於 `@last_sync_version`的值，就表示發生衝突。</span><span class="sxs-lookup"><span data-stu-id="526ad-250">If the value of `SYS_CHANGE_VERSION` for the row is larger than the value of `@last_sync_version`, there is a conflict.</span></span> <span data-ttu-id="526ad-251">如果發生衝突，系統將不會更新此資料列。</span><span class="sxs-lookup"><span data-stu-id="526ad-251">If there is a conflict, the row will not be updated.</span></span> <span data-ttu-id="526ad-252">`ISNULL()` 檢查是必要的，因為資料列可能沒有任何變更資訊可用。</span><span class="sxs-lookup"><span data-stu-id="526ad-252">The `ISNULL()` check is required because there might be no change information available for the row.</span></span> <span data-ttu-id="526ad-253">如果自從啟用變更追蹤或清除變更資訊以來，此資料列尚未更新，就不會有任何變更資訊存在。</span><span class="sxs-lookup"><span data-stu-id="526ad-253">No change information would exist if the row had not been updated since change tracking was enabled or since the change information was cleaned up.</span></span>  
  
```sql  
-- Assumption: @last_sync_version has been validated.  
  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        SELECT CT.SYS_CHANGE_VERSION  
        FROM CHANGETABLE(VERSION SalesLT.Product,  
                        (ProductID), (P.ProductID)) AS CT),  
        0)  
```  
  
 <span data-ttu-id="526ad-254">下列程式碼可以檢查更新的資料列計數，而且可以識別衝突的更多相關資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-254">The following code can check the updated row count and can identify more information about the conflict.</span></span>  
  
```sql  
-- If the change cannot be made, find out more information.  
IF (@@ROWCOUNT = 0)  
BEGIN  
    -- Obtain the complete change information for the row.  
    SELECT  
        CT.SYS_CHANGE_VERSION, CT.SYS_CHANGE_CREATION_VERSION,  
        CT.SYS_CHANGE_OPERATION, CT.SYS_CHANGE_COLUMNS  
    FROM  
        CHANGETABLE(CHANGES SalesLT.Product, @last_sync_version) AS CT  
    WHERE  
        CT.ProductID = @product_id;  
  
    -- Check CT.SYS_CHANGE_VERSION to verify that it really was a conflict.  
    -- Check CT.SYS_CHANGE_OPERATION to determine the type of conflict:  
    -- update-update or update-delete.  
    -- The row that is specified by @product_id might no longer exist   
    -- if it has been deleted.  
END  
```  
  
### <a name="setting-context-information"></a><span data-ttu-id="526ad-255">設定內容資訊</span><span class="sxs-lookup"><span data-stu-id="526ad-255">Setting Context Information</span></span>  
 <span data-ttu-id="526ad-256">應用程式可以使用 WITH CHANGE_TRACKING_CONTEXT 子句，將內容資訊與變更資訊儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="526ad-256">By using the WITH CHANGE_TRACKING_CONTEXT clause, an application can store context information together with the change information.</span></span> <span data-ttu-id="526ad-257">然後，您就可以從 CHANGETABLE(CHANGES ...) 傳回的 SYS_CHANGE_CONTEXT 資料行中取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-257">This information can then be obtained from the SYS_CHANGE_CONTEXT column that is returned by CHANGETABLE(CHANGES ...).</span></span>  
  
 <span data-ttu-id="526ad-258">內容資訊通常是用來識別變更的來源。</span><span class="sxs-lookup"><span data-stu-id="526ad-258">Context information is typically used to identify the source of the changes.</span></span> <span data-ttu-id="526ad-259">如果能夠識別變更的來源，再度同步處理時，資料存放區就可以使用該項資訊來避免取得變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-259">If the source of the change can be identified, that information can be used by a data store to avoid obtaining changes when it synchronizes again.</span></span>  
  
```sql  
  -- Try to update the row and check for a conflict.  
  WITH CHANGE_TRACKING_CONTEXT (@source_id)  
  UPDATE  
     SalesLT.Product  
  SET  
      ListPrice = @new_listprice  
  FROM  
      SalesLT.Product AS P  
  WHERE  
     ProductID = @product_id AND  
     @last_sync_version >= ISNULL (  
         (SELECT CT.SYS_CHANGE_VERSION FROM CHANGETABLE(VERSION SalesLT.Product,  
         (ProductID), (P.ProductID)) AS CT),  
         0)  
```  
  
### <a name="ensuring-consistent-and-correct-results"></a><span data-ttu-id="526ad-260">確保一致且正確的結果</span><span class="sxs-lookup"><span data-stu-id="526ad-260">Ensuring Consistent and Correct Results</span></span>  
 <span data-ttu-id="526ad-261">當應用程式驗證 @last_sync_version 的值時，必須考慮清除處理序。</span><span class="sxs-lookup"><span data-stu-id="526ad-261">An application must consider the cleanup process when it validates the value of @last_sync_version.</span></span> <span data-ttu-id="526ad-262">這是因為在呼叫 CHANGE_TRACKING_MIN_VALID_VERSION() 之後，但在進行更新之前，可能已經移除資料了。</span><span class="sxs-lookup"><span data-stu-id="526ad-262">This is because data could have been removed after CHANGE_TRACKING_MIN_VALID_VERSION() was called, but before the update was made.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="526ad-263">我們建議您使用快照集隔離並在快照集交易內部進行變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-263">We recommend that you use snapshot isolation and make the changes within a snapshot transaction.</span></span>  
  
```sql  
-- Prerequisite is to ensure ALLOW_SNAPSHOT_ISOLATION is ON for the database.  
  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
BEGIN TRAN  
    -- Verify that last_sync_version is valid.  
    IF (@last_sync_version <  
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('SalesLT.Product')))  
    BEGIN  
       RAISERROR (N'Last_sync_version too old', 16, -1);  
    END  
    ELSE  
    BEGIN  
        -- Try to update the row.  
        -- Check @@ROWCOUNT and check for a conflict.  
    END  
COMMIT TRAN  
```  
  
> [!NOTE]  
>  <span data-ttu-id="526ad-264">當快照集交易啟動之後，快照集交易內所更新的資料列有可能已經在另一個交易內更新。</span><span class="sxs-lookup"><span data-stu-id="526ad-264">There is a possibility that the row being updated within the snapshot transaction could have been updated in another transaction after the snapshot transaction was started.</span></span> <span data-ttu-id="526ad-265">在此情況下，將會發生快照集隔離更新衝突，而且會導致交易結束。</span><span class="sxs-lookup"><span data-stu-id="526ad-265">In this case, a snapshot isolation update conflict will occur and lead to the transaction being terminated.</span></span> <span data-ttu-id="526ad-266">如果發生這種情況，請重試更新。</span><span class="sxs-lookup"><span data-stu-id="526ad-266">If this happens, retry the update.</span></span> <span data-ttu-id="526ad-267">然後，這會讓變更追蹤衝突得以偵測到，而且不會變更任何資料列。</span><span class="sxs-lookup"><span data-stu-id="526ad-267">This will then lead to a change tracking conflict being detected and no rows being changed.</span></span>  
  
##  <a name="change-tracking-and-data-restore"></a><a name="DataRestore"></a><span data-ttu-id="526ad-268">變更追蹤和資料還原</span><span class="sxs-lookup"><span data-stu-id="526ad-268">Change Tracking and Data Restore</span></span>  
 <span data-ttu-id="526ad-269">需要同步處理的應用程式必須考慮已啟用變更追蹤的資料庫還原成舊版資料的情況。</span><span class="sxs-lookup"><span data-stu-id="526ad-269">Applications that require synchronization must consider the case in which a database that has change tracking enabled reverts to an earlier version of the data.</span></span> <span data-ttu-id="526ad-270">當容錯移轉到非同步資料庫鏡像，或是當使用記錄傳送而發生失敗時，從備份還原資料庫之後可能會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="526ad-270">This can occur after a database is restored from a backup, when there is a failover to an asynchronous database mirror, or when there is a failure when using log shipping.</span></span> <span data-ttu-id="526ad-271">下列案例說明這個問題：</span><span class="sxs-lookup"><span data-stu-id="526ad-271">The following scenario illustrates the issue:</span></span>  
  
1.  <span data-ttu-id="526ad-272">資料表 T1 有進行變更追蹤，此資料表的最小有效版本為 50。</span><span class="sxs-lookup"><span data-stu-id="526ad-272">Table T1 is change tracked, and the minimum valid version for table is 50.</span></span>  
  
2.  <span data-ttu-id="526ad-273">用戶端應用程式會同步處理版本 100 上的資料，並取得版本 50 與 100 之間所有變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="526ad-273">A client application synchronizes data at version 100 and obtains information about all changes between versions 50 and 100.</span></span>  
  
3.  <span data-ttu-id="526ad-274">版本 100 之後會對資料表 T1 進行其他變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-274">Additional changes are made to table T1 after version 100.</span></span>  
  
4.  <span data-ttu-id="526ad-275">在版本 120 上發生失敗情況，而且資料庫管理員會還原有遺失資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="526ad-275">At version 120, there is a failure and the database administrator restores the database with data loss.</span></span> <span data-ttu-id="526ad-276">在還原作業之後，資料表會包含直到版本 70 的資料，而最小的同步處理版本仍然是 50。</span><span class="sxs-lookup"><span data-stu-id="526ad-276">After the restore operation, the table contains data up through version 70, and the minimum synchronized version is still 50.</span></span>  
  
     <span data-ttu-id="526ad-277">這表示同步處理的資料存放區包含了不復存在於主要資料存放區內的資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-277">This means that the synchronized data store has data that no longer exists in the primary data store.</span></span>  
  
5.  <span data-ttu-id="526ad-278">T1 會更新許多次。</span><span class="sxs-lookup"><span data-stu-id="526ad-278">T1 is updated many times.</span></span> <span data-ttu-id="526ad-279">這會將目前的版本帶到 130。</span><span class="sxs-lookup"><span data-stu-id="526ad-279">This brings the current version to 130.</span></span>  
  
6.  <span data-ttu-id="526ad-280">用戶端應用程式會再次同步處理，並提供上一次同步處理的版本 100。</span><span class="sxs-lookup"><span data-stu-id="526ad-280">The client application synchronizes again and supplies a last-synchronized version of 100.</span></span> <span data-ttu-id="526ad-281">用戶端將會成功驗證這個號碼，因為 100 大於 50。</span><span class="sxs-lookup"><span data-stu-id="526ad-281">The client validates this number successfully because 100 is greater than 50.</span></span>  
  
     <span data-ttu-id="526ad-282">用戶端會取得版本 100 與 130 之間的變更。</span><span class="sxs-lookup"><span data-stu-id="526ad-282">The client obtains changes between version 100 and 130.</span></span> <span data-ttu-id="526ad-283">此時，用戶端不會意識到 70 與 100 之間的變更與之前不同。</span><span class="sxs-lookup"><span data-stu-id="526ad-283">At this point, the client is not aware that the changes between 70 and 100 are not the same as before.</span></span> <span data-ttu-id="526ad-284">用戶端與伺服器上的資料不會同步處理。</span><span class="sxs-lookup"><span data-stu-id="526ad-284">The data on the client and server are not synchronized.</span></span>  
  
 <span data-ttu-id="526ad-285">請注意，如果資料庫復原到版本 100 之後的某一點，同步處理就不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="526ad-285">Note that if the database was recovered to a point after version 100, there would be no problems with synchronization.</span></span> <span data-ttu-id="526ad-286">用戶端和伺服器會在下一次同步處理間隔期間正確同步處理資料。</span><span class="sxs-lookup"><span data-stu-id="526ad-286">The client and server would synchronize data correctly during the next synchronization interval.</span></span>  
  
 <span data-ttu-id="526ad-287">變更追蹤不支援從遺失資料進行復原。</span><span class="sxs-lookup"><span data-stu-id="526ad-287">Change tracking does not provide support for recovering from the loss of data.</span></span> <span data-ttu-id="526ad-288">但是，有兩個選擇可用來偵測這些類型的同步處理問題：</span><span class="sxs-lookup"><span data-stu-id="526ad-288">However, there are two options for detecting these types of synchronization issues:</span></span>  
  
-   <span data-ttu-id="526ad-289">將資料庫版本識別碼儲存在伺服器上，並在每次復原資料庫或是遺失資料時更新這個值。</span><span class="sxs-lookup"><span data-stu-id="526ad-289">Store a database version ID on the server, and update this value whenever a database is recovered or otherwise loses data.</span></span> <span data-ttu-id="526ad-290">每一個用戶端應用程式都將儲存這個識別碼，而且每一個用戶端在同步處理資料時，都必須驗證此識別碼。</span><span class="sxs-lookup"><span data-stu-id="526ad-290">Each client application would store the ID, and each client would have to validate this ID when it synchronizes data.</span></span> <span data-ttu-id="526ad-291">如果發生資料遺失，識別碼將不會相符，而用戶端也將重新初始化。</span><span class="sxs-lookup"><span data-stu-id="526ad-291">If data loss occurs, the IDs will not match and the clients would reinitialize.</span></span> <span data-ttu-id="526ad-292">但是有一項缺點，就是當資料遺失未跨越上一次同步處理的界限時，用戶端可能會執行不必要的重新初始化。</span><span class="sxs-lookup"><span data-stu-id="526ad-292">One drawback is if the data loss had not crossed the last synchronized boundary, the client might do unnecessary reinitialization.</span></span>  
  
-   <span data-ttu-id="526ad-293">當用戶端查詢變更時，請在伺服器上記錄每一個用戶端上一次同步處理的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="526ad-293">When a client queries for changes, record the last synchronization version number for each client on the server.</span></span> <span data-ttu-id="526ad-294">如果資料有問題，上一次同步處理的版本號碼將不會相符。</span><span class="sxs-lookup"><span data-stu-id="526ad-294">If there is a problem with the data, the last synchronized version numbers would not match.</span></span> <span data-ttu-id="526ad-295">這表示必須重新初始化。</span><span class="sxs-lookup"><span data-stu-id="526ad-295">This indicates that a reinitialization is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526ad-296">另請參閱</span><span class="sxs-lookup"><span data-stu-id="526ad-296">See Also</span></span>  
 <span data-ttu-id="526ad-297">[追蹤資料變更 &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="526ad-297">[Track Data Changes &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="526ad-298">[關於變更追蹤 &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="526ad-298">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="526ad-299">[管理變更追蹤 &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="526ad-299">[Manage Change Tracking &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="526ad-300">[啟用和停用變更追蹤 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="526ad-300">[Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="526ad-301">[CHANGETABLE &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="526ad-301">[CHANGETABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/changetable-transact-sql) </span></span>  
 <span data-ttu-id="526ad-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="526ad-302">[CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-min-valid-version-transact-sql) </span></span>  
 <span data-ttu-id="526ad-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="526ad-303">[CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/change-tracking-current-version-transact-sql) </span></span>  
 [<span data-ttu-id="526ad-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="526ad-304">WITH CHANGE_TRACKING_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/with-change-tracking-context-transact-sql)  
  
  
