---
title: 使用 OpenSqlFilestream 存取 FILESTREAM 資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
api_name:
- OpenSqlFilestream
api_location:
- sqlncli11.dll
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1a1416c0104e07c7bd228a723192ecb35bbe9216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702998"
---
# <a name="access-filestream-data-with-opensqlfilestream"></a><span data-ttu-id="6c025-102">使用 OpenSqlFilestream 存取 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="6c025-102">Access FILESTREAM Data with OpenSqlFilestream</span></span>
  <span data-ttu-id="6c025-103">OpenSqlFilestream API 會針對儲存在檔案系統中的 FILESTREAM 二進位大型物件 (BLOB) ，取得 Win32 相容的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6c025-103">The OpenSqlFilestream API obtains a Win32 compatible file handle for a FILESTREAM binary large object (BLOB) that is stored in the file system.</span></span> <span data-ttu-id="6c025-104">此控制代碼可傳遞給下列任何 Win32 API：[ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422)、[WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423)、[TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424)、[SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425)、[SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426) 或 [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427)。</span><span class="sxs-lookup"><span data-stu-id="6c025-104">The handle can be passed to any of the following Win32 APIs: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427).</span></span> <span data-ttu-id="6c025-105">如果您將此控制代碼傳遞給其他任何 Win32 API，將會傳回錯誤 ERROR_ACCESS_DENIED。</span><span class="sxs-lookup"><span data-stu-id="6c025-105">If you pass this handle to any other Win32 API, the error ERROR_ACCESS_DENIED is returned.</span></span> <span data-ttu-id="6c025-106">在認可或回復交易之前，必須將此控制代碼傳遞給 Win32 的 [CloseHandle API](https://go.microsoft.com/fwlink/?LinkId=86428) 來關閉此控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6c025-106">The handle must be closed by passing it to the Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API before the transaction is committed or rolled back.</span></span> <span data-ttu-id="6c025-107">如果無法關閉此控制代碼，將會導致伺服器端資源洩露。</span><span class="sxs-lookup"><span data-stu-id="6c025-107">Failing to close the handle will cause server-side resource leaks.</span></span>  
  
 <span data-ttu-id="6c025-108">所有 FILESTREAM 資料容器存取都必須於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 異動中執行。</span><span class="sxs-lookup"><span data-stu-id="6c025-108">All FILESTREAM data container access must be performed in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="6c025-109">陳述式也可在同一交易中執行。</span><span class="sxs-lookup"><span data-stu-id="6c025-109">statements can also be executed in the same transaction.</span></span> <span data-ttu-id="6c025-110">以維護 SQL 資料與 FILESTREAM 資料之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="6c025-110">This maintains consistency between the SQL data and FILESTREAM BLOB data.</span></span>  
  
 <span data-ttu-id="6c025-111">若要使用 Win32 存取 FILESTREAM BLOB，必須啟用 [Windows 授權](../security/choose-an-authentication-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="6c025-111">To access the FILESTREAM BLOB by using Win32, [Windows Authorization](../security/choose-an-authentication-mode.md) must be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6c025-112">當檔案已針對寫入存取開啟時，FILESTREAM 代理程式就會擁有此交易。</span><span class="sxs-lookup"><span data-stu-id="6c025-112">When the file is opened for write access, the transaction is owned by the FILESTREAM agent.</span></span> <span data-ttu-id="6c025-113">在釋放交易之前，僅允許 Win32 檔案 I/O。</span><span class="sxs-lookup"><span data-stu-id="6c025-113">Only Win32 file I/O is allowed until the transaction is released.</span></span> <span data-ttu-id="6c025-114">若要釋放該異動，您必須關閉寫入控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6c025-114">To release the transaction, the write handle must be closed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c025-115">語法</span><span class="sxs-lookup"><span data-stu-id="6c025-115">Syntax</span></span>  
  
```  
  
  HANDLE OpenSqlFilestream (  
  LPCWSTR  
  FilestreamPath  
  ,  
  SQL_FILESTREAM_DESIRED_ACCESS  
  DesiredAccess,  
ULONGOpenOptions,LPBYTEFilestreamTransactionContext,SIZE_TFilestreamTransactionContextLength,PLARGE_INTEGERAllocationSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c025-116">參數</span><span class="sxs-lookup"><span data-stu-id="6c025-116">Parameters</span></span>  
 <span data-ttu-id="6c025-117">*FilestreamPath*</span><span class="sxs-lookup"><span data-stu-id="6c025-117">*FilestreamPath*</span></span>  
 <span data-ttu-id="6c025-118">在這是 PathName 函式所 `nvarchar(max)` 傳回的[PathName](/sql/relational-databases/system-functions/pathname-transact-sql)路徑。</span><span class="sxs-lookup"><span data-stu-id="6c025-118">[in] Is the `nvarchar(max)` path that is returned by the [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) function.</span></span> <span data-ttu-id="6c025-119">PathName 必須從具有 FILESTREAM 資料表與資料行之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT 或 UPDATE 權限的帳戶內容中呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c025-119">PathName must be called from the context of an account that has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT or UPDATE permissions on the FILESTREAM table and column.</span></span>  
  
 <span data-ttu-id="6c025-120">*DesiredAccess*</span><span class="sxs-lookup"><span data-stu-id="6c025-120">*DesiredAccess*</span></span>  
 <span data-ttu-id="6c025-121">[in] 設定用來存取 FILESTREAM BLOB 資料的模式。</span><span class="sxs-lookup"><span data-stu-id="6c025-121">[in] Sets the mode used to access FILESTREAM BLOB data.</span></span> <span data-ttu-id="6c025-122">此值會傳遞給 [DeviceIoControl 函式](https://go.microsoft.com/fwlink/?LinkId=105527)。</span><span class="sxs-lookup"><span data-stu-id="6c025-122">This value is passed to the [DeviceIoControl Function](https://go.microsoft.com/fwlink/?LinkId=105527).</span></span>  
  
|<span data-ttu-id="6c025-123">名稱</span><span class="sxs-lookup"><span data-stu-id="6c025-123">Name</span></span>|<span data-ttu-id="6c025-124">值</span><span class="sxs-lookup"><span data-stu-id="6c025-124">Value</span></span>|<span data-ttu-id="6c025-125">意義</span><span class="sxs-lookup"><span data-stu-id="6c025-125">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="6c025-126">SQL_FILESTREAM_READ</span><span class="sxs-lookup"><span data-stu-id="6c025-126">SQL_FILESTREAM_READ</span></span>|<span data-ttu-id="6c025-127">0</span><span class="sxs-lookup"><span data-stu-id="6c025-127">0</span></span>|<span data-ttu-id="6c025-128">資料可以從檔案讀取。</span><span class="sxs-lookup"><span data-stu-id="6c025-128">Data can be read from the file.</span></span>|  
|<span data-ttu-id="6c025-129">SQL_FILESTREAM_WRITE</span><span class="sxs-lookup"><span data-stu-id="6c025-129">SQL_FILESTREAM_WRITE</span></span>|<span data-ttu-id="6c025-130">1</span><span class="sxs-lookup"><span data-stu-id="6c025-130">1</span></span>|<span data-ttu-id="6c025-131">資料可以寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="6c025-131">Data can be written to the file.</span></span>|  
|<span data-ttu-id="6c025-132">SQL_FILESTREAM_READWRITE</span><span class="sxs-lookup"><span data-stu-id="6c025-132">SQL_FILESTREAM_READWRITE</span></span>|<span data-ttu-id="6c025-133">2</span><span class="sxs-lookup"><span data-stu-id="6c025-133">2</span></span>|<span data-ttu-id="6c025-134">資料可以寫入檔案和從檔案讀取。</span><span class="sxs-lookup"><span data-stu-id="6c025-134">Data can be read and written from the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="6c025-135">這些值會定義在 sqlncli.h 中的 SQL_FILESTREAM_DESIRED_ACCESS 列舉內。</span><span class="sxs-lookup"><span data-stu-id="6c025-135">These values are defined in the SQL_FILESTREAM_DESIRED_ACCESS enumeration in sqlncli.h.</span></span>  
  
 <span data-ttu-id="6c025-136">*OpenOptions*</span><span class="sxs-lookup"><span data-stu-id="6c025-136">*OpenOptions*</span></span>  
 <span data-ttu-id="6c025-137">[in] 檔案屬性和旗標。</span><span class="sxs-lookup"><span data-stu-id="6c025-137">[in] The file attributes and flags.</span></span> <span data-ttu-id="6c025-138">這個參數也可以包含下列旗標的任意組合。</span><span class="sxs-lookup"><span data-stu-id="6c025-138">This parameter can also include any combination of the following flags.</span></span>  
  
|<span data-ttu-id="6c025-139">旗標</span><span class="sxs-lookup"><span data-stu-id="6c025-139">Flag</span></span>|<span data-ttu-id="6c025-140">值</span><span class="sxs-lookup"><span data-stu-id="6c025-140">Value</span></span>|<span data-ttu-id="6c025-141">意義</span><span class="sxs-lookup"><span data-stu-id="6c025-141">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="6c025-142">SQL_FILESTREAM_OPEN_NONE</span><span class="sxs-lookup"><span data-stu-id="6c025-142">SQL_FILESTREAM_OPEN_NONE</span></span>|<span data-ttu-id="6c025-143">0x00000000:</span><span class="sxs-lookup"><span data-stu-id="6c025-143">0x00000000:</span></span>|<span data-ttu-id="6c025-144">開啟或建立這個檔案時，不搭配任何特殊選項。</span><span class="sxs-lookup"><span data-stu-id="6c025-144">The file is being opened or created with no special options.</span></span>|  
|<span data-ttu-id="6c025-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span><span class="sxs-lookup"><span data-stu-id="6c025-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span></span>|<span data-ttu-id="6c025-146">0x00000001L</span><span class="sxs-lookup"><span data-stu-id="6c025-146">0x00000001L</span></span>|<span data-ttu-id="6c025-147">開啟或建立這個檔案是為了非同步 I/O。</span><span class="sxs-lookup"><span data-stu-id="6c025-147">The file is being opened or created for asynchronous I/O.</span></span>|  
|<span data-ttu-id="6c025-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span><span class="sxs-lookup"><span data-stu-id="6c025-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span></span>|<span data-ttu-id="6c025-149">0x00000002L</span><span class="sxs-lookup"><span data-stu-id="6c025-149">0x00000002L</span></span>|<span data-ttu-id="6c025-150">系統藉由不使用任何系統快取來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="6c025-150">The system opens the file by using no system caching.</span></span>|  
|<span data-ttu-id="6c025-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span><span class="sxs-lookup"><span data-stu-id="6c025-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span></span>|<span data-ttu-id="6c025-152">0x00000004L</span><span class="sxs-lookup"><span data-stu-id="6c025-152">0x00000004L</span></span>|<span data-ttu-id="6c025-153">系統不會透過中繼快取來寫入。</span><span class="sxs-lookup"><span data-stu-id="6c025-153">The system does not write through an intermediate cache.</span></span> <span data-ttu-id="6c025-154">會直接寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="6c025-154">Writes go directly to disk.</span></span>|  
|<span data-ttu-id="6c025-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span><span class="sxs-lookup"><span data-stu-id="6c025-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span></span>|<span data-ttu-id="6c025-156">0x00000008L</span><span class="sxs-lookup"><span data-stu-id="6c025-156">0x00000008L</span></span>|<span data-ttu-id="6c025-157">按順序從開頭至結尾存取檔案。</span><span class="sxs-lookup"><span data-stu-id="6c025-157">A file is accessed sequentially from beginning to end.</span></span> <span data-ttu-id="6c025-158">系統可使用這個做為最佳化檔案快取的提示。</span><span class="sxs-lookup"><span data-stu-id="6c025-158">The system can use this as a hint to optimize file caching.</span></span> <span data-ttu-id="6c025-159">如果應用程式藉移動檔案指標來進行隨機存取，則可能不會發生最佳快取。</span><span class="sxs-lookup"><span data-stu-id="6c025-159">If an application moves the file pointer for random access, optimal caching may not occur.</span></span>|  
|<span data-ttu-id="6c025-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span><span class="sxs-lookup"><span data-stu-id="6c025-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span></span>|<span data-ttu-id="6c025-161">0x00000010L</span><span class="sxs-lookup"><span data-stu-id="6c025-161">0x00000010L</span></span>|<span data-ttu-id="6c025-162">隨機存取檔案。</span><span class="sxs-lookup"><span data-stu-id="6c025-162">A file is accessed randomly.</span></span> <span data-ttu-id="6c025-163">系統可使用這個做為最佳化檔案快取的提示。</span><span class="sxs-lookup"><span data-stu-id="6c025-163">The system can use this as a hint to optimize file caching.</span></span>|  
  
 <span data-ttu-id="6c025-164">*FilestreamTransactionContext*</span><span class="sxs-lookup"><span data-stu-id="6c025-164">*FilestreamTransactionContext*</span></span>  
 <span data-ttu-id="6c025-165">[in] 此值由 [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) 函式傳回。</span><span class="sxs-lookup"><span data-stu-id="6c025-165">[in] The value that is returned by the [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) function.</span></span>  
  
 <span data-ttu-id="6c025-166">*FilestreamTransactionContextLength*</span><span class="sxs-lookup"><span data-stu-id="6c025-166">*FilestreamTransactionContextLength*</span></span>  
 <span data-ttu-id="6c025-167">[in] `varbinary(max)` 中由 GET_FILESTREAM_TRANSACTION_CONTEXT 函數傳回之資料的位元組數。</span><span class="sxs-lookup"><span data-stu-id="6c025-167">[in] Number of bytes in the `varbinary(max)` data that is returned by the GET_FILESTREAM_TRANSACTION_CONTEXT function.</span></span> <span data-ttu-id="6c025-168">此函數會傳回 N 個位元組的陣列。</span><span class="sxs-lookup"><span data-stu-id="6c025-168">The function returns an array of N bytes.</span></span> <span data-ttu-id="6c025-169">N 是由此函數所決定，而且是所傳回之位元組陣列的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c025-169">N is determined by the function and is a property of the byte array that is returned.</span></span>  
  
 <span data-ttu-id="6c025-170">*AllocationSize*</span><span class="sxs-lookup"><span data-stu-id="6c025-170">*AllocationSize*</span></span>  
 <span data-ttu-id="6c025-171">[in] 指定資料檔的初始配置大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="6c025-171">[in] Specifies the initial allocation size of the data file in bytes.</span></span> <span data-ttu-id="6c025-172">在讀取模式下將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6c025-172">It is ignored in read mode.</span></span> <span data-ttu-id="6c025-173">這個參數可以是 NULL，此時會使用預設檔案系統行為。</span><span class="sxs-lookup"><span data-stu-id="6c025-173">This parameter can be NULL, in which case the default file system behavior is used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c025-174">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c025-174">Return Value</span></span>  
 <span data-ttu-id="6c025-175">如果此函數成功，傳回值就是指定之檔案的開啟控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6c025-175">If the function succeeds, the return value is an open handle to a specified file.</span></span> <span data-ttu-id="6c025-176">如果此函數失敗，傳回值就是 INVALID_HANDLE_VALUE。</span><span class="sxs-lookup"><span data-stu-id="6c025-176">If the function fails, the return value is INVALID_HANDLE_VALUE.</span></span> <span data-ttu-id="6c025-177">如需更多的錯誤資訊，可呼叫 GetLastError()。</span><span class="sxs-lookup"><span data-stu-id="6c025-177">For extended error information, call GetLastError().</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6c025-178">範例</span><span class="sxs-lookup"><span data-stu-id="6c025-178">Examples</span></span>  
 <span data-ttu-id="6c025-179">下列範例將示範如何使用 `OpenSqlFilestream` API 來取得 Win32 控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6c025-179">The following examples show you how to use the `OpenSqlFilestream` API to obtain a Win32 handle.</span></span>  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
## <a name="remarks"></a><span data-ttu-id="6c025-180">備註</span><span class="sxs-lookup"><span data-stu-id="6c025-180">Remarks</span></span>  
 <span data-ttu-id="6c025-181">必須安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，才能使用此 API。</span><span class="sxs-lookup"><span data-stu-id="6c025-181">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client must be installed to use this API.</span></span> <span data-ttu-id="6c025-182">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端工具一起安裝。</span><span class="sxs-lookup"><span data-stu-id="6c025-182">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client tools.</span></span> <span data-ttu-id="6c025-183">如需詳細資訊，請參閱 [安裝 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="6c025-183">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c025-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c025-184">See Also</span></span>  
 <span data-ttu-id="6c025-185">[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c025-185">[Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span></span>  
 <span data-ttu-id="6c025-186">[對 FILESTREAM 資料進行部分更新](make-partial-updates-to-filestream-data.md) </span><span class="sxs-lookup"><span data-stu-id="6c025-186">[Make Partial Updates to FILESTREAM Data](make-partial-updates-to-filestream-data.md) </span></span>  
 [<span data-ttu-id="6c025-187">避免與 FILESTREAM 應用程式中的資料庫作業相衝突</span><span class="sxs-lookup"><span data-stu-id="6c025-187">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
