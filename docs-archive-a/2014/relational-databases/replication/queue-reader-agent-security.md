---
title: 佇列讀取器代理程式安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22a5e5751184b626ab1af86f01782a42028b5ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599475"
---
# <a name="queue-reader-agent-security"></a><span data-ttu-id="d542c-102">佇列讀取器代理程式安全性</span><span class="sxs-lookup"><span data-stu-id="d542c-102">Queue Reader Agent Security</span></span>
  <span data-ttu-id="d542c-103">**[佇列讀取器代理程式安全性]** 對話方塊，可以讓您指定執行佇列讀取器代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶，以及進行本機連接到散發者。</span><span class="sxs-lookup"><span data-stu-id="d542c-103">The **Queue Reader Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Queue Reader Agent runs and makes local connections to the Distributor.</span></span> <span data-ttu-id="d542c-104">代理程式會使用 **[發行者屬性]** 對話方塊 (可從 **[散發者屬性]** 對話方塊取得) 指定的帳戶，來連接到發行者；另外，代理程式會使用與散發代理程式用於訂閱的相同內容，來連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="d542c-104">The agent connects to the Publisher using the account specified in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box); the agent connects to the Subscriber using the same context as the Distribution Agent for the subscription.</span></span> <span data-ttu-id="d542c-105">如需詳細資訊，請參閱 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="d542c-105">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="d542c-106">帳戶必須有效，並且要指定正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="d542c-106">The account must be valid with the correct password specified.</span></span> <span data-ttu-id="d542c-107">等到代理程式執行時，才會驗證帳戶與密碼。</span><span class="sxs-lookup"><span data-stu-id="d542c-107">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d542c-108">選項。</span><span class="sxs-lookup"><span data-stu-id="d542c-108">Options</span></span>  
 <span data-ttu-id="d542c-109">**處理帳戶**</span><span class="sxs-lookup"><span data-stu-id="d542c-109">**Process account**</span></span>  
 <span data-ttu-id="d542c-110">輸入在散發者端執行佇列讀取器代理程式的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d542c-110">Enter a Windows account under which the Queue Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="d542c-111">您指定的 Windows 帳戶，至少必須是散發資料庫中之 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d542c-111">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="d542c-112">**[密碼]** 與 **[確認密碼]**</span><span class="sxs-lookup"><span data-stu-id="d542c-112">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="d542c-113">輸入 Windows 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="d542c-113">Enter the password for the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d542c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d542c-114">See Also</span></span>  
 <span data-ttu-id="d542c-115">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="d542c-115">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="d542c-116">[複寫代理程式安全性模型](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="d542c-116">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="d542c-117">[複寫代理程式概觀](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d542c-117">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="d542c-118">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="d542c-118">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
