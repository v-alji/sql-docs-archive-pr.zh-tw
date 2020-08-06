---
title: 進階合併式複寫衝突偵測與解決 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- column-level conflict tracking
- row-level conflict tracking
- viewing merge replication conflicts
- resolving merge replication conflicts
- logical record-level conflict tracking [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9122f0d704db948a0a8134da2b86e34ea6426dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584464"
---
# <a name="advanced-merge-replication-conflict-detection-and-resolution"></a><span data-ttu-id="c2861-102">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="c2861-102">Advanced Merge Replication Conflict Detection and Resolution</span></span>
  <span data-ttu-id="c2861-103">發行者與訂閱者連接並進行同步處理時，合併代理程式會偵測是否有任何衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-103">When a Publisher and a Subscriber are connected and synchronization occurs, the Merge Agent detects if there are any conflicts.</span></span> <span data-ttu-id="c2861-104">如果偵測到衝突，「合併代理程式」會使用衝突解析程式 (在發行項加入發行集時指定)，決定要接受及傳播至其他站台的資料。</span><span class="sxs-lookup"><span data-stu-id="c2861-104">If conflicts are detected, the Merge Agent uses a conflict resolver (which is specified when an article is added to a publication) to determine which data is accepted and propagated to other sites.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2861-105">雖然「訂閱者」會與「發行者」同步，但是衝突通常是在不同「訂閱者」端進行更新之間發生，而不是在「訂閱者」端和「發行者」端進行更新時發生。</span><span class="sxs-lookup"><span data-stu-id="c2861-105">Although a Subscriber synchronizes with the Publisher, conflicts typically occur between updates that are made at different Subscribers, instead of updates being made at a Subscriber and at the Publisher.</span></span>  
  
 <span data-ttu-id="c2861-106">衝突偵測與解決的行為取決於下列選項，這些選項會在本主題中說明：</span><span class="sxs-lookup"><span data-stu-id="c2861-106">The behavior of conflict detection and resolution depends on the following options, which are described in this topic:</span></span>  
  
-   <span data-ttu-id="c2861-107">您是否指定資料行層級追蹤、資料列層級追蹤或邏輯記錄層級追蹤。</span><span class="sxs-lookup"><span data-stu-id="c2861-107">Whether you specify column-level tracking, row-level tracking, or logical record-level tracking.</span></span>  
  
-   <span data-ttu-id="c2861-108">您是否指定預設的優先權式解決機制或指定發行項解析程式。</span><span class="sxs-lookup"><span data-stu-id="c2861-108">Whether you specify the default priority-based resolution mechanism or specify an article resolver.</span></span> <span data-ttu-id="c2861-109">發行項解析程式可以是：</span><span class="sxs-lookup"><span data-stu-id="c2861-109">An article resolver can be:</span></span>  
  
    -   <span data-ttu-id="c2861-110">以 Managed 程式碼撰寫的 *商務邏輯處理常式* 。</span><span class="sxs-lookup"><span data-stu-id="c2861-110">A *business logic handler* written in managed code.</span></span>  
  
    -   <span data-ttu-id="c2861-111">以 COM 為基礎的 *自訂解析程式*。</span><span class="sxs-lookup"><span data-stu-id="c2861-111">A COM-based *custom resolver*.</span></span>  
  
    -   <span data-ttu-id="c2861-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]提供之以 COM 為基礎的解析程式。</span><span class="sxs-lookup"><span data-stu-id="c2861-112">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)].</span></span>  
  
     <span data-ttu-id="c2861-113">如果使用預設解析機制，則會依據所用的訂閱類型進一步決定行為：用戶端或伺服器。</span><span class="sxs-lookup"><span data-stu-id="c2861-113">If the default resolution mechanism is used, behavior is further determined by the type of subscription used: client or server.</span></span>  
  
## <a name="conflict-detection"></a><span data-ttu-id="c2861-114">衝突偵測</span><span class="sxs-lookup"><span data-stu-id="c2861-114">Conflict Detection</span></span>  
 <span data-ttu-id="c2861-115">資料變更是否算是衝突取決於您為發行項所設定的衝突追蹤類型：</span><span class="sxs-lookup"><span data-stu-id="c2861-115">Whether a data change qualifies as a conflict or not depends on the type of conflict tracking you set for an article:</span></span>  
  
-   <span data-ttu-id="c2861-116">當您選取資料行層級衝突追蹤時，如果在一個以上的複寫節點對相同資料列中的相同資料行進行變更，則該變更會被視為衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-116">If you select column-level conflict tracking, it is considered a conflict if changes are made to the same column in the same row at more than one replication node.</span></span>  
  
-   <span data-ttu-id="c2861-117">當您選取資料列層級追蹤時，如果在一個以上的複寫節點對相同資料列中的任何資料行進行變更，則該變更會被視為衝突 (對應資料列中受影響的資料行不需要相同)。</span><span class="sxs-lookup"><span data-stu-id="c2861-117">If you select row-level tracking, it is considered a conflict if changes are made to any columns in the same row at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
-   <span data-ttu-id="c2861-118">當您選取邏輯記錄層級追蹤時，如果在一個以上的複寫節點對相同邏輯記錄中的任何資料列進行變更，則該變更會被視為衝突 (對應資料列中受影響的資料行不需要相同)。</span><span class="sxs-lookup"><span data-stu-id="c2861-118">If you select logical record-level tracking, it is considered a conflict if changes are made to any row in the same logical record at more than one replication node (the columns affected in the corresponding rows need not be the same).</span></span>  
  
 <span data-ttu-id="c2861-119">如需詳細資訊，請參閱 [偵測和解決邏輯記錄中的衝突](advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-119">For more information, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
 <span data-ttu-id="c2861-120">若要指定發行項的衝突追蹤與解決層級，請參閱＜ [指定合併發行項的衝突追蹤與解決層級](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)＞。</span><span class="sxs-lookup"><span data-stu-id="c2861-120">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>  
  
## <a name="conflict-resolution"></a><span data-ttu-id="c2861-121">衝突解決</span><span class="sxs-lookup"><span data-stu-id="c2861-121">Conflict Resolution</span></span>  
 <span data-ttu-id="c2861-122">在偵測到衝突後，「合併代理程式」會啟動選取的衝突解析程式，並使用該解析程式決定衝突成功者。</span><span class="sxs-lookup"><span data-stu-id="c2861-122">After a conflict is detected, the Merge Agent launches the selected conflict resolver and uses the resolver to determine the conflict winner.</span></span> <span data-ttu-id="c2861-123">成功的資料列已套用至「發行者」與「訂閱者」，而失敗的資料列則已寫入衝突資料表。</span><span class="sxs-lookup"><span data-stu-id="c2861-123">The winning row is applied at the Publisher and Subscriber, and the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="c2861-124">衝突會在解析程式執行後立即解決，除非您選擇以互動方式解決衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-124">Conflicts are resolved immediately after the resolver executes, unless you select to resolve conflicts interactively.</span></span>  
  
### <a name="resolver-types"></a><span data-ttu-id="c2861-125">解析程式類型</span><span class="sxs-lookup"><span data-stu-id="c2861-125">Resolver Types</span></span>  
 <span data-ttu-id="c2861-126">在合併式複寫中，衝突解決會在發行項層級發生。</span><span class="sxs-lookup"><span data-stu-id="c2861-126">In merge replication, conflict resolution takes place at the article level.</span></span> <span data-ttu-id="c2861-127">對於由許多發行項所組成的發行集來說，您可以使用各種不同的衝突解析程式來處理不同的發行項，也可以使用相同的解析程式來解決一個發行項、數個發行項，或者組成發行集的所有發行項。</span><span class="sxs-lookup"><span data-stu-id="c2861-127">For publications composed of several articles, you can have different conflict resolvers serving different articles, or the same conflict resolver serving one article, several articles, or all the articles comprising a publication.</span></span>  
  
 <span data-ttu-id="c2861-128">如果您計劃使用預設的優先權式衝突解析程式，就無需設定發行項的解析程式屬性。</span><span class="sxs-lookup"><span data-stu-id="c2861-128">If you plan to use the default priority-based conflict resolver, you do not have to set the resolver property of an article.</span></span> <span data-ttu-id="c2861-129">如果您要使用發行項解析程式而非預設的解析程式，則必須在「發行者」上選取可用的解析程式，以設定要使用此解析程式的發行項之解析程式屬性。</span><span class="sxs-lookup"><span data-stu-id="c2861-129">If you want to use an article resolver instead of the default resolver, you must set the resolver property for the article that will use it by selecting an available resolver on the Publisher.</span></span> <span data-ttu-id="c2861-130">需要傳遞至解析程式的任何特定資訊，也可以在解析程式資訊屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="c2861-130">Any specific information that needs to be passed to the resolver can also be specified in the resolver information property.</span></span>  
  
 <span data-ttu-id="c2861-131">合併式複寫提供四種類型的衝突解析程式：</span><span class="sxs-lookup"><span data-stu-id="c2861-131">Merge replication offers four types of conflict resolvers:</span></span>  
  
-   <span data-ttu-id="c2861-132">預設的優先權式衝突解析程式</span><span class="sxs-lookup"><span data-stu-id="c2861-132">The default priority-based conflict resolver</span></span>  
  
     <span data-ttu-id="c2861-133">根據訂閱是客訂閱或主訂閱而定，預設解決機制的行為會有所差異。</span><span class="sxs-lookup"><span data-stu-id="c2861-133">The default resolution mechanism behaves differently, depending on whether a subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="c2861-134">您可指派優先權值給使用主訂閱的個別「訂閱者」；對具有最高優先權的節點所做的變更會在任何衝突中優先。</span><span class="sxs-lookup"><span data-stu-id="c2861-134">You assign priority values to individual Subscribers that use server subscriptions; changes made at the node with the highest priority win any conflicts.</span></span> <span data-ttu-id="c2861-135">對於客訂閱，第一個寫入「發行者」的變更會在衝突中優先。</span><span class="sxs-lookup"><span data-stu-id="c2861-135">For client subscriptions, the first change written to the Publisher wins the conflict.</span></span>  
  
     <span data-ttu-id="c2861-136">建立訂閱之後，就不能變更訂閱的類型。</span><span class="sxs-lookup"><span data-stu-id="c2861-136">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
-   <span data-ttu-id="c2861-137">商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="c2861-137">A business logic handler</span></span>  
  
     <span data-ttu-id="c2861-138">商務邏輯處理常式架構允許您撰寫在合併同步處理過程中呼叫的 Managed 程式碼組件。</span><span class="sxs-lookup"><span data-stu-id="c2861-138">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="c2861-139">該組件包含商務邏輯，可在同步處理期間回應衝突及一些其他條件。</span><span class="sxs-lookup"><span data-stu-id="c2861-139">The assembly includes business logic that can respond to conflicts and a number of other conditions during synchronization.</span></span> <span data-ttu-id="c2861-140">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-140">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
-   <span data-ttu-id="c2861-141">以 COM 為基礎的自訂解析程式</span><span class="sxs-lookup"><span data-stu-id="c2861-141">A COM-based custom resolver</span></span>  
  
     <span data-ttu-id="c2861-142">合併式複寫提供一個 API，用於以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 等語言將解析程式撰寫為 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="c2861-142">Merge replication provides an API for writing resolvers as COM objects in languages such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="c2861-143">如需詳細資訊，請參閱 [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-143">For more information, see [COM-Based Custom Resolvers](advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
-   <span data-ttu-id="c2861-144">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]提供之以 COM 為基礎的解析程式。</span><span class="sxs-lookup"><span data-stu-id="c2861-144">A COM-based resolver supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span></span>  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c2861-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 包含多個以 COM 為基礎的解析程式。</span><span class="sxs-lookup"><span data-stu-id="c2861-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] includes a number of COM-based resolvers.</span></span> <span data-ttu-id="c2861-146">如需詳細資訊，請參閱 [以 COM 為基礎的 Microsoft 解析程式](advanced-merge-replication-conflict-com-based-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-146">For more information, see [Microsoft COM-Based Resolvers](advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
 <span data-ttu-id="c2861-147">如需如何選取適當解析程式類型的詳細資訊，請參閱[選擇解析程式](advanced-merge-replication-conflict-choose-a-resolver.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-147">For information about how to select the appropriate type of resolver, see [Choose a Resolver](advanced-merge-replication-conflict-choose-a-resolver.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2861-148">某些發行項解析程式的撰寫僅供處理特定作業的衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-148">Some article resolvers are written to handle conflicts only for certain operations.</span></span> <span data-ttu-id="c2861-149">例如，某個解析程式可以處理更新，但無法處理插入或刪除。</span><span class="sxs-lookup"><span data-stu-id="c2861-149">For example a resolver might handle updates, but not inserts or deletes.</span></span> <span data-ttu-id="c2861-150">預設的優先權式衝突解析程式會處理沒有由發行項解析程式所處理的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-150">The default priority-based conflict resolver handles any conflicts not handled by the article resolver.</span></span>  
  
 <span data-ttu-id="c2861-151">若要指定合併訂閱類型與衝突解決優先權，請參閱</span><span class="sxs-lookup"><span data-stu-id="c2861-151">To specify a merge subscription type and conflict resolution priority, see</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="c2861-152">:[指定合併訂閱類型及衝突解決優先順序 &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span><span class="sxs-lookup"><span data-stu-id="c2861-152">: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)</span></span>  
  
-   <span data-ttu-id="c2861-153">複寫 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 程式設計與 Replication Management Objects (RMO) 程式設計：[建立提取訂閱](../create-a-pull-subscription.md)和[建立發送訂閱](../create-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="c2861-153">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming and Replication Management Objects (RMO) programming: [Create a Pull Subscription](../create-a-pull-subscription.md) and [Create a Push Subscription](../create-a-push-subscription.md)</span></span>  
  
### <a name="interactive-resolver"></a><span data-ttu-id="c2861-154">互動解析程式</span><span class="sxs-lookup"><span data-stu-id="c2861-154">Interactive Resolver</span></span>  
 <span data-ttu-id="c2861-155">複寫提供「互動解析程式」使用者介面，可與預設的優先權式衝突解析程式或發行項解析程式一起使用。</span><span class="sxs-lookup"><span data-stu-id="c2861-155">Replication supplies an Interactive Resolver user interface that can be used in conjunction with either the default priority-based conflict resolver or an article resolver.</span></span> <span data-ttu-id="c2861-156">透過 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager 執行視需要的同步處理時，「互動解析程式」會在執行階段顯示衝突資料，並讓您選擇如何解決衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-156">When performing on-demand synchronization through [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager, the Interactive Resolver displays conflict data at run-time, and lets you choose how to resolve conflicts.</span></span> <span data-ttu-id="c2861-157">如需有關如何啟用互動式解決及啟動「互動解析程式」的詳細資訊，請參閱＜ [互動式衝突解決](advanced-merge-replication-conflict-interactive-resolution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c2861-157">For more information about how to enable interactive resolution and launch the Interactive Resolver, see [Interactive Conflict Resolution](advanced-merge-replication-conflict-interactive-resolution.md).</span></span>  
  
## <a name="viewing-conflicts"></a><span data-ttu-id="c2861-158">檢視衝突</span><span class="sxs-lookup"><span data-stu-id="c2861-158">Viewing Conflicts</span></span>  
 <span data-ttu-id="c2861-159">檢視衝突最直接的方法是使用「複寫衝突檢視器」，該檢視器可從 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 取得 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 也提供允許查詢衝突資料表的預存程序)。</span><span class="sxs-lookup"><span data-stu-id="c2861-159">The most straightforward way to view conflicts is to use the Replication Conflict Viewer, available from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also provides stored procedures that allow the conflict tables to be queried.).</span></span> <span data-ttu-id="c2861-160">「衝突檢視器」和「互動解析程式」是類似的工具，不過「互動解析程式」可讓您在同步處理發生時解決衝突，而「衝突解析程式」是設計用來在已解決衝突後檢視衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-160">The Conflict Viewer and Interactive Resolver are similar tools, but the Interactive Resolver allows you to resolve conflicts as synchronization occurs, whereas the Conflict Viewer is designed for viewing conflicts after they have been resolved.</span></span> <span data-ttu-id="c2861-161">如果系統資料表中仍有可用的衝突中繼資料 (衝突中繼資料依預設會保留 14 天)，您可以在「衝突檢視器」中覆寫衝突解決結果，不過如果經常需要直接介入，請考慮使用「互動解析程式」。</span><span class="sxs-lookup"><span data-stu-id="c2861-161">If the conflict metadata is still available in the system tables (conflict metadata is retained for 14 days by default), you can override conflict resolution outcomes in the Conflict Viewer, but if direct intervention is regularly required, consider using the Interactive Resolver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2861-162">「衝突檢視器」中不會顯示涉及邏輯記錄的衝突。</span><span class="sxs-lookup"><span data-stu-id="c2861-162">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="c2861-163">若要檢視這些衝突的相關資訊，請使用複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="c2861-163">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="c2861-164">如需詳細資訊，請參閱[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c2861-164">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
 <span data-ttu-id="c2861-165">「衝突檢視器」會顯示下列三個系統資料表中的資訊：</span><span class="sxs-lookup"><span data-stu-id="c2861-165">The Conflict Viewer displays information from three system tables:</span></span>  
  
-   <span data-ttu-id="c2861-166">複寫會為合併發行項中的每個資料表建立衝突資料表，並使用格式為 **MSmerge_conflict_\<PublicationName>_\<ArticleName>** 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2861-166">Replication creates a conflict table for each table in a merge article, with a name in the form **MSmerge_conflict_\<PublicationName>_\<ArticleName>**.</span></span>  
  
     <span data-ttu-id="c2861-167">衝突資料表的結構與其所根據的資料表相同。</span><span class="sxs-lookup"><span data-stu-id="c2861-167">Conflict tables have the same structure as the tables on which they are based.</span></span> <span data-ttu-id="c2861-168">其中一個資料表內的資料列含有衝突資料列的失敗版本 (資料列的優先版本位在實際的使用者資料表中)。</span><span class="sxs-lookup"><span data-stu-id="c2861-168">A row in one of these tables consists of the losing version of a conflict row (the winning version of the row is in the actual user table).</span></span>  
  
-   <span data-ttu-id="c2861-169">**MSmerge_conflicts_info** 資料表提供每一個衝突的相關資訊，包括衝突類型。</span><span class="sxs-lookup"><span data-stu-id="c2861-169">The **MSmerge_conflicts_info** table provides information about each conflict, including the conflict type.</span></span>  
  
-   <span data-ttu-id="c2861-170">**sysmergearticles** 資料表可識別哪些使用者資料表具有衝突資料表，並提供衝突資料表的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c2861-170">The **sysmergearticles** table identifies which user tables have conflict tables and provides information about the conflict tables.</span></span>  
  
 <span data-ttu-id="c2861-171">依預設，會儲存衝突資訊：</span><span class="sxs-lookup"><span data-stu-id="c2861-171">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="c2861-172">如果發行集相容性層級為 90RTM 或更高，則是在「發行者」與「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="c2861-172">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="c2861-173">如果發行集相容性層級低於 80RTM，則是在發行者端。</span><span class="sxs-lookup"><span data-stu-id="c2861-173">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="c2861-174">如果「訂閱者」執行 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]，則會儲存在「發行者」端。</span><span class="sxs-lookup"><span data-stu-id="c2861-174">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../../includes/ssew-md.md)].</span></span> <span data-ttu-id="c2861-175">衝突資料無法儲存在 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] 訂閱者上。</span><span class="sxs-lookup"><span data-stu-id="c2861-175">Conflict data cannot be stored on [!INCLUDE[ssEW](../../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="c2861-176">**若要檢視衝突**</span><span class="sxs-lookup"><span data-stu-id="c2861-176">**To view conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="c2861-177">:[檢視並解決合併式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="c2861-177">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   <span data-ttu-id="c2861-178">複寫 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 程式設計：[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](../view-conflict-information-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="c2861-178">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2861-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2861-179">See Also</span></span>  
 [<span data-ttu-id="c2861-180">同步處理資料</span><span class="sxs-lookup"><span data-stu-id="c2861-180">Synchronize Data</span></span>](../synchronize-data.md)  
  
  
