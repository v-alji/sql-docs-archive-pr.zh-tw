---
title: 記錄讀取器代理程式安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4be41aa9135e20a334616b9cb9d76a773f8d0e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707370"
---
# <a name="log-reader-agent-security"></a><span data-ttu-id="d0892-102">記錄讀取器代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="d0892-102">Log Reader Agent Security</span></span>
  <span data-ttu-id="d0892-103">**[記錄讀取器代理程式安全性]** 對話方塊可以讓您指定：</span><span class="sxs-lookup"><span data-stu-id="d0892-103">The **Log Reader Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="d0892-104">記錄讀取器代理程式在散發者端執行所用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0892-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="d0892-105">Windows 帳戶也稱為 *處理帳戶*，因為代理程式處理是在這個帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="d0892-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="d0892-106">記錄讀取器代理程式連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者所用的內容。</span><span class="sxs-lookup"><span data-stu-id="d0892-106">The context under which the Log Reader Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="d0892-107">可以模擬 Windows 帳戶進行連接，或者在您指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶的內容下進行連接。</span><span class="sxs-lookup"><span data-stu-id="d0892-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0892-108">即使發行者與散發者都是在同一部電腦上，記錄讀取器代理程式仍會連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="d0892-108">The Log Reader Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="d0892-109">記錄讀取器代理程式也會連接到散發者；這些連接都會模擬代理程式執行所用的 Windows 帳戶來進行。</span><span class="sxs-lookup"><span data-stu-id="d0892-109">The Log Reader Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="d0892-110">對於 Oracle 發行者，請在 **[發行者屬性]** 對話方塊 (可以從 **[散發者屬性]** 對話方塊中存取) 中，指定記錄讀取器代理程式連接到發行者所用的內容。</span><span class="sxs-lookup"><span data-stu-id="d0892-110">For Oracle Publishers, specify the context under which the Log Reader Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="d0892-111">如需詳細資訊，請參閱 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="d0892-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="d0892-112">所有帳戶都必須有效，並且每個帳戶皆有指定正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="d0892-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="d0892-113">等到代理程式執行時，才會驗證帳戶與密碼。</span><span class="sxs-lookup"><span data-stu-id="d0892-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0892-114">選項。</span><span class="sxs-lookup"><span data-stu-id="d0892-114">Options</span></span>  
 <span data-ttu-id="d0892-115">**處理帳戶**</span><span class="sxs-lookup"><span data-stu-id="d0892-115">**Process account**</span></span>  
 <span data-ttu-id="d0892-116">輸入記錄讀取器代理程式在散發者端執行所用的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0892-116">Enter a Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="d0892-117">您指定的 Windows 帳戶，至少必須是散發資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d0892-117">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="d0892-118">**[密碼]** 與 **[確認密碼]**</span><span class="sxs-lookup"><span data-stu-id="d0892-118">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="d0892-119">輸入 Windows 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="d0892-119">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="d0892-120">**連接到發行者**</span><span class="sxs-lookup"><span data-stu-id="d0892-120">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="d0892-121">選擇記錄讀取器代理程式是否應模擬 **[處理帳戶]** 文字方塊中所指定的帳戶，還是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="d0892-121">Select whether the Log Reader Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="d0892-122">如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="d0892-122">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d0892-123">建議您選取模擬 Windows 帳戶，而非使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0892-123">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="d0892-124">用於連接的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶至少必須是發行集資料庫內 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d0892-124">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0892-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0892-125">See Also</span></span>  
 <span data-ttu-id="d0892-126">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="d0892-126">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="d0892-127">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="d0892-127">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="d0892-128">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d0892-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="d0892-129">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="d0892-129">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
