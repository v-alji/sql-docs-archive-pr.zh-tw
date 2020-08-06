---
title: MSSQLSERVER_8992 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8992 (Database Engine error)
ms.assetid: 68467e6a-09d8-478f-8bd9-3bb09453ada3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adcf914accab43202cf148fe852b334c9b078287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607398"
---
# <a name="mssqlserver_8992"></a><span data-ttu-id="ad337-102">MSSQLSERVER_8992</span><span class="sxs-lookup"><span data-stu-id="ad337-102">MSSQLSERVER_8992</span></span>
    
## <a name="details"></a><span data-ttu-id="ad337-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ad337-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad337-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ad337-104">Product Name</span></span>|<span data-ttu-id="ad337-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ad337-105">SQL Server</span></span>|  
|<span data-ttu-id="ad337-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ad337-106">Event ID</span></span>|<span data-ttu-id="ad337-107">8992</span><span class="sxs-lookup"><span data-stu-id="ad337-107">8992</span></span>|  
|<span data-ttu-id="ad337-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ad337-108">Event Source</span></span>|<span data-ttu-id="ad337-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ad337-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ad337-110">元件</span><span class="sxs-lookup"><span data-stu-id="ad337-110">Component</span></span>|<span data-ttu-id="ad337-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ad337-111">SQLEngine</span></span>|  
|<span data-ttu-id="ad337-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ad337-112">Symbolic Name</span></span>|<span data-ttu-id="ad337-113">DBCC3_CHECK_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ad337-113">DBCC3_CHECK_CATALOG</span></span>|  
|<span data-ttu-id="ad337-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ad337-114">Message Text</span></span>|<span data-ttu-id="ad337-115">檢查目錄訊息 ERROR 層級 LEVEL 狀態 STATE:MESSAGE。</span><span class="sxs-lookup"><span data-stu-id="ad337-115">Check Catalog Msg ERROR Level LEVEL State STATE: MESSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad337-116">說明</span><span class="sxs-lookup"><span data-stu-id="ad337-116">Explanation</span></span>  
 <span data-ttu-id="ad337-117">DBCC CHECKCATALOG 或 DBCC CHECKDB 在指定之物件的系統中繼資料表中發現不一致。</span><span class="sxs-lookup"><span data-stu-id="ad337-117">DBCC CHECKCATALOG or DBCC CHECKDB found an inconsistency in the system metadata tables for the specified object.</span></span> <span data-ttu-id="ad337-118">亦即，在記錄的物件識別碼和錯誤訊息中指定的物件之間發生不一致。</span><span class="sxs-lookup"><span data-stu-id="ad337-118">That is, there is an inconsistency between the recorded object ID and the object specified in error message.</span></span>  
  
 <span data-ttu-id="ad337-119">當一個或多個系統資料表利用產生系統中繼資料不一致的方式進行手動更新，可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad337-119">This error can occur when one or more system tables has been manually updated in a way that creates an inconsistency in the system metadata.</span></span> <span data-ttu-id="ad337-120">例如，使用者可能已經手動刪除 **sysobjects** 資料表中的物件，而沒有移除其他資料表中相關聯的資料列，例如 **sysindexes** 和 **syscolumns**。</span><span class="sxs-lookup"><span data-stu-id="ad337-120">For example, a user may have manually deleted an object from the **sysobjects** table without removing associated rows in other tables such as **sysindexes** and **syscolumns**.</span></span>  
  
 <span data-ttu-id="ad337-121">根據已經從 SQL Server 2000 升級到 SQL Server 2005 或更新版本的資料庫執行 DBCC CHECKDB 時，可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad337-121">This error can occur when running DBCC CHECKDB against a database that has been upgraded from SQL Server 2000 to SQL Server 2005 or later.</span></span> <span data-ttu-id="ad337-122">在 SQL Server 2000 中，DBCC CHECKDB 不包含 DBCC CHECKCATALOG 功能，因此，除非特別針對 SQL Server 2000 中的資料庫執行 DBCC CHECKCATALOG，否則在升級前不會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad337-122">In SQL Server 2000, DBCC CHECKDB did not include DBCC CHECKCATALOG functionality, so the error would not be caught before upgrade unless DBCC CHECKCATALOG was specifically executed against the database in SQL Server 2000.</span></span>  
  
 <span data-ttu-id="ad337-123">您可能會看到下列任一種錯誤和錯誤 8992 一起出現：</span><span class="sxs-lookup"><span data-stu-id="ad337-123">You may see any of the following errors in conjunction with error 8992:</span></span>  
  
 <span data-ttu-id="ad337-124">訊息 3851：在系統資料表 sys.%ls%ls 中發現無效的資料列 (%ls)。</span><span class="sxs-lookup"><span data-stu-id="ad337-124">Msg 3851 - An invalid row (%ls) was found in the system table sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-125">訊息 3852：sys.%ls%ls 中的資料列 (%ls) 在 sys.%ls%ls 之中並沒有相符的資料列 (%ls)。</span><span class="sxs-lookup"><span data-stu-id="ad337-125">Msg 3852 - Row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-126">3853：sys.%ls%ls 中資料列 (%ls) 的屬性 (%ls) 在 sys.%ls%ls 中並沒有相符的資料列 (%ls)。</span><span class="sxs-lookup"><span data-stu-id="ad337-126">3853 - Attribute (%ls) of row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-127">3854：sys.%ls%ls 中資料列 (%ls) 的屬性 (%ls) 在 sys.%ls%ls 中相符的資料列 (%ls) 無效。</span><span class="sxs-lookup"><span data-stu-id="ad337-127">3854 - Attribute (%ls) of row (%ls) in sys.%ls%ls has a matching row (%ls) in sys.%ls%ls that is invalid.</span></span>  
  
 <span data-ttu-id="ad337-128">3855：屬性 (%ls) 存在，但是在 sys.%ls%ls 中沒有資料列 (%ls)。</span><span class="sxs-lookup"><span data-stu-id="ad337-128">3855 - Attribute (%ls) exists without a row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-129">3856：屬性 (%ls) 存在，但應該不是 sys.%ls%ls 中資料列 (%ls) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad337-129">3856 - Attribute (%ls) exists but should not for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-130">3857：必須有屬性 (%ls)，但是 sys.%ls%ls 中的資料列 (%ls) 缺少此屬性。</span><span class="sxs-lookup"><span data-stu-id="ad337-130">3857 - The attribute (%ls) is required but is missing for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="ad337-131">3858：sys.%ls%ls 中資料列 (%ls) 的屬性 (%ls) 有無效的值。</span><span class="sxs-lookup"><span data-stu-id="ad337-131">3858 - The attribute (%ls) of row (%ls) in sys.%ls%ls has an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad337-132">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ad337-132">User Action</span></span>  
  
### <a name="drop-and-re-create-the-specified-object"></a><span data-ttu-id="ad337-133">卸除指定的物件後再重新建立</span><span class="sxs-lookup"><span data-stu-id="ad337-133">Drop and Re-create the Specified Object</span></span>  
 <span data-ttu-id="ad337-134">如果可能，卸除指定的物件後再重新建立。</span><span class="sxs-lookup"><span data-stu-id="ad337-134">If possible, drop and recreate the specified object.</span></span> <span data-ttu-id="ad337-135">例如，如果物件為預存程序或使用者定義型別，重新建立物件可能會解決問題。</span><span class="sxs-lookup"><span data-stu-id="ad337-135">For example, if the object is a stored procedure or user-defined type, recreating the object may resolve the problem.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ad337-136">還原備份</span><span class="sxs-lookup"><span data-stu-id="ad337-136">Restore from Backup</span></span>  
 <span data-ttu-id="ad337-137">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad337-137">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span> <span data-ttu-id="ad337-138">此動作僅適用於備份不包含中繼資料錯誤時。</span><span class="sxs-lookup"><span data-stu-id="ad337-138">This action is only applicable if the backup does not contain the metadata error.</span></span>  
  
### <a name="export-the-data-to-a-new-database"></a><span data-ttu-id="ad337-139">將資料匯出到新資料庫</span><span class="sxs-lookup"><span data-stu-id="ad337-139">Export the Data to a New Database</span></span>  
 <span data-ttu-id="ad337-140">如果備份另有中繼資料不一致的情況，則您需要建立新的資料庫，並且將現有資料庫的內容匯出到新資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad337-140">If the backup also contains the metadata inconsistency, you need to create a new database and export the contents of the existing database to the new database.</span></span>  
  
### <a name="dbcc-checkdb-cannot-repair-this-error"></a><span data-ttu-id="ad337-141">DBCC CHECKDB 無法修復此錯誤</span><span class="sxs-lookup"><span data-stu-id="ad337-141">DBCC CHECKDB Cannot Repair This Error</span></span>  
 <span data-ttu-id="ad337-142">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="ad337-142">This error cannot be repaired.</span></span>  <span data-ttu-id="ad337-143">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="ad337-143">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
### <a name="do-not-manually-update-system-tables"></a><span data-ttu-id="ad337-144">不要手動更新系統資料表</span><span class="sxs-lookup"><span data-stu-id="ad337-144">Do Not Manually Update System Tables</span></span>  
 <span data-ttu-id="ad337-145">不要手動更新系統資料表。</span><span class="sxs-lookup"><span data-stu-id="ad337-145">Do not make manual updates to system tables.</span></span> <span data-ttu-id="ad337-146">SQL Server 不支援對系統資料庫進行任何手動變更。</span><span class="sxs-lookup"><span data-stu-id="ad337-146">SQL Server does not support any manual changes to system databases.</span></span> <span data-ttu-id="ad337-147">如果您更新 SQL Server 資料庫中的系統資料表，則會記錄兩個事件 (事件識別碼 17659 和事件識別碼 3859)。</span><span class="sxs-lookup"><span data-stu-id="ad337-147">If you update a system table in a SQL Server database, two events (event ID 17659 and event ID 3859) are logged.</span></span> <span data-ttu-id="ad337-148">如需詳細資訊，請參閱知識庫文件 2688307＜當您更新 SQL Server 資料庫中的系統資料表時，會記錄事件識別碼 17659 和事件識別碼 3859＞(機器翻譯)。</span><span class="sxs-lookup"><span data-stu-id="ad337-148">For more information, see KB article 2688307, "Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad337-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad337-149">See Also</span></span>  
 <span data-ttu-id="ad337-150">[Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database](https://support.microsoft.com/kb/2688307/EN-US) (當您更新 SQL Server 資料庫中的系統資料表時，會記錄事件識別碼 17659 和事件識別碼 3859)</span><span class="sxs-lookup"><span data-stu-id="ad337-150">[Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database](https://support.microsoft.com/kb/2688307/EN-US)</span></span>  
  
  
