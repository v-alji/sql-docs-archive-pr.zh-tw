---
title: 以 COM 為基礎的自訂解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b28795c1a7d43bcd4e8cb3f18723e05f9e76966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702821"
---
# <a name="com-based-custom-resolvers"></a><span data-ttu-id="d7e51-102">COM-Based Custom Resolvers</span><span class="sxs-lookup"><span data-stu-id="d7e51-102">COM-Based Custom Resolvers</span></span>
  <span data-ttu-id="d7e51-103">自訂解決器比預設解決機制更具有彈性，它們能使用複寫資料實作應用程式要求的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="d7e51-103">Custom resolvers provide more flexibility than the default resolution mechanism, and they can implement business logic required by applications using the replicated data.</span></span> <span data-ttu-id="d7e51-104">以 COM 為基礎的自訂解決器是一個實作 **ICustomResolver** COM 介面、其方法與屬性，以及特別為衝突解決所設計的其他支援介面與類型定義之動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="d7e51-104">A COM-based custom resolver is a dynamic-link library (DLL) that implements the **ICustomResolver** COM interface, its methods and properties, and other supporting interfaces and type definitions designed specifically for conflict resolution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7e51-105">如有可能，建議使用商務邏輯處理常式，而不要使用以 COM 為基礎的自訂解決器。</span><span class="sxs-lookup"><span data-stu-id="d7e51-105">It is recommended to use a business logic handler rather than a COM-based custom resolver if possible.</span></span> <span data-ttu-id="d7e51-106">如需商務邏輯處理常式的詳細資訊，請參閱[合併同步處理期間執行商務邏輯](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="d7e51-106">For more information on business logic handlers, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="d7e51-107">若要建立自訂 COM 解決器，您可以使用 replrec.dll 中所提供的類型程式庫；依預設，此程式庫安裝在 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM。</span><span class="sxs-lookup"><span data-stu-id="d7e51-107">To build a custom COM resolver, you can use the type library that is provided in the replrec.dll; by default, this library is installed at [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
 <span data-ttu-id="d7e51-108">在撰寫自訂 COM 解決器之前，您必須先決定：</span><span class="sxs-lookup"><span data-stu-id="d7e51-108">Before writing a custom COM resolver, you need to decide:</span></span>  
  
-   <span data-ttu-id="d7e51-109">您想解決的資料列變更之類型 (例如更新、插入、刪除)，以及在合併變更的上傳、下載，或兩者兼具期間，是否應叫用解決器。</span><span class="sxs-lookup"><span data-stu-id="d7e51-109">The types of row changes you want to resolve, such as updates, inserts, and deletes, and whether the resolver should be invoked during the upload of merge changes, the download of merge changes, or both.</span></span> <span data-ttu-id="d7e51-110">您可以指定一類變更、所有變更，或者任意組合。</span><span class="sxs-lookup"><span data-stu-id="d7e51-110">You can specify one type of change, all changes, or any combination.</span></span> <span data-ttu-id="d7e51-111">預設的合併衝突解決器可處理自訂解決器未能涵蓋的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="d7e51-111">The default merge conflict resolver handles any conflicts not covered by a custom resolver.</span></span>  
  
-   <span data-ttu-id="d7e51-112">解決衝突時是否要使用資料行追蹤。</span><span class="sxs-lookup"><span data-stu-id="d7e51-112">Whether to use column tracking when resolving the conflict.</span></span> <span data-ttu-id="d7e51-113">若啟用資料行層級追蹤，只有衝突所在的資料行中的資料會加上旗標標示為衝突，否則這些資料便會遭到合併。</span><span class="sxs-lookup"><span data-stu-id="d7e51-113">When column-level tracking is on, only data in those columns where a conflict exists are flagged as a conflict, otherwise the data is merged.</span></span> <span data-ttu-id="d7e51-114">但是，衝突解決的方式與資料列層級追蹤相同：優先權勝利者會覆寫整列資料 (但這些資料可能是來自於「發行者」、「訂閱者」的混合值或一些非來自「發行者」亦非「訂閱者」的變更值)。</span><span class="sxs-lookup"><span data-stu-id="d7e51-114">However, conflicts are resolved in the same way as row-level tracking: the priority winner overwrites the entire row of data (but the data can be a mix of values from the Publisher, Subscribers, or some altered values that were from neither Publisher nor Subscribers).</span></span> <span data-ttu-id="d7e51-115">如需相關資訊，請參閱 [偵測及解決合併式複寫衝突](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="d7e51-115">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
 <span data-ttu-id="d7e51-116">若要實作以 COM 為基礎的自訂 Conflict Resolver，請參閱＜ [針對合併發行項實作自訂衝突解析程式](../implement-a-custom-conflict-resolver-for-a-merge-article.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d7e51-116">To implement a COM-based custom conflict resolver, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
 <span data-ttu-id="d7e51-117">自訂解決器是指定給發行項的，而不是指定給整個發行集的。</span><span class="sxs-lookup"><span data-stu-id="d7e51-117">A custom resolver is specified for an article, not an entire publication.</span></span> <span data-ttu-id="d7e51-118">同一個解決器可以用於多個發行項，但是自訂解決器的邏輯通常為特定資料表所特有。</span><span class="sxs-lookup"><span data-stu-id="d7e51-118">The same resolver can be used with more than one article, but the logic in custom resolvers is often specific to a particular table.</span></span> <span data-ttu-id="d7e51-119">如果在建立解決器之後修改用於發行項的資料表 (例如，重新命名用於衝突解決的資料行)，則自訂解決器可能需要修改及重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d7e51-119">If the table used in the article is modified after the resolver is created (for example, renaming the column name that is used in conflict resolution), the custom resolver might need to be modified and recompiled.</span></span>  
  
 <span data-ttu-id="d7e51-120">若要指定自訂解析程式，請參閱＜ [指定合併發行項解析程式](../publish/specify-a-merge-article-resolver.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d7e51-120">To specify a custom resolver, see [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e51-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7e51-121">See Also</span></span>  
 <span data-ttu-id="d7e51-122">[進階合併式複寫衝突偵測與解決](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="d7e51-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="d7e51-123">Microsoft COM-Based Resolvers</span><span class="sxs-lookup"><span data-stu-id="d7e51-123">Microsoft COM-Based Resolvers</span></span>](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
