---
title: 維護計畫 (伺服器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c971edc9b641846068313f47ca410715ec552014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594527"
---
# <a name="maintenance-plan-servers"></a><span data-ttu-id="19dce-102">維護計畫 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="19dce-102">Maintenance Plan (Servers)</span></span>
  <span data-ttu-id="19dce-103">使用 **[伺服器]** 對話方塊可選取要執行維護計畫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="19dce-103">Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.</span></span>  
  
 <span data-ttu-id="19dce-104">若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="19dce-104">A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan.</span></span> <span data-ttu-id="19dce-105">針對多伺服器維護計畫，本機伺服器應設為主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="19dce-105">For multiserver maintenance plans, the local server should be configured as a master server.</span></span> <span data-ttu-id="19dce-106">在多伺服器環境中，這個對話方塊會顯示 **(本機)** 主要伺服器以及所有相對應的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="19dce-106">In multiserver environments, this dialog box displays the **(local)** master server and all corresponding target servers.</span></span> <span data-ttu-id="19dce-107">本機伺服器會建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="19dce-107">One [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created for the local server.</span></span> <span data-ttu-id="19dce-108">這會視您是否選取 **(本機)** 伺服器而啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="19dce-108">It is enabled or disabled depending on whether you select the **(local)** server.</span></span> <span data-ttu-id="19dce-109">如果選取目標伺服器，會建立多伺服器作業並下載到每個選取的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="19dce-109">If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers.</span></span> <span data-ttu-id="19dce-110">如果沒有選取目標伺服器，會刪除多伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="19dce-110">If no target servers are selected, the multiserver job is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dce-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19dce-111">See Also</span></span>  
 <span data-ttu-id="19dce-112">[維護計畫](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="19dce-112">[Maintenance Plans](maintenance-plans.md) </span></span>  
 <span data-ttu-id="19dce-113">[建立多伺服器環境](../../ssms/agent/create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="19dce-113">[Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="19dce-114">[設為主要伺服器](../../ssms/agent/make-a-master-server.md) </span><span class="sxs-lookup"><span data-stu-id="19dce-114">[Make a Master Server](../../ssms/agent/make-a-master-server.md) </span></span>  
 [<span data-ttu-id="19dce-115">設為目標伺服器</span><span class="sxs-lookup"><span data-stu-id="19dce-115">Make a Target Server</span></span>](../../ssms/agent/make-a-target-server.md)  
  
  
