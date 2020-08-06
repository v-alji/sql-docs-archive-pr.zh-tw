---
title: 保護訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], security
- Subscribers [SQL Server replication], security
- security [SQL Server replication], Subscribers
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f03b9a202c3c49f147368460518a579f28dc850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598271"
---
# <a name="secure-the-subscriber"></a><span data-ttu-id="501dd-102">保護訂閱者</span><span class="sxs-lookup"><span data-stu-id="501dd-102">Secure the Subscriber</span></span>
  <span data-ttu-id="501dd-103">「合併代理程式」與「散發代理程式」會連接到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="501dd-103">Merge Agents and Distribution Agents connect to the Subscriber.</span></span> <span data-ttu-id="501dd-104">這些連接會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入或 Windows 登入的內容下進行。</span><span class="sxs-lookup"><span data-stu-id="501dd-104">These connections can be made under the context of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login or a Windows login.</span></span> <span data-ttu-id="501dd-105">為遵循授與所需最小權限的原則，並同時保護所有密碼的儲存，有必要為這些代理程式提供適當的登入。</span><span class="sxs-lookup"><span data-stu-id="501dd-105">It is important to provide an appropriate login for these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords.</span></span> <span data-ttu-id="501dd-106">如需有關各代理程式需要的權限資訊，請參閱＜ [Replication Agent Security Model](replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="501dd-106">For information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
## <a name="distribution-agent"></a><span data-ttu-id="501dd-107">散發代理程式</span><span class="sxs-lookup"><span data-stu-id="501dd-107">Distribution Agent</span></span>  
 <span data-ttu-id="501dd-108">每個訂閱都有一個「散發代理程式」(獨立代理程式，在「新增發行集精靈」中所建發行集的預設值)，或者每個發行集資料庫和訂閱資料庫組都有一個「散發代理程式」(共用代理程式)。</span><span class="sxs-lookup"><span data-stu-id="501dd-108">There is either one Distribution Agent per subscription (an independent agent, the default for publications created in the New Publication Wizard) or one Distribution Agent per publication database and subscription database pair (a shared agent).</span></span> <span data-ttu-id="501dd-109">T</span><span class="sxs-lookup"><span data-stu-id="501dd-109">T</span></span>  
  
 <span data-ttu-id="501dd-110">若要指定發送訂閱的連接資訊，請參閱[建立發送訂閱](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-110">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="501dd-111">若要指定提取訂閱的連接資訊，請參閱[建立提取訂閱](../create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-111">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md)</span></span>  
  
## <a name="merge-agent"></a><span data-ttu-id="501dd-112">合併代理程式</span><span class="sxs-lookup"><span data-stu-id="501dd-112">Merge Agent</span></span>  
 <span data-ttu-id="501dd-113">每個合併訂閱都有其「合併代理程式」，以連接「發行者」和「訂閱者」，並更新這兩者。</span><span class="sxs-lookup"><span data-stu-id="501dd-113">Each merge subscription has its own Merge Agent that connects to and updates both the Publisher and the Subscriber.</span></span>  
  
 <span data-ttu-id="501dd-114">若要指定發送訂閱的連接資訊，請參閱[建立發送訂閱](../create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-114">To specify connection information for push subscriptions, see [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="501dd-115">若要指定提取訂閱的連接資訊，請參閱[建立提取訂閱](../create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-115">To specify connection information for pull subscriptions, see [Create a Pull Subscription](../create-a-pull-subscription.md).</span></span>  
  
## <a name="immediate-updating-subscriptions"></a><span data-ttu-id="501dd-116">立即更新訂閱</span><span class="sxs-lookup"><span data-stu-id="501dd-116">Immediate Updating Subscriptions</span></span>  
 <span data-ttu-id="501dd-117">設定立即更新訂閱時，要指定「訂閱者」用來連接到「發行者」的帳戶。</span><span class="sxs-lookup"><span data-stu-id="501dd-117">When you configure an immediate updating subscription, you specify an account at the Subscriber under which connections to the Publisher are made.</span></span> <span data-ttu-id="501dd-118">在訂閱者端引發的觸發程序，會使用這些連接將變更傳播至發行者。</span><span class="sxs-lookup"><span data-stu-id="501dd-118">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="501dd-119">此連接類型有三個選項可用：</span><span class="sxs-lookup"><span data-stu-id="501dd-119">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="501dd-120">複寫建立的連結伺服器；用您在設定時指定的認證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="501dd-120">A linked server that replication creates; the connection is made with the credentials you specify at configuration time.</span></span>  
  
-   <span data-ttu-id="501dd-121">複寫建立的連結伺服器；以在訂閱者端執行變更的使用者認證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="501dd-121">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
-   <span data-ttu-id="501dd-122">您已定義的連結伺服器或遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="501dd-122">A linked server or remote server that you have already defined.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="501dd-123">若要指定連接資訊，請使用 [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="501dd-123">To specify connection information, use the stored procedure [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="501dd-124">您也可以使用「新增訂閱精靈」的 **[可更新訂閱的登入]** 頁面，此頁面會呼叫 **sp_link_publication**。</span><span class="sxs-lookup"><span data-stu-id="501dd-124">You can also use the **Login for Updatable Subscriptions** page of the New Subscription Wizard, which calls **sp_link_publication**.</span></span> <span data-ttu-id="501dd-125">在某些情況下，如果「訂閱者」執行 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 或更新版本，且「發行者」執行較舊的版本，此預存程序可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="501dd-125">Under certain conditions, this stored procedure can fail if the Subscriber is running [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) or later, and the Publisher is running an earlier version.</span></span> <span data-ttu-id="501dd-126">如果在此情況下預存程序失敗，請將「發行者」升級為 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="501dd-126">If the stored procedure fails in this scenario, upgrade the Publisher to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 or later.</span></span>  
  
 <span data-ttu-id="501dd-127">如需詳細資訊，請參閱[建立交易式發行集的可更新訂閱](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)和[檢視及修改複寫安全性設定](view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-127">For more information, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="501dd-128">對於複寫在發行集資料庫中建立的檢視，為連接指定的帳戶應該只被授與插入、更新及刪除資料的權限，而不應該被授與任何其他權限。</span><span class="sxs-lookup"><span data-stu-id="501dd-128">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="501dd-129">針對發行集資料庫中以 **syncobj_** _\<HexadecimalNumber>_ 格式命名的檢視，您在每一個訂閱者端所設定帳戶都應該被授與這些檢視的權限。</span><span class="sxs-lookup"><span data-stu-id="501dd-129">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
## <a name="queued-updating-subscriptions"></a><span data-ttu-id="501dd-130">佇列更新訂閱</span><span class="sxs-lookup"><span data-stu-id="501dd-130">Queued Updating Subscriptions</span></span>  
 <span data-ttu-id="501dd-131">設定佇列更新訂閱時，請注意與安全性相關的兩方面：</span><span class="sxs-lookup"><span data-stu-id="501dd-131">When you configure queued updating subscriptions, there are two areas to keep in mind that relate to security:</span></span>  
  
-   <span data-ttu-id="501dd-132">每個散發者只能有一個「佇列讀取器代理程式」。</span><span class="sxs-lookup"><span data-stu-id="501dd-132">There is only one Queue Reader Agent for each Distributor.</span></span> <span data-ttu-id="501dd-133">建議為每個「散發者」最多設定一個為佇列更新訂閱啟用的發行集。</span><span class="sxs-lookup"><span data-stu-id="501dd-133">It is recommended that for each Distributor, you configure at most one publication that is enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="501dd-134">「佇列讀取器代理程式」可連接到「散發者」、「發行者」及各個「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="501dd-134">The Queue Reader agent makes connections to the Distributor, Publisher, and each Subscriber:</span></span>  
  
    -   <span data-ttu-id="501dd-135">代理程式執行和連接到「散發者」時所用的帳戶，會在您建立代理程式時指定 (如果使用「新增訂閱精靈」，則會在建立為更新訂閱啟用的發行集時建立代理程式)。</span><span class="sxs-lookup"><span data-stu-id="501dd-135">The account under which the agent runs and makes connections to the Distributor is specified when you create the agent (if you use the New Publication Wizard, the agent is created when you create a publication that is enabled for updating subscriptions).</span></span>  
  
    -   <span data-ttu-id="501dd-136">代理程式連接到「發行者」時所用的帳戶，會在您為「發行者」設定散發時指定。</span><span class="sxs-lookup"><span data-stu-id="501dd-136">The account under which the agent makes connections to the Publisher is specified when you configure distribution for a Publisher.</span></span> <span data-ttu-id="501dd-137">指定代理程式執行時所用的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="501dd-137">Specify the Windows account under which the agent runs or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account.</span></span>  
  
    -   <span data-ttu-id="501dd-138">代理程式連接到「訂閱者」時所用的帳戶，會在您建立訂閱時指定。</span><span class="sxs-lookup"><span data-stu-id="501dd-138">The account under which the agent makes connections to the Subscriber is specified when you create the subscription.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="501dd-139">使用「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證」以連接到「訂閱者」，然後為每個「訂閱者」的連接指定不同帳戶。</span><span class="sxs-lookup"><span data-stu-id="501dd-139">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication for connections to Subscribers, and specify a different account for the connection to each Subscriber.</span></span> <span data-ttu-id="501dd-140">如果使用提取訂閱，複寫會永遠將連接設定為使用「Windows 驗證」(對於提取訂閱來說，複寫無法存取使用「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證」所需的「訂閱者」端中繼資料)。</span><span class="sxs-lookup"><span data-stu-id="501dd-140">If you use a pull subscription, replication always sets the connection to use Windows Authentication (for pull subscriptions, replication cannot access metadata at the Subscriber required to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication).</span></span> <span data-ttu-id="501dd-141">在此情況下，請在設定訂閱後，將連接變更為使用「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證」。</span><span class="sxs-lookup"><span data-stu-id="501dd-141">In this case, change the connection to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication after the subscription is configured.</span></span>  
  
     <span data-ttu-id="501dd-142">如需詳細資訊，請參閱＜如何：建立交易式發行集的可更新訂閱 (SQL Server Management Studio)＞和[檢視及修改複寫安全性設定](view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="501dd-142">For more information, see How to: Create an Updating Subscription to a Transactional Publication (SQL Server Management Studio) and [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501dd-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="501dd-143">See Also</span></span>  
 <span data-ttu-id="501dd-144">[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="501dd-144">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="501dd-145">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="501dd-145">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="501dd-146">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="501dd-146">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
