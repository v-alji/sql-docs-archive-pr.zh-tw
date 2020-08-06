---
title: '[網站設定] 頁面 (報表管理員) |Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75805a4e30293195b23cd5b75f1de3a01a1e76d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699280"
---
# <a name="site-settings-page-report-manager"></a><span data-ttu-id="16154-102">站台設定頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="16154-102">Site Settings Page (Report Manager)</span></span>
  <span data-ttu-id="16154-103">您可以使用 [站台設定] 頁面來變更應用程式標題、針對報表記錄限制和報表處理逾時值設定整個網站的預設值、管理系統層級角色指派，以及管理共用排程。</span><span class="sxs-lookup"><span data-stu-id="16154-103">Use the Site Settings page to change the application title, set server-wide defaults for report history limits and report processing timeout values, manage system-level role assignments, and manage shared schedules.</span></span> <span data-ttu-id="16154-104">您必須擁有「內容管理員」和「系統管理員」權限才能檢視此頁面。</span><span class="sxs-lookup"><span data-stu-id="16154-104">You must have Content Manager and System Administrator permissions to view this page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16154-105">並非所有 SQL Server 版本都提供下列功能：報表記錄、報表執行和共用排程。</span><span class="sxs-lookup"><span data-stu-id="16154-105">The following features are not available in every edition of SQL Server: report history, report execution, and shared schedules.</span></span> <span data-ttu-id="16154-106">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="16154-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="16154-107">導覽</span><span class="sxs-lookup"><span data-stu-id="16154-107">Navigation</span></span>  
 <span data-ttu-id="16154-108">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="16154-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-site-settings-page"></a><span data-ttu-id="16154-109">若要開啟站台設定頁面</span><span class="sxs-lookup"><span data-stu-id="16154-109">To open the Site Settings page</span></span>  
  
1.  <span data-ttu-id="16154-110">開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="16154-110">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="16154-111">在頁面的頂端，按一下 **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="16154-111">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="16154-112">這樣就會開啟該站台的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="16154-112">This opens the General Properties page of the site.</span></span>  
  
     <span data-ttu-id="16154-113">**注意：** 如果您在功能表中看不到 [**網站設定**] 選項，表示您沒有必要的許可權。如需詳細資訊，請參閱[設定原生模式報表伺服器以進行本機管理 &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)的「網站設定」一節。</span><span class="sxs-lookup"><span data-stu-id="16154-113">**Note:** If you do not see the **Site Settings** option in the menu, you do not have the required permissions, For more information see the "site settings" section of [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="16154-114">選項。</span><span class="sxs-lookup"><span data-stu-id="16154-114">Options</span></span>  
 <span data-ttu-id="16154-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="16154-115">**Name**</span></span>  
 <span data-ttu-id="16154-116">指定此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 報表管理員執行個體使用的標題。</span><span class="sxs-lookup"><span data-stu-id="16154-116">Specify the title to use for this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="16154-117">根據預設，標題為 " [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] "。</span><span class="sxs-lookup"><span data-stu-id="16154-117">By default, the title is "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".</span></span>  
  
 <span data-ttu-id="16154-118">**選取報表記錄的預設值**</span><span class="sxs-lookup"><span data-stu-id="16154-118">**Select the default settings for report history**</span></span>  
 <span data-ttu-id="16154-119">選取要保留之報表記錄副本數目的預設值。</span><span class="sxs-lookup"><span data-stu-id="16154-119">Select a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="16154-120">此預設值提供建立報表記錄限制的初始設定。</span><span class="sxs-lookup"><span data-stu-id="16154-120">The default value provides an initial setting that establishes report history limits.</span></span> <span data-ttu-id="16154-121">您可以在報表層級變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="16154-121">You can vary these settings at the report level.</span></span> <span data-ttu-id="16154-122">如需詳細資訊，請參閱[快照集選項屬性頁 &#40;報表管理員&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="16154-122">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="16154-123">如果稍後限制報表記錄，則當現有的報表記錄超過指定的限制時，報表伺服器會將現有的報表記錄縮減至低於新限制的量。</span><span class="sxs-lookup"><span data-stu-id="16154-123">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="16154-124">會先刪除最舊的報表快照集。</span><span class="sxs-lookup"><span data-stu-id="16154-124">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="16154-125">如果報表記錄為空白或在限制以下，則會加入新報表快照集。</span><span class="sxs-lookup"><span data-stu-id="16154-125">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="16154-126">如果達到限制，加入新報表快照集時會刪除最舊的快照集。</span><span class="sxs-lookup"><span data-stu-id="16154-126">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
 <span data-ttu-id="16154-127">**報表執行逾時**</span><span class="sxs-lookup"><span data-stu-id="16154-127">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="16154-128">指定在特定秒數之後報表處理是否逾時。</span><span class="sxs-lookup"><span data-stu-id="16154-128">Specify whether report processing times out after a certain number of seconds.</span></span>  
  
 <span data-ttu-id="16154-129">此值會套用至報表伺服器上的報表處理。</span><span class="sxs-lookup"><span data-stu-id="16154-129">This value applies to report processing on a report server.</span></span> <span data-ttu-id="16154-130">它不會影響提供報表資料的資料庫伺服器上的資料處理。</span><span class="sxs-lookup"><span data-stu-id="16154-130">It does not affect data processing on the database server that provides the data for your report.</span></span>  
  
 <span data-ttu-id="16154-131">報表處理計時器時鐘在選取報表時會開始，而當報表開啟時就會結束。</span><span class="sxs-lookup"><span data-stu-id="16154-131">The report processing timer clock begins when the report is selected and ends when the report opens.</span></span> <span data-ttu-id="16154-132">當您設定此值時，請指定足以完成資料處理和報表處理的時間。</span><span class="sxs-lookup"><span data-stu-id="16154-132">When you set this value, specify enough time to complete both data processing and report processing.</span></span>  
  
 <span data-ttu-id="16154-133">**自訂報表產生器啟動 URL**</span><span class="sxs-lookup"><span data-stu-id="16154-133">**Custom Report Builder launch URL**</span></span>  
 <span data-ttu-id="16154-134">當報表伺服器不使用預設的報表產生器 URL 時，指定自訂 URL。</span><span class="sxs-lookup"><span data-stu-id="16154-134">Specify a custom URL when the report server does not use the default Report Builder URL.</span></span> <span data-ttu-id="16154-135">這個設定是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="16154-135">This setting is optional.</span></span> <span data-ttu-id="16154-136">如果您沒有指定值，將會使用預設 URL，這樣會將報表產生器視為 ClickOnce 應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="16154-136">If you do not specify a value, the default URL will be used, which launches Report Builder as a ClickOnce application.</span></span> <span data-ttu-id="16154-137">預設的 URL 是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="16154-137">The default URL is one of the following:</span></span>  
  
 <span data-ttu-id="16154-138">**原生模式報表伺服器：** 在原生模式安裝中，預設 URL 的格式會是 HTTP:// \<*computername*> /reportserver/reportbuilder/ReportBuilder_3_0_0_0. 應用程式。</span><span class="sxs-lookup"><span data-stu-id="16154-138">**Native mode report server:** In a native mode installation, the default URL will take the form of http://\<*computername*>/reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.</span></span>  
  
 <span data-ttu-id="16154-139">SharePoint 整合模式：預設 URL 的格式會是 HTTP:// \<*SharePoint_site*> /_vti_bin/reportbuilder/ReportBuilder_3_0_0_0. 應用程式）。</span><span class="sxs-lookup"><span data-stu-id="16154-139">SharePoint integrated mode: The default URL will take the form of http://\<*SharePoint_site*>/_vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application."</span></span>  
  
 <span data-ttu-id="16154-140">**套用**</span><span class="sxs-lookup"><span data-stu-id="16154-140">**Apply**</span></span>  
 <span data-ttu-id="16154-141">按一下即可儲存您對報表伺服器所做的變更。</span><span class="sxs-lookup"><span data-stu-id="16154-141">Click to save your changes to the report server.</span></span>  
  
 <span data-ttu-id="16154-142">**安全性**</span><span class="sxs-lookup"><span data-stu-id="16154-142">**Security**</span></span>  
 <span data-ttu-id="16154-143">按一下這個連結即可開啟 [系統角色指派] 頁面，在此頁面上您可以將使用者和群組帳戶指派至預先定義的系統角色。</span><span class="sxs-lookup"><span data-stu-id="16154-143">Click this link to open the System Role Assignments page, on which you can assign user and group accounts to predefined system roles.</span></span>  
  
 <span data-ttu-id="16154-144">**排程**</span><span class="sxs-lookup"><span data-stu-id="16154-144">**Schedules**</span></span>  
 <span data-ttu-id="16154-145">按一下此連結即可開啟 [排程] 頁面，在此頁面上您可以預先定義可供使用者為其報表和訂閱選取的共用排程。</span><span class="sxs-lookup"><span data-stu-id="16154-145">Click this link to open the Schedules page, on which you can predefine shared schedules that users can select for their reports and subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16154-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16154-146">See Also</span></span>  
 <span data-ttu-id="16154-147">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="16154-147">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="16154-148">[在原生模式報表伺服器上授與權限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="16154-148">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="16154-149">[預先定義的角色](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="16154-149">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="16154-150">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="16154-150">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
