---
title: Upgrade Advisor 進度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b504b8f1c8392ad2cf55837dc65bbb2f019d6f48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595413"
---
# <a name="upgrade-advisor-progress"></a><span data-ttu-id="75d7a-102">Upgrade Advisor 進度</span><span class="sxs-lookup"><span data-stu-id="75d7a-102">Upgrade Advisor Progress</span></span>
  <span data-ttu-id="75d7a-103">Upgrade Advisor 分析會以專用分析器開始，以便針對您所選取每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件執行分析。</span><span class="sxs-lookup"><span data-stu-id="75d7a-103">Upgrade Advisor analysis starts with a dedicated analyzer that performs an analysis of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that you selected.</span></span> <span data-ttu-id="75d7a-104">分析元件時，會在 [**進度**] 對話方塊中報告進度。</span><span class="sxs-lookup"><span data-stu-id="75d7a-104">As components are analyzed, progress is reported in the **Progress** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75d7a-105">選項</span><span class="sxs-lookup"><span data-stu-id="75d7a-105">Options</span></span>  
 <span data-ttu-id="75d7a-106">**動作**</span><span class="sxs-lookup"><span data-stu-id="75d7a-106">**Action**</span></span>  
 <span data-ttu-id="75d7a-107">指定選取要分析的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="75d7a-107">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component that is selected for analysis.</span></span>  
  
 <span data-ttu-id="75d7a-108">**狀態**</span><span class="sxs-lookup"><span data-stu-id="75d7a-108">**Status**</span></span>  
 <span data-ttu-id="75d7a-109">顯示從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件進度介面傳回的狀態值。</span><span class="sxs-lookup"><span data-stu-id="75d7a-109">Displays the status value returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component progress interface.</span></span>  
  
 <span data-ttu-id="75d7a-110">**Message**</span><span class="sxs-lookup"><span data-stu-id="75d7a-110">**Message**</span></span>  
 <span data-ttu-id="75d7a-111">顯示從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 個別分析器傳回的錯誤、失敗或成功訊息。</span><span class="sxs-lookup"><span data-stu-id="75d7a-111">Displays error, failure, or success messages returned from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] individual analyzer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75d7a-112">如果分析所需時間過長，您可以停止分析、結束 Upgrade Advisor 分析精靈，然後重新執行精靈。</span><span class="sxs-lookup"><span data-stu-id="75d7a-112">If the analysis is taking too long, you can stop the analysis, exit the Upgrade Advisor Analysis Wizard, and then rerun the wizard.</span></span> <span data-ttu-id="75d7a-113">若要縮短分析時間，請選取更少的元件進行掃描。</span><span class="sxs-lookup"><span data-stu-id="75d7a-113">To reduce analysis time, select fewer components to scan.</span></span>  
  
 <span data-ttu-id="75d7a-114">分析完成時，報表會寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="75d7a-114">When analysis is complete, the report is written to a file.</span></span> <span data-ttu-id="75d7a-115">您可以按一下 [**啟動報表**]，從這個頁面啟動報表檢視器，以查看報表。</span><span class="sxs-lookup"><span data-stu-id="75d7a-115">You can view the report by clicking **Launch Report** to launch the report viewer from this page.</span></span> <span data-ttu-id="75d7a-116">如果您想要稍後再查看報表，您可以從 Upgrade Advisor 開始頁面開啟**Upgrade Advisor 報表檢視器**。</span><span class="sxs-lookup"><span data-stu-id="75d7a-116">If you want to view the report later, you can open the **Upgrade Advisor Report Viewer** from the Upgrade Advisor start page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75d7a-117">每次您分析伺服器時，系統會儲存先前的報表。</span><span class="sxs-lookup"><span data-stu-id="75d7a-117">Previous reports are saved every time you analyze a server.</span></span> <span data-ttu-id="75d7a-118">這些報表使用時間戳記做為檔案名稱進行儲存。</span><span class="sxs-lookup"><span data-stu-id="75d7a-118">The reports are saved using the timestamp for the file name.</span></span> <span data-ttu-id="75d7a-119">報表檢視器會顯示最近儲存的五個報表。</span><span class="sxs-lookup"><span data-stu-id="75d7a-119">The report viewer displays the latest five saved reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d7a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75d7a-120">See Also</span></span>  
 <span data-ttu-id="75d7a-121">[如何：啟動 Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="75d7a-121">[How to: Launch Upgrade Advisor](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="75d7a-122">[如何：執行 Upgrade Advisor 分析嚮導](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="75d7a-122">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="75d7a-123">[SQL Server 元件](../../../2014/sql-server/install/sql-server-components.md) </span><span class="sxs-lookup"><span data-stu-id="75d7a-123">[SQL Server Components](../../../2014/sql-server/install/sql-server-components.md) </span></span>  
 <span data-ttu-id="75d7a-124">[Upgrade Advisor 使用者介面參考](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span><span class="sxs-lookup"><span data-stu-id="75d7a-124">[Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md) </span></span>  
 [<span data-ttu-id="75d7a-125">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="75d7a-125">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
