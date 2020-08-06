---
title: 教學課程：在連續連接的伺服器之間複寫資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 415cac62112c1c1d2aa6c42ec189c2614ec03923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606732"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a><span data-ttu-id="d21bc-102">教學課程：在連續連接的伺服器之間複寫資料</span><span class="sxs-lookup"><span data-stu-id="d21bc-102">Tutorial: Replicating Data Between Continuously Connected Servers</span></span>
  <span data-ttu-id="d21bc-103">對於在連續連接的伺服器之間移動資料的問題，複寫是一個很好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d21bc-103">Replication is a good solution to the problem of moving data between continuously connected servers.</span></span> <span data-ttu-id="d21bc-104">您可以使用複寫的精靈，輕鬆設定及管理複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="d21bc-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="d21bc-105">本教學課程告訴您，如何為連續連接的伺服器設定複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="d21bc-105">This tutorial shows you how to configure a replication topology for continuously connected servers.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="d21bc-106">學習內容</span><span class="sxs-lookup"><span data-stu-id="d21bc-106">What You Will Learn</span></span>  
 <span data-ttu-id="d21bc-107">本教學課程告訴您如何使用異動複寫，從一個資料庫將資料發行到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="d21bc-107">This tutorial will show you how to publish data from one database to another using transactional replication.</span></span> <span data-ttu-id="d21bc-108">第 1 課告訴您如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 建立發行集。</span><span class="sxs-lookup"><span data-stu-id="d21bc-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="d21bc-109">接下來的課程會告訴您，如何建立及驗證訂閱，以及如何測量延遲。</span><span class="sxs-lookup"><span data-stu-id="d21bc-109">Later lessons show how to create and validate a subscription and how to measure latency.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d21bc-110">需求</span><span class="sxs-lookup"><span data-stu-id="d21bc-110">Requirements</span></span>  
 <span data-ttu-id="d21bc-111">本教學課程是特別提供給熟悉基本資料庫作業但對複寫經驗有限的使用者。</span><span class="sxs-lookup"><span data-stu-id="d21bc-111">This tutorial is intended for users who are familiar with basic database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="d21bc-112">本教學課程要求您，先完成上一個教學課程 [準備伺服器進行複寫](tutorial-preparing-the-server-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="d21bc-112">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="d21bc-113">若要使用這個教學課程，系統上必須已安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="d21bc-113">To use this tutorial, your system must have the following components:</span></span>  
  
-   <span data-ttu-id="d21bc-114">在發行者伺服器 (來源)：</span><span class="sxs-lookup"><span data-stu-id="d21bc-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="d21bc-115">任何版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，除了 Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) 或 [!INCLUDE[ssEW](../../includes/ssew-md.md)]以外。</span><span class="sxs-lookup"><span data-stu-id="d21bc-115">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="d21bc-116">這兩種版本無法做為複寫發行者。</span><span class="sxs-lookup"><span data-stu-id="d21bc-116">These editions cannot be replication Publishers.</span></span>  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] <span data-ttu-id="d21bc-117">範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="d21bc-117">sample database.</span></span> <span data-ttu-id="d21bc-118">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="d21bc-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="d21bc-119">訂閱者伺服器 (目的地)：</span><span class="sxs-lookup"><span data-stu-id="d21bc-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="d21bc-120">任何版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，除了 [!INCLUDE[ssEW](../../includes/ssew-md.md)]以外。</span><span class="sxs-lookup"><span data-stu-id="d21bc-120">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="d21bc-121">在異動複寫中不能是訂閱者。</span><span class="sxs-lookup"><span data-stu-id="d21bc-121">cannot be a Subscriber in transactional replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d21bc-122">依預設，複寫未安裝在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="d21bc-122">Replication is not installed on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d21bc-123">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，您必須使用**系統管理員（sysadmin** ）固定伺服器角色成員的登入，連接到「發行者」和「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="d21bc-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="d21bc-124">**完成本教學課程的估計時間：30分鐘。**</span><span class="sxs-lookup"><span data-stu-id="d21bc-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="d21bc-125">本教學課程中的課程</span><span class="sxs-lookup"><span data-stu-id="d21bc-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="d21bc-126">第 1 課：使用異動複寫發行資料</span><span class="sxs-lookup"><span data-stu-id="d21bc-126">Lesson 1: Publishing Data Using Transactional Replication</span></span>](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [<span data-ttu-id="d21bc-127">第 2 課：建立交易式發行集的訂閱</span><span class="sxs-lookup"><span data-stu-id="d21bc-127">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [<span data-ttu-id="d21bc-128">第 3 課：驗證訂閱及測量延遲</span><span class="sxs-lookup"><span data-stu-id="d21bc-128">Lesson 3: Validating the Subscription and Measuring Latency</span></span>](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [<span data-ttu-id="d21bc-129">開始教學課程</span><span class="sxs-lookup"><span data-stu-id="d21bc-129">Start the Tutorial</span></span>](transactional/transactional-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="d21bc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d21bc-130">See Also</span></span>  
 [<span data-ttu-id="d21bc-131">複寫程式設計概念</span><span class="sxs-lookup"><span data-stu-id="d21bc-131">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
