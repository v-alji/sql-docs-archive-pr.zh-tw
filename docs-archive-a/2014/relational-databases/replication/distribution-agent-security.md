---
title: 散發代理程式安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4342d44a221d9b816a95a283917f005eb018827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585869"
---
# <a name="distribution-agent-security"></a><span data-ttu-id="5fc2c-102">散發代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="5fc2c-102">Distribution Agent Security</span></span>
  <span data-ttu-id="5fc2c-103">**[散發代理程式安全性]** 對話方塊，可以讓您指定散發代理程式執行用的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-103">The **Distribution Agent Security** dialog box allows you to specify the Windows account under which the Distribution Agent runs.</span></span> <span data-ttu-id="5fc2c-104">若為發送訂閱，散發代理程式會在散發者端執行；若為提取訂閱，則散發代理程式會在訂閱者端執行。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-104">The Distribution Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="5fc2c-105">此 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶亦稱為 *處理帳戶*，因為代理程式處理序會以此帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="5fc2c-106">對話方塊中其他可用的選項會視您存取的方式而定：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="5fc2c-107">如果是從新增訂閱精靈中存取對話方塊，它還可以讓您指定散發代理程式連接到訂閱者 (適用於發送訂閱) 或散發者 (適用於提取訂閱) 所用的內容。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Distribution Agent makes connections to the Subscriber (for push subscriptions) or the Distributor (for pull subscriptions).</span></span> <span data-ttu-id="5fc2c-108">此連線可以藉由模擬 Windows 帳戶，或用您指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶內容來進行。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-108">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="5fc2c-109">如果是從 **[訂閱屬性]** 對話方塊中存取對話方塊，請按一下 **[訂閱者連接]** 中的屬性按鈕 ( **...** )，或該對話方塊的 **[散發者連接]** 資料列，即可指定散發代理程式進行連接所用的內容。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Distribution Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Distributor Connection** row of that dialog box.</span></span> <span data-ttu-id="5fc2c-110">如需存取 [訂閱屬性]  對話方塊的詳細資訊，請參閱[檢視及修改發送訂閱屬性](view-and-modify-push-subscription-properties.md)和[如何：檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="5fc2c-111">所有帳戶都必須有效，並且每個帳戶皆有指定正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="5fc2c-112">等到代理程式執行時，才會驗證帳戶與密碼。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5fc2c-113">選項。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-113">Options</span></span>  
 <span data-ttu-id="5fc2c-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="5fc2c-114">**Process Account**</span></span>  
 <span data-ttu-id="5fc2c-115">輸入散發代理程式執行用的 Windows 帳戶：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-115">Enter a Windows account under which the Distribution Agent runs:</span></span>  
  
-   <span data-ttu-id="5fc2c-116">針對發送訂閱，帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="5fc2c-117">至少是散發資料庫中 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="5fc2c-118">是發行存取清單 (PAL) 的成員。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-118">Be a member of the publication access list (PAL).</span></span>  
  
    -   <span data-ttu-id="5fc2c-119">擁有快照集共用上的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-119">Have read permissions on the snapshot share.</span></span>  
  
    -   <span data-ttu-id="5fc2c-120">如果訂閱是針對非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者，訂閱者之 OLE DB 提供者的安裝目錄上，就要擁有讀取權限。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-120">Have read permissions on the install directory of the OLE DB provider for the Subscriber if the subscription is for a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber.</span></span>  
  
-   <span data-ttu-id="5fc2c-121">針對提取訂閱，帳戶至少必須是訂閱資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="5fc2c-122">如果是在進行連接時模擬處理帳戶，則需要其他的權限。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="5fc2c-123">請參閱以下的＜ **連接到散發者** ＞和＜ **連接到訂閱者** ＞章節。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-123">See the **Connect to the Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="5fc2c-124">無法為   的提取訂閱指定 [處理帳戶][!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]，因為散發代理程式無法在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 的執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="5fc2c-125">**[密碼]** 與 **[確認密碼]**</span><span class="sxs-lookup"><span data-stu-id="5fc2c-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="5fc2c-126">輸入 Windows 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="5fc2c-127">**連接到散發者**</span><span class="sxs-lookup"><span data-stu-id="5fc2c-127">**Connect to the Distributor**</span></span>  
 <span data-ttu-id="5fc2c-128">對於發送訂閱，要連接到散發者時，一律都會以模擬 **[處理帳戶]** 文字方塊中所指定的帳戶來進行。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-128">For push subscriptions, connections to the Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="5fc2c-129">對於提取訂閱，選取散發代理程式是否應模擬 **[處理帳戶]** 文字方塊中所指定的帳戶，還是要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到散發者。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-129">For pull subscriptions, select whether the Distribution Agent should make connections to the Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="5fc2c-130">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fc2c-131">建議您選取模擬 Windows 帳戶，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-131">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="5fc2c-132">用於連接的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="5fc2c-133">為 PAL 的成員。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="5fc2c-134">擁有快照集共用上的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-134">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="5fc2c-135">**連接到訂閱者**</span><span class="sxs-lookup"><span data-stu-id="5fc2c-135">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="5fc2c-136">針對提取訂閱，一律會藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-136">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="5fc2c-137">對於發送訂閱， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者與非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者的選項並不相同：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-137">For push subscriptions, the options are different for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="5fc2c-138">對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者：選取散發代理程式是否應模擬 **[處理帳戶]** 文字方塊中所指定的帳戶，還是要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-138">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers: select whether the Distribution Agent should make connections to the Subscriber by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="5fc2c-139">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-139">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5fc2c-140">建議您選取模擬 Windows 帳戶，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-140">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
     <span data-ttu-id="5fc2c-141">用於連接到訂閱者的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶至少必須是訂閱資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-141">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
-   <span data-ttu-id="5fc2c-142">對於非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者，請指定當散發代理程式要連接到訂閱者時，應使用的訂閱者端之資料庫登入。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-142">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, specify the database login at the Subscriber that should be used when the Distribution Agent connects to the Subscriber.</span></span> <span data-ttu-id="5fc2c-143">此登入應擁有在訂閱資料庫中建立物件的權限。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-143">The login should have sufficient permissions to create objects in the subscription database.</span></span> <span data-ttu-id="5fc2c-144">如需設定非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者的詳細資訊，請參閱[為非 SQL Server 訂閱者建立訂閱](create-a-subscription-for-a-non-sql-server-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-144">For more information about configuring non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, see [Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
 <span data-ttu-id="5fc2c-145">**其他連接選項**</span><span class="sxs-lookup"><span data-stu-id="5fc2c-145">**Additional connection options**</span></span>  
 <span data-ttu-id="5fc2c-146">僅限非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-146">Non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers only.</span></span> <span data-ttu-id="5fc2c-147">以連接字串的格式，為訂閱者指定任何連接選項 (Oracle 並不需要其他選項)。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-147">Specify any connection options for the Subscriber in the form of a connection string (Oracle does not require additional options).</span></span> <span data-ttu-id="5fc2c-148">每個選項應以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-148">Each option should be separated by a semi-colon.</span></span> <span data-ttu-id="5fc2c-149">以下為 IBM DB2 連接字串的範例 (分行符號僅為便於閱讀)：</span><span class="sxs-lookup"><span data-stu-id="5fc2c-149">The following is an example of an IBM DB2 connection string (line breaks are for readability):</span></span>  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 <span data-ttu-id="5fc2c-150">字串中的大多數選項是您設定之 DB2 伺服器的專用選項，但 **將二進位當作字元處理** 選項，應一律設定為 [False]  。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-150">Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**.</span></span> <span data-ttu-id="5fc2c-151">需要為 **初始目錄** 選項指定值，以便識別訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-151">A value is required for the **Initial Catalog** option to identify the subscription database.</span></span> <span data-ttu-id="5fc2c-152">如需相關資訊，請參閱 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="5fc2c-152">For more information, see [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc2c-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fc2c-153">See Also</span></span>  
 <span data-ttu-id="5fc2c-154">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="5fc2c-154">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="5fc2c-155">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="5fc2c-155">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="5fc2c-156">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="5fc2c-156">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="5fc2c-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="5fc2c-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="5fc2c-158">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="5fc2c-158">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
