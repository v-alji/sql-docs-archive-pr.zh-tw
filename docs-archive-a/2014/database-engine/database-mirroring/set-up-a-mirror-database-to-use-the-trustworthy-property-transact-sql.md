---
title: 設定鏡像資料庫可使用 Trustworthy 屬性 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd46a08037bcb6eee178a96d84bdab358e5350d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701761"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a><span data-ttu-id="7ed1a-102">設定鏡像資料庫可使用 Trustworthy 屬性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ed1a-102">Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)</span></span>
  <span data-ttu-id="7ed1a-103">備份資料庫時，TRUSTWORTHY 資料庫屬性將設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-103">When a database is backed up, the TRUSTWORTHY database property is set to OFF.</span></span> <span data-ttu-id="7ed1a-104">因此，新鏡像資料庫上的 TRUSTWORTHY 一律為 OFF。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-104">Therefore, on a new mirror database TRUSTWORTHY is always OFF.</span></span> <span data-ttu-id="7ed1a-105">您必須在鏡像開始之後執行額外的設定步驟，以確保資料庫在容錯移轉之後的可信度。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-105">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ed1a-106">如需此資料庫屬性的相關資訊，請參閱 [TRUSTWORTHY 資料庫屬性](../../relational-databases/security/trustworthy-database-property.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-106">For information about this database property, see [TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="7ed1a-107">程序</span><span class="sxs-lookup"><span data-stu-id="7ed1a-107">Procedure</span></span>  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a><span data-ttu-id="7ed1a-108">若要設定鏡像資料庫以使用 Trustworthy 屬性</span><span class="sxs-lookup"><span data-stu-id="7ed1a-108">To setup a mirror database to use the Trustworthy Property</span></span>  
  
1.  <span data-ttu-id="7ed1a-109">在主體伺服器執行個體上，確認主體資料庫是否已開啟 Trustworthy 屬性。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-109">On the principal server instance, verify that the principal database has the Trustworthy property turned on.</span></span>  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     <span data-ttu-id="7ed1a-110">如需詳細資訊，請參閱 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-110">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span>  
  
2.  <span data-ttu-id="7ed1a-111">啟動鏡像之後，請確認資料庫目前是否為主體資料庫、工作階段是否使用同步作業模式，以及工作階段是否已同步處理。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-111">After starting mirroring, verify that the database is currently the principal database, the session is using a synchronous operating mode, and the session is already synchronized.</span></span>  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     <span data-ttu-id="7ed1a-112">如需詳細資訊，請參閱 [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
3.  <span data-ttu-id="7ed1a-113">同步處理鏡像工作階段之後，請以手動方式執行容錯移轉，將工作交給鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-113">Once the mirroring session is synchronized, manually fail over to the mirror database.</span></span>  
  
     <span data-ttu-id="7ed1a-114">您可以在 SQL Server Management Studio 中或使用 Transact-SQL 執行此動作：</span><span class="sxs-lookup"><span data-stu-id="7ed1a-114">This can be done in either SQL Server Management Studio or using Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="7ed1a-115">手動容錯移轉資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed1a-115">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="7ed1a-116">手動容錯移轉資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed1a-116">Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  <span data-ttu-id="7ed1a-117">使用下列 ALTER DATABASE 命令開啟 Trustworthy 資料庫屬性：</span><span class="sxs-lookup"><span data-stu-id="7ed1a-117">Turn on the trustworthy database property using the following ALTER DATABASE command:</span></span>  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     <span data-ttu-id="7ed1a-118">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-118">For more information, see[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
5.  <span data-ttu-id="7ed1a-119">您可以選擇性地再次以手動方式進行容錯移轉，將工作交回給原始主體。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-119">Optionally, manually failover again to return to the original principal.</span></span>  
  
6.  <span data-ttu-id="7ed1a-120">您可以選擇性地將 SAFETY 設定為 OFF，並確認 WITNESS 也設為 OFF，以便切換到非同步的高效能模式。</span><span class="sxs-lookup"><span data-stu-id="7ed1a-120">Optionally, switch to asynchronous, high-performance mode by setting SAFETY to OFF and ensuring that WITNESS is also set to OFF.</span></span>  
  
     <span data-ttu-id="7ed1a-121">在 Transact-SQL 中：</span><span class="sxs-lookup"><span data-stu-id="7ed1a-121">In Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="7ed1a-122">在資料庫鏡像工作階段中變更交易安全性 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed1a-122">Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [<span data-ttu-id="7ed1a-123">從資料庫鏡像工作階段移除見證 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed1a-123">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     <span data-ttu-id="7ed1a-124">在 SQL Server Management Studio 中：</span><span class="sxs-lookup"><span data-stu-id="7ed1a-124">In SQL Server Management Studio:</span></span>  
  
    -   [<span data-ttu-id="7ed1a-125">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed1a-125">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ed1a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed1a-126">See Also</span></span>  
 <span data-ttu-id="7ed1a-127">[TRUSTWORTHY 資料庫屬性](../../relational-databases/security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="7ed1a-127">[TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="7ed1a-128">設定加密鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="7ed1a-128">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
