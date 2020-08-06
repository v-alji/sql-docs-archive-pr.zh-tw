---
title: MSSQLSERVER_1418 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1418 (Database Engine error)
ms.assetid: 6e9c7241-0201-44e0-9f8b-b3c4e293f0f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1fcac03f044aacce5e907824862eb589c97a07d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702945"
---
# <a name="mssqlserver_1418"></a><span data-ttu-id="9e758-102">MSSQLSERVER_1418</span><span class="sxs-lookup"><span data-stu-id="9e758-102">MSSQLSERVER_1418</span></span>
    
## <a name="details"></a><span data-ttu-id="9e758-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e758-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e758-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9e758-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="9e758-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9e758-105">Event ID</span></span>|<span data-ttu-id="9e758-106">1418</span><span class="sxs-lookup"><span data-stu-id="9e758-106">1418</span></span>|  
|<span data-ttu-id="9e758-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9e758-107">Event Source</span></span>|<span data-ttu-id="9e758-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9e758-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9e758-109">元件</span><span class="sxs-lookup"><span data-stu-id="9e758-109">Component</span></span>|<span data-ttu-id="9e758-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9e758-110">SQLEngine</span></span>|  
|<span data-ttu-id="9e758-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9e758-111">Symbolic Name</span></span>|<span data-ttu-id="9e758-112">DBM_PARTNERNOTFOUND</span><span class="sxs-lookup"><span data-stu-id="9e758-112">DBM_PARTNERNOTFOUND</span></span>|  
|<span data-ttu-id="9e758-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9e758-113">Message Text</span></span>|<span data-ttu-id="9e758-114">伺服器網路位址 "%.\*ls" 無法連上或不存在。</span><span class="sxs-lookup"><span data-stu-id="9e758-114">The server network address "%.\*ls" can not be reached or does not exist.</span></span> <span data-ttu-id="9e758-115">請檢查網路位址名稱，並檢查本機和遠端端點的連接埠是否可正常運作。</span><span class="sxs-lookup"><span data-stu-id="9e758-115">Check the network address name and that the ports for the local and remote endpoints are operational.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e758-116">說明</span><span class="sxs-lookup"><span data-stu-id="9e758-116">Explanation</span></span>  
 <span data-ttu-id="9e758-117">伺服器網路端點未回應，因為指定的伺服器網路位址無法連上或不存在。</span><span class="sxs-lookup"><span data-stu-id="9e758-117">The server network endpoint did not respond because the specified server network address cannot be reached or does not exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e758-118">根據預設，[!INCLUDE[msCoName](../../includes/msconame-md.md)] 作業系統會封鎖所有通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9e758-118">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] operating system blocks all ports.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e758-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9e758-119">User Action</span></span>  
 <span data-ttu-id="9e758-120">檢查網路位址名稱，然後重新發出命令。</span><span class="sxs-lookup"><span data-stu-id="9e758-120">Verify the network address name and reissue the command.</span></span>  
  
 <span data-ttu-id="9e758-121">您可能必須同時在兩個夥伴上執行更正動作。</span><span class="sxs-lookup"><span data-stu-id="9e758-121">Corrective action might be required on both partners.</span></span> <span data-ttu-id="9e758-122">例如，如果嘗試在主體伺服器執行個體上執行 SET PARTNER 時引發了這個訊息，訊息中可能暗示您只需要在鏡像伺服器執行個體上採取更正動作。</span><span class="sxs-lookup"><span data-stu-id="9e758-122">For example, if this message is raised when you are trying to run SET PARTNER on the principal server instance, the message might imply that you only have to take corrective action on the mirror server instance.</span></span> <span data-ttu-id="9e758-123">但是您可能必須同時在兩個夥伴上執行更正動作。</span><span class="sxs-lookup"><span data-stu-id="9e758-123">However, corrective actions might be required on both partners.</span></span>  
  
### <a name="additional-corrective-actions"></a><span data-ttu-id="9e758-124">其他更正動作</span><span class="sxs-lookup"><span data-stu-id="9e758-124">Additional Corrective Actions</span></span>  
  
-   <span data-ttu-id="9e758-125">確定鏡像資料庫是否已做好鏡像的準備。</span><span class="sxs-lookup"><span data-stu-id="9e758-125">Make sure that the mirror database is ready for mirroring.</span></span>  
  
-   <span data-ttu-id="9e758-126">確定鏡像伺服器執行個體的名稱和通訊埠是否正確。</span><span class="sxs-lookup"><span data-stu-id="9e758-126">Make sure that the name and port of the mirror server instance are correct.</span></span>  
  
-   <span data-ttu-id="9e758-127">確定目標鏡像伺服器執行個體不在防火牆後面。</span><span class="sxs-lookup"><span data-stu-id="9e758-127">Make sure that the destination mirror server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="9e758-128">確定主體伺服器執行個體不在防火牆後面。</span><span class="sxs-lookup"><span data-stu-id="9e758-128">Make sure that the principal server instance is not behind a firewall.</span></span>  
  
-   <span data-ttu-id="9e758-129">使用 **sys.database_mirroring_endpoints** 目錄檢視中的 **state** 或 **state_desc** 資料行來驗證夥伴上的端點是否已經啟動。</span><span class="sxs-lookup"><span data-stu-id="9e758-129">Verify that the endpoints are started on the partners by using the **state** or **state_desc** column the of the **sys.database_mirroring_endpoints** catalog view.</span></span> <span data-ttu-id="9e758-130">如果其中一個端點並未啟動，請執行 ALTER ENDPOINT 陳述式來啟動它。</span><span class="sxs-lookup"><span data-stu-id="9e758-130">If either endpoint is not started, execute an ALTER ENDPOINT statement to start it.</span></span>  
  
-   <span data-ttu-id="9e758-131">確定主體伺服器執行個體是否正在接聽指派給其資料庫鏡像端點的通訊埠，以及鏡像伺服器執行個體是否正在接聽其通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9e758-131">Make sure that the principal server instance is listening on the port assigned to its database mirroring endpoint and that and the mirror server instance is listening on its port.</span></span> <span data-ttu-id="9e758-132">如需詳細資訊，請參閱本主題稍後的「驗證通訊埠可用性」。</span><span class="sxs-lookup"><span data-stu-id="9e758-132">For more information, see "Verifying Port Availability," later in this topic.</span></span> <span data-ttu-id="9e758-133">如果夥伴並未接聽其指派的通訊埠，請將資料庫鏡像端點改為接聽不同的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9e758-133">If a partner is not listening on its assigned port, modify the database mirroring endpoint to listen on a different port.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9e758-134">安全性設定不正確可能會導致一般安裝錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9e758-134">Improperly configured security can cause a general setup error message.</span></span> <span data-ttu-id="9e758-135">伺服器執行個體通常會卸除不正確的連接要求，而不會回應。</span><span class="sxs-lookup"><span data-stu-id="9e758-135">Typically, the server instance drops the bad connection request without responding.</span></span> <span data-ttu-id="9e758-136">對於呼叫者，安全性組態錯誤可能由於其他各種原因所造成，例如鏡像資料庫狀態不正確或不存在、權限不正確等等。</span><span class="sxs-lookup"><span data-stu-id="9e758-136">To the caller, a security-configuration error could appear to have occurred for a variety of other reasons, such as the mirror database in a bad state or does not exist, incorrect permissions, and so on.</span></span>  
  
### <a name="using-the-error-log-file-for-diagnosis"></a><span data-ttu-id="9e758-137">使用錯誤記錄檔進行診斷</span><span class="sxs-lookup"><span data-stu-id="9e758-137">Using the Error Log File for Diagnosis</span></span>  
 <span data-ttu-id="9e758-138">在某些情況下，您只能使用錯誤記錄檔來進行調查。</span><span class="sxs-lookup"><span data-stu-id="9e758-138">In some cases, only error log files are available for investigation.</span></span> <span data-ttu-id="9e758-139">在這些情況下，請判斷錯誤記錄檔是否包含有關資料庫鏡像端點 TCP 通訊埠的錯誤訊息 26023。</span><span class="sxs-lookup"><span data-stu-id="9e758-139">In these cases, determine whether the error log contains error message 26023 for the TCP port of the database mirroring endpoint.</span></span> <span data-ttu-id="9e758-140">這是嚴重性 16 的錯誤，可能代表資料庫鏡像端點並未啟動。</span><span class="sxs-lookup"><span data-stu-id="9e758-140">This error, which is severity 16, might indicate that the database mirroring endpoint is not started.</span></span> <span data-ttu-id="9e758-141">即使 **sys.database_mirroring_endpoints** 顯示端點狀態已經啟動，還是有可能引發這個訊息。</span><span class="sxs-lookup"><span data-stu-id="9e758-141">This message can occur even if **sys.database_mirroring_endpoints** shows the endpoint state as started.</span></span>  
  
 <span data-ttu-id="9e758-142">解決您遇到的任何問題之後，請在主體伺服器上重新執行 ALTER DATABASE *database_name* SET PARTNER 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9e758-142">After resolving any issues that you encounter, rerun the ALTER DATABASE *database_name* SET PARTNER statement on the principal server.</span></span>  
  
### <a name="verifying-port-availability"></a><span data-ttu-id="9e758-143">驗證通訊埠可用性</span><span class="sxs-lookup"><span data-stu-id="9e758-143">Verifying Port Availability</span></span>  
 <span data-ttu-id="9e758-144">設定資料庫鏡像工作階段的網路時，請確定只有資料庫鏡像處理序會使用每個伺服器執行個體的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="9e758-144">When you are configuring the network for a database mirroring session, make sure the database mirroring endpoint of each server instance is used by only the database mirroring process.</span></span> <span data-ttu-id="9e758-145">如果有另一個處理序正在接聽指派給資料庫鏡像端點的通訊埠，其他伺服器執行個體的資料庫鏡像處理序便無法連接到該端點。</span><span class="sxs-lookup"><span data-stu-id="9e758-145">If another process is listening on the port assigned to a database mirroring endpoint, the database mirroring processes of the other server instances cannot connect to the endpoint.</span></span>  
  
 <span data-ttu-id="9e758-146">若要顯示 Windows 伺服器正在接聽的所有連接埠，請使用 **netstat** 命令提示字元公用程式。</span><span class="sxs-lookup"><span data-stu-id="9e758-146">To display all the ports on which a Windows-based server is listening, use the **netstat** command-prompt utility.</span></span> <span data-ttu-id="9e758-147">**netstat** 語法依 Windows 作業系統的版本而定。</span><span class="sxs-lookup"><span data-stu-id="9e758-147">The syntax for **netstat** depends on the version of the Windows operating system.</span></span> <span data-ttu-id="9e758-148">如需詳細資訊，請參閱作業系統文件集。</span><span class="sxs-lookup"><span data-stu-id="9e758-148">For more information, see the operating system documentation.</span></span>  
  
#### <a name="windows-server-2003-service-pack-1-sp1"></a><span data-ttu-id="9e758-149">Windows Server 2003 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="9e758-149">Windows Server 2003 Service Pack 1 (SP1)</span></span>  
 <span data-ttu-id="9e758-150">若要列出接聽通訊埠，以及已經開啟這些通訊埠的處理序，請在 Windows 命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="9e758-150">To list listening ports and the processes that have those ports opened, enter the following command at the Windows command prompt:</span></span>  
  
 <span data-ttu-id="9e758-151">**netstat -abn**</span><span class="sxs-lookup"><span data-stu-id="9e758-151">**netstat -abn**</span></span>  
  
#### <a name="windows-server-2003-pre-sp1"></a><span data-ttu-id="9e758-152">Windows Server 2003 (pre-SP1)</span><span class="sxs-lookup"><span data-stu-id="9e758-152">Windows Server 2003 (pre-SP1)</span></span>  
 <span data-ttu-id="9e758-153">若要識別接聽通訊埠，以及已經開啟這些通訊埠的處理序，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9e758-153">To identify the listening ports and the processes that have those ports opened, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9e758-154">取得處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e758-154">Obtain the process ID.</span></span>  
  
     <span data-ttu-id="9e758-155">若要取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的處理序識別碼，請連接到該執行個體並使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="9e758-155">To learn the process ID of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connect to that instance and use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT SERVERPROPERTY('ProcessID')   
    ```  
  
     <span data-ttu-id="9e758-156">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜SERVERPROPERTY (Transact-SQL)＞。</span><span class="sxs-lookup"><span data-stu-id="9e758-156">For more information, see "SERVERPROPERTY (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="9e758-157">比對處理序識別碼與下列 **netstat** 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="9e758-157">Match the process ID with the output of the following **netstat** command:</span></span>  
  
     <span data-ttu-id="9e758-158">**netstat -ano**</span><span class="sxs-lookup"><span data-stu-id="9e758-158">**netstat -ano**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e758-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e758-159">See Also</span></span>  
 <span data-ttu-id="9e758-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e758-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="9e758-161">[資料庫鏡像端點 &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9e758-161">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="9e758-162">[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9e758-162">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="9e758-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e758-163">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="9e758-164">[指定伺服器網路位址 &#40;資料庫鏡像&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="9e758-164">[Specify a Server Network Address &#40;Database Mirroring&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="9e758-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9e758-165">[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="9e758-166">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9e758-166">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
