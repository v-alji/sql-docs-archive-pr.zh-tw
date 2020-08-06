---
title: 過期的備份 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6a944b08b15d591a9bbce47a0c0c6a8de3eb54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597774"
---
# <a name="outdated-backup"></a><span data-ttu-id="3734c-102">過期的備份</span><span class="sxs-lookup"><span data-stu-id="3734c-102">Outdated Backup</span></span>
  <span data-ttu-id="3734c-103">這個規則會檢查資料庫是否有最新備份。</span><span class="sxs-lookup"><span data-stu-id="3734c-103">This rule checks that a database has recent backups.</span></span> <span data-ttu-id="3734c-104">排程定期備份對於保護資料庫避免因為許多不同失敗而造成資料遺失而言，是很重要的工作。</span><span class="sxs-lookup"><span data-stu-id="3734c-104">Scheduling regular backups is important for protecting your databases against data loss from many different failures.</span></span> <span data-ttu-id="3734c-105">備份資料的適當頻率取決於資料庫的復原模式、有關可能資料遺失的商業需求及資料庫的更新頻率。</span><span class="sxs-lookup"><span data-stu-id="3734c-105">The appropriate frequency for backing up data depends on the recovery model of the database, on business requirements about potential data loss, and on how frequently the database is updated.</span></span> <span data-ttu-id="3734c-106">在經常更新的資料庫中，備份之間的工作損失風險會快速地增加。</span><span class="sxs-lookup"><span data-stu-id="3734c-106">In a frequently updated database, the work-loss exposure increases fairly quickly between backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="3734c-107">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="3734c-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="3734c-108">我們建議您要更常執行備份，以防止資料庫遭受資料遺失。</span><span class="sxs-lookup"><span data-stu-id="3734c-108">We recommend that you perform backups frequently enough to protect databases against data loss.</span></span>  
  
 <span data-ttu-id="3734c-109">簡單復原模式和完整復原模式都需要資料備份。</span><span class="sxs-lookup"><span data-stu-id="3734c-109">The simple recovery model and full recovery model both require data backups.</span></span> <span data-ttu-id="3734c-110">在這兩種復原模式中，您都可以使用差異備份來補充完整備份，如此可有效率地減少資料遺失的風險。</span><span class="sxs-lookup"><span data-stu-id="3734c-110">For either recovery model, you can supplement your full backups with differential backups to efficiently reduce the risk of data loss.</span></span>  
  
 <span data-ttu-id="3734c-111">如果是使用完整復原模式的資料庫，我們建議您進行經常性的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="3734c-111">For a database that uses the full recovery model, we recommend that you take frequent log backups.</span></span> <span data-ttu-id="3734c-112">如果是包含非常重要之資料的實際執行資料庫，通常會每隔 1 到 15 分鐘進行一次記錄備份。</span><span class="sxs-lookup"><span data-stu-id="3734c-112">For a production database that contains very important data, log backups would typically be taken every one to fifteen minutes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3734c-113">建議的排程備份方法是資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="3734c-113">The recommended method for scheduling backups is a database maintenance plan.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="3734c-114">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3734c-114">For More Information</span></span>  
 [<span data-ttu-id="3734c-115">系統資料庫的備份與還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3734c-115">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="3734c-116">復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3734c-116">Recovery Models &#40;SQL Server&#41;</span></span>](../backup-restore/recovery-models-sql-server.md)  
  
 [<span data-ttu-id="3734c-117">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3734c-117">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [<span data-ttu-id="3734c-118">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3734c-118">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [<span data-ttu-id="3734c-119">維護計畫</span><span class="sxs-lookup"><span data-stu-id="3734c-119">Maintenance Plans</span></span>](../maintenance-plans/maintenance-plans.md)  
  
 [<span data-ttu-id="3734c-120">交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3734c-120">Transaction Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3734c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3734c-121">See Also</span></span>  
 [<span data-ttu-id="3734c-122">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="3734c-122">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
