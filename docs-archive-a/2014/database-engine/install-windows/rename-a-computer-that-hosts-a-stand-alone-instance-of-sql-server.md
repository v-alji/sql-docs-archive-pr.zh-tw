---
title: 重新命名管理 SQL Server 獨立執行個體的電腦 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- remote login errors [SQL Server]
- standalone computer names [SQL Server]
- names [SQL Server], standalone instances of SQL Server
- renaming standalone instances of SQL Server
- sysservers system table
- removing remote logins
- deleting remote logins
- dropping remote logins
ms.assetid: bbaf1445-b8a2-4ebf-babe-17d8cf20b037
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 079348921900a7cbf880027433280253df1a9e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707766"
---
# <a name="rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server"></a><span data-ttu-id="50d71-102">重新命名主控 SQL Server 獨立執行個體的電腦</span><span class="sxs-lookup"><span data-stu-id="50d71-102">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>
  <span data-ttu-id="50d71-103">當您變更了執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦名稱之後，便會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動期間辨識這個新名稱。</span><span class="sxs-lookup"><span data-stu-id="50d71-103">When you change the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the new name is recognized during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span> <span data-ttu-id="50d71-104">您不必重新執行安裝程式，即可重設電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="50d71-104">You do not have to run Setup again to reset the computer name.</span></span> <span data-ttu-id="50d71-105">請改用下列步驟來更新儲存在 sys.servers 中而且由系統函式 @@SERVERNAME 所報告的系統中繼資料。</span><span class="sxs-lookup"><span data-stu-id="50d71-105">Instead, use the following steps to update system metadata that is stored in sys.servers and reported by the system function @@SERVERNAME.</span></span> <span data-ttu-id="50d71-106">您可以更新系統中繼資料，以便反映使用 @@SERVERNAME 或從 sys.servers 中查詢伺服器名稱之遠端連接和應用程式的電腦名稱變更。</span><span class="sxs-lookup"><span data-stu-id="50d71-106">Update system metadata to reflect computer name changes for remote connections and applications that use @@SERVERNAME, or that query the server name from sys.servers.</span></span>  
  
 <span data-ttu-id="50d71-107">您不能使用下列步驟重新命名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="50d71-107">The following steps cannot be used to rename an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50d71-108">這些步驟只能用來重新命名執行個體名稱中與電腦名稱相對應的部分。</span><span class="sxs-lookup"><span data-stu-id="50d71-108">They can be used only to rename the part of the instance name that corresponds to the computer name.</span></span> <span data-ttu-id="50d71-109">例如，您可以將主控 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (名為 Instance1) 的電腦名稱 MB1 改成其他名稱，例如 MB2。</span><span class="sxs-lookup"><span data-stu-id="50d71-109">For example, you can change a computer named MB1 that hosts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named Instance1 to another name, such as MB2.</span></span> <span data-ttu-id="50d71-110">不過，該名稱中的執行個體部分 Instance1 將保持不變。</span><span class="sxs-lookup"><span data-stu-id="50d71-110">However, the instance part of the name, Instance1, will remain unchanged.</span></span> <span data-ttu-id="50d71-111">在這個範例中， \\\\*ComputerName*\\*InstanceName* 會從 \\\MB1\Instance1 變更為 \\\MB2\Instance1。</span><span class="sxs-lookup"><span data-stu-id="50d71-111">In this example, the \\\\*ComputerName*\\*InstanceName* would be changed from \\\MB1\Instance1 to \\\MB2\Instance1.</span></span>  
  
 <span data-ttu-id="50d71-112">**開始之前**</span><span class="sxs-lookup"><span data-stu-id="50d71-112">**Before you begin**</span></span>  
  
 <span data-ttu-id="50d71-113">在開始執行重新命名程序之前，請先檢閱下列資訊：</span><span class="sxs-lookup"><span data-stu-id="50d71-113">Before you begin the renaming process, review the following information:</span></span>  
  
-   <span data-ttu-id="50d71-114">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集的一部分時，此電腦的重新命名程序與主控獨立執行個體的電腦程序不同。</span><span class="sxs-lookup"><span data-stu-id="50d71-114">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the computer renaming process differs from a computer that hosts a stand-alone instance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="50d71-115">不支援在複寫時重新命名電腦，但在複寫時使用記錄傳送的情況例外。</span><span class="sxs-lookup"><span data-stu-id="50d71-115">does not support renaming computers that are involved in replication, except when you use log shipping with replication.</span></span> <span data-ttu-id="50d71-116">如果主要電腦已永久遺失，可以重新命名記錄傳送的次要電腦。</span><span class="sxs-lookup"><span data-stu-id="50d71-116">The secondary computer in log shipping can be renamed if the primary computer is permanently lost.</span></span> <span data-ttu-id="50d71-117">如需詳細資訊，請參閱[記錄傳送和複寫 &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="50d71-117">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="50d71-118">當您要重新命名設定為使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的電腦時，[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在電腦名稱變更之後可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="50d71-118">When you rename a computer that is configured to use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might not be available after the computer name change.</span></span> <span data-ttu-id="50d71-119">如需詳細資訊，請參閱 [重新命名報表伺服器電腦](../../reporting-services/report-server/rename-a-report-server-computer.md)。</span><span class="sxs-lookup"><span data-stu-id="50d71-119">For more information, see [Rename a Report Server Computer](../../reporting-services/report-server/rename-a-report-server-computer.md).</span></span>  
  
-   <span data-ttu-id="50d71-120">當您要重新命名已設定為使用資料庫鏡像的電腦時，您必須在重新命名作業之前關閉資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="50d71-120">When you rename a computer that is configured to use database mirroring, you must turn off database mirroring before the renaming operation.</span></span> <span data-ttu-id="50d71-121">然後使用新的電腦名稱，重新建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="50d71-121">Then, re-establish database mirroring with the new computer name.</span></span> <span data-ttu-id="50d71-122">資料庫鏡像的中繼資料並不會自動更新來反映新的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="50d71-122">Metadata for database mirroring will not be updated automatically to reflect the new computer name.</span></span> <span data-ttu-id="50d71-123">請使用下列步驟來更新系統中繼資料。</span><span class="sxs-lookup"><span data-stu-id="50d71-123">Use the following steps to update system metadata.</span></span>  
  
-   <span data-ttu-id="50d71-124">透過以硬式編碼方式參考電腦名稱的 Windows 群組來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的使用者，可能無法連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="50d71-124">Users who connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through a Windows group that uses a hard-coded reference to the computer name might not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50d71-125">如果 Windows 群組指定舊的電腦名稱，則重新命名之後可能會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="50d71-125">This can occur after the rename if the Windows group specifies the old computer name.</span></span> <span data-ttu-id="50d71-126">為了確保這種 Windows 群組在重新命名作業之後仍能連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請更新 Windows 群組，以指定新的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="50d71-126">To ensure that such Windows groups have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity following the renaming operation, update the Windows group to specify the new computer name.</span></span>  
  
 <span data-ttu-id="50d71-127">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後，您可以使用新的電腦名稱連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="50d71-127">You can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the new computer name after you have restarted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="50d71-128">為了確定 @@SERVERNAME 傳回已更新的本機伺服器執行個體名稱，您應該手動執行下列適用於您狀況的程序。</span><span class="sxs-lookup"><span data-stu-id="50d71-128">To ensure that @@SERVERNAME returns the updated name of the local server instance, you should manually run the following procedure that applies to your scenario.</span></span> <span data-ttu-id="50d71-129">您所使用的程序需視正在更新的電腦是主控 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預設執行個體還是具名執行個體而定。</span><span class="sxs-lookup"><span data-stu-id="50d71-129">The procedure you use depends on whether you are updating a computer that hosts a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-rename-a-computer-that-hosts-a-stand-alone-instance-of-ssnoversion"></a><span data-ttu-id="50d71-130">重新命名主控獨立執行個體的電腦 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50d71-130">To rename a computer that hosts a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="50d71-131">若為主控 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預設執行個體的重新命名電腦，請執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="50d71-131">For a renamed computer that hosts a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name>;  
    GO  
    sp_addserver <new_name>, local;  
    GO  
    ```  
  
     <span data-ttu-id="50d71-132">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="50d71-132">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="50d71-133">若為主控 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]具名執行個體的重新命名電腦，請執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="50d71-133">For a renamed computer that hosts a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name\instancename>;  
    GO  
    sp_addserver <new_name\instancename>, local;  
    GO  
    ```  
  
     <span data-ttu-id="50d71-134">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="50d71-134">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="after-the-renaming-operation"></a><span data-ttu-id="50d71-135">在重新命名作業之後</span><span class="sxs-lookup"><span data-stu-id="50d71-135">After the Renaming Operation</span></span>  
 <span data-ttu-id="50d71-136">在重新命名電腦之後，使用舊電腦名稱的任何連接都必須使用新名稱來連接。</span><span class="sxs-lookup"><span data-stu-id="50d71-136">After a computer has been renamed, any connections that used the old computer name must connect by using the new name.</span></span>  
  
#### <a name="to-verify-that-the-renaming-operation-has-completed-successfully"></a><span data-ttu-id="50d71-137">確認重新命名已成功地完成作業</span><span class="sxs-lookup"><span data-stu-id="50d71-137">To verify that the renaming operation has completed successfully</span></span>  
  
-   <span data-ttu-id="50d71-138">從 @@SERVERNAME 或 sys.servers 中選取資訊。</span><span class="sxs-lookup"><span data-stu-id="50d71-138">Select information from either @@SERVERNAME or sys.servers.</span></span> <span data-ttu-id="50d71-139">@@SERVERNAME 函式會傳回新名稱，而且 sys.servers 資料表會顯示新名稱。</span><span class="sxs-lookup"><span data-stu-id="50d71-139">The @@SERVERNAME function will return the new name, and the sys.servers table will show the new name.</span></span> <span data-ttu-id="50d71-140">下列範例示範如何使用 @@SERVERNAME。</span><span class="sxs-lookup"><span data-stu-id="50d71-140">The following example shows the use of @@SERVERNAME.</span></span>  
  
    ```  
    SELECT @@SERVERNAME AS 'Server Name';  
    ```  
  
## <a name="additional-considerations"></a><span data-ttu-id="50d71-141">其他考量</span><span class="sxs-lookup"><span data-stu-id="50d71-141">Additional Considerations</span></span>  
 <span data-ttu-id="50d71-142">**遠端登入** - 如果電腦上已有遠端登入，則執行 **sp_dropserver** 可能會產生類似下面的錯誤：</span><span class="sxs-lookup"><span data-stu-id="50d71-142">**Remote Logins** - If the computer has any remote logins, running **sp_dropserver** might generate an error similar to the following:</span></span>  
  
 `Server: Msg 15190, Level 16, State 1, Procedure sp_dropserver, Line 44 There are still remote logins for the server 'SERVER1'.`  
  
 <span data-ttu-id="50d71-143">若要解決錯誤，您必須卸除這部伺服器的遠端登入。</span><span class="sxs-lookup"><span data-stu-id="50d71-143">To resolve the error, you must drop remote logins for this server.</span></span>  
  
#### <a name="to-drop-remote-logins"></a><span data-ttu-id="50d71-144">卸除遠端登入</span><span class="sxs-lookup"><span data-stu-id="50d71-144">To drop remote logins</span></span>  
  
-   <span data-ttu-id="50d71-145">如果是預設執行個體，請執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="50d71-145">For a default instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name;  
    GO  
    ```  
  
-   <span data-ttu-id="50d71-146">如果是具名執行個體，請執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="50d71-146">For a named instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name\instancename;  
    GO  
    ```  
  
 <span data-ttu-id="50d71-147">**連結的伺服器組態** - 連結的伺服器組態將會受到電腦重新命名作業影響。</span><span class="sxs-lookup"><span data-stu-id="50d71-147">**Linked Server Configurations** - Linked server configurations will be affected by the computer renaming operation.</span></span> <span data-ttu-id="50d71-148">您可以使用 `sp_addlinkedserver` 或 `sp_setnetname` 更新電腦名稱參考。</span><span class="sxs-lookup"><span data-stu-id="50d71-148">Use `sp_addlinkedserver` or `sp_setnetname` to update computer name references.</span></span> <span data-ttu-id="50d71-149">如需詳細資訊，請參閱 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 或 [sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="50d71-149">For more information, see the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) or [sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql).</span></span>  
  
 <span data-ttu-id="50d71-150">**用戶端別名名稱** - 使用具名管道的用戶端別名將會受到電腦重新命名作業影響。</span><span class="sxs-lookup"><span data-stu-id="50d71-150">**Client Alias Names** - Client aliases that use named pipes will be affected by the computer renaming operation.</span></span> <span data-ttu-id="50d71-151">例如，如果您建立了指向 SRVR1 的別名 "PROD_SRVR" 並且使用具名管道通訊協定，此管道名稱將會類似這樣： `\\SRVR1\pipe\sql\query`。</span><span class="sxs-lookup"><span data-stu-id="50d71-151">For example, if an alias "PROD_SRVR" was created to point to SRVR1 and uses the named pipes protocol, the pipe name will look like `\\SRVR1\pipe\sql\query`.</span></span> <span data-ttu-id="50d71-152">重新命名電腦之後，具名管道的路徑將不再有效。</span><span class="sxs-lookup"><span data-stu-id="50d71-152">After the computer is renamed, the path of the named pipe will no longer be valid and.</span></span> <span data-ttu-id="50d71-153">如需具名管道的詳細資訊，請參閱 [使用具名管道建立有效的連接字串](https://go.microsoft.com/fwlink/?LinkId=111063)。</span><span class="sxs-lookup"><span data-stu-id="50d71-153">For more information about named pipes, see the [Creating a Valid Connection String Using Named Pipes](https://go.microsoft.com/fwlink/?LinkId=111063).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d71-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50d71-154">See Also</span></span>  
 [<span data-ttu-id="50d71-155">安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="50d71-155">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
