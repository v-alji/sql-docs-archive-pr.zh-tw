---
title: 初始化訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8c9388138ddec275dc1abd2b75e0b0c7fc99de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585816"
---
# <a name="initialize-subscriptions"></a><span data-ttu-id="f9366-102">初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="f9366-102">Initialize Subscriptions</span></span>
  <span data-ttu-id="f9366-103">訂閱者必須先初始化，才能開始接收複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="f9366-103">Subscribers must be initialized before they can begin receiving replicated data.</span></span> <span data-ttu-id="f9366-104">不需要有初始資料集，但訂閱者至少必須有每個複寫物件的結構描述，以及複寫所需的任何中繼資料表和程序。</span><span class="sxs-lookup"><span data-stu-id="f9366-104">An initial dataset is not required, but the Subscriber must at least have the schema for each replicated object and any metadata tables and procedures required by replication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9366-105">選項。</span><span class="sxs-lookup"><span data-stu-id="f9366-105">Options</span></span>  
 <span data-ttu-id="f9366-106">**訂閱屬性**</span><span class="sxs-lookup"><span data-stu-id="f9366-106">**Subscription properties**</span></span>  
 <span data-ttu-id="f9366-107">針對每個需要初始資料集的訂閱者，選取 **[初始化]** 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f9366-107">Select the check box in the **Initialize** column for each Subscriber that requires an initial data set.</span></span> <span data-ttu-id="f9366-108">如果清除此核取方塊，則只會初始化複寫中繼資料和程序。</span><span class="sxs-lookup"><span data-stu-id="f9366-108">If the check box is cleared, only the replication metadata and procedures will be initialized.</span></span> <span data-ttu-id="f9366-109">如需不使用快照集初始化訂閱的詳細資訊，請參閱[不使用快照集初始化交易式訂閱](initialize-a-transactional-subscription-without-a-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="f9366-109">For more information about initializing a subscription without a snapshot, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="f9366-110">在 **[初始化時機]** 資料行的下拉式清單方塊中，選取 **[立即]** ，即可使合併代理程式或散發代理程式在此精靈完成後，將快照集檔案傳送至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="f9366-110">Select **Immediately** from the drop-down list box in the **Initialize When** column to have the Merge Agent or Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed.</span></span> <span data-ttu-id="f9366-111">選取 **[第一次同步處理時]** ，即可使代理程式在下一個執行排程傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="f9366-111">Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run.</span></span> <span data-ttu-id="f9366-112">  的提取訂閱無法使用 [立即][!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 選項。</span><span class="sxs-lookup"><span data-stu-id="f9366-112">The **Immediately** option is not available for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="f9366-113">合併代理程式或散發代理程式無法在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]的執行個體上執行；因此必須經由其他方法初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="f9366-113">The Merge Agent and Distribution Agent do not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]; therefore the subscription must be initialized through another method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9366-114">精靈可能會提示散發者的連接，以便為散發者代理程式或合併代理程式啟動適當的作業。</span><span class="sxs-lookup"><span data-stu-id="f9366-114">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9366-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9366-115">See Also</span></span>  
 <span data-ttu-id="f9366-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f9366-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="f9366-117">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f9366-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="f9366-118">[初始化訂閱](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f9366-118">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="f9366-119">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="f9366-119">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
