---
title: 建立啟用 FILESTREAM 的資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fe6e5bc6e4f60bc0703482f3bf4d761104b3c5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701236"
---
# <a name="create-a-filestream-enabled-database"></a><span data-ttu-id="76ddd-102">建立啟用 FILESTREAM 的資料庫</span><span class="sxs-lookup"><span data-stu-id="76ddd-102">Create a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="76ddd-103">此主題說明如何建立支援 FILESTREAM 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="76ddd-103">This topic shows how to create a database that supports FILESTREAM.</span></span> <span data-ttu-id="76ddd-104">因為 FILESTREAM 使用特殊類型的檔案群組，所以當您在建立資料庫時，至少必須針對一個檔案群組指定 CONTAINS FILESTREAM 子句。</span><span class="sxs-lookup"><span data-stu-id="76ddd-104">Because FILESTREAM uses a special type of filegroup, when you create the database, you must specify the CONTAINS FILESTREAM clause for at least one filegroup.</span></span>  
  
 <span data-ttu-id="76ddd-105">FILESTREAM 檔案群組可以包含多個檔案。</span><span class="sxs-lookup"><span data-stu-id="76ddd-105">A FILESTREAM filegroup can contain more than one file.</span></span> <span data-ttu-id="76ddd-106">如需示範如何建立包含多個檔案之 FILESTREAM 檔案群組的程式碼範例，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="76ddd-106">For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
### <a name="to-create-a-filestream-enabled-database"></a><span data-ttu-id="76ddd-107">建立啟用 FILESTREAM 的資料庫</span><span class="sxs-lookup"><span data-stu-id="76ddd-107">To create a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="76ddd-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，按一下 **[新增查詢]** 顯示 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="76ddd-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="76ddd-109">複製 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼會建立稱為 Archive 的啟用 FILESTREAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="76ddd-109">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled database called Archive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76ddd-110">在這個指令碼中，目錄 C:\Data 必須存在。</span><span class="sxs-lookup"><span data-stu-id="76ddd-110">For this script, the directory C:\Data must exist.</span></span>  
  
3.  <span data-ttu-id="76ddd-111">若要建立資料庫，請按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="76ddd-111">To build the database, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ddd-112">範例</span><span class="sxs-lookup"><span data-stu-id="76ddd-112">Example</span></span>  
 <span data-ttu-id="76ddd-113">下列程式碼範例會建立名為 `Archive`的資料庫。</span><span class="sxs-lookup"><span data-stu-id="76ddd-113">The following code example creates a database that is named `Archive`.</span></span> <span data-ttu-id="76ddd-114">此資料庫包含三個檔案群組： `PRIMARY`、 `Arch1`和 `FileStreamGroup1`。</span><span class="sxs-lookup"><span data-stu-id="76ddd-114">The database contains three filegroups: `PRIMARY`, `Arch1`, and `FileStreamGroup1`.</span></span> <span data-ttu-id="76ddd-115">`PRIMARY` 和 `Arch1` 是一般的檔案群組，不能包含 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="76ddd-115">`PRIMARY` and `Arch1` are regular filegroups that cannot contain FILESTREAM data.</span></span> <span data-ttu-id="76ddd-116">`FileStreamGroup1` 則為 `FILESTREAM` 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="76ddd-116">`FileStreamGroup1` is the `FILESTREAM` filegroup.</span></span>  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 <span data-ttu-id="76ddd-117">如為 `FILESTREAM` 檔案群組，則 `FILENAME` 就是指路徑。</span><span class="sxs-lookup"><span data-stu-id="76ddd-117">For a `FILESTREAM` filegroup, `FILENAME` refers to a path.</span></span> <span data-ttu-id="76ddd-118">到最後一個資料夾為止的路徑必須存在，而最後一個資料夾則不得存在。</span><span class="sxs-lookup"><span data-stu-id="76ddd-118">The path up to the last folder must exist, and the last folder must not exist.</span></span> <span data-ttu-id="76ddd-119">在這個範例中， `c:\data` 必須存在。</span><span class="sxs-lookup"><span data-stu-id="76ddd-119">In this example, `c:\data` must exist.</span></span> <span data-ttu-id="76ddd-120">不過，當您執行 `filestream1` 陳述式時，不能存在 `CREATE DATABASE` 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="76ddd-120">However, the `filestream1` subfolder cannot exist when you execute the `CREATE DATABASE` statement.</span></span> <span data-ttu-id="76ddd-121">如需此語法的詳細資訊，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="76ddd-121">For more information about the syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
 <span data-ttu-id="76ddd-122">在您執行上述範例之後，filestream.hdr 檔案和 $FSLOG 資料夾就會出現在 c:\Data\filestream1 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="76ddd-122">After you run the previous example, a filestream.hdr file and an $FSLOG folder appears in the c:\Data\filestream1 folder.</span></span> <span data-ttu-id="76ddd-123">filestream.hdr 檔案是 FILESTREAM 容器的標頭檔案。</span><span class="sxs-lookup"><span data-stu-id="76ddd-123">The filestream.hdr file is a header file for the FILESTREAM container.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="76ddd-124">filestream.hdr 檔案是一個重要的系統檔案，</span><span class="sxs-lookup"><span data-stu-id="76ddd-124">The filestream.hdr file is an important system file.</span></span> <span data-ttu-id="76ddd-125">它包含了 FILESTREAM 標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="76ddd-125">It contains FILESTREAM header information.</span></span> <span data-ttu-id="76ddd-126">請勿移除或修改這個檔案。</span><span class="sxs-lookup"><span data-stu-id="76ddd-126">Do not remove or modify this file.</span></span>  
  
 <span data-ttu-id="76ddd-127">針對現有的資料庫，您可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式來加入 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="76ddd-127">For existing databases, you can use the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to add a FILESTREAM filegroup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ddd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76ddd-128">See Also</span></span>  
 <span data-ttu-id="76ddd-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76ddd-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="76ddd-130">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="76ddd-130">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
