---
title: 指令碼與 PowerShell 搭配 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597018"
---
# <a name="scripting-and-powershell-with-reporting-services"></a><span data-ttu-id="7b3b5-102">指令碼與 PowerShell 搭配 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="7b3b5-102">Scripting and PowerShell with Reporting Services</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7b3b5-103">支援透過指令碼進行各種開發和管理案例，包括 rs.exe 命令列公用程式、適用於 SharePoint 模式報表伺服器的 PowerShell Cmdlet，以及從原生和 SharePoint 模式的 PowerShell 運用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 物件模型。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-103">supports a wide range of development and management scenarios through script, including the rs.exe command line utility, PowerShell cmdlets for SharePoint mode report servers, and leveraging the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] object model from PowerShell for both Native and SharePoint mode.</span></span>

-   <span data-ttu-id="7b3b5-104">系統管理員可以用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 來撰寫指令碼，以將其部署和管理報表伺服器安裝的方式自動化。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-104">Administrators can write script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] to automate how they deploy and manage a report server installation.</span></span> <span data-ttu-id="7b3b5-105">管理員也可以產生並執行能夠建立、設定與更新報表伺服器資料庫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-105">Administrators can also generate and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that create, configure, and update a report server database.</span></span> <span data-ttu-id="7b3b5-106">系統管理員也可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的錄製和播放指令碼功能，將例行的維護工作自動化。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-106">Administrators can also use the record and playback script features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to automate routine maintenance tasks.</span></span>

-   <span data-ttu-id="7b3b5-107">開發人員可以建立包括指令碼的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-107">Developers can create custom applications that include script.</span></span> <span data-ttu-id="7b3b5-108">您可以執行呼叫報表伺服器 Web 服務的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-108">You can run script that makes calls to the Report Server Web service.</span></span> <span data-ttu-id="7b3b5-109">幾乎所有您可以使用 Managed 程式碼撰寫的作業也都可以使用指令碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-109">Almost any operation that you can write in managed code can also be written in script.</span></span>

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7b3b5-110">支援將 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 指令碼作為可由 RS.exe 公用程式處理的指令碼語言，此公用程式是在報表伺服器上執行的指令碼主機。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-110">supports [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET script as the script language that can be processed by the RS.exe utility, a script host that runs on the report server.</span></span>

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a><span data-ttu-id="7b3b5-111">Reporting Services SharePoint 模式的 PowerShell Cmdlet 和範例</span><span class="sxs-lookup"><span data-stu-id="7b3b5-111">Reporting Services SharePoint mode PowerShell cmdlets and samples</span></span>
 <span data-ttu-id="7b3b5-112">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="7b3b5-112">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7b3b5-113">SharePoint 模式包含用於管理報表伺服器的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-113">SharePoint mode includes [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlets for report server administration.</span></span>

-   <span data-ttu-id="7b3b5-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) 包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="7b3b5-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Includes the following examples:</span></span>

    -   <span data-ttu-id="7b3b5-115">建立服務應用程式和 Proxy</span><span class="sxs-lookup"><span data-stu-id="7b3b5-115">Create a service application and proxy</span></span>

    -   <span data-ttu-id="7b3b5-116">檢閱及更新傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="7b3b5-116">Review and update a delivery extension</span></span>

    -   <span data-ttu-id="7b3b5-117">取得並設定 Reporting Services 應用程式資料庫的屬性，例如資料庫逾時</span><span class="sxs-lookup"><span data-stu-id="7b3b5-117">Get and set Properties of the Reporting Service Application Database, for example database timeout</span></span>

    -   <span data-ttu-id="7b3b5-118">列出資料延伸模組</span><span class="sxs-lookup"><span data-stu-id="7b3b5-118">List Data Extensions</span></span>

## <a name="reporting-services-object-model-and-powershell-samples"></a><span data-ttu-id="7b3b5-119">Reporting Services 物件模型和 Powershell 範例</span><span class="sxs-lookup"><span data-stu-id="7b3b5-119">Reporting Services Object model and Powershell samples</span></span>
 <span data-ttu-id="7b3b5-120">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="7b3b5-120">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 <span data-ttu-id="7b3b5-121">PowerShell 呼叫核心物件模型，並在大部分情況適用於 SharePoint 和原生模式，例如移轉工作、訂閱工作和其他相關的 SQL15 訂閱工作範例。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-121">PowerShell calling the core object model and for the most part valid for SharePoint and native mode, for example the migration work, subscription work, and more related samples for subscriptions work in SQL15.</span></span>

-   <span data-ttu-id="7b3b5-122">[使用 PowerShell 變更及列出 Reporting Services 訂閱擁有者並執行訂閱](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-122">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>

-   <span data-ttu-id="7b3b5-123">[透過原生模式報表伺服器使用 PowerShell 建立 Azure VM](https://msdn.microsoft.com/library/azure/dn449661.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-123">[Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/azure/dn449661.aspx).</span></span>

-   <span data-ttu-id="7b3b5-124">請參閱[存取 Reporting Services WMI 提供者](access-the-reporting-services-wmi-provider.md)中的＜使用 PowerShell 存取 WMI 類別＞一節。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-124">See the section "Access the WMI classes using PowerShell" in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).</span></span>

-   <span data-ttu-id="7b3b5-125">[如何使用 PowerShell 管理 SSRS](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span><span class="sxs-lookup"><span data-stu-id="7b3b5-125">[How to Administer SSRS using PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span></span>

## <a name="rsexe-scripting-samples"></a><span data-ttu-id="7b3b5-126">RS.exe 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="7b3b5-126">RS.exe scripting samples</span></span>

-   <span data-ttu-id="7b3b5-127">[在報表伺服器之間遷移內容的範例 Reporting Services rs.exe 腳本](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-127">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>

-   <span data-ttu-id="7b3b5-128">如需其他指令碼、應用程式及延伸模組範例，請參閱 [SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="7b3b5-128">For additional script, application, and extension examples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b3b5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b3b5-129">See Also</span></span>
 <span data-ttu-id="7b3b5-130">[RS.exe 公用程式 &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [使用 rs.exe 公用程式和 Web 服務](script-with-the-rs-exe-utility-and-the-web-service.md)的[腳本部署和管理](script-deployment-and-administrative-tasks.md)工作腳本</span><span class="sxs-lookup"><span data-stu-id="7b3b5-130">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) [Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md)</span></span>


