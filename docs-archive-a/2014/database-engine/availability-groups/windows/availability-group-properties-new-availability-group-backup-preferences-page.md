---
title: 可用性群組屬性：新增可用性群組 (備份喜好設定頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.backuppreferences.f1
helpviewer_keywords:
- read-only routing
ms.assetid: 65fff22d-5963-4a8c-8b31-fe9ab247a03e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7914d4b1d7af06bcaf4f3fd05a260138e3edf5fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585610"
---
# <a name="availability-group-properties-new-availability-group-backup-preferences-page"></a><span data-ttu-id="e4791-102">可用性群組屬性：新增可用性群組 (備份喜好設定頁面)</span><span class="sxs-lookup"><span data-stu-id="e4791-102">Availability Group Properties: New Availability Group (Backup Preferences Page)</span></span>
  <span data-ttu-id="e4791-103">使用此對話方塊可以檢視和變更所選可用性群組的備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="e4791-103">Use this dialog box to view and change the backup preferences of the selected availability group.</span></span>  
  
 <span data-ttu-id="e4791-104">**若要檢視可用性群組屬性**</span><span class="sxs-lookup"><span data-stu-id="e4791-104">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="e4791-105">檢視可用性群組屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4791-105">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="e4791-106">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e4791-106">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="where-should-backups-occur"></a><span data-ttu-id="e4791-107">執行備份的位置</span><span class="sxs-lookup"><span data-stu-id="e4791-107">Where should backups occur?</span></span>  
 <span data-ttu-id="e4791-108">**慣用次要**</span><span class="sxs-lookup"><span data-stu-id="e4791-108">**Prefer Secondary**</span></span>  
 <span data-ttu-id="e4791-109">指定應該在次要複本上進行備份，但是主要複本是唯一線上複本的情況例外。</span><span class="sxs-lookup"><span data-stu-id="e4791-109">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="e4791-110">在此情況下，應該在主要複本上進行備份。</span><span class="sxs-lookup"><span data-stu-id="e4791-110">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="e4791-111">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="e4791-111">This is the default option.</span></span>  
  
 <span data-ttu-id="e4791-112">**僅次要**</span><span class="sxs-lookup"><span data-stu-id="e4791-112">**Secondary only**</span></span>  
 <span data-ttu-id="e4791-113">指定絕對不能在主要複本上執行備份。</span><span class="sxs-lookup"><span data-stu-id="e4791-113">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="e4791-114">如果主要複本是唯一的線上複本，不應該進行備份。</span><span class="sxs-lookup"><span data-stu-id="e4791-114">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
 <span data-ttu-id="e4791-115">**主要**</span><span class="sxs-lookup"><span data-stu-id="e4791-115">**Primary**</span></span>  
 <span data-ttu-id="e4791-116">指定備份一定要在主要複本上進行。</span><span class="sxs-lookup"><span data-stu-id="e4791-116">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="e4791-117">如果當您在次要複本上執行備份時，需要不支援的備份功能 (例如建立差異備份)，這個選項會很實用。</span><span class="sxs-lookup"><span data-stu-id="e4791-117">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
 <span data-ttu-id="e4791-118">**任何複本**</span><span class="sxs-lookup"><span data-stu-id="e4791-118">**Any Replica**</span></span>  
 <span data-ttu-id="e4791-119">指定當您選擇要執行備份的複本時，您希望備份作業忽略可用性複本的角色。</span><span class="sxs-lookup"><span data-stu-id="e4791-119">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="e4791-120">請注意，備份作業可能會評估其他因素，例如每個可用性複本的備份優先權，搭配其操作狀態和連接狀態。</span><span class="sxs-lookup"><span data-stu-id="e4791-120">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4791-121">不會強制執行備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="e4791-121">There is no enforcement of the backup-preference setting.</span></span> <span data-ttu-id="e4791-122">這個喜好設定的解譯取決於您在給定可用性群組之資料庫的備份作業中所編寫的邏輯 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="e4791-122">The interpretation of this preference depends on the logic, if any, that you script into back jobs for the databases in a given availability group.</span></span> <span data-ttu-id="e4791-123">如需詳細資訊，請參閱使用中[次要資料庫：次要複本上的備份 (AlwaysOn 可用性群組) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="e4791-123">For more information, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="replica-backup-priorities"></a><span data-ttu-id="e4791-124">複本備份優先權</span><span class="sxs-lookup"><span data-stu-id="e4791-124">Replica backup priorities</span></span>  
 <span data-ttu-id="e4791-125">此方格顯示裝載可用性群組複本的每個伺服器執行個體的目前備份優先權。</span><span class="sxs-lookup"><span data-stu-id="e4791-125">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="e4791-126">您可以使用此方格變更一個或多個可用性複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="e4791-126">Use this grid to change the backup priority of one or more availability replicas.</span></span>  
  
 <span data-ttu-id="e4791-127">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="e4791-127">**Server Instance**</span></span>  
 <span data-ttu-id="e4791-128">裝載可用性複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4791-128">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
 <span data-ttu-id="e4791-129">**備份優先權 (最低 = 1，最高 = 100)**</span><span class="sxs-lookup"><span data-stu-id="e4791-129">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
 <span data-ttu-id="e4791-130">指定在這個複本上執行備份的優先權 (相對於相同可用性群組中的其他複本)。</span><span class="sxs-lookup"><span data-stu-id="e4791-130">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="e4791-131">這個值是 0 到 100 範圍之間的整數。</span><span class="sxs-lookup"><span data-stu-id="e4791-131">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="e4791-132">1 表示最低優先權，100 表示最高優先權。</span><span class="sxs-lookup"><span data-stu-id="e4791-132">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="e4791-133">如果 [備份優先權]\*\*\*\* = 1，則只有當目前沒有更高優先權的可用性複本可用時，才會選擇此可用性複本來執行備份。</span><span class="sxs-lookup"><span data-stu-id="e4791-133">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
 <span data-ttu-id="e4791-134">**排除複本**</span><span class="sxs-lookup"><span data-stu-id="e4791-134">**Exclude Replica**</span></span>  
 <span data-ttu-id="e4791-135">決定是否絕對不要選擇這個可用性複本來執行備份。</span><span class="sxs-lookup"><span data-stu-id="e4791-135">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="e4791-136">例如，這對於您永遠不希望將備份容錯移轉到其中的遠端可用性複本十分有用。</span><span class="sxs-lookup"><span data-stu-id="e4791-136">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4791-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4791-137">See Also</span></span>  
 <span data-ttu-id="e4791-138">[作用中次要資料庫：次要複本上的備份 (AlwaysOn 可用性群組) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="e4791-138">[Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="e4791-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4791-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
