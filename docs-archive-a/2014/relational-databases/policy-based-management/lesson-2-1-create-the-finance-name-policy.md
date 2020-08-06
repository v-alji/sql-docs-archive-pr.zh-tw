---
title: 建立 Finance Name 原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 44ffff45f126d2ad9b73c5b8410b8f89ad2b0604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591963"
---
# <a name="create-the-finance-name-policy"></a><span data-ttu-id="019bc-102">建立 Finance Name 原則</span><span class="sxs-lookup"><span data-stu-id="019bc-102">Create the Finance Name Policy</span></span>
  <span data-ttu-id="019bc-103"> 在這項工作中，您將會建立名為 Finance 的資料庫，然後建立要求所有資料表都以字母 **fintbl** 為開頭的條件。</span><span class="sxs-lookup"><span data-stu-id="019bc-103">In this task, you will create a database named Finance, and then create a condition that requires all tables to start with the letters **fintbl**.</span></span> <span data-ttu-id="019bc-104">接著，您將會建立原則和原則類別目錄，以便針對 Finance 資料庫中的資料表強制執行命名標準。</span><span class="sxs-lookup"><span data-stu-id="019bc-104">Then, you will create a policy and policy category to enforce a naming standard for tables in the Finance database.</span></span>  
  
### <a name="to-create-the-finance-database"></a><span data-ttu-id="019bc-105">建立 Finance 資料庫</span><span class="sxs-lookup"><span data-stu-id="019bc-105">To create the Finance database</span></span>  
  
1.  <span data-ttu-id="019bc-106">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，開啟查詢視窗並執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="019bc-106">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window and execute the following statement:</span></span>  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  <span data-ttu-id="019bc-107">在物件總管中，按一下 [資料庫]\*\*\*\*，然後按下 F5 重新整理資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="019bc-107">In Object Explorer, click **Databases**, and then press F5 to refresh the list of databases.</span></span>  
  
### <a name="to-create-the-finance-tables-condition"></a><span data-ttu-id="019bc-108">建立 Finance Tables 條件</span><span class="sxs-lookup"><span data-stu-id="019bc-108">To create the Finance Tables condition</span></span>  
  
1.  <span data-ttu-id="019bc-109">在物件總管中，依序展開 [管理]\*\*\*\* 和 [原則管理]\*\*\*\*，以滑鼠右鍵按一下 [條件]\*\*\*\*，然後按一下 [新增條件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-109">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Conditions**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="019bc-110">在 [建立新條件]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **Finance Tables**。</span><span class="sxs-lookup"><span data-stu-id="019bc-110">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Tables**.</span></span>  
  
3.  <span data-ttu-id="019bc-111">在 [Facet]\*\*\*\* 清單中，選取 [多部分名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-111">In the **Facet** list, select **Multipart Name**.</span></span>  
  
4.  <span data-ttu-id="019bc-112">在 [**運算式**] 區域的 [**欄位**] 方塊中，選取 [ \*\* \@ 名稱**]; 在 [**運算子**] 方塊中，選取 [ **Like**]，然後在 [**值**] 方塊中輸入 **' fintbl 為開頭% '** ，強制所有資料表名稱的開頭都是字母**fintbl 為開頭\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-112">In the **Expression** area, in the **Field** box, select **\@Name**; in the **Operator** box, select **Like**; and in the **Value** box, type **'fintbl%'** to force all table names to start with the letters **fintbl**.</span></span>  
  
5.  <span data-ttu-id="019bc-113">在 [描述]\*\*\*\* 頁面上，輸入**財務資料表名稱的開頭必須是 fintbl**，然後按一下 [確定]\*\*\*\* 建立條件。</span><span class="sxs-lookup"><span data-stu-id="019bc-113">On the **Description** page, type **Finance table names must begin with fintbl**, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-finance-name-policy"></a><span data-ttu-id="019bc-114">建立 Finance Name 原則</span><span class="sxs-lookup"><span data-stu-id="019bc-114">To create the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="019bc-115">在物件總管中，以滑鼠右鍵按一下 [原則]\*\*\*\*，然後按一下 [新增原則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-115">In Object Explorer, right-click **Policies**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="019bc-116">在 [建立新原則]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **Finance Name**。</span><span class="sxs-lookup"><span data-stu-id="019bc-116">In the **Create New Policy** dialog box, in the **Name** box, type **Finance Name**.</span></span>  
  
3.  <span data-ttu-id="019bc-117">在 [檢查條件]\*\*\*\* 清單中，選取 [Finance Tables]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-117">In the **Check condition** list, select **Finance Tables**.</span></span> <span data-ttu-id="019bc-118">這會位於 [多部分名稱]\*\*\*\* 區域中。</span><span class="sxs-lookup"><span data-stu-id="019bc-118">This is in the **Multipart Name** area.</span></span>  
  
4.  <span data-ttu-id="019bc-119">在 [針對]\*\*\*\* 區域中，您將會看見可套用此原則的資料庫物件清單。</span><span class="sxs-lookup"><span data-stu-id="019bc-119">In the **Against** area you will see a list of the database objects that could apply this policy.</span></span> <span data-ttu-id="019bc-120">選取 [每份資料表]\*\*\*\* 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="019bc-120">Select the check box for **Every Table**.</span></span>  
  
5.  <span data-ttu-id="019bc-121">在 [每個資料庫]\*\*\*\* 區域中，展開 [全部]\*\*\*\*，然後按一下 [新增條件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-121">In the **Every Database** area, expand **Every**, and then click **New condition**.</span></span>  
  
6.  <span data-ttu-id="019bc-122">在 [建立新條件]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **Finance Database**。</span><span class="sxs-lookup"><span data-stu-id="019bc-122">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Database**.</span></span>  
  
7.  <span data-ttu-id="019bc-123">在 [**運算式**] 方塊中，完成運算式以包含\*\* \@ Name = ' 財務 '\*\*，然後按一下 **[確定]** 以關閉 [條件] 頁面。</span><span class="sxs-lookup"><span data-stu-id="019bc-123">In the **Expression** box, complete the expression to include **\@Name = 'Finance'**, and then click **OK** to close the condition page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="019bc-124">您可能必須按下 TAB 鍵跳離 [值]\*\*\*\* 方塊，才能啟用 [確定]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="019bc-124">You might have to tab out of the **Value** box to enable the **OK** button.</span></span>  
  
8.  <span data-ttu-id="019bc-125">在 [評估模式]\*\*\*\* 清單中，選取 [變更時: 避免]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-125">In the **Evaluation Mode** list, select **On change: prevent**.</span></span> <span data-ttu-id="019bc-126">這樣就會透過在 Finance 資料庫上建立資料庫觸發程序，強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="019bc-126">This will enforce the policy by creating a database trigger on the Finance database.</span></span>  
  
9. <span data-ttu-id="019bc-127">選取 [已啟用]\*\*\*\* 清單</span><span class="sxs-lookup"><span data-stu-id="019bc-127">Select the **Enabled** list.</span></span> <span data-ttu-id="019bc-128">([已啟用]\*\*\*\* 方塊不會套用至 [視需要]\*\*\*\* 原則)。</span><span class="sxs-lookup"><span data-stu-id="019bc-128">(The **Enabled** box does not apply to **On demand** policies.)</span></span>  
  
10. <span data-ttu-id="019bc-129">在 [伺服器限制]\*\*\*\* 清單中，選取 [無]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-129">In the **Server restriction** list, select **None**.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a><span data-ttu-id="019bc-130">建立 Finance 原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="019bc-130">To create the Finance policy category</span></span>  
  
1.  <span data-ttu-id="019bc-131">在物件總管中，展開 [管理]\*\*\*\*，以滑鼠右鍵按一下 [原則管理]\*\*\*\*，然後按一下 [管理類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="019bc-131">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="019bc-132">在 [**管理原則類別目錄**] 對話方塊中，于 [**名稱**] 底下 `Finance` 的空白方塊中輸入，然後清除 [託管**資料庫訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="019bc-132">In the **Manage Policy Categories** dialog box, under **Name**, type `Finance` in the blank box, and then clear **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="019bc-133">[託管資料庫訂閱]\*\*\*\* 將會強制執行個體中的每一個資料庫訂閱屬於這個原則類別目錄的原則。</span><span class="sxs-lookup"><span data-stu-id="019bc-133">**Mandate Database Subscriptions** will force every database in the instance to subscribe to the policies that belong to this policy category.</span></span> <span data-ttu-id="019bc-134">基於這個理由，只有 Finance 資料庫應該訂閱 Finance Name 原則。</span><span class="sxs-lookup"><span data-stu-id="019bc-134">For this lesson, only the Finance database should subscribe to the Finance Name policy.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="019bc-135">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="019bc-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="019bc-136">訂閱和檢查 Finance Name 原則</span><span class="sxs-lookup"><span data-stu-id="019bc-136">Subscribe to and Check the Finance Name Policy</span></span>](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
