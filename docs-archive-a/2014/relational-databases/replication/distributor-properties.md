---
title: 散發者屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
- sql12.rep.configdistwizard.distproperties.general.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
ms.assetid: f643c7c3-f238-4835-b81e-2c2b3b53b23f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 501c7931d651498fea49749be38af374c02424ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585861"
---
# <a name="sql-server-replication-distributor-properties"></a><span data-ttu-id="83060-102">SQL Server 複寫散發者屬性</span><span class="sxs-lookup"><span data-stu-id="83060-102">SQL Server Replication Distributor Properties</span></span>
<span data-ttu-id="83060-103">本主題討論 [散發者**屬性**] 視窗中 [**一般**]、[**發行者**] 和 [**散發資料庫**] 頁面上找到的屬性。</span><span class="sxs-lookup"><span data-stu-id="83060-103">This topic discusses the properties found on the **General**, **Publishers**, and **Distribution Database** pages within the **Distributor Properties** window.</span></span> 

## <a name="general"></a><span data-ttu-id="83060-104">一般</span><span class="sxs-lookup"><span data-stu-id="83060-104">General</span></span>
  <span data-ttu-id="83060-105">**[散發者屬性]** 對話方塊的 **[一般]** 頁面可讓您加入和刪除散發資料庫，以及設定散發資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="83060-105">The **General** page of the **Distributor Properties** dialog box allows you to add and delete distribution databases and set distribution database properties.</span></span>  
  
 <span data-ttu-id="83060-106">散發資料庫會儲存所有複寫類型的中繼資料和記錄資料，以及異動複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="83060-106">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span> <span data-ttu-id="83060-107">在許多情況下，單一散發資料庫即已足夠。</span><span class="sxs-lookup"><span data-stu-id="83060-107">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="83060-108">但是如果多個發行者使用單一散發者，請考慮為每個發行者建立散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="83060-108">But if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="83060-109">這樣可以確保流經每個散發資料庫的資料都不同。</span><span class="sxs-lookup"><span data-stu-id="83060-109">Doing so ensures that the data flowing through each distribution database is distinct.</span></span>  
  
### <a name="options"></a><span data-ttu-id="83060-110">選項</span><span class="sxs-lookup"><span data-stu-id="83060-110">Options</span></span>  
 <span data-ttu-id="83060-111">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="83060-111">**Databases**</span></span>  
 <span data-ttu-id="83060-112">**[資料庫]** 屬性方格會顯示散發者上之散發資料庫的名稱與保留屬性。</span><span class="sxs-lookup"><span data-stu-id="83060-112">The **Databases** property grid shows the name and retention properties of the distribution databases on the Distributor.</span></span> <span data-ttu-id="83060-113">**[交易保留]** 是為異動複寫儲存交易的時間長度 (交易保留也稱為散發保留)。</span><span class="sxs-lookup"><span data-stu-id="83060-113">**Transaction Retention** is the length of time transactions are stored for transactional replication (transaction retention is also known as distribution retention).</span></span> <span data-ttu-id="83060-114">**[記錄保留]** 是為所有的複寫類型儲存記錄中繼資料的時間長度。</span><span class="sxs-lookup"><span data-stu-id="83060-114">**History Retention** is the length of time history metadata is stored for all types of replication.</span></span> <span data-ttu-id="83060-115">如需散發保留的詳細資訊，請參閱[訂閱逾期與停用](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="83060-115">For more information about distribution retention, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="83060-116">按一下 **[資料庫]** 屬性方格中的屬性按鈕 ( **...** )，即可啟動 **[散發資料庫屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="83060-116">Click the properties button (**...**) in the **Databases** property grid to launch the **Distribution Database Properties** dialog box.</span></span>  
  
 <span data-ttu-id="83060-117">**新增**</span><span class="sxs-lookup"><span data-stu-id="83060-117">**New**</span></span>  
 <span data-ttu-id="83060-118">按一下即可建立新的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="83060-118">Click to create a new distribution database.</span></span>  
  
 <span data-ttu-id="83060-119">**刪除**</span><span class="sxs-lookup"><span data-stu-id="83060-119">**Delete**</span></span>  
 <span data-ttu-id="83060-120">在 **[資料庫]** 屬性方格中選取現有的散發資料庫，然後按一下 **[刪除]** 以刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="83060-120">Select an existing distribution database in the **Databases** property grid, and click **Delete** to delete the database.</span></span> <span data-ttu-id="83060-121">如果只有一個這種資料庫，就無法刪除此散發資料庫；每個散發者至少必須有一個散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="83060-121">You cannot delete the distribution database if there is only one such database; each Distributor must have at least one distribution database.</span></span> <span data-ttu-id="83060-122">若要刪除所有的散發資料庫，您必須停用電腦上的散發。</span><span class="sxs-lookup"><span data-stu-id="83060-122">To delete all distribution databases, you must disable distribution on the computer.</span></span> <span data-ttu-id="83060-123">如需詳細資訊，請參閱[停用發行和散發](disable-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="83060-123">For more information, see [Disable Publishing and Distribution](disable-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="83060-124">**設定檔預設值**</span><span class="sxs-lookup"><span data-stu-id="83060-124">**Profile Defaults**</span></span>  
 <span data-ttu-id="83060-125">按一下即可存取 **[代理程式設定檔]** 對話方塊中的複寫代理程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="83060-125">Click to access replication agent profiles in the **Agent Profiles** dialog box.</span></span> <span data-ttu-id="83060-126">如需有關設定檔的詳細資訊，請參閱＜ [Replication Agent Profiles](agents/replication-agent-profiles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="83060-126">For more information about profiles, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  

## <a name="publishers"></a><span data-ttu-id="83060-127">發行者</span><span class="sxs-lookup"><span data-stu-id="83060-127">Publishers</span></span>

  <span data-ttu-id="83060-128">**[散發者屬性]** 對話方塊的 **[發行者]** 頁面可讓您啟用發行者，以使用此散發者。</span><span class="sxs-lookup"><span data-stu-id="83060-128">The **Publishers** page of the **Distributor Properties** dialog box allows you to enable Publishers to use this Distributor.</span></span> <span data-ttu-id="83060-129">您也可以設定與這些發行者相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="83060-129">You can also set properties associated with those Publishers.</span></span> <span data-ttu-id="83060-130">請注意，讓發行者可以使用這個伺服器作為它的遠端散發者，並不會使該伺服器成為發行者。</span><span class="sxs-lookup"><span data-stu-id="83060-130">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="83060-131">您必須連接到發行者，設定其發行，並選擇此伺服器為散發者。</span><span class="sxs-lookup"><span data-stu-id="83060-131">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="83060-132">您可以透過新增發行集精靈來設定發行者和選擇散發者。</span><span class="sxs-lookup"><span data-stu-id="83060-132">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
### <a name="options"></a><span data-ttu-id="83060-133">選項</span><span class="sxs-lookup"><span data-stu-id="83060-133">Options</span></span>  
 <span data-ttu-id="83060-134">**發行者**</span><span class="sxs-lookup"><span data-stu-id="83060-134">**Publishers**</span></span>  
 <span data-ttu-id="83060-135">選取可使用這個散發者的伺服器。</span><span class="sxs-lookup"><span data-stu-id="83060-135">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="83060-136">按一下發行者旁的 [屬性] 按鈕 **(...)** ，以檢視和設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="83060-136">Click the Properties button **(...)** next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="83060-137">**加入**</span><span class="sxs-lookup"><span data-stu-id="83060-137">**Add**</span></span>  
 <span data-ttu-id="83060-138">如果未列出您要允許的伺服器，請按一下 [加入]\*\*\*\*，將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者或 Oracle 發行者加入可用發行者的清單中。</span><span class="sxs-lookup"><span data-stu-id="83060-138">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span> <span data-ttu-id="83060-139">如果您加入的伺服器是第一部使用此散發者作為遠端散發者的伺服器，系統會提示您提供管理連結密碼。</span><span class="sxs-lookup"><span data-stu-id="83060-139">If the server you add is the first server to use this Distributor as a remote Distributor, you are prompted to provide an administrative link password.</span></span>  
  
 <span data-ttu-id="83060-140">**管理連結密碼**</span><span class="sxs-lookup"><span data-stu-id="83060-140">**Administrative link password**</span></span>  
 <span data-ttu-id="83060-141">使用 **distributor_admin** 登入進行發行者和遠端散發者的連接複寫時，這可用來指定或更新該連接複寫的密碼：</span><span class="sxs-lookup"><span data-stu-id="83060-141">Use to specify or update the password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login:</span></span>  
  
-   <span data-ttu-id="83060-142">如果散發者伺服器只是當成本機散發者，這個密碼會隨機產生並自動設定。</span><span class="sxs-lookup"><span data-stu-id="83060-142">If the Distributor serves only as a local Distributor, this password is randomly generated and automatically configured.</span></span>  
-   <span data-ttu-id="83060-143">如果散發者已經有遠端發行者，此頁面上或設定散發精靈的 **[散發者密碼]** 頁面上一開始就會提供密碼。</span><span class="sxs-lookup"><span data-stu-id="83060-143">If the Distributor already has a remote Publisher, a password was initially supplied on this page or the **Distributor Password** page of the Configure Distribution Wizard.</span></span>    
-   <span data-ttu-id="83060-144">如果啟用此散發者的第一個遠端發行者，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="83060-144">If you enable the first remote Publisher for this Distributor, you are prompted to enter a password.</span></span>  
  
 <span data-ttu-id="83060-145">如需散發者安全性的詳細資訊，請參閱[保護散發者](security/secure-the-distributor.md)。</span><span class="sxs-lookup"><span data-stu-id="83060-145">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  

## <a name="distribution-database"></a><span data-ttu-id="83060-146">散發資料庫</span><span class="sxs-lookup"><span data-stu-id="83060-146">Distribution Database</span></span>
 <span data-ttu-id="83060-147"> [散發資料庫屬性\]\*\*\** 對話方塊可讓您檢視許多屬性，並設定資料庫的交易保留期限和記錄保留期限。</span><span class="sxs-lookup"><span data-stu-id="83060-147">The **Distribution Database Properties** dialog box allows you to view a number of properties and to set the transaction retention period and history retention period for the database.</span></span>  
  
### <a name="options"></a><span data-ttu-id="83060-148">選項。</span><span class="sxs-lookup"><span data-stu-id="83060-148">Options</span></span>  
 <span data-ttu-id="83060-149">**名稱**</span><span class="sxs-lookup"><span data-stu-id="83060-149">**Name**</span></span>  
 <span data-ttu-id="83060-150">散發資料庫的名稱，預設為「distribution」(唯讀)。</span><span class="sxs-lookup"><span data-stu-id="83060-150">The name of the distribution database, which defaults to 'distribution' (read-only).</span></span>  
  
 <span data-ttu-id="83060-151">**檔案位置**</span><span class="sxs-lookup"><span data-stu-id="83060-151">**File locations**</span></span>  
 <span data-ttu-id="83060-152">資料庫檔案和記錄檔的位置 (唯讀)。</span><span class="sxs-lookup"><span data-stu-id="83060-152">The location of the database file and the log file (read-only).</span></span>  
  
 <span data-ttu-id="83060-153">**交易保留期限**</span><span class="sxs-lookup"><span data-stu-id="83060-153">**Transaction retention period**</span></span>  
 <span data-ttu-id="83060-154">又稱為散發保留期限。</span><span class="sxs-lookup"><span data-stu-id="83060-154">Also known as the distribution retention period.</span></span> <span data-ttu-id="83060-155">交易的儲存時間長度，適用於異動複寫。</span><span class="sxs-lookup"><span data-stu-id="83060-155">The length of time transactions are stored for transactional replication.</span></span> <span data-ttu-id="83060-156">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="83060-156">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="83060-157">**記錄保留期限**</span><span class="sxs-lookup"><span data-stu-id="83060-157">**History retention period**</span></span>  
 <span data-ttu-id="83060-158">記錄中繼資料的儲存時間長度，適用於所有類型的複寫。</span><span class="sxs-lookup"><span data-stu-id="83060-158">The length of time history metadata is stored for all types of replication.</span></span>  
  
 <span data-ttu-id="83060-159">**佇列讀取器代理程式安全性**</span><span class="sxs-lookup"><span data-stu-id="83060-159">**Queue Reader Agent security**</span></span>  
 <span data-ttu-id="83060-160">佇列讀取器代理程式會用於具有佇列更新訂閱的異動複寫。</span><span class="sxs-lookup"><span data-stu-id="83060-160">The Queue Reader Agent is used by transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="83060-161">如果您在新增發行集精靈的 **[發行集類型]** 頁面上選取 **[具更新訂閱的交易式發行集]** ，則會自動建立佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="83060-161">A Queue Reader Agent is created automatically if you select **Transactional publication with updating subscriptions** on the **Publication Type** page of the New Publication Wizard.</span></span> <span data-ttu-id="83060-162">按一下 [安全性設定]\*\*\*\*，以變更執行代理程式和與散發者連線的帳戶。</span><span class="sxs-lookup"><span data-stu-id="83060-162">Click **Security Settings...** to change the account under which the agent runs and makes connections to the Distributor.</span></span>  
  
 <span data-ttu-id="83060-163">在此頁面上選取 **[建立佇列讀取器代理程式]** 也可以建立佇列讀取器代理程式 (如果已建立代理程式，此選項會停用)。</span><span class="sxs-lookup"><span data-stu-id="83060-163">A Queue Reader Agent can also be created by selecting **Create Queue Reader Agent** on this page (this option is disabled if the agent has already been created).</span></span>  
  
 <span data-ttu-id="83060-164">有兩個地方可以指定佇列讀取器代理程式的其他連接資訊：</span><span class="sxs-lookup"><span data-stu-id="83060-164">Additional connection information for the Queue Reader Agent is specified in two places:</span></span>    
-   <span data-ttu-id="83060-165">代理程式會使用 **[發行者屬性]** 對話方塊中指定的認證來連接發行者，該對話方塊可以從 **[散發者屬性]** 對話方塊的 **[發行者]** 頁面存取。</span><span class="sxs-lookup"><span data-stu-id="83060-165">The agent connects to the Publisher using the credentials specified in the **Publisher Properties** dialog box, which is available from the **Publishers** page of the **Distributor Properties** dialog box.</span></span>    
-   <span data-ttu-id="83060-166">代理程式會使用新增訂閱精靈中為散發代理程式指定的認證，來連接訂閱者。</span><span class="sxs-lookup"><span data-stu-id="83060-166">The agent connects to the Subscriber using the credentials specified for the Distribution Agent in the New Subscription Wizard.</span></span>  
  
 <span data-ttu-id="83060-167">如需詳細資訊，請參閱 \\ [Replication Agent Security Model](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="83060-167">For more information, see  \\[Replication Agent Security Model](security/replication-agent-security-model.md).</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="83060-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83060-168">See Also</span></span>  
 <span data-ttu-id="83060-169">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="83060-169">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="83060-170">檢視及修改散發者和發行者屬性</span><span class="sxs-lookup"><span data-stu-id="83060-170">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
  
