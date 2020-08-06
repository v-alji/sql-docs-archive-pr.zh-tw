---
title: 快照集代理程式安全性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 288dc294b7ace9ea5cb098c8deec53c3ae4569a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606745"
---
# <a name="snapshot-agent-security"></a><span data-ttu-id="d3a28-102">快照集代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="d3a28-102">Snapshot Agent Security</span></span>
  <span data-ttu-id="d3a28-103">**[快照集代理程式安全性]** 對話方塊可讓您指定：</span><span class="sxs-lookup"><span data-stu-id="d3a28-103">The **Snapshot Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="d3a28-104">在散發者端執行快照集代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d3a28-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="d3a28-105">Windows 帳戶也稱為 *處理帳戶*，因為代理程式處理是在這個帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="d3a28-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="d3a28-106">快照集代理程式用於連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者的內容。</span><span class="sxs-lookup"><span data-stu-id="d3a28-106">The context under which the Snapshot Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="d3a28-107">可以模擬 Windows 帳戶進行連接，或者在您指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶的內容下進行連接。</span><span class="sxs-lookup"><span data-stu-id="d3a28-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3a28-108">即使發行者和散發者不在同一部電腦上，快照集代理程式也會連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="d3a28-108">The Snapshot Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="d3a28-109">快照集代理程式也會連接到散發者；這些連接一律會藉由模擬執行代理程式的 Windows 帳戶來進行。</span><span class="sxs-lookup"><span data-stu-id="d3a28-109">The Snapshot Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="d3a28-110">針對 Oracle 發行者，請在 **[發行者屬性]** 對話方塊 (可從 **[散發者屬性]** 對話方塊中取得) 中指定快照集代理程式連接到發行者的內容。</span><span class="sxs-lookup"><span data-stu-id="d3a28-110">For Oracle Publishers, specify the context under which the Snapshot Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="d3a28-111">如需詳細資訊，請參閱 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="d3a28-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="d3a28-112">所有帳戶都必須有效，並且每個帳戶皆有指定正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="d3a28-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="d3a28-113">等到代理程式執行時，才會驗證帳戶與密碼。</span><span class="sxs-lookup"><span data-stu-id="d3a28-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d3a28-114">選項。</span><span class="sxs-lookup"><span data-stu-id="d3a28-114">Options</span></span>  
 <span data-ttu-id="d3a28-115">**處理帳戶**</span><span class="sxs-lookup"><span data-stu-id="d3a28-115">**Process account**</span></span>  
 <span data-ttu-id="d3a28-116">輸入在散發者端執行快照集代理程式的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d3a28-116">Enter a Windows account under which the Snapshot Agent runs at the Distributor.</span></span> <span data-ttu-id="d3a28-117">您指定的 Windows 帳戶必須：</span><span class="sxs-lookup"><span data-stu-id="d3a28-117">The Windows account you specify must:</span></span>  
  
-   <span data-ttu-id="d3a28-118">至少是散發資料庫中 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d3a28-118">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
-   <span data-ttu-id="d3a28-119">擁有快照集共用上的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="d3a28-119">Have write permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="d3a28-120">**[密碼]** 與 **[確認密碼]**</span><span class="sxs-lookup"><span data-stu-id="d3a28-120">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="d3a28-121">輸入 Windows 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="d3a28-121">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="d3a28-122">**連接到發行者**</span><span class="sxs-lookup"><span data-stu-id="d3a28-122">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="d3a28-123">選取快照集代理程式是藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶、或藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="d3a28-123">Select whether the Snapshot Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="d3a28-124">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="d3a28-124">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3a28-125">建議您選取模擬 Windows 帳戶，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d3a28-125">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="d3a28-126">用於連接的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶至少必須是發行集資料庫內 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d3a28-126">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a28-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3a28-127">See Also</span></span>  
 <span data-ttu-id="d3a28-128">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="d3a28-128">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="d3a28-129">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3a28-129">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="d3a28-130">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d3a28-130">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="d3a28-131">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="d3a28-131">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
