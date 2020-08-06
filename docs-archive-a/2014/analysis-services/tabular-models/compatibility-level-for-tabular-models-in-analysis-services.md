---
title: " (SSAS 表格式 SP1) 的相容性層級 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2853cd5509b66dbfaadd78c578b9676399e81977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708693"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a><span data-ttu-id="69b84-102">相容性層級 (SSAS 表格式 SP1)</span><span class="sxs-lookup"><span data-stu-id="69b84-102">Compatibility Level (SSAS Tabular SP1)</span></span>
  <span data-ttu-id="69b84-103">您可以在建立新的表格式模型專案時指定*相容性層級*、升級現有的表格式模型專案、升級現有的已部署表格式模型資料庫時，或是匯入 PowerPivot 活頁簿時。</span><span class="sxs-lookup"><span data-stu-id="69b84-103">You can specify *Compatibility Level* when creating new Tabular model projects, when upgrading existing Tabular model projects, when upgrading existing deployed Tabular model databases, or when importing PowerPivot workbooks.</span></span>  
  
## <a name="compatibility-level"></a><span data-ttu-id="69b84-104">相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-104">Compatibility Level</span></span>  
 <span data-ttu-id="69b84-105">將新版本和 Service Pack 安裝到實際作業電腦上之前，通常會先安裝到開發和測試電腦上。</span><span class="sxs-lookup"><span data-stu-id="69b84-105">It is common to install new versions and service packs on development and test computers prior to installing on production computers.</span></span> <span data-ttu-id="69b84-106">在這類情況下，務必了解為新的以及已部署到生產環境的表格式模型專案設定相容性層級的重要。</span><span class="sxs-lookup"><span data-stu-id="69b84-106">In such cases, it is important to understand setting compatibility level for both new Tabular model projects as well as those that have already been deployed into a production environment.</span></span>  
  
 <span data-ttu-id="69b84-107">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services 執行個體支援下列相容性層級 (資料庫版本)：</span><span class="sxs-lookup"><span data-stu-id="69b84-107">A [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services instance supports the following compatibility levels (database version):</span></span>  
  
-   <span data-ttu-id="69b84-108">SQL Server 2012 (1100) </span><span class="sxs-lookup"><span data-stu-id="69b84-108">SQL Server 2012 (1100)</span></span>  
  
-   <span data-ttu-id="69b84-109">SQL Server 2012 SP1 (1103)</span><span class="sxs-lookup"><span data-stu-id="69b84-109">SQL Server 2012 SP1 (1103)</span></span>  
  
-   <span data-ttu-id="69b84-110">SQL Server 2014 (1103)</span><span class="sxs-lookup"><span data-stu-id="69b84-110">SQL Server 2014 (1103)</span></span>  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a><span data-ttu-id="69b84-111">在建立新的表格式模型專案時設定相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-111">Set compatibility level when creating a new Tabular model project</span></span>  
 <span data-ttu-id="69b84-112">在 SQL Server Data Tools (SSDT) 中建立新的表格式模型專案時，您可以在 [**新表格式專案選項**] 對話方塊中指定相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-112">When creating a new Tabular model project in SQL Server Data Tools (SSDT), on the **New Tabular project options** dialog you can specify the compatibility level.</span></span> <span data-ttu-id="69b84-113">您可以選擇建立要部署到 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更新版本 Analysis Services 執行個體或部署到 SQL Server 2012 Analysis Services 執行個體 (不含 Service Pack 1) 的新專案。</span><span class="sxs-lookup"><span data-stu-id="69b84-113">You can choose between creating a new project to be deployed to an [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later Analysis Services instance or to an SQL Server 2012 Analysis Services instance (without Service Pack 1).</span></span>  
  
 <span data-ttu-id="69b84-114">您也可以透過選取 **[不要再顯示此訊息]** 選項指定預設相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-114">You can also specify a default compatibility level by selecting the **Do not show this message again** option.</span></span> <span data-ttu-id="69b84-115">所有後續專案都將使用您指定的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-115">All subsequent projects will use the compatibility level you specified.</span></span> <span data-ttu-id="69b84-116">您可以在 SSDT 的 [選項] 中變更預設相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-116">You can change the default compatibility level in SSDT in Options.</span></span>  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a><span data-ttu-id="69b84-117">將現有的表格式模型專案升級至 1103 相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-117">Upgrade an existing Tabular model project to 1103 compatibility level</span></span>  
 <span data-ttu-id="69b84-118">在安裝或1103更新版本之前，您可以 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 使用 [模型**屬性**] 視窗中的 [**相容性層級**] 屬性，升級在 SSDT 中建立的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="69b84-118">You can upgrade a Tabular model project created in SSDT prior to installing [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later to be database version 1103 compatible by using the **Compatibility Level** property in the model **Properties** window.</span></span> <span data-ttu-id="69b84-119">為了升級表格式模型專案，安裝 SSDT 所在的電腦必須已安裝 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更新版本，而工作空間資料庫所在的 Analysis Services 執行個體同樣必須已安裝 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="69b84-119">In order to upgrade a Tabular model project, the computer on which SSDT is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed and the Analysis Services instance on which the workspace database resides must also have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="69b84-120">您無法降級為舊版。</span><span class="sxs-lookup"><span data-stu-id="69b84-120">You cannot downgrade to an earlier version.</span></span>  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a><span data-ttu-id="69b84-121">將已部署的表格式模型資料庫升級至 1103 相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-121">Upgrade a deployed Tabular model database to 1103 compatibility level</span></span>  
 <span data-ttu-id="69b84-122">您可以使用 [**資料庫屬性**] 中的 [**相容性層級**] 屬性，將現有已部署的表格式模型資料庫升級至 SQL Server Management Studio (SSMS) 中相容的資料庫版本1103。</span><span class="sxs-lookup"><span data-stu-id="69b84-122">You can upgrade an existing deployed Tabular model database to database version 1103 compatible in SQL Server Management Studio (SSMS) by using the **Compatibility Level** property in **Database Properties**.</span></span> <span data-ttu-id="69b84-123">為了進行升級，安裝 SQL Server Analysis Services 執行個體所在的電腦上必須已安裝 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="69b84-123">In order to upgrade, the computer on which the SQL Server Analysis Services instance is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="69b84-124">您無法將部署的表格式模型資料庫降級為舊版。</span><span class="sxs-lookup"><span data-stu-id="69b84-124">You cannot downgrade a deployed Tabular model database to an earlier version.</span></span>  
  
### <a name="import-from-powerpivot"></a><span data-ttu-id="69b84-125">從 PowerPivot 匯入</span><span class="sxs-lookup"><span data-stu-id="69b84-125">Import from PowerPivot</span></span>  
 <span data-ttu-id="69b84-126">透過從 PowerPivot 匯入來建立新的表格式模型專案時，可以指定要將相容性層級升級為預設相容性層級 (之前已在 SSDT 中設定的話)，或是維持 PowerPivot 活頁簿中已指定的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-126">When creating a new Tabular model project by importing from PowerPivot, you can specify if you want to upgrade the compatibility level to the default compatibility level (if previously configured in SSDT) or leave the compatibility level to that already specified in the PowerPivot workbook.</span></span>  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a><span data-ttu-id="69b84-127">在 SSMS 中檢查表格式模型資料庫的相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-127">Check compatibility level for a Tabular model database in SSMS</span></span>  
 <span data-ttu-id="69b84-128">您可以藉由在資料庫屬性中) 的新功能，查看 [**相容性層級**] (屬性，在 SSMS 中檢查表格式模型資料庫的相容性層級 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 。 **Database Properties**</span><span class="sxs-lookup"><span data-stu-id="69b84-128">You can check the compatibility level for a Tabular model database in SSMS by viewing the **Compatibility Level** property (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Database Properties**.</span></span>  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a><span data-ttu-id="69b84-129">在 SSMS 中檢查 Analysis Services 執行個體支援的相容性層級</span><span class="sxs-lookup"><span data-stu-id="69b84-129">Check supported compatibility level for an Analysis Services instance in SSMS</span></span>  
 <span data-ttu-id="69b84-130">您可以藉由在 [**資訊**] 頁面上查看 [**支援的相容性層級**] 屬性，在 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] **Analysis Services 屬性**中) 的新 (，以檢查 SSMS 支援的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="69b84-130">You can check the supported compatibility level in SSMS by viewing the **Supported Compatibility Level** property on the **Information** page (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Services Properties**.</span></span> <span data-ttu-id="69b84-131">支援的相容性層級 1103 表示已安裝 SQL Server SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="69b84-131">A supported compatibility level of 1103 indicates SQL Server SP1 or later is installed.</span></span> <span data-ttu-id="69b84-132">支援的相容性層級無法變更。</span><span class="sxs-lookup"><span data-stu-id="69b84-132">The supported compatibility level cannot be changed.</span></span>  
  
  
