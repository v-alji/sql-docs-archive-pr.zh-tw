---
title: 使用 Transact-SQL 存取 FILESTREAM 資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06d395f1acc3723fc6b45fdfa08efbae354d8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703001"
---
# <a name="access-filestream-data-with-transact-sql"></a><span data-ttu-id="424b8-102">使用 Transact-SQL 存取 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="424b8-102">Access FILESTREAM Data with Transact-SQL</span></span>
  <span data-ttu-id="424b8-103">本主題描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT、UPDATE 及 DELETE 陳述式來管理 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="424b8-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE, and DELETE statements to manage FILESTREAM data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="424b8-104">本主題中的範例需要使用在 [建立啟用 FILESTREAM 的資料庫](create-a-filestream-enabled-database.md) 和 [建立儲存 FILESTREAM 資料的資料表](create-a-table-for-storing-filestream-data.md)中建立之啟用 FILESTREAM 的資料庫和資料表。</span><span class="sxs-lookup"><span data-stu-id="424b8-104">The examples in this topic require the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
##  <a name="inserting-a-row-that-contains-filestream-data"></a><a name="ins"></a> <span data-ttu-id="424b8-105">插入包含 FILESTREAM 資料的資料列</span><span class="sxs-lookup"><span data-stu-id="424b8-105">Inserting a Row That Contains FILESTREAM Data</span></span>  
 <span data-ttu-id="424b8-106">若要將資料列加入至支援 FILESTREAM 資料的資料表，請使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="424b8-106">To add a row to a table that supports FILESTREAM data, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span> <span data-ttu-id="424b8-107">當您將資料插入 FILESTREAM 資料行時，可以插入 NULL 或 `varbinary(max)` 值。</span><span class="sxs-lookup"><span data-stu-id="424b8-107">When you insert data into a FILESTREAM column, you can insert NULL or a `varbinary(max)` value.</span></span>  
  
### <a name="inserting-null"></a><span data-ttu-id="424b8-108">插入 NULL</span><span class="sxs-lookup"><span data-stu-id="424b8-108">Inserting NULL</span></span>  
 <span data-ttu-id="424b8-109">下列範例將示範如何插入 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="424b8-109">The following example shows how to insert `NULL`.</span></span> <span data-ttu-id="424b8-110">當 FILESTREAM 值為 `NULL`時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 就不會在檔案系統中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="424b8-110">When the FILESTREAM value is `NULL`, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not create a file in the file system.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertnull)]  
  
### <a name="inserting-a-zero-length-record"></a><span data-ttu-id="424b8-111">插入長度為零的記錄</span><span class="sxs-lookup"><span data-stu-id="424b8-111">Inserting a Zero-Length Record</span></span>  
 <span data-ttu-id="424b8-112">下列範例將示範如何使用 `INSERT` 來建立長度為零的記錄。</span><span class="sxs-lookup"><span data-stu-id="424b8-112">The following example shows how to use `INSERT` to create a zero-length record.</span></span> <span data-ttu-id="424b8-113">當您想要取得檔案控制代碼，但是將要使用 Win32 API 操作檔案時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="424b8-113">This is useful for when you want to obtain a file handle, but will be manipulating the file by using Win32 APIs.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertzero)]  
  
### <a name="creating-a-data-file"></a><span data-ttu-id="424b8-114">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="424b8-114">Creating a Data File</span></span>  
 <span data-ttu-id="424b8-115">下列範例將示範如何使用 `INSERT` 來建立包含資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="424b8-115">The following example shows how to use `INSERT` to create a file that contains data.</span></span> <span data-ttu-id="424b8-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將 `Seismic Data` 字串轉換成 `varbinary(max)` 值。</span><span class="sxs-lookup"><span data-stu-id="424b8-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] converts the string `Seismic Data` to a `varbinary(max)` value.</span></span> <span data-ttu-id="424b8-117">FILESTREAM 會建立此 Windows 檔案 (如果不存在的話)，然後資料會加入到此資料檔中。</span><span class="sxs-lookup"><span data-stu-id="424b8-117">FILESTREAM creates the Windows file if it does not already exist.The data is then added to the data file.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertdata)]  
  
 <span data-ttu-id="424b8-118">當您從 `Archive`.`dbo.Records`</span><span class="sxs-lookup"><span data-stu-id="424b8-118">When you select all data from the `Archive`.`dbo.Records`</span></span> <span data-ttu-id="424b8-119">資料表中選取所有資料時，其結果與下表所顯示的結果很相似。</span><span class="sxs-lookup"><span data-stu-id="424b8-119">table, the results are similar to the results that are shown in the following table.</span></span> <span data-ttu-id="424b8-120">不過， `Id` 資料行將包含不同的 GUID。</span><span class="sxs-lookup"><span data-stu-id="424b8-120">However, the `Id` column will contain different GUIDs.</span></span>  
  
|<span data-ttu-id="424b8-121">Id</span><span class="sxs-lookup"><span data-stu-id="424b8-121">Id</span></span>|<span data-ttu-id="424b8-122">SerialNumber</span><span class="sxs-lookup"><span data-stu-id="424b8-122">SerialNumber</span></span>|<span data-ttu-id="424b8-123">繼續</span><span class="sxs-lookup"><span data-stu-id="424b8-123">Resume</span></span>|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
##  <a name="updating-filestream-data"></a><a name="upd"></a> <span data-ttu-id="424b8-124">更新 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="424b8-124">Updating FILESTREAM Data</span></span>  
 <span data-ttu-id="424b8-125">您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 來更新檔案系統檔案中的資料。不過，當您必須將大量資料串流處理至檔案時，可能不會想要這樣做。</span><span class="sxs-lookup"><span data-stu-id="424b8-125">You can use [!INCLUDE[tsql](../../includes/tsql-md.md)] to update the data in the file system file; although, you might not want to do this when you have to stream large amounts of data to a file.</span></span>  
  
 <span data-ttu-id="424b8-126">下列範例會以文字 `Xray 1`來取代檔案記錄中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="424b8-126">The following example replaces any text in the file record with the text `Xray 1`.</span></span>  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_updatedata)]  
  
##  <a name="deleting-filestream-data"></a><a name="del"></a> <span data-ttu-id="424b8-127">刪除 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="424b8-127">Deleting FILESTREAM Data</span></span>  
 <span data-ttu-id="424b8-128">當您刪除包含 FILESTREAM 欄位的資料列時，您也會刪除其基礎檔案系統的檔案。</span><span class="sxs-lookup"><span data-stu-id="424b8-128">When you delete a row that contains a FILESTREAM field, you also delete its underlying file system files.</span></span> <span data-ttu-id="424b8-129">因此，刪除資料列與檔案的唯一方法，是使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="424b8-129">The only way to delete a row, and therefore the file, is to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span>  
  
 <span data-ttu-id="424b8-130">下列範例將示範如何刪除資料列及相關聯的檔案系統檔案。</span><span class="sxs-lookup"><span data-stu-id="424b8-130">The following example shows how to delete a row and its associated file system files.</span></span>  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_deletedata)]  
  
 <span data-ttu-id="424b8-131">當您從 `dbo.Archive` 資料表中選取所有資料時，此資料列就會消失。</span><span class="sxs-lookup"><span data-stu-id="424b8-131">When you select all data from the `dbo.Archive` table, the row is gone.</span></span> <span data-ttu-id="424b8-132">您無法再使用相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="424b8-132">You can no longer use the associated file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="424b8-133">基礎檔案會由 FILESTREAM 記憶體回收行程所移除。</span><span class="sxs-lookup"><span data-stu-id="424b8-133">The underlying files are removed by the FILESTREAM garbage collector.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424b8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="424b8-134">See Also</span></span>  
 <span data-ttu-id="424b8-135">[啟用及設定 FILESTREAM](enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="424b8-135">[Enable and Configure FILESTREAM](enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="424b8-136">避免與 FILESTREAM 應用程式中的資料庫作業相衝突</span><span class="sxs-lookup"><span data-stu-id="424b8-136">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
