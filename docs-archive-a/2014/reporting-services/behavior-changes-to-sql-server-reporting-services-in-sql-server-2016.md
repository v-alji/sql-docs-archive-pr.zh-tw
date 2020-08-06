---
title: SQL Server 2014 中 SQL Server Reporting Services 的行為變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 966447192c492a907f0b506ae21befd513b2fcfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593341"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a><span data-ttu-id="aa701-102">SQL Server 2014 中 SQL Server Reporting Services 的行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-102">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>
  <span data-ttu-id="aa701-103">本主題描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中的行為變更。</span><span class="sxs-lookup"><span data-stu-id="aa701-103">This topic describes behavior changes in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="aa701-104">行為變更會影響 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中功能的運作或互動方式 (相較於舊版的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="aa701-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="aa701-105">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="aa701-105">In this topic:</span></span>  
  
-   [<span data-ttu-id="aa701-106">SQL Server 2014 Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-106">SQL Server 2014 Reporting Services Behavior Changes</span></span>](#bkmk_sql14)  
  
-   [<span data-ttu-id="aa701-107">SQL Server 2012 Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-107">SQL Server 2012 Reporting Services Behavior Changes</span></span>](#bkmk_rc0)  
  
-   [<span data-ttu-id="aa701-108">SQL Server 2008 R2 Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-108">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a><span data-ttu-id="aa701-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="aa701-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]行為沒有任何變更。</span><span class="sxs-lookup"><span data-stu-id="aa701-110">There are no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] behavior changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a><span data-ttu-id="aa701-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="aa701-112">本節描述 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的行為變更。</span><span class="sxs-lookup"><span data-stu-id="aa701-112">This section describes behavior changes to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a><span data-ttu-id="aa701-113">檢視項目權限將不會下載共用資料集 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="aa701-113">View Items permission will not download Shared Datasets (SharePoint Mode)</span></span>  
 <span data-ttu-id="aa701-114">**新的行為：** 具有「視圖專案」 SharePoint 許可權的使用者無法再下載 Reporting Services 共用資料集的內容。</span><span class="sxs-lookup"><span data-stu-id="aa701-114">**New Behavior:** Users with the SharePoint permission of "View Items" can no longer download the contents of Reporting Services shared datasets.</span></span> <span data-ttu-id="aa701-115">這項行為變更現在與報表、資料來源和模型的「視圖專案」許可權一致。</span><span class="sxs-lookup"><span data-stu-id="aa701-115">This behavior change is now consistent with the "View Items" permissions for reports, data sources, and models.</span></span> <span data-ttu-id="aa701-116">具有「視圖專案」許可權的使用者可以查看和執行報表、資料來源和模型，但無法下載其內容。</span><span class="sxs-lookup"><span data-stu-id="aa701-116">Users with "View Items" permission can view and execute reports, data sources, and models but they cannot download their content.</span></span>  
  
 <span data-ttu-id="aa701-117">**先前的行為：** 具有「視圖專案」 SharePoint 許可權的使用者可以下載 Reporting Services 共用資料集的內容。</span><span class="sxs-lookup"><span data-stu-id="aa701-117">**Previous Behavior:** Users with the "View Items" SharePoint permission could download the contents of Reporting Services shared datasets.</span></span>  
  
 <span data-ttu-id="aa701-118">如需有關 SharePoint 權限等級的詳細資訊，請參閱＜ [使用者權限與權限等級](https://technet.microsoft.com/library/cc721640.aspx)＞</span><span class="sxs-lookup"><span data-stu-id="aa701-118">For more information on SharePoint permission levels, see [User permissions and permission levels](https://technet.microsoft.com/library/cc721640.aspx)</span></span>  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a><span data-ttu-id="aa701-119">報表伺服器追蹤記錄位於 SharePoint 模式的新位置 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="aa701-119">Report Server trace logs are in a new location for SharePoint mode (SharePoint Mode)</span></span>  
 <span data-ttu-id="aa701-120">**新的行為：** 若為以 SharePoint 模式安裝的報表伺服器，報表伺服器追蹤記錄將會在%Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\reportserver\logfiles 底下。</span><span class="sxs-lookup"><span data-stu-id="aa701-120">**New behavior:** For a report server installed in SharePoint mode, the report server trace logs will be under %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.</span></span>  
  
 <span data-ttu-id="aa701-121">**先前的行為：** 在類似下列的路徑下找到報表伺服器追蹤記錄檔：%Programfilesdir%\Microsoft SQL Server \\<RS_instance> \Reporting Services\LogFiles</span><span class="sxs-lookup"><span data-stu-id="aa701-121">**Previous Behavior:** Report Server trace logs were found under a path similar to the following:  %Programfilesdir%\Microsoft SQL Server\\<RS_instance>\Reporting Services\LogFiles</span></span>  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a><span data-ttu-id="aa701-122">不再支援 GetServerConfigInfo SOAP API (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="aa701-122">GetServerConfigInfo SOAP API is no longer supported (SharePoint Mode)</span></span>  
 <span data-ttu-id="aa701-123">**新的行為**：使用 PowerShell Cmdlet "Get-程式 get-sprsserviceapplicationservers"</span><span class="sxs-lookup"><span data-stu-id="aa701-123">**New behavior**: Use PowerShell cmdlet "Get-SPRSServiceApplicationServers"</span></span>  
  
 <span data-ttu-id="aa701-124">**先前的行為：** 客戶可以開發 SOAP 用戶端程式代碼，直接與 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 端點通訊，並 ( # A1 呼叫 GetReportServerConfigInfo。</span><span class="sxs-lookup"><span data-stu-id="aa701-124">**Previous Behavior:** Customers could develop SOAP client code to communicate directly with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] end point, and call GetReportServerConfigInfo().</span></span>  
  
### <a name="report-server-configuration-and-management-tools"></a><span data-ttu-id="aa701-125">報表伺服器組態和管理工具</span><span class="sxs-lookup"><span data-stu-id="aa701-125">Report Server Configuration and Management Tools</span></span>  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a><span data-ttu-id="aa701-126">組態管理員不用於 SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="aa701-126">Configuration Manager is not used for SharePoint Mode</span></span>  
 <span data-ttu-id="aa701-127">**新的行為** ： [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員不再支援 SharePoint 模式的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa701-127">**New behavior:** The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint Mode report servers.</span></span> <span data-ttu-id="aa701-128">您現在可以使用 SharePoint 管理中心完成 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 模式的組態設定，因此 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員不再支援 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="aa701-128">Configuration of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode can now be completed by using SharePoint Central administration and therefore [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint mode.</span></span> <span data-ttu-id="aa701-129">組態管理員現在僅用於原生模式的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa701-129">Configuration Manager is now only used for Native mode report servers.</span></span>  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a><span data-ttu-id="aa701-130">您無法將伺服器從一種模式變更為另一種模式</span><span class="sxs-lookup"><span data-stu-id="aa701-130">You cannot change the server from one mode to another</span></span>  
 <span data-ttu-id="aa701-131">**新的行為** ：您無法變更伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="aa701-131">**New behavior:** You cannot change server modes.</span></span> <span data-ttu-id="aa701-132">如果您以原生模式安裝報表伺服器，就無法將其變更或重新設定為 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="aa701-132">If you install a report server as Native mode you cannot change or re-configure it to be SharePoint mode.</span></span> <span data-ttu-id="aa701-133">如果您在 SharePoint 模式下安裝，可以將報表伺服器變更為原生模式。</span><span class="sxs-lookup"><span data-stu-id="aa701-133">If you install in SharePoint mode, you can change the report server to native mode.</span></span>  
  
 <span data-ttu-id="aa701-134">**先前的行為** ：客戶會在 SharePoint 模式下安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa701-134">**Previous Behavior:** Customer installs a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode.</span></span> <span data-ttu-id="aa701-135">如果客戶想要將報表伺服器切換到原生模式，可以開啟 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員切換到原生模式，方法是，建立新的原生模式資料庫，或連線至現有的原生模式資料庫。</span><span class="sxs-lookup"><span data-stu-id="aa701-135">If the customer wants to switch the report server to Native mode, they could open the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] configuration manager to switch to Native mode by either creating a new or connecting to an existing Native mode database.</span></span> <span data-ttu-id="aa701-136">客戶也可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 組態管理員從 SharePoint 模式切換到原生模式。</span><span class="sxs-lookup"><span data-stu-id="aa701-136">The customer could also use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager to switch from SharePoint mode to Native mode.</span></span>  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a><span data-ttu-id="aa701-137">SQL Server 2008 R2 Reporting Services 行為變更</span><span class="sxs-lookup"><span data-stu-id="aa701-137">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="aa701-138">本節描述中的行為變更 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aa701-138">This section describes behavior changes in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa701-139">因為 SQL Server 2008 R2 是 SQL Server 2008 的次要版本更新，所以建議您也檢閱 SQL Server 2008 章節中的內容。</span><span class="sxs-lookup"><span data-stu-id="aa701-139">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a><span data-ttu-id="aa701-140">Reporting Services WMI 提供者程式庫中的 SecureConnectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="aa701-140">SecureConnectionLevel Property in the Reporting Services WMI Provider Library</span></span>  
 <span data-ttu-id="aa701-141">在的 WMI 提供者程式庫中， [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **SecureConnectionLevel**屬性允許、、、的值， `0` `1` `2` `3` 並 `0` 指出任何 web 服務方法都不需要安全通訊端層 (SSL) ， `3` 表示所有 web 服務方法都需要 ssl，而 `1` 和則 `2` 指出需要 ssl 的 web 服務方法子集。</span><span class="sxs-lookup"><span data-stu-id="aa701-141">In the WMI provider library for [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the **SecureConnectionLevel** property allows values of `0`,`1`,`2`,`3`, with `0` indicating that Secure Socket Layer (SSL) is not required for any of the Web service methods, `3` indicating that SSL is required for all the Web service methods, and `1` and `2` indicate subsets of Web service methods that require SSL.</span></span> <span data-ttu-id="aa701-142">在中 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，這些值將只有兩個可能的意義：</span><span class="sxs-lookup"><span data-stu-id="aa701-142">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], these values will have only two possible meanings:</span></span>  
  
-   <span data-ttu-id="aa701-143">`0` 表示任何 Web 服務方法都不需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="aa701-143">`0` indicates SSL is not required for any of the Web service methods.</span></span>  
  
-   <span data-ttu-id="aa701-144">正整數表示所有 Web 服務方法都需要 SSL。</span><span class="sxs-lookup"><span data-stu-id="aa701-144">A positive integer indicates SSL is required for all the Web service methods.</span></span>  
  
 <span data-ttu-id="aa701-145">這項變更會影響報表伺服器回應 Web 服務呼叫的方式。</span><span class="sxs-lookup"><span data-stu-id="aa701-145">This change affects how the report server responds to Web service calls.</span></span> <span data-ttu-id="aa701-146">例如，如果 <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> **SecureConnectionLevel**設定為0，且中的所有方法都 <xref:ReportService2005.ReportingService2005> 設定為、或**SecureConnectionLevel** ，則現在會傳回任何內容 `1` `2` `3` 。</span><span class="sxs-lookup"><span data-stu-id="aa701-146">For example, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> now returns nothing if **SecureConnectionLevel** is set to 0 and all the methods in <xref:ReportService2005.ReportingService2005> if **SecureConnectionLevel** is set to `1`, `2`, or `3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa701-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa701-147">See Also</span></span>  
 <span data-ttu-id="aa701-148">[Reporting Services 的新 &#40;&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa701-148">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="aa701-149">[SQL Server 2014 中 SQL Server Reporting Services 已被取代的功能](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa701-149">[Deprecated Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span></span>  
 <span data-ttu-id="aa701-150">[SQL Server 2014 中 SQL Server Reporting Services 已停止的功能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aa701-150">[Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span></span>  
 [<span data-ttu-id="aa701-151">SQL Server 2014 中 SQL Server Reporting Services 的重大變更</span><span class="sxs-lookup"><span data-stu-id="aa701-151">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
