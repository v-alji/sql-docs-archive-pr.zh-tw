---
title: 資料庫檔案立即初始化 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
ms.openlocfilehash: dedd2c5b8d075dee8aeeb438904137558c664d95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595106"
---
# <a name="database-instant-file-initialization"></a><span data-ttu-id="4c0cc-102">資料庫立即檔案初始化</span><span class="sxs-lookup"><span data-stu-id="4c0cc-102">Database Instant File Initialization</span></span>
  <span data-ttu-id="4c0cc-103">系統會將資料和記錄檔初始化，以覆寫磁碟上先前刪除之檔案中所遺留的任何現有資料。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-103">Data and log files are initialized to overwrite any existing data left on the disk from previously deleted files.</span></span> <span data-ttu-id="4c0cc-104">資料檔和記錄檔初始化的方式是先在您執行下列作業之一時，在檔案中填入 0：</span><span class="sxs-lookup"><span data-stu-id="4c0cc-104">Data and log files are first initialized by filling the files with zeros when you perform one of the following operations:</span></span>  
  
-   <span data-ttu-id="4c0cc-105">建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-105">Create a database.</span></span>  
  
-   <span data-ttu-id="4c0cc-106">新增檔案、記錄或資料到現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-106">Add files, log or data, to an existing database.</span></span>  
  
-   <span data-ttu-id="4c0cc-107">增加現有檔案的大小 (包括自動成長作業)。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-107">Increase the size of an existing file (including autogrow operations).</span></span>  
  
-   <span data-ttu-id="4c0cc-108">還原資料庫或檔案群組。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-108">Restore a database or filegroup.</span></span>  
  
 <span data-ttu-id="4c0cc-109">檔案初始化會導致這些作業需要較長的時間。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-109">File initialization causes these operations to take longer.</span></span> <span data-ttu-id="4c0cc-110">不過，當資料第一次寫入檔案時，作業系統並不需要在檔案中填入 0。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-110">However, when data is written to the files for the first time, the operating system does not have to fill the files with zeros.</span></span>  
  
## <a name="instant-file-initialization"></a><span data-ttu-id="4c0cc-111">立即檔案初始化</span><span class="sxs-lookup"><span data-stu-id="4c0cc-111">Instant File Initialization</span></span>  
 <span data-ttu-id="4c0cc-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，資料檔可以立即初始化。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-112">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data files can be initialized instantaneously.</span></span> <span data-ttu-id="4c0cc-113">這可以加快先前提到之檔案作業的執行速度。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-113">This allows for fast execution of the previously mentioned file operations.</span></span> <span data-ttu-id="4c0cc-114">立即檔案初始化會回收使用的磁碟空間，卻不會在該空間中填入零。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-114">Instant file initialization reclaims used disk space without filling that space with zeros.</span></span> <span data-ttu-id="4c0cc-115">而是在新資料寫入檔案時將磁碟內容覆寫為新資料。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-115">Instead, disk content is overwritten as new data is written to the files.</span></span> <span data-ttu-id="4c0cc-116">記錄檔無法立即初始化。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-116">Log files cannot be initialized instantaneously.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c0cc-117">檔案立即初始化只在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] 或 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 或更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-117">Instant file initialization is available only on [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] or [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="4c0cc-118">只有在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) 服務帳戶被授與 SE_MANAGE_VOLUME_NAME 時，才能使用立即檔案初始化。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-118">Instant file initialization is only available if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) service account has been granted SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="4c0cc-119">Windows Administrator 群組的成員擁有此權限，並可將此權限授與其他使用者 (方法是將他們新增到「執行磁碟區維護工作」  安全性原則。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-119">Members of the Windows Administrator group have this right and can grant it to other users by adding them to the **Perform Volume Maintenance Tasks** security policy.</span></span> <span data-ttu-id="4c0cc-120">如需指派使用者權限的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-120">For more information about assigning user rights, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="4c0cc-121">當 TDE 啟用時，無法使用立即檔案初始化。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-121">Instant file initialization is not available when TDE is enabled.</span></span>  
  
 <span data-ttu-id="4c0cc-122">授與帳戶「 `Perform volume maintenance tasks` 」權限：</span><span class="sxs-lookup"><span data-stu-id="4c0cc-122">To grant an account the `Perform volume maintenance tasks` permission:</span></span>  
  
1.  <span data-ttu-id="4c0cc-123">在將建立備份檔案的電腦上，開啟「`Local Security Policy`」應用程式 (`secpol.msc`)。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-123">On the computer where the backup file will be created, open the `Local Security Policy` application (`secpol.msc`).</span></span>  
  
2.  <span data-ttu-id="4c0cc-124">在左窗格中，展開 [本機原則] ，然後按一下 [使用者權限指派] 。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-124">In the left pane, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
3.  <span data-ttu-id="4c0cc-125">在右窗格中，按兩下 [執行磁碟區維護工作]。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-125">In the right pane, double-click **Perform volume maintenance tasks**.</span></span>  
  
4.  <span data-ttu-id="4c0cc-126">按一下 [新增使用者或群組] \*\*\*\* ，新增用於備份的任何使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-126">Click **Add User or Group** and add any user accounts that are used for backups.</span></span>  
  
5.  <span data-ttu-id="4c0cc-127">按一下 **[** 套用]，然後關閉所有 `Local Security Policy` 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-127">Click **Apply**, and then close all `Local Security Policy` dialog boxes.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="4c0cc-128">安全性考量</span><span class="sxs-lookup"><span data-stu-id="4c0cc-128">Security Considerations</span></span>  
 <span data-ttu-id="4c0cc-129">刪除的磁碟內容只有在新資料寫入檔案時才會被覆寫，因此，未經授權的主體可能會存取刪除的內容。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-129">Because the deleted disk content is overwritten only as new data is written to the files, the deleted content might be accessed by an unauthorized principal.</span></span> <span data-ttu-id="4c0cc-130">當資料庫檔案附加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體後，檔案上的任意存取控制清單 (DACL) 可降低此一資訊洩漏威脅。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-130">While the database file is attached to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this information disclosure threat is reduced by the discretionary access control list (DACL) on the file.</span></span> <span data-ttu-id="4c0cc-131">此 DACL 只允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和本機系統管理員存取檔案。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-131">This DACL allows file access only to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the local administrator.</span></span> <span data-ttu-id="4c0cc-132">但是當檔案卸離後，沒有 SE_MANAGE_VOLUME_NAME 的使用者或服務便能存取該檔案。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-132">However, when the file is detached, it may be accessed by a user or service that does not have SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="4c0cc-133">備份資料庫時也存在類似的威脅。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-133">A similar threat exists when the database is backed up.</span></span> <span data-ttu-id="4c0cc-134">如果備份檔案未使用適當的 DACL 保護，未經授權的使用者或服務便可存取刪除的內容。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-134">The deleted content can become available to an unauthorized user or service if the backup file is not protected with an appropriate DACL.</span></span>  
  
 <span data-ttu-id="4c0cc-135">如果洩漏刪除的內容可能是一項隱憂，您應該採取下列其中一項或兩項方法：</span><span class="sxs-lookup"><span data-stu-id="4c0cc-135">If the potential for disclosing deleted content is a concern, you should do one or both of the following:</span></span>  
  
-   <span data-ttu-id="4c0cc-136">務必確保所有卸離的資料檔和備份檔都具有限制的 DACL。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-136">Always make sure that any detached data files and backup files have restrictive DACLs.</span></span>  
  
-   <span data-ttu-id="4c0cc-137">停用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的立即檔案初始化，方法是從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶撤銷 SE_MANAGE_VOLUME_NAME。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-137">Disable instant file initialization for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by revoking SE_MANAGE_VOLUME_NAME from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c0cc-138">停用立即檔案初始化只會影響使用者權限撤銷後建立或大小增加的檔案。</span><span class="sxs-lookup"><span data-stu-id="4c0cc-138">Disabling instant file initialization only affects files that are created or increased in size after the user right is revoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0cc-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c0cc-139">See Also</span></span>  
 [<span data-ttu-id="4c0cc-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4c0cc-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
