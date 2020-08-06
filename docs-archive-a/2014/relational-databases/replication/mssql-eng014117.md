---
title: MSSQL_ENG014117 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014117 error
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4694aacc7d1f5ee31f4ff54d8cdd4256b48f713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584424"
---
# <a name="mssql_eng014117"></a><span data-ttu-id="71152-102">MSSQL_ENG014117</span><span class="sxs-lookup"><span data-stu-id="71152-102">MSSQL_ENG014117</span></span>
    
## <a name="message-details"></a><span data-ttu-id="71152-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="71152-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71152-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="71152-104">Product Name</span></span>|<span data-ttu-id="71152-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="71152-105">SQL Server</span></span>|  
|<span data-ttu-id="71152-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="71152-106">Event ID</span></span>|<span data-ttu-id="71152-107">14117</span><span class="sxs-lookup"><span data-stu-id="71152-107">14117</span></span>|  
|<span data-ttu-id="71152-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="71152-108">Event Source</span></span>|<span data-ttu-id="71152-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="71152-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="71152-110">元件</span><span class="sxs-lookup"><span data-stu-id="71152-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="71152-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="71152-111">Symbolic Name</span></span>||  
|<span data-ttu-id="71152-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="71152-112">Message Text</span></span>|<span data-ttu-id="71152-113">'%s' 並未設定為散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="71152-113">'%s' is not configured as a distribution database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="71152-114">說明</span><span class="sxs-lookup"><span data-stu-id="71152-114">Explanation</span></span>  
 <span data-ttu-id="71152-115">如果下列條件中的一或兩條成立，則會發生此錯誤：</span><span class="sxs-lookup"><span data-stu-id="71152-115">This error can occur if one or both of the following are true:</span></span>  
  
-   <span data-ttu-id="71152-116">**msdb..MSdistributiondbs**中遺失指定散發資料庫的項目。</span><span class="sxs-lookup"><span data-stu-id="71152-116">The entry for the specified distribution database is missing from **msdb..MSdistributiondbs**.</span></span>  
  
-   <span data-ttu-id="71152-117">**master** 資料庫中沒有本機伺服器的項目，或者該項目不正確。</span><span class="sxs-lookup"><span data-stu-id="71152-117">There is not an entry for the local server in the **master** database, or the entry that is there is incorrect.</span></span>  
  
     <span data-ttu-id="71152-118">針對拓撲中所有伺服器，複寫預計應使用電腦名稱與選擇性的執行個體名稱註冊 (叢集執行個體則為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虛擬伺服器名稱加上選擇性的執行個體名稱)。</span><span class="sxs-lookup"><span data-stu-id="71152-118">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="71152-119">要讓複寫正常運作， `SELECT @@SERVERNAME` 針對拓撲中每部伺服器傳回的值，都應該符合電腦名稱或虛擬伺服器名稱加上選擇性執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="71152-119">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
     <span data-ttu-id="71152-120">若您已透過 IP 位址或完整格式的網域名稱 (FQDN) 註冊任一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，就不支援複寫。</span><span class="sxs-lookup"><span data-stu-id="71152-120">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="71152-121">如果您設定複寫時，依 IP 位址或依 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 FQDN 註冊了任何 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行個體，就可能會引發這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="71152-121">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="71152-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="71152-122">User Action</span></span>  
 <span data-ttu-id="71152-123">請確認「散發者」執行個體註冊正確。</span><span class="sxs-lookup"><span data-stu-id="71152-123">Verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="71152-124">若電腦網路名稱和 SQL Server 執行個體名稱不符，則：</span><span class="sxs-lookup"><span data-stu-id="71152-124">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="71152-125">加入 SQL Server 執行個體名稱做為有效網路名稱。</span><span class="sxs-lookup"><span data-stu-id="71152-125">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="71152-126">設定另一可用網路名稱的方法之一，是將它加入本機主機檔案。</span><span class="sxs-lookup"><span data-stu-id="71152-126">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="71152-127">本機主機檔案預設位於 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc。如需進一步資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="71152-127">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="71152-128">例如，若電腦名稱為 comp1，電腦 IP 位址是 10.193.17.129，且執行個體名稱為 inst1/instname，請將下列項目加入主機檔案：</span><span class="sxs-lookup"><span data-stu-id="71152-128">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="71152-129">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="71152-129">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="71152-130">停用散發，註冊執行個體，然後重新建立散發。</span><span class="sxs-lookup"><span data-stu-id="71152-130">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="71152-131">如果 @@SERVERNAME 的值對非叢集執行個體並不正確，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="71152-131">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="71152-132">執行 [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 預存程序之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，@@SERVERNAME 的變更才能生效。</span><span class="sxs-lookup"><span data-stu-id="71152-132">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="71152-133">如果 @@SERVERNAME 的值不是正確的非叢集執行個體值，則必須使用叢集管理員變更名稱。</span><span class="sxs-lookup"><span data-stu-id="71152-133">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="71152-134">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="71152-134">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 <span data-ttu-id="71152-135">在確認「散發者」執行個體已正確註冊之後，請確認散發資料庫是否列在 **msdb..MSdistributiondbs**中。</span><span class="sxs-lookup"><span data-stu-id="71152-135">After verifying that the Distributor instance is registered properly, verify that the distribution database is listed in **msdb..MSdistributiondbs**.</span></span> <span data-ttu-id="71152-136">如果其沒有列在其中：</span><span class="sxs-lookup"><span data-stu-id="71152-136">If it is not listed:</span></span>  
  
1.  <span data-ttu-id="71152-137">為散發組態編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="71152-137">Script out the distribution configuration.</span></span> <span data-ttu-id="71152-138">如需詳細資訊，請參閱 [Scripting Replication](scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="71152-138">For more information, see [Scripting Replication](scripting-replication.md).</span></span>  
  
2.  <span data-ttu-id="71152-139">停用散發，然後再重新啟用它。</span><span class="sxs-lookup"><span data-stu-id="71152-139">Disable distribution and then re-enable it.</span></span> <span data-ttu-id="71152-140">如需詳細資訊，請參閱 [Configure Distribution](configure-distribution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="71152-140">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71152-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71152-141">See Also</span></span>  
 [<span data-ttu-id="71152-142">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="71152-142">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
