---
title: 根據物件評估原則式管理原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f0de02092c87a727b723a5940805f34a75052e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597775"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a><span data-ttu-id="4d571-102">根據物件評估原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="4d571-102">Evaluate a Policy-Based Management Policy from an Object</span></span>
  <span data-ttu-id="4d571-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中根據伺服器執行個體、資料庫或資料庫物件評估原則。</span><span class="sxs-lookup"><span data-stu-id="4d571-103">This topic describes how to evaluate a policy from a server instance, database, or database object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4d571-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4d571-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d571-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4d571-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d571-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="4d571-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4d571-107">安全性</span><span class="sxs-lookup"><span data-stu-id="4d571-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d571-108">**若要使用下列項目來根據物件評估原則：**</span><span class="sxs-lookup"><span data-stu-id="4d571-108">**To evaluate a policy from an object, using:**</span></span>  
  
     [<span data-ttu-id="4d571-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d571-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d571-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="4d571-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4d571-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="4d571-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4d571-112">執行模式會定義成原則的一部分，而且無法在 **[評估原則]** 對話方塊中變更。</span><span class="sxs-lookup"><span data-stu-id="4d571-112">The execution mode is defined as part of the policy and cannot be changed in the **Evaluate Policies** dialog box.</span></span>  
  
-   <span data-ttu-id="4d571-113">**[評估原則]** 對話方塊只會顯示適用於資料庫物件的原則。</span><span class="sxs-lookup"><span data-stu-id="4d571-113">The **Evaluate Policies** dialog box only shows policies appropriate for the database object.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d571-114">Security</span><span class="sxs-lookup"><span data-stu-id="4d571-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d571-115">權限</span><span class="sxs-lookup"><span data-stu-id="4d571-115">Permissions</span></span>  
 <span data-ttu-id="4d571-116">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="4d571-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d571-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d571-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a><span data-ttu-id="4d571-118">若要根據物件評估原則</span><span class="sxs-lookup"><span data-stu-id="4d571-118">To evaluate a policy from an object</span></span>  
  
1.  <span data-ttu-id="4d571-119">在 [物件總管] 中，以滑鼠右鍵按一下伺服器執行個體、資料庫或資料庫物件、指向 [原則]\*\*\*\*，然後選取 [評估]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d571-119">In Object Explorer, right-click a server instance, a database, or a database object, point to **Policies**, and select **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="4d571-120">在 **[評估原則]** 對話方塊中，選取一個或多個原則，然後按一下 **[評估]** 以評估模式執行原則。</span><span class="sxs-lookup"><span data-stu-id="4d571-120">In the **Evaluate Policies** dialog box, select one or more policies and click **Evaluate** to run the policy in evaluation mode.</span></span> <span data-ttu-id="4d571-121">這樣會產生目標集的符合報表，但是不會重新設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或是強制未來的符合。</span><span class="sxs-lookup"><span data-stu-id="4d571-121">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span> <span data-ttu-id="4d571-122">如果目標不符合選定原則而且其屬性可透過原則式管理來重新設定，您可以按一下 [套用]\*\*\*\* 來強制符合原則。</span><span class="sxs-lookup"><span data-stu-id="4d571-122">For targets that do not comply with the selected policies and have properties that can be reconfigured by Policy-Based Management, you can enforce policy compliance by clicking **Apply**.</span></span> <span data-ttu-id="4d571-123">如需有關 **[評估原則]** 對話方塊可用之選項的詳細資訊，請參閱＜ [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md)＞、＜ [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)＞和＜ [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4d571-123">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md), and [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="4d571-124">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="4d571-124">When finished, click **Close**.</span></span>  
  
  
