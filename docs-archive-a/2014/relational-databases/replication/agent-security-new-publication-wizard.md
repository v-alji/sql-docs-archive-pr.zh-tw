---
title: 代理程式安全性 (新增發行集精靈) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0da30cb49a73024ca83d8587a4f6477d21c49c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593964"
---
# <a name="agent-security-new-publication-wizard"></a><span data-ttu-id="bedb2-102">代理程式安全性 (新增發行集精靈)</span><span class="sxs-lookup"><span data-stu-id="bedb2-102">Agent Security (New Publication Wizard)</span></span>
  <span data-ttu-id="bedb2-103">**[代理程式安全性]** 頁面可讓您指定執行下列代理程式的帳戶，並與複寫拓撲中的電腦建立連接。</span><span class="sxs-lookup"><span data-stu-id="bedb2-103">The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:</span></span>  
  
-   <span data-ttu-id="bedb2-104">所有發行集的快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="bedb2-104">The Snapshot Agent for all publications.</span></span>  
  
-   <span data-ttu-id="bedb2-105">所有交易式發行集的記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="bedb2-105">The Log Reader Agent for all transactional publications.</span></span>  
  
-   <span data-ttu-id="bedb2-106">允許可更新訂閱的交易式發行集之佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="bedb2-106">The Queue Reader Agent for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="bedb2-107">如果您在 [發行集類型] 頁面上指定 [具有可更新訂閱的交易式發行集]，則不論您所使用可更新訂閱類型為何都會建立此代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="bedb2-107">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use.</span></span> <span data-ttu-id="bedb2-108">如需有關可更新訂閱的詳細資訊，請參閱＜ [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bedb2-108">For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="bedb2-109">如需有關代理程式所需權限和複寫安全性的最佳做法的詳細資訊，請參閱＜ [Replication Agent Security Model](security/replication-agent-security-model.md) ＞和＜ [Replication Security Best Practices](security/replication-security-best-practices.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bedb2-109">For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bedb2-110">選項。</span><span class="sxs-lookup"><span data-stu-id="bedb2-110">Options</span></span>  
 <span data-ttu-id="bedb2-111">**快照集代理程式**</span><span class="sxs-lookup"><span data-stu-id="bedb2-111">**Snapshot Agent**</span></span>  
 <span data-ttu-id="bedb2-112">所有發行集都會顯示。</span><span class="sxs-lookup"><span data-stu-id="bedb2-112">Displayed for all publications.</span></span> <span data-ttu-id="bedb2-113">按一下 **[安全性設定]** ，即可在 **[快照集代理程式安全性]** 對話方塊中指定安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bedb2-113">Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="bedb2-114">如需有關快照集代理程式所使用帳戶需要之權限的詳細資訊，請在 **[快照集代理程式安全性]** 對話方塊中按一下 **[說明]** 。</span><span class="sxs-lookup"><span data-stu-id="bedb2-114">Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.</span></span>  
  
 <span data-ttu-id="bedb2-115">**記錄讀取器代理程式**</span><span class="sxs-lookup"><span data-stu-id="bedb2-115">**Log Reader Agent**</span></span>  
 <span data-ttu-id="bedb2-116">所有交易式發行集都會顯示。</span><span class="sxs-lookup"><span data-stu-id="bedb2-116">Displayed for all transactional publications.</span></span> <span data-ttu-id="bedb2-117">按一下 **[安全性設定]** ，即可在 **[記錄讀取器代理程式安全性]** 對話方塊中指定安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bedb2-117">Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.</span></span>  
  
 <span data-ttu-id="bedb2-118">如需有關記錄讀取器代理程式所使用帳戶需要之權限的詳細資訊，請在 **[記錄讀取器代理程式安全性]** 對話方塊中按一下 **[說明]** 。</span><span class="sxs-lookup"><span data-stu-id="bedb2-118">Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bedb2-119">每一個使用異動複寫發行的資料庫都有一個記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="bedb2-119">There is one Log Reader Agent for each database that is published using transactional replication.</span></span> <span data-ttu-id="bedb2-120">如果交易式發行集已存在資料庫中，則安全性設定是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="bedb2-120">If a transactional publication already exists in the database, the security settings are read-only.</span></span> <span data-ttu-id="bedb2-121">您可以在 **[發行集屬性]** 對話方塊中變更設定，但變更會影響資料庫中的所有交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="bedb2-121">You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.</span></span>  
  
 <span data-ttu-id="bedb2-122">**佇列讀取器代理程式**</span><span class="sxs-lookup"><span data-stu-id="bedb2-122">**Queue Reader Agent**</span></span>  
 <span data-ttu-id="bedb2-123">允許可更新訂閱的交易式發行集都會顯示。</span><span class="sxs-lookup"><span data-stu-id="bedb2-123">Displayed for transactional publications that allow updatable subscriptions.</span></span> <span data-ttu-id="bedb2-124">按一下 **[安全性設定]** ，即可在 **[佇列讀取器代理程式安全性]** 對話方塊中指定安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bedb2-124">Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box.</span></span> <span data-ttu-id="bedb2-125">此精靈完成時就會建立佇列讀取器代理程式作業；與您是否建立任何佇列更新訂閱無關。</span><span class="sxs-lookup"><span data-stu-id="bedb2-125">A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions.</span></span> <span data-ttu-id="bedb2-126">如果您不要建立任何佇列更新訂閱，就可以停用此作業。</span><span class="sxs-lookup"><span data-stu-id="bedb2-126">If you do not plan to create any queued updating subscriptions, you can disable the job.</span></span> <span data-ttu-id="bedb2-127">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 [Jobs] 資料夾中，以滑鼠右鍵按一下作業 (以下列格式命名： *[\<Publisher>].\<integer>* .)，然後按一下 [停用]。</span><span class="sxs-lookup"><span data-stu-id="bedb2-127">Right-click the job (named in the form: *[\<Publisher>].\<integer>*.) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Jobs** folder, and then click **Disable**.</span></span>  
  
 <span data-ttu-id="bedb2-128">如需有關佇列讀取器代理程式所使用的帳戶所需之權限的詳細資訊，請在 **[佇列讀取器代理程式安全性]** 對話方塊上按一下 **[說明]** 。</span><span class="sxs-lookup"><span data-stu-id="bedb2-128">Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bedb2-129">針對每個散發資料庫 (及其服務的所有發行者) 都有一個佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="bedb2-129">There is one Queue Reader Agent for each distribution database (and all Publishers that it serves).</span></span> <span data-ttu-id="bedb2-130">在使用給定散發資料庫的任何發行者上，如果已存在允許佇列更新訂閱的交易式發行集，則安全性設定是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="bedb2-130">If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read-only.</span></span> <span data-ttu-id="bedb2-131">您可以在 **[散發者屬性]** 對話方塊中，變更用於執行佇列讀取器代理程式和建立連接的帳戶，但變更會影響使用散發資料庫之所有發行者的發行集。</span><span class="sxs-lookup"><span data-stu-id="bedb2-131">You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedb2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bedb2-132">See Also</span></span>  
 <span data-ttu-id="bedb2-133">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="bedb2-133">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="bedb2-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="bedb2-134">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="bedb2-135">[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bedb2-135">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 <span data-ttu-id="bedb2-136">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bedb2-136">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="bedb2-137">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="bedb2-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="bedb2-138">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="bedb2-138">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="bedb2-139">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="bedb2-139">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
