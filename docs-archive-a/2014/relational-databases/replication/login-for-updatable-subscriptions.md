---
title: 可更新訂閱的登入 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a5cc9190c77f506b13ba8b5fba0e32d5a925570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707366"
---
# <a name="login-for-updatable-subscriptions"></a><span data-ttu-id="4c33d-102">可更新訂閱的登入</span><span class="sxs-lookup"><span data-stu-id="4c33d-102">Login for Updatable Subscriptions</span></span>
  <span data-ttu-id="4c33d-103">如果您在此精靈的 **[可更新的訂閱]** 頁面上選取 **[複寫]** ，就必須在訂閱者端指定帳戶，並使用此帳戶建立發行者的連接，以進行立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="4c33d-103">If you selected **Replicate** on the **Updatable Subscriptions** page of this wizard, you must specify an account at the Subscriber under which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="4c33d-104">在訂閱者端引發的觸發程序，會使用這些連接將變更傳播至發行者。</span><span class="sxs-lookup"><span data-stu-id="4c33d-104">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="4c33d-105">即使您在 **[可更新的訂閱]** 頁面上選取 **[佇列變更且儘可能認可]** ，也需要此帳戶，因為 [新增訂閱精靈] 預設會將佇列更新設定為在必要時切換到立即更新。</span><span class="sxs-lookup"><span data-stu-id="4c33d-105">This account is required even if you selected **Queue changes and commit when possible** on the **Updatable Subscriptions** page, because by default the New Subscription Wizard configures queued updating with the ability to switch to immediate updating if required.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4c33d-106">對於複寫在發行集資料庫中建立的檢視，為連接指定的帳戶應該只被授與插入、更新及刪除資料的權限，而不應該被授與任何其他權限。</span><span class="sxs-lookup"><span data-stu-id="4c33d-106">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="4c33d-107">針對發行集資料庫中以 **syncobj_** _\<HexadecimalNumber>_ 格式命名的檢視，您在每一個訂閱者端所設定帳戶都應該被授與這些檢視的權限。</span><span class="sxs-lookup"><span data-stu-id="4c33d-107">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
 <span data-ttu-id="4c33d-108">此連接類型有三個選項可用：</span><span class="sxs-lookup"><span data-stu-id="4c33d-108">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="4c33d-109">您已定義的連結伺服器或遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c33d-109">A linked server or remote server that you have already defined.</span></span>  
  
-   <span data-ttu-id="4c33d-110">複寫建立的連結伺服器；以您在此精靈中指定的認證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="4c33d-110">A linked server that replication creates; the connection is made with the credentials you specify in this wizard.</span></span>  
  
-   <span data-ttu-id="4c33d-111">複寫建立的連結伺服器；以在訂閱者端執行變更的使用者認證來建立連接。</span><span class="sxs-lookup"><span data-stu-id="4c33d-111">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
 <span data-ttu-id="4c33d-112">此精靈中可以指定前兩個選項。</span><span class="sxs-lookup"><span data-stu-id="4c33d-112">The first two options can be specified in this wizard.</span></span> <span data-ttu-id="4c33d-113">您只能使用[sp_link_publication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)來指定最後一個選項;為參數指定**1**的值 **@security_mode** 。</span><span class="sxs-lookup"><span data-stu-id="4c33d-113">The last option can only be specified using [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql); specify a value of **1** for the parameter **@security_mode**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c33d-114">選項。</span><span class="sxs-lookup"><span data-stu-id="4c33d-114">Options</span></span>  
 <span data-ttu-id="4c33d-115">**建立使用下列 SQL Server 驗證登入進行連接的連結伺服器：**</span><span class="sxs-lookup"><span data-stu-id="4c33d-115">**Create a linked server that connects using the following SQL Server Authentication login:**</span></span>  
 <span data-ttu-id="4c33d-116">複寫會使用 **[登入]** 和 **[密碼]** 欄位中指定的認證，來建立連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c33d-116">Replication creates a linked server using the credentials specified in the **Login** and **Password** fields.</span></span>  
  
 <span data-ttu-id="4c33d-117">**登入**</span><span class="sxs-lookup"><span data-stu-id="4c33d-117">**Login**</span></span>  
 <span data-ttu-id="4c33d-118">輸入只具有此主題所描述權限的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="4c33d-118">Enter a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that has only the permissions described in this topic.</span></span>  
  
 <span data-ttu-id="4c33d-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="4c33d-119">**Password**</span></span>  
 <span data-ttu-id="4c33d-120">為 **[登入]** 中指定的登入輸入增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="4c33d-120">Enter a strong password for the login specified in **Login**.</span></span>  
  
 <span data-ttu-id="4c33d-121">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="4c33d-121">**Confirm Password**</span></span>  
 <span data-ttu-id="4c33d-122">重新輸入密碼，以確認密碼輸入正確</span><span class="sxs-lookup"><span data-stu-id="4c33d-122">Re-enter the password to confirm that it was entered correctly.</span></span>  
  
 <span data-ttu-id="4c33d-123">**使用您已定義的連結伺服器或遠端伺服器。**</span><span class="sxs-lookup"><span data-stu-id="4c33d-123">**Use a linked server or remote server that you have already defined.**</span></span>  
 <span data-ttu-id="4c33d-124">此選項需要您已定義的連結伺服器或遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c33d-124">This option requires a linked server or remote server that you have already defined.</span></span> <span data-ttu-id="4c33d-125">如需詳細資訊，請參閱[連結的伺服器 &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md) 和[遠端伺服器](../../database-engine/configure-windows/remote-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="4c33d-125">For more information, see [Linked Servers &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md) and [Remote Servers](../../database-engine/configure-windows/remote-servers.md).</span></span> <span data-ttu-id="4c33d-126">請確定連結伺服器或遠端伺服器使用的登入具有增強式密碼，且只具有此主題所描述的權限。</span><span class="sxs-lookup"><span data-stu-id="4c33d-126">Ensure that the login used for the linked server or remote server has a strong password and has only the permissions described in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c33d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c33d-127">See Also</span></span>  
 <span data-ttu-id="4c33d-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="4c33d-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="4c33d-129">[檢視及修改複寫安全性設定](security/view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="4c33d-129">[View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="4c33d-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4c33d-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="4c33d-131">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="4c33d-131">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
