---
title: Analysis Services 中使用的工具和應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36bbcbca4323a9ce327b5fa89398dfb20da319c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592286"
---
# <a name="tools-and-applications-used-in-analysis-services"></a><span data-ttu-id="aa767-102">Analysis Services 中使用的工具和應用程式</span><span class="sxs-lookup"><span data-stu-id="aa767-102">Tools and applications used in Analysis Services</span></span>
  <span data-ttu-id="aa767-103">尋找在 Analysis Services 執行個體上建立 Analysis Services 模型和管理關聯資料庫所需的工具與應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa767-103">Find the tools and applications you'll need for building Analysis Services models, and managing the associated databases on an Analysis Services instance.</span></span>

## <a name="analysis-services-model-designers"></a><span data-ttu-id="aa767-104">Analysis Services 模型設計師</span><span class="sxs-lookup"><span data-stu-id="aa767-104">Analysis Services Model Designers</span></span>
 <span data-ttu-id="aa767-105">表格式與多維度模型是從 Visual Studio Shell 內建方案中的專案範本建立的。</span><span class="sxs-lookup"><span data-stu-id="aa767-105">Tabular and multidimensional models are created from project templates in a solution built inside the Visual Studio shell.</span></span> <span data-ttu-id="aa767-106">專案範本可供設計人員建立組成 Analysis Services 方案的模型、Cube、維度及角色。</span><span class="sxs-lookup"><span data-stu-id="aa767-106">The project template provides the designers for creating models, cubes, dimensions, and roles that comprise an Analysis Services solution.</span></span>

### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a><span data-ttu-id="aa767-107">下載 SQL Server Data Tools for Business Intelligence (SSDT-BI)</span><span class="sxs-lookup"><span data-stu-id="aa767-107">Download SQL Server Data Tools for Business Intelligence (SSDT-BI)</span></span>
 <span data-ttu-id="aa767-108">之前稱為 Business Intelligence Development Studio (BIDS) 的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI) 是用來建立 Analysis Services 模型、Reporting Services 報表和 Integration Services 封裝。</span><span class="sxs-lookup"><span data-stu-id="aa767-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="aa767-109">您可以從以下位置下載 SSDT-BI：</span><span class="sxs-lookup"><span data-stu-id="aa767-109">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="aa767-110">下載 SSDT-BI for Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="aa767-110">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="aa767-111">下載 SSDT-BI for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="aa767-111">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="aa767-112">如果電腦上已安裝舊版的 SSDT-BI 或 BIDS，較新的版本會與舊版並存安裝。</span><span class="sxs-lookup"><span data-stu-id="aa767-112">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="aa767-113">通常會在單一工作站上執行新版與舊版的設計工具，這樣一來，您就可以修改與特定伺服器版本繫結的專案和方案。</span><span class="sxs-lookup"><span data-stu-id="aa767-113">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="aa767-114">Visual Studio 2012 和 Visual Studio 2013 版的 SSDT 有幾個下載網站。</span><span class="sxs-lookup"><span data-stu-id="aa767-114">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="aa767-115">大部分都未包括 BI 專案範本。</span><span class="sxs-lookup"><span data-stu-id="aa767-115">Most do not include the BI project templates.</span></span> <span data-ttu-id="aa767-116">使用上述連結會讓您得到正確的版本。</span><span class="sxs-lookup"><span data-stu-id="aa767-116">Using the links above will get you the correct version.</span></span> <span data-ttu-id="aa767-117">如果您看到 [商業智慧專案範本] 資料夾，您會知道您擁有正確的 SSDT-BI 版本。</span><span class="sxs-lookup"><span data-stu-id="aa767-117">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="aa767-118">此資料夾包含 Analysis Services、Reporting Services 和 Integration Services 適用的專案範本。</span><span class="sxs-lookup"><span data-stu-id="aa767-118">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="aa767-119">依據您安裝 SSDT-BI 的方式，您也可能會看到一個額外的 SQL Server 資料庫專案範本。</span><span class="sxs-lookup"><span data-stu-id="aa767-119">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="aa767-120">![SSDT 中的新專案範本](media/ssdt-biprojects.png "SSDT 中的新專案範本")</span><span class="sxs-lookup"><span data-stu-id="aa767-120">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="administrative-tools"></a><span data-ttu-id="aa767-121">系統管理工具</span><span class="sxs-lookup"><span data-stu-id="aa767-121">Administrative tools</span></span>

### <a name="sql-server-management-studio"></a><span data-ttu-id="aa767-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa767-122">SQL Server Management Studio</span></span>
 <span data-ttu-id="aa767-123">Management Studio 是所有 SQL Server 功能 (包括 Analysis Services) 的主要系統管理工具。</span><span class="sxs-lookup"><span data-stu-id="aa767-123">Management Studio is the primary administration tool for all SQL Server features, including Analysis Services.</span></span> <span data-ttu-id="aa767-124">SQL Server Management Studio 是選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="aa767-124">SQL Server Management Studio is an optional component.</span></span> <span data-ttu-id="aa767-125">如果您在 Windows Server 2012 的 [應用程式] 頁面上未看到該元件和其他 SQL Server 應用程式，請執行 SQL Server 安裝程式以將其新增到您的安裝。</span><span class="sxs-lookup"><span data-stu-id="aa767-125">If you don't see it with other SQL Server applications on the Apps page in Windows Server 2012, run SQL Server Setup to add it to your installation.</span></span>

### <a name="sql-server-profiler"></a><span data-ttu-id="aa767-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="aa767-126">SQL Server Profiler</span></span>
 <span data-ttu-id="aa767-127">雖然 SQL Server Profiler 已正式被取代，但它卻是監視連線、MDX 查詢執行及其他伺服器作業最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="aa767-127">Although it's officially deprecated, SQL Server Profiler provides an easy way to monitor connections, MDX query execution, and other server operations.</span></span> <span data-ttu-id="aa767-128">SQL Server Profiler 是預設會安裝的元件。</span><span class="sxs-lookup"><span data-stu-id="aa767-128">SQL Server Profiler is installed by default.</span></span> <span data-ttu-id="aa767-129">您可以在 Windows Server 2012 的 [應用程式] 頁面上看到該元件和其他 SQL Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa767-129">You can find it with SQL Server applications on Apps in Windows Server 2012.</span></span>

### <a name="powershell"></a><span data-ttu-id="aa767-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa767-130">PowerShell</span></span>
 <span data-ttu-id="aa767-131">您可以使用 PowerShell 命令來執行許多系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="aa767-131">You can use PowerShell commands to perform many administrative tasks.</span></span> <span data-ttu-id="aa767-132">如需詳細資訊，請參閱＜ [Analysis Services PowerShell](analysis-services-powershell.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="aa767-132">See [Analysis Services PowerShell](analysis-services-powershell.md) for more information.</span></span>

### <a name="community-and-third-party-tools"></a><span data-ttu-id="aa767-133">社群與協力廠商工具</span><span class="sxs-lookup"><span data-stu-id="aa767-133">Community and Third-party tools</span></span>
 <span data-ttu-id="aa767-134">如需社群程式碼範例，請造訪 [Analysis Services codeplex 頁面](https://sqlsrvanalysissrvcs.codeplex.com/) 。</span><span class="sxs-lookup"><span data-stu-id="aa767-134">Check the [Analysis Services codeplex page](https://sqlsrvanalysissrvcs.codeplex.com/) for community code samples.</span></span> <span data-ttu-id="aa767-135">針對支援 Analysis Services 的協力廠商工具尋求建議時，[論壇](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices)會很有説明。</span><span class="sxs-lookup"><span data-stu-id="aa767-135">[Forums](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) can be helpful when seeking recommendations for third-party tools that support Analysis Services.</span></span>
