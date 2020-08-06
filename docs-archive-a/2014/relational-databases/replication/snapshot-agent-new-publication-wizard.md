---
title: 快照集代理程式 (新增發行集精靈) | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c45fa3444fb2f81436a40a2bfb80519aea105c47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606746"
---
# <a name="snapshot-agent-new-publication-wizard"></a><span data-ttu-id="63ffe-102">快照集代理程式 (新增發行集精靈)</span><span class="sxs-lookup"><span data-stu-id="63ffe-102">Snapshot Agent (New Publication Wizard)</span></span>
  <span data-ttu-id="63ffe-103">快照集代理程式會建立檔案，檔案中包含用來初始化新訂閱的發行集結構描述和資料。</span><span class="sxs-lookup"><span data-stu-id="63ffe-103">The Snapshot Agent creates files containing the publication schema and data that are used to initialize new subscriptions.</span></span> <span data-ttu-id="63ffe-104">依預設，在新增發行集精靈中建立發行集之後，會立即執行快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="63ffe-104">By default, the Snapshot Agent runs immediately after the publication is created in the New Publication Wizard.</span></span> <span data-ttu-id="63ffe-105">此後，代理程式就根據您指定的排程來執行。</span><span class="sxs-lookup"><span data-stu-id="63ffe-105">Subsequently, the agent runs according to a schedule you specify.</span></span> <span data-ttu-id="63ffe-106">代理程式每次執行時是否建立新的快照集檔案，視選擇的複寫類型和選項而定。</span><span class="sxs-lookup"><span data-stu-id="63ffe-106">Whether the agent creates new snapshot files each time it runs depends on the type of replication and options chosen.</span></span> <span data-ttu-id="63ffe-107">如需詳細資訊，請參閱[建立和套用快照集](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="63ffe-107">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="63ffe-108">對於使用參數化篩選的合併式發行集，在完成發行集快照集之後，您必須為資料的每一個資料分割建立快照集。</span><span class="sxs-lookup"><span data-stu-id="63ffe-108">For merge publications that use parameterized filters, you must create a snapshot for each partition of data after the publication snapshot has completed.</span></span> <span data-ttu-id="63ffe-109">如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="63ffe-109">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="63ffe-110">選項。</span><span class="sxs-lookup"><span data-stu-id="63ffe-110">Options</span></span>  
 <span data-ttu-id="63ffe-111">**[立即建立快照集]** (合併式複寫) 或 **[立即建立快照集，並保留快照集為可使用狀態，以初始化訂閱]** (異動複寫)</span><span class="sxs-lookup"><span data-stu-id="63ffe-111">**Create a snapshot immediately** (merge replication) or **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** (transactional replication)</span></span>  
 <span data-ttu-id="63ffe-112">選取此核取方塊即可在完成新增發行集精靈之後立即建立快照集。</span><span class="sxs-lookup"><span data-stu-id="63ffe-112">Select this check box to create a snapshot immediately after the New Publication Wizard is completed.</span></span> <span data-ttu-id="63ffe-113">如果您想要在產生快照集之後變更 **[發行集屬性]** 對話方塊中的快照集屬性，或要初始化不具有快照集的訂閱者，請清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="63ffe-113">Clear this check box if you plan to change snapshot properties in the **Publication Properties** dialog box before generating a snapshot, or if you will initialize the Subscriber without a snapshot.</span></span> <span data-ttu-id="63ffe-114">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="63ffe-114">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63ffe-115">精靈可能會提示散發者的連接，以便為散發者代理程式或合併代理程式啟動適當的作業。</span><span class="sxs-lookup"><span data-stu-id="63ffe-115">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
 <span data-ttu-id="63ffe-116">**排程快照集代理程式在下列時間執行**</span><span class="sxs-lookup"><span data-stu-id="63ffe-116">**Schedule the Snapshot Agent to run at the following times**</span></span>  
 <span data-ttu-id="63ffe-117">接受執行快照集代理程式的預設排程，或按一下 **[變更]** 來指定排程。</span><span class="sxs-lookup"><span data-stu-id="63ffe-117">Accept the default schedule for running the Snapshot Agent, or click **Change** to specify a schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ffe-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ffe-118">See Also</span></span>  
 <span data-ttu-id="63ffe-119">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="63ffe-119">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="63ffe-120">[建立和套用初始快照集](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="63ffe-120">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="63ffe-121">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="63ffe-121">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="63ffe-122">[使用快照集初始化訂閱](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="63ffe-122">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="63ffe-123">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="63ffe-123">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="63ffe-124">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="63ffe-124">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
