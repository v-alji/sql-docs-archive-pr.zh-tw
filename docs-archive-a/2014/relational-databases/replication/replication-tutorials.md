---
title: 複寫教學課程 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4d70abd6c58b3eb0fa4a53e2806ab1b3fbe9245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585266"
---
# <a name="replication-tutorials"></a><span data-ttu-id="1a6a8-102">複寫教學課程</span><span class="sxs-lookup"><span data-stu-id="1a6a8-102">Replication Tutorials</span></span>
  <span data-ttu-id="1a6a8-103">複寫課程包含可用來學習如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]設定及執行複寫拓撲的教學課程。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-103">Replication includes tutorials that you can use to learn how to set up and run replication topologies using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1a6a8-104">在複寫教學課程中，「發行者」是指包含所要複寫之來源資料的伺服器，而「訂閱者」則是指目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-104">In the replication tutorials, "Publisher" refers to the server that contains that source data being replicated and "Subscriber" refers to the destination server.</span></span> <span data-ttu-id="1a6a8-105">發行者和訂閱者可以共用相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，但這不是必要條件。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-105">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="1a6a8-106">如需詳細資訊，請參閱 [複寫發行模型概觀](publish/replication-publishing-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-106">For more information, see [Replication Publishing Model Overview](publish/replication-publishing-model-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a6a8-107">這些教學課程所示範的大部分工作都可以透過程式設計的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-107">Most of the tasks shown in these tutorials can be performed programmatically.</span></span> <span data-ttu-id="1a6a8-108">如需詳細資訊，請參閱《[開發人員指南》 &#40;Replication&#41;](concepts/replication-developer-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-108">For more information, see [Developer's Guide &#40;Replication&#41;](concepts/replication-developer-documentation.md).</span></span>  
  
## <a name="replication-tutorials"></a><span data-ttu-id="1a6a8-109">複寫教學課程</span><span class="sxs-lookup"><span data-stu-id="1a6a8-109">Replication Tutorials</span></span>  
 [<span data-ttu-id="1a6a8-110">準備用於複寫的伺服器</span><span class="sxs-lookup"><span data-stu-id="1a6a8-110">Preparing the Server for Replication</span></span>](tutorial-preparing-the-server-for-replication.md)  
 <span data-ttu-id="1a6a8-111">了解如何準備伺服器，以便使用最低權限執行複寫。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-111">Learn how to prepare servers so that replication can be run with least privileges.</span></span> <span data-ttu-id="1a6a8-112">您必須先完成本教學課程，才能進行其他複寫教學課程。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-112">You must complete this tutorial before the other replication tutorials.</span></span>  
  
 [<span data-ttu-id="1a6a8-113">在連續連接的伺服器之間複寫資料</span><span class="sxs-lookup"><span data-stu-id="1a6a8-113">Replicating Data Between Continuously Connected Servers</span></span>](tutorial-replicating-data-between-continuously-connected-servers.md)  
 <span data-ttu-id="1a6a8-114">了解如何使用異動複寫，在完全連接的伺服器之間複寫資料。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-114">Learn how to use transactional replication to replicate data between fully connected servers.</span></span>  
  
 [<span data-ttu-id="1a6a8-115">利用行動用戶端複寫資料</span><span class="sxs-lookup"><span data-stu-id="1a6a8-115">Replicating Data with Mobile Clients</span></span>](tutorial-replicating-data-with-mobile-clients.md)  
 <span data-ttu-id="1a6a8-116">了解如何使用合併式複寫，在伺服器與一個或多個只是偶而連接的用戶端之間交換資料。</span><span class="sxs-lookup"><span data-stu-id="1a6a8-116">Learn how to use merge replication to exchange data between a server and one or more clients that are only occasionally connected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6a8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a6a8-117">See Also</span></span>  
 [<span data-ttu-id="1a6a8-118">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="1a6a8-118">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
