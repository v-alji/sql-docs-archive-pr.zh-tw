---
title: 修改資源健康狀態原則定義 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.UTILITY.ADMINISTRATION.F1
ms.assetid: 27bec0b6-92e9-448e-8c70-fe36802cf128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d2651a2dd0b4994a6dacaad6c01d3f1ec68c98e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595967"
---
# <a name="modify-a-resource-health-policy-definition-sql-server-utility"></a><span data-ttu-id="2ff43-102">修改資源健康情況原則定義 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="2ff43-102">Modify a Resource Health Policy Definition (SQL Server Utility)</span></span>
  <span data-ttu-id="2ff43-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 來修改 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的資源健全狀況原則定義。</span><span class="sxs-lookup"><span data-stu-id="2ff43-103">This topic describes how to modify a resource health policy definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2ff43-104">在您於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內修改資源使用量原則之前，您必須先建立公用程式控制點 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="2ff43-104">Before you modify a resource utilization policy in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="2ff43-105">如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="2ff43-105">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2ff43-106">您可以針對資料層應用程式和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]受管理的執行個體設定公用程式資源使用率原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-106">Utility resource utilization policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2ff43-107">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對所有資料層應用程式和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體以全域方式定義資源使用率原則，也可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對每一個資料層應用程式及每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體個別定義原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-107">Resource utilization policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="2ff43-108">您也可以實作全域原則，並讓個別的資料層應用程式或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體設定自己的原則定義。</span><span class="sxs-lookup"><span data-stu-id="2ff43-108">You can also implement global policies and have individual data-tier applications or managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configured with their own policy definitions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ff43-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ff43-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="modify-global-resource-utilization-policies-in-a-sql-server-utility"></a><span data-ttu-id="2ff43-110">在 SQL Server 公用程式中修改全域資源使用量原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-110">Modify global resource utilization policies in a SQL Server Utility.</span></span>  
  
1.  <span data-ttu-id="2ff43-111">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 UCP。</span><span class="sxs-lookup"><span data-stu-id="2ff43-111">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ff43-112">在 [公用程式總管] 導覽窗格中，按一下 **[公用程式管理]** 來檢視或修改全域監視原則，然後在 [公用程式總管] 內容窗格中按一下 **[原則]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2ff43-112">In the Utility Explorer navigation pane, click **Utility Administration** to view or modify global monitoring policies, then click the **Policy** tab in the Utility Explorer content pane.</span></span>  
  
3.  <span data-ttu-id="2ff43-113">在公用程式總管內容窗格中，按一下箭頭或原則描述來選取 [Set global data-tier monitoring policies (設定全域資料層監視原則)] 或 [Set global managed instance monitoring policies (設定全域受管理的執行個體監視原則)]。</span><span class="sxs-lookup"><span data-stu-id="2ff43-113">In the Utility Explorer content pane, select **Set global data-tier monitoring policies** or **Set global managed instance monitoring policies** by clicking on the arrow or the policy description.</span></span>  
  
4.  <span data-ttu-id="2ff43-114">您可以使用原則描述右邊的控制項來設定使用量過高或使用量過低原則的臨界值。</span><span class="sxs-lookup"><span data-stu-id="2ff43-114">Use the controls on the right side of the policy descriptions to set underutilization or overutilization policy thresholds.</span></span>  
  
5.  <span data-ttu-id="2ff43-115">視需要使用 [套用] 、[捨棄] 或 [還原預設值]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2ff43-115">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="2ff43-116">原則變更最多需要花上 15 分鐘的時間傳回到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式儀表板及清單檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2ff43-116">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
6.  <span data-ttu-id="2ff43-117">若要重新整理資料，請以滑鼠右鍵按一下公用程式總管功能窗格中的 [公用程式管理] 節點，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="2ff43-117">To refresh data, right-click on the **Utility Administration** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
#### <a name="modify-resource-health-policy-definitions-for-an-individual-data-tier-application-or-an-individual-managed-instance-of-sql-server-in-a-sql-server-utility"></a><span data-ttu-id="2ff43-118">在 SQL Server 公用程式中，針對個別的資料層應用程式或個別的 SQL Server 受管理的執行個體，修改其資源健全狀況原則定義。</span><span class="sxs-lookup"><span data-stu-id="2ff43-118">Modify resource health policy definitions for an individual data-tier application or an individual managed instance of SQL Server in a SQL Server Utility</span></span>  
  
1.  <span data-ttu-id="2ff43-119">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 UCP。</span><span class="sxs-lookup"><span data-stu-id="2ff43-119">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ff43-120">在公用程式總管功能窗格中，按一下 [部署的資料層應用程式] 或按一下 [受管理的執行個體]，檢視或修改個別資料層應用程式或受管理的執行個體的監視原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-120">In the Utility Explorer navigation pane, click **Deployed Date-tier Applications**, or click **Managed Instances**, to view or modify monitoring policies for an individual data-tier application or managed instance.</span></span>  
  
3.  <span data-ttu-id="2ff43-121">在公用程式總管內容窗格清單檢視中，按一下您想要修改原則的資料層應用程式或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱，然後按一下 [原則詳細資料] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2ff43-121">In the Utility Explorer content pane list view, click the data-tier application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name whose policies you would like to modify, then click on the **Policy Details** tab.</span></span>  
  
4.  <span data-ttu-id="2ff43-122">按一下箭頭或原則描述，選取要檢視或修改的原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-122">Select the policy to view or modify by clicking on the arrow or the policy description.</span></span> <span data-ttu-id="2ff43-123">預設會選取全域原則。</span><span class="sxs-lookup"><span data-stu-id="2ff43-123">Global policies are selected by default.</span></span>  
  
5.  <span data-ttu-id="2ff43-124">選取 [覆寫全域原則] 的選項按鈕，針對指定的資料層應用程式來覆寫全域原則及實作個別的原則定義。</span><span class="sxs-lookup"><span data-stu-id="2ff43-124">Select the radio button to **Override the global policy** to override global policies and implement an individual policy definition for the specified data-tier application.</span></span>  
  
6.  <span data-ttu-id="2ff43-125">您可以使用原則描述右邊的控制項來設定使用量過高或使用量過低原則的臨界值。</span><span class="sxs-lookup"><span data-stu-id="2ff43-125">Use the controls on the right side of the policy description to set underutilization or overutilization policy thresholds.</span></span>  
  
7.  <span data-ttu-id="2ff43-126">視需要使用 [套用] 、[捨棄] 或 [還原預設值]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2ff43-126">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="2ff43-127">原則變更最多需要花上 15 分鐘的時間傳回到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式儀表板及清單檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2ff43-127">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
8.  <span data-ttu-id="2ff43-128">若要重新整理資料，請以滑鼠右鍵按一下公用程式總管功能窗格中的 [部署的資料層應用程式] 節點，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="2ff43-128">To refresh data, right-click on the **Deployed Data-tier Applications** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff43-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ff43-129">See Also</span></span>  
 <span data-ttu-id="2ff43-130">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="2ff43-130">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="2ff43-131">檢視資源健全狀況原則結果 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="2ff43-131">View Resource Health Policy Results &#40;SQL Server Utility&#41;</span></span>](view-resource-health-policy-results-sql-server-utility.md)  
  
  
