---
title: 檢視資料庫快照集的疏鬆檔案大小 (Transact-SQL) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704142"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a><span data-ttu-id="ddddf-102">檢視資料庫快照集的疏鬆檔案大小 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddddf-102">View the Size of the Sparse File of a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="ddddf-103">此主題描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 來確認 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫檔案是疏鬆檔案，以及了解其實際和最大大小。</span><span class="sxs-lookup"><span data-stu-id="ddddf-103">This topic describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to verify that a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database file is a sparse file and to find out its actual and maximum sizes.</span></span> <span data-ttu-id="ddddf-104">疏鬆檔案是 NTFS 檔案系統的功能，提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫快照集所使用。</span><span class="sxs-lookup"><span data-stu-id="ddddf-104">Sparse files, which are a feature of the NTFS file system, are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshots.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddddf-105">資料庫快照集建立期間，可以利用 CREATE DATABASE 陳述式中的檔案名稱，建立疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="ddddf-105">During database snapshot creation, sparse files are created by using the file names in the CREATE DATABASE statement.</span></span> <span data-ttu-id="ddddf-106">這些檔案名稱儲存在 **physical_name** 資料行的 **sys.master_files** 中。</span><span class="sxs-lookup"><span data-stu-id="ddddf-106">These file names are stored in **sys.master_files** in the **physical_name** column.</span></span> <span data-ttu-id="ddddf-107">在 **sys.database_files** (不管是在來源資料庫或快照集) 中， **physical_name** 資料行一律會包含來源資料庫檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddddf-107">In **sys.database_files** (whether in the source database or in a snapshot), the **physical_name** column always contains the names of the source database files.</span></span>  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a><span data-ttu-id="ddddf-108">確認資料庫檔案是疏鬆檔案</span><span class="sxs-lookup"><span data-stu-id="ddddf-108">Verify that a Database File is a Sparse File</span></span>  
  
1.  <span data-ttu-id="ddddf-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體上：</span><span class="sxs-lookup"><span data-stu-id="ddddf-109">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="ddddf-110">從資料庫快照集的 **sys.database_files** 或從 **sys.master_files** 選取 **is_sparse**資料行。</span><span class="sxs-lookup"><span data-stu-id="ddddf-110">Select the **is_sparse** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="ddddf-111">值表示檔案是否為疏鬆檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ddddf-111">The value indicates whether the file is a sparse file, as follows:</span></span>  
  
     <span data-ttu-id="ddddf-112">1 = 檔案是疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="ddddf-112">1 = File is a sparse file.</span></span>  
  
     <span data-ttu-id="ddddf-113">0 = 檔案不是疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="ddddf-113">0 = File is not a sparse file.</span></span>  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a><span data-ttu-id="ddddf-114">查明疏鬆檔案的實際大小</span><span class="sxs-lookup"><span data-stu-id="ddddf-114">Find Out the Actual Size of a Sparse File</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddddf-115">疏鬆檔案是以每次遞增 64 KB 的方式成長；因此磁碟上的疏鬆檔案大小一律是 64 KB 的倍數。</span><span class="sxs-lookup"><span data-stu-id="ddddf-115">Sparse files grow in 64-kilobyte (KB) increments; thus, the size of a sparse file on disk is always a multiple of 64 KB.</span></span>  
  
 <span data-ttu-id="ddddf-116">若要查看快照集的每個稀疏檔案目前在磁片上使用的位元組數目，請查詢**size_on_disk_bytes** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql)動態管理檢視的 [size_on_disk_bytes] 資料行。</span><span class="sxs-lookup"><span data-stu-id="ddddf-116">To view the number of bytes that each sparse file of a snapshot is currently using on disk, query the **size_on_disk_bytes** column of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][sys.dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) dynamic management view.</span></span>  
  
 <span data-ttu-id="ddddf-117">若要檢視疏鬆檔案使用的磁碟空間，請以滑鼠右鍵按一下 Microsoft Windows 中的檔案，然後按一下 [內容]並查看 [磁碟大小] 值。</span><span class="sxs-lookup"><span data-stu-id="ddddf-117">To view the disk space used by a sparse file, right-click the file in Microsoft Windows, click **Properties**, and look at the **Size on disk** value.</span></span>  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a><span data-ttu-id="ddddf-118">查明疏鬆檔案的大小上限</span><span class="sxs-lookup"><span data-stu-id="ddddf-118">Find Out the Maximum Size of a Sparse File</span></span>  
 <span data-ttu-id="ddddf-119">疏鬆檔案的成長大小上限，為建立快照集時對應來源資料庫檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="ddddf-119">The maximum size to which a sparse can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span> <span data-ttu-id="ddddf-120">若要知道此大小，您可以使用以下其中一種方式：</span><span class="sxs-lookup"><span data-stu-id="ddddf-120">To learn this size, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="ddddf-121">使用 Windows 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="ddddf-121">Using Windows Command Prompt:</span></span>  
  
    1.  <span data-ttu-id="ddddf-122">使用 Windows **dir** 命令。</span><span class="sxs-lookup"><span data-stu-id="ddddf-122">Use Windows **dir** commands.</span></span>  
  
    2.  <span data-ttu-id="ddddf-123">選取疏鬆檔案，在 Windows 中開啟該檔案的 **[內容]** 對話方塊，並查看 **[大小]** 的值。</span><span class="sxs-lookup"><span data-stu-id="ddddf-123">Select the sparse file, open the file **Properties** dialog box in Windows, and look at the **Size** value.</span></span>  
  
-   <span data-ttu-id="ddddf-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體上：</span><span class="sxs-lookup"><span data-stu-id="ddddf-124">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="ddddf-125">從資料庫快照集的 **sys.database_files** 或從 **sys.master_files** 選取 **size**資料行。</span><span class="sxs-lookup"><span data-stu-id="ddddf-125">Select the **size** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="ddddf-126">在 SQL 頁面中， **size** 資料行的值會反映出快照集可以使用的空間上限；此數值相當於 Windows 的 **[大小]** 欄位，只不過它代表檔案中的 SQL 頁面數；以位元組計算的大小如下：</span><span class="sxs-lookup"><span data-stu-id="ddddf-126">The value of **size** column reflects the maximum space, in SQL pages, that the snapshot can ever use; this value is equivalent to the Windows **Size** field, except that it is represented in terms of the number of SQL pages in the file; the size in bytes is:</span></span>  
  
     <span data-ttu-id="ddddf-127">( *頁數* \* 8192)</span><span class="sxs-lookup"><span data-stu-id="ddddf-127">( *number_of_pages* \* 8192)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddddf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddddf-128">See Also</span></span>  
 <span data-ttu-id="ddddf-129">[資料庫快照集 &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddddf-129">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="ddddf-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddddf-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span></span>  
 <span data-ttu-id="ddddf-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ddddf-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 [<span data-ttu-id="ddddf-132">sys.master_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ddddf-132">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
