---
title: 保護散發者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Distributors
- Distributors [SQL Server replication], security
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d55f5e214f89b678367124da8342ec9801ab686a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584378"
---
# <a name="secure-the-distributor"></a><span data-ttu-id="00b0f-102">保護散發者</span><span class="sxs-lookup"><span data-stu-id="00b0f-102">Secure the Distributor</span></span>
  <span data-ttu-id="00b0f-103">下列複寫代理程式連接到「散發者」：記錄讀取代理程式、快照集代理程式、佇列讀取器代理程式、散發代理程式及合併代理程式。</span><span class="sxs-lookup"><span data-stu-id="00b0f-103">The following replication agents connect to the Distributor: the Log Reader Agent, Snapshot Agent, Queue Reader Agent, Distribution Agent, and Merge Agent.</span></span> <span data-ttu-id="00b0f-104">為遵循授與所需最小權限的原則，並同時保護所有密碼的儲存，有必要為這些代理程式中的每一個提供適當的登入。</span><span class="sxs-lookup"><span data-stu-id="00b0f-104">It is important to provide an appropriate login for each of these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords:</span></span>  
  
-   <span data-ttu-id="00b0f-105">如需管理登入和密碼的資訊，請參閱[管理複寫的登入與密碼](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)。</span><span class="sxs-lookup"><span data-stu-id="00b0f-105">For information about managing logins and passwords, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="00b0f-106">如需各代理程式所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="00b0f-106">For detailed information about the permissions required for each agent, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span>  
  
 <span data-ttu-id="00b0f-107">除了正確管理登入與密碼外，還有必要了解 **repl_distributor** 遠端伺服器連結的角色與 **distributor_admin** 帳戶。</span><span class="sxs-lookup"><span data-stu-id="00b0f-107">In addition to managing logins and passwords appropriately, it is important to understand the role of the **repl_distributor** remote server link and the **distributor_admin** account.</span></span>  
  
## <a name="securing-the-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="00b0f-108">設定從發行者到散發者連接的安全性</span><span class="sxs-lookup"><span data-stu-id="00b0f-108">Securing the Connection from the Publisher to the Distributor</span></span>  
 <span data-ttu-id="00b0f-109">為了支援管理預存程序在「發行者」端執行並在「散發者」端更新資訊時的必要通訊，複寫會自動設定遠端伺服器 **repl_distributor**。</span><span class="sxs-lookup"><span data-stu-id="00b0f-109">To support the communication necessary when administrative stored procedures execute at the Publisher and update information at the Distributor, replication automatically configures the remote server **repl_distributor**.</span></span> <span data-ttu-id="00b0f-110">不管散發資料庫是包含在「發行者」執行個體 (本機「散發者」) 內還是位於遠端 **執行個體 (遠端「散發者」) 內，** repl_distributor [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 遠端伺服器項目都會用於至散發資料庫的通訊。</span><span class="sxs-lookup"><span data-stu-id="00b0f-110">The **repl_distributor** remote server entry is used for communication to the distribution database regardless of whether the distribution database is contained within the Publisher instance (a local Distributor) or resides within a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance (a remote Distributor).</span></span>  
  
 <span data-ttu-id="00b0f-111">當散發資料庫包含在本機執行個體上時，系統會自動產生並設定一個隨機密碼。</span><span class="sxs-lookup"><span data-stu-id="00b0f-111">When the distribution database is contained on a local instance, a random password is generated and configured automatically.</span></span> <span data-ttu-id="00b0f-112">當散發資料庫位於遠端執行個體時，管理員會在設定「發行者」與「散發者」期間設定一個共用密碼；然後用這個密碼來提供往返於 **repl_distributor** 連結之傳輸量的驗證。</span><span class="sxs-lookup"><span data-stu-id="00b0f-112">When the distribution database is located on a remote instance, the administrator configures a shared password during setup of the Publisher and Distributor; this password is then used to provide authentication of traffic that traverses the **repl_distributor** link.</span></span>  
  
 <span data-ttu-id="00b0f-113">「散發者」使用 **repl_distributor** 遠端伺服器項目來確認呼叫伺服器已在「散發者」端設定為「發行者」，驗證「發行者」提供的密碼，並驗證預存程序在執行期間為複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="00b0f-113">The Distributor uses the **repl_distributor** remote server entry to verify that the calling server is configured as a Publisher at the Distributor, validates the password supplied by the Publisher, and validates that the stored procedure is a replication stored procedure during execution.</span></span>  
  
 <span data-ttu-id="00b0f-114">在設定期間為 **repl_distributor** 遠端伺服器項目設定的密碼與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入 ( **distributor_admin**，已新增到「散發者」端的 **sysadmin** 固定伺服器角色) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="00b0f-114">The password configured for the **repl_distributor** remote server entry during setup is associated with a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login, **distributor_admin**, which is added to the **sysadmin** fixed server role at the Distributor.</span></span> <span data-ttu-id="00b0f-115">連接到「散發者」時， **distributor_admin** 登入由複寫預存程序使用。</span><span class="sxs-lookup"><span data-stu-id="00b0f-115">The **distributor_admin** login is used by replication stored procedures when connecting to the Distributor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00b0f-116">請勿手動變更 **distributor_admin** 的密碼。</span><span class="sxs-lookup"><span data-stu-id="00b0f-116">Do not change the password for the **distributor_admin** manually.</span></span> <span data-ttu-id="00b0f-117">請始終使用 **sp_changedistributor_password** 預存程序，或 **中** [散發者屬性] **或** [更新複寫密碼] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]對話方塊，因為密碼變更稍後會自動套用到本機發行集。</span><span class="sxs-lookup"><span data-stu-id="00b0f-117">Always use the **sp_changedistributor_password** stored procedure, or the **Distributor Properties** or **Update Replication Passwords** dialog boxes in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], because password changes are then applied to local publications automatically.</span></span>  
  
## <a name="snapshot-folder-security"></a><span data-ttu-id="00b0f-118">快照集資料夾安全性</span><span class="sxs-lookup"><span data-stu-id="00b0f-118">Snapshot Folder Security</span></span>  
 <span data-ttu-id="00b0f-119">確定快照集共用已將讀取權限授與「合併代理程式」(針對合併式複寫) 或「散發代理程式」(針對快照式或異動複寫) 執行時所使用的帳戶，並且已將寫入權限授與「快照集代理程式」執行時所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="00b0f-119">Ensure that the snapshot share has read access granted to the account under which the Merge Agent (for merge replication) or Distribution Agent (for snapshot or transactional replication) runs and write access granted to the account under which the Snapshot Agent runs.</span></span> <span data-ttu-id="00b0f-120">如需快照集資料夾的詳細資訊，請參閱[保護快照集資料夾](secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="00b0f-120">For more information about the snapshot folder, see [Secure the Snapshot Folder](secure-the-snapshot-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b0f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b0f-121">See Also</span></span>  
 <span data-ttu-id="00b0f-122">[檢視及修改複寫安全性設定](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="00b0f-122">[View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="00b0f-123">[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="00b0f-123">[Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="00b0f-124">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="00b0f-124">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="00b0f-125">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="00b0f-125">SQL Server Replication Security</span></span>](view-and-modify-replication-security-settings.md)  
  
  
