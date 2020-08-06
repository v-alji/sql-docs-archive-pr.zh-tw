---
title: 維護計畫 (管理連接) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b6b9f0c1652ead2f21567634b758ce81485b47b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594531"
---
# <a name="maintenance-plan-manage-connections"></a><span data-ttu-id="86b0b-102">維護計畫 (管理連接)</span><span class="sxs-lookup"><span data-stu-id="86b0b-102">Maintenance Plan (Manage Connections)</span></span>
  <span data-ttu-id="86b0b-103">使用 **[管理連接]** 對話方塊，來指定維護計畫所用的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="86b0b-103">Use the **Manage Connections** dialog box to specify the properties of connections used by maintenance plans.</span></span> <span data-ttu-id="86b0b-104">建立維護計畫時，會在建立此計畫的伺服器建立本機連接。</span><span class="sxs-lookup"><span data-stu-id="86b0b-104">When you create a maintenance plan, a local connection to the server where you created the plan is created.</span></span> <span data-ttu-id="86b0b-105">使用此連接即可建立工作 (Task)，在本機連接上執行工作 (Work)。</span><span class="sxs-lookup"><span data-stu-id="86b0b-105">Use this connection to create tasks that perform work on this local connection.</span></span> <span data-ttu-id="86b0b-106">需要時，請使用 **[管理連接]** 對話方塊將它們加入。</span><span class="sxs-lookup"><span data-stu-id="86b0b-106">When needed, use the **Manage Connections** dialog box to add them.</span></span> <span data-ttu-id="86b0b-107">設定其他連接時，它們會出現在每個工作的連接方塊中。</span><span class="sxs-lookup"><span data-stu-id="86b0b-107">When additional connections are configured they appear in the connections box for each task.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86b0b-108">選項。</span><span class="sxs-lookup"><span data-stu-id="86b0b-108">Options</span></span>  
 <span data-ttu-id="86b0b-109">**Server**</span><span class="sxs-lookup"><span data-stu-id="86b0b-109">**Server**</span></span>  
 <span data-ttu-id="86b0b-110">伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="86b0b-110">The server instance.</span></span>  
  
 <span data-ttu-id="86b0b-111">**驗證**</span><span class="sxs-lookup"><span data-stu-id="86b0b-111">**Authentication**</span></span>  
 <span data-ttu-id="86b0b-112">指出是以 Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="86b0b-112">Indicates whether the connection is made with Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b0b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b0b-113">See Also</span></span>  
 [<span data-ttu-id="86b0b-114">維護計畫</span><span class="sxs-lookup"><span data-stu-id="86b0b-114">Maintenance Plans</span></span>](maintenance-plans.md)  
  
  
