---
title: " (AlwaysOn 可用性群組嚮導) 的驗證頁面 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2010074a357932f8af7358a05ee6ed16f5c0881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585608"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a><span data-ttu-id="c6180-102">驗證頁面 (AlwaysOn 可用性群組精靈)</span><span class="sxs-lookup"><span data-stu-id="c6180-102">Validation Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="c6180-103">本說明主題描述 [驗證]\*\*\*\* 頁面的選項。</span><span class="sxs-lookup"><span data-stu-id="c6180-103">This help topic describes the options of the **Validation** page.</span></span> <span data-ttu-id="c6180-104">本主題適用於 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 的[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]、[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]和[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6180-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c6180-105">使用此頁面可以驗證環境是否支援您在精靈之先前頁面上所做的所有組態選擇。</span><span class="sxs-lookup"><span data-stu-id="c6180-105">Use this page to validate that your environment supports all the configuration choices you made on previous pages of the wizard.</span></span>  
  
##  <a name="validation-page-options"></a><a name="PageOptions"></a><span data-ttu-id="c6180-106">驗證頁面選項</span><span class="sxs-lookup"><span data-stu-id="c6180-106">Validation Page Options</span></span>  
 <span data-ttu-id="c6180-107">**可用性群組驗證的結果。**</span><span class="sxs-lookup"><span data-stu-id="c6180-107">**Results of availability group validation.**</span></span>  
 <span data-ttu-id="c6180-108">此方格會顯示每個已完成驗證步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="c6180-108">This grid displays the results of each completed validation step.</span></span> <span data-ttu-id="c6180-109">方格資料行如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6180-109">The grid columns are as follows:</span></span>  
  
 <span data-ttu-id="c6180-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c6180-110">**Name**</span></span>  
 <span data-ttu-id="c6180-111">顯示描述特定步驟的片語。</span><span class="sxs-lookup"><span data-stu-id="c6180-111">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="c6180-112">**結果**</span><span class="sxs-lookup"><span data-stu-id="c6180-112">**Result**</span></span>  
 <span data-ttu-id="c6180-113">顯示下列其中一個超連結文字。</span><span class="sxs-lookup"><span data-stu-id="c6180-113">Displays one of the following hyperlink texts.</span></span> <span data-ttu-id="c6180-114">如需有關給定驗證步驟之結果的詳細資訊，請按一下超連結。</span><span class="sxs-lookup"><span data-stu-id="c6180-114">For more information about the result of given validation step, click the hyperlink.</span></span>  
  
|<span data-ttu-id="c6180-115">結果</span><span class="sxs-lookup"><span data-stu-id="c6180-115">Result</span></span>|<span data-ttu-id="c6180-116">描述</span><span class="sxs-lookup"><span data-stu-id="c6180-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c6180-117">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="c6180-117">**Error**</span></span>|<span data-ttu-id="c6180-118">表示驗證步驟失敗。</span><span class="sxs-lookup"><span data-stu-id="c6180-118">Indicates that the validation step failed.</span></span> <span data-ttu-id="c6180-119">按一下連結可檢視錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c6180-119">Click the link to view the error message.</span></span>|  
|<span data-ttu-id="c6180-120">**已略過**</span><span class="sxs-lookup"><span data-stu-id="c6180-120">**Skipped**</span></span>|<span data-ttu-id="c6180-121">表示已略過驗證步驟，因為您的選項不需要驗證。</span><span class="sxs-lookup"><span data-stu-id="c6180-121">Indicates that the validation step was skipped because it is not required by your selections.</span></span> <span data-ttu-id="c6180-122">按一下連結可檢視略過步驟的原因。</span><span class="sxs-lookup"><span data-stu-id="c6180-122">Click the link to view the reason that a step was skipped.</span></span>|  
|<span data-ttu-id="c6180-123">「成功」</span><span class="sxs-lookup"><span data-stu-id="c6180-123">**Success**</span></span>|<span data-ttu-id="c6180-124">表示驗證步驟已順利完成。</span><span class="sxs-lookup"><span data-stu-id="c6180-124">Indicates that the validation step completed successfully</span></span>|  
|<span data-ttu-id="c6180-125">**警告**</span><span class="sxs-lookup"><span data-stu-id="c6180-125">**Warning**</span></span>|<span data-ttu-id="c6180-126">表示可用性群組組態可能有問題。</span><span class="sxs-lookup"><span data-stu-id="c6180-126">Indicates a potential issue with the availability group configuration.</span></span>  <span data-ttu-id="c6180-127">按一下連結可檢視警告訊息。</span><span class="sxs-lookup"><span data-stu-id="c6180-127">Click the link to view the warning message.</span></span>|  
  
 <span data-ttu-id="c6180-128">**重新執行驗證**</span><span class="sxs-lookup"><span data-stu-id="c6180-128">**Re-run Validation**</span></span>  
 <span data-ttu-id="c6180-129">如果您在精靈外部進行變更以回應驗證錯誤，按一下可重複驗證步驟。</span><span class="sxs-lookup"><span data-stu-id="c6180-129">Click to repeat the validation steps if you make a change outside of the wizard in response to a validation error.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c6180-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="c6180-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c6180-131">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6180-131">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="c6180-132">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="c6180-132">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="c6180-133">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6180-133">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="c6180-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6180-134">See Also</span></span>  
 [<span data-ttu-id="c6180-135">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="c6180-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
