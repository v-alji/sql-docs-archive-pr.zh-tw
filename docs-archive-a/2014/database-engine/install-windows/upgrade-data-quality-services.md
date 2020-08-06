---
title: 升級 Data Quality Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d2544df341a831f2f676ec58150ed64a800fb96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594164"
---
# <a name="upgrade-data-quality-services"></a><span data-ttu-id="6bfd6-102">升級 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="6bfd6-102">Upgrade Data Quality Services</span></span>
  <span data-ttu-id="6bfd6-103">本主題提供有關如何將您現有的 Data Quality Services (DQS) 安裝升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-103">This topic provides information on how to upgrade your existing installation of Data Quality Services (DQS) to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="6bfd6-104">將 DQS 中的資料品質伺服器升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的過程中，您也必須升級 DQS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-104">As part of upgrading your Data Quality Server in DQS to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must also upgrade the DQS databases schema.</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="6bfd6-105">在升級 DQS 之前，您必須先備份 DQS 資料庫，以免在結構描述升級期間有任何意外的遺失資料狀況。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-105">You must back up your DQS databases before upgrading DQS to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="6bfd6-106">如需有關備份 DQS 資料庫的詳細資訊，請參閱 [備份及還原 DQS 資料庫](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-106">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
> -   <span data-ttu-id="6bfd6-107">您可以使用最新或舊版 Data Quality Client 連接至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 Data Quality Server 或 Integration Services 中的 [DQS 清理轉換](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) ，以執行您的資料品質工作。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-107">You can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client or the [DQS Cleansing Transformation](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) in Integration Services to perform your data quality tasks.</span></span>  
> -   <span data-ttu-id="6bfd6-108">將 Data Quality Services 和 Master Data Services 升級為 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] CTP2 之後，您可以繼續使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 版適用於 Excel 的 Master Data Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-108">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Data Quality Services and Master Data Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="6bfd6-109">不過，在升級為 SQL Server 2014 CTP2 之後，任何舊版適用於 Excel 的 Master Data Services 增益集將無法運作。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-109">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="6bfd6-110">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 您可以在 [這裡](https://go.microsoft.com/fwlink/?LinkId=328664)下載  SP1 版適用於 Excel 的 Master Data Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-110">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6bfd6-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="6bfd6-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="6bfd6-112">您必須以 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦上 Administrator 群組成員的身分登入。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="6bfd6-113">您的 Windows 使用者帳戶必須是安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 之 SQL Server 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
##  <a name="upgrading-dqs"></a><a name="Upgrade"></a> <span data-ttu-id="6bfd6-114">升級 DQS</span><span class="sxs-lookup"><span data-stu-id="6bfd6-114">Upgrading DQS</span></span>  
 <span data-ttu-id="6bfd6-115">升級 DQS：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-115">To upgrade DQS:</span></span>  
  
1.  <span data-ttu-id="6bfd6-116">在開始升級程序之前，請先備份 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-116">Back up your DQS databases before you start the upgrade process.</span></span> <span data-ttu-id="6bfd6-117">如需有關備份 DQS 資料庫的詳細資訊，請參閱 [備份及還原 DQS 資料庫](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-117">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="6bfd6-118">將安裝 DQS 的 SQL Server 執行個體升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-118">Upgrade the SQL Server instance where DQS is installed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="6bfd6-119">執行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-119">Run the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="6bfd6-120">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-120">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="6bfd6-121">在右窗格中，按一下 [**從 SQL Server 2005]、[SQL Server 2008]、[SQL Server 2008 R2] 或 [SQL Server 2012**]。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-121">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="6bfd6-122">完成安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-122">Complete the Setup wizard.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6bfd6-123">如果 Data Quality Client 先前已安裝在這部電腦上，此作業會將您的 SQL Server 執行個體升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，而且也會安裝最新的 Data Quality Client。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-123">This will upgrade your SQL Server instance to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and also install the latest Data Quality Client, if Data Quality Client was previously installed on this computer.</span></span> <span data-ttu-id="6bfd6-124">如果您已將 Data Quality Client 安裝在其他電腦上，則必須在那些電腦上執行步驟 2 的子步驟，才能安裝 Data Quality Client 的目前版本。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-124">If you have Data Quality Client installed on other computers, you must run the sub steps in Step 2 on those computers to install the current version of Data Quality Client.</span></span> <span data-ttu-id="6bfd6-125">安裝精靈會將 Data Quality Client 的目前版本與 Data Quality Client 的現有版本並列安裝。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-125">The Setup wizard installs the current version of Data Quality Client alongside the existing version of Data Quality Client.</span></span> <span data-ttu-id="6bfd6-126">升級 DQS 資料庫結構描述之後，您可以使用最新或舊版 Data Quality Client 連接至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的資料品質伺服器。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-126">After you upgrade the DQS databases schema, you can connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Data Quality Server by using the current or an earlier version of Data Quality Client.</span></span>  
  
3.  <span data-ttu-id="6bfd6-127">升級 DQS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-127">Upgrade the DQS databases schema.</span></span>  
  
    1.  <span data-ttu-id="6bfd6-128">以系統管理員身分啟動命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-128">Start Command Prompt as an administrator.</span></span>  
  
    2.  <span data-ttu-id="6bfd6-129">在命令提示字元中，將目錄變更為 DQSInstaller.exe 所在的位置。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-129">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="6bfd6-130">若為 SQL Server 的預設執行個體，DQSInstaller.exe 檔案位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-130">For the default instance of SQL Server, the DQSInstaller.exe file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  <span data-ttu-id="6bfd6-131">在命令提示字元中輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-131">At the command prompt, type the following command, and press ENTER:</span></span>  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  <span data-ttu-id="6bfd6-132">安裝程式會提示您先備份 DQS 資料庫後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-132">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="6bfd6-133">若已備份 DQS 資料庫，請輸入 `Y` 或 `Yes`，然後按 ENTER 鍵繼續升級。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-133">If you have already backed up your DQS databases, type `Y` or `Yes`, and then press ENTER to continue with the upgrade.</span></span>  
  
    5.  <span data-ttu-id="6bfd6-134">在成功升級 DQS 資料庫結構描述之後，將會顯示完成訊息。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-134">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
##  <a name="verifying-the-dqs-databases-schema-upgrade"></a><a name="Verify"></a> <span data-ttu-id="6bfd6-135">確認 DQS 資料庫結構描述升級</span><span class="sxs-lookup"><span data-stu-id="6bfd6-135">Verifying the DQS Databases Schema Upgrade</span></span>  
 <span data-ttu-id="6bfd6-136">若要確認 DQS 資料庫結構描述升級成功，您可以查詢中每個資料庫中的 A_DB_VERSION 資料表，以檢查 DQS_MAIN 和 DQS_PROJECTS 資料庫中的目前版本。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-136">To verify that DQS databases schema have successfully upgraded, you can check the current version in the DQS_MAIN and DQS_PROJECTS databases by querying the A_DB_VERSION table in each database.</span></span> <span data-ttu-id="6bfd6-137">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-137">To do so:</span></span>  
  
1.  <span data-ttu-id="6bfd6-138">啟動 SQL Server Management Studio，並連接到包含已升級之 DQS 資料庫結構描述的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-138">Start SQL Server Management Studio, and connect to the SQL Server instance that contains the upgraded DQS databases schema.</span></span>  
  
2.  <span data-ttu-id="6bfd6-139">執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-139">Run the following query:</span></span>  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  <span data-ttu-id="6bfd6-140">輸出會顯示每個升級項目和升級日期。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-140">The output will display an entry for each upgrade along with the date of the upgrade.</span></span> <span data-ttu-id="6bfd6-141">最新日期的最大 VERSION_ID 和 ASSEMBLY_VERSION 為目前版本。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-141">The maximum VERSION_ID and ASSEMBLY_VERSION on the latest date is the current version.</span></span> <span data-ttu-id="6bfd6-142">STATUS 資料行中的值為 2 代表成功。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-142">A value of 2 in the STATUS column indicates success.</span></span> <span data-ttu-id="6bfd6-143">如果發生錯誤，錯誤會列示在 ERROR 資料行中。</span><span class="sxs-lookup"><span data-stu-id="6bfd6-143">If an error has occurred, the error will be listed in the ERROR column.</span></span> <span data-ttu-id="6bfd6-144">範例輸出：</span><span class="sxs-lookup"><span data-stu-id="6bfd6-144">A sample output:</span></span>  
  
    |<span data-ttu-id="6bfd6-145">ID</span><span class="sxs-lookup"><span data-stu-id="6bfd6-145">ID</span></span>|<span data-ttu-id="6bfd6-146">UPGRADE_DATE</span><span class="sxs-lookup"><span data-stu-id="6bfd6-146">UPGRADE_DATE</span></span>|<span data-ttu-id="6bfd6-147">VERSION_ID</span><span class="sxs-lookup"><span data-stu-id="6bfd6-147">VERSION_ID</span></span>|<span data-ttu-id="6bfd6-148">ASSEMBLY_VERSION</span><span class="sxs-lookup"><span data-stu-id="6bfd6-148">ASSEMBLY_VERSION</span></span>|<span data-ttu-id="6bfd6-149">USER_NAME</span><span class="sxs-lookup"><span data-stu-id="6bfd6-149">USER_NAME</span></span>|<span data-ttu-id="6bfd6-150">狀態</span><span class="sxs-lookup"><span data-stu-id="6bfd6-150">STATUS</span></span>|<span data-ttu-id="6bfd6-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="6bfd6-151">ERROR</span></span>|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |<span data-ttu-id="6bfd6-152">1000</span><span class="sxs-lookup"><span data-stu-id="6bfd6-152">1000</span></span>|<span data-ttu-id="6bfd6-153">2013-08-11 05:26:39.567</span><span class="sxs-lookup"><span data-stu-id="6bfd6-153">2013-08-11 05:26:39.567</span></span>|<span data-ttu-id="6bfd6-154">1200</span><span class="sxs-lookup"><span data-stu-id="6bfd6-154">1200</span></span>|<span data-ttu-id="6bfd6-155">11.0.3000.0</span><span class="sxs-lookup"><span data-stu-id="6bfd6-155">11.0.3000.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="6bfd6-156">2</span><span class="sxs-lookup"><span data-stu-id="6bfd6-156">2</span></span>||  
    |<span data-ttu-id="6bfd6-157">1001</span><span class="sxs-lookup"><span data-stu-id="6bfd6-157">1001</span></span>|<span data-ttu-id="6bfd6-158">2013-09-19 15:09:37.750</span><span class="sxs-lookup"><span data-stu-id="6bfd6-158">2013-09-19 15:09:37.750</span></span>|<span data-ttu-id="6bfd6-159">1600</span><span class="sxs-lookup"><span data-stu-id="6bfd6-159">1600</span></span>|<span data-ttu-id="6bfd6-160">12.0.xxxx.0</span><span class="sxs-lookup"><span data-stu-id="6bfd6-160">12.0.xxxx.0</span></span>|\<DOMAIN\UserName>|<span data-ttu-id="6bfd6-161">2</span><span class="sxs-lookup"><span data-stu-id="6bfd6-161">2</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="6bfd6-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bfd6-162">See Also</span></span>  
 <span data-ttu-id="6bfd6-163">[安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="6bfd6-163">[Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md) </span></span>  
 <span data-ttu-id="6bfd6-164">[移除 Data Quality Server 物件](../../sql-server/install/remove-data-quality-server-objects.md) </span><span class="sxs-lookup"><span data-stu-id="6bfd6-164">[Remove Data Quality Server Objects](../../sql-server/install/remove-data-quality-server-objects.md) </span></span>  
 [<span data-ttu-id="6bfd6-165">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="6bfd6-165">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
  
  
