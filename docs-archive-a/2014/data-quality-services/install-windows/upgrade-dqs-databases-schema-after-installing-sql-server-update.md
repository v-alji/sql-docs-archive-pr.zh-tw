---
title: 在安裝 SQL Server 更新之後升級 DQS 資料庫結構描述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 80a1714ea250cf7cf5d34bc9d208a42a64284308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596920"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a><span data-ttu-id="77517-102">在安裝 SQL Server 更新之後升級 DQS 資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="77517-102">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>
  <span data-ttu-id="77517-103">在之前設定的 DQS 執行個體上安裝 SQL Server 更新 (修補、Hotfix 或累計更新) 之後，您可能必須使用 **upgrade** 命令列參數執行 DQSInstaller.exe 檔案來升級 DQS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="77517-103">After you have installed a SQL Server update (patch, hotfix, or cumulative update) on a previously configured DQS instance, you might have to upgrade the DQS databases schema by running the DQSInstaller.exe file with the **upgrade** command line parameter.</span></span> <span data-ttu-id="77517-104">否則，當您嘗試使用 Data Quality Client 連接至資料品質伺服器時，您可能會收到以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="77517-104">Otherwise, you might receive the following error while trying to connect to Data Quality Server using your Data Quality Client:</span></span>  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 <span data-ttu-id="77517-105">升級 DQS 資料庫結構描述並不會影響 DQS 資料庫中的現有資料 (知識庫、資料品質專案及 DQS_STAGING_DATA 資料庫中的匯出結果)。</span><span class="sxs-lookup"><span data-stu-id="77517-105">Upgrading DQS databases schema does not impact your existing data in the DQS databases (knowledge bases, data quality projects, and exported results in the DQS_STAGING_DATA database).</span></span> <span data-ttu-id="77517-106">但是，在您升級 DQS 資料庫結構描述之前必須先備份 DQS 資料庫，以免在結構描述升級期間有任何意外的資料遺失狀況。</span><span class="sxs-lookup"><span data-stu-id="77517-106">However, you must back up your DQS databases before upgrading DQS databases schema to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="77517-107">如需有關備份 DQS 資料庫的詳細資訊，請參閱 [備份及還原 DQS 資料庫](../backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="77517-107">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77517-108">大部分的 SQL Server 更新都需要升級至 DQS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="77517-108">Most of the SQL Server updates will require an upgrade to the DQS databases schema.</span></span> <span data-ttu-id="77517-109">如需將需要升級至 DQS 資料庫結構描述之 SQL Server 更新的詳細資訊，請參閱 [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(升級 DQS：在 Data Quality Services 上安裝累計更新或 Hotfix 修補) 中步驟 1.A 的圖表。</span><span class="sxs-lookup"><span data-stu-id="77517-109">For information about the SQL Server updates that will require an upgrade to the DQS databases schema, see the chart in step 1.A in [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="77517-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="77517-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="77517-111">您必須以 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 電腦上 Administrator 群組成員的身分登入。</span><span class="sxs-lookup"><span data-stu-id="77517-111">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="77517-112">您的 Windows 使用者帳戶必須是安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 之 SQL Server 執行個體上系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="77517-112">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-dqs-databases-schema"></a><span data-ttu-id="77517-113">若要升級 DQS 資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="77517-113">To upgrade DQS databases schema</span></span>  
  
1.  <span data-ttu-id="77517-114">(建議) 在您繼續升級結構描述之前，請先備份 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="77517-114">(Recommended) Back up your DQS databases before you proceed with the schema upgrade.</span></span> <span data-ttu-id="77517-115">如需有關備份 DQS 資料庫的詳細資訊，請參閱 [備份及還原 DQS 資料庫](../backing-up-and-restoring-dqs-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="77517-115">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="77517-116">啟動 [命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="77517-116">Start Command Prompt.</span></span>  
  
3.  <span data-ttu-id="77517-117">在命令提示字元中，將目錄變更為 DQSInstaller.exe 所在的位置。</span><span class="sxs-lookup"><span data-stu-id="77517-117">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="77517-118">如果已經安裝了 SQL Server 的預設執行個體，DQSInstaller.exe 檔會位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn。</span><span class="sxs-lookup"><span data-stu-id="77517-118">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  <span data-ttu-id="77517-119">在命令提示字元中輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="77517-119">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  <span data-ttu-id="77517-120">安裝程式會提示您先備份 DQS 資料庫後再繼續。</span><span class="sxs-lookup"><span data-stu-id="77517-120">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="77517-121">如果您已經備份 DQS 資料庫，請輸入 `Y` 或 `Yes` 然後按 ENTER 繼續升級。</span><span class="sxs-lookup"><span data-stu-id="77517-121">If you have already backed up your DQS databases, type `Y` or `Yes` and press ENTER to continue with the upgrade.</span></span>  
  
6.  <span data-ttu-id="77517-122">在成功升級 DQS 資料庫結構描述之後，將會顯示完成訊息。</span><span class="sxs-lookup"><span data-stu-id="77517-122">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="77517-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="77517-123">Next Steps</span></span>  
 <span data-ttu-id="77517-124">從 Data Quality Client 應用程式登入已升級的資料品質伺服器。</span><span class="sxs-lookup"><span data-stu-id="77517-124">Log on to the upgraded Data Quality Server from a Data Quality Client application.</span></span>  
  
 <span data-ttu-id="77517-125">如需有關在安裝 SQL Server 更新之後升級 DQS 資料庫結構描述及相關疑難排解步驟的詳細資訊，請參閱 [升級 DQS：在 Data Quality Services 上安裝累計更新或 Hotfix 修補](https://go.microsoft.com/fwlink/?LinkID=251565)。</span><span class="sxs-lookup"><span data-stu-id="77517-125">For more information about upgrading DQS databases schema after installing SQL Server updates and associated troubleshooting steps, see [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77517-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77517-126">See Also</span></span>  
 <span data-ttu-id="77517-127">[安裝 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="77517-127">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="77517-128">在 .NET Framework 更新之後升級 SQLCLR 組件</span><span class="sxs-lookup"><span data-stu-id="77517-128">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
