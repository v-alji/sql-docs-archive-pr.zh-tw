---
title: 選取資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688477"
---
# <a name="select-the-data-source"></a><span data-ttu-id="c469b-102">選取資料來源</span><span class="sxs-lookup"><span data-stu-id="c469b-102">Select the Data Source</span></span>
  <span data-ttu-id="c469b-103">使用報表精靈的這個頁面，即可定義報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c469b-103">Use this page of the Report Wizard to define a data source for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c469b-104">選項</span><span class="sxs-lookup"><span data-stu-id="c469b-104">Options</span></span>  
 <span data-ttu-id="c469b-105">**共用資料來源**</span><span class="sxs-lookup"><span data-stu-id="c469b-105">**Shared data source**</span></span>  
 <span data-ttu-id="c469b-106">選取 [共用資料來源]\*\*\*\*，即可使用預先定義的共用資料來源，且其已擁有您想要使用的資料來源連接資訊。</span><span class="sxs-lookup"><span data-stu-id="c469b-106">Select **Shared Data Source** to use a predefined shared data source that already has the data source connection information you want to use.</span></span> <span data-ttu-id="c469b-107">此清單包含專案中所包含的所有共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="c469b-107">The list contains all shared data sources that are included in the project.</span></span>  
  
 <span data-ttu-id="c469b-108">**新增資料來源**</span><span class="sxs-lookup"><span data-stu-id="c469b-108">**New data source**</span></span>  
 <span data-ttu-id="c469b-109">選取 [新增資料來源]\*\*\*\*，即可定義新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c469b-109">Select **New data source** to define a new data source.</span></span> <span data-ttu-id="c469b-110">資料來源資訊只會用於目前的報表。</span><span class="sxs-lookup"><span data-stu-id="c469b-110">The data source information will be used only with the current report.</span></span>  
  
 <span data-ttu-id="c469b-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c469b-111">**Name**</span></span>  
 <span data-ttu-id="c469b-112">輸入資料來源之連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="c469b-112">Type a name for the connection to the data source.</span></span> <span data-ttu-id="c469b-113">資料來源名稱在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c469b-113">The data source name must be unique within the report.</span></span>  
  
 <span data-ttu-id="c469b-114">**型別**</span><span class="sxs-lookup"><span data-stu-id="c469b-114">**Type**</span></span>  
 <span data-ttu-id="c469b-115">選取您要使用的資料來源類型 (例如，如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫，請選擇 [) ] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c469b-115">Select the type of data source you are using (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, choose [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).</span></span>  
  
 <span data-ttu-id="c469b-116">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="c469b-116">**Connection string**</span></span>  
 <span data-ttu-id="c469b-117">輸入資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c469b-117">Type a connection string for the data source.</span></span> <span data-ttu-id="c469b-118">如需連接字串的詳細資訊，請參閱[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c469b-118">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="c469b-119">按一下 **[編輯]** ，即可在 **[連接屬性]** 對話方塊中指定資料來源伺服器。</span><span class="sxs-lookup"><span data-stu-id="c469b-119">Click **Edit** to specify the data source server in the **Connection Properties** dialog box.</span></span> <span data-ttu-id="c469b-120">您可以指定本機或遠端資料來源。</span><span class="sxs-lookup"><span data-stu-id="c469b-120">You can specify a local or remote data source.</span></span>  
  
 <span data-ttu-id="c469b-121">按一下 **[認證]** ，即可提供資料庫認證。</span><span class="sxs-lookup"><span data-stu-id="c469b-121">Click **Credentials** to supply database credentials.</span></span> <span data-ttu-id="c469b-122">至少您指定的認證必須足以讓您基於報表設計用途，來連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="c469b-122">At a minimum, the credentials you specify must be sufficient for you to connect to the data source for report design purposes.</span></span> <span data-ttu-id="c469b-123">當報表是部署在報表伺服器上時，資料庫認證必須配合報表的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="c469b-123">When the report is deployed on a report server, the database credentials must accommodate all users of the report.</span></span> <span data-ttu-id="c469b-124">例如，如果您希望所有報表使用者都使用其認證來連接到資料來源，請選擇 [使用 Windows 驗證 (整合式安全性)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c469b-124">For example, if you want all report users to connect to the data source using their credentials, choose **Use Windows Authentication (Integrated Security)**.</span></span> <span data-ttu-id="c469b-125">您指定的認證對於資料來源必須是有效的，所以如果您選擇 Windows 驗證，請確定資料來源會接受來自將執行報表之所有使用者帳戶的連接。</span><span class="sxs-lookup"><span data-stu-id="c469b-125">The credentials you specify must be valid for the data source, so if you choose Windows Authentication, be sure that the data source accepts connections from all user accounts that will be running the report.</span></span> <span data-ttu-id="c469b-126">資料庫認證可以從報表中個別加以管理。</span><span class="sxs-lookup"><span data-stu-id="c469b-126">Database credentials can be managed separately from the report.</span></span> <span data-ttu-id="c469b-127">如需詳細資訊，請參閱 [管理報表資料來源](report-data/manage-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="c469b-127">For more information, see [Manage Report Data Sources](report-data/manage-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="c469b-128">**將此做為共用資料來源**</span><span class="sxs-lookup"><span data-stu-id="c469b-128">**Make this a shared data source**</span></span>  
 <span data-ttu-id="c469b-129">選取此選項，即可將資料來源儲存在專案中當做共用資料來源，而不是儲存在報表中。</span><span class="sxs-lookup"><span data-stu-id="c469b-129">Select this option to store the data source in the project as a shared data source, instead of in the report.</span></span> <span data-ttu-id="c469b-130">如此一來，您就可以將它當做專案中其他報表的資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="c469b-130">That way, you can use it as the data source for other reports in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c469b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c469b-131">See Also</span></span>  
 <span data-ttu-id="c469b-132">[內嵌和共用資料連線或資料來源 &#40;報表產生器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c469b-132">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c469b-133">[指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="c469b-133">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="c469b-134">[Reporting Services 報表伺服器](../../2014/reporting-services/reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="c469b-134">[Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="c469b-135">[Rsreportdesigner.config 設定檔](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="c469b-135">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="c469b-136">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c469b-136">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="c469b-137">報表精靈說明</span><span class="sxs-lookup"><span data-stu-id="c469b-137">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
