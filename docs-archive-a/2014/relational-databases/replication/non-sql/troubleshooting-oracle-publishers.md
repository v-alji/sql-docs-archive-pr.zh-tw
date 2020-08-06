---
title: 針對 Oracle 發行者進行疑難排解 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], troubleshooting
- troubleshooting [SQL Server replication], Oracle publishing
ms.assetid: be94f1c1-816b-4b1d-83f6-2fd6f5807ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4097b2c185b6dde307cd9b295d3b5b32f5797649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593927"
---
# <a name="troubleshooting-oracle-publishers"></a><span data-ttu-id="93528-102">Oracle 發行者疑難排解</span><span class="sxs-lookup"><span data-stu-id="93528-102">Troubleshooting Oracle Publishers</span></span>
  <span data-ttu-id="93528-103">本主題列出設定和使用「Oracle 發行者」時可能發生的一些問題。</span><span class="sxs-lookup"><span data-stu-id="93528-103">This topic lists a number of issues that might arise when configuring and using an Oracle Publisher.</span></span>  
  
## <a name="an-error-is-raised-regarding-oracle-client-and-networking-software"></a><span data-ttu-id="93528-104">發生有關 Oracle 用戶端與網路軟體的錯誤</span><span class="sxs-lookup"><span data-stu-id="93528-104">An Error Is Raised Regarding Oracle Client and Networking Software</span></span>  
 <span data-ttu-id="93528-105">在「散發者」執行 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帳戶，必須對 Oracle 用戶端網路軟體的安裝目錄 (以及所有子目錄) 具有讀取與執行權限。</span><span class="sxs-lookup"><span data-stu-id="93528-105">The account under which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] runs on the Distributor must be granted read and execute permissions for the directory (and all subdirectories) in which the Oracle client networking software is installed.</span></span> <span data-ttu-id="93528-106">如果沒有被授與權限或者 Oracle 用戶端元件沒有正確安裝，您將收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-106">If the permissions are not granted or the Oracle client components are not installed properly, you will receive the following error message:</span></span>  
  
 <span data-ttu-id="93528-107">「由於 [Microsoft OLE DB Provider for Oracle]，連接到伺服器失敗。</span><span class="sxs-lookup"><span data-stu-id="93528-107">"Connection to server failed with [Microsoft OLE DB Provider for Oracle].</span></span> <span data-ttu-id="93528-108">找不到 Oracle 用戶端和網路元件。</span><span class="sxs-lookup"><span data-stu-id="93528-108">Oracle client and networking components were not found.</span></span> <span data-ttu-id="93528-109">這些元件由 Oracle 公司提供，是 Oracle 7.3.3 或更新版本用戶端軟體安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="93528-109">These components are supplied by Oracle Corporation and are part of the Oracle Version 7.3.3 or later client software installation.</span></span> <span data-ttu-id="93528-110">在這些元件安裝前，Provider 無法運作」。</span><span class="sxs-lookup"><span data-stu-id="93528-110">Provider is unable to function until these components are installed."</span></span>  
  
 <span data-ttu-id="93528-111">如果在「散發者」端已安裝適當的 Oracle 用戶端，請確定在用戶端完成安裝後，停止並重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="93528-111">If an appropriate Oracle client has been installed at the Distributor, ensure that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] was stopped and then restarted after the client installation completed.</span></span> <span data-ttu-id="93528-112">為了讓 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 辨識用戶端元件，這是必要的動作。</span><span class="sxs-lookup"><span data-stu-id="93528-112">This is required in order for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to recognize the client components.</span></span>  
  
 <span data-ttu-id="93528-113">如果您確認已被授與權限並且元件已安裝正確，但仍產生此錯誤，請確認 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI 的登錄設定正確：</span><span class="sxs-lookup"><span data-stu-id="93528-113">If you have verified that permissions are granted and that components are installed correctly, but this error persists, verify that the registry settings at HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI are correct:</span></span>  
  
-   <span data-ttu-id="93528-114">對於 Oracle 10g，正確的設定為</span><span class="sxs-lookup"><span data-stu-id="93528-114">For Oracle 10g, the correct settings are</span></span>  
  
    -   <span data-ttu-id="93528-115">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="93528-115">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="93528-116">OracleSqlLib = orasql10.dll</span><span class="sxs-lookup"><span data-stu-id="93528-116">OracleSqlLib = orasql10.dll</span></span>  
  
    -   <span data-ttu-id="93528-117">OracleXaLib = oraclient10.dll</span><span class="sxs-lookup"><span data-stu-id="93528-117">OracleXaLib = oraclient10.dll</span></span>  
  
-   <span data-ttu-id="93528-118">對於 Oracle 9i，正確的設定為</span><span class="sxs-lookup"><span data-stu-id="93528-118">For Oracle 9i, the correct settings are</span></span>  
  
    -   <span data-ttu-id="93528-119">OracleOciLib = oci.dll</span><span class="sxs-lookup"><span data-stu-id="93528-119">OracleOciLib = oci.dll</span></span>  
  
    -   <span data-ttu-id="93528-120">OracleSqlLib = orasql9.dll</span><span class="sxs-lookup"><span data-stu-id="93528-120">OracleSqlLib = orasql9.dll</span></span>  
  
    -   <span data-ttu-id="93528-121">OracleXaLib = oraclient9.dll</span><span class="sxs-lookup"><span data-stu-id="93528-121">OracleXaLib = oraclient9.dll</span></span>  
  
## <a name="the-sql-server-distributor-cannot-connect-to-the-oracle-database-instance"></a><span data-ttu-id="93528-122">SQL Server 散發者無法連接到 Oracle 資料庫執行個體</span><span class="sxs-lookup"><span data-stu-id="93528-122">The SQL Server Distributor Cannot Connect to the Oracle Database Instance</span></span>  
 <span data-ttu-id="93528-123">如果「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」無法連接到「Oracle 發行者」，請確定：</span><span class="sxs-lookup"><span data-stu-id="93528-123">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, ensure that:</span></span>  
  
-   <span data-ttu-id="93528-124">「散發者」上安裝了必要的 Oracle 軟體。</span><span class="sxs-lookup"><span data-stu-id="93528-124">The necessary Oracle software is installed on the Distributor.</span></span>  
  
-   <span data-ttu-id="93528-125">Oracle 資料庫在線上，並且您可以使用 SQL\*Plus 之類的工具與其連接。</span><span class="sxs-lookup"><span data-stu-id="93528-125">The Oracle database is online and you can connect to it using a tool like SQL\*Plus.</span></span>  
  
-   <span data-ttu-id="93528-126">複寫用於連接到「Oracle 發行者」的登入擁有足夠權限。</span><span class="sxs-lookup"><span data-stu-id="93528-126">The login replication uses to connect to the Oracle Publisher has sufficient permissions.</span></span> <span data-ttu-id="93528-127">如需詳細資訊，請參閱[設定 Oracle 發行者](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="93528-127">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
-   <span data-ttu-id="93528-128">在「Oracle 發行者」設定期間定義的 TNS 名稱列在 tnsnames.ora 檔案中。</span><span class="sxs-lookup"><span data-stu-id="93528-128">The TNS names defined during configuration of the Oracle Publisher are listed in the tnsnames.ora file.</span></span>  
  
-   <span data-ttu-id="93528-129">使用正確的 Oracle 首頁和路徑。</span><span class="sxs-lookup"><span data-stu-id="93528-129">The correct Oracle Home and path are used.</span></span> <span data-ttu-id="93528-130">即使「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」上只安裝一組 Oracle 二進位編碼檔案，也請確定正確設定了與 Oracle 首頁相關的環境變數。</span><span class="sxs-lookup"><span data-stu-id="93528-130">Even if you have only one set of Oracle binaries installed on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, ensure that the environment variables related to the Oracle Home are set properly.</span></span> <span data-ttu-id="93528-131">如果變更環境變數值，必須停止並重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="93528-131">If you change environment variable values, you must stop and restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for the change to take effect.</span></span>  
  
 <span data-ttu-id="93528-132">如需設定和測試連接的詳細資訊，請參閱[設定 Oracle 發行者](configure-an-oracle-publisher.md)中的＜在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者上安裝與設定 Oracle 用戶端網路軟體＞。</span><span class="sxs-lookup"><span data-stu-id="93528-132">For more information about configuring and testing connectivity, see "Installing and Configuring Oracle Client Networking Software on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="the-oracle-publisher-is-associated-with-another-distributor"></a><span data-ttu-id="93528-133">Oracle 發行者與另一散發者產生關聯</span><span class="sxs-lookup"><span data-stu-id="93528-133">The Oracle Publisher Is Associated with Another Distributor</span></span>  
 <span data-ttu-id="93528-134">一個「Oracle 發行者」只能與一個「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」相關聯。</span><span class="sxs-lookup"><span data-stu-id="93528-134">An Oracle Publisher can only be associated with one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="93528-135">如果有另一個「散發者」與該「Oracle 發行者」相關聯，則必須在卸除它之後方可使用另一個「散發者」。</span><span class="sxs-lookup"><span data-stu-id="93528-135">If a different Distributor is associated with the Oracle Publisher, it must be dropped before another Distributor can be used.</span></span> <span data-ttu-id="93528-136">如果沒有先卸除該「散發者」，您將收到下列錯誤訊息之一：</span><span class="sxs-lookup"><span data-stu-id="93528-136">If the Distributor is not dropped first, you will receive one of the following error messages:</span></span>  
  
-   <span data-ttu-id="93528-137">「Oracle 伺服器執行個體 '\<*OraclePublisherName*>' 之前已經設定使用 '\<*SQLServerDistributorName*>' 做為其散發者。</span><span class="sxs-lookup"><span data-stu-id="93528-137">"Oracle server instance '\<*OraclePublisherName*>' has been previously configured to use '\<*SQLServerDistributorName*>' as its Distributor.</span></span> <span data-ttu-id="93528-138">若要開始使用 '\<*NewSQLServerDistributorName*>' 做為其散發者，您必須移除 Oracle 伺服器執行個體上目前的複寫組態，這會刪除該伺服器執行個體上的所有發行集」。</span><span class="sxs-lookup"><span data-stu-id="93528-138">To begin using '\<*NewSQLServerDistributorName*>' as its Distributor, you must remove the current replication configuration on the Oracle server instance, which will delete all publications on that server instance."</span></span>  
  
-   <span data-ttu-id="93528-139">「Oracle 伺服器 '\<*OracleServerName*>' 已經定義為散發者 '\<*SQLServerDistributorName*>. *\<DistributionDatabaseName>* ' 上的發行者 '\<*OraclePublisherName*>'。</span><span class="sxs-lookup"><span data-stu-id="93528-139">"Oracle server '\<*OracleServerName*>' is already defined as publisher '\<*OraclePublisherName*>' on distributor '\<*SQLServerDistributorName*>.*\<DistributionDatabaseName>*'.</span></span> <span data-ttu-id="93528-140">請卸除發行者或是卸除公用同義字 ' *\<SynonymName>* ' 來重新建立」。</span><span class="sxs-lookup"><span data-stu-id="93528-140">Drop the publisher or drop the public synonym '*\<SynonymName>*' to recreate."</span></span>  
  
 <span data-ttu-id="93528-141">在卸除某個「Oracle 散發者」時，Oracle 資料庫中的複寫物件也會自動清除。</span><span class="sxs-lookup"><span data-stu-id="93528-141">When an Oracle Publisher is dropped, the replication objects in the Oracle database are automatically cleaned up.</span></span> <span data-ttu-id="93528-142">但是在某些情況下必須手動清除 Oracle 複寫物件。</span><span class="sxs-lookup"><span data-stu-id="93528-142">However, manual cleanup of the Oracle replication objects is necessary in some cases.</span></span> <span data-ttu-id="93528-143">若要手動清除複寫建立的 Oracle 複寫物件：</span><span class="sxs-lookup"><span data-stu-id="93528-143">To manually clean up Oracle replication objects created by replication:</span></span>  
  
1.  <span data-ttu-id="93528-144">連接到具有 DBA 權限的 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="93528-144">Connect to the Oracle publisher with DBA permissions.</span></span>  
  
2.  <span data-ttu-id="93528-145">發出 SQL 命令 `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`。</span><span class="sxs-lookup"><span data-stu-id="93528-145">Issue the SQL command `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`.</span></span>  
  
3.  <span data-ttu-id="93528-146">發出 SQL 命令 `DROP USER <replication_administrative_user_schema>``CASCADE;`。</span><span class="sxs-lookup"><span data-stu-id="93528-146">Issue the SQL command `DROP USER <replication_administrative_user_schema>``CASCADE;`.</span></span>  
  
## <a name="sql-server-error-21663-is-raised-regarding-the-lack-of-a-primary-key"></a><span data-ttu-id="93528-147">發生有關缺少主索引鍵的 SQL Server 錯誤 21663</span><span class="sxs-lookup"><span data-stu-id="93528-147">SQL Server Error 21663 Is Raised Regarding the Lack of a Primary Key</span></span>  
 <span data-ttu-id="93528-148">交易式發行集中的發行項必須擁有有效的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93528-148">Articles in transactional publications must have a valid primary key.</span></span> <span data-ttu-id="93528-149">如果它們沒有有效的主索引鍵，您將在嘗試新增發行項時收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-149">If they do not have a valid primary key, you will receive the following error message when you attempt to add an article:</span></span>  
  
 <span data-ttu-id="93528-150">「找不到有效的來源資料表 [\<*TableOwner*>].[\<*TableName*>] 主索引鍵」</span><span class="sxs-lookup"><span data-stu-id="93528-150">"No valid primary key found for source table [\<*TableOwner*>].[\<*TableName*>]"</span></span>  
  
 <span data-ttu-id="93528-151">如需主索引鍵需求的詳細資訊，請參閱＜ [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md)＞主題中的＜唯一索引和條件約束＞一節。</span><span class="sxs-lookup"><span data-stu-id="93528-151">For information about requirements for primary keys, see the section "Unique Indexes and Constraints" in the topic [Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md).</span></span>  
  
## <a name="sql-server-error-21642-is-raised-regarding-a-duplicate-linked-server-login"></a><span data-ttu-id="93528-152">發生有關重複連結伺服器登入的 SQL Server 錯誤 21642</span><span class="sxs-lookup"><span data-stu-id="93528-152">SQL Server Error 21642 Is Raised Regarding a Duplicate Linked Server Login</span></span>  
 <span data-ttu-id="93528-153">在最初設定「Oracle 發行者」時，會為「發行者」與「散發者」之間的連接建立一個連結伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="93528-153">When an Oracle Publisher is initially configured, a linked server entry is created for the connection between the Publisher and the Distributor.</span></span> <span data-ttu-id="93528-154">連結伺服器的名稱與 Oracle TNS 服務名稱相同。</span><span class="sxs-lookup"><span data-stu-id="93528-154">The linked server has the same name as the Oracle TNS service name.</span></span> <span data-ttu-id="93528-155">如果您嘗試建立相同名稱的連結伺服器，將顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-155">If you attempt to create a linked server with the same name, the following error message is shown:</span></span>  
  
 <span data-ttu-id="93528-156">「異質性發行者需要已連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="93528-156">"Heterogeneous publishers require a linked server.</span></span> <span data-ttu-id="93528-157">已經存在名稱為 ' *\<LinkedServerName>* ' 的連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="93528-157">A linked server named '*\<LinkedServerName>*' already exists.</span></span> <span data-ttu-id="93528-158">請移除已連結伺服器或選擇不同的發行者名稱」。</span><span class="sxs-lookup"><span data-stu-id="93528-158">Please remove linked server or choose a different publisher name."</span></span>  
  
 <span data-ttu-id="93528-159">如果您嘗試直接建立連結伺服器，或者您之前已卸除「Oracle 發行者」與「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」之間的關聯性，現在又嘗試重新設定，便可能引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="93528-159">This error can occur if you attempt to create the linked server directly or if you have previously dropped the relationship between the Oracle Publisher and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor, and you are now attempting to reconfigure it.</span></span> <span data-ttu-id="93528-160">若在嘗試重新設定「發行者」時收到此錯誤，請使用 [sp_dropserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql) 卸除連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="93528-160">If you receive this error while attempting to reconfigure the Publisher, drop the linked server with [sp_dropserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql).</span></span>  
  
 <span data-ttu-id="93528-161">若您必須透過連結伺服器連線來連接到 Oracle 發行者，請建立另一個 TNS 服務名稱，然後在呼叫 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 時使用這個名稱。</span><span class="sxs-lookup"><span data-stu-id="93528-161">If you need to connect to the Oracle Publisher over a linked server connection, create another TNS service name, and then use this name when calling [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="93528-162">如需建立 TNS 服務名稱的詳細資訊，請參閱 Oracle 文件集。</span><span class="sxs-lookup"><span data-stu-id="93528-162">For information about creating TNS service names, see the Oracle documentation.</span></span>  
  
## <a name="sql-server-error-21617-is-raised"></a><span data-ttu-id="93528-163">發生 SQL Server 錯誤 21617</span><span class="sxs-lookup"><span data-stu-id="93528-163">SQL Server Error 21617 Is Raised</span></span>  
 <span data-ttu-id="93528-164">Oracle 發行使用 Oracle 應用程式 SQL\*PLUS 將「發行者」支援程式碼的封裝下載到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93528-164">Oracle publishing uses the Oracle application SQL\*PLUS to download the package of Publisher support code to the Oracle database.</span></span> <span data-ttu-id="93528-165">嘗試設定 Oracle 發行者之前，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會確認是否可透過散發者上的系統路徑存取 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="93528-165">Before attempting to configure the Oracle Publisher, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verifies that SQL\*PLUS is accessible through the system path on the Distributor.</span></span> <span data-ttu-id="93528-166">若無法載入 SQL\*PLUS，則會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-166">If SQL\*PLUS cannot be loaded, the following error message is shown:</span></span>  
  
 <span data-ttu-id="93528-167">「無法執行 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="93528-167">"Unable to run SQL\*PLUS.</span></span> <span data-ttu-id="93528-168">請確認散發者端已安裝目前版本的 Oracle 用戶端程式碼」。</span><span class="sxs-lookup"><span data-stu-id="93528-168">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="93528-169">嘗試在散發者上尋找 SQL\*PLUS。</span><span class="sxs-lookup"><span data-stu-id="93528-169">Try to locate SQL\*PLUS on the Distributor.</span></span> <span data-ttu-id="93528-170">對於 Oracle 10g 用戶端安裝，此可執行檔的名稱為 sqlplus.exe，</span><span class="sxs-lookup"><span data-stu-id="93528-170">For an Oracle 10g client install, the name of this executable is sqlplus.exe.</span></span> <span data-ttu-id="93528-171">通常安裝於 %ORACLE_HOME%/bin。</span><span class="sxs-lookup"><span data-stu-id="93528-171">It is typically installed in %ORACLE_HOME%/bin.</span></span> <span data-ttu-id="93528-172">若要確認 SQL\*PLUS 的路徑是否顯示在系統路徑中，請檢查系統變數 **Path** 的值：</span><span class="sxs-lookup"><span data-stu-id="93528-172">To verify that the path of SQL\*PLUS appears in the system path, examine the value of the system variable **Path**:</span></span>  
  
1.  <span data-ttu-id="93528-173">以滑鼠右鍵按一下 **[我的電腦]** ，然後再按 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-173">Right-click **My Computer**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="93528-174">按一下 **[進階]** 索引標籤，然後再按 **[環境變數]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-174">Click the **Advanced** tab, and then click **Environment variables**.</span></span>  
  
3.  <span data-ttu-id="93528-175">在 **[環境變數]** 對話方塊的 **[系統變數]** 清單中，選取 **[Path]** 變數，然後按一下 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-175">In the **Environment Variables** dialog box, in the **System variables** list, select the **Path** variable, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="93528-176">在 **[編輯系統變數]** 對話方塊中：如果 **[變數值]** 文字方塊中不存在包含 sqlplus.exe 的資料夾路徑，則編輯字串以包含它。</span><span class="sxs-lookup"><span data-stu-id="93528-176">In the **Edit System Variable** dialog box: if the path to the folder that contains sqlplus.exe is not present in the **Variable value** text box, edit the string to include it.</span></span>  
  
5.  <span data-ttu-id="93528-177">按一下每個開啟對話方塊上的 **[確定]** ，以結束並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="93528-177">Click **OK** on each open dialog box to exit and save changes.</span></span>  
  
 <span data-ttu-id="93528-178">如果您在「散發者」上找不到 sqlplus.exe，請於「散發者」端安裝目前版本的 Oracle 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="93528-178">If you cannot locate sqlplus.exe on the Distributor, install a current version of the Oracle client software at the Distributor.</span></span> <span data-ttu-id="93528-179">如需詳細資訊，請參閱[設定 Oracle 發行者](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="93528-179">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="sql-server-error-21620-is-raised"></a><span data-ttu-id="93528-180">發生 SQL Server 錯誤 21620</span><span class="sxs-lookup"><span data-stu-id="93528-180">SQL Server Error 21620 Is Raised</span></span>  
 <span data-ttu-id="93528-181">如果連接到 8.1 版之前的 Oracle 資料庫，Oracle 發行需要在散發者上安裝 9 版以上的 Oracle 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="93528-181">If you are connecting to an Oracle database earlier than version 8.1, Oracle publishing requires that the Oracle client software installed on the Distributor be from version 9.</span></span> <span data-ttu-id="93528-182">如果連接到 8.1 版或更新版本的 Oracle 資料庫，則建議採用 10 版或更新版本的 Oracle 用戶端軟體。</span><span class="sxs-lookup"><span data-stu-id="93528-182">If you are connecting to an Oracle database that is version 8.1 or later, we recommend that the Oracle client software be version 10 or later.</span></span>  
  
 <span data-ttu-id="93528-183">嘗試設定「Oracle 發行者」之前，Oracle 發行會確認可透過「散發者」上系統路徑存取的 SQL\*PLUS 版本是不是 9 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="93528-183">Before attempting to configure the Oracle Publisher, Oracle publishing verifies that the version of SQL\*PLUS accessible through the system path on the Distributor is version 9 or later.</span></span> <span data-ttu-id="93528-184">如果不是，會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-184">If it is not, the following error message is shown:</span></span>  
  
 <span data-ttu-id="93528-185">「可透過系統 Path 變數存取的 SQL\*PLUS 版本，目前不足以支援 Oracle 發行。</span><span class="sxs-lookup"><span data-stu-id="93528-185">"The version of SQL\*PLUS that is accessible through the system Path variable is not current enough to support Oracle publishing.</span></span> <span data-ttu-id="93528-186">請確認散發者端已安裝目前版本的 Oracle 用戶端程式碼」。</span><span class="sxs-lookup"><span data-stu-id="93528-186">Make certain that a current version of the Oracle client code is installed at the distributor."</span></span>  
  
 <span data-ttu-id="93528-187">如果在「散發者」上安裝了多個版本的 Oracle 用戶端軟體，請確定最新版本至少是 9 版，並且系統 path 變數會首先參考此版本 (只要最新的版本最先出現，就會發生對其他版本的參考)。</span><span class="sxs-lookup"><span data-stu-id="93528-187">If you have multiple versions of the Oracle client software installed on the Distributor, make sure that the most current version is at least version 9 and that the system path variable refers first to this version (references to other versions can appear as long as the most recent appears first).</span></span> <span data-ttu-id="93528-188">如需有關編輯系統 path 變數的詳細資訊，請參閱本主題前面的＜發生 SQL Server 錯誤 21617＞一節。</span><span class="sxs-lookup"><span data-stu-id="93528-188">For more information about editing the system path variable, see the section "SQL Server Error 21617 is Raised" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21624-or-error-21629-is-raised"></a><span data-ttu-id="93528-189">發生 SQL Server 錯誤 21624 或錯誤 21629</span><span class="sxs-lookup"><span data-stu-id="93528-189">SQL Server Error 21624 or Error 21629 Is Raised</span></span>  
 <span data-ttu-id="93528-190">對於 64 位元的「散發者」，Oracle 發行會使用 Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="93528-190">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> <span data-ttu-id="93528-191">請確定已安裝 Oracle OLEDB 提供者，並在「散發者」上註冊。</span><span class="sxs-lookup"><span data-stu-id="93528-191">Make sure that the Oracle OLEDB provider is installed and registered on the Distributor.</span></span> <span data-ttu-id="93528-192">如果未安裝和註冊提供者，便會顯示以下一或兩則錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-192">If the provider is not installed and registered, one or both of the following error messages is shown:</span></span>  
  
-   <span data-ttu-id="93528-193">在散發者 '%s' 端找不到已註冊的 Oracle OLEDB 提供者 (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="93528-193">"Unable to locate the registered Oracle OLEDB provider, OraOLEDB.Oracle, at distributor '%s'.</span></span> <span data-ttu-id="93528-194">請確認已安裝目前版本的 Oracle OLEDB 提供者，並在散發者端註冊」。</span><span class="sxs-lookup"><span data-stu-id="93528-194">Make certain that a current version of the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
-   <span data-ttu-id="93528-195">「CLSID 登錄機碼指出散發者端沒有已經註冊的 Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="93528-195">"The CLSID registry key indicating that the Oracle OLEDB Provider for Oracle, OraOLEDB.Oracle, has been registered is not present at the distributor.</span></span> <span data-ttu-id="93528-196">請確認已安裝 Oracle OLEDB 提供者，並在散發者端註冊」。</span><span class="sxs-lookup"><span data-stu-id="93528-196">Make certain that the Oracle OLEDB provider is installed and registered at the distributor."</span></span>  
  
 <span data-ttu-id="93528-197">如果使用的是 10g 版的 Oracle 用戶端軟體，提供者為 OraOLEDB10.dll；如果是 9i 版，則提供者為 OraOLEDB.dll。</span><span class="sxs-lookup"><span data-stu-id="93528-197">If you are using Oracle client software version 10g, the provider is OraOLEDB10.dll; for version 9i, it is OraOLEDB.dll.</span></span> <span data-ttu-id="93528-198">提供者安裝於 %ORACLE_HOME%\BIN (例如，C:\oracle\product\10.1.0\Client_1\bin)。</span><span class="sxs-lookup"><span data-stu-id="93528-198">The provider is installed in %ORACLE_HOME%\BIN (for example, C:\oracle\product\10.1.0\Client_1\bin).</span></span> <span data-ttu-id="93528-199">如果判斷出「散發者」端未安裝 Oracle OLEDB 提供者，請從 Oracle 提供的 Oracle 用戶端軟體安裝光碟片安裝它。</span><span class="sxs-lookup"><span data-stu-id="93528-199">If you determine that the Oracle OLEDB provider is not installed on the Distributor, install it from the Oracle client software install disc provided by Oracle.</span></span> <span data-ttu-id="93528-200">如需詳細資訊，請參閱[設定 Oracle 發行者](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="93528-200">For more information, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="93528-201">如果安裝了 Oracle OLEDB 提供者，請確定其已註冊。</span><span class="sxs-lookup"><span data-stu-id="93528-201">If the Oracle OLEDB provider is installed, make sure that it is registered.</span></span> <span data-ttu-id="93528-202">若要註冊提供者 DLL，請從安裝 DLL 的目錄執行下列命令，然後停止 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，然後重新啟動它。</span><span class="sxs-lookup"><span data-stu-id="93528-202">To register the provider DLL, execute the following command from the directory in which the DLL is installed, and then stop and restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="93528-203">`regsvr32 OraOLEDB10.dll` 或 `regsvr32 OraOLEDB.dll`。</span><span class="sxs-lookup"><span data-stu-id="93528-203">`regsvr32 OraOLEDB10.dll` or `regsvr32 OraOLEDB.dll`.</span></span>  
  
## <a name="sql-server-error-21626-or-error-21627-is-raised"></a><span data-ttu-id="93528-204">發生 SQL Server 錯誤 21626 或錯誤 21627</span><span class="sxs-lookup"><span data-stu-id="93528-204">SQL Server Error 21626 or Error 21627 Is Raised</span></span>  
 <span data-ttu-id="93528-205">為了確認 Oracle 發行環境是否設定正確， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會嘗試使用您在設定期間指定的登入認證連接「Oracle 發行者」。</span><span class="sxs-lookup"><span data-stu-id="93528-205">To verify that the Oracle publishing environment is configured properly, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tries to connect to the Oracle Publisher with the login credentials you specified during configuration.</span></span> <span data-ttu-id="93528-206">如果「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」無法連接到「Oracle 發行者」，會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-206">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor cannot connect to the Oracle Publisher, the following error message is shown:</span></span>  
  
-   <span data-ttu-id="93528-207">「無法使用 Oracle OLEDB 提供者 (OraOLEDB.Oracle) 連接到 Oracle 資料庫伺服器 '%s'。」</span><span class="sxs-lookup"><span data-stu-id="93528-207">"Unable to connect to Oracle database server '%s' using the Oracle OLEDB provider OraOLEDB.Oracle."</span></span>  
  
 <span data-ttu-id="93528-208">如果顯示此錯誤訊息，請透過使用「Oracle 發行者」設定期間指定的登入和密碼直接執行 SQL\*PLUS，確認與 Oracle 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="93528-208">If this error message is shown, verify connectivity to the Oracle database by running SQL\*PLUS directly using the same login and password specified during configuration of the Oracle Publisher.</span></span> <span data-ttu-id="93528-209">如需詳細資訊，請參閱本主題稍早的「SQL Server 散發者無法連接到 Oracle 資料庫執行個體」一節。</span><span class="sxs-lookup"><span data-stu-id="93528-209">For more information, see the section "The SQL Server Distributor Cannot Connect to the Oracle Database Instance" earlier in this topic.</span></span>  
  
## <a name="sql-server-error-21628-is-raised"></a><span data-ttu-id="93528-210">發生 SQL Server 錯誤 21628</span><span class="sxs-lookup"><span data-stu-id="93528-210">SQL Server Error 21628 Is Raised</span></span>  
 <span data-ttu-id="93528-211">對於 64 位元的「散發者」，Oracle 發行會使用 Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="93528-211">For 64-bit Distributors, Oracle publishing uses the Oracle OLEDB Provider for Oracle (OraOLEDB.Oracle).</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="93528-212">會建立登錄項目，以允許使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]在處理序中執行 Oracle 提供者。</span><span class="sxs-lookup"><span data-stu-id="93528-212">creates a registry entry to allow the Oracle provider to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93528-213">如果讀取或寫入此登錄項目時發生問題，則會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-213">If there is a problem reading or writing this registry entry, the following error message is shown:</span></span>  
  
 <span data-ttu-id="93528-214">「無法更新散發者 '%s' 的登錄，以允許使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]在處理序中執行 Oracle OLEDB 提供者 (OraOLEDB.Oracle)。</span><span class="sxs-lookup"><span data-stu-id="93528-214">"Unable to update the registry of distributor '%s' to allow Oracle OLEDB provider OraOLEDB.Oracle to run in process with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93528-215">請確認目前的登入已獲得授權，可修改 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 擁有的登錄機碼」。</span><span class="sxs-lookup"><span data-stu-id="93528-215">Make certain that current login is authorized to modify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] owned registry keys."</span></span>  
  
 <span data-ttu-id="93528-216">Oracle 發行需要存在登錄項目，且對於 64 位元「散發者」該登錄項目應設定為 **1** 。</span><span class="sxs-lookup"><span data-stu-id="93528-216">Oracle publishing requires the registry entry to exist and to be set to **1** for 64 bit Distributors.</span></span> <span data-ttu-id="93528-217">如果該項目不存在， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="93528-217">If the entry does not exist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will attempt to create it.</span></span> <span data-ttu-id="93528-218">如果該項目存在，但設定為 **0**，則設定不會變更；「Oracle 發行者」的設定將失敗。</span><span class="sxs-lookup"><span data-stu-id="93528-218">If the entry exists, but is set to **0**, the setting will not be changed; the configuration of the Oracle Publisher will fail.</span></span>  
  
 <span data-ttu-id="93528-219">若要檢視和修改登錄設定：</span><span class="sxs-lookup"><span data-stu-id="93528-219">To view and modify the registry setting:</span></span>  
  
1.  <span data-ttu-id="93528-220">按一下 **[開始]** ，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-220">Click **Start**, and then click **Run**.</span></span>  
  
2.  <span data-ttu-id="93528-221">在 **[執行]** 對話方塊中，輸入 **regedit**，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-221">In the **Run** dialog box, type **regedit**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="93528-222">瀏覽至 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\ *\<InstanceName>* \Providers。</span><span class="sxs-lookup"><span data-stu-id="93528-222">Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\*\<InstanceName>* \Providers.</span></span>  
  
     <span data-ttu-id="93528-223">[Providers] 下應包含一個名為 OraOLEDB.Oracle 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="93528-223">Included under Providers should be a folder named OraOLEDB.Oracle.</span></span> <span data-ttu-id="93528-224">在此資料夾中應是 DWORD 值名稱 **AllowInProcess**，其值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="93528-224">Within this folder should be the DWORD value name **AllowInProcess**, with a value of **1**.</span></span>  
  
4.  <span data-ttu-id="93528-225">如果判斷出 **AllowInProcess** 設定為 **0**，請將登錄項目更新為 **1**：</span><span class="sxs-lookup"><span data-stu-id="93528-225">If you determine that **AllowInProcess** is set to **0**, update the registry entry to **1**:</span></span>  
  
    1.  <span data-ttu-id="93528-226">以滑鼠右鍵按一下項目，然後再按 **[修改]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-226">Right-click the entry, and then click **Modify**.</span></span>  
  
    2.  <span data-ttu-id="93528-227">在 **[編輯字串]** 對話方塊的 **[值資料]** 欄位中輸入 **[1]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-227">In the **Edit String** dialog box, type **1** in the **Value data** field.</span></span>  
  
## <a name="sql-server-error-21684-is-raised"></a><span data-ttu-id="93528-228">發生 SQL Server 錯誤 21684</span><span class="sxs-lookup"><span data-stu-id="93528-228">SQL Server Error 21684 Is Raised</span></span>  
 <span data-ttu-id="93528-229">如果管理的使用者帳戶沒有足夠權限，就會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93528-229">If the administrative user account does not have sufficient privileges, the following error message is shown:</span></span>  
  
 <span data-ttu-id="93528-230">「與 Oracle 發行者 '%s' 管理者登入相關聯的權限不足。」</span><span class="sxs-lookup"><span data-stu-id="93528-230">"The permissions associated with the administrator login for Oracle publisher '%s' are not sufficient."</span></span>  
  
 <span data-ttu-id="93528-231">若要確認已授與使用者的權限，請執行下列查詢： `SELECT * from session_privs`。</span><span class="sxs-lookup"><span data-stu-id="93528-231">To verify the permissions granted to the user, execute the following query: `SELECT * from session_privs`.</span></span> <span data-ttu-id="93528-232">輸出應如下所示：</span><span class="sxs-lookup"><span data-stu-id="93528-232">The output should be similar to the following:</span></span>  
  
 `PRIVILEGE`  
  
 `------------------`  
  
 `CREATE SESSION`  
  
 `CREATE TABLE`  
  
 `CREATE PUBLIC SYNONYM`  
  
 `DROP PUBLIC SYNONYM`  
  
 `CREATE VIEW`  
  
 `CREATE SEQUENCE`  
  
 `CREATE PROCEDURE`  
  
 `CREATE TRIGGER`  
  
## <a name="you-encounter-permissions-issues-for-the-replication-user-schema"></a><span data-ttu-id="93528-233">遇到複寫使用者結構描述的權限問題</span><span class="sxs-lookup"><span data-stu-id="93528-233">You Encounter Permissions Issues for the Replication User Schema</span></span>  
 <span data-ttu-id="93528-234">複寫使用者結構描述必須擁有[設定 Oracle 發行者](configure-an-oracle-publisher.md)的＜手動建立使用者結構描述＞中所述的權限。</span><span class="sxs-lookup"><span data-stu-id="93528-234">The replication user schema must have the permissions described in "Creating the User Schema Manually" in [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
## <a name="oracle-error-ora-01000"></a><span data-ttu-id="93528-235">Oracle 錯誤 ORA-01000</span><span class="sxs-lookup"><span data-stu-id="93528-235">Oracle Error ORA-01000</span></span>  
 <span data-ttu-id="93528-236">將發行項新增至發行集的過程中，複寫使用「Oracle 發行者」的資料指標。</span><span class="sxs-lookup"><span data-stu-id="93528-236">Replication uses cursors on the Oracle Publisher during the process of adding articles to a publication.</span></span> <span data-ttu-id="93528-237">在此處理過程中，可能會超過「發行者」上可用資料指標的最大數目。</span><span class="sxs-lookup"><span data-stu-id="93528-237">It is possible to exceed the maximum number of cursors available on the Publisher during this process.</span></span> <span data-ttu-id="93528-238">如果發生此種情形，則會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="93528-238">If this occurs, the following error is raised:</span></span>  
  
 <span data-ttu-id="93528-239">「ORA-01000：超出開啟之資料指標的最大數目」</span><span class="sxs-lookup"><span data-stu-id="93528-239">"ORA-01000: maximum open cursors exceeded"</span></span>  
  
 <span data-ttu-id="93528-240">為避免此問題，請確定 Oracle 資料庫中的 **max_open_cursors** 設定已設成足夠大 (至少 1000)。</span><span class="sxs-lookup"><span data-stu-id="93528-240">To avoid this problem, ensure that the **max_open_cursors** setting in the Oracle databases is set to a sufficiently high number (at least 1000).</span></span> <span data-ttu-id="93528-241">如需此設定的詳細資訊，請參閱 Oracle 文件集。</span><span class="sxs-lookup"><span data-stu-id="93528-241">For more information about this setting, see the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-01555"></a><span data-ttu-id="93528-242">Oracle 錯誤 ORA-01555</span><span class="sxs-lookup"><span data-stu-id="93528-242">Oracle Error ORA-01555</span></span>  
 <span data-ttu-id="93528-243">下列 Oracle 資料庫錯誤與快照式複寫無關；而與 Oracle 如何建構資料的讀取一致檢視相關：</span><span class="sxs-lookup"><span data-stu-id="93528-243">The following Oracle database error is not related to snapshot replication; it is related to how Oracle constructs read-consistent views of data:</span></span>  
  
 <span data-ttu-id="93528-244">「ORA-01555:快照集太舊」</span><span class="sxs-lookup"><span data-stu-id="93528-244">"ORA-01555: Snapshot too old"</span></span>  
  
 <span data-ttu-id="93528-245">Oracle 會在發出 SQL 陳述式時，使用稱為回復區段的物件建構資料的讀取一致檢視。</span><span class="sxs-lookup"><span data-stu-id="93528-245">Using objects known as rollback segments, Oracle constructs read-consistent views of data as of the point in time a SQL statement is issued.</span></span> <span data-ttu-id="93528-246">在回復資訊為其他並行的階段作業所覆寫時，可能會發生「快照集太舊」錯誤。</span><span class="sxs-lookup"><span data-stu-id="93528-246">A "snapshot too old" error might occur when rollback information is overwritten by other concurrent sessions.</span></span> <span data-ttu-id="93528-247">對於 Oracle 9i 之前的版本，建議使用以下方法來減少此錯誤的發生頻率：增加回復區段的大小和 (或) 數目，並將大型交易指派到特定的回復區段。</span><span class="sxs-lookup"><span data-stu-id="93528-247">Prior to Oracle 9i, the recommended method of reducing the frequency of this error was to increase the size and/or number of rollback segments, and to assign large transactions to a specific rollback segment.</span></span>  
  
 <span data-ttu-id="93528-248">在 Oracle 9i 中，Oracle 提出了 UNDO 資料表空間概念來取代回復區段。</span><span class="sxs-lookup"><span data-stu-id="93528-248">In Oracle 9i, Oracle introduced the UNDO tablespace concept, which replaces the rollback segment.</span></span> <span data-ttu-id="93528-249">為防止在 Oracle 9i 中發生「快照集太舊」錯誤，建議您：</span><span class="sxs-lookup"><span data-stu-id="93528-249">To prevent the "snapshot too old" error in Oracle 9i, it is recommended that you:</span></span>  
  
-   <span data-ttu-id="93528-250">建立一個包含適當可用空間量的 UNDO 資料表空間。</span><span class="sxs-lookup"><span data-stu-id="93528-250">Create an UNDO tablespace with an appropriate amount of free space.</span></span>  
  
-   <span data-ttu-id="93528-251">在資料表空間上設定保留保證 (Oracle 10G 和更高版本)。</span><span class="sxs-lookup"><span data-stu-id="93528-251">Set the retention guarantee on the tablespace (Oracle 10G and greater).</span></span>  
  
-   <span data-ttu-id="93528-252">設定 Oracle 初始化參數 UNDO_MANAGEMENT 與 UNDO_RETENTION。</span><span class="sxs-lookup"><span data-stu-id="93528-252">Configure the Oracle initialization parameters UNDO_MANAGEMENT and UNDO_RETENTION.</span></span>  
  
 <span data-ttu-id="93528-253">如需避免「快照集太舊」錯誤的詳細資料，請參閱 Oracle 文件集。</span><span class="sxs-lookup"><span data-stu-id="93528-253">For further details about avoiding the "snapshot too old" error, consult the Oracle documentation.</span></span>  
  
## <a name="oracle-error-ora-22285"></a><span data-ttu-id="93528-254">Oracle 錯誤 ORA-22285</span><span class="sxs-lookup"><span data-stu-id="93528-254">Oracle Error ORA-22285</span></span>  
 <span data-ttu-id="93528-255">如果資料表包括 BFILE 資料行，則該資料行的資料儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="93528-255">If a table includes a BFILE column, the data for the column is stored in the file system.</span></span> <span data-ttu-id="93528-256">複寫管理使用者帳戶必須被授與目錄存取權限。在該目錄中，資料使用下列語法儲存：</span><span class="sxs-lookup"><span data-stu-id="93528-256">The replication administrative user account must be granted access to the directory in which the data is stored using the following syntax:</span></span>  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 <span data-ttu-id="93528-257">如果未授與存取權，「記錄讀取器代理程式」將發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="93528-257">If access is not granted, the following error is raised by the Log Reader Agent:</span></span>  
  
 <span data-ttu-id="93528-258">「ORA-22285：目錄或 FILEOPEN 作業的檔案不存在」</span><span class="sxs-lookup"><span data-stu-id="93528-258">"ORA-22285: non-existent directory or file for FILEOPEN operation"</span></span>  
  
## <a name="changes-are-made-that-require-reconfiguration-of-the-publisher"></a><span data-ttu-id="93528-259">進行需要重新設定發行者的變更</span><span class="sxs-lookup"><span data-stu-id="93528-259">Changes Are Made That Require Reconfiguration of the Publisher</span></span>  
 <span data-ttu-id="93528-260">對複寫中繼資料資料表或程序的變更要求您卸除「發行者」，然後對其重新設定。</span><span class="sxs-lookup"><span data-stu-id="93528-260">Changes to replication metadata tables or procedures require that you drop and reconfigure the Publisher.</span></span> <span data-ttu-id="93528-261">若要重新設定「發行者」，必須先卸除「發行者」，然後再使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、Transact-SQL 或 RMO 重新設定。</span><span class="sxs-lookup"><span data-stu-id="93528-261">To reconfigure the Publisher, you must drop the Publisher and configure it again using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL, or RMO.</span></span> <span data-ttu-id="93528-262">如需設定發行者的詳細資訊，請參閱[設定 Oracle 發行者](configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="93528-262">For information about configuring the Publisher, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="93528-263">**卸除 Oracle 發行者 (** SQL Server Management Studio **)**</span><span class="sxs-lookup"><span data-stu-id="93528-263">**To drop an Oracle Publisher (** SQL Server Management Studio **)**</span></span>  
  
1.  <span data-ttu-id="93528-264">連接到 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中「Oracle 發行者」的「散發者」，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="93528-264">Connect to the Distributor for the Oracle Publisher in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and expand the server node.</span></span>  
  
2.  <span data-ttu-id="93528-265">以滑鼠右鍵按一下 **[複寫]** ，然後按一下 **[散發者屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="93528-265">Right-click **Replication**, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="93528-266">在 **[散發者屬性]** 對話方塊的 **[發行者]** 頁面上，清除「Oracle 發行者」的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="93528-266">On the **Publishers** page of the **Distributor Properties** dialog box, clear the check box for the Oracle Publisher.</span></span>  
  
4.  <span data-ttu-id="93528-267">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="93528-267">Click **OK**.</span></span>  
  
 <span data-ttu-id="93528-268">**若要卸除 Oracle 發行者 (Transact-SQL)**</span><span class="sxs-lookup"><span data-stu-id="93528-268">**To drop an Oracle Publisher (Transact-SQL)**</span></span>  
  
-   <span data-ttu-id="93528-269">執行 **sp_dropdistpublisher**。</span><span class="sxs-lookup"><span data-stu-id="93528-269">Execute **sp_dropdistpublisher**.</span></span> <span data-ttu-id="93528-270">如需詳細資訊，請參閱 [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="93528-270">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93528-271">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93528-271">See Also</span></span>  
 <span data-ttu-id="93528-272">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="93528-272">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="93528-273">Oracle 發行概觀</span><span class="sxs-lookup"><span data-stu-id="93528-273">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
