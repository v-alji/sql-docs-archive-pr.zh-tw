---
title: 已取代資料庫維護計畫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584988"
---
# <a name="database-maintenance-plans-superseded"></a><span data-ttu-id="7c144-102">已取代資料庫維護計畫</span><span class="sxs-lookup"><span data-stu-id="7c144-102">Database maintenance plans superseded</span></span>
    
## <a name="component"></a><span data-ttu-id="7c144-103">元件</span><span class="sxs-lookup"><span data-stu-id="7c144-103">Component</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="7c144-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理程式</span><span class="sxs-lookup"><span data-stu-id="7c144-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c144-105">描述</span><span class="sxs-lookup"><span data-stu-id="7c144-105">Description</span></span>  
 <span data-ttu-id="7c144-106">現有的資料庫維護計劃已經升級，而且仍會繼續運作。</span><span class="sxs-lookup"><span data-stu-id="7c144-106">Existing database maintenance plans are upgraded and continue to work.</span></span> <span data-ttu-id="7c144-107">但是，您將無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來建立新的資料庫維護計劃。</span><span class="sxs-lookup"><span data-stu-id="7c144-107">However, you will not be able to create new database maintenance plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7c144-108">若要在 [物件總管] 中檢視維護計畫，請展開 [管理]，然後再展開 [舊版]。</span><span class="sxs-lookup"><span data-stu-id="7c144-108">To view the maintenance plans in Object Explorer, expand Management, and then expand Legacy.</span></span> <span data-ttu-id="7c144-109">您可以從任何資料庫維護計畫的內容功能表中選取 [**遷移**]，將現有的資料庫維護計畫遷移至新的格式。</span><span class="sxs-lookup"><span data-stu-id="7c144-109">You can migrate existing database maintenance plans to the new format by selecting **Migrate** from the context menu for any database maintenance plan.</span></span> <span data-ttu-id="7c144-110">因為新維護計畫功能並非直接取代資料庫維護計畫，所以移轉後，某些功能可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="7c144-110">Because the new maintenance plan feature is not a direct replacement of database maintenance plans, some functionality might be lost after migration.</span></span> <span data-ttu-id="7c144-111">移轉資料庫維護計畫並不會刪除舊計畫，所以您可以測試維護計畫的功能後，再移除舊計畫。</span><span class="sxs-lookup"><span data-stu-id="7c144-111">Migrating a database maintenance plan does not delete the old plan, so you can test its functionality as a maintenance plan before removing the old plan.</span></span>  
  
 <span data-ttu-id="7c144-112">資料庫維護計畫不再支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="7c144-112">The following features are no longer supported within database maintenance plans:</span></span>  
  
-   <span data-ttu-id="7c144-113">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="7c144-113">Log shipping</span></span>  
  
-   <span data-ttu-id="7c144-114">[**資料庫完整性檢查**] 工作的 [**嘗試修復任何次要問題**] 選項</span><span class="sxs-lookup"><span data-stu-id="7c144-114">The **Attempt to repair any minor problems** option of the **Database Integrity Check** task</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="7c144-115">更正動作</span><span class="sxs-lookup"><span data-stu-id="7c144-115">Corrective Action</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7c144-116">禁止在資料庫維護計劃中包含記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="7c144-116">prevents log shipping from being included in a database maintenance plan.</span></span> <span data-ttu-id="7c144-117">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜記錄傳送＞。</span><span class="sxs-lookup"><span data-stu-id="7c144-117">For more information, see "Log Shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
