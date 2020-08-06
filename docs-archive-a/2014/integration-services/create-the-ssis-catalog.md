---
title: 建立 SSIS 目錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2572cc131f34a21171054a159e3b7968c453a780
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592785"
---
# <a name="create-the-ssis-catalog"></a><span data-ttu-id="48479-102">建立 SSIS 目錄</span><span class="sxs-lookup"><span data-stu-id="48479-102">Create the SSIS Catalog</span></span>
  <span data-ttu-id="48479-103">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中設計和測試封裝之後，可以將包含封裝的專案，部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="48479-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="48479-104">在您將專案部署至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器之前，該伺服器必須包含 `SSISDB` 目錄。</span><span class="sxs-lookup"><span data-stu-id="48479-104">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the server must contain the `SSISDB` catalog.</span></span> <span data-ttu-id="48479-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 的安裝程式不會自動建立目錄，您必須依照下列指示手動建立目錄。</span><span class="sxs-lookup"><span data-stu-id="48479-105">The installation program for [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] does not automatically create the catalog; you need to manually create the catalog by using the following instructions.</span></span>  
  
 <span data-ttu-id="48479-106">您可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中建立 SSISDB 目錄。</span><span class="sxs-lookup"><span data-stu-id="48479-106">You can create the SSISDB catalog in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="48479-107">您也可以使用 Windows PowerShell 以程式設計方式建立目錄。</span><span class="sxs-lookup"><span data-stu-id="48479-107">You also create the catalog programmatically by using Windows PowerShell.</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a><span data-ttu-id="48479-108">若要在 SQL Server Management Studio 中建立 SSISDB 目錄</span><span class="sxs-lookup"><span data-stu-id="48479-108">To create the SSISDB catalog in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="48479-109">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48479-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="48479-110">連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Database Engine。</span><span class="sxs-lookup"><span data-stu-id="48479-110">Connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Database Engine.</span></span>  
  
3.  <span data-ttu-id="48479-111">在物件總管中，展開伺服器節點，以滑鼠右鍵按一下 [Integration Services 目錄]  節點，然後按一下 [建立目錄] 。</span><span class="sxs-lookup"><span data-stu-id="48479-111">In Object Explorer, expand the server node, right-click the **Integration Services Catalogs** node, and then click **Create Catalog**.</span></span>  
  
4.  <span data-ttu-id="48479-112">按一下 **[啟用 CLR 整合]** 。</span><span class="sxs-lookup"><span data-stu-id="48479-112">Click **Enable CLR Integration**.</span></span>  
  
     <span data-ttu-id="48479-113">目錄便會使用 CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="48479-113">The catalog uses CLR stored procedures.</span></span>  
  
5.  <span data-ttu-id="48479-114">按一下 [在 SQL Server 啟動時允許自動執行 Integration Services 預存程序]，讓 [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) 預存程序會在每次 [!INCLUDE[ssIS](../includes/ssis-md.md)] 伺服器執行個體重新啟動時執行。</span><span class="sxs-lookup"><span data-stu-id="48479-114">Click **Enable automatic execution of Integration Services stored procedure at SQL Server startup** to enable the [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) stored procedure to run each time the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance is restarted.</span></span>  
  
     <span data-ttu-id="48479-115">預存程序會執行 SSISDB 目錄之作業狀態的維護。</span><span class="sxs-lookup"><span data-stu-id="48479-115">The stored procedure performs maintenance of the state of operations for the SSISDB catalog.</span></span> <span data-ttu-id="48479-116">它會在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 伺服器執行個體效能降低時，修正正在執行之任何封裝的狀態。</span><span class="sxs-lookup"><span data-stu-id="48479-116">It fixes the status of any packages there were running if and when the [!INCLUDE[ssIS](../includes/ssis-md.md)] server instance goes down.</span></span>  
  
6.  <span data-ttu-id="48479-117">輸入密碼，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="48479-117">Enter a password, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="48479-118">此密碼保護用來加密目錄資料的資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="48479-118">The password protects the database master key that is used for encrypting the catalog data.</span></span> <span data-ttu-id="48479-119">請將密碼儲存在安全位置。</span><span class="sxs-lookup"><span data-stu-id="48479-119">Save the password in a secure location.</span></span> <span data-ttu-id="48479-120">建議您同時備份資料庫主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="48479-120">It is recommended that you also back up the database master key.</span></span> <span data-ttu-id="48479-121">如需相關資訊，請參閱 [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md)。</span><span class="sxs-lookup"><span data-stu-id="48479-121">For more information, see [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md).</span></span>  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a><span data-ttu-id="48479-122">若要以程式設計方式建立 SSISDB 目錄</span><span class="sxs-lookup"><span data-stu-id="48479-122">To create the SSISDB catalog programmatically</span></span>  
  
1.  <span data-ttu-id="48479-123">執行下列 PowerShell 指令碼：</span><span class="sxs-lookup"><span data-stu-id="48479-123">Execute the following PowerShell script:</span></span>  
  
    ```powershell
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()
    ```  
  
     <span data-ttu-id="48479-124">如需如何使用 Windows PowerShell 和 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空間的其他範例，請參閱 blogs.msdn.com 上的部落格文章：[SQL Server 2012 中的 SSIS 和 PowerShell](https://go.microsoft.com/fwlink/?LinkId=242539)。</span><span class="sxs-lookup"><span data-stu-id="48479-124">For more examples of how to use Windows PowerShell and the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace, see the blog entry, [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), on blogs.msdn.com.</span></span> <span data-ttu-id="48479-125">如需此命名空間的概觀和程式碼範例，請參閱 blogs.msdn.com 上的部落格文章： [SSIS 目錄管理物件模型初探](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)。</span><span class="sxs-lookup"><span data-stu-id="48479-125">For an overview of the namespace and code examples, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48479-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48479-126">See Also</span></span>  
 <span data-ttu-id="48479-127">[SSIS 目錄](catalog/ssis-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="48479-127">[SSIS Catalog](catalog/ssis-catalog.md) </span></span>  
 [<span data-ttu-id="48479-128">備份、 還原和移動的 SSIS 目錄</span><span class="sxs-lookup"><span data-stu-id="48479-128">Backup, Restore, and Move the SSIS Catalog</span></span>](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
