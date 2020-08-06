---
title: Resource 資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595096"
---
# <a name="resource-database"></a><span data-ttu-id="9691d-102">Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="9691d-102">Resource Database</span></span>
  <span data-ttu-id="9691d-103">Resource 資料庫是一個唯讀的資料庫，其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]擁有的所有系統物件。</span><span class="sxs-lookup"><span data-stu-id="9691d-103">The Resource database is a read-only database that contains all the system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9691d-104">系統物件 (例如 sys.objects) 實際上會保存在 Resource 資料庫中，但邏輯上會出現在每個資料庫的 sys 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="9691d-104">system objects, such as sys.objects, are physically persisted in the Resource database, but they logically appear in the sys schema of every database.</span></span> <span data-ttu-id="9691d-105">Resource 資料庫不包含使用者資料或使用者中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9691d-105">The Resource database does not contain user data or user metadata.</span></span>  
  
 <span data-ttu-id="9691d-106">Resource 資料庫讓升級為新版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的程序變得更快且更容易。</span><span class="sxs-lookup"><span data-stu-id="9691d-106">The Resource database makes upgrading to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an easier and faster procedure.</span></span> <span data-ttu-id="9691d-107">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，升級需要卸除和建立系統物件。</span><span class="sxs-lookup"><span data-stu-id="9691d-107">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], upgrading required dropping and creating system objects.</span></span> <span data-ttu-id="9691d-108">由於 Resource 資料庫檔案包含所有系統物件，因此現在只要將單一 Resource 資料庫檔案複製到本機伺服器即可完成升級。</span><span class="sxs-lookup"><span data-stu-id="9691d-108">Because the Resource database file contains all system objects, an upgrade is now accomplished simply by copying the single Resource database file to the local server.</span></span>  
  
## <a name="physical-properties-of-resource"></a><span data-ttu-id="9691d-109">Resource 的實體屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-109">Physical Properties of Resource</span></span>  
 <span data-ttu-id="9691d-110">Resource 資料庫的實體檔案名稱為 mssqlsystemresource.mdf 和 mssqlsystemresource.ldf。</span><span class="sxs-lookup"><span data-stu-id="9691d-110">The physical file names of the Resource database are mssqlsystemresource.mdf and mssqlsystemresource.ldf.</span></span> <span data-ttu-id="9691d-111">這些檔案位於 \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\，因此不應移動。</span><span class="sxs-lookup"><span data-stu-id="9691d-111">These files are located in \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ and should not be moved.</span></span> <span data-ttu-id="9691d-112">每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體只有一個相關聯的 mssqlsystemresource.mdf 檔案，而且這些執行個體不共用此檔案。</span><span class="sxs-lookup"><span data-stu-id="9691d-112">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one and only one associated mssqlsystemresource.mdf file, and instances do not share this file.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9691d-113">升級和 Service Pack 有時會提供新的資源資料庫，其會安裝到 BINN 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9691d-113">Upgrades and service packs sometimes provide a new resource database which is installed to the BINN folder.</span></span> <span data-ttu-id="9691d-114">變更資源資料庫的位置不受支援，亦不建議。</span><span class="sxs-lookup"><span data-stu-id="9691d-114">Changing the location of the resource database is not supported or recommended.</span></span>  
  
## <a name="backing-up-and-restoring-the-resource-database"></a><span data-ttu-id="9691d-115">備份與還原 Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="9691d-115">Backing Up and Restoring the Resource Database</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9691d-116">無法備份 Resource 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9691d-116">cannot back up the Resource database.</span></span> <span data-ttu-id="9691d-117">您可以將 mssqlsystemresource.mdf 檔視為二進位 (.EXE) 檔案而非資料庫檔案，藉以進行以檔案為基礎或以磁碟為基礎的備份，不過您無法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來還原備份。</span><span class="sxs-lookup"><span data-stu-id="9691d-117">You can perform your own file-based or a disk-based backup by treating the mssqlsystemresource.mdf file as if it were a binary (.EXE) file, rather than a database file, but you cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to restore your backups.</span></span> <span data-ttu-id="9691d-118">還原 mssqlsystemresource.mdf 的備份副本只能手動完成，而且您必須小心不要使用過期或可能不安全的 Resource 資料庫來覆寫目前的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9691d-118">Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current Resource database with an out-of-date or potentially insecure version.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9691d-119">還原 mssqlsystemresource.mdf 的備份後，您必須重新套用任何後續的更新。</span><span class="sxs-lookup"><span data-stu-id="9691d-119">After restoring a backup of mssqlsystemresource.mdf, you must reapply any subsequent updates.</span></span>  
  
## <a name="accessing-the-resource-database"></a><span data-ttu-id="9691d-120">存取 Resource 資料庫</span><span class="sxs-lookup"><span data-stu-id="9691d-120">Accessing the Resource Database</span></span>  
 <span data-ttu-id="9691d-121">Resource 資料庫僅能由 Microsoft 客戶支援服務 (CSS) 的專業人員修改或在他們的指示下修改。</span><span class="sxs-lookup"><span data-stu-id="9691d-121">The Resource database should only be modified by or at the direction of a Microsoft Customer Support Services (CSS) specialist.</span></span> <span data-ttu-id="9691d-122">Resource 資料庫的識別碼一律為 32767。</span><span class="sxs-lookup"><span data-stu-id="9691d-122">The ID of the Resource database is always 32767.</span></span> <span data-ttu-id="9691d-123">其他與 Resource 資料庫相關聯的重要值是版本號碼以及上次更新資料庫的時間。</span><span class="sxs-lookup"><span data-stu-id="9691d-123">Other important values associated with the Resource database are the version number and the last time that the database was updated.</span></span>  
  
 <span data-ttu-id="9691d-124">**若要判斷** Resource **資料庫的版本號碼，請使用**：</span><span class="sxs-lookup"><span data-stu-id="9691d-124">**To determine the version number of the** Resource **database, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 <span data-ttu-id="9691d-125">**若要判斷** Resource **資料庫上次更新的時間，請使用**：</span><span class="sxs-lookup"><span data-stu-id="9691d-125">**To determine when the** Resource **database was last updated, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 <span data-ttu-id="9691d-126">**若要存取系統物件的 SQL 定義，請使用 OBJECT_DEFINITION 函數：**</span><span class="sxs-lookup"><span data-stu-id="9691d-126">**To access SQL definitions of system objects, use the OBJECT_DEFINITION function:**</span></span>  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="9691d-127">相關內容</span><span class="sxs-lookup"><span data-stu-id="9691d-127">Related Content</span></span>  
 [<span data-ttu-id="9691d-128">系統資料庫</span><span class="sxs-lookup"><span data-stu-id="9691d-128">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="9691d-129">資料庫管理員的診斷連接</span><span class="sxs-lookup"><span data-stu-id="9691d-129">Diagnostic Connection for Database Administrators</span></span>](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [<span data-ttu-id="9691d-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9691d-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [<span data-ttu-id="9691d-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9691d-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [<span data-ttu-id="9691d-132">以單一使用者模式啟動 SQL Server</span><span class="sxs-lookup"><span data-stu-id="9691d-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
