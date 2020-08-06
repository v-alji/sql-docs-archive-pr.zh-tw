---
title: 正在執行 Upgrade Advisor (使用者介面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a5e47ef2b8183823dff884e114adc420e371adf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606589"
---
# <a name="running-upgrade-advisor-user-interface"></a><span data-ttu-id="9bd94-102">執行 Upgrade Advisor (使用者介面)</span><span class="sxs-lookup"><span data-stu-id="9bd94-102">Running Upgrade Advisor (User Interface)</span></span>
  <span data-ttu-id="9bd94-103">在升級規劃期間，您可以執行 Upgrade Advisor 來分析本機或遠端元件。</span><span class="sxs-lookup"><span data-stu-id="9bd94-103">You can run Upgrade Advisor to analyze local or remote components during upgrade planning.</span></span> <span data-ttu-id="9bd94-104">Upgrade Advisor 會針對分析的每個元件和執行個體產生一份報表。</span><span class="sxs-lookup"><span data-stu-id="9bd94-104">Upgrade Advisor produces a report for each component and instance that is analyzed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9bd94-105">Upgrade Advisor 不會分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的遠端執行個體。</span><span class="sxs-lookup"><span data-stu-id="9bd94-105">Upgrade Advisor does not analyze remote instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9bd94-106">若要分析 [!INCLUDE[ssRS](../../includes/ssrs.md)] 執行個體，您必須將 Upgrade Advisor 安裝在已安裝 [!INCLUDE[ssRS](../../includes/ssrs.md)] 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9bd94-106">To analyze an instance of [!INCLUDE[ssRS](../../includes/ssrs.md)], Upgrade Advisor must be installed on the computer where [!INCLUDE[ssRS](../../includes/ssrs.md)] is installed.</span></span>  
>   
>  <span data-ttu-id="9bd94-107">若要分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services，您必須在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 同一部 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 電腦上安裝並安裝和。</span><span class="sxs-lookup"><span data-stu-id="9bd94-107">To analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, you must have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] installed and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed on the same computer.</span></span>  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a><span data-ttu-id="9bd94-108">執行 Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="9bd94-108">Running the Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="9bd94-109">執行 Upgrade Advisor 分析精靈具有六個步驟：</span><span class="sxs-lookup"><span data-stu-id="9bd94-109">Running the Upgrade Advisor Analysis Wizard has six steps:</span></span>  
  
1.  <span data-ttu-id="9bd94-110">從 Upgrade Advisor 開始頁面啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="9bd94-110">Launch the wizard from the Upgrade Advisor start page.</span></span>  
  
2.  <span data-ttu-id="9bd94-111">識別要分析的伺服器和元件。</span><span class="sxs-lookup"><span data-stu-id="9bd94-111">Identify server and components to analyze.</span></span>  
  
3.  <span data-ttu-id="9bd94-112">蒐集驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="9bd94-112">Gather authentication information.</span></span>  
  
4.  <span data-ttu-id="9bd94-113">根據元件類型，蒐集其他參數。</span><span class="sxs-lookup"><span data-stu-id="9bd94-113">Gather additional parameters based on component type.</span></span>  
  
5.  <span data-ttu-id="9bd94-114">分析選取的元件。</span><span class="sxs-lookup"><span data-stu-id="9bd94-114">Analyze selected components.</span></span>  
  
6.  <span data-ttu-id="9bd94-115">產生升級問題的報表。</span><span class="sxs-lookup"><span data-stu-id="9bd94-115">Generate report of upgrade issues.</span></span>  
  
 <span data-ttu-id="9bd94-116">如需有關 Upgrade Advisor 分析 Wizard 的詳細資訊，請參閱[如何：執行 Upgrade Advisor 分析 wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="9bd94-116">For more information about the Upgrade Advisor Analysis Wizard, see [How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).</span></span>  
  
 <span data-ttu-id="9bd94-117">如需每個步驟所需的特定資訊，請參閱[Upgrade Advisor 使用者介面參考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="9bd94-117">For specific information that is required for each step, see [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).</span></span>  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a><span data-ttu-id="9bd94-118">執行 Upgrade Advisor 報表檢視器</span><span class="sxs-lookup"><span data-stu-id="9bd94-118">Running the Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="9bd94-119">您可以使用 Upgrade Advisor 報表檢視器來檢視 Upgrade Advisor 分析精靈所產生的報表。</span><span class="sxs-lookup"><span data-stu-id="9bd94-119">You use the Upgrade Advisor Report Viewer to view reports generated by the Upgrade Advisor Analysis Wizard.</span></span> <span data-ttu-id="9bd94-120">載入報表時，您可以依據下列因數來篩選報表的元件：</span><span class="sxs-lookup"><span data-stu-id="9bd94-120">When the report is loaded, you can filter the components of the report by the following factors:</span></span>  
  
-   <span data-ttu-id="9bd94-121">所有問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-121">All issues</span></span>  
  
-   <span data-ttu-id="9bd94-122">所有升級的問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-122">All upgrade issues</span></span>  
  
-   <span data-ttu-id="9bd94-123">升級前的問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-123">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="9bd94-124">所有移轉的問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-124">All migration issues</span></span>  
  
-   <span data-ttu-id="9bd94-125">已解決的問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-125">Resolved issues</span></span>  
  
-   <span data-ttu-id="9bd94-126">未解決的問題</span><span class="sxs-lookup"><span data-stu-id="9bd94-126">Unresolved issues</span></span>  
  
 <span data-ttu-id="9bd94-127">如需使用報表檢視器的逐步指示，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9bd94-127">For step-by-step instructions for using the report viewer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9bd94-128">如何：檢視升級建議程式報表</span><span class="sxs-lookup"><span data-stu-id="9bd94-128">How to: View an Upgrade Advisor Report</span></span>](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [<span data-ttu-id="9bd94-129">如何：篩選報表</span><span class="sxs-lookup"><span data-stu-id="9bd94-129">How to: Filter Reports</span></span>](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [<span data-ttu-id="9bd94-130">如何：匯出報表</span><span class="sxs-lookup"><span data-stu-id="9bd94-130">How to: Export Reports</span></span>](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="9bd94-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bd94-131">See Also</span></span>  
 <span data-ttu-id="9bd94-132">[如何：執行 Upgrade Advisor 分析嚮導](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="9bd94-132">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="9bd94-133">[Upgrade Advisor 使用者介面參考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9bd94-133">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 <span data-ttu-id="9bd94-134">[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9bd94-134">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9bd94-135">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="9bd94-135">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
