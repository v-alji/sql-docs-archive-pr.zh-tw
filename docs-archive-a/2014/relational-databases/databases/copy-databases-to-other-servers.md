---
title: 複製資料庫至其他伺服器 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699769"
---
# <a name="copy-databases-to-other-servers"></a><span data-ttu-id="563e2-102">複製資料庫至其他伺服器</span><span class="sxs-lookup"><span data-stu-id="563e2-102">Copy Databases to Other Servers</span></span>
  <span data-ttu-id="563e2-103">有時候，將資料庫從某部電腦複製到另一部電腦很有用，包括測試、一致性檢查、開發軟體、執行報表、建立鏡像資料庫，或讓資料庫可用於遠端分支機構的作業。</span><span class="sxs-lookup"><span data-stu-id="563e2-103">It is sometimes useful to copy a database from one computer to another, whether for testing, checking consistency, developing software, running reports, creating a mirror database, or, possibly, to make the database available to remote-branch operations.</span></span>  
  
 <span data-ttu-id="563e2-104">複製資料庫的方式有許多種：</span><span class="sxs-lookup"><span data-stu-id="563e2-104">There are several ways to copy a database:</span></span>  
  
-   <span data-ttu-id="563e2-105">使用複製資料庫精靈</span><span class="sxs-lookup"><span data-stu-id="563e2-105">Using the Copy Database Wizard</span></span>  
  
     <span data-ttu-id="563e2-106">您可以使用「複製資料庫精靈」在伺服器之間複製或移動資料庫，或將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫升級至更新版本。</span><span class="sxs-lookup"><span data-stu-id="563e2-106">You can use the Copy Database Wizard to copy or move databases between servers or to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a later version.</span></span> <span data-ttu-id="563e2-107">如需詳細資訊，請參閱 [Use the Copy Database Wizard](use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="563e2-107">For more information, see [Use the Copy Database Wizard](use-the-copy-database-wizard.md).</span></span>  
  
-   <span data-ttu-id="563e2-108">還原資料庫備份</span><span class="sxs-lookup"><span data-stu-id="563e2-108">Restoring a database backup</span></span>  
  
     <span data-ttu-id="563e2-109">若要複製整個資料庫，您可以使用 BACKUP 與 RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="563e2-109">To copy an entire database, you can use the BACKUP and RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="563e2-110">還原資料庫的完整備份，可用來將某部電腦的資料庫複製到另一部上，而會這麼做通常有許多原因。</span><span class="sxs-lookup"><span data-stu-id="563e2-110">Typically, restoring a full backup of a database is used to copy the database from one computer to another for a variety of reasons.</span></span> <span data-ttu-id="563e2-111">如需使用備份與還原來複製資料庫的資訊，請參閱 [使用備份與還原複製資料庫](copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="563e2-111">For information on using backup and restore to copy a database, see [Copy Databases with Backup and Restore](copy-databases-with-backup-and-restore.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="563e2-112">若要設定鏡像資料庫以執行資料庫鏡像作業，您必須使用 RESTORE DATABASE *<資料庫名稱>* WITH NORECOVERY 將資料庫還原成鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="563e2-112">To set up a mirror database for database mirroring, you must restore the database onto the mirror server by using RESTORE DATABASE *<database_name>* WITH NORECOVERY.</span></span> <span data-ttu-id="563e2-113">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="563e2-113">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="563e2-114">使用產生指令碼精靈來發行資料庫</span><span class="sxs-lookup"><span data-stu-id="563e2-114">Using the Generate Scripts Wizard to publish databases</span></span>  
  
     <span data-ttu-id="563e2-115">您可以使用產生指令碼精靈，將某個資料庫從本機電腦傳送至 Web 主控提供者。</span><span class="sxs-lookup"><span data-stu-id="563e2-115">You can use the Generate Scripts Wizard to transfer a database from a local computer to a Web hosting provider.</span></span> <span data-ttu-id="563e2-116">如需詳細資訊，請參閱 [產生和發佈指令碼精靈](../scripting/generate-and-publish-scripts-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="563e2-116">For more information, see [Generate and Publish Scripts Wizard](../scripting/generate-and-publish-scripts-wizard.md).</span></span>  
  
  
