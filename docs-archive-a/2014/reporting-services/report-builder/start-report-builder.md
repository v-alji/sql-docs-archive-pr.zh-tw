---
title: 開始報表產生器 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 28c046f5f46e1633cb108bf2d7f1803d6adc702b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598238"
---
# <a name="start-report-builder-report-builder"></a><span data-ttu-id="7c183-102">啟動報表產生器 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="7c183-102">Start Report Builder (Report Builder)</span></span>
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]<span data-ttu-id="7c183-103">包含獨立和 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 版本的報表產生器。</span><span class="sxs-lookup"><span data-stu-id="7c183-103">includes stand-alone and [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] versions of Report Builder.</span></span> <span data-ttu-id="7c183-104">[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 版本可以搭配在原生模式或 SharePoint 整合模式下安裝的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用。</span><span class="sxs-lookup"><span data-stu-id="7c183-104">The [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version can be used with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed in native or SharePoint integrated mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c183-105">報表產生器無法安裝在 Itanium 64 型電腦上。</span><span class="sxs-lookup"><span data-stu-id="7c183-105">Report Builder cannot be installed on Itanium 64-based computers.</span></span> <span data-ttu-id="7c183-106">這同樣適用於 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 和單機版本的報表產生器。</span><span class="sxs-lookup"><span data-stu-id="7c183-106">This applies to the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] and stand-alone versions of Report Builder.</span></span>  
  
 <span data-ttu-id="7c183-107">如果開啟之 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 版本的報表產生器為舊版的報表產生器，請連絡可以更新報表管理員和 SharePoint 網站的管理員來使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本的報表產生器。</span><span class="sxs-lookup"><span data-stu-id="7c183-107">If the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder that opens is an earlier version of Report Builder, contact your administrator who can update Report Manager and the SharePoint site to use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Report Builder</span></span>  
  
 <span data-ttu-id="7c183-108">您也可以在已發行至 SharePoint 的 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 活頁簿上使用 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 版本的報表產生器建立報表。</span><span class="sxs-lookup"><span data-stu-id="7c183-108">You can also use the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder to create reports on a [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] workbook that has been published to SharePoint.</span></span> <span data-ttu-id="7c183-109">如需搭配使用報表產生器的詳細資訊 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ，請參閱在 technet.microsoft.com 上[使用 PowerPivot 資料建立 Reporting Services 報表](https://go.microsoft.com/fwlink/?LinkId=185238)。</span><span class="sxs-lookup"><span data-stu-id="7c183-109">For more information about using Report Builder with [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], see [Create a Reporting Services Report with PowerPivot Data](https://go.microsoft.com/fwlink/?LinkId=185238) on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="7c183-110">若要從本機電腦上的 [**開始**] 功能表獨立啟動報表產生器，您或系統管理員必須先在電腦上安裝報表產生器，才能使用此工具。</span><span class="sxs-lookup"><span data-stu-id="7c183-110">To start Report Builder stand-alone from the **Start** menu on your local computer, you or an administrator must install Report Builder directly on your computer before the tool is available for you to use.</span></span> <span data-ttu-id="7c183-111">安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時不會安裝單機版本；您必須另外進行下載與安裝。</span><span class="sxs-lookup"><span data-stu-id="7c183-111">The stand-alone version is not installed when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]; you must download and install it separately.</span></span> <span data-ttu-id="7c183-112">若要下載報表產生器，請參閱[Microsoft® SQL Server®2012報表產生器](https://go.microsoft.com/fwlink/?LinkId=401502)。</span><span class="sxs-lookup"><span data-stu-id="7c183-112">To download Report Builder, see [Microsoft® SQL Server® 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkId=401502).</span></span>  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a><span data-ttu-id="7c183-113">若要從報表管理員啟動報表產生器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="7c183-113">To start Report Builder ClickOnce from Report Manager</span></span>  
  
1.  <span data-ttu-id="7c183-114">在網頁瀏覽器的網址列中，輸入報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="7c183-114">In your Web browser, type the URL for your report server in the address bar.</span></span> <span data-ttu-id="7c183-115">根據預設，URL 為 HTTP:// \<*servername*> /reports。</span><span class="sxs-lookup"><span data-stu-id="7c183-115">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="7c183-116">報表管理員隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7c183-116">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="7c183-117">按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="7c183-117">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="7c183-118">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="7c183-118">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="7c183-119">若要使用 URL 來啟動報表產生器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="7c183-119">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="7c183-120">在網頁瀏覽器中，於網址列中輸入下列 URL：</span><span class="sxs-lookup"><span data-stu-id="7c183-120">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="7c183-121">HTTP:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0. 應用程式</span><span class="sxs-lookup"><span data-stu-id="7c183-121">http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application</span></span>  
  
2.  <span data-ttu-id="7c183-122">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7c183-122">Press ENTER.</span></span>  
  
     <span data-ttu-id="7c183-123">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="7c183-123">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a><span data-ttu-id="7c183-124">以 SharePoint 整合模式啟動報表產生器 ClickOnce</span><span class="sxs-lookup"><span data-stu-id="7c183-124">To start Report Builder ClickOnce in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="7c183-125">巡覽至包含您需要之文件庫的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="7c183-125">Navigate to the SharePoint site that contains the library you want.</span></span>  
  
2.  <span data-ttu-id="7c183-126">開啟文件庫。</span><span class="sxs-lookup"><span data-stu-id="7c183-126">Open the library.</span></span>  
  
3.  <span data-ttu-id="7c183-127">按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c183-127">Click **Documents**.</span></span>  
  
4.  <span data-ttu-id="7c183-128">在 [新增文件]\*\*\*\* 功能表上，按一下 [報表產生器報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c183-128">On the **New Document** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="7c183-129">報表產生器隨即開啟，而且您可以在報表伺服器上建立報表或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="7c183-129">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
     <span data-ttu-id="7c183-130">**注意**如果 [**新增檔**] 功能表未列出 [**報表產生器報表**]、[**報表產生器模型**] 和 [**報表資料來源**] 選項，則必須將其內容類型加入至 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="7c183-130">**Note** If the **New Document** menu does not list the **Report Builder Report**, **Report Builder Model**, and **Report Data Source** options, their content types need to be added to the SharePoint library.</span></span> <span data-ttu-id="7c183-131">如需詳細資訊，請參閱 msdn.microsoft.com 上的《線上叢書》中的[將報表伺服器內容類型加入至程式庫 &#40;Reporting Services SharePoint 整合模式中的&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="7c183-131">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a><span data-ttu-id="7c183-132">若要從開始功能表獨立啟動報表產生器</span><span class="sxs-lookup"><span data-stu-id="7c183-132">To start Report Builder stand-alone from the Start menu</span></span>  
  
1.  <span data-ttu-id="7c183-133">在 [開始] 功能表上，按一下 [**所有程式**]，然後按一下 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="7c183-133">On the Start menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="7c183-134">按一下 [報表產生器] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="7c183-134">Click **Report Builder** .</span></span>  
  
     <span data-ttu-id="7c183-135">報表產生器隨即開啟，而且您可以建立或開啟報表。</span><span class="sxs-lookup"><span data-stu-id="7c183-135">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="7c183-136">若要建立新的報表，請按一下報表產生器左上角的 SQL Server 圖示，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="7c183-136">To create a new report, click the SQL Server icon in the upper left-hand corner of Report Builder, and then click New.</span></span>  
  
4.  <span data-ttu-id="7c183-137">若要開啟儲存於您本機電腦或報表伺服器上的現有報表，請按一下左上角的 SQL Server 圖示，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="7c183-137">To open an existing report stored on your local machine or a report server, click the SQL Server icon in the upper left-hand corner, and then click Open.</span></span>  
  
     <span data-ttu-id="7c183-138">如果您在現有伺服器清單中看不到報表伺服器，請關閉 [**開啟報表**] 對話方塊，然後按一下報表產生器底部的 [**連接**]，以連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c183-138">If you don't see the report server in the list of existing servers, close the **Open Report** dialog box and then click **Connect** at the bottom of Report Builder to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c183-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c183-139">See Also</span></span>  
 [<span data-ttu-id="7c183-140">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="7c183-140">Report Builder in SQL Server 2014</span></span>](report-builder-in-sql-server-2016.md)  
  
  
