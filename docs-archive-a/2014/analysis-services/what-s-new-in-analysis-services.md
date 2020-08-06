---
title: Analysis Services 和商業智慧的&#39;新功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18863a565b63ccc1a9bd2eb0e7619d4d133c5d33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592887"
---
# <a name="what39s-new-in-sql-server-2014-analysis-services"></a><span data-ttu-id="81772-102">SQL Server 2014 中的新功能&#39;Analysis Services</span><span class="sxs-lookup"><span data-stu-id="81772-102">What&#39;s New in SQL Server 2014 Analysis Services</span></span>
  <span data-ttu-id="81772-103">除了針對多維度模型支援 Power View 報表的新增功能之外， [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 舊版也不會變更。</span><span class="sxs-lookup"><span data-stu-id="81772-103">With exception to added functionality supporting Power View Reports against Multidimensional Models, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is unchanged from the previous release.</span></span>

 <span data-ttu-id="81772-104">如需 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 此版本中其他產品和技術的相關資訊，請參閱[SQL Server 2014 中的新功能](../sql-server/what-s-new-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="81772-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies that are different in this release, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>

## <a name="updates-to-design-tool-installation"></a><span data-ttu-id="81772-105">設計工具安裝的更新</span><span class="sxs-lookup"><span data-stu-id="81772-105">Updates to Design Tool installation</span></span>
 <span data-ttu-id="81772-106">之前稱為 Business Intelligence Development Studio (BIDS) 的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI) 是用來建立 Analysis Services 模型、Reporting Services 報表和 Integration Services 封裝。</span><span class="sxs-lookup"><span data-stu-id="81772-106">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="81772-107">您可以從以下位置下載 SSDT-BI：</span><span class="sxs-lookup"><span data-stu-id="81772-107">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="81772-108">下載 SSDT-BI for Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="81772-108">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="81772-109">下載 SSDT-BI for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="81772-109">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="81772-110">如果電腦上已安裝舊版的 SSDT-BI 或 BIDS，較新的版本會與舊版並存安裝。</span><span class="sxs-lookup"><span data-stu-id="81772-110">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="81772-111">通常會在單一工作站上執行新版與舊版的設計工具，這樣一來，您就可以修改與特定伺服器版本繫結的專案和方案。</span><span class="sxs-lookup"><span data-stu-id="81772-111">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="81772-112">Visual Studio 2012 和 Visual Studio 2013 版的 SSDT 有幾個下載網站。</span><span class="sxs-lookup"><span data-stu-id="81772-112">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="81772-113">大部分都未包括 BI 專案範本。</span><span class="sxs-lookup"><span data-stu-id="81772-113">Most do not include the BI project templates.</span></span> <span data-ttu-id="81772-114">使用上述連結會讓您得到正確的版本。</span><span class="sxs-lookup"><span data-stu-id="81772-114">Using the links above will get you the correct version.</span></span> <span data-ttu-id="81772-115">如果您看到 [商業智慧專案範本] 資料夾，您會知道您擁有正確的 SSDT-BI 版本。</span><span class="sxs-lookup"><span data-stu-id="81772-115">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="81772-116">此資料夾包含 Analysis Services、Reporting Services 和 Integration Services 適用的專案範本。</span><span class="sxs-lookup"><span data-stu-id="81772-116">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="81772-117">依據您安裝 SSDT-BI 的方式，您也可能會看到一個額外的 SQL Server 資料庫專案範本。</span><span class="sxs-lookup"><span data-stu-id="81772-117">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="81772-118">![SSDT 中的新專案範本](media/ssdt-biprojects.png "SSDT 中的新專案範本")</span><span class="sxs-lookup"><span data-stu-id="81772-118">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="features-recently-added-power-view-for-multidimensional-models"></a><span data-ttu-id="81772-119">最近加入的功能：多維度模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="81772-119">Features recently added: Power View for Multidimensional Models</span></span>
 <span data-ttu-id="81772-120">能夠針對多維度模型建立 Power View 報表的功能最先在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 累計更新 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="81772-120">The ability to create Power View reports against multidimensional models was first introduced in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 4.</span></span> <span data-ttu-id="81772-121">多維度模型的 Power View 功能現在已經是 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="81772-121">Power View for Multidimensional Models functionality is now included as part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>

 <span data-ttu-id="81772-122">**多維度模型的 Power View 報表**</span><span class="sxs-lookup"><span data-stu-id="81772-122">**Power View Report for a Multidimensional Model**</span></span>

 <span data-ttu-id="81772-123">![Power View 報表](media/powerviewreport-wn.gif "Power View 報表")</span><span class="sxs-lookup"><span data-stu-id="81772-123">![Power View Report](media/powerviewreport-wn.gif "Power View Report")</span></span>

 <span data-ttu-id="81772-124">此功能可幫助組織啟用要與最新用戶端報表工具一起使用的多維度模型 (也稱為 OLAP Cube)，好讓現有的 BI 投資達到最大效益。</span><span class="sxs-lookup"><span data-stu-id="81772-124">This functionality helps organizations maximize existing BI investments by enabling multidimensional models (also known as OLAP cubes) to be used with the latest client reporting tools.</span></span> <span data-ttu-id="81772-125">根據多維度模型中的資料類型，使用者可以輕鬆地建立各種不同的動態視覺效果，從資料表和矩陣到泡泡圖和地圖。</span><span class="sxs-lookup"><span data-stu-id="81772-125">Depending on the types of data in the multidimensional model, users can easily create a variety of dynamic visualizations from tables and matrices, to bubble charts and geographical maps.</span></span> <span data-ttu-id="81772-126">多維度模型現在也支援使用 Data Analysis Expressions (DAX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="81772-126">Multidimensional models now also support queries using Data Analysis Expressions (DAX).</span></span>

 <span data-ttu-id="81772-127">多維度模型的 Power View 要求 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中必須有內建的 Power View 報表功能 (SharePoint 模式)。</span><span class="sxs-lookup"><span data-stu-id="81772-127">Power View for Multidimensional Models requires the built-in Power View reporting capability in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (in SharePoint mode).</span></span> <span data-ttu-id="81772-128">Power View 的其他版本 (特別是 Excel 2013 中的 Power View 增益集) 不支援多維度模型。</span><span class="sxs-lookup"><span data-stu-id="81772-128">Other versions of Power View, specifically the Power View Add-in in Excel 2013, do not support multidimensional models.</span></span>

 <span data-ttu-id="81772-129">若要深入瞭解，請參閱多[維度模型的 Power View](https://msdn.microsoft.com/library/dn140246.aspx)。</span><span class="sxs-lookup"><span data-stu-id="81772-129">To learn more, see [Power View for Multidimensional Models](https://msdn.microsoft.com/library/dn140246.aspx).</span></span>


