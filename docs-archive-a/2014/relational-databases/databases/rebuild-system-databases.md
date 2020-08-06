---
title: 重建系統資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f695589fa0fc1b86d4433d36afa1bc6357aabd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595098"
---
# <a name="rebuild-system-databases"></a><span data-ttu-id="9637c-102">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-102">Rebuild System Databases</span></span>
  <span data-ttu-id="9637c-103">您必須重建系統資料庫，才能在 [master](master-database.md)、 [model](model-database.md)、 [msdb](msdb-database.md)或 [resource](resource-database.md) 系統資料庫中修正損毀問題，或修改預設的伺服器層級定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-103">System databases must be rebuilt to fix corruption problems in the [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md), or [resource](resource-database.md) system databases or to modify the default server-level collation.</span></span> <span data-ttu-id="9637c-104">本主題將提供在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中重建系統資料庫的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="9637c-104">This topic provides step-by-step instructions to rebuild system databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="9637c-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9637c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9637c-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9637c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9637c-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="9637c-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9637c-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="9637c-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="9637c-109">**程序：**</span><span class="sxs-lookup"><span data-stu-id="9637c-109">**Procedures:**</span></span>  
  
     [<span data-ttu-id="9637c-110">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-110">Rebuild System Databases</span></span>](#RebuildProcedure)  
  
     [<span data-ttu-id="9637c-111">重建資源資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-111">Rebuild the resource Database</span></span>](#Resource)  
  
     [<span data-ttu-id="9637c-112">建立新的 msdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-112">Create a New msdb Database</span></span>](#CreateMSDB)  
  
-   <span data-ttu-id="9637c-113">**後續操作：**</span><span class="sxs-lookup"><span data-stu-id="9637c-113">**Follow Up:**</span></span>  
  
     [<span data-ttu-id="9637c-114">疑難排解重建錯誤</span><span class="sxs-lookup"><span data-stu-id="9637c-114">Troubleshoot Rebuild Errors</span></span>](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9637c-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="9637c-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9637c-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="9637c-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9637c-117">重建 master、model、msdb 和 tempdb 系統資料庫時，系統會在這些資料庫的原始位置中卸除並重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="9637c-117">When the master, model, msdb, and tempdb system databases are rebuilt, the databases are dropped and re-created in their original location.</span></span> <span data-ttu-id="9637c-118">如果您在重建陳述式中指定了新的定序，系統就會使用該定序設定來建立系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-118">If a new collation is specified in the rebuild statement, the system databases are created using that collation setting.</span></span> <span data-ttu-id="9637c-119">使用者對這些資料庫所做的任何修改都將遺失。</span><span class="sxs-lookup"><span data-stu-id="9637c-119">Any user modifications to these databases are lost.</span></span> <span data-ttu-id="9637c-120">例如，您可能會在 master 資料庫中設有使用者定義的物件、在 msdb 中設有排程的作業，或在 model 資料庫中變更預設資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="9637c-120">For example, you may have user-defined objects in the master database, scheduled jobs in msdb, or changes to the default database settings in the model database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9637c-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="9637c-121">Prerequisites</span></span>  
 <span data-ttu-id="9637c-122">請在重建系統資料庫之前執行下列工作，以便確保您可以將系統資料庫還原成目前的設定。</span><span class="sxs-lookup"><span data-stu-id="9637c-122">Perform the following tasks before you rebuild the system databases to ensure that you can restore the system databases to their current settings.</span></span>  
  
1.  <span data-ttu-id="9637c-123">記錄所有伺服器範圍的組態值。</span><span class="sxs-lookup"><span data-stu-id="9637c-123">Record all server-wide configuration values.</span></span>  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  <span data-ttu-id="9637c-124">記錄所有套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 Service Pack 和 Hotfix 以及目前的定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-124">Record all service packs and hotfixes applied to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current collation.</span></span> <span data-ttu-id="9637c-125">您必須在重建系統資料庫之後重新套用這些更新。</span><span class="sxs-lookup"><span data-stu-id="9637c-125">You must reapply these updates after rebuilding the system databases.</span></span>  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  <span data-ttu-id="9637c-126">記錄系統資料庫之所有資料和記錄檔的目前位置。</span><span class="sxs-lookup"><span data-stu-id="9637c-126">Record the current location of all data and log files for the system databases.</span></span> <span data-ttu-id="9637c-127">重建系統資料庫會將所有系統資料庫安裝到其原始位置。</span><span class="sxs-lookup"><span data-stu-id="9637c-127">Rebuilding the system databases installs all system databases to their original location.</span></span> <span data-ttu-id="9637c-128">如果您已將系統資料庫的資料或記錄檔移至不同的位置，就必須再次移動這些檔案。</span><span class="sxs-lookup"><span data-stu-id="9637c-128">If you have moved system database data or log files to a different location, you must move the files again.</span></span>  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  <span data-ttu-id="9637c-129">找出 master、model 和 msdb 資料庫的目前備份。</span><span class="sxs-lookup"><span data-stu-id="9637c-129">Locate the current backup of the master, model, and msdb databases.</span></span>  
  
5.  <span data-ttu-id="9637c-130">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體設定為複寫散發者，請找出散發資料庫的目前備份。</span><span class="sxs-lookup"><span data-stu-id="9637c-130">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, locate the current backup of the distribution database.</span></span>  
  
6.  <span data-ttu-id="9637c-131">確定您擁有重建系統資料庫的適當權限。</span><span class="sxs-lookup"><span data-stu-id="9637c-131">Ensure you have appropriate permissions to rebuild the system databases.</span></span> <span data-ttu-id="9637c-132">若要執行這項作業，您必須是系統管理員 (`sysadmin`) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="9637c-132">To perform this operation, you must be a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="9637c-133">如需詳細資訊，請參閱 [伺服器層級角色](../security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-133">For more information, see [Server-Level Roles](../security/authentication-access/server-level-roles.md).</span></span>  
  
7.  <span data-ttu-id="9637c-134">確認 master、model 和 msdb 資料與記錄範本檔案的副本都存在本機伺服器上。</span><span class="sxs-lookup"><span data-stu-id="9637c-134">Verify that copies of the master, model, msdb data and log template files exist on the local server.</span></span> <span data-ttu-id="9637c-135">這些範本檔案的預設位置為 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates。</span><span class="sxs-lookup"><span data-stu-id="9637c-135">The default location for the template files is C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates.</span></span> <span data-ttu-id="9637c-136">這些檔案會在重建程序期間使用，而且它們必須存在，才能讓安裝程式順利執行。</span><span class="sxs-lookup"><span data-stu-id="9637c-136">These files are used during the rebuild process and must be present for Setup to succeed.</span></span> <span data-ttu-id="9637c-137">如果這些檔案已遺失，請執行安裝程式的修復功能，或手動從安裝媒體中複製這些檔案。</span><span class="sxs-lookup"><span data-stu-id="9637c-137">If they are missing, run the Repair feature of Setup, or manually copy the files from your installation media.</span></span> <span data-ttu-id="9637c-138">若要在安裝媒體上找到這些檔案，請巡覽至適當的平台目錄 (x86 或 x64)，然後巡覽至 setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates。</span><span class="sxs-lookup"><span data-stu-id="9637c-138">To locate the files on the installation media, navigate to the appropriate platform directory (x86 or x64) and then navigate to setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.</span></span>  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> <span data-ttu-id="9637c-139">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-139">Rebuild System Databases</span></span>  
 <span data-ttu-id="9637c-140">下列程序會重建 master、model、msdb 和 tempdb 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-140">The following procedure rebuilds the master, model, msdb, and tempdb system databases.</span></span> <span data-ttu-id="9637c-141">您無法指定要重建的系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-141">You cannot specify the system databases to be rebuilt.</span></span> <span data-ttu-id="9637c-142">若為叢集執行個體，您必須在使用中節點上執行此程序，而且必須先讓對應叢集應用程式群組中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源離線，然後再執行此程序。</span><span class="sxs-lookup"><span data-stu-id="9637c-142">For clustered instances, this procedure must be performed on the active node and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource in the corresponding cluster application group must be taken offline before performing the procedure.</span></span>  
  
 <span data-ttu-id="9637c-143">這項程序不會重建 resource 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-143">This procedure does not rebuild the resource database.</span></span> <span data-ttu-id="9637c-144">請參閱本主題後面的＜重建 resource 資料庫程序＞一節。</span><span class="sxs-lookup"><span data-stu-id="9637c-144">See the section, "Rebuild the resource Database Procedure" later in this topic.</span></span>  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a><span data-ttu-id="9637c-145">若要重建 SQL Server 執行個體的系統資料庫：</span><span class="sxs-lookup"><span data-stu-id="9637c-145">To rebuild system databases for an instance of SQL Server:</span></span>  
  
1.  <span data-ttu-id="9637c-146">將 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝媒體插入光碟機，或在命令提示字元中，將目錄變更為本機伺服器上 setup.exe 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="9637c-146">Insert the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media into the disk drive, or, from a command prompt, change directories to the location of the setup.exe file on the local server.</span></span> <span data-ttu-id="9637c-147">伺服器的預設位置是 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release。</span><span class="sxs-lookup"><span data-stu-id="9637c-147">The default location on the server is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release.</span></span>  
  
2.  <span data-ttu-id="9637c-148">在 [命令提示字元] 視窗中，輸入下列命令。</span><span class="sxs-lookup"><span data-stu-id="9637c-148">From a command prompt window, enter the following command.</span></span> <span data-ttu-id="9637c-149">方括號是用來表示選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="9637c-149">Square brackets are used to indicate optional parameters.</span></span> <span data-ttu-id="9637c-150">請勿輸入方括號。</span><span class="sxs-lookup"><span data-stu-id="9637c-150">Do not enter the brackets.</span></span> <span data-ttu-id="9637c-151">使用啟用使用者帳戶控制 (UAC) 的 Windows 作業系統時，必須要有更高的權限才能執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="9637c-151">When using a Windows operating system that has User Account Control (UAC) enabled, running Setup requires elevated privileges.</span></span> <span data-ttu-id="9637c-152">您必須以管理員的身分執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9637c-152">The command prompt must be run as Administrator.</span></span>  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |<span data-ttu-id="9637c-153">參數名稱</span><span class="sxs-lookup"><span data-stu-id="9637c-153">Parameter name</span></span>|<span data-ttu-id="9637c-154">描述</span><span class="sxs-lookup"><span data-stu-id="9637c-154">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="9637c-155">/QUIET 或 /Q</span><span class="sxs-lookup"><span data-stu-id="9637c-155">/QUIET or /Q</span></span>|<span data-ttu-id="9637c-156">指定安裝程式的執行不使用任何使用者介面。</span><span class="sxs-lookup"><span data-stu-id="9637c-156">Specifies that Setup run without any user interface.</span></span>|  
    |<span data-ttu-id="9637c-157">/ACTION=REBUILDDATABASE</span><span class="sxs-lookup"><span data-stu-id="9637c-157">/ACTION=REBUILDDATABASE</span></span>|<span data-ttu-id="9637c-158">指定安裝程式要重新建立系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-158">Specifies that Setup re-create the system databases.</span></span>|  
    |<span data-ttu-id="9637c-159">/INSTANCENAME=*InstanceName*</span><span class="sxs-lookup"><span data-stu-id="9637c-159">/INSTANCENAME=*InstanceName*</span></span>|<span data-ttu-id="9637c-160">這是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9637c-160">Is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9637c-161">若為預設執行個體，請輸入 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="9637c-161">For the default instance, enter MSSQLSERVER.</span></span>|  
    |<span data-ttu-id="9637c-162">/SQLSYSADMINACCOUNTS=*accounts*</span><span class="sxs-lookup"><span data-stu-id="9637c-162">/SQLSYSADMINACCOUNTS=*accounts*</span></span>|<span data-ttu-id="9637c-163">指定要加入至系統管理員 (`sysadmin`) 固定伺服器角色的 Windows 群組或個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="9637c-163">Specifies the Windows groups or individual accounts to add to the `sysadmin` fixed server role.</span></span> <span data-ttu-id="9637c-164">指定多個帳戶時，請以空格隔開這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="9637c-164">When specifying more than one account, separate the accounts with a blank space.</span></span> <span data-ttu-id="9637c-165">例如，您可以輸入 **BUILTIN\Administrators MyDomain\MyUser**。</span><span class="sxs-lookup"><span data-stu-id="9637c-165">For example, enter **BUILTIN\Administrators MyDomain\MyUser**.</span></span> <span data-ttu-id="9637c-166">當您要指定的帳戶在帳戶名稱中包含空白時，請以雙引號括住該帳戶。</span><span class="sxs-lookup"><span data-stu-id="9637c-166">When you are specifying an account that contains a blank space within the account name, enclose the account in double quotation marks.</span></span> <span data-ttu-id="9637c-167">例如，輸入 `NT AUTHORITY\SYSTEM`。</span><span class="sxs-lookup"><span data-stu-id="9637c-167">For example, enter `NT AUTHORITY\SYSTEM`.</span></span>|  
    |<span data-ttu-id="9637c-168">[ /SAPWD=*StrongPassword* ]</span><span class="sxs-lookup"><span data-stu-id="9637c-168">[ /SAPWD=*StrongPassword* ]</span></span>|<span data-ttu-id="9637c-169">指定帳戶的密碼 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` 。</span><span class="sxs-lookup"><span data-stu-id="9637c-169">Specifies the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` account.</span></span> <span data-ttu-id="9637c-170">如果執行個體使用混合驗證 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 驗證) 模式，這就是必要的參數。</span><span class="sxs-lookup"><span data-stu-id="9637c-170">This parameter is required if the instance uses Mixed Authentication ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication) mode.</span></span><br /><br /> <span data-ttu-id="9637c-171">\*\* \* \* 安全性 \* 注意事項 \* \*\* `sa` 帳戶是已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，而且通常是惡意使用者的目標。</span><span class="sxs-lookup"><span data-stu-id="9637c-171">**\*\* Security Note \*\*** The `sa` account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="9637c-172">請務必針對 `sa` 登入使用一個增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="9637c-172">It is very important that you use a strong password for the `sa` login.</span></span><br /><br /> <span data-ttu-id="9637c-173">請勿針對 Windows 驗證模式指定此參數。</span><span class="sxs-lookup"><span data-stu-id="9637c-173">Do not specify this parameter for Windows Authentication mode.</span></span>|  
    |<span data-ttu-id="9637c-174">[ /SQLCOLLATION=*CollationName* ]</span><span class="sxs-lookup"><span data-stu-id="9637c-174">[ /SQLCOLLATION=*CollationName* ]</span></span>|<span data-ttu-id="9637c-175">指定新的伺服器層級定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-175">Specifies a new server-level collation.</span></span> <span data-ttu-id="9637c-176">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="9637c-176">This parameter is optional.</span></span> <span data-ttu-id="9637c-177">如果沒有指定，就會使用伺服器的目前定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-177">When not specified, the current collation of the server is used.</span></span><br /><br /> <span data-ttu-id="9637c-178">**\*\* 重要事項 \*\*** 變更伺服器層級定序並不會變更現有使用者資料庫的定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-178">**\*\* Important \*\*** Changing the server-level collation does not change the collation of existing user databases.</span></span> <span data-ttu-id="9637c-179">所有新建立的使用者資料庫預設都會使用新的定序。</span><span class="sxs-lookup"><span data-stu-id="9637c-179">All newly created user databases will use the new collation by default.</span></span><br /><br /> <span data-ttu-id="9637c-180">如需詳細資訊，請參閱 [設定或變更伺服器定序](../collations/set-or-change-the-server-collation.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-180">For more information, see [Set or Change the Server Collation](../collations/set-or-change-the-server-collation.md).</span></span>|  
  
3.  <span data-ttu-id="9637c-181">當安裝程式完成系統資料庫的重建作業時，它就會返回命令提示字元，而且不會顯示任何訊息。</span><span class="sxs-lookup"><span data-stu-id="9637c-181">When Setup has completed rebuilding the system databases, it returns to the command prompt with no messages.</span></span> <span data-ttu-id="9637c-182">您可以檢查 Summary.txt 記錄檔來確認此程序是否順利完成。</span><span class="sxs-lookup"><span data-stu-id="9637c-182">Examine the Summary.txt log file to verify that the process completed successfully.</span></span> <span data-ttu-id="9637c-183">這個檔案位於 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs。</span><span class="sxs-lookup"><span data-stu-id="9637c-183">This file is located at C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span>  
  
## <a name="post-rebuild-tasks"></a><span data-ttu-id="9637c-184">重建後的工作</span><span class="sxs-lookup"><span data-stu-id="9637c-184">Post-Rebuild Tasks</span></span>  
 <span data-ttu-id="9637c-185">重建資料庫之後，您可能必須執行下列額外的工作：</span><span class="sxs-lookup"><span data-stu-id="9637c-185">After rebuilding the database you may need to perform the following additional tasks:</span></span>  
  
-   <span data-ttu-id="9637c-186">還原 master、model 和 msdb 資料庫的最新完整備份。</span><span class="sxs-lookup"><span data-stu-id="9637c-186">Restore your most recent full backups of the master, model, and msdb databases.</span></span> <span data-ttu-id="9637c-187">如需詳細資訊，請參閱[系統資料庫的備份與還原 &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-187">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9637c-188">如果您已變更伺服器定序，請勿還原系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-188">If you have changed the server collation, do not restore the system databases.</span></span> <span data-ttu-id="9637c-189">這樣做會將新的定序取代成先前的定序設定。</span><span class="sxs-lookup"><span data-stu-id="9637c-189">Doing so will replace the new collation with the previous collation setting.</span></span>  
  
     <span data-ttu-id="9637c-190">如果無法使用備份，或者還原的備份並非最新備份，請重新建立任何遺漏的項目。</span><span class="sxs-lookup"><span data-stu-id="9637c-190">If a backup is not available or if the restored backup is not current, re-create any missing entries.</span></span> <span data-ttu-id="9637c-191">例如，請針對您的使用者資料庫、備份裝置、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入、端點等重新建立所有遺漏的項目。</span><span class="sxs-lookup"><span data-stu-id="9637c-191">For example, re-create all missing entries for your user databases, backup devices, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, end points, and so on.</span></span> <span data-ttu-id="9637c-192">重新建立項目的最佳方式是執行建立這些項目的原始指令碼。</span><span class="sxs-lookup"><span data-stu-id="9637c-192">The best way to re-create entries is to run the original scripts that created them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9637c-193">我們建議您保護指令碼的安全，防止它們遭受未獲授權的人員更改。</span><span class="sxs-lookup"><span data-stu-id="9637c-193">We recommend that you secure your scripts to prevent their being altered by unauthorized by individuals.</span></span>  
  
-   <span data-ttu-id="9637c-194">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體設定為複寫散發者，您就必須還原散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-194">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, you must restore the distribution database.</span></span> <span data-ttu-id="9637c-195">如需詳細資訊，請參閱 [備份及還原複寫的資料庫](../replication/administration/back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-195">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
-   <span data-ttu-id="9637c-196">將系統資料庫移至您先前記錄的位置。</span><span class="sxs-lookup"><span data-stu-id="9637c-196">Move the system databases to the locations you recorded previously.</span></span> <span data-ttu-id="9637c-197">如需詳細資訊，請參閱 [移動系統資料庫](system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-197">For more information, see [Move System Databases](system-databases.md).</span></span>  
  
-   <span data-ttu-id="9637c-198">確認伺服器範圍的組態值符合您先前記錄的值。</span><span class="sxs-lookup"><span data-stu-id="9637c-198">Verify the server-wide configuration values match the values you recorded previously.</span></span>  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="9637c-199">重建資源資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-199">Rebuild the resource Database</span></span>  
 <span data-ttu-id="9637c-200">下列程序會重建 resource 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-200">The following procedure rebuilds the resource system database.</span></span> <span data-ttu-id="9637c-201">當您重建 resource 資料庫時，所有 Service Pack 和 Hotfix 都會遺失，因此必須重新套用。</span><span class="sxs-lookup"><span data-stu-id="9637c-201">When you rebuild the resource database, all service packs and hot fixes are lost, and therefore must be reapplied.</span></span>  
  
#### <a name="to-rebuild-the-resource-system-database"></a><span data-ttu-id="9637c-202">若要重建 resource 系統資料庫：</span><span class="sxs-lookup"><span data-stu-id="9637c-202">To rebuild the resource system database:</span></span>  
  
1.  <span data-ttu-id="9637c-203">從散發程式媒體啟動 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式 (setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="9637c-203">Launch the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup program (setup.exe) from the distribution media.</span></span>  
  
2.  <span data-ttu-id="9637c-204">在左側導覽區域中，按一下 **[維護]** ，然後按一下 **[修復]** 。</span><span class="sxs-lookup"><span data-stu-id="9637c-204">In the left navigation area, click **Maintenance**, and then click **Repair**.</span></span>  
  
3.  <span data-ttu-id="9637c-205">安裝程式支援規則和檔案常式將會執行，以便確保您的系統已安裝必要元件而且電腦通過安裝程式驗證規則。</span><span class="sxs-lookup"><span data-stu-id="9637c-205">Setup support rule and file routines run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="9637c-206">按一下 **[確定]** 或 **[安裝]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="9637c-206">Click **OK** or **Install** to continue.</span></span>  
  
4.  <span data-ttu-id="9637c-207">在 [選取執行個體] 頁面上，選取要修復的執行個體，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="9637c-207">On the Select Instance page, select the instance to repair, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9637c-208">修復規則將會執行，以便驗證作業。</span><span class="sxs-lookup"><span data-stu-id="9637c-208">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="9637c-209">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="9637c-209">To continue, click **Next**.</span></span>  
  
6.  <span data-ttu-id="9637c-210">在 **[已完成修復準備工作]** 頁面中，按一下 **[修復]** 。</span><span class="sxs-lookup"><span data-stu-id="9637c-210">From the **Ready to Repair** page, click **Repair**.</span></span> <span data-ttu-id="9637c-211">[完成] 頁面會指出作業已完成。</span><span class="sxs-lookup"><span data-stu-id="9637c-211">The Complete page indicates that the operation is finished.</span></span>  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> <span data-ttu-id="9637c-212">建立新的 msdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-212">Create a New msdb Database</span></span>  
 <span data-ttu-id="9637c-213">如果 `msdb` 資料庫損毀，而且您沒有資料庫的備份 `msdb` ，您可以 `msdb` 使用**instmsdb**腳本來建立新的。</span><span class="sxs-lookup"><span data-stu-id="9637c-213">If the `msdb` database is damaged and you do not have a backup of the `msdb` database, you can create a new `msdb` by using the **instmsdb** script.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9637c-214">`msdb`使用**instmsdb**腳本重建資料庫將會排除儲存在中的所有資訊， `msdb` 例如作業、警示、操作員、維護計畫、備份歷程記錄、以原則為基礎的管理設定、Database Mail、效能資料倉儲等等。</span><span class="sxs-lookup"><span data-stu-id="9637c-214">Rebuilding the `msdb` database using the **instmsdb** script will eliminate all the information stored in `msdb` such as jobs, alert, operators, maintenance plans, backup history, Policy-Based Management settings, Database Mail, Performance Data Warehouse, etc.</span></span>  
  
1.  <span data-ttu-id="9637c-215">停止所有連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的服務，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent、 [!INCLUDE[ssRS](../../includes/ssrs.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)]，以及使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 做為資料存放區的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="9637c-215">Stop all services connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)], and all applications using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as data store.</span></span>  
  
2.  <span data-ttu-id="9637c-216">使用命令 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從命令列啟動 `NET START MSSQLSERVER /T3608`</span><span class="sxs-lookup"><span data-stu-id="9637c-216">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command line using the command: `NET START MSSQLSERVER /T3608`</span></span>  
  
     <span data-ttu-id="9637c-217">如需詳細資訊，請參閱 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9637c-217">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="9637c-218">在另一個命令列視窗中， `msdb` 執行下列命令來卸離資料庫， *\<servername>* 並將取代為的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span><span class="sxs-lookup"><span data-stu-id="9637c-218">In another command line window, detach the `msdb` database by executing the following command, replacing *\<servername>* with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span></span>  
  
4.  <span data-ttu-id="9637c-219">使用 Windows Explorer 重新命名資料庫檔案 `msdb` 。</span><span class="sxs-lookup"><span data-stu-id="9637c-219">Using the Windows Explorer, rename the `msdb` database files.</span></span> <span data-ttu-id="9637c-220">根據預設，這些檔案位於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 DATA 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9637c-220">By default these are in the DATA sub-folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="9637c-221">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員正常停止並重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="9637c-221">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service normally.</span></span>  
  
6.  <span data-ttu-id="9637c-222">在命令列視窗中，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並執行命令： `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span><span class="sxs-lookup"><span data-stu-id="9637c-222">In a command line window, connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and execute the command: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span></span>  
  
     <span data-ttu-id="9637c-223">將 *\<servername>* 取代為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9637c-223">Replace *\<servername>* with the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="9637c-224">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的檔案系統路徑。</span><span class="sxs-lookup"><span data-stu-id="9637c-224">Use the file system path of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
7.  <span data-ttu-id="9637c-225">使用 [Windows 記事本] 開啟 **instmsdb.out** 檔，並檢查輸出是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9637c-225">Using the Windows Notepad, open the **instmsdb.out** file and check the output for any errors.</span></span>  
  
8.  <span data-ttu-id="9637c-226">在執行個體上重新套用任何已安裝的 Service Pack 或 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="9637c-226">Re-apply any service packs or hotfix installed on the instance.</span></span>  
  
9. <span data-ttu-id="9637c-227">重新建立儲存在資料庫中的使用者內容 `msdb` ，例如工作、警示等。</span><span class="sxs-lookup"><span data-stu-id="9637c-227">Recreate the user content stored in the `msdb` database, such as jobs, alert, etc.</span></span>  
  
10. <span data-ttu-id="9637c-228">備份 `msdb` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9637c-228">Backup the `msdb` database.</span></span>  
  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> <span data-ttu-id="9637c-229">疑難排解重建錯誤</span><span class="sxs-lookup"><span data-stu-id="9637c-229">Troubleshoot Rebuild Errors</span></span>  
 <span data-ttu-id="9637c-230">語法和其他執行階段錯誤會顯示在 [命令提示字元] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="9637c-230">Syntax and other run-time errors are displayed in the command prompt window.</span></span> <span data-ttu-id="9637c-231">您可以檢查安裝程式陳述式是否有下列語法錯誤：</span><span class="sxs-lookup"><span data-stu-id="9637c-231">Examine the Setup statement for the following syntax errors:</span></span>  
  
-   <span data-ttu-id="9637c-232">在每個參數名稱前面遺漏了斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="9637c-232">Missing slash mark (/) in front of each parameter name.</span></span>  
  
-   <span data-ttu-id="9637c-233">在參數名稱與參數值之間遺漏了等號 (=)。</span><span class="sxs-lookup"><span data-stu-id="9637c-233">Missing equal sign (=) between the parameter name and the parameter value.</span></span>  
  
-   <span data-ttu-id="9637c-234">在參數名稱與等號之間存在空格。</span><span class="sxs-lookup"><span data-stu-id="9637c-234">Presence of blank spaces between the parameter name and the equal sign.</span></span>  
  
-   <span data-ttu-id="9637c-235">存在逗號 (,) 或語法中並未指定的其他字元。</span><span class="sxs-lookup"><span data-stu-id="9637c-235">Presence of commas (,) or other characters that are not specified in the syntax.</span></span>  
  
 <span data-ttu-id="9637c-236">重建作業完成之後，請檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9637c-236">After the rebuild operation is complete, examine the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs for any errors.</span></span> <span data-ttu-id="9637c-237">預設記錄檔位置是 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs。</span><span class="sxs-lookup"><span data-stu-id="9637c-237">The default log location is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span> <span data-ttu-id="9637c-238">若要找出包含重建程序結果的記錄檔，請在命令提示字元中，將目錄變更為 Logs 資料夾，然後執行 `findstr /s RebuildDatabase summary*.*`。</span><span class="sxs-lookup"><span data-stu-id="9637c-238">To locate the log file that contains the results of the rebuild process, change directories to the Logs folder from a command prompt, and then run `findstr /s RebuildDatabase summary*.*`.</span></span> <span data-ttu-id="9637c-239">這項搜尋將會為您指出包含重建系統資料庫結果的任何記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9637c-239">This search will point you to any log files that contain the results of rebuilding system databases.</span></span> <span data-ttu-id="9637c-240">您可以開啟這些記錄檔，然後檢查它們是否有相關的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9637c-240">Open the log files and examine them for relevant error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9637c-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9637c-241">See Also</span></span>  
 [<span data-ttu-id="9637c-242">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="9637c-242">System Databases</span></span>](system-databases.md)  
  
  
