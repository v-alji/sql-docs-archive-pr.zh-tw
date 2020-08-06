---
title: '[選取資料庫] 頁面 (新增可用性組嚮導-加入資料庫 Wizard) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c626b8f0953f18a6dd4661124a09b7f542caeb82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707893"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a><span data-ttu-id="683f3-102">[選取資料庫] 頁面 (新增可用性組嚮導-加入資料庫 Wizard) </span><span class="sxs-lookup"><span data-stu-id="683f3-102">Select Databases Page (New Availability Group Wizard-Add Database Wizard)</span></span>
  <span data-ttu-id="683f3-103"> 本描述主題描述 [指定資料庫\]\*\*\** 頁面的選項。</span><span class="sxs-lookup"><span data-stu-id="683f3-103">This help topic describes the options of the **Specify Databases** page.</span></span> <span data-ttu-id="683f3-104">此主題適用於 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 的 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 和 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="683f3-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a> <span data-ttu-id="683f3-105">選取資料庫選項</span><span class="sxs-lookup"><span data-stu-id="683f3-105">Select Databases Options</span></span>  
 <span data-ttu-id="683f3-106">**[這個 SQL Server 執行個體上的使用者資料庫]** 方格會列出每個本機使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="683f3-106">The **User databases on this instance of SQL Server** grid lists every local user database.</span></span> <span data-ttu-id="683f3-107">資料行如下：</span><span class="sxs-lookup"><span data-stu-id="683f3-107">The columns are as follows:</span></span>  
  
 <span data-ttu-id="683f3-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="683f3-108">**Name**</span></span>  
 <span data-ttu-id="683f3-109">顯示本機使用者資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="683f3-109">Displays the name of a local user database.</span></span>  
  
 <span data-ttu-id="683f3-110">**大小**</span><span class="sxs-lookup"><span data-stu-id="683f3-110">**Size**</span></span>  
 <span data-ttu-id="683f3-111">顯示資料庫大小 (如果精靈可使用大小)。</span><span class="sxs-lookup"><span data-stu-id="683f3-111">Displays the database size, if the size is available to the wizard.</span></span>  
  
 <span data-ttu-id="683f3-112">**狀態**</span><span class="sxs-lookup"><span data-stu-id="683f3-112">**Status**</span></span>  
 <span data-ttu-id="683f3-113">顯示超連結，其文字指出給定的資料庫是否符合加入可用性群組的必要條件。</span><span class="sxs-lookup"><span data-stu-id="683f3-113">Displays a hyperlink whose text that indicates whether a given database meets the prerequisites for being added to an availability group.</span></span> <span data-ttu-id="683f3-114">如果狀態為 **[符合必要條件]**，表示您可以將此資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="683f3-114">If the status is "**Meets prerequisites**" you can add the database to the availability group.</span></span> <span data-ttu-id="683f3-115">如果資料庫不符合所有必要條件， **[狀態]** 超連結會提供為什麼資料庫不合格的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="683f3-115">If a database does not meet all of the prerequisites, the **Status** hyperlink provides a brief explanation of why the database is ineligible.</span></span> <span data-ttu-id="683f3-116">如需詳細資訊，請按一下此超連結。</span><span class="sxs-lookup"><span data-stu-id="683f3-116">For more information, click the hyperlink.</span></span>  
  
 <span data-ttu-id="683f3-117">對資料庫採取動作以符合必要條件時，您可以離開精靈的 **[選取資料庫]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="683f3-117">You can leave the wizard on the **Select Database** page while you take action on a database to meet a prerequisite.</span></span> <span data-ttu-id="683f3-118">當您返回 **[選取資料庫]** 頁面時，請按一下 **[重新整理]** 更新方格。</span><span class="sxs-lookup"><span data-stu-id="683f3-118">When you return to the **Select Databases** page, click **Refresh** to update the grid.</span></span>  
  
 <span data-ttu-id="683f3-119">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="683f3-119">**Refresh**</span></span>  
 <span data-ttu-id="683f3-120">按一下以重新整理方格。</span><span class="sxs-lookup"><span data-stu-id="683f3-120">Click to refresh the grid.</span></span> <span data-ttu-id="683f3-121">對資料庫採取動作以符合必要條件之後，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="683f3-121">This is useful after you take action on a database to meet a prerequisite.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="683f3-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="683f3-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="683f3-123">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="683f3-123">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="683f3-124">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="683f3-124">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="683f3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="683f3-125">See Also</span></span>  
 <span data-ttu-id="683f3-126">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="683f3-126">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="683f3-127">AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;</span><span class="sxs-lookup"><span data-stu-id="683f3-127">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
