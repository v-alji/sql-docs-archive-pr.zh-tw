---
title: 資料庫檔案與檔案群組 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91e22e536a91878609feedf2977ffa7d78a54d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595117"
---
# <a name="database-files-and-filegroups"></a><span data-ttu-id="afddf-102">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="afddf-102">Database Files and Filegroups</span></span>
  <span data-ttu-id="afddf-103">基本上，每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫都有兩個作業系統檔案：資料檔與記錄檔。</span><span class="sxs-lookup"><span data-stu-id="afddf-103">At a minimum, every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database has two operating system files: a data file and a log file.</span></span> <span data-ttu-id="afddf-104">資料檔包含諸如資料表、索引、預存程序以及檢視等資料和物件。</span><span class="sxs-lookup"><span data-stu-id="afddf-104">Data files contain data and objects such as tables, indexes, stored procedures, and views.</span></span> <span data-ttu-id="afddf-105">記錄檔包含復原資料庫中所有交易必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="afddf-105">Log files contain the information that is required to recover all transactions in the database.</span></span> <span data-ttu-id="afddf-106">資料檔可以組成檔案群組，以方便配置及管理。</span><span class="sxs-lookup"><span data-stu-id="afddf-106">Data files can be grouped together in filegroups for allocation and administration purposes.</span></span>  
  
## <a name="database-files"></a><span data-ttu-id="afddf-107">資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="afddf-107">Database Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="afddf-108">資料庫有三種檔案類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="afddf-108">databases have three types of files, as shown in the following table.</span></span>  
  
|<span data-ttu-id="afddf-109">檔案</span><span class="sxs-lookup"><span data-stu-id="afddf-109">File</span></span>|<span data-ttu-id="afddf-110">描述</span><span class="sxs-lookup"><span data-stu-id="afddf-110">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="afddf-111">Primary</span><span class="sxs-lookup"><span data-stu-id="afddf-111">Primary</span></span>|<span data-ttu-id="afddf-112">主要資料檔包含資料庫啟動資訊，並指到資料庫中的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="afddf-112">The primary data file contains the startup information for the database and points to the other files in the database.</span></span> <span data-ttu-id="afddf-113">使用者資料和物件可儲存於此檔案或次要的資料檔中。</span><span class="sxs-lookup"><span data-stu-id="afddf-113">User data and objects can be stored in this file or in secondary data files.</span></span> <span data-ttu-id="afddf-114">每個資料庫都有一個主要資料檔案。</span><span class="sxs-lookup"><span data-stu-id="afddf-114">Every database has one primary data file.</span></span> <span data-ttu-id="afddf-115">建議您將主要資料檔的副檔名設為 .mdf。</span><span class="sxs-lookup"><span data-stu-id="afddf-115">The recommended file name extension for primary data files is .mdf.</span></span>|  
|<span data-ttu-id="afddf-116">次要</span><span class="sxs-lookup"><span data-stu-id="afddf-116">Secondary</span></span>|<span data-ttu-id="afddf-117">次要資料檔是選擇性且使用者自訂的，並可儲存使用者資料。</span><span class="sxs-lookup"><span data-stu-id="afddf-117">Secondary data files are optional, are user-defined, and store user data.</span></span> <span data-ttu-id="afddf-118">次要檔可用以將資料分散在多個磁碟上，即透過將每個檔案放在不同的磁碟機上來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="afddf-118">Secondary files can be used to spread data across multiple disks by putting each file on a different disk drive.</span></span> <span data-ttu-id="afddf-119">此外，若資料庫超過了單一 Windows 檔案的大小上限，您可使用次要資料檔，以容許資料庫繼續成長。</span><span class="sxs-lookup"><span data-stu-id="afddf-119">Additionally, if a database exceeds the maximum size for a single Windows file, you can use secondary data files so the database can continue to grow.</span></span><br /><br /> <span data-ttu-id="afddf-120">建議您將次要資料檔的副檔名設為 .ndf。</span><span class="sxs-lookup"><span data-stu-id="afddf-120">The recommended file name extension for secondary data files is .ndf.</span></span>|  
|<span data-ttu-id="afddf-121">交易記錄</span><span class="sxs-lookup"><span data-stu-id="afddf-121">Transaction Log</span></span>|<span data-ttu-id="afddf-122">交易記錄檔包含了用來復原資料庫的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="afddf-122">The transaction log files hold the log information that is used to recover the database.</span></span> <span data-ttu-id="afddf-123">每個資料庫至少要有一個記錄檔。</span><span class="sxs-lookup"><span data-stu-id="afddf-123">There must be at least one log file for each database.</span></span> <span data-ttu-id="afddf-124">建議的交易記錄檔的副檔名為 .ldf。</span><span class="sxs-lookup"><span data-stu-id="afddf-124">The recommended file name extension for transaction logs is .ldf.</span></span>|  
  
 <span data-ttu-id="afddf-125">例如，一個簡單的資料庫 **Sales** 可由一個包含所有資料和物件的主要檔案，以及一個包含交易記錄資訊的記錄檔所組成。</span><span class="sxs-lookup"><span data-stu-id="afddf-125">For example, a simple database named **Sales** can be created that includes one primary file that contains all data and objects and a log file that contains the transaction log information.</span></span> <span data-ttu-id="afddf-126">也可以建立名稱為 **Orders** 的複雜資料庫，以包含一個主要檔案和五個次要檔案。</span><span class="sxs-lookup"><span data-stu-id="afddf-126">Alternatively, a more complex database named **Orders** can be created that includes one primary file and five secondary files.</span></span> <span data-ttu-id="afddf-127">在資料庫中的資料和物件平均分散於總共六個檔案中，而且有四個記錄檔包含交易記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="afddf-127">The data and objects within the database spread across all six files, and the four log files contain the transaction log information.</span></span>  
  
 <span data-ttu-id="afddf-128">依預設，資料和交易記錄會放置在相同的磁碟和路徑中。</span><span class="sxs-lookup"><span data-stu-id="afddf-128">By default, the data and transaction logs are put on the same drive and path.</span></span> <span data-ttu-id="afddf-129">這是透過處理單一磁碟系統來完成。</span><span class="sxs-lookup"><span data-stu-id="afddf-129">This is done to handle single-disk systems.</span></span> <span data-ttu-id="afddf-130">然而，這對於實際執行環境可能不是最合適的。</span><span class="sxs-lookup"><span data-stu-id="afddf-130">However, this may not be optimal for production environments.</span></span> <span data-ttu-id="afddf-131">我們建議您將資料和記錄檔放在不同的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="afddf-131">We recommend that you put data and log files on separate disks.</span></span>  
  
## <a name="filegroups"></a><span data-ttu-id="afddf-132">檔案群組</span><span class="sxs-lookup"><span data-stu-id="afddf-132">Filegroups</span></span>  
 <span data-ttu-id="afddf-133">每個資料庫有一個主要的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-133">Every database has a primary filegroup.</span></span> <span data-ttu-id="afddf-134">此檔案群組可能包含主要資料檔和未放入其他檔案群組的次要檔案。</span><span class="sxs-lookup"><span data-stu-id="afddf-134">This filegroup contains the primary data file and any secondary files that are not put into other filegroups.</span></span> <span data-ttu-id="afddf-135">可建立使用者自訂檔案群組來將資料檔群組在一起，以利管理、資料配置和放置之用。</span><span class="sxs-lookup"><span data-stu-id="afddf-135">User-defined filegroups can be created to group data files together for administrative, data allocation, and placement purposes.</span></span>  
  
 <span data-ttu-id="afddf-136">例如，您以可將三個檔案 (Data1.ndf、Data2.ndf 以及 Data3.ndf) 分別建立於三台磁碟機內，並將它們指派至檔案群組 **fgroup1**。</span><span class="sxs-lookup"><span data-stu-id="afddf-136">For example, three files, Data1.ndf, Data2.ndf, and Data3.ndf, can be created on three disk drives, respectively, and assigned to the filegroup **fgroup1**.</span></span> <span data-ttu-id="afddf-137">接著您可根據檔案群組 **fgroup1**來建立資料表。</span><span class="sxs-lookup"><span data-stu-id="afddf-137">A table can then be created specifically on the filegroup **fgroup1**.</span></span> <span data-ttu-id="afddf-138">資料表的資料查詢可分散至三個磁碟，藉此改善效能。</span><span class="sxs-lookup"><span data-stu-id="afddf-138">Queries for data from the table will be spread across the three disks; this will improve performance.</span></span> <span data-ttu-id="afddf-139">另一個改善效能的作法是將單一檔案建立在 RAID (獨立磁碟的重複陣列，通稱磁碟陣列) 的條狀磁碟組上。</span><span class="sxs-lookup"><span data-stu-id="afddf-139">The same performance improvement can be accomplished by using a single file created on a RAID (redundant array of independent disks) stripe set.</span></span> <span data-ttu-id="afddf-140">然而，檔案和檔案群組都可讓您輕鬆地將新的檔案加至新的磁碟內。</span><span class="sxs-lookup"><span data-stu-id="afddf-140">However, files and filegroups let you easily add new files to new disks.</span></span>  
  
 <span data-ttu-id="afddf-141">所有儲存在檔案群組中的資料檔列於下表。</span><span class="sxs-lookup"><span data-stu-id="afddf-141">All data files are stored in the filegroups listed in the following table.</span></span>  
  
|<span data-ttu-id="afddf-142">檔案群組</span><span class="sxs-lookup"><span data-stu-id="afddf-142">Filegroup</span></span>|<span data-ttu-id="afddf-143">描述</span><span class="sxs-lookup"><span data-stu-id="afddf-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afddf-144">Primary</span><span class="sxs-lookup"><span data-stu-id="afddf-144">Primary</span></span>|<span data-ttu-id="afddf-145">包含主要檔案的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-145">The filegroup that contains the primary file.</span></span> <span data-ttu-id="afddf-146">所有的系統資料表都配置於主要檔案群組內。</span><span class="sxs-lookup"><span data-stu-id="afddf-146">All system tables are allocated to the primary filegroup.</span></span>|  
|<span data-ttu-id="afddf-147">使用者定義</span><span class="sxs-lookup"><span data-stu-id="afddf-147">User-defined</span></span>|<span data-ttu-id="afddf-148">使用者在初次建立資料庫或之後修改資料庫時，特別建立的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-148">Any filegroup that is specifically created by the user when the user first creates or later modifies the database.</span></span>|  
  
### <a name="default-filegroup"></a><span data-ttu-id="afddf-149">預設的檔案群組</span><span class="sxs-lookup"><span data-stu-id="afddf-149">Default Filegroup</span></span>  
 <span data-ttu-id="afddf-150">若在資料庫中建立物件時未指明屬於哪個檔案群組，就會將物件指定至預設的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-150">When objects are created in the database without specifying which filegroup they belong to, they are assigned to the default filegroup.</span></span> <span data-ttu-id="afddf-151">在任何時候，都只有一個檔案群組指定為預設檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-151">At any time, exactly one filegroup is designated as the default filegroup.</span></span> <span data-ttu-id="afddf-152">在預設檔案群組中的檔案必須夠大，才能容納未配置到其他檔案群組的新物件。</span><span class="sxs-lookup"><span data-stu-id="afddf-152">The files in the default filegroup must be large enough to hold any new objects not allocated to other filegroups.</span></span>  
  
 <span data-ttu-id="afddf-153">除非使用 ALTER DATABASE 陳述式加以變更，否則 PRIMARY 檔案群組就是預設的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="afddf-153">The PRIMARY filegroup is the default filegroup unless it is changed by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="afddf-154">系統物件和資料表仍配置於 PRIMARY 檔案群組內，而非新的預設檔案群組之中。</span><span class="sxs-lookup"><span data-stu-id="afddf-154">Allocation for the system objects and tables remains within the PRIMARY filegroup, not the new default filegroup.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="afddf-155">相關內容</span><span class="sxs-lookup"><span data-stu-id="afddf-155">Related Content</span></span>  
 [<span data-ttu-id="afddf-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="afddf-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [<span data-ttu-id="afddf-157">ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="afddf-157">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [<span data-ttu-id="afddf-158">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="afddf-158">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
