---
title: 安全性 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ed38291a-6afe-449f-9f32-3ae04502bd6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d744d00068ebd51148aa71ccf5b9ad170ed2f077
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707194"
---
# <a name="security-report-builder"></a><span data-ttu-id="86a0b-102">安全性 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="86a0b-102">Security (Report Builder)</span></span>
  <span data-ttu-id="86a0b-103">報表產生器是一種報表撰寫用戶端應用程式，專為搭配報表伺服器使用而設計 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="86a0b-103">Report Builder is a report authoring client application that is designed to work with a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="86a0b-104">該報表伺服器可以設定為以獨立伺服器的原生模式運作，或者以 SharePoint 整合模式運作以支援 SharePoint 網站上的報表。</span><span class="sxs-lookup"><span data-stu-id="86a0b-104">The report server can be configured to work in native mode as a stand-alone server or in SharePoint integrated mode to support reports on a SharePoint site.</span></span>  
  
 <span data-ttu-id="86a0b-105">在報表產生器中，您可以撰寫報表、共用的資料集以及可重複使用的報表組件。</span><span class="sxs-lookup"><span data-stu-id="86a0b-105">In Report Builder, you can author reports, shared datasets, and reusable report parts.</span></span> <span data-ttu-id="86a0b-106">從報表伺服器或 SharePoint 網站上，您可以編輯報表並且加入共用的資料來源、共用的資料集以及共用的報表組件。</span><span class="sxs-lookup"><span data-stu-id="86a0b-106">From a report server or SharePoint site, you can edit reports and add shared data sources, shared datasets, and shared report parts.</span></span>  
  
 <span data-ttu-id="86a0b-107">在撰寫、發行並且使用報表與報表相關的項目之前，您必須先了解與下列層面相關的安全性功能：</span><span class="sxs-lookup"><span data-stu-id="86a0b-107">To author, publish, and use reports and report-related items, you should understand how security features relate to the following areas:</span></span>  
  
-   <span data-ttu-id="86a0b-108">**您在其中發行報表的報表伺服器或 SharePoint 網站** ：這些功能是由報表伺服器管理員或 SharePoint 網站管理員所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-108">**The report server or SharePoint site where you publish reports** These features are managed by the report server administrator or SharePoint site administrator.</span></span>  
  
-   <span data-ttu-id="86a0b-109">**已發行的報表與報表相關的項目** ：報表相關的項目包括內嵌與共用的資料來源，以及它們的認證、共用的資料集、參數、報表組件與報表模型。</span><span class="sxs-lookup"><span data-stu-id="86a0b-109">**Published reports and report-related items** Report-related items include embedded and shared data sources and their credentials, shared datasets, parameters, report parts, and report models.</span></span> <span data-ttu-id="86a0b-110">套用到這些項目的安全性功能是由報表作者所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-110">Security features that apply to these items are managed by the report author.</span></span> <span data-ttu-id="86a0b-111">報表伺服器管理員或 SharePoint 網站管理員必須授與報表作者適當的權限，報表作者才能夠發行並共用項目。</span><span class="sxs-lookup"><span data-stu-id="86a0b-111">The report author must be granted sufficient permissions by the report server administrator or SharePoint site administrator to publish and share the items.</span></span>  
  
-   <span data-ttu-id="86a0b-112">**報表所使用的外部資料來源** ：這些功能是由外部資料來源的擁有者所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-112">**External data sources that are used by a report** These features are managed by the owner of the external data source.</span></span>  
  
-   <span data-ttu-id="86a0b-113">**以外部資料來源為基礎的報表模型** ：這些功能由模型設計人員所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-113">**Report models that are based on external data sources** These features are managed by the model designer.</span></span>  
  
-   <span data-ttu-id="86a0b-114">**互動式報表功能，例如參數** ：這些功能是由報表作者所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-114">**Interactive report features such as parameters** These features are managed by the report author.</span></span>  
  
 <span data-ttu-id="86a0b-115">請檢閱本主題中的資訊，協助您更深入了解如何使用安全性功能，進一步協助管理及維護報表與報表相關項目的安全性。</span><span class="sxs-lookup"><span data-stu-id="86a0b-115">Review the information in this topic to better understand how to use security features to help manage and secure reports and report-related items.</span></span>  
  
##  <a name="understanding-security-for-report-servers"></a><a name="ReportServers"></a> <span data-ttu-id="86a0b-116">了解報表伺服器的安全性</span><span class="sxs-lookup"><span data-stu-id="86a0b-116">Understanding Security for Report Servers</span></span>  
 <span data-ttu-id="86a0b-117">發行報表與檢視報表是需要有適當權限才能進行的作業。</span><span class="sxs-lookup"><span data-stu-id="86a0b-117">Publishing reports and viewing reports are privileged operations.</span></span> <span data-ttu-id="86a0b-118">報表伺服器管理員會授與使用權限，確保只有獲得授權的使用者才可以在下列其中一種報表伺服器上發行並檢視報表：</span><span class="sxs-lookup"><span data-stu-id="86a0b-118">A report server administrator grants permissions to ensure that only authorized users can publish and view reports on one of the following types of report servers:</span></span>  
  
-   <span data-ttu-id="86a0b-119">以原生模式設定的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="86a0b-119">Report server configured in native mode</span></span>  
  
     <span data-ttu-id="86a0b-120">若要連接或瀏覽至報表伺服器，您必須具有有效的 URL 與存取伺服器的適當權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-120">To connect to or browse to a report server, you must have a valid URL and have sufficient permissions to access the server.</span></span>  
  
     <span data-ttu-id="86a0b-121">若要在報表伺服器上檢視或發行項目，套用到報表相關項目與作業的多組使用權限會根據角色分組。</span><span class="sxs-lookup"><span data-stu-id="86a0b-121">To view or publish items on a report server, sets of permissions that apply to report-related items and operations are organized into roles.</span></span> <span data-ttu-id="86a0b-122">報表伺服器管理員會將您指派為一個或多個角色。</span><span class="sxs-lookup"><span data-stu-id="86a0b-122">A report server administrator assigns you to one or more roles.</span></span> <span data-ttu-id="86a0b-123">例外，預先定義的角色 [瀏覽者] 可以讓您檢視報表、資料夾、模型與資源。</span><span class="sxs-lookup"><span data-stu-id="86a0b-123">For example, the predefined role Browser enables you to view reports, folders, models, and resources.</span></span>  
  
     <span data-ttu-id="86a0b-124">如果您無法連接或瀏覽至報表伺服器，請連絡報表伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="86a0b-124">If you cannot connect to or browse to a report server, contact the report server administrator.</span></span> <span data-ttu-id="86a0b-125">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書》](https://go.microsoft.com/fwlink/?linkid=121312) 中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文件集的 [Reporting Services 安全性與保護](../security/reporting-services-security-and-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-125">For more information, see [Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
-   <span data-ttu-id="86a0b-126">以 SharePoint 整合模式設定的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="86a0b-126">Report server configured in SharePoint integrated mode</span></span>  
  
     <span data-ttu-id="86a0b-127">若要連接至與報表伺服器整合的 SharePoint 網站，您必須具有有效之 SharePoint 網站或子網站的 URL 以及存取該報表伺服器的適當權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-127">To connect to a SharePoint site that is integrated with a report server, you must have a valid URL to the SharePoint site or subsite and have sufficient permissions to access it.</span></span>  
  
     <span data-ttu-id="86a0b-128">用於存取報表相關項目和作業的權限是透過 SharePoint 安全性原則所授與，這些原則會將使用者或群組帳戶對應至權限等級 (相對於項目)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-128">Permission to access report-related items and operations is granted through SharePoint security policies that map a user or group account with a permission level, relative to an item.</span></span>  
  
     <span data-ttu-id="86a0b-129">如果您無法連接或瀏覽到 SharePoint 網站或子站台，請連絡 SharePoint 網站管理員。</span><span class="sxs-lookup"><span data-stu-id="86a0b-129">If you cannot connect to or browse to a SharePoint site or subsite, contact the SharePoint site administrator.</span></span>  
  
=
  
##  <a name="understanding-security-for-published-reports-and-report-related-items"></a><a name="Reports"></a><span data-ttu-id="86a0b-130">瞭解已發行報表和報表相關專案的安全性</span><span class="sxs-lookup"><span data-stu-id="86a0b-130">Understanding Security for Published Reports and Report-related Items</span></span>  
 <span data-ttu-id="86a0b-131">報表與報表相關項目的安全性是由報表伺服器管理員所管理。</span><span class="sxs-lookup"><span data-stu-id="86a0b-131">Security for reports and report-related items is managed by the report server administrator.</span></span> <span data-ttu-id="86a0b-132">報表相關的項目包括內嵌與共用的資料來源，包括了認證、共用的資料集、參數、報表組件與模型。</span><span class="sxs-lookup"><span data-stu-id="86a0b-132">Report-related items include embedded and shared data sources including credentials, shared datasets, parameters, report parts, and models.</span></span>  
  
 <span data-ttu-id="86a0b-133">在報表伺服器或 SharePoint 網站上，報表與報表相關項目及作業的安全性為獨立的。</span><span class="sxs-lookup"><span data-stu-id="86a0b-133">On a report server or SharePoint site, reports and report-related items and operations are independently securable.</span></span> <span data-ttu-id="86a0b-134">用於存取項目和作業的權限是透過安全性原則所授與，這些原則會將使用者或群組帳戶對應至權限等級 (相對於項目)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-134">Permission to access items and operations is granted through security policies that map a user or group account with a permission level, relative to an item.</span></span> <span data-ttu-id="86a0b-135">為了簡化維護大量原則的複雜性與成本，容器 (例如資料夾) 上的使用權限會由容器中的項目繼承。</span><span class="sxs-lookup"><span data-stu-id="86a0b-135">To reduce the complexity and overhead of maintaining a large number of policies, permissions on a container, such as a folder, are inherited by items in the container.</span></span> <span data-ttu-id="86a0b-136">例如，如果使用者對某一資料夾具有特定的 [檢視報表] 權限，那麼該使用者對於資料夾中的項目也具有 [檢視報表] 權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-136">For example, if a user has the specific View Reports permission on a folder, they have View Reports permission on the items in the folder.</span></span>  
  
 <span data-ttu-id="86a0b-137">可以透過使用項目層級安全式的方式，覆寫項目或資料夾上的權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-137">Permissions can be overridden on items or folders by using item level security.</span></span> <span data-ttu-id="86a0b-138">套用項目層級安全性後，來自父容器的權限繼承將不再適用於該項目。</span><span class="sxs-lookup"><span data-stu-id="86a0b-138">When item-level security is applied, permission inheritance from the parent container no longer applies to the item.</span></span> <span data-ttu-id="86a0b-139">如果對資料夾套用項目層級安全性，則巢狀資料夾會繼承相同的權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-139">If item-level security is applied to a folder, nested folders inherit the same permissions.</span></span>  
  
 <span data-ttu-id="86a0b-140">如果您無法瀏覽到或找到其他使用者已為您發行的項目，可能表示您對該項目或資料夾尚未具有適當的權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-140">If you are not able to browse to and find items that someone else has published for you, you might have a permissions issue on the item or on the folder.</span></span>  
  
 <span data-ttu-id="86a0b-141">若要讓其他使用者瀏覽到並且找到您已發行要共用的項目，您必須請報表伺服器管理員設定資料夾組織，以便為您的使用者提供存取權限。</span><span class="sxs-lookup"><span data-stu-id="86a0b-141">To enable others to browse to and find items that you published to be shared, you must work with the report server administrator to set up a folder organization that provides access to your users.</span></span> <span data-ttu-id="86a0b-142">撰寫報表並且執行已發行的報表時，必須能夠使用 Access。</span><span class="sxs-lookup"><span data-stu-id="86a0b-142">Access must be available for authoring reports and for running published reports.</span></span>  
  
 <span data-ttu-id="86a0b-143">如需詳細資訊，請參閱《 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span><span class="sxs-lookup"><span data-stu-id="86a0b-143">For more information, see the following topics in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span></span>  
  
-   [<span data-ttu-id="86a0b-144">角色與權限 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="86a0b-144">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
-   [<span data-ttu-id="86a0b-145">管理共用資料集</span><span class="sxs-lookup"><span data-stu-id="86a0b-145">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
### <a name="update-notifications-for-report-parts"></a><span data-ttu-id="86a0b-146">報表組件更新通知</span><span class="sxs-lookup"><span data-stu-id="86a0b-146">Update Notifications for Report Parts</span></span>  
 <span data-ttu-id="86a0b-147">報表組件會發行到報表伺服器，讓其他使用者可以共用這些組件。</span><span class="sxs-lookup"><span data-stu-id="86a0b-147">Report parts are published to a report server so that others can share them.</span></span> <span data-ttu-id="86a0b-148">根據預設，您可以指定要發行報表組件的目標位置。</span><span class="sxs-lookup"><span data-stu-id="86a0b-148">By design, you specify the location to publish report parts to.</span></span>  
  
 <span data-ttu-id="86a0b-149">在報表中加入報表組件的使用者可以啟用更新功能。</span><span class="sxs-lookup"><span data-stu-id="86a0b-149">Users who include report parts in their reports can enable the update feature.</span></span> <span data-ttu-id="86a0b-150">啟用這項功能時，使用者會在報表伺服器上的報表組件發生變更時，收到通知。</span><span class="sxs-lookup"><span data-stu-id="86a0b-150">When this feature is enabled, users receive notifications when report parts change on the report server.</span></span>  
  
 <span data-ttu-id="86a0b-151">如果報表組件已經從原來的位置移動，那麼更新通知會包含報表組件目前的位置以及先前的位置。</span><span class="sxs-lookup"><span data-stu-id="86a0b-151">If report parts are moved from the original location, the update notice includes both the current location and the previous location of the report part.</span></span> <span data-ttu-id="86a0b-152">只接受來自受信任位置的更新。</span><span class="sxs-lookup"><span data-stu-id="86a0b-152">Accept updates only from trusted locations.</span></span>  
  
 <span data-ttu-id="86a0b-153">如需詳細資訊，請參閱 [報表組件 &#40;報表產生器及 SSRS&#41;](../report-parts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-153">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
=  
  
##  <a name="understanding-security-for-report-data-and-external-data-sources"></a><a name="Data"></a> <span data-ttu-id="86a0b-154">了解報表資料與外部資料來源的安全性</span><span class="sxs-lookup"><span data-stu-id="86a0b-154">Understanding Security for Report Data and External Data Sources</span></span>  
 <span data-ttu-id="86a0b-155">若要存取報表中每一個外部資料來源的資料，您可以建立內嵌資料來源或是將加入報表中共用資料來源或共用資料集的參考。</span><span class="sxs-lookup"><span data-stu-id="86a0b-155">To access data from each external data source in a report, you create an embedded data source or add a reference to a shared data source or shared dataset in your report.</span></span>  
  
 <span data-ttu-id="86a0b-156">針對每一個外部資料來源，您必須提供存取該來源及其底層資料的適當認證。</span><span class="sxs-lookup"><span data-stu-id="86a0b-156">For each external data source, you must supply credentials that are sufficient to access the source and the underlying data.</span></span> <span data-ttu-id="86a0b-157">資料來源擁有者會指定提供存取的認證類型。</span><span class="sxs-lookup"><span data-stu-id="86a0b-157">The data source owner specifies the type of credentials that provides this access.</span></span>  
  
 <span data-ttu-id="86a0b-158">認證不會儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="86a0b-158">Credentials are not saved in the report definition.</span></span> <span data-ttu-id="86a0b-159">這些認證會另外進行管理，有別與報表伺服器或 SharePoint 以及報表撰寫用戶端上的報表。</span><span class="sxs-lookup"><span data-stu-id="86a0b-159">They are managed independently from the report on the report server or SharePoint site and on the report authoring client.</span></span>  
  
 <span data-ttu-id="86a0b-160">在報表設計階段，認證會用於執行資料集查詢和預覽報表。</span><span class="sxs-lookup"><span data-stu-id="86a0b-160">At report design time, credentials are used to run dataset queries and preview the report.</span></span> <span data-ttu-id="86a0b-161">在執行階段，認證會用於執行報表與快取查詢結果。</span><span class="sxs-lookup"><span data-stu-id="86a0b-161">At run time, credentials are used to run the report and cache query results.</span></span> <span data-ttu-id="86a0b-162">您也可以獨立地快取共用資料集查詢結果。</span><span class="sxs-lookup"><span data-stu-id="86a0b-162">You can also cache shared dataset query results independently.</span></span> <span data-ttu-id="86a0b-163">設計階段與執行階段使用的認證可能會不同。</span><span class="sxs-lookup"><span data-stu-id="86a0b-163">Design time and run time credentials might differ.</span></span> <span data-ttu-id="86a0b-164">如需詳細資訊，請參閱 [在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-164">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="86a0b-165">如需維護資料安全的詳細資訊，請參閱《 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span><span class="sxs-lookup"><span data-stu-id="86a0b-165">For more information about securing data, see the following topic in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span></span>  
  
-   [<span data-ttu-id="86a0b-166">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="86a0b-166">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 <span data-ttu-id="86a0b-167">如需資料來源的詳細資訊，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="86a0b-167">For more information about data sources, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
=
  
##  <a name="understanding-models-and-security-filters"></a><a name="Models"></a> <span data-ttu-id="86a0b-168">了解模型與安全性篩選</span><span class="sxs-lookup"><span data-stu-id="86a0b-168">Understanding Models and Security Filters</span></span>  
 <span data-ttu-id="86a0b-169">當資料擷取自以外部資料為基礎的報表模型時，您可以在模型中套用安全性篩選。這是維護資料安全的好方法，因為如此一來，每一位執行報表的使用者都只能看到他們有權限讀取的內容。</span><span class="sxs-lookup"><span data-stu-id="86a0b-169">When data is retrieved from a report model that is based on external data, you can apply security filters in the model  This is a good way to secure data so that each user who runs a report can see only the data that they have permissions to.</span></span>  
  
 <span data-ttu-id="86a0b-170">報表參數不能用於資料列層級安全性，也無法防止使用者或使用者群組查看特定的資料列。</span><span class="sxs-lookup"><span data-stu-id="86a0b-170">Report parameters are not used for row-level security; they do not prevent users or groups of users from seeing specific rows of data.</span></span> <span data-ttu-id="86a0b-171">若要為報表內所顯示的資料套用安全性，您需要使用安全性篩選或模型項目安全性。</span><span class="sxs-lookup"><span data-stu-id="86a0b-171">To apply security to the data displayed within a report, you must use security filters or model item security.</span></span>  
  
=
  
##  <a name="understanding-security-for-report-authoring-for-interactive-features"></a><a name="Interactive"></a> <span data-ttu-id="86a0b-172">了解撰寫具有互動式功能之報表的安全性</span><span class="sxs-lookup"><span data-stu-id="86a0b-172">Understanding Security for Report Authoring for Interactive Features</span></span>  
 <span data-ttu-id="86a0b-173">報表經常會使用參數，讓使用者可以互動式地自訂他們的報表檢視。</span><span class="sxs-lookup"><span data-stu-id="86a0b-173">Reports frequently use parameters to enable a user to interactively customize their view of a report.</span></span> <span data-ttu-id="86a0b-174">請採用下列秘訣協助設計出遵循優良作法的報表：</span><span class="sxs-lookup"><span data-stu-id="86a0b-174">Use the following tips to help design reports that follow good practices:</span></span>  
  
-   <span data-ttu-id="86a0b-175">除非您會提供有效的值，否則請不要使用依據查詢參數以及屬於 **[文字]** 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="86a0b-175">Do not use parameters that are based on query parameters and that are type **Text** unless you provide valid values.</span></span> <span data-ttu-id="86a0b-176">可用的值清單有助於使用者只選擇有效的值。</span><span class="sxs-lookup"><span data-stu-id="86a0b-176">An available values list helps a user choose only valid values.</span></span> <span data-ttu-id="86a0b-177">如果沒有有效的值清單，則您將無法限制使用者可以輸入的值。</span><span class="sxs-lookup"><span data-stu-id="86a0b-177">Without an available values list, you cannot restrict which values a user can enter.</span></span>  
  
-   <span data-ttu-id="86a0b-178">請不要使用全域 [&UserID] 來維護私人資料的安全性。</span><span class="sxs-lookup"><span data-stu-id="86a0b-178">Do not use the global [&UserID] to secure private data.</span></span> <span data-ttu-id="86a0b-179">這個值做為報表參數時，可以利用 URL 存取語法在報表 URL 中指定它。</span><span class="sxs-lookup"><span data-stu-id="86a0b-179">As a report parameter, this value can be specified in a report URL by using URL access syntax.</span></span> <span data-ttu-id="86a0b-180">在共用資料集的運算式中使用這個值，會讓資料集無法被快取。</span><span class="sxs-lookup"><span data-stu-id="86a0b-180">Using this value in an expression in a shared dataset prevents the dataset from being cached.</span></span> <span data-ttu-id="86a0b-181">如需詳細資訊，請參閱《 [URL Access Parameter Reference](../url-access-parameter-reference.md) 線上叢書》 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="86a0b-181">For more information, see [URL Access Parameter Reference](../url-access-parameter-reference.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="86a0b-182">項目發行到報表伺服器後，報表伺服器管理員可以指定以角色為基礎的安全性或資料夾與項目層級安全性，藉此維護這些項目的安全。</span><span class="sxs-lookup"><span data-stu-id="86a0b-182">After items are published to a report server, the report server administrator can help secure them by assigning role-based security or folder and item level security.</span></span> <span data-ttu-id="86a0b-183">如需詳細資訊，請參閱《 [Secure Reports and Resources](../security/secure-reports-and-resources.md) 線上叢書》 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="86a0b-183">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="86a0b-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86a0b-184">See Also</span></span>  
 <span data-ttu-id="86a0b-185">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="86a0b-185">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="86a0b-186">報表參數 &#40;報表產生器和報表設計師&#41;</span><span class="sxs-lookup"><span data-stu-id="86a0b-186">Report Parameters &#40;Report Builder and Report Designer&#41;</span></span>](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
  
