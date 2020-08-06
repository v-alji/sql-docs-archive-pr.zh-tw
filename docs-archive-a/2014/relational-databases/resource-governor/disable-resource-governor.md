---
title: 停用資源管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 172f01bdde0f792cd9ed72ad371e5811b8de8885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699403"
---
# <a name="disable-resource-governor"></a><span data-ttu-id="09917-102">停用資源管理員</span><span class="sxs-lookup"><span data-stu-id="09917-102">Disable Resource Governor</span></span>
  <span data-ttu-id="09917-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 停用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="09917-103">You can disable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="09917-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="09917-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="09917-105">**若要停用 Resource Governor，請使用下列方式：** [物件總管](#RGOffObjEx)、[Resource Governor 屬性](#RGOffProp)、[Transact-SQL](#RGOffTSQL)</span><span class="sxs-lookup"><span data-stu-id="09917-105">**To disable Resource Governorn, using:**  [Object Explorer](#RGOffObjEx), [Resource Governor Properties](#RGOffProp), [Transact-SQL](#RGOffTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="09917-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="09917-106">Before You Begin</span></span>  
 <span data-ttu-id="09917-107">停用資源管理員會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="09917-107">Disabling the Resource Governor has the following results:</span></span>  
  
-   <span data-ttu-id="09917-108">系統不會執行分類函數。</span><span class="sxs-lookup"><span data-stu-id="09917-108">The classifier function is not run.</span></span>  
  
-   <span data-ttu-id="09917-109">所有新的連接都會自動分類至預設工作負載群組中。</span><span class="sxs-lookup"><span data-stu-id="09917-109">All new connections are automatically classified into the default workload group.</span></span>  
  
-   <span data-ttu-id="09917-110">系統起始的要求會分類至內部工作負載群組中。</span><span class="sxs-lookup"><span data-stu-id="09917-110">System-initiated requests are classified into the internal workload group.</span></span>  
  
-   <span data-ttu-id="09917-111">所有現有的工作負載群組和資源集區設定都會重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="09917-111">All existing workload group and resource pool settings are reset to their default values.</span></span> <span data-ttu-id="09917-112">在此情況下，如果到達限制，系統將不會引發任何事件。</span><span class="sxs-lookup"><span data-stu-id="09917-112">In this case, no events are fired when limits are reached.</span></span>  
  
-   <span data-ttu-id="09917-113">一般的系統監視不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="09917-113">Normal system monitoring is not affected.</span></span>  
  
-   <span data-ttu-id="09917-114">您可以變更組態，但這些變更在資源管理員啟用之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="09917-114">Configuration changes can be made, but the changes do not take effect until the Resource Governor is enabled.</span></span>  
  
-   <span data-ttu-id="09917-115">一旦重新啟動 SQL Server 之後，資源管理員將不會載入其組態，而是只有預設和內部工作負載群組與資源集區。</span><span class="sxs-lookup"><span data-stu-id="09917-115">Upon restarting SQL Server, the Resource Governor will not load its configuration, but instead will have only the default and internal workload groups and resource pools.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="09917-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="09917-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="09917-117">在使用者交易中時，您無法使用 `ALTER RESOURCE GOVERNOR` 陳述式停用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="09917-117">You cannot use the `ALTER RESOURCE GOVERNOR` statement to disable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="09917-118">權限</span><span class="sxs-lookup"><span data-stu-id="09917-118">Permissions</span></span>  
 <span data-ttu-id="09917-119">停用資源管理員需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="09917-119">Disabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="disable-resource-governor-using-object-explorer"></a><a name="RGOffObjEx"></a> <span data-ttu-id="09917-120">使用物件總管停用資源管理員</span><span class="sxs-lookup"><span data-stu-id="09917-120">Disable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="09917-121">**若要使用物件總管停用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="09917-121">**To disable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="09917-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="09917-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="09917-123">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [停用]。</span><span class="sxs-lookup"><span data-stu-id="09917-123">Right-click **Resource Governor**, and then click **Disable**.</span></span>  
  
##  <a name="disable-resource-governor-using-resource-governor-properties"></a><a name="RGOffProp"></a> <span data-ttu-id="09917-124">使用資源管理員屬性停用資源管理員</span><span class="sxs-lookup"><span data-stu-id="09917-124">Disable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="09917-125">**若要使用資源管理員屬性頁面來停用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="09917-125">**To disable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="09917-126">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="09917-126">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="09917-127">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]，這會開啟 [資源管理員屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="09917-127">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="09917-128">按一下 **[啟用資源管理員]** 核取方塊，確定未選取方塊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="09917-128">Click the **Enable Resource Governor** check box, ensure that the box is not selected, and then click **OK**.</span></span>  
  
##  <a name="disable-resource-governor-using-transact-sql"></a><a name="RGOffTSQL"></a> <span data-ttu-id="09917-129">使用 Transact-SQL 停用資源管理員</span><span class="sxs-lookup"><span data-stu-id="09917-129">Disable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="09917-130">**若要使用 Transact-SQL 停用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="09917-130">**To disable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="09917-131">執行 **ALTER RESOURCE GOVERNOR DISABLE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="09917-131">Run the **ALTER RESOURCE GOVERNOR DISABLE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="09917-132">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09917-132">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="09917-133">下列範例會啟用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="09917-133">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="09917-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09917-134">See Also</span></span>  
 <span data-ttu-id="09917-135">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="09917-135">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="09917-136">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="09917-136">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="09917-137">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="09917-137">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="09917-138">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="09917-138">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="09917-139">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="09917-139">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="09917-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09917-140">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
