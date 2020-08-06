---
title: 啟動與停止報表伺服器服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b751fd1a31830ffdc96cb296fa39d08e396c8c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595630"
---
# <a name="start-and-stop-the-report-server-service"></a><span data-ttu-id="226d2-102">啟動與停止 Report Server 服務</span><span class="sxs-lookup"><span data-stu-id="226d2-102">Start and Stop the Report Server Service</span></span>
  <span data-ttu-id="226d2-103">報表伺服器會實作成一項 Windows 服務，其中包含報表伺服器 Web 服務、報表管理員和背景處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="226d2-103">A report server is implemented as a Windows service that contains the Report Server Web service, Report Manager, and a background processing application.</span></span> <span data-ttu-id="226d2-104">如果您想要使用任何報表伺服器功能，就必須執行這項服務。</span><span class="sxs-lookup"><span data-stu-id="226d2-104">The service must be running if you want to use any report server functionality.</span></span> <span data-ttu-id="226d2-105">停止此服務會停止所有報表伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="226d2-105">Stopping the service stops all report server operations.</span></span>  
  
 <span data-ttu-id="226d2-106">當此服務停止時，原本在服務執行時會進行之排程報表和訂閱處理的要求都會加入至佇列。</span><span class="sxs-lookup"><span data-stu-id="226d2-106">While the service is stopped, requests for scheduled report and subscription processing that would have occurred had the service been running are added to the queue.</span></span> <span data-ttu-id="226d2-107">這是因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 所執行的作業會建立事件。</span><span class="sxs-lookup"><span data-stu-id="226d2-107">This is because jobs that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent create the events.</span></span> <span data-ttu-id="226d2-108">如果您想要在此服務關閉時避免作業積存，請考慮一併停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="226d2-108">If you want to avoid a backlog of operations while the service is off, consider stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as well.</span></span>  
  
 <span data-ttu-id="226d2-109">您可以使用各種工具來啟動或停止報表伺服器服務，包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 中提供的「服務」工具。</span><span class="sxs-lookup"><span data-stu-id="226d2-109">You can use a variety of tools to start or stop the Report Server service, including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, and the Services tool provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span>  
  
 <span data-ttu-id="226d2-110">如果您執行的不只是啟動或停止服務，例如變更服務帳戶，則必須使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具。</span><span class="sxs-lookup"><span data-stu-id="226d2-110">If you are doing more than starting or stopping the service, such as changing the service account, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="226d2-111">使用其他工具來變更服務帳戶可能會破壞您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="226d2-111">Using other tools to change the service account can break your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="226d2-112">如需詳細資訊，請參閱《 [設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="226d2-112">For more information, see [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="226d2-113">您無法暫停和繼續服務。</span><span class="sxs-lookup"><span data-stu-id="226d2-113">You cannot pause and resume the service.</span></span> <span data-ttu-id="226d2-114">沒有啟動參數。</span><span class="sxs-lookup"><span data-stu-id="226d2-114">There are no start parameters.</span></span> <span data-ttu-id="226d2-115">雖然沒有明確的相依性，但是如果您的報表伺服器支援任何訂閱或排程的報表作業，就必須執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="226d2-115">Although there are no explicit dependencies, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running if you support any subscriptions or scheduled report operations on the report server.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a><span data-ttu-id="226d2-116">使用 Reporting Services 組態工具來啟動或停止服務</span><span class="sxs-lookup"><span data-stu-id="226d2-116">To start or stop the service using the Reporting Services Configuration tool</span></span>  
  
1.  <span data-ttu-id="226d2-117">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並連接到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="226d2-117">Start [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server.</span></span>  
  
2.  <span data-ttu-id="226d2-118">在 [報表伺服器狀態] 頁面上，按一下 **[停止]** 或 **[啟動]**。</span><span class="sxs-lookup"><span data-stu-id="226d2-118">On the Report Server Status page, click **Stop** or **Start**.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a><span data-ttu-id="226d2-119">使用系統管理工具中的服務來啟動或停止服務</span><span class="sxs-lookup"><span data-stu-id="226d2-119">To start or stop the service using Services in Administrative Tools</span></span>  
  
-   <span data-ttu-id="226d2-120">在 [系統管理工具] 中開啟 [服務]、以滑鼠右鍵按一下 **[SQL Server Reporting Services (MSSQLSERVER)]**，然後按一下 **[停止]** 或 **[重新啟動]**。</span><span class="sxs-lookup"><span data-stu-id="226d2-120">In Administrative Tools, open Services, right-click **SQL Server Reporting Services (MSSQLSERVER)**, and click **Stop** or **Restart**.</span></span>  
  
 <span data-ttu-id="226d2-121">如果您執行多個執行個體，或者報表伺服器是以具名執行個體執行，請確認括號中的執行個體名稱是否對應於您要停止或重新啟動的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="226d2-121">If you are running multiple instance or if the report server is running as a named instance, verify that the instance name in parentheses corresponds to the report server instance you want to stop or restart.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a><span data-ttu-id="226d2-122">使用 SQL Server 組態管理員來啟動或停止服務</span><span class="sxs-lookup"><span data-stu-id="226d2-122">To start or stop the service using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="226d2-123">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="226d2-123">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
2.  <span data-ttu-id="226d2-124">選取 [SQL Server 服務]，並以滑鼠右鍵按一下 **[SQL Server Reporting Services]**，然後按一下 **[停止]** 或 **[重新啟動]**。</span><span class="sxs-lookup"><span data-stu-id="226d2-124">Select SQL Server Services, right-click **SQL Server Reporting Services**, and click **Stop** or **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226d2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="226d2-125">See Also</span></span>  
 [<span data-ttu-id="226d2-126">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="226d2-126">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
