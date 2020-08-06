---
title: SQL 寫入器服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- VDI [SQL Server]
- restoring [SQL Server], SQL Writer Service
- backups [SQL Server], while SQL Server running
- Volume Shadow Copy Service
- volume backups while running [SQL Server]
- Virtual Backup Device Interface [SQL Server]
- SQL Writer Service
- services [SQL Server], SQL Writer
- MSDE Writer
- VSS
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 310722c6617c7a2c9e0f384ec23ae371ab230536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585580"
---
# <a name="sql-writer-service"></a><span data-ttu-id="b664e-102">SQL 寫入器服務</span><span class="sxs-lookup"><span data-stu-id="b664e-102">SQL Writer Service</span></span>
  <span data-ttu-id="b664e-103">SQL 寫入器服務能透過「磁碟區陰影複製服務」架構，提供附加功能給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的備份和還原。</span><span class="sxs-lookup"><span data-stu-id="b664e-103">The SQL Writer Service provides added functionality for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the Volume Shadow Copy Service framework.</span></span>  
  
 <span data-ttu-id="b664e-104">系統會自動安裝 SQL 寫入器服務。</span><span class="sxs-lookup"><span data-stu-id="b664e-104">The SQL Writer Service is installed automatically.</span></span> <span data-ttu-id="b664e-105">當磁碟區陰影複製服務 (VSS) 應用程式要求備份或還原時，此服務必須已在執行中。</span><span class="sxs-lookup"><span data-stu-id="b664e-105">It must be running when the Volume Shadow Copy Service (VSS) application requests a backup or restore.</span></span> <span data-ttu-id="b664e-106">若要設定此服務，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services Applet。</span><span class="sxs-lookup"><span data-stu-id="b664e-106">To configure the service, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services applet.</span></span> <span data-ttu-id="b664e-107">SQL 寫入器服務會安裝在所有作業系統上。</span><span class="sxs-lookup"><span data-stu-id="b664e-107">The SQL Writer Service installs on all operating systems.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="b664e-108">目的</span><span class="sxs-lookup"><span data-stu-id="b664e-108">Purpose</span></span>  
 <span data-ttu-id="b664e-109">執行時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會鎖定並對資料檔案取得獨佔式存取。</span><span class="sxs-lookup"><span data-stu-id="b664e-109">When running, [!INCLUDE[ssDE](../../includes/ssde-md.md)] locks and has exclusive access to the data files.</span></span> <span data-ttu-id="b664e-110">未執行 SQL 寫入器服務時，Windows 中執行的備份程式沒有資料檔案的存取權，而且備份必須使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份來執行。</span><span class="sxs-lookup"><span data-stu-id="b664e-110">When the SQL Writer Service is not running, backup programs running in Windows do not have access to the data files, and backups must be performed using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup.</span></span>  
  
 <span data-ttu-id="b664e-111">使用 SQL 寫入器服務，以允許 Windows 備份程式於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行時複製 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b664e-111">Use the SQL Writer Service to permit Windows backup programs to copy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
## <a name="volume-shadow-copy-service"></a><span data-ttu-id="b664e-112">磁碟區陰影複製服務</span><span class="sxs-lookup"><span data-stu-id="b664e-112">Volume Shadow Copy Service</span></span>  
 <span data-ttu-id="b664e-113">VSS 是一組實作架構的 COM API，允許當系統上的應用程式寫入磁碟區的同時，仍能同時進行磁碟區備份作業。</span><span class="sxs-lookup"><span data-stu-id="b664e-113">The VSS is a set of COM APIs that implements a framework to allow volume backups to be performed while applications on a system continue to write to the volumes.</span></span> <span data-ttu-id="b664e-114">VSS 提供一致的介面，讓更新磁碟資料 (寫入者) 與備份應用程式 (要求者) 的使用者應用程式間可以取得協調。</span><span class="sxs-lookup"><span data-stu-id="b664e-114">The VSS provides a consistent interface that allows coordination between user applications that update data on disk (writers) and those that back up applications (requestors).</span></span>  
  
 <span data-ttu-id="b664e-115">VSS 能在不過度降低所提供服務的效能與穩定性之下，在執行中的系統，特別是伺服器上，擷取和複製可靠的影像以供備份。</span><span class="sxs-lookup"><span data-stu-id="b664e-115">The VSS captures and copies stable images for backup on running systems, particularly servers, without unduly degrading the performance and stability of the services they provide.</span></span> <span data-ttu-id="b664e-116">如需有關 VSS 的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="b664e-116">For more information on the VSS, see your Windows documentation.</span></span>  
  
## <a name="virtual-backup-device-interface-vdi"></a><span data-ttu-id="b664e-117">虛擬備份裝置介面 (VDI)</span><span class="sxs-lookup"><span data-stu-id="b664e-117">Virtual Backup Device Interface (VDI)</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b664e-118">提供一種稱為「虛擬備份裝置介面 (VDI)」的 API，可讓獨立軟體廠商將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 整合到他們的產品中，以對備份和還原作業提供支援。</span><span class="sxs-lookup"><span data-stu-id="b664e-118">provides an API called Virtual Backup Device Interface (VDI) that enables independent software vendors to integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into their products for providing support for backup and restore operations.</span></span> <span data-ttu-id="b664e-119">這些 API 可提供最高的可靠性與效能，並能支援所有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原功能，包括所有熱備份與快照集備份能力。</span><span class="sxs-lookup"><span data-stu-id="b664e-119">These APIs are engineered to provide maximum reliability and performance, and support the full range of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore functionality, including the full range of hot and snapshot backup capabilities.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="b664e-120">權限</span><span class="sxs-lookup"><span data-stu-id="b664e-120">Permissions</span></span>  
 <span data-ttu-id="b664e-121">SQL 寫入器服務必須以 **本機系統** 帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="b664e-121">The SQL Writer service must run under the **Local System** account.</span></span> <span data-ttu-id="b664e-122">SQL 寫入器服務使用 **NT Service\SQLWriter** 登入連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b664e-122">The SQL Writer service uses the **NT Service\SQLWriter** login to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b664e-123">使用 **NT Service\SQLWriter** 登入可讓 SQL 寫入器處理序在指定為 **沒有登入**的帳戶中，以較低權限層級執行，藉此限制漏洞。</span><span class="sxs-lookup"><span data-stu-id="b664e-123">Using the **NT Service\SQLWriter** login allows the SQL Writer process to run at a lower privilege level in an account designated as **no login**, which limits vulnerability.</span></span> <span data-ttu-id="b664e-124">如果停用 SQL 寫入器服務，則依賴 VSS 快照集的任何公用程式 (例如 System Center Data Protection Manager) 以及其他一些協力廠商產品都將損毀，更糟的情況會導致資料庫備份不一致的風險。</span><span class="sxs-lookup"><span data-stu-id="b664e-124">If the SQL Writer service is disabled, then any utility which in relies on VSS snapshots, such as System Center Data Protection Manager, as well as some other 3rd-party products, would be broken, or worse, at risk of taking backups of databases which were not consistent.</span></span> <span data-ttu-id="b664e-125">如果執行所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]系統或主機系統 (在虛擬機器的情況下) 只需要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 備份，則可以放心停用 SQL 寫入器服務並移除登入。</span><span class="sxs-lookup"><span data-stu-id="b664e-125">If neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the system it runs on, nor the host system (in the event of a virtual machine), need to use anything besides [!INCLUDE[tsql](../../includes/tsql-md.md)] backup, then the SQL Writer service can be safely disabled and the login removed.</span></span>  <span data-ttu-id="b664e-126">請注意，系統或磁碟區層級備份都可能叫用 SQL 寫入器服務，而不論備份是否直接以快照集為基礎。</span><span class="sxs-lookup"><span data-stu-id="b664e-126">Note that the SQL Writer service may be invoked by a system or volume level backup, whether the backup is directly snapshot-based or not.</span></span> <span data-ttu-id="b664e-127">某些系統備份產品使用 VSS 避免遭到開啟或鎖定檔案的封鎖。</span><span class="sxs-lookup"><span data-stu-id="b664e-127">Some system backup products use VSS to avoid being blocked by open or locked files.</span></span> <span data-ttu-id="b664e-128">由於 SQL 寫入器服務在活動過程中會暫時凍結 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的所有 I/O，因此 SQL 寫入器服務需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的更高權限。</span><span class="sxs-lookup"><span data-stu-id="b664e-128">The SQL Writer service needs elevated permissions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because in the course of its activities it briefly freezes all I/O for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="features"></a><span data-ttu-id="b664e-129">特性</span><span class="sxs-lookup"><span data-stu-id="b664e-129">Features</span></span>  
 <span data-ttu-id="b664e-130">SQL 寫入器支援：</span><span class="sxs-lookup"><span data-stu-id="b664e-130">SQL Writer supports:</span></span>  
  
-   <span data-ttu-id="b664e-131">完整的資料庫備份和還原，包括全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="b664e-131">Full database backup and restore including full-text catalogs</span></span>  
  
-   <span data-ttu-id="b664e-132">差異備份和還原</span><span class="sxs-lookup"><span data-stu-id="b664e-132">Differential backup and restore</span></span>  
  
-   <span data-ttu-id="b664e-133">以移動的方式還原</span><span class="sxs-lookup"><span data-stu-id="b664e-133">Restore with move</span></span>  
  
-   <span data-ttu-id="b664e-134">重新命名資料庫</span><span class="sxs-lookup"><span data-stu-id="b664e-134">Database rename</span></span>  
  
-   <span data-ttu-id="b664e-135">僅複製備份</span><span class="sxs-lookup"><span data-stu-id="b664e-135">Copy-only backup</span></span>  
  
-   <span data-ttu-id="b664e-136">自動復原資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="b664e-136">Auto-recovery of database snapshot</span></span>  
  
 <span data-ttu-id="b664e-137">SQL 寫入器不支援：</span><span class="sxs-lookup"><span data-stu-id="b664e-137">SQL Writer does not support:</span></span>  
  
-   <span data-ttu-id="b664e-138">記錄備份</span><span class="sxs-lookup"><span data-stu-id="b664e-138">Log backups</span></span>  
  
-   <span data-ttu-id="b664e-139">檔案與檔案群組備份</span><span class="sxs-lookup"><span data-stu-id="b664e-139">File and filegroup backup</span></span>  
  
-   <span data-ttu-id="b664e-140">分頁還原</span><span class="sxs-lookup"><span data-stu-id="b664e-140">Page restore</span></span>  
  
  
