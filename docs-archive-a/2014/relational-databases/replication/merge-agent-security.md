---
title: 合併代理程式安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecbb044ca87ccfc74c5cb39a016667d15cf7a859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702846"
---
# <a name="merge-agent-security"></a><span data-ttu-id="4d785-102">合併代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="4d785-102">Merge Agent Security</span></span>
  <span data-ttu-id="4d785-103">**[合併代理程式安全性]** 對話方塊可讓您指定執行合併代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d785-103">The **Merge Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Merge Agent runs.</span></span> <span data-ttu-id="4d785-104">合併代理程式會在發送訂閱的散發者端和提取訂閱的訂閱者端執行。</span><span class="sxs-lookup"><span data-stu-id="4d785-104">The Merge Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="4d785-105">Windows 帳戶也稱為 *處理帳戶*，因為代理程式處理是在這個帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="4d785-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="4d785-106">對話方塊中其他可用的選項會視您存取的方式而定：</span><span class="sxs-lookup"><span data-stu-id="4d785-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="4d785-107">如果從新增訂閱精靈存取此對話方塊，就也可以指定合併代理程式用於連接到訂閱者 (適用於發送訂閱) 或發行者和散發者 (適用於提取訂閱) 的內容。</span><span class="sxs-lookup"><span data-stu-id="4d785-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Merge Agent makes connections to the Subscriber (for push subscriptions) or the Publisher and Distributor (for pull subscriptions).</span></span> <span data-ttu-id="4d785-108">可以使用 Windows 帳戶或在您指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶的內容之下建立連線。</span><span class="sxs-lookup"><span data-stu-id="4d785-108">The connection can be made using the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="4d785-109">如果從 **[訂閱屬性]** 對話方塊存取此對話方塊，請按一下該對話方塊的 **[訂閱者連接]** 或 **[發行者連接]** 資料列中的屬性按鈕 ( **...** )，來指定合併代理程式要在其下建立連接的內容。</span><span class="sxs-lookup"><span data-stu-id="4d785-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Merge Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Publisher Connection** row of that dialog box.</span></span> <span data-ttu-id="4d785-110">如需存取 [訂閱屬性]  對話方塊的詳細資訊，請參閱[檢視及修改發送訂閱屬性](view-and-modify-push-subscription-properties.md)和[如何：檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4d785-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="4d785-111">所有帳戶都必須有效，並且每個帳戶皆有指定正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="4d785-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="4d785-112">等到代理程式執行時，才會驗證帳戶與密碼。</span><span class="sxs-lookup"><span data-stu-id="4d785-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4d785-113">選項。</span><span class="sxs-lookup"><span data-stu-id="4d785-113">Options</span></span>  
 <span data-ttu-id="4d785-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="4d785-114">**Process Account**</span></span>  
 <span data-ttu-id="4d785-115">輸入要在其下執行合併代理程式的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d785-115">Enter a Windows account under which the Merge Agent runs.</span></span>  
  
-   <span data-ttu-id="4d785-116">針對發送訂閱，帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="4d785-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="4d785-117">至少是散發資料庫中 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="4d785-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="4d785-118">為 PAL 的成員。</span><span class="sxs-lookup"><span data-stu-id="4d785-118">Be a member of the PAL.</span></span>  
  
    -   <span data-ttu-id="4d785-119">為與發行集資料庫中使用者相關聯的登入。</span><span class="sxs-lookup"><span data-stu-id="4d785-119">Be a login associated with a user in the publication database.</span></span>  
  
    -   <span data-ttu-id="4d785-120">擁有快照集共用上的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4d785-120">Have read permissions on the snapshot share.</span></span>  
  
-   <span data-ttu-id="4d785-121">針對提取訂閱，帳戶至少必須是訂閱資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="4d785-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="4d785-122">如果是在進行連接時模擬處理帳戶，則需要其他的權限。</span><span class="sxs-lookup"><span data-stu-id="4d785-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="4d785-123">請參閱下面的 **[連接到發行者與散發者]** 和 **[連接到訂閱者]** 章節。</span><span class="sxs-lookup"><span data-stu-id="4d785-123">See the **Connect to the Publisher and Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="4d785-124">[處理帳戶]  不可以指定提取訂閱至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]，因為合併代理程式無法在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="4d785-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Merge Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="4d785-125">**[密碼]** 與 **[確認密碼]**</span><span class="sxs-lookup"><span data-stu-id="4d785-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="4d785-126">輸入 Windows 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="4d785-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="4d785-127">**[連接到發行者與散發者]**</span><span class="sxs-lookup"><span data-stu-id="4d785-127">**Connect to the Publisher and Distributor**</span></span>  
 <span data-ttu-id="4d785-128">針對發送訂閱，一律會藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶，來連接到發行者與散發者。</span><span class="sxs-lookup"><span data-stu-id="4d785-128">For push subscriptions, connections to the Publisher and Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="4d785-129">針對提取訂閱，選取合併代理程式是否應藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到發行者與散發者。</span><span class="sxs-lookup"><span data-stu-id="4d785-129">For pull subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="4d785-130">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="4d785-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="4d785-131">建議您選取模擬 Windows 帳戶，而非使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d785-131">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="4d785-132">用於連接的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="4d785-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="4d785-133">為 PAL 的成員。</span><span class="sxs-lookup"><span data-stu-id="4d785-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="4d785-134">為與發行集資料庫中使用者相關聯的登入。</span><span class="sxs-lookup"><span data-stu-id="4d785-134">Be a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="4d785-135">為與散發資料庫中之使用者相關聯的登入 (使用者可為 Guest 使用者)。</span><span class="sxs-lookup"><span data-stu-id="4d785-135">Be a login associated with a user in the distribution database (the user can be the Guest user).</span></span>  
  
-   <span data-ttu-id="4d785-136">擁有快照集共用上的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4d785-136">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="4d785-137">**連接到訂閱者**</span><span class="sxs-lookup"><span data-stu-id="4d785-137">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="4d785-138">針對提取訂閱，一律會藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="4d785-138">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="4d785-139">針對發送訂閱，選取合併代理程式是否應藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到發行者與散發者。</span><span class="sxs-lookup"><span data-stu-id="4d785-139">For push subscriptions, select whether the Merge Agent should make connections to the Publisher and Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="4d785-140">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="4d785-140">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d785-141">建議您選取模擬 Windows 帳戶，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d785-141">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="4d785-142">用於連接到訂閱者的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶至少必須是訂閱資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="4d785-142">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d785-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d785-143">See Also</span></span>  
 <span data-ttu-id="4d785-144">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="4d785-144">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="4d785-145">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="4d785-145">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="4d785-146">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4d785-146">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="4d785-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="4d785-147">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="4d785-148">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="4d785-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
