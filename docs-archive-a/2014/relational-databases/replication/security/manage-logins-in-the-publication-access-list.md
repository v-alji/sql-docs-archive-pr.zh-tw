---
title: 管理發行集存取清單中的登入 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593923"
---
# <a name="manage-logins-in-the-publication-access-list"></a><span data-ttu-id="16cf0-102">管理發行集存取清單中的登入</span><span class="sxs-lookup"><span data-stu-id="16cf0-102">Manage Logins in the Publication Access List</span></span>
  <span data-ttu-id="16cf0-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中管理發行集存取清單內的登入。</span><span class="sxs-lookup"><span data-stu-id="16cf0-103">This topic describes how to manage logins in the Publication Access List in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="16cf0-104">發行集的存取是由發行集存取清單 (PAL) 所控制。</span><span class="sxs-lookup"><span data-stu-id="16cf0-104">Access to a publication is controlled by the publication access list (PAL).</span></span> <span data-ttu-id="16cf0-105">可以從 PAL 中加入及移除登入和群組。</span><span class="sxs-lookup"><span data-stu-id="16cf0-105">Logins and groups can be added and removed from the PAL.</span></span>  
  
 <span data-ttu-id="16cf0-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="16cf0-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="16cf0-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="16cf0-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="16cf0-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="16cf0-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="16cf0-109">**若要管理發行集存取清單中的登入，請使用：**</span><span class="sxs-lookup"><span data-stu-id="16cf0-109">**To manage logins in the Publication Access List, using:**</span></span>  
  
     [<span data-ttu-id="16cf0-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16cf0-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="16cf0-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16cf0-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="16cf0-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="16cf0-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="16cf0-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="16cf0-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="16cf0-114">您必須先將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入與發行集資料庫中的資料庫使用者產生關聯，才能將該登入加入 PAL 中。</span><span class="sxs-lookup"><span data-stu-id="16cf0-114">You must associate the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login with a database user in the publication database before you add the login to the PAL.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="16cf0-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16cf0-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="16cf0-116">您可利用發行集存取清單 (PAL) 來管理登入，此清單位於 [發行集屬性 - \<Publication>] 對話方塊的 [發行集存取清單] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="16cf0-116">You use the publication access list (PAL) on the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box to manage logins.</span></span> <span data-ttu-id="16cf0-117">如需存取這個對話方塊的詳細資訊，請參閱[檢視和修改發行集屬性](../publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="16cf0-117">For more information about how to access this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-manage-logins-in-the-pal"></a><span data-ttu-id="16cf0-118">若要在 PAL 中管理登入</span><span class="sxs-lookup"><span data-stu-id="16cf0-118">To manage logins in the PAL</span></span>  
  
1.  <span data-ttu-id="16cf0-119">在 [發行集屬性 - \<Publication>] 對話方塊的 [發行集存取清單] 頁面中，使用 [新增]、[移除] 和 [全部移除] 按鈕在 PAL 新增及移除登入和群組。</span><span class="sxs-lookup"><span data-stu-id="16cf0-119">On the **Publication Access List** page of the **Publication Properties - \<Publication>** dialog box, use the **Add**, **Remove**, and **Remove All** buttons to add and remove logins and groups from the PAL.</span></span> <span data-ttu-id="16cf0-120">請不要從 PAL 移除 **distributor_admin** 。</span><span class="sxs-lookup"><span data-stu-id="16cf0-120">Do not remove **distributor_admin** from the PAL.</span></span> <span data-ttu-id="16cf0-121">此帳戶由複寫使用。</span><span class="sxs-lookup"><span data-stu-id="16cf0-121">This account is used by replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16cf0-122">如果使用遠端散發者，則 PAL 中的帳戶在發行者和散發者兩端都必須是可以使用的。</span><span class="sxs-lookup"><span data-stu-id="16cf0-122">If a remote Distributor is used, accounts in the PAL must be available at both the Publisher and the Distributor.</span></span> <span data-ttu-id="16cf0-123">該帳戶必須是在兩部伺服器都已定義的網域帳戶或本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="16cf0-123">The account must be either a domain account or a local account that is defined at both servers.</span></span> <span data-ttu-id="16cf0-124">與兩個登入相關聯的密碼必須是一樣的。</span><span class="sxs-lookup"><span data-stu-id="16cf0-124">The passwords that are associated with both logins must be the same.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="16cf0-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16cf0-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a><span data-ttu-id="16cf0-126">檢視屬於 PAL 的群組和登入</span><span class="sxs-lookup"><span data-stu-id="16cf0-126">To view groups and logins that belong to the PAL</span></span>  
  
1.  <span data-ttu-id="16cf0-127">在發行集資料庫的發行者上，執行 [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="16cf0-127">At the Publisher on the publication database, execute [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql).</span></span> <span data-ttu-id="16cf0-128">針對 [ \*\* \@ 發行\*\*集]，指定發行集名稱。</span><span class="sxs-lookup"><span data-stu-id="16cf0-128">For **\@publication**, specify the publication name.</span></span> <span data-ttu-id="16cf0-129">這樣會顯示有關 PAL 中群組和登入的資訊。</span><span class="sxs-lookup"><span data-stu-id="16cf0-129">This displays information about the groups and logins in the PAL.</span></span>  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a><span data-ttu-id="16cf0-130">將群組和登入加入 PAL</span><span class="sxs-lookup"><span data-stu-id="16cf0-130">To add groups and logins to the PAL</span></span>  
  
1.  <span data-ttu-id="16cf0-131">在發行集資料庫的發行者上，執行 [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="16cf0-131">At the Publisher on the publication database, execute [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql).</span></span> <span data-ttu-id="16cf0-132">針對 [ \*\* \@ 發行**集] 指定發行集名稱，並針對** \@ [登\*\*入] 指定要加入之登入或群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="16cf0-132">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being added.</span></span>  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a><span data-ttu-id="16cf0-133">從 PAL 中移除群組和登入</span><span class="sxs-lookup"><span data-stu-id="16cf0-133">To remove groups and logins from the PAL</span></span>  
  
1.  <span data-ttu-id="16cf0-134">在發行集資料庫的發行者上，執行 [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="16cf0-134">At the Publisher on the publication database, execute [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql).</span></span> <span data-ttu-id="16cf0-135">針對 [ \*\* \@ 發行**集] 指定發行集名稱，並針對** \@ [登\*\*入] 指定要移除之登入或群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="16cf0-135">For **\@publication**, specify the publication name; and for **\@login**, specify the name of the login or group that is being removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cf0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16cf0-136">See Also</span></span>  
 <span data-ttu-id="16cf0-137">[複寫代理程式安全性模型](replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="16cf0-137">[Replication Agent Security Model](replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="16cf0-138">[保護複寫拓撲](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="16cf0-138">[Secure a Replication Topology](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="16cf0-139">保護發行者</span><span class="sxs-lookup"><span data-stu-id="16cf0-139">Secure the Publisher</span></span>](secure-the-publisher.md)  
  
  
