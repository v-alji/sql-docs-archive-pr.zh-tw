---
title: 設定 Integration Services 服務的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 055eadd9a1d59c59dd40675b142eae480763f6f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709725"
---
# <a name="set-the-properties-of-the-integration-services-service"></a><span data-ttu-id="74573-102">設定 Integration Services 服務的屬性</span><span class="sxs-lookup"><span data-stu-id="74573-102">Set the Properties of the Integration Services Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="74573-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="74573-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="74573-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="74573-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="74573-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="74573-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="74573-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務會管理並監視 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的封裝。</span><span class="sxs-lookup"><span data-stu-id="74573-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages and monitors packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="74573-107">當您第一次安裝時 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務就會啟動，而且服務的啟動類型會設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="74573-107">When you first install [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span>  
  
 <span data-ttu-id="74573-108">在您已經安裝 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務之後，就可以使用 [SQL Server 組態管理員] 或 [服務] MMC 嵌入式管理單元來設定服務的屬性。</span><span class="sxs-lookup"><span data-stu-id="74573-108">After the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has been installed, you can set the properties of the service by using either SQL Server Configuration Manager or the Services MMC snap-in.</span></span>  
  
 <span data-ttu-id="74573-109">若要設定服務的其他重要功能 (包括它儲存和管理封裝的位置)，您就必須修改服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="74573-109">To configure other important features of the service, including the locations where it stores and manages packages, you must modify the configuration file of the service.</span></span> <span data-ttu-id="74573-110">如需詳細資訊，請參閱 [設定 Integration Services 服務 &#40;SSIS 服務&#41;](service/integration-services-service-ssis-service.md)回溯相容。</span><span class="sxs-lookup"><span data-stu-id="74573-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a><span data-ttu-id="74573-111">使用 SQL Server 組態管理員來設定 Integration Services 服務的屬性</span><span class="sxs-lookup"><span data-stu-id="74573-111">To set properties of the Integration Services service by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="74573-112">在 **[開始]** 功能表上，依序指向 **[所有程式]** 、 **[Microsoft SQL Server]** 和 **[組態工具]** ，然後按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="74573-112">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="74573-113">在 [SQL Server 組態管理員]\*\*\*\* 嵌入式管理單元中，尋找服務清單中的 [SQL Server Integration Services]\*\*\*\*，以滑鼠右鍵按一下 [SQL Server Integration Services]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74573-113">In the **SQL Server Configuration Manager** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="74573-114">在 [ **SQL Server Integration Services 屬性**] 對話方塊中，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="74573-114">In the **SQL Server Integration Services Properties** dialog box you can do the following:</span></span>  
  
    -   <span data-ttu-id="74573-115">按一下 **[登入]** 索引標籤，以檢視登入資訊 (例如帳戶名稱)。</span><span class="sxs-lookup"><span data-stu-id="74573-115">Click the **Log On** tab to view the logon information such as the account name.</span></span>  
  
    -   <span data-ttu-id="74573-116">按一下 **[服務]** 索引標籤，即可檢視服務的相關資訊 (例如主機電腦的名稱)，並指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的啟動模式。</span><span class="sxs-lookup"><span data-stu-id="74573-116">Click the **Service** tab to view information about the service such as the name of the host computer and to specify the start mode of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="74573-117">[進階]\*\*\*\* 索引標籤不包含 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="74573-117">The **Advanced** tab contains no information for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="74573-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="74573-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="74573-119">在 [檔案]\*\*\*\* 功能表上，按一下 [結束]\*\*\*\*，以關閉 [SQL Server 組態管理員]\*\*\*\* 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="74573-119">On the **File** menu, click **Exit** to close the **SQL Server Configuration Manager** snap-in.</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a><span data-ttu-id="74573-120">使用服務來設定 Integration Services 服務的屬性</span><span class="sxs-lookup"><span data-stu-id="74573-120">To set properties of the Integration Services service by using Services</span></span>  
  
1.  <span data-ttu-id="74573-121">在 **[控制台]** 中，如果您使用「一般檢視」，請按一下 **[系統管理工具]**，如果您使用「類別檢視」，請按一下 **[效能及維護]** ，然後按一下 **[系統管理工具]**。</span><span class="sxs-lookup"><span data-stu-id="74573-121">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="74573-122">按一下 [服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74573-122">Click **Services**.</span></span>  
  
3.  <span data-ttu-id="74573-123">在 [服務]\*\*\*\* 嵌入式管理單元中，尋找服務清單中的 [SQL Server Integration Services]\*\*\*\*，以滑鼠右鍵按一下 [SQL Server Integration Services]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74573-123">In the **Services** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="74573-124">在 **[SQL Server Integration Services 屬性]** 對話方塊中，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="74573-124">In the **SQL Server Integration Services Properties** dialog box, you can do the following:</span></span>  
  
    -   <span data-ttu-id="74573-125">按一下 [**一般**] 索引標籤。若要啟用服務，請選取 [手動] 或 [自動] 啟動類型。</span><span class="sxs-lookup"><span data-stu-id="74573-125">Click the **General** tab. To enable the service, select either the manual or automatic startup type.</span></span> <span data-ttu-id="74573-126">若要停用服務，請在 **[啟動類型]** 方塊中選取 [停用]。</span><span class="sxs-lookup"><span data-stu-id="74573-126">To disable the service, select Disable in the **Startup type** box.</span></span> <span data-ttu-id="74573-127">選取 [停用] 不會停止目前正在執行的服務。</span><span class="sxs-lookup"><span data-stu-id="74573-127">Selecting Disable does not stop the service if it is currently running.</span></span>  
  
         <span data-ttu-id="74573-128">如果已啟用服務，則可以按一下 **[停止]** 停止服務，或按一下 **[啟動]** 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="74573-128">If the service is already enabled, you can click **Stop** to stop the service, or click **Start** to start the service.</span></span>  
  
    -   <span data-ttu-id="74573-129">按一下 **[登入]** 索引標籤，即可檢視或編輯登入資訊。</span><span class="sxs-lookup"><span data-stu-id="74573-129">Click the **Log On** tab to view or edit the logon information.</span></span>  
  
    -   <span data-ttu-id="74573-130">按一下 **[復原]** 索引標籤，以檢視服務失敗的預設電腦回應。</span><span class="sxs-lookup"><span data-stu-id="74573-130">Click the **Recovery** tab to view the default computer responses to service failure.</span></span> <span data-ttu-id="74573-131">您可以修改這些選項，以配合您的環境。</span><span class="sxs-lookup"><span data-stu-id="74573-131">You can modify these options to suit your environment.</span></span>  
  
    -   <span data-ttu-id="74573-132">按一下 **[相依性]** 索引標籤，以檢視相依性服務的清單。</span><span class="sxs-lookup"><span data-stu-id="74573-132">Click the **Dependencies** tab to view a list of dependent services.</span></span> <span data-ttu-id="74573-133">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務不具有相依性。</span><span class="sxs-lookup"><span data-stu-id="74573-133">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has no dependencies.</span></span>  
  
5.  <span data-ttu-id="74573-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="74573-134">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="74573-135">或者，如果啟動類型是 [手動] 或 [自動]，則可以用滑鼠右鍵按一下 [SQL Server Integration Services]\*\*\*\*，然後按一下 [啟動]、[停止] 或 [重新啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74573-135">Optionally, if the startup type is Manual or Automatic, you can right-click **SQL Server Integration Services** and click **Start, Stop, or Restart**.</span></span>  
  
7.  <span data-ttu-id="74573-136">在 [檔案]\*\*\*\* 功能表上，按一下 [結束]\*\*\*\*，以關閉 [服務]\*\*\*\* 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="74573-136">On the **File** menu, click **Exit** to close the **Services** snap-in.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74573-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74573-137">See Also</span></span>  
 [<span data-ttu-id="74573-138">管理 Integration Services 服務</span><span class="sxs-lookup"><span data-stu-id="74573-138">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
