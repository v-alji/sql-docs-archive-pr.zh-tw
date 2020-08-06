---
title: 依照排程評估原則式管理原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f1c6b1a7d13d14c02f4b4e537c2dbdb2df39d02c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699460"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a><span data-ttu-id="8273e-102">依照排程評估原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="8273e-102">Evaluate a Policy-Based Management Policy on a Schedule</span></span>
  <span data-ttu-id="8273e-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中依照排程評估原則式管理原則。</span><span class="sxs-lookup"><span data-stu-id="8273e-103">This topic describes how to evaluate a Policy-Based Management policy on a schedule in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8273e-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8273e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8273e-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8273e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8273e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="8273e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8273e-107">**若要使用下列項目來依照排程評估原則：**</span><span class="sxs-lookup"><span data-stu-id="8273e-107">**To evaluate a policy on a schedule, using:**</span></span>  
  
     [<span data-ttu-id="8273e-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8273e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8273e-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="8273e-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8273e-110">Security</span><span class="sxs-lookup"><span data-stu-id="8273e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8273e-111">權限</span><span class="sxs-lookup"><span data-stu-id="8273e-111">Permissions</span></span>  
 <span data-ttu-id="8273e-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="8273e-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8273e-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8273e-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a><span data-ttu-id="8273e-114">若要依照排程評估原則</span><span class="sxs-lookup"><span data-stu-id="8273e-114">To evaluate a policy on a schedule</span></span>  
  
1.  <span data-ttu-id="8273e-115">在 **[物件總管]** 中，按一下加號，展開包含您想要評估之原則排程的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8273e-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy schedule that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="8273e-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8273e-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="8273e-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="8273e-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="8273e-118">按一下加號展開 **[原則]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8273e-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="8273e-119">以滑鼠右鍵按一下您想要評估其排程的原則，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="8273e-119">Right-click the policy whose schedule you what to evaluate and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="8273e-120">在 [開啟原則 -_policy_name_] 對話方塊的 [評估模式] 清單中，選取 [按排程時間]。</span><span class="sxs-lookup"><span data-stu-id="8273e-120">On the **Open Policy -**_policy_name_ dialog box, in the **Evaluation Mode** list, select **On schedule**.</span></span>  
  
7.  <span data-ttu-id="8273e-121">在 **[排程]** 底下，按一下 **[挑選]** 指定現有的排程，或按一下 **[新增]** 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="8273e-121">Under **Schedule**, click either **Pick** to specify an existing schedule or **New** to create a new schedule.</span></span>  
  
8.  <span data-ttu-id="8273e-122">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8273e-122">When finished, click **OK**.</span></span>  
  
  
