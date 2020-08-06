---
title: Microsoft 複寫互動式衝突解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8cbd2231ab1ab357321f9887bced986e182e608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709205"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a><span data-ttu-id="16b81-102">Microsoft Replication Interactive Conflict Resolver</span><span class="sxs-lookup"><span data-stu-id="16b81-102">Microsoft Replication Interactive Conflict Resolver</span></span>
  <span data-ttu-id="16b81-103">Interactive Conflict Resolver 可用於使用 Windows Synchronization Manager 同步處理的合併訂閱。</span><span class="sxs-lookup"><span data-stu-id="16b81-103">The Interactive Conflict Resolver can be used for merge subscriptions that are synchronized using Windows Synchronization Manager.</span></span> <span data-ttu-id="16b81-104">它可以讓您針對資料衝突，進行檢視、比較、編輯以及選取結果。</span><span class="sxs-lookup"><span data-stu-id="16b81-104">It allows you to view, compare, edit, and select the outcome for data conflicts.</span></span> <span data-ttu-id="16b81-105">複寫還包含衝突檢視器，它可以讓您在認可衝突結果之後，還能夠進行檢視及修改。</span><span class="sxs-lookup"><span data-stu-id="16b81-105">Replication also includes the Conflict Viewer, which allows you to view and modify conflict outcomes after they have been committed.</span></span> <span data-ttu-id="16b81-106">Interactive Conflict Resolver 可以讓您在同步處理期間選取結果。</span><span class="sxs-lookup"><span data-stu-id="16b81-106">The Interactive Conflict Resolver allows you to select the outcome during synchronization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16b81-107">「互動解析程式」中不會顯示涉及邏輯記錄的衝突。</span><span class="sxs-lookup"><span data-stu-id="16b81-107">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="16b81-108">若要檢視這些衝突的相關資訊，請使用複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="16b81-108">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="16b81-109">如需詳細資訊，請參閱[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="16b81-109">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="16b81-110">選項。</span><span class="sxs-lookup"><span data-stu-id="16b81-110">Options</span></span>  
 <span data-ttu-id="16b81-111">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="16b81-111">**Column name**</span></span>  
 <span data-ttu-id="16b81-112">資料表中所有資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="16b81-112">The name of all columns in the table.</span></span> <span data-ttu-id="16b81-113">一或多個資料行可能有衝突的資料。</span><span class="sxs-lookup"><span data-stu-id="16b81-113">One or more columns might have conflicting data.</span></span> <span data-ttu-id="16b81-114">無論是哪些資料行發生衝突，整個成功的資料列會覆寫整個失敗的資料列。</span><span class="sxs-lookup"><span data-stu-id="16b81-114">Regardless of which columns conflict, the entire winning row will overwrite the entire losing row.</span></span>  
  
 <span data-ttu-id="16b81-115">**建議的解決方案**</span><span class="sxs-lookup"><span data-stu-id="16b81-115">**Suggested Resolution**</span></span>  
 <span data-ttu-id="16b81-116">Conflict Resolver 針對發行項所提供的建議解決方案。</span><span class="sxs-lookup"><span data-stu-id="16b81-116">The suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="16b81-117">**發行者**</span><span class="sxs-lookup"><span data-stu-id="16b81-117">**Publisher**</span></span>  
 <span data-ttu-id="16b81-118">在發行者端的資料值。</span><span class="sxs-lookup"><span data-stu-id="16b81-118">The data value at the Publisher.</span></span>  
  
 <span data-ttu-id="16b81-119">**訂閱者**</span><span class="sxs-lookup"><span data-stu-id="16b81-119">**Subscriber**</span></span>  
 <span data-ttu-id="16b81-120">在訂閱者端的資料值。</span><span class="sxs-lookup"><span data-stu-id="16b81-120">The data value at the Subscriber.</span></span>  
  
 <span data-ttu-id="16b81-121">**接受建議**、 **接受發行者**，以及 **接受訂閱者**</span><span class="sxs-lookup"><span data-stu-id="16b81-121">**Accept Suggested**, **Accept Publisher**, and **Accept Subscriber**</span></span>  
 <span data-ttu-id="16b81-122">按一下即可接受會套用在發行者端或訂閱者端的資料列 (視何者於衝突中失敗而定)。</span><span class="sxs-lookup"><span data-stu-id="16b81-122">Click to accept the row that will be applied at either the Publisher or the Subscriber, depending on which one lost the conflict.</span></span> <span data-ttu-id="16b81-123">如果發行者在衝突中失敗了，其他所有訂閱者在下次與發行者同步處理時，就會接收到成功的資料列。</span><span class="sxs-lookup"><span data-stu-id="16b81-123">If the Publisher lost the conflict, all other Subscribers will receive the winning row the next time they synchronize with the Publisher.</span></span>  
  
 <span data-ttu-id="16b81-124">**自動解決其餘衝突**</span><span class="sxs-lookup"><span data-stu-id="16b81-124">**Resolve remaining conflicts automatically**</span></span>  
 <span data-ttu-id="16b81-125">使用 Conflict Resolver 針對發行項所提供的建議解決方案，來解決其餘所有的衝突。</span><span class="sxs-lookup"><span data-stu-id="16b81-125">Resolve all remaining conflicts using the suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="16b81-126">**記錄衝突的詳細資料以供日後參考。**</span><span class="sxs-lookup"><span data-stu-id="16b81-126">**Log the details of the conflict for later reference**</span></span>  
 <span data-ttu-id="16b81-127">記錄系統資料表中衝突的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="16b81-127">Logs the details of the conflict in system tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b81-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16b81-128">See Also</span></span>  
 <span data-ttu-id="16b81-129">[互動式衝突解決方法](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="16b81-129">[Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span></span>  
 <span data-ttu-id="16b81-130">[檢視並解決合併式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="16b81-130">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 <span data-ttu-id="16b81-131">[使用 Windows Synchronization Manager 同步處理訂閱 &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span><span class="sxs-lookup"><span data-stu-id="16b81-131">[Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span></span>  
 [<span data-ttu-id="16b81-132">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="16b81-132">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
