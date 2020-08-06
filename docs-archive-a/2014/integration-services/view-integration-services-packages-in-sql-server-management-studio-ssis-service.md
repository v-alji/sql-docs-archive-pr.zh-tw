---
title: 在 SQL Server Management Studio (SSIS 服務) 中查看 Integration Services 套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ba86320f1b1a685eab6e80399f3e8c21bd110eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687027"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a><span data-ttu-id="bf01a-102">在 SQL Server Management Studio 中檢視 Integration Services 封裝 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="bf01a-102">View Integration Services Packages in SQL Server Management Studio (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="bf01a-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="bf01a-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="bf01a-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="bf01a-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="bf01a-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="bf01a-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="bf01a-106">此程序描述如何在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，以及檢視 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務所管理的封裝清單。</span><span class="sxs-lookup"><span data-stu-id="bf01a-106">This procedure describes how to connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and view a list of the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
### <a name="to-connect-to-integration-services"></a><span data-ttu-id="bf01a-107">連接到 Integration Services</span><span class="sxs-lookup"><span data-stu-id="bf01a-107">To connect to Integration Services</span></span>  
  
1.  <span data-ttu-id="bf01a-108">按一下 **[開始]** ，依序指向 **[所有程式]** 和 **[Microsoft SQL Server]** ，然後按一下 **[SQL Server Management Studio]** 。</span><span class="sxs-lookup"><span data-stu-id="bf01a-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="bf01a-109">在 [連接到伺服器] 對話方塊中，選取 [伺服器類型] 清單中的 [Integration Services]，在 [伺服器名稱] 方塊中提供伺服器名稱，然後按一下 [連接]。</span><span class="sxs-lookup"><span data-stu-id="bf01a-109">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and then click **Connect**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bf01a-110">如果您無法連接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務目前可能沒有執行。</span><span class="sxs-lookup"><span data-stu-id="bf01a-110">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="bf01a-111">若要了解此服務的狀態，請按一下 **[開始]** ，依序指向 **[所有程式]** 、 **[Microsoft SQL Server]** 和 **[組態工具]** ，然後按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="bf01a-111">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="bf01a-112">在左窗格中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="bf01a-112">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="bf01a-113">在右窗格中，尋找 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="bf01a-113">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="bf01a-114">如果此服務尚未執行，請將它啟動。</span><span class="sxs-lookup"><span data-stu-id="bf01a-114">Start the service if it is not already running.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bf01a-115">隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="bf01a-115">opens.</span></span> <span data-ttu-id="bf01a-116">依預設，[物件總管] 視窗會在 Studio 左下角開啟並定位。</span><span class="sxs-lookup"><span data-stu-id="bf01a-116">By default the Object Explorer window is open and positioned in the lower-left corner of the studio.</span></span> <span data-ttu-id="bf01a-117">如果 [物件總管] 未開啟，請按一下 **[檢視]** 功能表上的 **[物件總管]** 。</span><span class="sxs-lookup"><span data-stu-id="bf01a-117">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a><span data-ttu-id="bf01a-118">若要檢視 Integration Services 服務所管理的封裝</span><span class="sxs-lookup"><span data-stu-id="bf01a-118">To view the packages that Integration Services service manages</span></span>  
  
1.  <span data-ttu-id="bf01a-119">在 [物件總管] 中，展開 [存放的封裝] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf01a-119">In Object Explorer, expand the Stored Packages folder.</span></span>  
  
2.  <span data-ttu-id="bf01a-120">展開 [Stored Packages] 的子資料夾以顯示封裝。</span><span class="sxs-lookup"><span data-stu-id="bf01a-120">Expand the Stored Packages subfolders to show packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf01a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf01a-121">See Also</span></span>  
 <span data-ttu-id="bf01a-122">[套件管理 &#40;SSIS 服務&#41;](service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="bf01a-122">[Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="bf01a-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf01a-123">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
