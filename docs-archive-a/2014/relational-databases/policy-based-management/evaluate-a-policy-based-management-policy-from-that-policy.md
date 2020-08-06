---
title: 根據原則式管理原則評估該原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 207c86f1465c49238fc9b50ee75489b43d956caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597777"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a><span data-ttu-id="ce9b9-102">根據原則式管理原則評估該原則</span><span class="sxs-lookup"><span data-stu-id="ce9b9-102">Evaluate a Policy-Based Management Policy from That Policy</span></span>
  <span data-ttu-id="ce9b9-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用某個原則來評估該原則。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-103">This topic describes how to evaluate a policy using that policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ce9b9-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ce9b9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ce9b9-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ce9b9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ce9b9-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ce9b9-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ce9b9-107">**若要使用下列項目來評估原則：**</span><span class="sxs-lookup"><span data-stu-id="ce9b9-107">**To evaluate a policy, using:**</span></span>  
  
     [<span data-ttu-id="ce9b9-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ce9b9-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ce9b9-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="ce9b9-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ce9b9-110">Security</span><span class="sxs-lookup"><span data-stu-id="ce9b9-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ce9b9-111">權限</span><span class="sxs-lookup"><span data-stu-id="ce9b9-111">Permissions</span></span>  
 <span data-ttu-id="ce9b9-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ce9b9-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ce9b9-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy"></a><span data-ttu-id="ce9b9-114">若要評估原則</span><span class="sxs-lookup"><span data-stu-id="ce9b9-114">To evaluate a policy</span></span>  
  
1.  <span data-ttu-id="ce9b9-115">在 **[物件總管]** 中，按一下加號，展開包含您想要評估之原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="ce9b9-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ce9b9-117">按一下加號展開 **[原則管理]**。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="ce9b9-118">按一下加號展開 **[原則]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="ce9b9-119">以滑鼠右鍵按一下您想要評估的原則，然後選取 [評估]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-119">Right-click the policy that you want to evaluate and select **Evaluate**.</span></span>  
  
6.  <span data-ttu-id="ce9b9-120">在 **[評估結果]**  對話方塊中，您可以查看原則評估的結果。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-120">In the **Evaluate Results**  dialog box, you see the results of the policy evaluation.</span></span> <span data-ttu-id="ce9b9-121">如果目標不符合此原則而且其屬性可透過原則式管理來重新設定，您可以按一下 [套用]\*\*\*\* 來強制符合原則。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-121">For targets that do not comply with the policy and have properties that can be reconfigured by Policy-Based Management, you can enforce compliance by clicking **Apply**.</span></span> <span data-ttu-id="ce9b9-122">如需有關 **[評估原則]** 對話方塊中之可用選項的詳細資訊，請參閱＜ [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) ＞和＜ [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-122">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) and [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).</span></span>  
  
7.  <span data-ttu-id="ce9b9-123">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-123">When finished, click **Close**.</span></span>  
  
  
