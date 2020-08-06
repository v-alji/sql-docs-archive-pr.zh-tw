---
title: 使用容錯移轉可用性群組精靈 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.failoverwizard.progress.f1
- sql12.swb.failoverwizard.f1
- sql12.swb.failoverwizard.selectnewprimary.f1
- sql12.swb.failoverwizard.confirmdataloss.f1
- sql12.swb.failoverwizard.connecttoreplicas.f1
helpviewer_keywords:
- failover [SQL Server], failover
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], configuring
ms.assetid: 4a602584-63e4-4322-aafc-5d715b82b834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bd059712aae9c23ebbda107370ad112d7917cd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594184"
---
# <a name="use-the-fail-over-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="be21f-102">使用容錯移轉可用性群組精靈 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="be21f-102">Use the Fail Over Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="be21f-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 PowerShell，針對 AlwaysOn 可用性群組執行規劃的手動容錯移轉或強制手動容錯移轉 (強制容錯移轉)。</span><span class="sxs-lookup"><span data-stu-id="be21f-103">This topic describes how to perform a planned manual failover or forced manual failover (forced failover) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="be21f-104">可用性群組會在可用性複本層級容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="be21f-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="be21f-105">如果您容錯移轉至處於 SYNCHRONIZED 狀態的次要複本，此精靈就會執行規劃的手動容錯移轉 (不會遺失資料)。</span><span class="sxs-lookup"><span data-stu-id="be21f-105">If you fail over to a secondary replica in the SYNCHRONIZED state, the wizard performs a planned manual failover (without data loss).</span></span> <span data-ttu-id="be21f-106">如果您容錯移轉至處於 UNSYNCHRONIZED 或 NOT SYNCHRONIZING 狀態的次要複本，此精靈就會執行強制手動容錯移轉，也稱為「強制容錯移轉」 (可能會遺失資料)。</span><span class="sxs-lookup"><span data-stu-id="be21f-106">If you fail over to a secondary replica in the UNSYNCHRONIZED or NOT SYNCHRONIZING state, the wizard performs a forced manual failover-also known as a *forced failover* (with possible data loss).</span></span> <span data-ttu-id="be21f-107">這兩種手動容錯移轉形式都會將您所連接的次要複本轉換成主要角色。</span><span class="sxs-lookup"><span data-stu-id="be21f-107">Both forms of manual failover transition the secondary replica to which you are connected to the primary role.</span></span> <span data-ttu-id="be21f-108">規劃的手動容錯移轉目前會將先前的主要複本會轉換成次要角色。</span><span class="sxs-lookup"><span data-stu-id="be21f-108">A planned manual failover currently transitions the former primary replica to the secondary role.</span></span> <span data-ttu-id="be21f-109">強制容錯移轉之後，當先前的主要複本上線時，它就會轉換成次要角色。</span><span class="sxs-lookup"><span data-stu-id="be21f-109">After a forced failover, when the former primary replica comes online, it transitions to the secondary role.</span></span>  
  


  
-   <span data-ttu-id="be21f-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]頁面**</span><span class="sxs-lookup"><span data-stu-id="be21f-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] pages:**</span></span>  
  
     <span data-ttu-id="be21f-111">[選取新的主要複本頁面](#SelectNewPrimaryReplica) (本主題稍後)</span><span class="sxs-lookup"><span data-stu-id="be21f-111">[Select New Primary Replica page](#SelectNewPrimaryReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="be21f-112">[連接到複本頁面](#ConnectToReplica) (本主題稍後)</span><span class="sxs-lookup"><span data-stu-id="be21f-112">[Connect to Replica page](#ConnectToReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="be21f-113">[確認可能遺失資料頁面](#ConfirmPotentialDataLoss) (本主題稍後)</span><span class="sxs-lookup"><span data-stu-id="be21f-113">[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss) (later in this topic)</span></span>  
  
     <span data-ttu-id="be21f-114">[[摘要] 頁面 &#40;AlwaysOn 可用性群組嚮導&#41;](summary-page-always-on-availability-group-wizards.md)</span><span class="sxs-lookup"><span data-stu-id="be21f-114">[Summary Page &#40;AlwaysOn Availability Group Wizards&#41;](summary-page-always-on-availability-group-wizards.md)</span></span>  
  
     [<span data-ttu-id="be21f-115">&#40;AlwaysOn 可用性群組嚮導的進度頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="be21f-115">Progress Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](progress-page-always-on-availability-group-wizards.md)  
  
     [<span data-ttu-id="be21f-116">&#40;AlwaysOn 可用性群組嚮導的結果頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="be21f-116">Results Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](results-page-always-on-availability-group-wizards.md)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="be21f-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="be21f-117">Before You Begin</span></span>  
 <span data-ttu-id="be21f-118">第一次進行規劃的手動容錯移轉之前，請參閱 [執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)或 PowerShell，針對 AlwaysOn 可用性群組執行規劃的手動容錯移轉或強制手動容錯移轉 (強制容錯移轉)。</span><span class="sxs-lookup"><span data-stu-id="be21f-118">Before your first planned manual failover, see the "Before You Begin" section in [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="be21f-119">第一次進行強制容錯移轉之前，請先參閱＜開始之前＞和＜後續：強制容錯移轉後的重要任務＞小節 (位於[執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) 中)。</span><span class="sxs-lookup"><span data-stu-id="be21f-119">Before your first forced failover, see the "Before You Begin" and "Follow Up: Essential Tasks After a Forced Failover" sections in [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="be21f-120">限制事項</span><span class="sxs-lookup"><span data-stu-id="be21f-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="be21f-121">目標次要複本接受命令之後，容錯移轉命令就會傳回。</span><span class="sxs-lookup"><span data-stu-id="be21f-121">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="be21f-122">不過，在可用性群組完成容錯移轉之後，會以非同步方式復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="be21f-122">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="be21f-123">容錯移轉時，不會保留可用性群組內跨資料庫的一致性。</span><span class="sxs-lookup"><span data-stu-id="be21f-123">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be21f-124">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 不支援跨資料庫交易和分散式交易。</span><span class="sxs-lookup"><span data-stu-id="be21f-124">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="be21f-125">如需詳細資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="be21f-125">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-for-using-the-failover-availability-group-wizard"></a><a name="Prerequisites"></a> <span data-ttu-id="be21f-126">使用容錯移轉可用性群組精靈的必要條件</span><span class="sxs-lookup"><span data-stu-id="be21f-126">Prerequisites for Using the Failover Availability Group Wizard</span></span>  
  
-   <span data-ttu-id="be21f-127">您必須連接到裝載目前可用之可用性複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="be21f-127">You must be connected to the server instance that hosts an availability replica that is currently available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="be21f-128">Security</span><span class="sxs-lookup"><span data-stu-id="be21f-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="be21f-129">權限</span><span class="sxs-lookup"><span data-stu-id="be21f-129">Permissions</span></span>  
 <span data-ttu-id="be21f-130">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="be21f-130">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="be21f-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be21f-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="be21f-132">**若要使用容錯移轉可用性群組精靈**</span><span class="sxs-lookup"><span data-stu-id="be21f-132">**To Use the Failover Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="be21f-133">在 [物件總管] 中，連接到裝載需要容錯移轉之可用性群組次要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="be21f-133">In Object Explorer, connect to the server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="be21f-134">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="be21f-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="be21f-135">若要啟動 [容錯移轉可用性群組精靈]，請以滑鼠右鍵按一下您要容錯移轉的可用性群組，然後選取 [容錯移轉] 。</span><span class="sxs-lookup"><span data-stu-id="be21f-135">To launch the Failover Availability Group Wizard, right-click the availability group that you are going to fail over, and select **Failover**.</span></span>  
  
4.  <span data-ttu-id="be21f-136">**[簡介]** 頁面所呈現的資訊主要取決於任何次要複本是否符合規劃容錯移轉的資格。</span><span class="sxs-lookup"><span data-stu-id="be21f-136">The information presented by the **Introduction** page depends on whether any secondary replica is eligible for a planned failover.</span></span> <span data-ttu-id="be21f-137">如果此頁面顯示 **[執行這個可用性群組的計劃的容錯移轉]** ，表示您可以在不遺失資料的情況下容錯移轉可用性群組。</span><span class="sxs-lookup"><span data-stu-id="be21f-137">If this page says, "**Perform a planned failover for this availability group**", you can failover the availability group without data loss.</span></span>  
  
5.  <span data-ttu-id="be21f-138">在 [選取新的主要複本]  頁面上，您可以在選擇將成為新主要複本的次要複本 (「容錯移轉目標」 ) 之前，檢視目前主要複本和 WSFC 仲裁的狀態。</span><span class="sxs-lookup"><span data-stu-id="be21f-138">On the **Select New Primary Replica** page, you can view the status of the current primary replica and of the WSFC quorum, before you choose the secondary replica that will become the new primary replica (the *failover target*).</span></span> <span data-ttu-id="be21f-139">若為規劃的手動容錯移轉，請務必選取 **[容錯移轉整備]** 值為 **[無資料遺失]** 的次要複本。</span><span class="sxs-lookup"><span data-stu-id="be21f-139">For a planned manual failover, be sure to select a secondary replica whose **Failover Readiness** value is "**No data loss**".</span></span> <span data-ttu-id="be21f-140">若為強制容錯移轉，則對於所有可能的容錯移轉目標而言，這個值會是「\*\*資料遺失，警告 (***#***) \*\*」，其中 *#* 表示給定次要複本的警告數目。</span><span class="sxs-lookup"><span data-stu-id="be21f-140">For a forced failover, for all the possible failover targets, this value will be "**Data loss, Warnings(***#***)**", where *#* indicates the number of warnings that exist for a given secondary replica.</span></span> <span data-ttu-id="be21f-141">若要檢視給定容錯移轉目標的警告，請按一下其 [容錯移轉整備] 值。</span><span class="sxs-lookup"><span data-stu-id="be21f-141">To view the warnings for a given failover target, click its "Failover Readiness" value.</span></span>  
  
     <span data-ttu-id="be21f-142">如需詳細資訊，請參閱本主題稍後的＜ [選取新的主要複本頁面](#SelectNewPrimaryReplica)＞。</span><span class="sxs-lookup"><span data-stu-id="be21f-142">For more information, see [Select New Primary Replica page](#SelectNewPrimaryReplica), later in this topic.</span></span>  
  
6.  <span data-ttu-id="be21f-143">在 **[連接到複本]** 頁面上，連接到容錯移轉目標。</span><span class="sxs-lookup"><span data-stu-id="be21f-143">On the **Connect to Replica** page,  connect to the failover target.</span></span> <span data-ttu-id="be21f-144">如需詳細資訊，請參閱本主題稍後的＜ [連接到複本頁面](#ConnectToReplica)＞。</span><span class="sxs-lookup"><span data-stu-id="be21f-144">For more information, see [Connect to Replica page](#ConnectToReplica), later in this topic.</span></span>  
  
7.  <span data-ttu-id="be21f-145">如果您正在執行強制容錯移轉，此精靈會顯示 **[確認可能遺失資料]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="be21f-145">If you are performing a forced failover, the wizard displays the **Confirm Potential Data Loss** page.</span></span> <span data-ttu-id="be21f-146">若要繼續進行容錯移轉，您必須選取 **[按一下這裡確認可能遺失資料的容錯移轉]** 。</span><span class="sxs-lookup"><span data-stu-id="be21f-146">To proceed with the failover, you must select **Click here to confirm failover with potential data loss**.</span></span> <span data-ttu-id="be21f-147">如需詳細資訊，請參閱本主題稍後的＜[確認可能遺失資料頁面](#ConfirmPotentialDataLoss)＞。</span><span class="sxs-lookup"><span data-stu-id="be21f-147">For more information, see .[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss), later in this topic.</span></span>  
  
8.  <span data-ttu-id="be21f-148">在 **[摘要]** 頁面上，檢閱容錯移轉至選取次要複本的影響。</span><span class="sxs-lookup"><span data-stu-id="be21f-148">On the **Summary** page, review the implications of failing over to the selected secondary replica.</span></span>  
  
     <span data-ttu-id="be21f-149">如果您對所做的選擇感到滿意時，可以選擇按一下 **[指令碼]** ，建立精靈將執行之步驟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="be21f-149">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="be21f-150">然後，若要將可用性群組容錯移轉至選取的次要複本，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="be21f-150">Then, to failover the availability group to the selected secondary replica, click **Finish**.</span></span>  
  
9. <span data-ttu-id="be21f-151">**[進度]** 頁面會顯示容錯移轉可用性群組的進度。</span><span class="sxs-lookup"><span data-stu-id="be21f-151">The **Progress** page displays the progress of failing over the availability group.</span></span>  
  
10. <span data-ttu-id="be21f-152">當容錯移轉作業完成時， **[結果]** 頁面就會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="be21f-152">When the failover operation finishes, the **Results** page displays the result.</span></span> <span data-ttu-id="be21f-153">當精靈完成時，按一下 **[關閉]** 以結束。</span><span class="sxs-lookup"><span data-stu-id="be21f-153">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="be21f-154">如需詳細資訊，請參閱[結果頁面 &#40;AlwaysOn 可用性群組精靈&#41;](results-page-always-on-availability-group-wizards.md)。</span><span class="sxs-lookup"><span data-stu-id="be21f-154">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="be21f-155">在進行強制容錯移轉之後，請參閱＜後續：強制容錯移轉後＞一節 (位於[執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) 中)。</span><span class="sxs-lookup"><span data-stu-id="be21f-155">After a forced failover, see the "Follow Up: After a Forced Failover" section in the [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
## <a name="help-for-pages-that-are-exclusive-to-this-wizard"></a><span data-ttu-id="be21f-156">此精靈專用頁面的說明</span><span class="sxs-lookup"><span data-stu-id="be21f-156">Help for Pages that are Exclusive to This Wizard</span></span>  
 <span data-ttu-id="be21f-157">本節描述的是 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]特有的頁面。</span><span class="sxs-lookup"><span data-stu-id="be21f-157">This section describes the pages that are unique to the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span>  
  
 
  
 <span data-ttu-id="be21f-158">此精靈的其他頁面都與一個或多個其他 AlwaysOn 可用性群組精靈共用說明，而且記載於個別的 F1 說明主題中。</span><span class="sxs-lookup"><span data-stu-id="be21f-158">The other pages of this wizard share help with one or more of the other AlwaysOn Availability Groups wizards and are documented in separate F1 help topics.</span></span>  
  
###  <a name="select-new-primary-replica-page"></a><a name="SelectNewPrimaryReplica"></a> <span data-ttu-id="be21f-159">Select New Primary Replica Page</span><span class="sxs-lookup"><span data-stu-id="be21f-159">Select New Primary Replica Page</span></span>  
 <span data-ttu-id="be21f-160">本節描述的是 **[選取新的主要複本]** 頁面的選項。</span><span class="sxs-lookup"><span data-stu-id="be21f-160">This section describes the options of the **Select New Primary Replica** page.</span></span> <span data-ttu-id="be21f-161">您可以使用此頁面來選取可用性群組將容錯移轉的目標次要複本 (容錯移轉目標)。</span><span class="sxs-lookup"><span data-stu-id="be21f-161">Use this page to select the secondary replica (failover target) to which the availability group will fail over.</span></span> <span data-ttu-id="be21f-162">這個複本將成為新的主要複本。</span><span class="sxs-lookup"><span data-stu-id="be21f-162">This replica will become the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="be21f-163">頁面選項</span><span class="sxs-lookup"><span data-stu-id="be21f-163">Page Options</span></span>  
 <span data-ttu-id="be21f-164">**目前的主要複本**</span><span class="sxs-lookup"><span data-stu-id="be21f-164">**Current Primary Replica**</span></span>  
 <span data-ttu-id="be21f-165">顯示目前主要複本的名稱 (如果它已上線的話)。</span><span class="sxs-lookup"><span data-stu-id="be21f-165">Displays the name of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="be21f-166">**主要複本狀態**</span><span class="sxs-lookup"><span data-stu-id="be21f-166">**Primary Replica Status**</span></span>  
 <span data-ttu-id="be21f-167">顯示目前主要複本的狀態 (如果它已上線的話)。</span><span class="sxs-lookup"><span data-stu-id="be21f-167">Displays the status of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="be21f-168">**仲裁狀態**</span><span class="sxs-lookup"><span data-stu-id="be21f-168">**Quorum Status**</span></span>  
 <span data-ttu-id="be21f-169">顯示可用性複本的 WSFC 仲裁狀態，它有下列幾種：</span><span class="sxs-lookup"><span data-stu-id="be21f-169">Displays the WSFC quorum status for the availability replica, one of:</span></span>  
  
|<span data-ttu-id="be21f-170">值</span><span class="sxs-lookup"><span data-stu-id="be21f-170">Value</span></span>|<span data-ttu-id="be21f-171">描述</span><span class="sxs-lookup"><span data-stu-id="be21f-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be21f-172">**一般仲裁**</span><span class="sxs-lookup"><span data-stu-id="be21f-172">**Normal quorum**</span></span>|<span data-ttu-id="be21f-173">叢集已經使用一般仲裁來啟動。</span><span class="sxs-lookup"><span data-stu-id="be21f-173">The cluster has started with normal quorum.</span></span>|  
|<span data-ttu-id="be21f-174">**強制仲裁**</span><span class="sxs-lookup"><span data-stu-id="be21f-174">**Forced quorum**</span></span>|<span data-ttu-id="be21f-175">叢集已經使用強制仲裁來啟動。</span><span class="sxs-lookup"><span data-stu-id="be21f-175">The cluster has started with forced quorum.</span></span>|  
|<span data-ttu-id="be21f-176">**未知的仲裁**</span><span class="sxs-lookup"><span data-stu-id="be21f-176">**Unknown quorum**</span></span>|<span data-ttu-id="be21f-177">無法取得叢集仲裁狀態。</span><span class="sxs-lookup"><span data-stu-id="be21f-177">The cluster quorum status is unavailable.</span></span>|  
|<span data-ttu-id="be21f-178">**不適用**</span><span class="sxs-lookup"><span data-stu-id="be21f-178">**Not applicable**</span></span>|<span data-ttu-id="be21f-179">裝載可用性複本的節點沒有任何仲裁。</span><span class="sxs-lookup"><span data-stu-id="be21f-179">The node that hosts the availability replica has no quorum.</span></span>|  
  
 <span data-ttu-id="be21f-180">如需詳細資訊，請參閱 [WSFC 仲裁模式和投票組態 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="be21f-180">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
 <span data-ttu-id="be21f-181">**選擇新的主要複本**</span><span class="sxs-lookup"><span data-stu-id="be21f-181">**Choose a new primary replica**</span></span>  
 <span data-ttu-id="be21f-182">您可以使用此方格來選取要成為新主要複本的次要複本。</span><span class="sxs-lookup"><span data-stu-id="be21f-182">Use this grid to select a secondary replica to become the new primary replica.</span></span> <span data-ttu-id="be21f-183">此方格中的資料行如下所示：</span><span class="sxs-lookup"><span data-stu-id="be21f-183">The columns in this grid are as follows:</span></span>  
  
 <span data-ttu-id="be21f-184">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="be21f-184">**Server Instance**</span></span>  
 <span data-ttu-id="be21f-185">顯示裝載次要複本之伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="be21f-185">Displays the name of a server instance that hosts a secondary replica.</span></span>  
  
 <span data-ttu-id="be21f-186">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="be21f-186">**Availability Mode**</span></span>  
 <span data-ttu-id="be21f-187">顯示伺服器執行個體的可用性模式，它有下列幾種：</span><span class="sxs-lookup"><span data-stu-id="be21f-187">Displays the availability mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="be21f-188">值</span><span class="sxs-lookup"><span data-stu-id="be21f-188">Value</span></span>|<span data-ttu-id="be21f-189">描述</span><span class="sxs-lookup"><span data-stu-id="be21f-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be21f-190">**同步認可**</span><span class="sxs-lookup"><span data-stu-id="be21f-190">**Synchronous commit**</span></span>|<span data-ttu-id="be21f-191">在同步認可模式下認可交易之前，同步認可主要複本會等候同步認可次要複本確認它已完成強行寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="be21f-191">Under synchronous-commit mode, before committing transactions, a synchronous-commit primary replica waits for a synchronous-commit secondary replica to acknowledge that it has finished hardening the log.</span></span> <span data-ttu-id="be21f-192">同步認可模式可確定，一旦給定次要資料庫與主要資料庫同步處理之後，認可的交易就會受到完整保護。</span><span class="sxs-lookup"><span data-stu-id="be21f-192">Synchronous-commit mode ensures that once a given secondary database is synchronized with the primary database, committed transactions are fully protected.</span></span>|  
|<span data-ttu-id="be21f-193">**非同步認可**</span><span class="sxs-lookup"><span data-stu-id="be21f-193">**Asynchronous commit**</span></span>|<span data-ttu-id="be21f-194">在非同步認可模式下，主要複本會認可交易，而不等候確認非同步認可次要複本已經強行寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="be21f-194">Under asynchronous-commit mode, the primary replica commits transactions without waiting for acknowledgement that an asynchronous-commit secondary replica has hardened the log.</span></span> <span data-ttu-id="be21f-195">非同步認可模式會將次要資料庫上的交易延遲降至最低，但允許這些資料庫落後主要資料庫，因此可能會發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="be21f-195">Asynchronous-commit mode minimizes transaction latency on the secondary databases but allows them to lag behind the primary databases, making some data loss possible.</span></span>|  
  
 <span data-ttu-id="be21f-196">如需詳細資訊，請參閱[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="be21f-196">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="be21f-197">**容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="be21f-197">**Failover Mode**</span></span>  
 <span data-ttu-id="be21f-198">顯示伺服器執行個體的容錯移轉模式，它有下列幾種：</span><span class="sxs-lookup"><span data-stu-id="be21f-198">Displays the failover mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="be21f-199">值</span><span class="sxs-lookup"><span data-stu-id="be21f-199">Value</span></span>|<span data-ttu-id="be21f-200">描述</span><span class="sxs-lookup"><span data-stu-id="be21f-200">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be21f-201">**自動**</span><span class="sxs-lookup"><span data-stu-id="be21f-201">**Automatic**</span></span>|<span data-ttu-id="be21f-202">每當次要複本與主要複本同步處理時，設定為自動容錯移轉的次要複本也支援規劃的手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="be21f-202">A secondary replica that is configured for automatic failover also supports planned manual failover whenever the secondary replica is synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="be21f-203">**手動**</span><span class="sxs-lookup"><span data-stu-id="be21f-203">**Manual**</span></span>|<span data-ttu-id="be21f-204">手動容錯移轉的類型有兩種：規劃 (不會遺失資料) 和強制 (可能會遺失資料)。</span><span class="sxs-lookup"><span data-stu-id="be21f-204">Two types of manual failover exist: planned (without data loss) and forced (with possible data loss).</span></span> <span data-ttu-id="be21f-205">給定的次要複本會根據次要複本的可用性模式和同步處理狀態 (同步認可模式)，僅支援其中一種類型。</span><span class="sxs-lookup"><span data-stu-id="be21f-205">For a given secondary replica, only one of these is supported, depending on the availability mode and, for synchronous-commit mode, the synchronization state of the secondary replica.</span></span> <span data-ttu-id="be21f-206">若要判斷給定次要複本目前支援的手動容錯移轉形式，請查看此方格的 **[容錯移轉整備]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="be21f-206">To determine which form of manual failover is currently supported by a given secondary replica, see the **Failover Readiness** column of this grid.</span></span>|  
  
 <span data-ttu-id="be21f-207">如需詳細資訊，請參閱[容錯移轉及容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="be21f-207">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="be21f-208">**[容錯移轉整備]**</span><span class="sxs-lookup"><span data-stu-id="be21f-208">**Failover Readiness**</span></span>  
 <span data-ttu-id="be21f-209">顯示次要複本的容錯移轉整備，它有下列幾種：</span><span class="sxs-lookup"><span data-stu-id="be21f-209">Displays failover readiness of the secondary replica, one of:</span></span>  
  
|<span data-ttu-id="be21f-210">值</span><span class="sxs-lookup"><span data-stu-id="be21f-210">Value</span></span>|<span data-ttu-id="be21f-211">描述</span><span class="sxs-lookup"><span data-stu-id="be21f-211">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be21f-212">**[無資料遺失]**</span><span class="sxs-lookup"><span data-stu-id="be21f-212">**No data loss**</span></span>|<span data-ttu-id="be21f-213">這個次要複本目前支援規劃的容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="be21f-213">This secondary replica currently supports planned failover.</span></span> <span data-ttu-id="be21f-214">只有當同步認可模式的次要複本目前與主要複本同步處理時，才會出現此值。</span><span class="sxs-lookup"><span data-stu-id="be21f-214">This value occurs only when a synchronous-commit mode secondary replica is currently synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="be21f-215">**資料遺失，警告(** *#* **)**</span><span class="sxs-lookup"><span data-stu-id="be21f-215">**Data loss, Warnings(** *#* **)**</span></span>|<span data-ttu-id="be21f-216">這個次要複本目前支援強制容錯移轉 (可能會遺失資料)。</span><span class="sxs-lookup"><span data-stu-id="be21f-216">This secondary replica currently supports forced failover (with possible data loss).</span></span> <span data-ttu-id="be21f-217">每當次要複本並未與主要複本同步處理時，就會出現此值。</span><span class="sxs-lookup"><span data-stu-id="be21f-217">This value occurs whenever the secondary replica is not synchronized with the primary replica.</span></span> <span data-ttu-id="be21f-218">如需有關可能遺失資料的詳細資訊，請按一下資料遺失警告連結。</span><span class="sxs-lookup"><span data-stu-id="be21f-218">Click the data-loss warnings link for information about the possible data loss.</span></span>|  
  
 <span data-ttu-id="be21f-219">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="be21f-219">**Refresh**</span></span>  
 <span data-ttu-id="be21f-220">按一下可更新方格。</span><span class="sxs-lookup"><span data-stu-id="be21f-220">Click to update the grid.</span></span>  
  
 <span data-ttu-id="be21f-221">**取消**</span><span class="sxs-lookup"><span data-stu-id="be21f-221">**Cancel**</span></span>  
 <span data-ttu-id="be21f-222">按一下可取消精靈。</span><span class="sxs-lookup"><span data-stu-id="be21f-222">Click to cancel the wizard.</span></span> <span data-ttu-id="be21f-223">在 **[選取新的主要複本]** 頁面上，取消精靈會導致精靈結束，而不執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="be21f-223">On the **Select New Primary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="confirm-potential-data-loss-page"></a><a name="ConfirmPotentialDataLoss"></a> <span data-ttu-id="be21f-224">Confirm Potential Data Loss Page</span><span class="sxs-lookup"><span data-stu-id="be21f-224">Confirm Potential Data Loss Page</span></span>  
 <span data-ttu-id="be21f-225">本節描述的是 **[確認可能遺失資料]** 頁面的選項 (只有當您正在執行強制容錯移轉時，才會顯示此頁面)。</span><span class="sxs-lookup"><span data-stu-id="be21f-225">This section describes the options of the **Confirm Potential Data Loss** page, which is displayed only if you are performing a forced failover.</span></span> <span data-ttu-id="be21f-226">本主題僅供 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="be21f-226">This topic is used only by the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="be21f-227">您可以使用此頁面來指出是否願意承擔可能遺失資料的風險，以便強制可用性群組容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="be21f-227">Use this page to indicate whether you are willing to risk possible data loss in order to force the availability group to fail over.</span></span>  
  
#### <a name="confirm-potential-data-loss-options"></a><span data-ttu-id="be21f-228">確認可能遺失資料選項</span><span class="sxs-lookup"><span data-stu-id="be21f-228">Confirm Potential Data Loss Options</span></span>  
 <span data-ttu-id="be21f-229">如果選取的次要複本並未與主要複本同步處理，此精靈就會顯示一則警告，表示容錯移轉至此次要複本可能會導致一個或多個資料庫的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="be21f-229">If the selected secondary replica is not synchronized with the primary replica, the wizard displays a warning that failing over to this secondary replica could cause data loss on one or more databases.</span></span>  
  
 <span data-ttu-id="be21f-230">**按一下這裡確認可能遺失資料的容錯移轉**</span><span class="sxs-lookup"><span data-stu-id="be21f-230">**Click here to confirm failover with potential data loss.**</span></span>  
 <span data-ttu-id="be21f-231">如果您願意承擔遺失資料的風險，以便將這個可用性群組中的資料庫提供給使用者，請按一下此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="be21f-231">If you are willing to risk data loss in order to make the databases in this availability group available to users, click this checkbox.</span></span> <span data-ttu-id="be21f-232">如果您不願意承擔遺失資料的風險，可以按一下 **[上一步]** 返回 **[選取新的主要複本]** 頁面，或按一下 **[取消]** 結束精靈而不容錯移轉可用性群組。</span><span class="sxs-lookup"><span data-stu-id="be21f-232">If you are not willing to risk data loss, you can either click **Previous** to return to the **Select New Primary Replica** page, or click **Cancel** to exit the wizard without failing over the availability group.</span></span>  
  
 <span data-ttu-id="be21f-233">**取消**</span><span class="sxs-lookup"><span data-stu-id="be21f-233">**Cancel**</span></span>  
 <span data-ttu-id="be21f-234">按一下可取消精靈。</span><span class="sxs-lookup"><span data-stu-id="be21f-234">Click to cancel the wizard.</span></span> <span data-ttu-id="be21f-235">在 **[確認可能遺失資料]** 頁面上，取消精靈會導致精靈結束，而不執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="be21f-235">On the **Confirm Potential Data Loss** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="connect-to-replica-page"></a><a name="ConnectToReplica"></a> <span data-ttu-id="be21f-236">Connect to Replica Page</span><span class="sxs-lookup"><span data-stu-id="be21f-236">Connect to Replica Page</span></span>  
 <span data-ttu-id="be21f-237">本節描述的是 **之** [連接到複本] [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]頁面的選項。</span><span class="sxs-lookup"><span data-stu-id="be21f-237">This section describes the options of the **Connect to Replica** page of the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="be21f-238">只有當您沒有連接到目標次要複本時，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="be21f-238">This page is displayed only if you are not connected to the target secondary replica.</span></span> <span data-ttu-id="be21f-239">您可以使用此頁面來連接到已選取成為新主要複本的次要複本。</span><span class="sxs-lookup"><span data-stu-id="be21f-239">Use this page to connect to the secondary replica that you have selected as the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="be21f-240">頁面選項</span><span class="sxs-lookup"><span data-stu-id="be21f-240">Page Options</span></span>  
 <span data-ttu-id="be21f-241">**方格資料行：**</span><span class="sxs-lookup"><span data-stu-id="be21f-241">**Grid columns:**</span></span>  
 <span data-ttu-id="be21f-242">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="be21f-242">**Server Instance**</span></span>  
 <span data-ttu-id="be21f-243">顯示將裝載可用性複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="be21f-243">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="be21f-244">**連線方式**</span><span class="sxs-lookup"><span data-stu-id="be21f-244">**Connected As**</span></span>  
 <span data-ttu-id="be21f-245">顯示在建立連接後連接到伺服器執行個體的帳戶。</span><span class="sxs-lookup"><span data-stu-id="be21f-245">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="be21f-246">如果此資料行對於給定的伺服器執行個體顯示 **[未連接]** ，您就必須按一下 **[連接]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="be21f-246">If this column displays "**Not Connected**" for a given server instance, you will need to click the **Connect** button.</span></span>  
  
 <span data-ttu-id="be21f-247">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="be21f-247">**Connect**</span></span>  
 <span data-ttu-id="be21f-248">如果這個伺服器執行個體是在與其他需要連接的伺服器執行個體不同的帳戶下執行，請按一下此按鈕。</span><span class="sxs-lookup"><span data-stu-id="be21f-248">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="be21f-249">**取消**</span><span class="sxs-lookup"><span data-stu-id="be21f-249">**Cancel**</span></span>  
 <span data-ttu-id="be21f-250">按一下可取消精靈。</span><span class="sxs-lookup"><span data-stu-id="be21f-250">Click to cancel the wizard.</span></span> <span data-ttu-id="be21f-251">在 **[連接到複本]** 頁面上，取消精靈會導致精靈結束，而不執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="be21f-251">On the **Connect to Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be21f-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be21f-252">See Also</span></span>  
 <span data-ttu-id="be21f-253">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be21f-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="be21f-254">[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="be21f-254">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="be21f-255">[容錯移轉和容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="be21f-255">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="be21f-256">[執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be21f-256">[Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="be21f-257">[執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be21f-257">[Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="be21f-258">透過強制仲裁執行 WSFC 災害復原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="be21f-258">WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  
