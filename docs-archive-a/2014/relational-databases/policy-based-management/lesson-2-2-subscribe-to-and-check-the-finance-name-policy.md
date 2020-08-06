---
title: 訂閱和檢查 Finance Name 原則 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2bfe6f463d03fe8b95f000dc6f34dc0718a7729f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585337"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a><span data-ttu-id="48442-102">訂閱和檢查 Finance Name 原則</span><span class="sxs-lookup"><span data-stu-id="48442-102">Subscribe to and Check the Finance Name Policy</span></span>
  <span data-ttu-id="48442-103">在這項工作中，您會將 Finance 資料庫設定為訂閱 Finance 原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="48442-103">In this task, you will configure the Finance database to subscribe to the Finance policy category.</span></span> <span data-ttu-id="48442-104">然後，您將測試 Finance Name 原則。</span><span class="sxs-lookup"><span data-stu-id="48442-104">Then, you will test the Finance Name policy.</span></span>  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a><span data-ttu-id="48442-105">訂閱 Finance 原則類別目錄</span><span class="sxs-lookup"><span data-stu-id="48442-105">To subscribe to the Finance policy category</span></span>  
  
1.  <span data-ttu-id="48442-106">在物件總管中，展開 [**資料庫**]，以滑鼠右鍵按一下 `Finance` ，指向 [**原則**]，然後按一下 [**類別**]。</span><span class="sxs-lookup"><span data-stu-id="48442-106">In Object Explorer, expand **Databases**, right-click `Finance`, point to **Policies**, and then click **Categories**.</span></span>  
  
2.  <span data-ttu-id="48442-107">針對類別目錄選取 [已**訂閱**] 核取方塊 `Finance` 。</span><span class="sxs-lookup"><span data-stu-id="48442-107">Select the **Subscribed** checkbox for the `Finance` category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a><span data-ttu-id="48442-108">測試 Finance Name 原則的強制執行</span><span class="sxs-lookup"><span data-stu-id="48442-108">To test the enforcement of the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="48442-109">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，開啟查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="48442-109">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window.</span></span> <span data-ttu-id="48442-110">執行下列陳述式，以便嘗試建立違反 **Finance Name** 原則的資料表。</span><span class="sxs-lookup"><span data-stu-id="48442-110">Execute the following statements that try to create a table that violates the **Finance Name** policy.</span></span> <span data-ttu-id="48442-111">此資料表違反了原則，因為資料表名稱並未以字母 **fintbl**為開頭。</span><span class="sxs-lookup"><span data-stu-id="48442-111">The table violates the policy because the table name does not begin with the letters **fintbl**.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="48442-112">請注意，這個原則會讓您無法建立資料表，並且傳回提供原則名稱的參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="48442-112">Notice that the policy prevents the table from being created and returns an informational message that provides the policy name.</span></span>  
  
2.  <span data-ttu-id="48442-113">若要提供有效的名稱，請依照下列內容修改程式碼並再次執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="48442-113">To provide a valid name, modify the code as follows and run the statement again.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="48442-114">這次就會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="48442-114">This time, the table is created.</span></span>  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a><span data-ttu-id="48442-115">將原則套用至整個伺服器</span><span class="sxs-lookup"><span data-stu-id="48442-115">To apply the policy to the whole server</span></span>  
  
1.  <span data-ttu-id="48442-116">目前，只有 Finance 資料庫訂閱 Finance 原則類別目錄。</span><span class="sxs-lookup"><span data-stu-id="48442-116">Currently, only the Finance database subscribes to the Finance policy category.</span></span> <span data-ttu-id="48442-117">在許多情況下，將原則類別目錄套用至整個伺服器是比較簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="48442-117">In many cases, it is easier to apply the policy category to the whole server.</span></span> <span data-ttu-id="48442-118">在物件總管中，展開 [管理]\*\*\*\*，以滑鼠右鍵按一下 [原則管理]\*\*\*\*，然後按一下 [管理類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48442-118">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="48442-119">在 [管理原則類別目錄]\*\*\*\* 對話方塊中，找出 Finance 類別目錄，然後針對 Finance 類別目錄選取 [託管資料庫訂閱]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="48442-119">In the **Manage Policy Categories** dialog box, locate the Finance category, and select the **Mandate Database Subscriptions** checkbox for the Finance category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="48442-120">此時，Finance 類別目錄會套用至所有資料庫，但是您已建立的條件會將 Finance Name 原則限制為 Finance 資料庫。</span><span class="sxs-lookup"><span data-stu-id="48442-120">Now the Finance category applies to all databases, but the condition that you have created restricts the Finance Name policy to the Finance database.</span></span> <span data-ttu-id="48442-121">這點就說明了如何以將在許多伺服器上正確套用的方式，使用複雜的條件組合來建立原則的目標。</span><span class="sxs-lookup"><span data-stu-id="48442-121">This shows how you can use complex combinations of conditions to target policies in ways that will apply correctly on many servers.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="48442-122">總結</span><span class="sxs-lookup"><span data-stu-id="48442-122">Summary</span></span>  
 <span data-ttu-id="48442-123">這個教學課程已經示範了如何建立以原則為基礎的管理條件、原則和原則群組，以及如何套用篩選和檢查以原則為基礎的管理目標是否符合。</span><span class="sxs-lookup"><span data-stu-id="48442-123">This tutorial has shown you how to create Policy-Based Management conditions, policies and policy groups, and how to apply filters and check the compliance of Policy-Based Management targets.</span></span>  
  
## <a name="next"></a><span data-ttu-id="48442-124">下一個</span><span class="sxs-lookup"><span data-stu-id="48442-124">Next</span></span>  
 <span data-ttu-id="48442-125">本教學課程已完成。</span><span class="sxs-lookup"><span data-stu-id="48442-125">This tutorial is finished.</span></span> <span data-ttu-id="48442-126">若要返回開頭，請按一下 [教學課程：使用以原則為基礎的管理來管理伺服器](tutorial-administering-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="48442-126">To return to the start, click [Tutorial: Administering Servers by Using Policy-Based Management](tutorial-administering-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="48442-127">如需教學課程的清單，請參閱[SQL Server 2014 的教學](../../tutorials/tutorials-for-sql-server-2014.md)課程。</span><span class="sxs-lookup"><span data-stu-id="48442-127">For a list of tutorials, see [Tutorials for SQL Server 2014](../../tutorials/tutorials-for-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48442-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48442-128">See Also</span></span>  
 [<span data-ttu-id="48442-129">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="48442-129">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
