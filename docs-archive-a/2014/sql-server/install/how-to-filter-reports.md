---
title: 如何：篩選報表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Upgrade Advisor], filtering
- filtering reports [Reporting Services]
ms.assetid: bc3dbe16-f6c1-4f07-8d88-2b8e86302c7e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4946b9ea208c0fad98426b7c7fc4247cfaa47680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606050"
---
# <a name="how-to-filter-reports"></a><span data-ttu-id="e0303-102">如何：篩選報表</span><span class="sxs-lookup"><span data-stu-id="e0303-102">How to: Filter Reports</span></span>
  <span data-ttu-id="e0303-103">此主題描述如何使用 Upgrade Advisor 報表檢視器，將篩選套用至報表。</span><span class="sxs-lookup"><span data-stu-id="e0303-103">This topic describes how you can use the Upgrade Advisor Report Viewer to apply filters to a report.</span></span>  
  
### <a name="to-filter-reports"></a><span data-ttu-id="e0303-104">篩選報表</span><span class="sxs-lookup"><span data-stu-id="e0303-104">To filter reports</span></span>  
  
1.  <span data-ttu-id="e0303-105">在報表檢視器中，顯示您想要篩選的報表。</span><span class="sxs-lookup"><span data-stu-id="e0303-105">In the report viewer, display the report that you want to filter.</span></span> <span data-ttu-id="e0303-106">如需指示，請參閱[如何：查看 Upgrade Advisor 報表](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)。</span><span class="sxs-lookup"><span data-stu-id="e0303-106">For instructions, see [How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md).</span></span>  
  
2.  <span data-ttu-id="e0303-107">在 [**篩選依據**] 清單中，選取要查看的問題類型：</span><span class="sxs-lookup"><span data-stu-id="e0303-107">In the **Filter by** list, select a type of issue to view:</span></span>  
  
    -   <span data-ttu-id="e0303-108">**所有問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-108">**All issues**.</span></span> <span data-ttu-id="e0303-109">這會顯示尚未標示為已解決的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-109">This displays all issues that have not been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="e0303-110">**所有升級問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-110">**All upgrade issues**.</span></span> <span data-ttu-id="e0303-111">這會顯示與升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 相關的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-111">This displays all issues that are related to upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="e0303-112">**升級前的問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-112">**Pre-upgrade issues**.</span></span> <span data-ttu-id="e0303-113">這會顯示應該或必須在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前修正的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-113">This displays all issues that should or must be fixed before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="e0303-114">**所有的遷移問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-114">**All migration issues**.</span></span> <span data-ttu-id="e0303-115">這會顯示與移轉資料或應用程式至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 相關的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-115">This displays all issues that are related to migrating data or applications to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="e0303-116">**已解決的問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-116">**Resolved Issues**.</span></span> <span data-ttu-id="e0303-117">這會顯示已經標示為已解決的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-117">This displays all issues that have been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="e0303-118">**未解決的問題**。</span><span class="sxs-lookup"><span data-stu-id="e0303-118">**Unresolved Issues**.</span></span> <span data-ttu-id="e0303-119">這會顯示尚未解決的所有問題。</span><span class="sxs-lookup"><span data-stu-id="e0303-119">This displays all issues that have not yet been resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0303-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0303-120">See Also</span></span>  
 <span data-ttu-id="e0303-121">[如何：執行 Upgrade Advisor 分析嚮導](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e0303-121">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="e0303-122">[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e0303-122">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="e0303-123">[Upgrade Advisor 的 how to 主題](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="e0303-123">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="e0303-124">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="e0303-124">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
