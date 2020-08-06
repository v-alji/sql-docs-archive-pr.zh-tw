---
title: 互動式衝突解決方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57d0de17c4d958a1b842748810ba24717e6866e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584459"
---
# <a name="interactive-conflict-resolution"></a><span data-ttu-id="77f9c-102">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="77f9c-102">Interactive Conflict Resolution</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="77f9c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫提供互動式解決器，可讓您在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同步處理管理員中於需要同步處理期間手動解決衝突。</span><span class="sxs-lookup"><span data-stu-id="77f9c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="77f9c-104">「互動解析程式」是圖形介面，會在執行時期啟動並顯示各衝突資料列的資料，以及提供檢視及編輯衝突資料的選項，然後個別解決每項衝突。</span><span class="sxs-lookup"><span data-stu-id="77f9c-104">Activated at run time, the Interactive Resolver is a graphical interface that displays data for each conflicting row, and provides options for viewing and editing the conflict data, and resolving each conflict individually.</span></span>  
  
 <span data-ttu-id="77f9c-105">「互動解析程式」與「衝突檢視器」相類似。</span><span class="sxs-lookup"><span data-stu-id="77f9c-105">The Interactive Resolver resembles the Conflict Viewer.</span></span> <span data-ttu-id="77f9c-106">「衝突檢視器」是顯示合併同步之後已解決的衝突結果，而「互動解析程式」則顯示解決之前的每個衝突，並在合併同步期間讓您決定每個衝突的結果。</span><span class="sxs-lookup"><span data-stu-id="77f9c-106">However, the Conflict Viewer displays the results of conflicts that are already resolved after merge synchronization, and the Interactive Resolver displays each conflict prior to resolution, allowing you to determine the outcome of each conflict during merge synchronization.</span></span> <span data-ttu-id="77f9c-107">在衝突發生時應有人監視「互動解析程式」。</span><span class="sxs-lookup"><span data-stu-id="77f9c-107">Someone should be available to monitor the Interactive Resolver when a conflict occurs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77f9c-108">「互動式解決」需要 Windows Synchronization Manager。</span><span class="sxs-lookup"><span data-stu-id="77f9c-108">Interactive Resolution requires Windows Synchronization Manager.</span></span> <span data-ttu-id="77f9c-109">如果是在 Windows Synchronization Manager 之外執行同步處理 (如 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或複寫監視器中已排程的同步處理或視需要同步處理)，則不需要使用者的介入，就會根據為發行項指定的解決器自動解決衝突。</span><span class="sxs-lookup"><span data-stu-id="77f9c-109">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span> <span data-ttu-id="77f9c-110">「互動解析程式」中不會顯示涉及邏輯記錄的衝突。</span><span class="sxs-lookup"><span data-stu-id="77f9c-110">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="77f9c-111">若要檢視這些衝突的相關資訊，請使用複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="77f9c-111">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="77f9c-112">如需詳細資訊，請參閱[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="77f9c-112">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a><span data-ttu-id="77f9c-113">發行項解析程式與互動解析程式</span><span class="sxs-lookup"><span data-stu-id="77f9c-113">Article Resolvers and the Interactive Resolver</span></span>  
 <span data-ttu-id="77f9c-114">衝突解析程式 (預設解析程式、商務邏輯處理常式或自訂解析程式) 會在發行集建立時指派給特定的發行項，並利用一組規則來決定衝突資料列資料輸入時應使用那一組資料。</span><span class="sxs-lookup"><span data-stu-id="77f9c-114">Conflict resolvers (either the default resolver, a business logic handler, or a custom resolver) are assigned to specific articles when a publication is created, and use a set of rules to determine which set of data should be used when conflicting row data is entered.</span></span> <span data-ttu-id="77f9c-115">「互動解析程式」並不是一個具有可決定衝突中成功者與失敗者的獨立衝突解析程式，它只是一個搭配預設與自訂解析程式使用的工具。</span><span class="sxs-lookup"><span data-stu-id="77f9c-115">The Interactive Resolver is not a separate conflict resolver with rules for determining conflict winners and losers, but a tool used in conjunction with default and custom resolvers.</span></span> <span data-ttu-id="77f9c-116">發行項解析程式仍會決定成功與失敗的資料列，但「互動解析程式」可讓使用者介入以接受、拒絕或修改結果。</span><span class="sxs-lookup"><span data-stu-id="77f9c-116">The article resolver still determines the winning and losing row, but the Interactive Resolver allows user intervention to accept, reject, or modify the results.</span></span>  
  
 <span data-ttu-id="77f9c-117">若要使用「互動解析程式」，必須為每個發行項以及需要它的訂閱啟用互動式解決。</span><span class="sxs-lookup"><span data-stu-id="77f9c-117">To use the Interactive Resolver, interactive resolution must be enabled for each article and subscription that requires it.</span></span> <span data-ttu-id="77f9c-118">為一個或多個發行項和訂閱啟用「互動解析程式」之後，便會在合併同步處理期間偵測到衝突時使用它。</span><span class="sxs-lookup"><span data-stu-id="77f9c-118">After it is enabled for one or more articles and subscriptions, the Interactive Resolver is used when a conflict is detected during merge synchronization.</span></span>  
  
 <span data-ttu-id="77f9c-119">若要使用互動解析程式，請參閱[指定合併發行項的互動式衝突解決方法](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution)和[使用 Windows Synchronization Manager 同步處理訂閱 &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="77f9c-119">To use the Interactive Resolver, see [Specify Interactive Conflict Resolution for Merge Articles](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) and [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f9c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f9c-120">See Also</span></span>  
 [<span data-ttu-id="77f9c-121">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="77f9c-121">Advanced Merge Replication Conflict Detection and Resolution</span></span>](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
