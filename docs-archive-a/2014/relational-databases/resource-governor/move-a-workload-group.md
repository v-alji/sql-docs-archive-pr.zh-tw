---
title: 移動工作負載群組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f73b48f0ec2255760b4ee55acfaf91dc02af7cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699391"
---
# <a name="move-a-workload-group"></a><span data-ttu-id="1ea7f-102">移動工作負載群組</span><span class="sxs-lookup"><span data-stu-id="1ea7f-102">Move a Workload Group</span></span>
  <span data-ttu-id="1ea7f-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 將資源管理員工作負載群組移至不同的資源集區。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-103">You can move a Resource Governor workload group to a different resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="1ea7f-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="1ea7f-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="1ea7f-105">**若要移動工作負載群組，請使用下列方式：** [SQL Server Management Studio](#MoveWGSSMS)、[Transact-SQL](#MoveWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="1ea7f-105">**To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ea7f-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="1ea7f-106">Before You Begin</span></span>  
 <span data-ttu-id="1ea7f-107">如果有暫止的資源管理員組態作業，則無法移動工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-107">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="1ea7f-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="1ea7f-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1ea7f-109">如果有暫止的資源管理員組態作業，則無法移動工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-109">You cannot move a workload group if there is a pending Resource Governor configuration operation.</span></span> <span data-ttu-id="1ea7f-110">您可以藉由查詢 [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 動態管理檢視的方式，查看目前 is_configuration_pending 的狀況，以判斷是否有暫止的組態。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-110">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ea7f-111">權限</span><span class="sxs-lookup"><span data-stu-id="1ea7f-111">Permissions</span></span>  
 <span data-ttu-id="1ea7f-112">移動工作負載群組需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-112">Moving a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="move-a-workload-group-using-sql-server-management-studio"></a><a name="MoveWGSSMS"></a> <span data-ttu-id="1ea7f-113">使用 SQL Server Management Studio 移動工作負載群組</span><span class="sxs-lookup"><span data-stu-id="1ea7f-113">Move a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1ea7f-114">**若要使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="1ea7f-114">**To move a workload group by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**</span></span>  
  
1.  <span data-ttu-id="1ea7f-115">在 [物件總管] 中，遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-115">In Object Explorer, recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="1ea7f-116">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]，這會開啟 [資源管理員屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-116">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="1ea7f-117">在 **[資源集區]** 視窗中，按一下包含要移動之工作負載群組的資源集區。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-117">In the **Resource Pools** window, click the resource pool containing the workload group to be moved.</span></span> <span data-ttu-id="1ea7f-118">**[工作負載群組]** 視窗現在會列出該資源集區中的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-118">The **Workload Groups** window now lists the workload groups in that resource pool.</span></span>  
  
4.  <span data-ttu-id="1ea7f-119">在 [工作負載群組] 視窗中，以滑鼠右鍵按一下要移動之工作負載群組左側的向右箭頭，然後按一下 [移至]。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-119">In the **Workload Groups** window, right-click the right arrow to the left of the workload group to be moved, and click **Move to**.</span></span> <span data-ttu-id="1ea7f-120">這會顯示 **[移動工作負載群組]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-120">This displays a **Move Workload Group** window.</span></span>  
  
5.  <span data-ttu-id="1ea7f-121">可用的資源集區會顯示在此視窗中。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-121">Available resource pools are displayed in the window.</span></span> <span data-ttu-id="1ea7f-122">按一下您想要將工作負載群組移到其中的資源集區名稱，然後按一下 **[確定]** 執行此動作。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-122">Click the name of the resource pool that you want to move the workload group to, and then click **OK** to carry out this action.</span></span>  
  
6.  <span data-ttu-id="1ea7f-123">等到您按一下 **[確定]** 之後，這個動作才會完成。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-123">This action is not completed until after you click **OK**.</span></span> <span data-ttu-id="1ea7f-124">當您按一下 **[確定]** ，就會執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-124">When you click **OK**, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
7.  <span data-ttu-id="1ea7f-125">如果建立或重新設定資源集區或工作負載群組的作業失敗，在屬性頁的標題下方會出現摘要錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-125">If the create or reconfigure operation fails for the resource pool or workload group, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="1ea7f-126">若要查看詳細錯誤訊息，按一下錯誤訊息上的向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-126">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
##  <a name="move-a-workload-group-using-transact-sql"></a><a name="MoveWGTSQL"></a> <span data-ttu-id="1ea7f-127">使用 Transact-SQL 移動工作負載群組</span><span class="sxs-lookup"><span data-stu-id="1ea7f-127">Move a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="1ea7f-128">**若要使用 Transact-SQL 移動工作負載群組**</span><span class="sxs-lookup"><span data-stu-id="1ea7f-128">**To move a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="1ea7f-129">執行 `ALTER WORKLOAD GROUP` 陳述式，並指定要移動之工作負載群組的名稱以及要移入的資源集區。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-129">Run the `ALTER WORKLOAD GROUP` statement specifying the name of the workload group to be moved and the resource pool to which it should be moved.</span></span>  
  
2.  <span data-ttu-id="1ea7f-130">執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-130">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="1ea7f-131">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea7f-131">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1ea7f-132">下列範例會將名為 `groupAdhoc` 的工作負載群組移至預設資源集區。</span><span class="sxs-lookup"><span data-stu-id="1ea7f-132">The following example moves a workload group named `groupAdhoc` to the default resource pool.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ea7f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea7f-133">See Also</span></span>  
 <span data-ttu-id="1ea7f-134">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1ea7f-134">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="1ea7f-135">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="1ea7f-135">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="1ea7f-136">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="1ea7f-136">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="1ea7f-137">[建立工作負載群組](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="1ea7f-137">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="1ea7f-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1ea7f-138">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="1ea7f-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea7f-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
