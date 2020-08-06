---
title: 教學課程：準備伺服器進行複寫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1f036ff2a111ee6b5f97655b9bebaf34391a436
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606734"
---
# <a name="tutorial-preparing-the-server-for-replication"></a><span data-ttu-id="10f2f-102">教學課程：準備伺服器進行複寫</span><span class="sxs-lookup"><span data-stu-id="10f2f-102">Tutorial: Preparing the Server for Replication</span></span>
  <span data-ttu-id="10f2f-103">在設定複寫拓撲之前，規劃安全性是很重要的步驟。</span><span class="sxs-lookup"><span data-stu-id="10f2f-103">It is important to plan for security before you configure your replication topology.</span></span> <span data-ttu-id="10f2f-104">此教學課程為您示範：如何讓複寫拓撲有更強固的保護，以及如何設定散發，這是複寫資料的第一步。</span><span class="sxs-lookup"><span data-stu-id="10f2f-104">This tutorial shows you how to better secure a replication topology as well as how to configure distribution, which is the first step in replicating data.</span></span> <span data-ttu-id="10f2f-105">您必須完成此教學課程，才能進行任何其他教學課程。</span><span class="sxs-lookup"><span data-stu-id="10f2f-105">You must complete this tutorial before any of the others.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10f2f-106">若要在伺服器之間安全地複寫資料，必須實作 [複寫安全性最佳做法](security/replication-security-best-practices.md)中的所有建議。</span><span class="sxs-lookup"><span data-stu-id="10f2f-106">To replicate data securely between servers, you should implement all of the recommendations in [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="10f2f-107">學習內容</span><span class="sxs-lookup"><span data-stu-id="10f2f-107">What You Will Learn</span></span>  
 <span data-ttu-id="10f2f-108">在此教學課程中，您將學習如何準備伺服器，以便在最低權限下安全地執行複寫。</span><span class="sxs-lookup"><span data-stu-id="10f2f-108">In this tutorial you will learn how to prepare a server so that replication can run securely with least privileges.</span></span> <span data-ttu-id="10f2f-109">第 1 課示範如何建立用來執行複寫代理程式的 Windows 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="10f2f-109">The first lesson shows how to create the Windows service accounts used to run replication agents.</span></span> <span data-ttu-id="10f2f-110">第 2 課示範如何設定用來產生及儲存發行集快照集的資料夾。</span><span class="sxs-lookup"><span data-stu-id="10f2f-110">The second lesson shows how to configure the folder used to generate and store publication snapshots.</span></span> <span data-ttu-id="10f2f-111">第 3 課示範如何設定散發及設定權限。</span><span class="sxs-lookup"><span data-stu-id="10f2f-111">The third lesson shows how to configure distribution and set permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f2f-112">需求</span><span class="sxs-lookup"><span data-stu-id="10f2f-112">Requirements</span></span>  
 <span data-ttu-id="10f2f-113">此教學課程是特別提供給熟悉基本資料庫作業但只稍微涉獵複寫作業的使用者。</span><span class="sxs-lookup"><span data-stu-id="10f2f-113">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to replication.</span></span>  
  
 <span data-ttu-id="10f2f-114">若要使用這個教學課程，系統上必須已安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="10f2f-114">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] <span data-ttu-id="10f2f-115">與 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="10f2f-115">with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="10f2f-116">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="10f2f-116">To enhance security, the sample databases are not installed by default.</span></span>  
  
 <span data-ttu-id="10f2f-117">**完成本教學課程的估計時間：30分鐘。**</span><span class="sxs-lookup"><span data-stu-id="10f2f-117">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="10f2f-118">本教學課程中的課程</span><span class="sxs-lookup"><span data-stu-id="10f2f-118">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="10f2f-119">第 1 課：建立用於複寫的 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="10f2f-119">Lesson 1: Creating Windows Accounts for Replication</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [<span data-ttu-id="10f2f-120">第 2 課：準備快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="10f2f-120">Lesson 2: Preparing the Snapshot Folder</span></span>](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [<span data-ttu-id="10f2f-121">第 3 課：設定散發</span><span class="sxs-lookup"><span data-stu-id="10f2f-121">Lesson 3: Configuring Distribution</span></span>](lesson-3-configuring-distribution.md)  
  
 [<span data-ttu-id="10f2f-122">開始教學課程</span><span class="sxs-lookup"><span data-stu-id="10f2f-122">Start the Tutorial</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="10f2f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10f2f-123">See Also</span></span>  
 <span data-ttu-id="10f2f-124">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="10f2f-124">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="10f2f-125">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="10f2f-125">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
