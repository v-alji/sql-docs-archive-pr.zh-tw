---
title: 使用 Upgrade Advisor 來準備升級 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e53d895cb19a172d0810ae9d6c2bda3406732da1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700576"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a><span data-ttu-id="ce80e-102">使用 Upgrade Advisor 來準備升級</span><span class="sxs-lookup"><span data-stu-id="ce80e-102">Use Upgrade Advisor to Prepare for Upgrades</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce80e-103">Upgrade Advisor 可以協助您完成升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的相關準備工作。</span><span class="sxs-lookup"><span data-stu-id="ce80e-103">Upgrade Advisor helps you prepare for upgrades to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ce80e-104">Upgrade Advisor 會分析已安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 舊版元件，然後產生報告，以指出在您升級之前或之後要修正的問題。</span><span class="sxs-lookup"><span data-stu-id="ce80e-104">Upgrade Advisor analyzes installed components from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then generates a report that identifies issues to fix either before or after you upgrade.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="ce80e-105">Upgrade Advisor 如何運作</span><span class="sxs-lookup"><span data-stu-id="ce80e-105">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="ce80e-106">當您執行 Upgrade Advisor 時，Upgrade Advisor 首頁會出現。</span><span class="sxs-lookup"><span data-stu-id="ce80e-106">When you run Upgrade Advisor, the Upgrade Advisor Home page appears.</span></span> <span data-ttu-id="ce80e-107">您可以從首頁執行下列工具：</span><span class="sxs-lookup"><span data-stu-id="ce80e-107">From the Home page, you can run the following tools:</span></span>  
  
-   <span data-ttu-id="ce80e-108">Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="ce80e-108">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="ce80e-109">Upgrade Advisor 報表檢視器</span><span class="sxs-lookup"><span data-stu-id="ce80e-109">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="ce80e-110">Upgrade Advisor 說明</span><span class="sxs-lookup"><span data-stu-id="ce80e-110">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="ce80e-111">第一次使用 Upgrade Advisor 時，請執行 Upgrade Advisor Analysis 精靈分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="ce80e-111">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="ce80e-112">當精靈完成分析時，請在 Upgrade Advisor 報表檢視器中檢視產生的報表。</span><span class="sxs-lookup"><span data-stu-id="ce80e-112">When the wizard finishes the analysis, view the resulting reports in the Upgrade Advisor Report Viewer.</span></span> <span data-ttu-id="ce80e-113">每一份報告都會提供 Upgrade Advisor 說明資訊的連結，以協助您修正或降低已知問題的影響。</span><span class="sxs-lookup"><span data-stu-id="ce80e-113">Each report provides links to information in Upgrade Advisor Help that will help you fix or reduce the effect of the known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis"></a><span data-ttu-id="ce80e-114">Upgrade Advisor 分析</span><span class="sxs-lookup"><span data-stu-id="ce80e-114">Upgrade Advisor Analysis</span></span>  
 <span data-ttu-id="ce80e-115">Upgrade Advisor 會分析下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件：</span><span class="sxs-lookup"><span data-stu-id="ce80e-115">Upgrade Advisor analyzes the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 <span data-ttu-id="ce80e-116">分析會檢查可以存取的物件，例如指令碼、預存程序、觸發程序和追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="ce80e-116">The analysis examines objects that can be accessed, such as scripts, stored procedures, triggers, and trace files.</span></span> <span data-ttu-id="ce80e-117">Upgrade Advisor 無法分析桌面應用程式或加密的預存程序。</span><span class="sxs-lookup"><span data-stu-id="ce80e-117">Upgrade Advisor cannot analyze desktop applications or encrypted stored procedures.</span></span>  
  
 <span data-ttu-id="ce80e-118">輸出為 XML 報表的形式。</span><span class="sxs-lookup"><span data-stu-id="ce80e-118">Output is in the form of an XML report.</span></span> <span data-ttu-id="ce80e-119">請使用 Upgrade Advisor 報表檢視器來檢視 XML 報表。</span><span class="sxs-lookup"><span data-stu-id="ce80e-119">View the XML report by using the Upgrade Advisor report viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce80e-120">報表可能包含「其他升級問題」項目。</span><span class="sxs-lookup"><span data-stu-id="ce80e-120">Reports might contain an "other upgrade issues" item.</span></span> <span data-ttu-id="ce80e-121">這個項目會連結到 Upgrade Advisor 不會偵測，但您的伺服器或應用程式中可能存在的問題清單。</span><span class="sxs-lookup"><span data-stu-id="ce80e-121">This item links to a list of issues that are not detected by Upgrade Advisor, but might exist on your server or in your applications.</span></span> <span data-ttu-id="ce80e-122">您應該檢閱無法偵測到的問題清單，並判斷您是否因為這些無法偵測到的問題，而必須變更伺服器或應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce80e-122">You should review the list of undetectable issues and determine whether you must change your server or applications because of the undetectable issues.</span></span>  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a><span data-ttu-id="ce80e-123">如何安裝和執行 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="ce80e-123">How to Install and Run Upgrade Advisor</span></span>  
 <span data-ttu-id="ce80e-124">安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor 的位置取決於您要分析的項目。</span><span class="sxs-lookup"><span data-stu-id="ce80e-124">The location where you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="ce80e-125">Upgrade Advisor 支援所有支援元件 ([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 除外) 的遠端分析。</span><span class="sxs-lookup"><span data-stu-id="ce80e-125">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ce80e-126">如果不要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的執行個體，可以將 Upgrade Advisor 安裝在可連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，且符合 Upgrade Advisor 必要條件的任何電腦上。</span><span class="sxs-lookup"><span data-stu-id="ce80e-126">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="ce80e-127">如需詳細資訊，請參閱 [支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="ce80e-127">For more information, see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="ce80e-128">如果您要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的執行個體，則必須將 Upgrade Advisor 安裝在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="ce80e-128">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="ce80e-129">功能套件提供 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="ce80e-129">Upgrade Advisor is available in a feature pack.</span></span>  
  
 <span data-ttu-id="ce80e-130">安裝及執行 Upgrade Advisor 的先決條件如下：</span><span class="sxs-lookup"><span data-stu-id="ce80e-130">Prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="ce80e-131">SP2、Windows 7 SP1 及 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1。</span><span class="sxs-lookup"><span data-stu-id="ce80e-131">SP2, Windows 7 SP1, and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span>  
  
-   <span data-ttu-id="ce80e-132">Windows Installer 從版本 4.5 開始。</span><span class="sxs-lookup"><span data-stu-id="ce80e-132">Windows Installer beginning with version 4.5.</span></span> <span data-ttu-id="ce80e-133">您可以從[Windows Installer 的網站](https://www.microsoft.com/download/details.aspx?id=8483)安裝 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="ce80e-133">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="ce80e-134">Microsoft .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="ce80e-134">Microsoft .NET Framework 4.</span></span> <span data-ttu-id="ce80e-135">.NET Framework 4 可在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 產品媒體上取得，並從[.NET Framework 4 下載頁面](https://go.microsoft.com/fwlink/?LinkId=209895)取得。</span><span class="sxs-lookup"><span data-stu-id="ce80e-135">.NET Framework 4 is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [.NET Framework 4 download page](https://go.microsoft.com/fwlink/?LinkId=209895).</span></span>  
  
    -   <span data-ttu-id="ce80e-136">若要從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 媒體安裝 .NET Framework 4，請找出光碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="ce80e-136">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="ce80e-137">然後，在 \redist 資料夾上按兩下滑鼠按鈕後於 DotNetFrameworks 資料夾上再按兩下滑鼠按鈕，然後執行 dotNetFx40_Full_x86_x64.exe (32 位元作業系統或 64 位元作業系統)。</span><span class="sxs-lookup"><span data-stu-id="ce80e-137">Then, double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for 32-bit operating systems or for 64-bit operating systems).</span></span>  
  
 <span data-ttu-id="ce80e-138">若要從網路安裝 Upgrade Advisor，請在下載網頁上按一下 [下載] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce80e-138">To install Upgrade Advisor from the Web, click the download button on the download page.</span></span> <span data-ttu-id="ce80e-139">接著您可立即執行安裝，或是儲存 SQLUA.msi 檔，並於稍後再執行。</span><span class="sxs-lookup"><span data-stu-id="ce80e-139">You can then run installation immediately, or save the SQLUA.msi file to run later.</span></span> <span data-ttu-id="ce80e-140">如果要從產品光碟安裝，請直接從產品光碟執行 SQLUA.msi。</span><span class="sxs-lookup"><span data-stu-id="ce80e-140">If you are installing from the product disc, run SQLUA.msi directly from the product disk.</span></span>  
  
 <span data-ttu-id="ce80e-141">安裝 Upgrade Advisor 之後，您可以從 [**開始**] 功能表開啟它：</span><span class="sxs-lookup"><span data-stu-id="ce80e-141">After you install Upgrade Advisor, you can open it from the **Start** menu:</span></span>  
  
-   <span data-ttu-id="ce80e-142">按一下 [**開始**]，指向 [**所有程式**]，再指向 [] [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] ，然後按一下 [ \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor\*\*]。</span><span class="sxs-lookup"><span data-stu-id="ce80e-142">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
 <span data-ttu-id="ce80e-143">如需詳細資訊，請參閱 Upgrade Advisor 下載以及 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本資訊中的 Upgrade Advisor 文件。</span><span class="sxs-lookup"><span data-stu-id="ce80e-143">For more information, see the Upgrade Advisor documentation included in the Upgrade Advisor download and the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Release Notes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce80e-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce80e-144">See Also</span></span>  
 <span data-ttu-id="ce80e-145">[使用 SQL Server 的多個版本和實例](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ce80e-145">[Work with Multiple Versions and Instances of SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="ce80e-146">[支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="ce80e-146">[Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 [<span data-ttu-id="ce80e-147">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="ce80e-147">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
