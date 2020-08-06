---
title: 使用卸離與附加移動資料庫 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- moving databases [SQL Server]
- database detaching [SQL Server]
- relocating databases [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 768a70dfe94af6f8d65f7c76fa08d3dff650fe7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606867"
---
# <a name="move-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="a4997-102">使用卸離與附加移動資料庫 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a4997-102">Move a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="a4997-103">此主題描述如何將卸離的資料庫移動到另一個位置，再重新附加到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中相同或不同的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4997-103">This topic describes how to move a detached database to another location and re-attach it to the same or a different server instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a4997-104">不過，建議您使用 ALTER DATABASE 計畫的重新放置程序來移動資料庫，而不要使用卸離和附加。</span><span class="sxs-lookup"><span data-stu-id="a4997-104">However, we recommend that you move databases by using the ALTER DATABASE planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="a4997-105">如需詳細資訊，請參閱 [移動使用者資料庫](move-user-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="a4997-105">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4997-106">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4997-106">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="a4997-107">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4997-107">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="a4997-108">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4997-108">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a4997-109">程序</span><span class="sxs-lookup"><span data-stu-id="a4997-109">Procedure</span></span>  
  
#### <a name="to-move-a-database-by-using-detach-and-attach"></a><span data-ttu-id="a4997-110">透過使用卸離和附加來移動資料庫</span><span class="sxs-lookup"><span data-stu-id="a4997-110">To move a database by using detach and attach</span></span>  
  
1.  <span data-ttu-id="a4997-111">卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4997-111">Detach the database.</span></span> <span data-ttu-id="a4997-112">如需詳細資訊，請參閱 [卸離資料庫](detach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a4997-112">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="a4997-113">在 Windows 檔案總管或 Windows 的 [命令提示字元] 視窗中，將卸離的資料庫檔案和記錄檔移動到新位置。</span><span class="sxs-lookup"><span data-stu-id="a4997-113">In a Windows Explorer or Windows Command Prompt window, move the detached database file or files and log file or files to the new location.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4997-114">若要移動單一檔案的資料庫，且檔案小到可以容納在電子郵件中，您可以利用電子郵件來移動。</span><span class="sxs-lookup"><span data-stu-id="a4997-114">To move a single-file database, you can use email if the file size is small enough for email to accommodate.</span></span>  
  
     <span data-ttu-id="a4997-115">即使您想要建立新的記錄檔，也應該一併移動記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4997-115">You should move the log files even if you intend to create new log files.</span></span> <span data-ttu-id="a4997-116">在某些情況下，重新附加資料庫需要其現有的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4997-116">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="a4997-117">因此，一律保留所有卸離的記錄檔，直到資料庫在沒有這些檔案的情形下成功附加為止。</span><span class="sxs-lookup"><span data-stu-id="a4997-117">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4997-118">如果您嘗試在不指定記錄檔的情形下附加資料庫，附加作業會在其原始位置中尋找記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4997-118">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="a4997-119">如果原始位置中仍有記錄的副本存在，則會附加該副本。</span><span class="sxs-lookup"><span data-stu-id="a4997-119">If a copy of the log still exists in the original location, that copy is attached.</span></span> <span data-ttu-id="a4997-120">若要避免使用原始記錄檔，請指定新記錄檔的路徑，或者移除記錄檔的原始副本 (在將記錄檔複製到新位置後)。</span><span class="sxs-lookup"><span data-stu-id="a4997-120">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="a4997-121">附加複製的檔案。</span><span class="sxs-lookup"><span data-stu-id="a4997-121">Attach the copied files.</span></span> <span data-ttu-id="a4997-122">如需詳細資訊，請參閱 [Attach a Database](attach-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="a4997-122">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4997-123">範例</span><span class="sxs-lookup"><span data-stu-id="a4997-123">Example</span></span>  
 <span data-ttu-id="a4997-124">下列範例 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] 會在 [查詢編輯器] 視窗中執行語句的複本，並連接到附加的伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="a4997-124">The following example creates a copy of the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="a4997-125">卸離 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] 語句：</span><span class="sxs-lookup"><span data-stu-id="a4997-125">Detach the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  <span data-ttu-id="a4997-126">使用您選擇的方法，將資料庫檔案 (AdventureWorks208R2_Data.mdf 和 AdventureWorks208R2_log) 分別複製到：C:\MySQLServer\AdventureWorks208R2_Data.mdf 和 C:\MySQLServer\AdventureWorks208R2_Log.ldf。</span><span class="sxs-lookup"><span data-stu-id="a4997-126">Using the method of your choice, copy the database files (AdventureWorks208R2_Data.mdf and AdventureWorks208R2_log) to: C:\MySQLServer\AdventureWorks208R2_Data.mdf and C:\MySQLServer\AdventureWorks208R2_Log.ldf, respectively.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a4997-127">針對實際執行的資料庫，將資料庫與交易記錄放在不同的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="a4997-127">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="a4997-128">若要經由網路將檔案複製到遠端電腦的磁碟，請使用遠端位置的通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="a4997-128">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="a4997-129">UNC 名稱的格式為 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_。</span><span class="sxs-lookup"><span data-stu-id="a4997-129">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="a4997-130">如同將檔案寫入本機硬碟一樣，您必須將在遠端磁碟讀取或寫入檔案所需的適當權限，授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體所用的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4997-130">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="a4997-131">若要附加已移動的資料庫和記錄檔 (選擇性)，請執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a4997-131">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="a4997-132">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，新附加的資料庫無法立即在 [物件總管] 中可見。</span><span class="sxs-lookup"><span data-stu-id="a4997-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="a4997-133">若要檢視資料庫，請在 [物件總管] 中按一下 **[檢視]** ，然後按一下 **[重新整理]** 。</span><span class="sxs-lookup"><span data-stu-id="a4997-133">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="a4997-134">在 [物件總管] 中展開 **[資料庫]** 節點時，剛才附加的資料庫就會出現在資料庫清單中。</span><span class="sxs-lookup"><span data-stu-id="a4997-134">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4997-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4997-135">See Also</span></span>  
 [<span data-ttu-id="a4997-136">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a4997-136">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
