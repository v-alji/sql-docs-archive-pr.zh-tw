---
title: 變更資源集區設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2183cceaaf8a3e183d96c154075f9a922942c2c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697879"
---
# <a name="change-resource-pool-settings"></a><span data-ttu-id="8fcda-102">變更資源集區設定</span><span class="sxs-lookup"><span data-stu-id="8fcda-102">Change Resource Pool Settings</span></span>
  <span data-ttu-id="8fcda-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]來變更資源集區設定。</span><span class="sxs-lookup"><span data-stu-id="8fcda-103">You can change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="8fcda-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="8fcda-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="8fcda-105">**若要變更資源集區的設定，請使用下列方式：** [SQL Server Management Studio](#ChgRPProp)、[Transact-SQL](#ChgRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="8fcda-105">**To change the settings for a resource pool, using:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8fcda-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="8fcda-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="8fcda-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="8fcda-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8fcda-108">最大 CPU 百分比必須大於或等於最小 CPU 百分比。</span><span class="sxs-lookup"><span data-stu-id="8fcda-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="8fcda-109">最大記憶體百分比必須大於或等於最小記憶體百分比。</span><span class="sxs-lookup"><span data-stu-id="8fcda-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="8fcda-110">所有資源集區之最小 CPU 百分比和最小記憶體百分比的總和不得超過 100。</span><span class="sxs-lookup"><span data-stu-id="8fcda-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8fcda-111">權限</span><span class="sxs-lookup"><span data-stu-id="8fcda-111">Permissions</span></span>  
 <span data-ttu-id="8fcda-112">變更資源集區設定需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="8fcda-112">Changing resource pool settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-resource-pool-settings-using-sql-server-management-studio"></a><a name="ChgRPProp"></a> <span data-ttu-id="8fcda-113">使用 SQL Server Management Studio 變更資源集區設定</span><span class="sxs-lookup"><span data-stu-id="8fcda-113">Change Resource Pool Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8fcda-114">**若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="8fcda-114">**To change resource pool settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="8fcda-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 [管理]  節點至 [資源集區] 。</span><span class="sxs-lookup"><span data-stu-id="8fcda-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Pools**.</span></span>  
  
2.  <span data-ttu-id="8fcda-116">以滑鼠右鍵按一下要修改的資源集區，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8fcda-116">Right-click the resource pool to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="8fcda-117">在 **[資源管理員屬性]** 頁面的 **[資源集區]** 方格中，選取資源集區的資料列 (如果系統沒有自動選取的話)。</span><span class="sxs-lookup"><span data-stu-id="8fcda-117">In the **Resource Governor Properties** page, select the row for the resource pool in the **Resource pools** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="8fcda-118">在資料列中按一下或按兩下要變更的資料格，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="8fcda-118">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="8fcda-119">若要儲存變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8fcda-119">To save the changes, click **OK**</span></span>  
  
##  <a name="change-resource-pool-settings-using-transact-sql"></a><a name="ChgRPTSQL"></a> <span data-ttu-id="8fcda-120">使用 Transact-SQL 變更資源集區設定</span><span class="sxs-lookup"><span data-stu-id="8fcda-120">Change Resource Pool Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="8fcda-121">**若要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="8fcda-121">**To change resource pool settings by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="8fcda-122">執行 `ALTER RESOURCE POOL` 陳述式，並指定要變更的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8fcda-122">Run the `ALTER RESOURCE POOL` statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="8fcda-123">執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8fcda-123">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="8fcda-124">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8fcda-124">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="8fcda-125">下列範例會變更名為 `poolAdhoc`的資源集區的最大 CPU 百分比設定。</span><span class="sxs-lookup"><span data-stu-id="8fcda-125">The following example changes the max CPU percentage setting for the resource pool named `poolAdhoc`.</span></span>  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fcda-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fcda-126">See Also</span></span>  
 <span data-ttu-id="8fcda-127">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-127">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="8fcda-128">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-128">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="8fcda-129">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-129">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="8fcda-130">[刪除資源集區](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-130">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="8fcda-131">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-131">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="8fcda-132">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="8fcda-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="8fcda-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8fcda-133">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="8fcda-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8fcda-134">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
