---
title: SQL Server 複寫發行者屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701047"
---
# <a name="sql-server-replication-publisher-properties"></a><span data-ttu-id="ed5cc-102">SQL Server 複寫發行者屬性</span><span class="sxs-lookup"><span data-stu-id="ed5cc-102">SQL Server Replication Publisher Properties</span></span>
  <span data-ttu-id="ed5cc-103">本節包含散發者端和發行者端可用之發行者屬性的資訊。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-103">This section contains information on Publisher properties available at the Distributor and the Publisher.</span></span> 

## <a name="general"></a><span data-ttu-id="ed5cc-104">一般</span><span class="sxs-lookup"><span data-stu-id="ed5cc-104">General</span></span>  
  <span data-ttu-id="ed5cc-105"> [發行者屬性\]\*\*\** 對話方塊的 [一般\]\*\*\** 頁面，會顯示散發者與發行者所使用之散發資料庫的唯讀資訊。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-105">The **General** page of the **Publisher Properties** dialog box displays read-only information on the Distributor and distribution database that the Publisher uses.</span></span> <span data-ttu-id="ed5cc-106">若要變更散發者或發行者的散發資料庫：</span><span class="sxs-lookup"><span data-stu-id="ed5cc-106">To change the Distributor or distribution database for a Publisher:</span></span>  
  
1.  <span data-ttu-id="ed5cc-107">在發行者上停用發行。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-107">Disable publishing on the Publisher.</span></span> <span data-ttu-id="ed5cc-108">如需詳細資訊，請參閱[停用發行和散發](disable-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-108">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>    
2.  <span data-ttu-id="ed5cc-109">重新設定發行和散發。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-109">Reconfigure publishing and distribution.</span></span> <span data-ttu-id="ed5cc-110">如需詳細資訊，請參閱 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  

## <a name="distributor"></a><span data-ttu-id="ed5cc-111">散發者</span><span class="sxs-lookup"><span data-stu-id="ed5cc-111">Distributor</span></span>
  <span data-ttu-id="ed5cc-112"> [發行者屬性\]\*\*\** 對話方塊可讓您檢視和修改與發行者及其散發者之間的關聯性建立關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-112">The **Publisher Properties** dialog box allows you to view and modify properties associated with the relationship between the Publisher and its Distributor.</span></span>  
  
### <a name="options"></a><span data-ttu-id="ed5cc-113">選項</span><span class="sxs-lookup"><span data-stu-id="ed5cc-113">Options</span></span>  
 <span data-ttu-id="ed5cc-114">**代理程式至發行者的連接**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-114">**Agent Connection to the Publisher**</span></span>  
 <span data-ttu-id="ed5cc-115">指定下列代理程式用來從散發者連接到發行者的內容。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-115">Specify the context under which the following agents make connections from the Distributor to the Publisher:</span></span>  
  
-   <span data-ttu-id="ed5cc-116">允許佇列更新訂閱之交易式發行集的佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-116">The Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="ed5cc-117">Oracle 發行集的快照集代理程式和記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-117">The Snapshot Agent and Log Reader Agent for Oracle publications.</span></span>  
  
 <span data-ttu-id="ed5cc-118">選取 **[模擬代理程式處理帳戶]** 來使用執行這些代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶連接到發行者，或指定 **[SQL Server 驗證]**，然後輸入 **[登入]** 和 **[密碼]** 的值。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-118">Select **Impersonate agent process account** to make connections to the Publisher using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which these agents run, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> <span data-ttu-id="ed5cc-119">建議您選取 **[模擬代理程式處理帳戶]**。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-119">It is recommended that you select **Impersonate agent process account**.</span></span> <span data-ttu-id="ed5cc-120">如需代理程式安全性的詳細資訊，請參閱[複寫代理程式安全性模型](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-120">For more information on agent security, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="ed5cc-121">執行這些代理程式的 Windows 帳戶會在新增發行集精靈中指定。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-121">The Windows accounts under which these agents run are specified in the New Publication Wizard.</span></span> <span data-ttu-id="ed5cc-122">可以在下列位置變更這些帳戶：</span><span class="sxs-lookup"><span data-stu-id="ed5cc-122">These accounts can be changed:</span></span>  
  
-   <span data-ttu-id="ed5cc-123">在佇列讀取器代理程式的 **[散發者屬性]** 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-123">In the **Distributor Properties** dialog box for the Queue Reader Agent.</span></span>  
  
-   <span data-ttu-id="ed5cc-124">在快照集代理程式和記錄讀取器代理程式的 **[發行集屬性]** 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-124">In the **Publication Properties** dialog box for the Snapshot Agent and Log Reader Agent.</span></span>  
  
 <span data-ttu-id="ed5cc-125">**其他**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-125">**Miscellaneous**</span></span>  
 <span data-ttu-id="ed5cc-126">屬性 **[發行者類型]** 和 **[散發資料庫名稱]** 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-126">The properties **Publisher Type** and **Distribution Database Name** are read-only.</span></span> <span data-ttu-id="ed5cc-127">可以變更屬性 **[預設快照集資料夾]** 。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-127">The property **Default Snapshot Folder** can be changed.</span></span> <span data-ttu-id="ed5cc-128">如需快照集資料夾的詳細資訊，請參閱[保護快照集資料夾](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-128">For more information about the snapshot folder, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  

## <a name="publication-databases"></a><span data-ttu-id="ed5cc-129">發行集資料庫</span><span class="sxs-lookup"><span data-stu-id="ed5cc-129">Publication Databases</span></span>
  <span data-ttu-id="ed5cc-130">**[發行者屬性]** 對話方塊的 **[發行集資料庫]** 頁面，可讓 **系統管理員 (sysadmin)** 固定伺服器角色中的使用者啟用資料庫供複寫。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-130">The **Publication Databases** page of the **Publisher Properties** dialog box allows a user in the **sysadmin** fixed server role to enable databases for replication.</span></span> <span data-ttu-id="ed5cc-131">啟用資料庫不會發行此資料庫；不過，它允許該資料庫之 **db_owner** 固定資料庫角色中的任何使用者在資料庫上建立一個或多個發行集。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-131">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications on the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="ed5cc-132">選項</span><span class="sxs-lookup"><span data-stu-id="ed5cc-132">Options</span></span>  
 <span data-ttu-id="ed5cc-133">**異動**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-133">**Transactional**</span></span>  
 <span data-ttu-id="ed5cc-134">選取此核取方塊即可讓 **db_owner** 固定資料庫角色中的使用者，在資料庫中建立快照式發行集或交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-134">Select this check box to allow users in the **db_owner** fixed database role to create snapshot publications or transactional publications in the database.</span></span> 
  
 <span data-ttu-id="ed5cc-135">**合併式**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-135">**Merge**</span></span>  
 <span data-ttu-id="ed5cc-136">選取此核取方塊即可讓 **db_owner** 固定資料庫角色中的使用者，在資料庫中建立合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-136">Select this check box to allow users in the **db_owner** fixed database role to create merge publications in the database.</span></span>  

## <a name="subscribers"></a><span data-ttu-id="ed5cc-137">訂閱者</span><span class="sxs-lookup"><span data-stu-id="ed5cc-137">Subscribers</span></span>

  <span data-ttu-id="ed5cc-138">[發行者屬性]\*\*\*\* 對話方塊的 [訂閱者]\*\*\*\* 頁面，是用於執行  之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本之發行者。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-138">The **Subscribers** page of the **Publisher Properties** dialog box is used for Publishers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="ed5cc-139">此頁面可讓您啟用訂閱者，以接收來自此發行者的發行集資料。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-139">The page allows you to enable Subscribers to receive data from publications on this Publisher.</span></span> <span data-ttu-id="ed5cc-140">啟用訂閱者以接收來自此發行者的資料，並不會在此發行者上建立發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-140">Enabling a Subscriber to receive data from this Publisher does not create subscriptions to publications on this Publisher.</span></span> <span data-ttu-id="ed5cc-141">若要建立訂閱，您必須使用新增訂閱精靈。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-141">To create a subscription, you must use the New Subscription Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="ed5cc-142">選項</span><span class="sxs-lookup"><span data-stu-id="ed5cc-142">Options</span></span>  
 <span data-ttu-id="ed5cc-143">**訂閱者**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-143">**Subscribers**</span></span>  
 <span data-ttu-id="ed5cc-144">**[訂閱者]** 屬性方格，會顯示已啟用來接收此發行者之發行集資料的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-144">The **Subscribers** property grid shows Subscribers that are enabled to receive data from publications on this Publisher.</span></span> <span data-ttu-id="ed5cc-145">按一下訂閱者旁的屬性按鈕 (**...**)，即可檢視和設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-145">Click the properties button (**...**) next to a Subscriber to view and set additional properties.</span></span>  
  
 <span data-ttu-id="ed5cc-146">**加入**</span><span class="sxs-lookup"><span data-stu-id="ed5cc-146">**Add**</span></span>  
 <span data-ttu-id="ed5cc-147">按一下 **[加入]** 即可加入訂閱者，然後按一下 **[加入 SQL Server 訂閱者]** 或 **[加入非 SQL Server 訂閱者]**。</span><span class="sxs-lookup"><span data-stu-id="ed5cc-147">Click **Add** to add a Subscriber, and then click **Add SQL Server Subscriber** or **Add Non-SQL Server Subscriber**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ed5cc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed5cc-148">See Also</span></span>  
 [<span data-ttu-id="ed5cc-149">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="ed5cc-149">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
