---
title: 刪除工作負載群組 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699418"
---
# <a name="delete-a-workload-group"></a><span data-ttu-id="8ebee-102">刪除工作負載群組</span><span class="sxs-lookup"><span data-stu-id="8ebee-102">Delete a Workload Group</span></span>
  <span data-ttu-id="8ebee-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 刪除工作負載群組或資源集區。</span><span class="sxs-lookup"><span data-stu-id="8ebee-103">You can delete a workload group or resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="8ebee-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="8ebee-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="8ebee-105">**若要刪除工作負載群組，請使用下列方式：** [物件總管](#DelWGObjEx)、[Resource Governor 屬性](#DelWGRGProp)、[Transact-SQL](#DelWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="8ebee-105">**To delete a workload group, using:**  [Object Explorer](#DelWGObjEx), [Resource Governor Properties](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ebee-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="8ebee-106">Before You Begin</span></span>  
 <span data-ttu-id="8ebee-107">如果工作負載群組包含作用中工作階段，您就無法刪除該工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="8ebee-107">You cannot delete a workload group if it contains active sessions.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="8ebee-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="8ebee-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8ebee-109">如果工作負載群組包含使用中工作階段，當呼叫 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式以套用變更時，刪除工作負載群組或將工作負載群組移到不同的資源集區將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ebee-109">If a workload group contains active sessions, deleting or moving the workload group to a different resource pool will fail when the ALTER RESOURCE GOVERNOR RECONFIGURE statement is called to apply the change.</span></span> <span data-ttu-id="8ebee-110">若要避免這個問題，您可以採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="8ebee-110">To avoid this problem, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="8ebee-111">等到受影響之群組的所有工作階段已經中斷連接後，重新執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ebee-111">Wait until all the sessions from the affected group have disconnected, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
-   <span data-ttu-id="8ebee-112">在受影響的群組中，使用 KILL 命令明確地停止工作階段，然後重新執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ebee-112">Explicitly stop sessions in the affected group by using the KILL command, and then rerun the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span> <span data-ttu-id="8ebee-113">在您使用 [刪除] 之後但停止使用中工作階段之前，如果您決定不想要明確地停止工作階段，請使用原始名稱來重新建立群組，然後將該群組移到原始的資源集區。</span><span class="sxs-lookup"><span data-stu-id="8ebee-113">If you decide that you do not want to explicitly stop sessions after you use **Delete** but before you stop active sessions, re-create the group by using the original name and move the group to the original resource pool.</span></span>  
  
-   <span data-ttu-id="8ebee-114">重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="8ebee-114">Restart the server.</span></span> <span data-ttu-id="8ebee-115">重新啟動程序完成後，將不會建立已經刪除的群組，而且已經移動的群組將會使用新的資源集區指派。</span><span class="sxs-lookup"><span data-stu-id="8ebee-115">After the restart process is completed, the deleted group will not be created, and a moved group will use the new resource pool assignment.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8ebee-116">權限</span><span class="sxs-lookup"><span data-stu-id="8ebee-116">Permissions</span></span>  
 <span data-ttu-id="8ebee-117">刪除工作負載群組需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="8ebee-117">Deleting a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> <span data-ttu-id="8ebee-118">使用物件總管刪除工作負載群組</span><span class="sxs-lookup"><span data-stu-id="8ebee-118">Delete a Workload Group Using Object Explorer</span></span>  
 <span data-ttu-id="8ebee-119">**若要使用物件總管刪除工作負載群組**</span><span class="sxs-lookup"><span data-stu-id="8ebee-119">**To delete a workload group by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="8ebee-120">在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源集區]** 。</span><span class="sxs-lookup"><span data-stu-id="8ebee-120">In[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="8ebee-121">遞迴地向下展開 **[資源集區]** 至資源集區中的 **[工作負載群組]** 節點，此資源集區包含要刪除的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="8ebee-121">Recursively expand **Resource Pools** down to and including the **Workload Groups** node in the resource pool that contains the workload group to be deleted.</span></span>  
  
3.  <span data-ttu-id="8ebee-122">以滑鼠右鍵按一下工作負載群組，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="8ebee-122">Right-click the workload group, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="8ebee-123">在 **[刪除物件]** 視窗中，工作負載群組便列於 **[要刪除的物件]** 清單內。</span><span class="sxs-lookup"><span data-stu-id="8ebee-123">In the **Delete Object** window, the workload group is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="8ebee-124">若要刪除工作負載群組，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8ebee-124">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> <span data-ttu-id="8ebee-125">使用資源管理員屬性刪除工作負載群組</span><span class="sxs-lookup"><span data-stu-id="8ebee-125">Delete a Workload Group Using Resource Governor Properties</span></span>  
 <span data-ttu-id="8ebee-126">**若要使用資源管理員屬性頁面來刪除工作負載群組**</span><span class="sxs-lookup"><span data-stu-id="8ebee-126">**To delete a workload group by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="8ebee-127">在 [物件總管] 中，遞迴地展開 **[管理]** 節點底下，包括 **[資源集區]** 。</span><span class="sxs-lookup"><span data-stu-id="8ebee-127">In Object Explorer, recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="8ebee-128">以滑鼠右鍵按一下包含要修改之工作負載群組的資源集區，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8ebee-128">Right-click the resource pool that contains the workload group to be deleted, and then click **Properties**.</span></span> <span data-ttu-id="8ebee-129">這會開啟 **[資源管理員屬性]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="8ebee-129">This opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="8ebee-130">在 [資源集區的工作負載群組] 視窗中，按一下要刪除之工作負載群組的資料列，然後以滑鼠右鍵按一下資料列左側的向右箭頭，再按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="8ebee-130">In the **Workload groups for resource pool** window, click the line for the workload group to be deleted, then right-click the right arrow on the left side of the line, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="8ebee-131">若要刪除工作負載群組，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8ebee-131">To delete the workload group, click **OK**.</span></span>  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> <span data-ttu-id="8ebee-132">使用 Transact-SQL 刪除工作負載群組</span><span class="sxs-lookup"><span data-stu-id="8ebee-132">Delete a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="8ebee-133">**若要使用 Transact-SQL 刪除工作負載群組**</span><span class="sxs-lookup"><span data-stu-id="8ebee-133">**To delete a workload group by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="8ebee-134">執行 `DROP WORKLOAD GROUP` 陳述式，並指定要刪除之工作負載群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ebee-134">Run the `DROP WORKLOAD GROUP` statement specifying the name of the workload group to delete.</span></span>  
  
2.  <span data-ttu-id="8ebee-135">在您發出 `ALTER RESOURCE GOVERNOR RECONFIGURE` 陳述式之前，請先確認要刪除的工作負載群組中沒有任何使用中要求。</span><span class="sxs-lookup"><span data-stu-id="8ebee-135">Before you issue the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement, verify that there are no active requests in the workload group being deleted.</span></span> <span data-ttu-id="8ebee-136">如果有使用中要求，`ALTER RESOURCE GOVERNOR` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ebee-136">If there are active requests, `ALTER RESOURCE GOVERNOR` will fail.</span></span> <span data-ttu-id="8ebee-137">若要避免這個問題，您可以採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="8ebee-137">To avoid this issue, you can take one of the following actions:</span></span>  
  
    -   <span data-ttu-id="8ebee-138">等候直到工作負載群組的所有工作階段都中斷連接為止。</span><span class="sxs-lookup"><span data-stu-id="8ebee-138">Wait until all the sessions from the workload group have disconnected.</span></span>  
  
    -   <span data-ttu-id="8ebee-139">使用 `KILL` 命令來明確地停止工作負載群組中的工作階段。</span><span class="sxs-lookup"><span data-stu-id="8ebee-139">Explicitly stop sessions in the workload group by using the `KILL` command.</span></span>  
  
    -   <span data-ttu-id="8ebee-140">重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="8ebee-140">Restart the server.</span></span> <span data-ttu-id="8ebee-141">系統不會重新建立工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="8ebee-141">The workload group will not be re-created.</span></span>  
  
    -   <span data-ttu-id="8ebee-142">在您已經發出 `DROP WORKLOAD GROUP` 陳述式但決定您不要明確地停止工作階段以套用變更的案例中，您可以使用您發出 DROP 陳述式前的相同名稱重新建立群組，然後將該群組移到原始的資源集區。</span><span class="sxs-lookup"><span data-stu-id="8ebee-142">In a scenario in which you have issued the `DROP WORKLOAD GROUP` statement but decide that you do not want to explicitly stop sessions to apply the change, you can re-create the group by using the same name that it had before you issued the DROP statement, and then move the group to the original resource pool.</span></span>  
  
3.  <span data-ttu-id="8ebee-143">執行 `ALTER RESOURCE GOVERNOR RECONFIGURE` 語句。</span><span class="sxs-lookup"><span data-stu-id="8ebee-143">Run the `ALTER RESOURCE GOVERNOR RECONFIGURE` statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="8ebee-144">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebee-144">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="8ebee-145">下列範例會卸除名稱為 `groupAdhoc`的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="8ebee-145">The following example drops a workload group named `groupAdhoc`.</span></span>  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ebee-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ebee-146">See Also</span></span>  
 <span data-ttu-id="8ebee-147">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8ebee-147">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="8ebee-148">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8ebee-148">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="8ebee-149">[建立工作負載群組](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="8ebee-149">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="8ebee-150">[刪除資源集區](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8ebee-150">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="8ebee-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ebee-151">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="8ebee-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ebee-152">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="8ebee-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8ebee-153">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
