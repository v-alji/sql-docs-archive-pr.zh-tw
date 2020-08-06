---
title: 權限或安全性實體頁面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.permissions.f1
- sql12.swb.SecurableAndEffectPermissions.f1
- sql12.swb.availabilitygroupproperties.permission.f1
- sql12.swb.common.columnperm.f1
- sql12.swb.SecurableAndEffectivePermission.f1
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80417c720258833850f07eb67f83f5c47f487ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697714"
---
# <a name="permissions-or-securables-page"></a><span data-ttu-id="f6985-102">權限或安全性實體頁面</span><span class="sxs-lookup"><span data-stu-id="f6985-102">Permissions or Securables Page</span></span>
  <span data-ttu-id="f6985-103">使用 **[權限]** 頁面或 **[安全性實體]** 頁面可檢視或設定安全性實體的權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-103">Use the **Permissions** page or the **Securables** page to view or set the permissions for securables.</span></span> <span data-ttu-id="f6985-104">您可以從許多位置開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="f6985-104">This page can be opened from many locations.</span></span> <span data-ttu-id="f6985-105">此頁面的內容會隨著開啟頁面的方式以及頁面中包含的內容而稍有不同。</span><span class="sxs-lookup"><span data-stu-id="f6985-105">The contents of the page can change slightly, depending on how the page is opened and what it contains.</span></span> <span data-ttu-id="f6985-106">當頁面開啟時，頁面的上層方格可能會填入資料或是空白。</span><span class="sxs-lookup"><span data-stu-id="f6985-106">The top grid of the page might be populated when the page opens, or it might be empty.</span></span> <span data-ttu-id="f6985-107">若要在上方格中加入項目，請按一下 **[搜尋]** 。</span><span class="sxs-lookup"><span data-stu-id="f6985-107">To add items to the upper grid, click **Search**.</span></span> <span data-ttu-id="f6985-108">在上方格中選取項目，然後在 **[明確]** 索引標籤上設定適當的權限。若要檢視彙總的權限，請使用 **[有效]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f6985-108">In the upper grid, select an item, and then set the appropriate permissions on the **Explicit** tab. To view aggregated permissions, use the **Effective** tab.</span></span>  
  
 <span data-ttu-id="f6985-109">若要了解安全性實體和主體的可能組合，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 主題中安全性實體特有的語法連結。</span><span class="sxs-lookup"><span data-stu-id="f6985-109">To understand the possible combinations of securables and principals, see the securable-specific syntax links in the topic [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="f6985-110">如需相關資訊，請參閱 [Securables](securables.md)。</span><span class="sxs-lookup"><span data-stu-id="f6985-110">For more information, see [Securables](securables.md).</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="f6985-111">頁首</span><span class="sxs-lookup"><span data-stu-id="f6985-111">Page Header</span></span>  
 <span data-ttu-id="f6985-112">**[權限]** 或 **[安全性實體]** 頁面的標頭會隨著安全性實體或主體而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f6985-112">The header of the **Permissions** or **Securables** page varies depending on the securable or principal.</span></span> <span data-ttu-id="f6985-113">此頁面顯示項目相關的資訊，例如名稱。</span><span class="sxs-lookup"><span data-stu-id="f6985-113">It displays information relevant to the item, such as its name.</span></span>  
  
## <a name="upper-grid"></a><span data-ttu-id="f6985-114">上方格</span><span class="sxs-lookup"><span data-stu-id="f6985-114">Upper Grid</span></span>  
 <span data-ttu-id="f6985-115">上方格包含一或多個可以設定權限的項目。</span><span class="sxs-lookup"><span data-stu-id="f6985-115">The upper grid contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="f6985-116">此對話方塊提供 **[搜尋]** 按鈕，供您選取要加入上方格的物件或主體。</span><span class="sxs-lookup"><span data-stu-id="f6985-116">This dialog box provides the **Search** button for selecting objects or principals to add to the upper grid.</span></span> <span data-ttu-id="f6985-117">此方格的名稱可能會顯示 **[安全性實體]** 或是安全性實體或主體的一或多個類型。</span><span class="sxs-lookup"><span data-stu-id="f6985-117">The name of the grid might display **Securables** or one or more types of securables or principals.</span></span> <span data-ttu-id="f6985-118">顯示在上方格中的資料行會隨著主體或安全性實體而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f6985-118">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="f6985-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f6985-119">**Name**</span></span>  
 <span data-ttu-id="f6985-120">加入此方格的每一個主體或安全性實體名稱。</span><span class="sxs-lookup"><span data-stu-id="f6985-120">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="f6985-121">**型別**</span><span class="sxs-lookup"><span data-stu-id="f6985-121">**Type**</span></span>  
 <span data-ttu-id="f6985-122">描述每個項目的類型。</span><span class="sxs-lookup"><span data-stu-id="f6985-122">Describes the type of each item.</span></span>  
  
## <a name="explicit-tab"></a><span data-ttu-id="f6985-123">明確索引標籤</span><span class="sxs-lookup"><span data-stu-id="f6985-123">Explicit Tab</span></span>  
 <span data-ttu-id="f6985-124">**[明確]** 索引標籤會列出上方格中選取之安全性實體的可能權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-124">The **Explicit** tab lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="f6985-125">若要設定權限，請選取或清除 [授與] \(或 [允許])、[可授與] 和 [拒絕] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f6985-125">To configure the permissions, select or clear the **Grant** (or **Allow**), **With Grant**, and **Deny** check boxes.</span></span> <span data-ttu-id="f6985-126">所有選項不適用於所有明確權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-126">All options are not available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="f6985-127">**權限**</span><span class="sxs-lookup"><span data-stu-id="f6985-127">**Permissions**</span></span>  
 <span data-ttu-id="f6985-128">權限的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6985-128">The name of the permission.</span></span>  
  
 <span data-ttu-id="f6985-129">**授與者**</span><span class="sxs-lookup"><span data-stu-id="f6985-129">**Grantor**</span></span>  
 <span data-ttu-id="f6985-130">授與權限的主體。</span><span class="sxs-lookup"><span data-stu-id="f6985-130">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="f6985-131">**授與**</span><span class="sxs-lookup"><span data-stu-id="f6985-131">**Grant**</span></span>  
 <span data-ttu-id="f6985-132">選取此選項即可授與此權限給登入。</span><span class="sxs-lookup"><span data-stu-id="f6985-132">Select to grant this permission to the login.</span></span> <span data-ttu-id="f6985-133">清除此選項即可撤銷這個權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-133">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="f6985-134">**使用授與**</span><span class="sxs-lookup"><span data-stu-id="f6985-134">**With Grant**</span></span>  
 <span data-ttu-id="f6985-135">反映出所列權限之 WITH GRANT 選項的狀態。</span><span class="sxs-lookup"><span data-stu-id="f6985-135">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="f6985-136">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f6985-136">This box is read-only.</span></span> <span data-ttu-id="f6985-137">若要套用此權限，請使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f6985-137">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="f6985-138">**拒絕**</span><span class="sxs-lookup"><span data-stu-id="f6985-138">**Deny**</span></span>  
 <span data-ttu-id="f6985-139">選取此選項即可拒絕授與此權限給登入。</span><span class="sxs-lookup"><span data-stu-id="f6985-139">Select to deny this permission to the login.</span></span> <span data-ttu-id="f6985-140">清除此選項即可撤銷這個權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-140">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="f6985-141">**資料行權限**</span><span class="sxs-lookup"><span data-stu-id="f6985-141">**Column Permissions**</span></span>  
 <span data-ttu-id="f6985-142">如果是包含資料行的物件 (如資料表、檢視表或資料表值函數)，[資料行權限] 按鈕會開啟 [資料行權限] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6985-142">For objects that contain columns (such as tables, views, or table-valued functions), the **Column Permissions** button opens the **Column Permissions** dialog box.</span></span> <span data-ttu-id="f6985-143">在此對話方塊中，您可以針對資料表或檢視表的個別資料行設定 **[授與]** 、 **[允許]** 或 **[拒絕]** 權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-143">In this dialog box, you can set **Grant**, **Allow**, or **Deny** permissions on individual columns of a table or view.</span></span> <span data-ttu-id="f6985-144">並非所有物件類型或權限都可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="f6985-144">This option is not available for all object types or permissions.</span></span>  
  
## <a name="effective-tab"></a><span data-ttu-id="f6985-145">有效索引標籤</span><span class="sxs-lookup"><span data-stu-id="f6985-145">Effective Tab</span></span>  
 <span data-ttu-id="f6985-146">主體所擁有而且與安全性實體有關的權限可能來自於針對幾個不同主體所設定的權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-146">The permissions that a principal has related to a securable may come from permissions that are set for several different principals.</span></span> <span data-ttu-id="f6985-147">例如，可個別為登入授與權限，而登入也可以是某個群組的成員。</span><span class="sxs-lookup"><span data-stu-id="f6985-147">For example, a login might be granted permissions individually and also as a member of a group.</span></span> <span data-ttu-id="f6985-148">**[有效]** 索引標籤會顯示結合明確權限以及從群組或角色成員資格取得之權限的結果。</span><span class="sxs-lookup"><span data-stu-id="f6985-148">The **Effective** tab shows the result of combining explicit permissions and the permissions that are received from group or role memberships.</span></span> <span data-ttu-id="f6985-149">授與的權限會經過彙總。</span><span class="sxs-lookup"><span data-stu-id="f6985-149">Grant permissions are aggregated.</span></span> <span data-ttu-id="f6985-150">拒絕權限會覆寫所有授與權限。</span><span class="sxs-lookup"><span data-stu-id="f6985-150">A deny permission overrides all grant permissions.</span></span>  
  
 <span data-ttu-id="f6985-151">**權限**</span><span class="sxs-lookup"><span data-stu-id="f6985-151">**Permissions**</span></span>  
 <span data-ttu-id="f6985-152">權限的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6985-152">The name of the permission.</span></span>  
  
 <span data-ttu-id="f6985-153">**資料行**</span><span class="sxs-lookup"><span data-stu-id="f6985-153">**Column**</span></span>  
 <span data-ttu-id="f6985-154">受到權限影響的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f6985-154">The names of columns that are affected by the permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6985-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6985-155">See Also</span></span>  
 <span data-ttu-id="f6985-156">[資料庫層級角色](authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="f6985-156">[Database-Level Roles](authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="f6985-157">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="f6985-157">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
