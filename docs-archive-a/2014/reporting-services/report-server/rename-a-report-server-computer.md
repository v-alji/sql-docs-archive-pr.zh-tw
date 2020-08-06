---
title: 重新命名報表伺服器電腦 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe8f699c17f9e5f1e11406ac6e5c161488767ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606635"
---
# <a name="rename-a-report-server-computer"></a><span data-ttu-id="70b01-102">重新命名報表伺服器電腦</span><span class="sxs-lookup"><span data-stu-id="70b01-102">Rename a Report Server Computer</span></span>
  <span data-ttu-id="70b01-103">重新命名電腦會使 Web 伺服器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (如果它在同一台電腦上) 發生對應的名稱變更。</span><span class="sxs-lookup"><span data-stu-id="70b01-103">Renaming a computer causes a corresponding name change for the Web server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (if it is on the same computer).</span></span> <span data-ttu-id="70b01-104">在某些情況下，當電腦名稱變更後，可能就無法存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70b01-104">In some cases, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] may not be accessible after a computer name change.</span></span> <span data-ttu-id="70b01-105">電腦名稱變更之後，您可以利用本主題提供的步驟來重新設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b01-105">Use the steps provided in this topic to reconfigure a report server after a computer name change.</span></span>  
  
## <a name="renaming-a-sql-server-database-engine"></a><span data-ttu-id="70b01-106">重新命名 SQL Server Database Engine</span><span class="sxs-lookup"><span data-stu-id="70b01-106">Renaming a SQL Server Database Engine</span></span>  
 <span data-ttu-id="70b01-107">如果您要重新命名執行報表伺服器資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="70b01-107">If you rename the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance that runs the report server database, do the following:</span></span>  
  
1.  <span data-ttu-id="70b01-108">啟動 Reporting Services 組態工具，然後連接到使用重新命名的伺服器中報表伺服器資料庫的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b01-108">Start the Reporting Services Configuration tool and connect to the report server that uses the report server database on the renamed server.</span></span>  
  
2.  <span data-ttu-id="70b01-109">開啟 [資料庫安裝] 頁面。</span><span class="sxs-lookup"><span data-stu-id="70b01-109">Open the Database Setup page.</span></span>  
  
3.  <span data-ttu-id="70b01-110">在 **[伺服器名稱]** 中，輸入或選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名稱，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="70b01-110">In **Server Name**, type or select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] name, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="70b01-111">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="70b01-111">Click **Apply**.</span></span>  
  
 <span data-ttu-id="70b01-112">如果報表伺服器正使用本機 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，您可以利用 *(local)* 或 *(local)\instancename* 來指定伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b01-112">If the report server is using a local [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you can use *(local)* or *(local)\instancename* to specify the server.</span></span> <span data-ttu-id="70b01-113">如果您利用 *(local)* 來參考伺服器，您可以重新命名伺服器，如此一來，連接就可以繼續運作。</span><span class="sxs-lookup"><span data-stu-id="70b01-113">If you use *(local)* to refer to the server, you can rename the server and the connections will continue to work.</span></span> <span data-ttu-id="70b01-114">如果您是使用遠端伺服器，或者 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 是利用伺服器名稱來設定的，則每當伺服器名稱變更時，您都必須更新資料庫連接資訊。</span><span class="sxs-lookup"><span data-stu-id="70b01-114">If you are using a remote server, or if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is configured using the server name, you must update the database connection information whenever the server name is changed.</span></span>  
  
## <a name="renaming-a-report-server-computer"></a><span data-ttu-id="70b01-115">重新命名報表伺服器電腦</span><span class="sxs-lookup"><span data-stu-id="70b01-115">Renaming a Report Server Computer</span></span>  
 <span data-ttu-id="70b01-116">如果您要重新命名執行報表伺服器的電腦，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="70b01-116">If you rename a computer that runs a report server, do the following:</span></span>  
  
1.  <span data-ttu-id="70b01-117">在文字編輯器中開啟**RSReportServer.config** ，並修改 `UrlRoot` 設定以反映新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="70b01-117">Open **RSReportServer.config** in a text editor and modify the `UrlRoot` setting to reflect the new server name.</span></span> <span data-ttu-id="70b01-118">傳遞延伸模組利用 `UrlRoot` 設定來撰寫用於存取儲存在報表伺服器上之項目的 URL。</span><span class="sxs-lookup"><span data-stu-id="70b01-118">The `UrlRoot` setting is used by delivery extensions to compose the URL used to access items stored on the report server.</span></span> <span data-ttu-id="70b01-119">若要變更報表伺服器 URL 位址，您必須更新 `UrlRoot` 設定，讓訂閱能夠如預期般繼續傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="70b01-119">Changing the report server URL address requires that you update the `UrlRoot` setting so that subscriptions continue to deliver reports as expected.</span></span>  
  
2.  <span data-ttu-id="70b01-120">在相同的檔案中，如果已設定名稱，請修改 `ReportServerUrl` 設定來反映新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="70b01-120">In the same file, if it is set, modify the `ReportServerUrl` setting to reflect the new server name.</span></span> <span data-ttu-id="70b01-121">請注意，並非每一種安裝都使用此設定。</span><span class="sxs-lookup"><span data-stu-id="70b01-121">Note that this setting is not used in every installation.</span></span> <span data-ttu-id="70b01-122">如果它是空的，請不要執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="70b01-122">If it is empty, do nothing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70b01-123">如果您在企業網路上使用 Windows 網際網路命名服務 (WINS)，報表伺服器和報表管理員可能還可以在先前的名稱下繼續使用一段時間。</span><span class="sxs-lookup"><span data-stu-id="70b01-123">If you are using Windows Internet Naming Service (WINS) on your corporate network, the report server and Report Manager may continue to be available under the previous name for a period of time.</span></span> <span data-ttu-id="70b01-124">WINS 會將 IP 位址對應到它所提供服務的每台電腦。</span><span class="sxs-lookup"><span data-stu-id="70b01-124">WINS maps an IP address to each computer it services.</span></span> <span data-ttu-id="70b01-125">WINS 為重新命名的電腦重新整理 IP 位址之後，就無法再利用舊的電腦名稱來存取報表伺服器或報表管理員。</span><span class="sxs-lookup"><span data-stu-id="70b01-125">After WINS refreshes the IP address for the renamed computer, the old computer name can no longer be used to access a report server or Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b01-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b01-126">See Also</span></span>  
 <span data-ttu-id="70b01-127">[Rsreportserver.config 設定檔](rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="70b01-127">[RSReportServer Configuration File](rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="70b01-128">[Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="70b01-128">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="70b01-129">[Reporting Services 報表伺服器 &#40;原生模式&#41;](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="70b01-129">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="70b01-130">[啟動與停止 Report Server 服務](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="70b01-130">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="70b01-131">rsconfig 公用程式 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="70b01-131">rsconfig Utility &#40;SSRS&#41;</span></span>](../tools/rsconfig-utility-ssrs.md)  
  
  
