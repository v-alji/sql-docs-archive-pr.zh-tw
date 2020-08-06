---
title: 教學課程：利用行動用戶端複寫資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdf8be7cb0da11f0aa1022ba656d50c10826ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606730"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a><span data-ttu-id="121be-102">教學課程：利用行動用戶端複寫資料</span><span class="sxs-lookup"><span data-stu-id="121be-102">Tutorial: Replicating Data with Mobile Clients</span></span>
  <span data-ttu-id="121be-103">對於在中央伺服器與只是偶爾連接的行動用戶端之間移動資料的問題，複寫是一個很好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="121be-103">Replication is a good solution to the problem of moving data between a central server and mobile clients that are only occasionally connected.</span></span> <span data-ttu-id="121be-104">您可以使用複寫的精靈，輕鬆設定及管理複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="121be-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="121be-105">本教學課程告訴您，如何為行動用戶端設定複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="121be-105">This tutorial shows you how to configure a replication topology for mobile clients.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="121be-106">學習內容</span><span class="sxs-lookup"><span data-stu-id="121be-106">What You Will Learn</span></span>  
 <span data-ttu-id="121be-107">在本教學課程中，您將使用合併複寫，從中央資料庫發行資料給一個或多個行動用戶端使用者，讓每一個使用者都取得獨一無二篩選的資料子集。</span><span class="sxs-lookup"><span data-stu-id="121be-107">In this tutorial you will use merge replication to publish data from a central database to one or more mobile users so that each user gets a uniquely filtered subset of the data.</span></span> <span data-ttu-id="121be-108">第 1 課告訴您如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 建立發行集。</span><span class="sxs-lookup"><span data-stu-id="121be-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="121be-109">接下來的課程會告訴您，如何建立及同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="121be-109">Later lessons show how to create and synchronize a subscription.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="121be-110">需求</span><span class="sxs-lookup"><span data-stu-id="121be-110">Requirements</span></span>  
 <span data-ttu-id="121be-111">此教學課程是特別提供給熟悉基本資料庫作業但對複寫經驗有限的使用者。</span><span class="sxs-lookup"><span data-stu-id="121be-111">This tutorial is intended for users familiar with fundamental database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="121be-112">開始進行本教學課程之前，必須先完成 [教學課程：準備伺服器進行複寫](tutorial-preparing-the-server-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="121be-112">Before you start this tutorial, you must complete [Tutorial: Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="121be-113">若要使用這個教學課程，系統上必須已安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="121be-113">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   <span data-ttu-id="121be-114">在發行者伺服器 (來源)：</span><span class="sxs-lookup"><span data-stu-id="121be-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="121be-115">任何版本的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，除了 Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) 或 [!INCLUDE[ssEW](../../includes/ssew-md.md)]以外。</span><span class="sxs-lookup"><span data-stu-id="121be-115">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="121be-116">這兩種版本無法做為複寫發行者。</span><span class="sxs-lookup"><span data-stu-id="121be-116">These editions cannot be a replication Publisher.</span></span>  
  
    -   <span data-ttu-id="121be-117">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="121be-117">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="121be-118">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="121be-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="121be-119">訂閱者伺服器 (目的地)：</span><span class="sxs-lookup"><span data-stu-id="121be-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="121be-120">任何版本的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，除了 [!INCLUDE[ssEW](../../includes/ssew-md.md)]以外。</span><span class="sxs-lookup"><span data-stu-id="121be-120">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="121be-121">不受本教學課程建立的發行集支援。</span><span class="sxs-lookup"><span data-stu-id="121be-121">is not supported by the publication created in this tutorial.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="121be-122">依預設，複寫未安裝在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="121be-122">Replication is not installed by default on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="121be-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，您必須使用 sysadmin 固定伺服器角色成員的登入，連接到發行者和訂閱者。</span><span class="sxs-lookup"><span data-stu-id="121be-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the sysadmin fixed server role.</span></span>  
  
 <span data-ttu-id="121be-124">**完成本教學課程的估計時間：30分鐘。**</span><span class="sxs-lookup"><span data-stu-id="121be-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="121be-125">本教學課程中的課程</span><span class="sxs-lookup"><span data-stu-id="121be-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="121be-126">第 1 課：使用合併式複寫發行資料</span><span class="sxs-lookup"><span data-stu-id="121be-126">Lesson 1: Publishing Data Using Merge Replication</span></span>](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [<span data-ttu-id="121be-127">第 2 課：建立合併式發行集的訂閱</span><span class="sxs-lookup"><span data-stu-id="121be-127">Lesson 2: Creating a Subscription to the Merge Publication</span></span>](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [<span data-ttu-id="121be-128">開始教學課程</span><span class="sxs-lookup"><span data-stu-id="121be-128">Start the Tutorial</span></span>](merge/merge-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="121be-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="121be-129">See Also</span></span>  
 [<span data-ttu-id="121be-130">複寫程式設計概念</span><span class="sxs-lookup"><span data-stu-id="121be-130">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
