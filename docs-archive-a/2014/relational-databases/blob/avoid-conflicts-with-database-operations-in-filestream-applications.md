---
title: 避免與 FILESTREAM 應用程式中的資料庫作業相衝突 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32 and Transact-SQL Conflicts
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ac7e681766396d3a3b4412d91a968b4cdc653c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599031"
---
# <a name="avoid-conflicts-with-database-operations-in-filestream-applications"></a><span data-ttu-id="ea1b7-102">避免與 FILESTREAM 應用程式中的資料庫作業相衝突</span><span class="sxs-lookup"><span data-stu-id="ea1b7-102">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>
  <span data-ttu-id="ea1b7-103">使用 SqlOpenFilestream() 來開啟 Win32 檔案控制代碼以便讀取或寫入 FILESTREAM BLOB 資料的應用程式可能會與在一般交易中管理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式發生衝突錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-103">Applications that use SqlOpenFilestream() to open Win32 file handles for reading or writing FILESTREAM BLOB data can encounter conflict errors with [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are managed in a common transaction.</span></span> <span data-ttu-id="ea1b7-104">這包括需要很長時間才能執行完成的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或 MARS 查詢。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-104">This includes [!INCLUDE[tsql](../../includes/tsql-md.md)] or MARS queries that take a long time to finish execution.</span></span> <span data-ttu-id="ea1b7-105">若要有效避免這些衝突類型，您必須仔細地設計應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-105">Applications must be carefully designed to help avoid these types of conflicts.</span></span>  
  
 <span data-ttu-id="ea1b7-106">當 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 或應用程式嘗試開啟 FILESTREAM BLOB 時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會檢查相關聯的交易內容。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-106">When [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or applications try to open FILESTREAM BLOBs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] checks the associated transaction context.</span></span> <span data-ttu-id="ea1b7-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會根據開啟作業是使用 DDL 陳述式、DML 陳述式、擷取資料或管理交易，允許或拒絕此要求。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] allows or denies the request based on whether the open operation is working with DDL statements, DML statements, retrieving data, or managing transactions.</span></span> <span data-ttu-id="ea1b7-108">下表將顯示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 根據交易所開啟的檔案類型來判斷允許或拒絕 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-108">The following table shows how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines whether a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will be allowed or denied based on the type of files that are open in the transaction.</span></span>  
  
|<span data-ttu-id="ea1b7-109">Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea1b7-109">Transact-SQL statements</span></span>|<span data-ttu-id="ea1b7-110">開啟以便讀取</span><span class="sxs-lookup"><span data-stu-id="ea1b7-110">Opened for read</span></span>|<span data-ttu-id="ea1b7-111">開啟以便寫入</span><span class="sxs-lookup"><span data-stu-id="ea1b7-111">Opened for write</span></span>|  
|------------------------------|---------------------|----------------------|  
|<span data-ttu-id="ea1b7-112">使用資料庫中繼資料的 DDL 陳述式，例如 CREATE TABLE、CREATE INDEX、DROP TABLE 和 ALTER TABLE。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-112">DDL statements that work with database metadata, such as CREATE TABLE, CREATE INDEX, DROP TABLE, and ALTER TABLE.</span></span>|<span data-ttu-id="ea1b7-113">允許</span><span class="sxs-lookup"><span data-stu-id="ea1b7-113">Allowed</span></span>|<span data-ttu-id="ea1b7-114">封鎖並且因逾時而失敗。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-114">Are blocked and fail with a time-out.</span></span>|  
|<span data-ttu-id="ea1b7-115">使用資料庫所儲存之資料的 DML 陳述式，例如 UPDATE、DELETE 和 INSERT。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-115">DML statements that work with the data that is stored in the database, such as UPDATE, DELETE, and INSERT.</span></span>|<span data-ttu-id="ea1b7-116">允許</span><span class="sxs-lookup"><span data-stu-id="ea1b7-116">Allowed</span></span>|<span data-ttu-id="ea1b7-117">拒絕</span><span class="sxs-lookup"><span data-stu-id="ea1b7-117">Denied</span></span>|  
|<span data-ttu-id="ea1b7-118">SELECT</span><span class="sxs-lookup"><span data-stu-id="ea1b7-118">SELECT</span></span>|<span data-ttu-id="ea1b7-119">允許</span><span class="sxs-lookup"><span data-stu-id="ea1b7-119">Allowed</span></span>|<span data-ttu-id="ea1b7-120">允許</span><span class="sxs-lookup"><span data-stu-id="ea1b7-120">Allowed</span></span>|  
|<span data-ttu-id="ea1b7-121">COMMIT TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="ea1b7-121">COMMIT TRANSACTION</span></span>|<span data-ttu-id="ea1b7-122">拒絕\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-122">Denied\*</span></span>|<span data-ttu-id="ea1b7-123">拒絕\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-123">Denied\*.</span></span>|  
|<span data-ttu-id="ea1b7-124">SAVE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="ea1b7-124">SAVE TRANSACTION</span></span>|<span data-ttu-id="ea1b7-125">拒絕\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-125">Denied\*</span></span>|<span data-ttu-id="ea1b7-126">拒絕\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-126">Denied\*</span></span>|  
|<span data-ttu-id="ea1b7-127">ROLLBACK</span><span class="sxs-lookup"><span data-stu-id="ea1b7-127">ROLLBACK</span></span>|<span data-ttu-id="ea1b7-128">允許\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-128">Allowed\*</span></span>|<span data-ttu-id="ea1b7-129">允許\*</span><span class="sxs-lookup"><span data-stu-id="ea1b7-129">Allowed\*</span></span>|  
  
 <span data-ttu-id="ea1b7-130">\* 取消交易，而且交易內容的開啟控制代碼會失效。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-130">\* The transaction is canceled, and open handles for the transaction context are invalidated.</span></span> <span data-ttu-id="ea1b7-131">應用程式必須關閉所有開啟控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-131">The application must close all open handles.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ea1b7-132">範例</span><span class="sxs-lookup"><span data-stu-id="ea1b7-132">Examples</span></span>  
 <span data-ttu-id="ea1b7-133">下列範例會顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和 FILESTREAM Win32 存取如何造成衝突。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-133">The following examples show how [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and FILESTREAM Win32 access can cause conflicts.</span></span>  
  
### <a name="a-opening-a-filestream-blob-for-write-access"></a><span data-ttu-id="ea1b7-134">A.</span><span class="sxs-lookup"><span data-stu-id="ea1b7-134">A.</span></span> <span data-ttu-id="ea1b7-135">開啟 FILESTREAM BLOB 進行寫入存取</span><span class="sxs-lookup"><span data-stu-id="ea1b7-135">Opening a FILESTREAM BLOB for write access</span></span>  
 <span data-ttu-id="ea1b7-136">下列範例會顯示開啟檔案進行唯寫存取的作用。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-136">The following example shows the effect of opening a file for write access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, ...);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, ...).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### <a name="b-opening-a-filestream-blob-for-read-access"></a><span data-ttu-id="ea1b7-137">B.</span><span class="sxs-lookup"><span data-stu-id="ea1b7-137">B.</span></span> <span data-ttu-id="ea1b7-138">開啟 FILESTREAM BLOB 進行讀取存取</span><span class="sxs-lookup"><span data-stu-id="ea1b7-138">Opening a FILESTREAM BLOB for read access</span></span>  
 <span data-ttu-id="ea1b7-139">下列範例會顯示開啟檔案進行唯讀存取的作用。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-139">The following example shows the effect of opening a file for read access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="c-opening-and-closing-multiple-filestream-blob-files"></a><span data-ttu-id="ea1b7-140">C.</span><span class="sxs-lookup"><span data-stu-id="ea1b7-140">C.</span></span> <span data-ttu-id="ea1b7-141">開啟並關閉多個 FILESTREAM BLOB 檔案</span><span class="sxs-lookup"><span data-stu-id="ea1b7-141">Opening and closing multiple FILESTREAM BLOB files</span></span>  
 <span data-ttu-id="ea1b7-142">如果已開啟多個檔案，就會使用限制最嚴格的規則。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-142">If multiple files are open, the most restrictive rule is used.</span></span> <span data-ttu-id="ea1b7-143">下列範例會開啟兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-143">The following example opens two files.</span></span> <span data-ttu-id="ea1b7-144">第一個檔案會開啟以便讀取，而第二個檔案會開啟以便寫入。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-144">The first file is opened for read and the second for write.</span></span> <span data-ttu-id="ea1b7-145">在開啟第二個檔案之前，系統會拒絕 DML 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-145">DML statements will be denied until the second file is opened.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="d-failing-to-close-a-cursor"></a><span data-ttu-id="ea1b7-146">D.</span><span class="sxs-lookup"><span data-stu-id="ea1b7-146">D.</span></span> <span data-ttu-id="ea1b7-147">無法關閉資料指標</span><span class="sxs-lookup"><span data-stu-id="ea1b7-147">Failing to close a cursor</span></span>  
 <span data-ttu-id="ea1b7-148">下列範例會顯示未關閉的陳述式資料指標如何讓 `OpenSqlFilestream()` 無法開啟 BLOB 進行寫入存取。</span><span class="sxs-lookup"><span data-stu-id="ea1b7-148">The following example shows how a statement cursor that is not closed can prevent `OpenSqlFilestream()` from opening the BLOB for write access.</span></span>  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea1b7-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea1b7-149">See Also</span></span>  
 <span data-ttu-id="ea1b7-150">[使用 OpenSqlFilestream 存取 FILESTREAM 資料](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="ea1b7-150">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="ea1b7-151">使用 Multiple Active Result Set &#40;MARS&#41;</span><span class="sxs-lookup"><span data-stu-id="ea1b7-151">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](../native-client/features/using-multiple-active-result-sets-mars.md)  
  
  
