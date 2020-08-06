---
title: 存取用於 DQS 作業的資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 515b087a8d16e44314d1a21d3dfbd6f13c767f5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701989"
---
# <a name="access-data-for-the-dqs-operations"></a><span data-ttu-id="71222-102">存取用於 DQS 作業的資料</span><span class="sxs-lookup"><span data-stu-id="71222-102">Access Data for the DQS Operations</span></span>
  <span data-ttu-id="71222-103">若要使用您的來源資料進行 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 作業，並匯出已處理的資料，您可以執行下列任一項操作：</span><span class="sxs-lookup"><span data-stu-id="71222-103">To use your source data for [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) operations, and export your processed data, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="71222-104">將來源資料複製到 DQS_STAGING_DATA 資料庫中的資料表/檢視，然後使用該資料進行 DQS 作業。</span><span class="sxs-lookup"><span data-stu-id="71222-104">Copy your source data to a table/view in the DQS_STAGING_DATA database, and then use it for DQS operations.</span></span> <span data-ttu-id="71222-105">您也可以將已處理的資料匯出到 DQS_STAGING_DATA 資料庫的新資料表中。</span><span class="sxs-lookup"><span data-stu-id="71222-105">You can also export the processed data to a new table in the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="71222-106">若要這樣做，您的 Windows 使用者帳戶必須擁有對於 DQS_STAGING_DATA 資料庫的讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="71222-106">To do so, your Windows user account must be granted read/write access to the DQS_STAGING_DATA database.</span></span>  
  
-   <span data-ttu-id="71222-107">使用您自己的資料庫做為 DQS 作業的來源資料以及匯出已處理資料的目的地。</span><span class="sxs-lookup"><span data-stu-id="71222-107">Use your own database as the source data for the DQS operations, and destination for exporting the processed data.</span></span> <span data-ttu-id="71222-108">若要執行此作業，請確定您的資料庫位於和 Data Quality Server 資料庫相同的 SQL Server 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="71222-108">To do so, ensure that your database is in the same SQL Server instance as the Data Quality Server databases.</span></span> <span data-ttu-id="71222-109">否則，在 Data Quality Client 中，該資料庫將無法用於進行 DQS 作業。</span><span class="sxs-lookup"><span data-stu-id="71222-109">Otherwise, the database will not be available in the Data Quality Client for DQS operations.</span></span> <span data-ttu-id="71222-110">此外，必須授與您的 Windows 使用者帳戶 DQS_STAGING_DATA 資料庫的權限，才可匯出比對結果，因為比對結果會以兩階段匯出：首先會將比對結果先匯出到 DQS_STAGING_DATA 資料庫中的暫存資料表，然後再將其移到目的地資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="71222-110">Also, your Windows user account must be granted access on the DQS_STAGING_DATA database for exporting the matching results because matching results are exported in two phases: first, the matching results are exported to the temporary tables in the DQS_STAGING_DATA database, and then moved to the table in your destination database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="71222-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="71222-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="71222-112">您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的安裝。</span><span class="sxs-lookup"><span data-stu-id="71222-112">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="71222-113">如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="71222-113">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="71222-114">您的 Windows 使用者帳戶在資料庫引擎執行個體中，必須是適當固定伺服器角色 (例如 securityadmin、serveradmin 或 sysadmin) 的成員，才能授與/修改對資料庫上 SQL 登入的存取權。</span><span class="sxs-lookup"><span data-stu-id="71222-114">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) in the database engine instance to grant/modify access to SQL login on databases.</span></span>  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a><span data-ttu-id="71222-115">授與使用者 DQS_STAGING_DATA 資料庫的讀/寫存取權</span><span class="sxs-lookup"><span data-stu-id="71222-115">To grant read/write access to a User on the DQS_STAGING_DATA Database</span></span>  
  
1.  <span data-ttu-id="71222-116">啟動 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="71222-116">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="71222-117">在 Microsoft SQL Server Management Studio 中，展開您的 SQL Server 執行個體及 **[安全性]**，然後展開 **[登入]**。</span><span class="sxs-lookup"><span data-stu-id="71222-117">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="71222-118">以滑鼠右鍵按一下 SQL 登入，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="71222-118">Right-click a SQL login, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="71222-119">在 **[登入屬性]** 對話方塊的左窗格中，按一下 **[使用者對應]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="71222-119">In the **Login Properties** dialog box, click the **User Mapping** page in the left pane.</span></span>  
  
5.  <span data-ttu-id="71222-120">在右窗格中，選取 **[DQS_STAGING_DATA]** 資料庫的 **[對應]** 資料行底下的核取方塊，然後在 **[資料庫角色成員資格對象 :DQS_STAGING_DATA]** 窗格中選取下列角色：</span><span class="sxs-lookup"><span data-stu-id="71222-120">In the right pane, select the check box under the **Map** column for the **DQS_STAGING_DATA** database, and then select the following roles in the **Database role membership for: DQS_STAGING_DATA** pane:</span></span>  
  
    -   <span data-ttu-id="71222-121">**db_datareader**：從資料表/檢視讀取資料。</span><span class="sxs-lookup"><span data-stu-id="71222-121">**db_datareader**: Read data from tables/views.</span></span>  
  
    -   <span data-ttu-id="71222-122">**db_datawriter**：加入、刪除或變更資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="71222-122">**db_datawriter**: Add, delete, or change data in tables.</span></span>  
  
    -   <span data-ttu-id="71222-123">**db_ddladmin**：建立、修改或刪除資料表/檢視。</span><span class="sxs-lookup"><span data-stu-id="71222-123">**db_ddladmin**: Create, modify, or delete tables/views.</span></span>  
  
6.  <span data-ttu-id="71222-124">在 **[登入屬性]** 對話方塊中，按一下 **[確定]** 套用變更。</span><span class="sxs-lookup"><span data-stu-id="71222-124">In the **Login Properties** dialog box, click **OK** to apply the changes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="71222-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71222-125">Next Steps</span></span>  
 <span data-ttu-id="71222-126">嘗試執行存取資料庫做為 DQS 作業之資料來源的 DQS 作業，然後將處理過的資料匯出到資料庫。</span><span class="sxs-lookup"><span data-stu-id="71222-126">Try performing DQS operations that accesses the database as data source for DQS operation, and then exports the processed data to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71222-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71222-127">See Also</span></span>  
 [<span data-ttu-id="71222-128">安裝 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="71222-128">Install Data Quality Services</span></span>](install-data-quality-services.md)  
  
  
