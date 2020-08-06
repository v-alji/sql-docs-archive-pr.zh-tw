---
title: " (AlwaysOn 可用性群組嚮導的進度頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.progress.f1
- sql12.swb.newagwizard.progress.f1
- sql11.swb.failoverwizard.progress.f1
- sql11.swb.adddatabasewizard.progress.f1
- sql11.swb.addreplicawizard.progress.f1
- sql11.swb.newagwizard.progress.f1
- sql12.swb.adddatabasewizard.progress.f1
- sql12.swb.failoverwixard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7de8df6906d930215d71a0adc562bd7cef961ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707905"
---
# <a name="progress-page-alwayson-availability-group-wizards"></a><span data-ttu-id="7043c-102">進度頁面 (AlwaysOn 可用性群組精靈)</span><span class="sxs-lookup"><span data-stu-id="7043c-102">Progress Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="7043c-103">使用此對話方塊可以檢視您在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中執行之 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]精靈的進度。</span><span class="sxs-lookup"><span data-stu-id="7043c-103">Use this dialog box to view the progress of a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard that you are running in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7043c-104">進度列會指出精靈所執行之步驟的相對進度。</span><span class="sxs-lookup"><span data-stu-id="7043c-104">The progress bar indicates the relative progress of the steps that the wizard is performing.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7043c-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="7043c-105">UI element list</span></span>  
 <span data-ttu-id="7043c-106">**更多詳細資料**</span><span class="sxs-lookup"><span data-stu-id="7043c-106">**More details**</span></span>  
 <span data-ttu-id="7043c-107">按一下向下箭號可顯示進度方格，這個方格會依照順序列出任何已完成的步驟，接著列出目前進行中的作業。</span><span class="sxs-lookup"><span data-stu-id="7043c-107">Click the down arrow to display a progress grid that lists any completed steps, in order, followed by the current in-progress operation.</span></span> <span data-ttu-id="7043c-108">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="7043c-108">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="7043c-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7043c-109">**Name**</span></span>  
 <span data-ttu-id="7043c-110">顯示描述特定步驟的片語。</span><span class="sxs-lookup"><span data-stu-id="7043c-110">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="7043c-111">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7043c-111">**Status**</span></span>  
 <span data-ttu-id="7043c-112">指出已完成步驟的結果以及目前步驟的完成百分比，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7043c-112">Indicates the outcome of completed steps and the percentage of completion of the current step, as follows:</span></span>  
  
|<span data-ttu-id="7043c-113">結果</span><span class="sxs-lookup"><span data-stu-id="7043c-113">Result</span></span>|<span data-ttu-id="7043c-114">描述</span><span class="sxs-lookup"><span data-stu-id="7043c-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7043c-115">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="7043c-115">**Error**</span></span>|<span data-ttu-id="7043c-116">表示這個步驟的作業發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7043c-116">Indicates the operation for this step experienced an error.</span></span> <span data-ttu-id="7043c-117">按一下連結可顯示描述錯誤的訊息對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7043c-117">Click the link to display a message dialog box that describes the error.</span></span>|  
|<span data-ttu-id="7043c-118">**進行中 (** 完成百分比 **)**</span><span class="sxs-lookup"><span data-stu-id="7043c-118">**In Progress (** *percentage-completed* **)**</span></span>|<span data-ttu-id="7043c-119">表示作業目前正在進行，並且估計這個步驟已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="7043c-119">Indicates that the operation is occurring now and estimates the percentage of this step that has completed.</span></span>|  
|<span data-ttu-id="7043c-120">「成功」</span><span class="sxs-lookup"><span data-stu-id="7043c-120">**Success**</span></span>|<span data-ttu-id="7043c-121">表示這個步驟的作業已順利完成。</span><span class="sxs-lookup"><span data-stu-id="7043c-121">Indicates the operation for this step completed successfully.</span></span>|  
  
 <span data-ttu-id="7043c-122">**較少詳細資料**</span><span class="sxs-lookup"><span data-stu-id="7043c-122">**Fewer Details**</span></span>  
 <span data-ttu-id="7043c-123">按一下可隱藏進度方格。</span><span class="sxs-lookup"><span data-stu-id="7043c-123">Click to hide the progress grid.</span></span>  
  
 <span data-ttu-id="7043c-124">**取消**</span><span class="sxs-lookup"><span data-stu-id="7043c-124">**Cancel**</span></span>  
 <span data-ttu-id="7043c-125">按一下可略過任何其餘作業，然後結束精靈。</span><span class="sxs-lookup"><span data-stu-id="7043c-125">Click to skip any remaining operations and then exit the wizard.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7043c-126">相關工作</span><span class="sxs-lookup"><span data-stu-id="7043c-126">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7043c-127">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7043c-127">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="7043c-128">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="7043c-128">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="7043c-129">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7043c-129">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="7043c-130">使用容錯移轉可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7043c-130">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="7043c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7043c-131">See Also</span></span>  
 [<span data-ttu-id="7043c-132">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="7043c-132">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
