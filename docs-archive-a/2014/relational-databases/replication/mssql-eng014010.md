---
title: MSSQL_ENG014010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014010 error
ms.assetid: 6ea84f2f-e7a2-4028-9ea9-af0d2eba660e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c3d989eb7ae78562fb77d9896545539ba4ca3c7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585307"
---
# <a name="mssql_eng014010"></a><span data-ttu-id="4e098-102">MSSQL_ENG014010</span><span class="sxs-lookup"><span data-stu-id="4e098-102">MSSQL_ENG014010</span></span>
    
## <a name="message-details"></a><span data-ttu-id="4e098-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="4e098-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e098-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4e098-104">Product Name</span></span>|<span data-ttu-id="4e098-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4e098-105">SQL Server</span></span>|  
|<span data-ttu-id="4e098-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4e098-106">Event ID</span></span>|<span data-ttu-id="4e098-107">14010</span><span class="sxs-lookup"><span data-stu-id="4e098-107">14010</span></span>|  
|<span data-ttu-id="4e098-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="4e098-108">Event Source</span></span>|<span data-ttu-id="4e098-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4e098-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4e098-110">元件</span><span class="sxs-lookup"><span data-stu-id="4e098-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="4e098-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4e098-111">Symbolic Name</span></span>||  
|<span data-ttu-id="4e098-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4e098-112">Message Text</span></span>|<span data-ttu-id="4e098-113">伺服器 '%s' 並未定義為訂閱伺服器。</span><span class="sxs-lookup"><span data-stu-id="4e098-113">The server '%s' is not defined as a subscription server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4e098-114">說明</span><span class="sxs-lookup"><span data-stu-id="4e098-114">Explanation</span></span>  
 <span data-ttu-id="4e098-115">針對拓撲中所有伺服器，複寫預計應使用電腦名稱與選擇性的執行個體名稱註冊 (叢集執行個體則為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 虛擬伺服器名稱加上選擇性的執行個體名稱)。</span><span class="sxs-lookup"><span data-stu-id="4e098-115">Replication expects all servers in a topology to be registered using the computer name with an optional instance name (in the case of a clustered instance, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtual server name with the optional instance name).</span></span> <span data-ttu-id="4e098-116">要讓複寫正常運作， `SELECT @@SERVERNAME` 針對拓撲中每部伺服器傳回的值，都應該符合電腦名稱或虛擬伺服器名稱加上選擇性執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="4e098-116">For replication to function properly, the value returned by `SELECT @@SERVERNAME` for each server in the topology should match the computer name or virtual server name with the optional instance name.</span></span>  
  
 <span data-ttu-id="4e098-117">若您已透過 IP 位址或完整格式的網域名稱 (FQDN) 註冊任一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，就不支援複寫。</span><span class="sxs-lookup"><span data-stu-id="4e098-117">Replication is not supported if you have registered any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances by IP address or by Fully Qualified Domain Name (FQDN).</span></span> <span data-ttu-id="4e098-118">如果在您設定複寫時透過 IP 位址或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 FQDN 註冊了任意 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行個體，便會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e098-118">If you have any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances registered by IP address or by FQDN in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you configured replication, this error could be raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4e098-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4e098-119">User Action</span></span>  
 <span data-ttu-id="4e098-120">確認拓撲中的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體均已正確註冊。</span><span class="sxs-lookup"><span data-stu-id="4e098-120">Verify that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances in the topology are registered properly.</span></span> <span data-ttu-id="4e098-121">若電腦網路名稱和 SQL Server 執行個體名稱不符，則：</span><span class="sxs-lookup"><span data-stu-id="4e098-121">If the network name of the computer and the name of the SQL Server instance differ, either:</span></span>  
  
-   <span data-ttu-id="4e098-122">加入 SQL Server 執行個體名稱做為有效網路名稱。</span><span class="sxs-lookup"><span data-stu-id="4e098-122">Add the SQL Server instance name as a valid network name.</span></span> <span data-ttu-id="4e098-123">設定另一可用網路名稱的方法之一，是將它加入本機主機檔案。</span><span class="sxs-lookup"><span data-stu-id="4e098-123">One method to set an alternative network name is to add it to the local hosts file.</span></span> <span data-ttu-id="4e098-124">本機主機檔案預設位於 WINDOWS\system32\drivers\etc 或 WINNT\system32\drivers\etc。如需進一步資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="4e098-124">The local hosts file is located by default at WINDOWS\system32\drivers\etc or WINNT\system32\drivers\etc. For more information, see the Windows documentation.</span></span>  
  
     <span data-ttu-id="4e098-125">例如，若電腦名稱為 comp1，電腦 IP 位址是 10.193.17.129，且執行個體名稱為 inst1/instname，請將下列項目加入主機檔案：</span><span class="sxs-lookup"><span data-stu-id="4e098-125">For example, if the computer name is comp1 and the computer has an IP address of 10.193.17.129, and the instance name is inst1/instname, add the following entry to the hosts file:</span></span>  
  
     <span data-ttu-id="4e098-126">10.193.17.129 inst1</span><span class="sxs-lookup"><span data-stu-id="4e098-126">10.193.17.129 inst1</span></span>  
  
-   <span data-ttu-id="4e098-127">移除複寫，註冊每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，然後重新建立複寫。</span><span class="sxs-lookup"><span data-stu-id="4e098-127">Remove replication, register each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then reestablish replication.</span></span> <span data-ttu-id="4e098-128">如果 @@SERVERNAME 的值對非叢集執行個體並不正確，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="4e098-128">If the value of @@SERVERNAME is not correct for a nonclustered instance, follow these steps:</span></span>  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     <span data-ttu-id="4e098-129">執行 [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) 預存程序之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，@@SERVERNAME 的變更才能生效。</span><span class="sxs-lookup"><span data-stu-id="4e098-129">After you execute the [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql) stored procedure, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service for the change to @@SERVERNAME to take effect.</span></span>  
  
     <span data-ttu-id="4e098-130">如果 @@SERVERNAME 的值不是正確的非叢集執行個體值，則必須使用叢集管理員變更名稱。</span><span class="sxs-lookup"><span data-stu-id="4e098-130">If the value of @@SERVERNAME is not correct for a clustered instance, you must change the name using Cluster Administrator.</span></span> <span data-ttu-id="4e098-131">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4e098-131">For more information, see [AlwaysOn Failover Cluster Instances &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e098-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e098-132">See Also</span></span>  
 <span data-ttu-id="4e098-133">[@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e098-133">[@@SERVERNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/servername-transact-sql) </span></span>  
 [<span data-ttu-id="4e098-134">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="4e098-134">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
