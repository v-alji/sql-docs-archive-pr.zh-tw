---
title: 設定資料庫鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
ms.assetid: da45efed-55eb-4c71-be34-ac2589dfce8d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7e55e973ffbb888394d13578f21e08a08ae9d03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596884"
---
# <a name="setting-up-database-mirroring-sql-server"></a><span data-ttu-id="8f628-102">設定資料庫鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f628-102">Setting Up Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="8f628-103">本節描述的是設定資料庫鏡像的必要條件、建議事項及步驟。</span><span class="sxs-lookup"><span data-stu-id="8f628-103">This section describes the prerequisites, recommendations, and steps for setting up database mirroring.</span></span> <span data-ttu-id="8f628-104">如需資料庫鏡像的簡介，請參閱 [資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-104">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8f628-105">我們建議您在離峰時間設定資料庫鏡像，因為組態會影響效能。</span><span class="sxs-lookup"><span data-stu-id="8f628-105">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
 
  
##  <a name="preparing-a-server-instance-to-host-a-mirror-server"></a><a name="PrepareInstances"></a> <span data-ttu-id="8f628-106">準備伺服器執行個體以裝載鏡像伺服器</span><span class="sxs-lookup"><span data-stu-id="8f628-106">Preparing a Server Instance to Host a Mirror Server</span></span>  
 <span data-ttu-id="8f628-107">在資料庫鏡像工作階段中：</span><span class="sxs-lookup"><span data-stu-id="8f628-107">For each database mirroring session:</span></span>  
  
1.  <span data-ttu-id="8f628-108">主體伺服器、鏡像伺服器和見證 (如果有的話) 必須是由位於個別主機系統上的個別伺服器執行個體所裝載。</span><span class="sxs-lookup"><span data-stu-id="8f628-108">The principal server, mirror server, and witness, if any, must be hosted by separate server instances, which should be on separate host systems.</span></span> <span data-ttu-id="8f628-109">每一個伺服器執行個體都需要資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="8f628-109">Each of the server instances requires a database mirroring endpoint.</span></span> <span data-ttu-id="8f628-110">如果您需要建立資料庫鏡像端點，請確定其他伺服器執行個體能夠存取它。</span><span class="sxs-lookup"><span data-stu-id="8f628-110">If you need to create a database mirroring endpoint, ensure that it is accessible to the other server instances.</span></span>  
  
     <span data-ttu-id="8f628-111">伺服器執行個體用於資料庫鏡像的驗證格式，是其資料庫鏡像端點的屬性。</span><span class="sxs-lookup"><span data-stu-id="8f628-111">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="8f628-112">有兩種傳輸安全性可用於資料庫鏡像：Windows 驗證或以憑證為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="8f628-112">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="8f628-113">如需詳細資訊，請參閱[資料庫鏡像的傳輸安全性和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-113">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="8f628-114">網路存取的需求與驗證形式相關，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f628-114">The requirements for network access are specific to the form of authentication, as follows:</span></span>  
  
    -   <span data-ttu-id="8f628-115">**如果使用 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="8f628-115">**If using Windows Authentication**</span></span>  
  
         <span data-ttu-id="8f628-116">如果伺服器執行個體正在不同的網域使用者帳戶下執行，每個執行個體都會需要登入其他執行個體的 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f628-116">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="8f628-117">如果登入不存在，您就必須自行建立。</span><span class="sxs-lookup"><span data-stu-id="8f628-117">If the login does not exist, you must create it.</span></span> <span data-ttu-id="8f628-118">如需詳細資訊，請參閱 [使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-118">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
    -   <span data-ttu-id="8f628-119">**如果使用憑證**</span><span class="sxs-lookup"><span data-stu-id="8f628-119">**If using certificates**</span></span>  
  
         <span data-ttu-id="8f628-120">若要啟用某伺服器執行個體上資料庫鏡像的憑證驗證，系統管理員必須設定每一個伺服器執行個體，才能同時在傳出和傳入的連接使用憑證。</span><span class="sxs-lookup"><span data-stu-id="8f628-120">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="8f628-121">您必須先設定傳出連接。</span><span class="sxs-lookup"><span data-stu-id="8f628-121">Outbound connections must be configured first.</span></span> <span data-ttu-id="8f628-122">如需詳細資訊，請參閱[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-122">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="8f628-123">確定所有資料庫使用者的登入都存在於鏡像伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8f628-123">Make sure that logins exist on the mirror server for all the database users.</span></span> <span data-ttu-id="8f628-124">如需詳細資訊，請參閱[設定資料庫鏡像的登入帳戶或 AlwaysOn 可用性群組 &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-124">For more information, see [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
3.  <span data-ttu-id="8f628-125">在即將裝載鏡像資料庫的伺服器執行個體上，設定鏡像資料庫所需的其餘環境。</span><span class="sxs-lookup"><span data-stu-id="8f628-125">On the server instance that will host the mirror database, set up the rest of the environment that is required for the mirrored database.</span></span> <span data-ttu-id="8f628-126">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-126">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="overview-establishing-a-database-mirroring-session"></a><a name="EstablishUsingWinAuthentication"></a> <span data-ttu-id="8f628-127">概觀：建立資料庫鏡像工作階段</span><span class="sxs-lookup"><span data-stu-id="8f628-127">Overview: Establishing a Database Mirroring Session</span></span>  
 <span data-ttu-id="8f628-128">建立鏡像工作階段的基本步驟如下：</span><span class="sxs-lookup"><span data-stu-id="8f628-128">The basic steps for establishing a mirroring session are as follows:</span></span>  
  
1.  <span data-ttu-id="8f628-129">在每項還原作業上使用 RESTORE WITH NORECOVERY，透過還原下列備份來建立鏡像資料庫：</span><span class="sxs-lookup"><span data-stu-id="8f628-129">Create the mirror database by restoring the following backups, using RESTORE WITH NORECOVERY on every restore operation:</span></span>  
  
    1.  <span data-ttu-id="8f628-130">在確定建立備份時主體資料庫已經使用完整復原模式之後，還原主體資料庫最近的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="8f628-130">Restore a recent full database backup of the principal database, after making sure that the principal database was already using the full recovery model when the backup was taken.</span></span> <span data-ttu-id="8f628-131">鏡像資料庫必須擁有與主體資料庫相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f628-131">The mirror database must have the same name as the principal database.</span></span>  
  
    2.  <span data-ttu-id="8f628-132">如果自還原完整備份之後您已經建立任何差異資料庫備份，請還原最近的差異備份。</span><span class="sxs-lookup"><span data-stu-id="8f628-132">If you have taken any differential backups of the database since the restored full backup, restore your most recent differential backup.</span></span>  
  
    3.  <span data-ttu-id="8f628-133">還原自從完整或差異資料庫備份後進行的所有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="8f628-133">Restore all the log backups done since the full or differential database backup.</span></span>  
  
     <span data-ttu-id="8f628-134">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8f628-135">進行主體資料庫的備份後，請儘快完成剩下的設定步驟。</span><span class="sxs-lookup"><span data-stu-id="8f628-135">Complete the remaining setup steps as soon as you can after taking the backup of the principal database.</span></span> <span data-ttu-id="8f628-136">在夥伴上啟動鏡像之前，您應該在原始資料庫上建立目前的記錄備份，並將它還原到未來的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f628-136">Before you can start mirroring on the partners, you should create a current log backup on the original database and restore it to the future mirror database.</span></span>  
  
2.  <span data-ttu-id="8f628-137">您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或「資料庫鏡像精靈」來設定鏡像。</span><span class="sxs-lookup"><span data-stu-id="8f628-137">You can set up mirroring by using either [!INCLUDE[tsql](../../includes/tsql-md.md)] or the Database Mirroring Wizard.</span></span> <span data-ttu-id="8f628-138">如需詳細資訊，請參閱下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="8f628-138">For more information, see one of the following:</span></span>  
  
    -   [<span data-ttu-id="8f628-139">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-139">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
    -   [<span data-ttu-id="8f628-140">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
3.  <span data-ttu-id="8f628-141">依預設，工作階段會設定為完整交易安全性 (SAFETY 設定為 FULL)，它會以不含自動容錯移轉的同步高安全性模式啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="8f628-141">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="8f628-142">您可以依照下列方式，將工作階段重新設定為在具有自動容錯移轉的高安全性模式下執行，或在非同步的高效能模式下執行：</span><span class="sxs-lookup"><span data-stu-id="8f628-142">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="8f628-143">**具有自動容錯移轉的高安全性模式**</span><span class="sxs-lookup"><span data-stu-id="8f628-143">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="8f628-144">如果您想讓高安全性模式工作階段支援自動容錯移轉，請加入見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f628-144">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span>  
  
         <span data-ttu-id="8f628-145">**加入見證**</span><span class="sxs-lookup"><span data-stu-id="8f628-145">**To add a witness**</span></span>  
  
        -   [<span data-ttu-id="8f628-146">使用 Windows 驗證新增資料庫鏡像見證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-146">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
        -   [<span data-ttu-id="8f628-147">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-147">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
        > [!NOTE]  
        >  <span data-ttu-id="8f628-148">資料庫擁有者可以隨時關閉資料庫的見證。</span><span class="sxs-lookup"><span data-stu-id="8f628-148">The database owner can turn off the witness for a database at any time.</span></span> <span data-ttu-id="8f628-149">見證關閉後相當於沒有見證，不會發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="8f628-149">Turning off the witness is equivalent to having no witness, and automatic failover cannot occur.</span></span>  
  
    -   <span data-ttu-id="8f628-150">**高效能模式**</span><span class="sxs-lookup"><span data-stu-id="8f628-150">**High-performance mode**</span></span>  
  
         <span data-ttu-id="8f628-151">或者，如果您不想進行自動容錯移轉，而且較注重效能而非可用性，請關閉交易安全性。</span><span class="sxs-lookup"><span data-stu-id="8f628-151">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="8f628-152">如需詳細資訊，請參閱[在資料庫鏡像工作階段中變更交易安全性 &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-152">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8f628-153">在高效能模式中，WITNESS 需要設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="8f628-153">In high-performance mode, WITNESS needs to be set to OFF.</span></span> <span data-ttu-id="8f628-154">如需詳細資訊，請參閱[仲裁：見證如何影響資料庫可用性 &#40;資料庫鏡像&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-154">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f628-155">如需使用 Microsoft Windows 驗證以 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定資料庫鏡像的範例，請參閱[範例：使用 Windows 驗證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-155">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using Microsoft Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span></span>  
>   
>  <span data-ttu-id="8f628-156">如需使用以憑證為基礎的安全性以 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定資料庫鏡像範例，請參閱[範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8f628-156">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using certificate-based security, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
 
  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="8f628-157">本節內容</span><span class="sxs-lookup"><span data-stu-id="8f628-157">In This Section</span></span>  
 [<span data-ttu-id="8f628-158">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-158">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
 <span data-ttu-id="8f628-159">摘要說明在繼續進行暫停的工作階段之前，建立鏡像資料庫或準備鏡像資料庫的步驟。</span><span class="sxs-lookup"><span data-stu-id="8f628-159">Summarizes the steps for creating a mirror database or preparing a mirror database before resuming a suspended session.</span></span> <span data-ttu-id="8f628-160">同時提供如何主題的連結。</span><span class="sxs-lookup"><span data-stu-id="8f628-160">Also provides links to how-to topics.</span></span>  
  
 [<span data-ttu-id="8f628-161">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-161">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
 <span data-ttu-id="8f628-162">描述伺服器網路位址的語法、位址如何識別伺服器執行個體的資料庫鏡像端點，以及如何找出系統的完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="8f628-162">Describes the syntax of a server network address, how the address identifies the database mirroring endpoint of the server instance, and how to find the fully-qualified domain name of a system.</span></span>  
  
 [<span data-ttu-id="8f628-163">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-163">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
 <span data-ttu-id="8f628-164">描述如何使用設定資料庫鏡像安全性精靈，在資料庫上啟動資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="8f628-164">Describes how to use the Configure Database Mirroring Security Wizard to start database mirroring on a database.</span></span>  
  
 [<span data-ttu-id="8f628-165">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-165">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
 <span data-ttu-id="8f628-166">描述設定資料庫鏡像的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步驟。</span><span class="sxs-lookup"><span data-stu-id="8f628-166">Describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] steps for setting up database mirroring.</span></span>  
  
 [<span data-ttu-id="8f628-167">範例：使用 Windows 驗證設定資料庫鏡像 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-167">Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)  
 <span data-ttu-id="8f628-168">包含一則範例，內容說明使用 Windows 驗證建立具有見證之資料庫鏡像工作階段的所有必要階段。</span><span class="sxs-lookup"><span data-stu-id="8f628-168">Contains an example of all the stages required to create a database mirroring session with a witness, using Windows Authentication.</span></span>  
  
 [<span data-ttu-id="8f628-169">範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-169">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
 <span data-ttu-id="8f628-170">包含一則範例，內容說明使用以憑證為基礎的驗證建立具有見證之資料庫鏡像工作階段的所有必要階段。</span><span class="sxs-lookup"><span data-stu-id="8f628-170">Contains an example of all the stages required to create a database mirroring session with a witness, using certificate-based authentication.</span></span>  
  
 [<span data-ttu-id="8f628-171">設定資料庫鏡像的登入帳戶，或 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-171">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
 <span data-ttu-id="8f628-172">描述針對使用與本機伺服器執行個體不同之帳戶的遠端伺服器執行個體，建立登入。</span><span class="sxs-lookup"><span data-stu-id="8f628-172">Describes creating a login for a remote server instance that is using a different account than the local server instance.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8f628-173">相關工作</span><span class="sxs-lookup"><span data-stu-id="8f628-173">Related Tasks</span></span>  
 <span data-ttu-id="8f628-174">**SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="8f628-174">**SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8f628-175">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-175">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="8f628-176">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-176">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
 <span data-ttu-id="8f628-177">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="8f628-177">**Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="8f628-178">使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-178">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;</span></span>](../database-mirroring-allow-network-access-windows-authentication.md)  
  
-   [<span data-ttu-id="8f628-179">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-179">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="8f628-180">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-180">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="8f628-181">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-181">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="8f628-182">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-182">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="8f628-183">使用 Windows 驗證新增資料庫鏡像見證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-183">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="8f628-184">設定鏡像資料庫以使用 Trustworthy 屬性 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-184">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
 <span data-ttu-id="8f628-185">**Transact-SQL/SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="8f628-185">**Transact-SQL/SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="8f628-186">在升級伺服器執行個體時將鏡像資料庫的停機時間減至最少</span><span class="sxs-lookup"><span data-stu-id="8f628-186">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>](upgrading-mirrored-instances.md)  
  
-   [<span data-ttu-id="8f628-187">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-187">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="8f628-188">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-188">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="8f628-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f628-189">See Also</span></span>  
 <span data-ttu-id="8f628-190">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f628-190">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="8f628-191">[資料庫鏡像：互通性與共存性 &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f628-191">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="8f628-192">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="8f628-192">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="8f628-193">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="8f628-193">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
  
