---
title: master 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac38453237ed6816c32ed974e8141c57c93ceb44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709526"
---
# <a name="master-database"></a><span data-ttu-id="3ef35-102">master 資料庫</span><span class="sxs-lookup"><span data-stu-id="3ef35-102">master Database</span></span>
  <span data-ttu-id="3ef35-103">**master** 資料庫會記錄 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統的所有系統層級資訊。</span><span class="sxs-lookup"><span data-stu-id="3ef35-103">The **master** database records all the system-level information for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system.</span></span> <span data-ttu-id="3ef35-104">這包括了整個執行個體範圍的中繼資料，例如登入帳戶、端點、連結的伺服器，以及系統組態設定。</span><span class="sxs-lookup"><span data-stu-id="3ef35-104">This includes instance-wide metadata such as logon accounts, endpoints, linked servers, and system configuration settings.</span></span> <span data-ttu-id="3ef35-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，系統物件不再儲存於 **master** 資料庫，而是儲存於 [Resource 資料庫](resource-database.md)。</span><span class="sxs-lookup"><span data-stu-id="3ef35-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], system objects are no longer stored in the **master** database; instead, they are stored in the [Resource database](resource-database.md).</span></span> <span data-ttu-id="3ef35-106">**master** 資料庫也會記錄所有其他資料庫的存在與這些資料庫檔案的所在位置，並記錄 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="3ef35-106">Also, **master** is the database that records the existence of all other databases and the location of those database files and records the initialization information for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ef35-107">因此，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] master **資料庫無法使用，** 也會無法啟動。</span><span class="sxs-lookup"><span data-stu-id="3ef35-107">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot start if the **master** database is unavailable.</span></span>  
  
## <a name="physical-properties-of-master"></a><span data-ttu-id="3ef35-108">master 的實體屬性</span><span class="sxs-lookup"><span data-stu-id="3ef35-108">Physical Properties of master</span></span>  
 <span data-ttu-id="3ef35-109">下表列出了 **master** 資料與記錄檔的初始組態值。</span><span class="sxs-lookup"><span data-stu-id="3ef35-109">The following table lists the initial configuration values of the **master** data and log files.</span></span> <span data-ttu-id="3ef35-110">對於不同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，這些檔案的大小稍有不同。</span><span class="sxs-lookup"><span data-stu-id="3ef35-110">The sizes of these files may vary slightly for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="3ef35-111">檔案</span><span class="sxs-lookup"><span data-stu-id="3ef35-111">File</span></span>|<span data-ttu-id="3ef35-112">邏輯名稱</span><span class="sxs-lookup"><span data-stu-id="3ef35-112">Logical name</span></span>|<span data-ttu-id="3ef35-113">實體名稱</span><span class="sxs-lookup"><span data-stu-id="3ef35-113">Physical name</span></span>|<span data-ttu-id="3ef35-114">檔案成長</span><span class="sxs-lookup"><span data-stu-id="3ef35-114">File growth</span></span>|  
|----------|------------------|-------------------|-----------------|  
|<span data-ttu-id="3ef35-115">主要資料</span><span class="sxs-lookup"><span data-stu-id="3ef35-115">Primary data</span></span>|<span data-ttu-id="3ef35-116">master</span><span class="sxs-lookup"><span data-stu-id="3ef35-116">master</span></span>|<span data-ttu-id="3ef35-117">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="3ef35-117">master.mdf</span></span>|<span data-ttu-id="3ef35-118">以 10% 的比例自動成長，直到磁碟已滿。</span><span class="sxs-lookup"><span data-stu-id="3ef35-118">Autogrow by 10 percent until the disk is full.</span></span>|  
|<span data-ttu-id="3ef35-119">Log</span><span class="sxs-lookup"><span data-stu-id="3ef35-119">Log</span></span>|<span data-ttu-id="3ef35-120">mastlog</span><span class="sxs-lookup"><span data-stu-id="3ef35-120">mastlog</span></span>|<span data-ttu-id="3ef35-121">mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="3ef35-121">mastlog.ldf</span></span>|<span data-ttu-id="3ef35-122">以 10% 的比例自動成長，最大至 2 TB。</span><span class="sxs-lookup"><span data-stu-id="3ef35-122">Autogrow by 10 percent to a maximum of 2 terabytes.</span></span>|  
  
 <span data-ttu-id="3ef35-123">如需如何移動 **master** 資料與記錄檔的資訊，請參閱 [移動系統資料庫](system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="3ef35-123">For information about how to move the **master** data and log files, see [Move System Databases](system-databases.md).</span></span>  
  
### <a name="database-options"></a><span data-ttu-id="3ef35-124">資料庫選項</span><span class="sxs-lookup"><span data-stu-id="3ef35-124">Database Options</span></span>  
 <span data-ttu-id="3ef35-125">下表列出了 **master** 資料庫中每個資料庫選項的預設值，以及是否可修改該選項。</span><span class="sxs-lookup"><span data-stu-id="3ef35-125">The following table lists the default value for each database option in the **master** database and whether the option can be modified.</span></span> <span data-ttu-id="3ef35-126">若要檢視這些選項目前的設定，請參閱 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="3ef35-126">To view the current settings for these options, use the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
|<span data-ttu-id="3ef35-127">資料庫選項</span><span class="sxs-lookup"><span data-stu-id="3ef35-127">Database option</span></span>|<span data-ttu-id="3ef35-128">預設值</span><span class="sxs-lookup"><span data-stu-id="3ef35-128">Default value</span></span>|<span data-ttu-id="3ef35-129">可以修改</span><span class="sxs-lookup"><span data-stu-id="3ef35-129">Can be modified</span></span>|  
|---------------------|-------------------|---------------------|  
|<span data-ttu-id="3ef35-130">ALLOW_SNAPSHOT_ISOLATION</span><span class="sxs-lookup"><span data-stu-id="3ef35-130">ALLOW_SNAPSHOT_ISOLATION</span></span>|<span data-ttu-id="3ef35-131">開啟</span><span class="sxs-lookup"><span data-stu-id="3ef35-131">ON</span></span>|<span data-ttu-id="3ef35-132">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-132">No</span></span>|  
|<span data-ttu-id="3ef35-133">ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3ef35-133">ANSI_NULL_DEFAULT</span></span>|<span data-ttu-id="3ef35-134">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-134">OFF</span></span>|<span data-ttu-id="3ef35-135">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-135">Yes</span></span>|  
|<span data-ttu-id="3ef35-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="3ef35-136">ANSI_NULLS</span></span>|<span data-ttu-id="3ef35-137">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-137">OFF</span></span>|<span data-ttu-id="3ef35-138">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-138">Yes</span></span>|  
|<span data-ttu-id="3ef35-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="3ef35-139">ANSI_PADDING</span></span>|<span data-ttu-id="3ef35-140">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-140">OFF</span></span>|<span data-ttu-id="3ef35-141">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-141">Yes</span></span>|  
|<span data-ttu-id="3ef35-142">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="3ef35-142">ANSI_WARNINGS</span></span>|<span data-ttu-id="3ef35-143">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-143">OFF</span></span>|<span data-ttu-id="3ef35-144">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-144">Yes</span></span>|  
|<span data-ttu-id="3ef35-145">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="3ef35-145">ARITHABORT</span></span>|<span data-ttu-id="3ef35-146">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-146">OFF</span></span>|<span data-ttu-id="3ef35-147">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-147">Yes</span></span>|  
|<span data-ttu-id="3ef35-148">AUTO_CLOSE</span><span class="sxs-lookup"><span data-stu-id="3ef35-148">AUTO_CLOSE</span></span>|<span data-ttu-id="3ef35-149">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-149">OFF</span></span>|<span data-ttu-id="3ef35-150">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-150">No</span></span>|  
|<span data-ttu-id="3ef35-151">AUTO_CREATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="3ef35-151">AUTO_CREATE_STATISTICS</span></span>|<span data-ttu-id="3ef35-152">開啟</span><span class="sxs-lookup"><span data-stu-id="3ef35-152">ON</span></span>|<span data-ttu-id="3ef35-153">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-153">Yes</span></span>|  
|<span data-ttu-id="3ef35-154">AUTO_SHRINK</span><span class="sxs-lookup"><span data-stu-id="3ef35-154">AUTO_SHRINK</span></span>|<span data-ttu-id="3ef35-155">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-155">OFF</span></span>|<span data-ttu-id="3ef35-156">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-156">No</span></span>|  
|<span data-ttu-id="3ef35-157">AUTO_UPDATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="3ef35-157">AUTO_UPDATE_STATISTICS</span></span>|<span data-ttu-id="3ef35-158">開啟</span><span class="sxs-lookup"><span data-stu-id="3ef35-158">ON</span></span>|<span data-ttu-id="3ef35-159">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-159">Yes</span></span>|  
|<span data-ttu-id="3ef35-160">AUTO_UPDATE_STATISTICS_ASYNC</span><span class="sxs-lookup"><span data-stu-id="3ef35-160">AUTO_UPDATE_STATISTICS_ASYNC</span></span>|<span data-ttu-id="3ef35-161">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-161">OFF</span></span>|<span data-ttu-id="3ef35-162">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-162">Yes</span></span>|  
|<span data-ttu-id="3ef35-163">CHANGE_TRACKING</span><span class="sxs-lookup"><span data-stu-id="3ef35-163">CHANGE_TRACKING</span></span>|<span data-ttu-id="3ef35-164">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-164">OFF</span></span>|<span data-ttu-id="3ef35-165">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-165">No</span></span>|  
|<span data-ttu-id="3ef35-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="3ef35-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="3ef35-167">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-167">OFF</span></span>|<span data-ttu-id="3ef35-168">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-168">Yes</span></span>|  
|<span data-ttu-id="3ef35-169">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="3ef35-169">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="3ef35-170">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-170">OFF</span></span>|<span data-ttu-id="3ef35-171">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-171">Yes</span></span>|  
|<span data-ttu-id="3ef35-172">CURSOR_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3ef35-172">CURSOR_DEFAULT</span></span>|<span data-ttu-id="3ef35-173">GLOBAL</span><span class="sxs-lookup"><span data-stu-id="3ef35-173">GLOBAL</span></span>|<span data-ttu-id="3ef35-174">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-174">Yes</span></span>|  
|<span data-ttu-id="3ef35-175">資料庫可用性選項</span><span class="sxs-lookup"><span data-stu-id="3ef35-175">Database Availability Options</span></span>|<span data-ttu-id="3ef35-176">ONLINE</span><span class="sxs-lookup"><span data-stu-id="3ef35-176">ONLINE</span></span><br /><br /> <span data-ttu-id="3ef35-177">MULTI_USER</span><span class="sxs-lookup"><span data-stu-id="3ef35-177">MULTI_USER</span></span><br /><br /> <span data-ttu-id="3ef35-178">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="3ef35-178">READ_WRITE</span></span>|<span data-ttu-id="3ef35-179">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-179">No</span></span><br /><br /> <span data-ttu-id="3ef35-180">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-180">No</span></span><br /><br /> <span data-ttu-id="3ef35-181">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-181">No</span></span>|  
|<span data-ttu-id="3ef35-182">DATE_CORRELATION_OPTIMIZATION</span><span class="sxs-lookup"><span data-stu-id="3ef35-182">DATE_CORRELATION_OPTIMIZATION</span></span>|<span data-ttu-id="3ef35-183">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-183">OFF</span></span>|<span data-ttu-id="3ef35-184">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-184">Yes</span></span>|  
|<span data-ttu-id="3ef35-185">DB_CHAINING</span><span class="sxs-lookup"><span data-stu-id="3ef35-185">DB_CHAINING</span></span>|<span data-ttu-id="3ef35-186">開啟</span><span class="sxs-lookup"><span data-stu-id="3ef35-186">ON</span></span>|<span data-ttu-id="3ef35-187">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-187">No</span></span>|  
|<span data-ttu-id="3ef35-188">ENCRYPTION</span><span class="sxs-lookup"><span data-stu-id="3ef35-188">ENCRYPTION</span></span>|<span data-ttu-id="3ef35-189">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-189">OFF</span></span>|<span data-ttu-id="3ef35-190">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-190">No</span></span>|  
|<span data-ttu-id="3ef35-191">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="3ef35-191">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="3ef35-192">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-192">OFF</span></span>|<span data-ttu-id="3ef35-193">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-193">Yes</span></span>|  
|<span data-ttu-id="3ef35-194">PAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="3ef35-194">PAGE_VERIFY</span></span>|<span data-ttu-id="3ef35-195">CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="3ef35-195">CHECKSUM</span></span>|<span data-ttu-id="3ef35-196">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-196">Yes</span></span>|  
|<span data-ttu-id="3ef35-197">PARAMETERIZATION</span><span class="sxs-lookup"><span data-stu-id="3ef35-197">PARAMETERIZATION</span></span>|<span data-ttu-id="3ef35-198">簡單</span><span class="sxs-lookup"><span data-stu-id="3ef35-198">SIMPLE</span></span>|<span data-ttu-id="3ef35-199">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-199">Yes</span></span>|  
|<span data-ttu-id="3ef35-200">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="3ef35-200">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="3ef35-201">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-201">OFF</span></span>|<span data-ttu-id="3ef35-202">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-202">Yes</span></span>|  
|<span data-ttu-id="3ef35-203">READ_COMMITTED_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="3ef35-203">READ_COMMITTED_SNAPSHOT</span></span>|<span data-ttu-id="3ef35-204">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-204">OFF</span></span>|<span data-ttu-id="3ef35-205">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-205">No</span></span>|  
|<span data-ttu-id="3ef35-206">RECOVERY</span><span class="sxs-lookup"><span data-stu-id="3ef35-206">RECOVERY</span></span>|<span data-ttu-id="3ef35-207">簡單</span><span class="sxs-lookup"><span data-stu-id="3ef35-207">SIMPLE</span></span>|<span data-ttu-id="3ef35-208">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-208">Yes</span></span>|  
|<span data-ttu-id="3ef35-209">RECURSIVE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="3ef35-209">RECURSIVE_TRIGGERS</span></span>|<span data-ttu-id="3ef35-210">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-210">OFF</span></span>|<span data-ttu-id="3ef35-211">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-211">Yes</span></span>|  
|<span data-ttu-id="3ef35-212">Service Broker 選項</span><span class="sxs-lookup"><span data-stu-id="3ef35-212">Service Broker Options</span></span>|<span data-ttu-id="3ef35-213">DISABLE_BROKER</span><span class="sxs-lookup"><span data-stu-id="3ef35-213">DISABLE_BROKER</span></span>|<span data-ttu-id="3ef35-214">否</span><span class="sxs-lookup"><span data-stu-id="3ef35-214">No</span></span>|  
|<span data-ttu-id="3ef35-215">TRUSTWORTHY</span><span class="sxs-lookup"><span data-stu-id="3ef35-215">TRUSTWORTHY</span></span>|<span data-ttu-id="3ef35-216">OFF</span><span class="sxs-lookup"><span data-stu-id="3ef35-216">OFF</span></span>|<span data-ttu-id="3ef35-217">是</span><span class="sxs-lookup"><span data-stu-id="3ef35-217">Yes</span></span>|  
  
 <span data-ttu-id="3ef35-218">如需這些資料庫選項的描述，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3ef35-218">For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="3ef35-219">限制</span><span class="sxs-lookup"><span data-stu-id="3ef35-219">Restrictions</span></span>  
 <span data-ttu-id="3ef35-220">您不能在 **master** 資料庫上執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3ef35-220">The following operations cannot be performed on the **master** database:</span></span>  
  
-   <span data-ttu-id="3ef35-221">加入檔案或檔案群組。</span><span class="sxs-lookup"><span data-stu-id="3ef35-221">Adding files or filegroups.</span></span>  
  
-   <span data-ttu-id="3ef35-222">變更定序。</span><span class="sxs-lookup"><span data-stu-id="3ef35-222">Changing collation.</span></span> <span data-ttu-id="3ef35-223">預設定序是伺服器定序。</span><span class="sxs-lookup"><span data-stu-id="3ef35-223">The default collation is the server collation.</span></span>  
  
-   <span data-ttu-id="3ef35-224">變更資料庫擁有者。</span><span class="sxs-lookup"><span data-stu-id="3ef35-224">Changing the database owner.</span></span> <span data-ttu-id="3ef35-225">**master** 是由 **sa**所擁有。</span><span class="sxs-lookup"><span data-stu-id="3ef35-225">**master** is owned by **sa**.</span></span>  
  
-   <span data-ttu-id="3ef35-226">建立全文檢索目錄或全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="3ef35-226">Creating a full-text catalog or full-text index.</span></span>  
  
-   <span data-ttu-id="3ef35-227">在資料庫中的系統資料表上建立觸發程序。</span><span class="sxs-lookup"><span data-stu-id="3ef35-227">Creating triggers on system tables in the database.</span></span>  
  
-   <span data-ttu-id="3ef35-228">卸除資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ef35-228">Dropping the database.</span></span>  
  
-   <span data-ttu-id="3ef35-229">從資料庫卸載**來賓**使用者。</span><span class="sxs-lookup"><span data-stu-id="3ef35-229">Dropping the **guest** user from the database.</span></span>  
  
-   <span data-ttu-id="3ef35-230">啟用異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="3ef35-230">Enabling change data capture.</span></span>  
  
-   <span data-ttu-id="3ef35-231">參與資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="3ef35-231">Participating in database mirroring.</span></span>  
  
-   <span data-ttu-id="3ef35-232">移除主要檔案群組、主要資料檔或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ef35-232">Removing the primary filegroup, primary data file, or log file.</span></span>  
  
-   <span data-ttu-id="3ef35-233">重新命名資料庫或主要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="3ef35-233">Renaming the database or primary filegroup.</span></span>  
  
-   <span data-ttu-id="3ef35-234">將資料庫設定為 OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="3ef35-234">Setting the database to OFFLINE.</span></span>  
  
-   <span data-ttu-id="3ef35-235">將資料庫或主要檔案群組設定為 READ_ONLY。</span><span class="sxs-lookup"><span data-stu-id="3ef35-235">Setting the database or primary filegroup to READ_ONLY.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="3ef35-236">建議</span><span class="sxs-lookup"><span data-stu-id="3ef35-236">Recommendations</span></span>  
 <span data-ttu-id="3ef35-237">當您使用 **master** 資料庫時，請考慮下列建議：</span><span class="sxs-lookup"><span data-stu-id="3ef35-237">When you work with the **master** database, consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="3ef35-238">永遠保留 **master** 資料庫的最新備份。</span><span class="sxs-lookup"><span data-stu-id="3ef35-238">Always have a current backup of the **master** database available.</span></span>  
  
-   <span data-ttu-id="3ef35-239">在執行下列作業後，立即備份 **master** 資料庫：</span><span class="sxs-lookup"><span data-stu-id="3ef35-239">Back up the **master** database as soon as possible after the following operations:</span></span>  
  
    -   <span data-ttu-id="3ef35-240">建立、修改或卸除任何資料庫</span><span class="sxs-lookup"><span data-stu-id="3ef35-240">Creating, modifying, or dropping any database</span></span>  
  
    -   <span data-ttu-id="3ef35-241">變更伺服器或資料庫組態值</span><span class="sxs-lookup"><span data-stu-id="3ef35-241">Changing server or database configuration values</span></span>  
  
    -   <span data-ttu-id="3ef35-242">修改或加入登入帳戶</span><span class="sxs-lookup"><span data-stu-id="3ef35-242">Modifying or adding logon accounts</span></span>  
  
-   <span data-ttu-id="3ef35-243">請勿在 **master**中建立使用者物件。</span><span class="sxs-lookup"><span data-stu-id="3ef35-243">Do not create user objects in **master**.</span></span> <span data-ttu-id="3ef35-244">如果您這樣做，就必須更經常地備份 **master** 。</span><span class="sxs-lookup"><span data-stu-id="3ef35-244">If you do, **master** must be backed up more frequently.</span></span>  
  
-   <span data-ttu-id="3ef35-245">請勿將 **master** 資料庫的 TRUSTWORTHY 選項設為 ON。</span><span class="sxs-lookup"><span data-stu-id="3ef35-245">Do not set the TRUSTWORTHY option to ON for the **master** database.</span></span>  
  
## <a name="what-to-do-if-master-becomes-unusable"></a><span data-ttu-id="3ef35-246">如果 master 變得無法使用該怎麼辦</span><span class="sxs-lookup"><span data-stu-id="3ef35-246">What to Do If master Becomes Unusable</span></span>  
 <span data-ttu-id="3ef35-247">如果 **master** 資料庫變得無法使用，您可以使用下列任一方法將資料庫回復到可用狀態：</span><span class="sxs-lookup"><span data-stu-id="3ef35-247">If **master** becomes unusable, you can return the database to a usable state in either of the following ways:</span></span>  
  
-   <span data-ttu-id="3ef35-248">從現行資料庫備份來還原 **master** 。</span><span class="sxs-lookup"><span data-stu-id="3ef35-248">Restore **master** from a current database backup.</span></span>  
  
     <span data-ttu-id="3ef35-249">如果您可以啟動伺服器執行個體，應該就能夠從完整資料庫備份來還原 **master** 。</span><span class="sxs-lookup"><span data-stu-id="3ef35-249">If you can start the server instance, you should be able to restore **master** from a full database backup.</span></span> <span data-ttu-id="3ef35-250">如需詳細資訊，請參閱 [還原 master 資料庫 &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="3ef35-250">For more information, see [Restore the master Database &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="3ef35-251">完全重建 **master** 。</span><span class="sxs-lookup"><span data-stu-id="3ef35-251">Rebuild **master** completely.</span></span>  
  
     <span data-ttu-id="3ef35-252">如果 **master** 嚴重損壞，使您無法啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須重建 **master**。</span><span class="sxs-lookup"><span data-stu-id="3ef35-252">If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must rebuild **master**.</span></span> <span data-ttu-id="3ef35-253">如需詳細資訊，請參閱 [重建系統資料庫](rebuild-system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="3ef35-253">For more information, see [Rebuild System Databases](rebuild-system-databases.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3ef35-254">重建 **master** 將會重建所有的系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ef35-254">Rebuilding **master** rebuilds all of the system databases.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="3ef35-255">相關內容</span><span class="sxs-lookup"><span data-stu-id="3ef35-255">Related Content</span></span>  
 [<span data-ttu-id="3ef35-256">重建系統資料庫</span><span class="sxs-lookup"><span data-stu-id="3ef35-256">Rebuild System Databases</span></span>](rebuild-system-databases.md)  
  
 [<span data-ttu-id="3ef35-257">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="3ef35-257">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="3ef35-258">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ef35-258">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="3ef35-259">sys.master_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ef35-259">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [<span data-ttu-id="3ef35-260">移動資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="3ef35-260">Move Database Files</span></span>](move-database-files.md)  
  
  
