---
title: 大型備份或還原記錄資料表會讓升級看起來不會回應 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 918c20f58c00c535d8ed41d887e9671f5e821a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585768"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a><span data-ttu-id="239b8-102">大型備份或還原記錄資料表會使升級作業看似沒有回應</span><span class="sxs-lookup"><span data-stu-id="239b8-102">Large backup or restore history tables make upgrade appear to not respond</span></span>
  <span data-ttu-id="239b8-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，新的資料行會加入至某些備份和還原記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="239b8-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], new columns were added to some of the backup and restore history tables.</span></span> <span data-ttu-id="239b8-104">升級這些資料表需要更改它們，以便加入新的資料行。</span><span class="sxs-lookup"><span data-stu-id="239b8-104">Upgrading these tables requires altering them to add the new columns.</span></span> <span data-ttu-id="239b8-105">如果其中一個或多個資料表包含大量資料列，則升級會延滯相當長的一段時間，等候 ALTER TABLE 陳述式將資料行加入至該資料表。</span><span class="sxs-lookup"><span data-stu-id="239b8-105">If one or more of these tables contains a large number of rows, the upgrade will stall for a substantial amount of time on the ALTER TABLE statement that adds columns to that table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="239b8-106">元件</span><span class="sxs-lookup"><span data-stu-id="239b8-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="239b8-107">描述</span><span class="sxs-lookup"><span data-stu-id="239b8-107">Description</span></span>  
 <span data-ttu-id="239b8-108">如果下列其中一個備份或還原歷程記錄資料表包含大量資料列，則升級可能會停止回應：</span><span class="sxs-lookup"><span data-stu-id="239b8-108">Upgrade can appear to stop responding if any of the following backup or restore history tables contains a large number of rows:</span></span>  
  
-   <span data-ttu-id="239b8-109">**backupfile**</span><span class="sxs-lookup"><span data-stu-id="239b8-109">**backupfile**</span></span>  
  
-   <span data-ttu-id="239b8-110">**backupmediafamily**</span><span class="sxs-lookup"><span data-stu-id="239b8-110">**backupmediafamily**</span></span>  
  
-   <span data-ttu-id="239b8-111">**backupmediaset**</span><span class="sxs-lookup"><span data-stu-id="239b8-111">**backupmediaset**</span></span>  
  
-   <span data-ttu-id="239b8-112">**backupset**</span><span class="sxs-lookup"><span data-stu-id="239b8-112">**backupset**</span></span>  
  
-   <span data-ttu-id="239b8-113">**restorefile**</span><span class="sxs-lookup"><span data-stu-id="239b8-113">**restorefile**</span></span>  
  
-   <span data-ttu-id="239b8-114">**restorefilegroup**</span><span class="sxs-lookup"><span data-stu-id="239b8-114">**restorefilegroup**</span></span>  
  
-   <span data-ttu-id="239b8-115">**restorehistory**</span><span class="sxs-lookup"><span data-stu-id="239b8-115">**restorehistory**</span></span>  
  
 <span data-ttu-id="239b8-116">如果其中任何資料表含有 10,000 個以上的資料列，Upgrade Advisor 會報告不相容的失敗。</span><span class="sxs-lookup"><span data-stu-id="239b8-116">If any of these tables has 10,000 or more rows, Upgrade Advisor reports a noncompliance failure.</span></span> <span data-ttu-id="239b8-117">但是，它不會報告哪一份資料表超過允許的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="239b8-117">It does not report which table exceeds the allowed number of rows.</span></span> <span data-ttu-id="239b8-118">超過 10,000 個資料列的第一份資料表會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="239b8-118">The first table that exceeds 10,000 rows causes the failure.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="239b8-119">更正動作</span><span class="sxs-lookup"><span data-stu-id="239b8-119">Corrective Action</span></span>  
 <span data-ttu-id="239b8-120">升級資料庫之前，如果其中任何資料表超過 10,000 個資料列，我們建議您將此數目縮減為小於 10,000。</span><span class="sxs-lookup"><span data-stu-id="239b8-120">Before you upgrade a database, if any of these tables exceeds 10,000 rows, we recommend that you reduce the number to less than 10,000.</span></span> <span data-ttu-id="239b8-121">若要減少所有這些資料表中的資料列，您可以執行**sp_delete_backuphistory**預存程式。</span><span class="sxs-lookup"><span data-stu-id="239b8-121">To reduce rows in all of these tables, you can run the **sp_delete_backuphistory** stored procedure.</span></span> <span data-ttu-id="239b8-122">這個程序會在所有備份和還原記錄資料表中刪除早於指定日期之備份組的項目。</span><span class="sxs-lookup"><span data-stu-id="239b8-122">This procedure deletes the entries in all of the backup and restore history tables for backup sets older than a specified date.</span></span> <span data-ttu-id="239b8-123">如需詳細資訊，請參閱 [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="239b8-123">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239b8-124">您可以升級備份和還原記錄資料表大於 10,000 個資料列的資料庫。</span><span class="sxs-lookup"><span data-stu-id="239b8-124">You can upgrade a database whose backup and restore history tables are larger than 10,000 rows.</span></span> <span data-ttu-id="239b8-125">但是當系統更改大型資料表時，升級作業可能會看似延滯。</span><span class="sxs-lookup"><span data-stu-id="239b8-125">But the upgrade may appear to stall while large tables are being altered.</span></span> <span data-ttu-id="239b8-126">資料表的體積越大，安裝程式完成作業所花費的時間就越長。</span><span class="sxs-lookup"><span data-stu-id="239b8-126">The larger the tables, the longer that Setup takes to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239b8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="239b8-127">See Also</span></span>  
 <span data-ttu-id="239b8-128">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="239b8-128">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="239b8-129">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="239b8-129">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
