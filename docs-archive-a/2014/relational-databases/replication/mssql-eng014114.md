---
title: MSSQL_ENG014114 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014114 error
ms.assetid: f5f04590-e1c6-40d8-ab2b-98c791a0fc44
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba2a1fde59f55eecbfeeec46555567cde964f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584423"
---
# <a name="mssql_eng014114"></a><span data-ttu-id="831c7-102">MSSQL_ENG014114</span><span class="sxs-lookup"><span data-stu-id="831c7-102">MSSQL_ENG014114</span></span>
    
## <a name="message-details"></a><span data-ttu-id="831c7-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="831c7-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="831c7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="831c7-104">Product Name</span></span>|<span data-ttu-id="831c7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="831c7-105">SQL Server</span></span>|  
|<span data-ttu-id="831c7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="831c7-106">Event ID</span></span>|<span data-ttu-id="831c7-107">14114</span><span class="sxs-lookup"><span data-stu-id="831c7-107">14114</span></span>|  
|<span data-ttu-id="831c7-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="831c7-108">Event Source</span></span>|<span data-ttu-id="831c7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="831c7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="831c7-110">元件</span><span class="sxs-lookup"><span data-stu-id="831c7-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="831c7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="831c7-111">Symbolic Name</span></span>||  
|<span data-ttu-id="831c7-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="831c7-112">Message Text</span></span>|<span data-ttu-id="831c7-113">'%s' 並未設定為散發者。</span><span class="sxs-lookup"><span data-stu-id="831c7-113">'%s' is not configured as a Distributor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="831c7-114">說明</span><span class="sxs-lookup"><span data-stu-id="831c7-114">Explanation</span></span>  
 <span data-ttu-id="831c7-115">如果錯誤訊息指定了特定的執行個體而非 'null'，則指定的執行個體尚未正確設定，以識別為「散發者」。</span><span class="sxs-lookup"><span data-stu-id="831c7-115">If the error message specifies a particular instance, rather than 'null', the instance specified has not been properly configured to be recognized as a Distributor.</span></span>  
  
 <span data-ttu-id="831c7-116">如果訊息指定 'null' 為「散發者」，則 **master** 資料庫中沒有本機伺服器的項目，或者項目不正確 (可能因為電腦已重新命名)。</span><span class="sxs-lookup"><span data-stu-id="831c7-116">If the message specifies 'null' as a Distributor, there is no entry for the local server in **master** database, or the entry is incorrect (perhaps because the computer was renamed).</span></span> <span data-ttu-id="831c7-117">針對拓撲中所有伺服器，複寫預計應使用電腦名稱與選擇性的執行個體名稱註冊 (叢集執行個體則為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虛擬伺服器名稱加上選擇性的執行個體名稱)。</span><span class="sxs-lookup"><span data-stu-id="831c7-117">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="831c7-118">要讓複寫正常運作， `SELECT @@SERVERNAME` 針對拓撲中每部伺服器傳回的值，都應該符合電腦名稱或虛擬伺服器名稱加上選擇性執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="831c7-118">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="831c7-119">若您已透過 IP 位址或完整格式的網域名稱 (FQDN) 註冊任一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，就不支援複寫。</span><span class="sxs-lookup"><span data-stu-id="831c7-119">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="831c7-120">如果您設定複寫時，依 IP 位址或依 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 FQDN 註冊了任何 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行個體，就可能會引發這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="831c7-120">If you had any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="831c7-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="831c7-121">User Action</span></span>  
 <span data-ttu-id="831c7-122">如果錯誤訊息指定了特定的執行個體，請將伺服器設定為「散發者」。</span><span class="sxs-lookup"><span data-stu-id="831c7-122">If the error message specifies a particular instance, configure the server as a Distributor.</span></span> <span data-ttu-id="831c7-123">如需詳細資訊，請參閱 [Configure Distribution](configure-distribution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="831c7-123">For more information, see [Configure Distribution](configure-distribution.md).</span></span>  
  
 <span data-ttu-id="831c7-124">如果訊息未指定特定執行個體 ('null')，請確認「散發者」執行個體已正確註冊。</span><span class="sxs-lookup"><span data-stu-id="831c7-124">If the message does not specify a particular instance ('null'), verify that the Distributor instance is registered properly.</span></span> <span data-ttu-id="831c7-125">若電腦網路名稱和 SQL Server 執行個體名稱不符，則：</span><span class="sxs-lookup"><span data-stu-id="831c7-125">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="831c7-126">加入 SQL Server 執行個體名稱做為有效網路名稱。</span><span class="sxs-lookup"><span data-stu-id="831c7-126">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="831c7-127">設定另一可用網路名稱的方法之一，是將它加入本機主機檔案。</span><span class="sxs-lookup"><span data-stu-id="831c7-127">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="831c7-128">本機主機檔案預設位於 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc。如需進一步資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="831c7-128">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="831c7-129">例如，若電腦名稱為 comp1，電腦 IP 位址是 10.193.17.129，且執行個體名稱為 inst1/instname，請將下列項目加入主機檔案：</span><span class="sxs-lookup"><span data-stu-id="831c7-129">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="831c7-130">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="831c7-130">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="831c7-131">停用散發，註冊執行個體，然後重新建立散發。</span><span class="sxs-lookup"><span data-stu-id="831c7-131">Disable distribution, register the instance, and then reestablish distribution.</span></span> <span data-ttu-id="831c7-132">如果 @@SERVERNAME 的值對非叢集執行個體並不正確，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="831c7-132">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="831c7-133">執行 [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 預存程序之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，@@SERVERNAME 的變更才能生效。</span><span class="sxs-lookup"><span data-stu-id="831c7-133">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="831c7-134">如果 @@SERVERNAME 的值不是正確的非叢集執行個體值，則必須使用叢集管理員變更名稱。</span><span class="sxs-lookup"><span data-stu-id="831c7-134">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="831c7-135">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="831c7-135">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831c7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="831c7-136">See Also</span></span>  
 [<span data-ttu-id="831c7-137">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="831c7-137">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
