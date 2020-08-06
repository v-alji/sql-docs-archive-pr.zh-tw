---
title: 交易 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c693b550e0c1adb8f5910d99c7125c85f41abb8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707646"
---
# <a name="transactions-master-data-services"></a><span data-ttu-id="9c26c-102">交易 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9c26c-102">Transactions (Master Data Services)</span></span>
  <span data-ttu-id="9c26c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，每次對成員採取動作時，就會記錄交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a transaction is recorded each time action is taken on a member.</span></span> <span data-ttu-id="9c26c-104">交易可由所有使用者檢視，並由系統管理員反轉。</span><span class="sxs-lookup"><span data-stu-id="9c26c-104">Transactions can be viewed by all users and reversed by administrators.</span></span> <span data-ttu-id="9c26c-105">交易會顯示日期、時間、採取動作的使用者以及其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9c26c-105">Transactions show the date, time, and user who took the action, along with other details.</span></span> <span data-ttu-id="9c26c-106">使用者可以在交易中加入註解，指出交易發生的原因。</span><span class="sxs-lookup"><span data-stu-id="9c26c-106">Users can add an annotation to a transaction, to indicate why a transaction took place.</span></span>  
  
## <a name="when-transaction-are-recorded"></a><span data-ttu-id="9c26c-107">記錄交易時</span><span class="sxs-lookup"><span data-stu-id="9c26c-107">When Transaction Are Recorded</span></span>  
 <span data-ttu-id="9c26c-108">當成員發生下列情況時，則記錄交易：</span><span class="sxs-lookup"><span data-stu-id="9c26c-108">Transactions are recorded when members:</span></span>  
  
-   <span data-ttu-id="9c26c-109">建立、刪除或重新啟用。</span><span class="sxs-lookup"><span data-stu-id="9c26c-109">Are created, deleted, or reactivated.</span></span>  
  
-   <span data-ttu-id="9c26c-110">屬性值變更。</span><span class="sxs-lookup"><span data-stu-id="9c26c-110">Have attribute values changed.</span></span>  
  
-   <span data-ttu-id="9c26c-111">在階層中移動。</span><span class="sxs-lookup"><span data-stu-id="9c26c-111">Are moved in a hierarchy.</span></span>  
  
 <span data-ttu-id="9c26c-112">當商務規則變更屬性值時，不會記錄交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-112">Transactions are not recorded when business rules change attribute values.</span></span>  
  
## <a name="view-and-manage-transactions"></a><span data-ttu-id="9c26c-113">檢視及管理交易</span><span class="sxs-lookup"><span data-stu-id="9c26c-113">View and Manage Transactions</span></span>  
 <span data-ttu-id="9c26c-114">在 [總管]\*\*\*\* 功能區域中，您可以檢視和註解自己進行的交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-114">In the **Explorer** functional area, you can view and annotate (add comments to) the transactions that you made yourself.</span></span>  
  
 <span data-ttu-id="9c26c-115">在 [版本管理]\*\*\*\* 功能區域中，系統管理員可以檢視其可存取模型當中所有使用者的全數交易，並反轉任何交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-115">In the **Version Management** functional area, administrators can view all transactions for all users for the models they have access to, and reverse any of these transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c26c-116">只要系統管理員的 [版本管理]\*\*\*\* 功能區域未套用唯讀權限層級，即可檢視所有使用者的全數交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-116">Administrators can view all transactions for all users as long as they don't have the read-only permission level applied in the **Version Management** functional area .</span></span> <span data-ttu-id="9c26c-117">例如，如果系統管理員設定了唯讀權限和更新權限等級，系統管理員就無法查看其他使用者的交易，因為唯讀權限的優先順序高於更新權限。</span><span class="sxs-lookup"><span data-stu-id="9c26c-117">For example, if the read-only permission and update permission level is set for the administrator, the administrator will not be able to see other user transactions because the read-only permission will take precedence over the update permission.</span></span>

## <a name="system-settings"></a><span data-ttu-id="9c26c-118">系統設定</span><span class="sxs-lookup"><span data-stu-id="9c26c-118">System Settings</span></span>  
 <span data-ttu-id="9c26c-119">當記錄暫存時， [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有一項設定會影響是否記錄交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-119">There is a setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affects whether or not transactions are recorded when records are staged.</span></span> <span data-ttu-id="9c26c-120">此設定只會影響 SQL Server 2008 R2。</span><span class="sxs-lookup"><span data-stu-id="9c26c-120">This setting affects SQL Server 2008 R2 only.</span></span> <span data-ttu-id="9c26c-121">您可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫的 [系統設定] 資料表中調整這項設定。</span><span class="sxs-lookup"><span data-stu-id="9c26c-121">You can adjust this setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="9c26c-122">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9c26c-122">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
 <span data-ttu-id="9c26c-123">在此版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中匯入資料時，可以指定是否要在起始預存程序時記錄交易。</span><span class="sxs-lookup"><span data-stu-id="9c26c-123">When importing data in this version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify whether or not to log transactions when initiating the stored procedure.</span></span> <span data-ttu-id="9c26c-124">如需詳細資訊，請參閱[暫存預存程序 &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9c26c-124">For more information, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="concurrency"></a><span data-ttu-id="9c26c-125">並行</span><span class="sxs-lookup"><span data-stu-id="9c26c-125">Concurrency</span></span>  
 <span data-ttu-id="9c26c-126">如果在多個「檔案總管」工作階段中同時顯示一個特定的實體值，就可以對相同的值進行同時編輯。</span><span class="sxs-lookup"><span data-stu-id="9c26c-126">If a particular entity value is shown simultaneously in more than one Explorer session, concurrent edits to the same value are possible.</span></span> <span data-ttu-id="9c26c-127">MDS 將不會自動偵測到同時編輯。</span><span class="sxs-lookup"><span data-stu-id="9c26c-127">Concurrent edits will not be detected automatically by MDS.</span></span> <span data-ttu-id="9c26c-128">當多個使用者從多個工作階段 (例如從多部電腦、多個瀏覽器索引標籤或視窗，或多個使用者帳戶) 的網頁瀏覽器中使用 MDS Explorer 時，可能會發生這個情況。</span><span class="sxs-lookup"><span data-stu-id="9c26c-128">This can occur when multiple users use the MDS Explorer in the Web browser from multiple sessions, for example from multiple computers, multiple browser tabs or windows, or multiple user accounts.</span></span>  
  
 <span data-ttu-id="9c26c-129">即使允許異動，多個使用者還是可以更新相同的實體值而不發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c26c-129">More than one user can update the same entity values without error despite transactions being enabled.</span></span> <span data-ttu-id="9c26c-130">通常在時間順序上，對值進行的最後一個編輯，其優先順序最高。</span><span class="sxs-lookup"><span data-stu-id="9c26c-130">Typically the last edit to the value in a sequence of time will take precedence.</span></span> <span data-ttu-id="9c26c-131">重複編輯衝突可以在異動記錄中手動觀察到，並透過管理員手動保留。</span><span class="sxs-lookup"><span data-stu-id="9c26c-131">The duplicate edit conflict can be manually observed in the transaction history and can be reversed manually by the administrator.</span></span> <span data-ttu-id="9c26c-132">交易記錄將會針對 [先前的值]\*\*\*\* 顯示個別的交易，並針對每個工作階段的相關屬性顯示 [新值]\*\*\*\*，但若有多個含相同舊值的 [新值]\*\*\*\* 存在時，不會自動解決衝突。</span><span class="sxs-lookup"><span data-stu-id="9c26c-132">The transaction history will show the individual transactions for the **Prior value** and **New value** for the attribute in question from each session, but will not automatically resolve the conflict when multiple **New Values** exist for the same old value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9c26c-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="9c26c-133">Related Tasks</span></span>  
  
|<span data-ttu-id="9c26c-134">工作描述</span><span class="sxs-lookup"><span data-stu-id="9c26c-134">Task Description</span></span>|<span data-ttu-id="9c26c-135">主題</span><span class="sxs-lookup"><span data-stu-id="9c26c-135">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="9c26c-136">藉由反轉交易來復原一個動作 (僅限系統管理員)。</span><span class="sxs-lookup"><span data-stu-id="9c26c-136">Undo an action by reversing a transaction (administrators only).</span></span>|[<span data-ttu-id="9c26c-137">反轉交易 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9c26c-137">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="9c26c-138">相關內容</span><span class="sxs-lookup"><span data-stu-id="9c26c-138">Related Content</span></span>  
  
-   [<span data-ttu-id="9c26c-139">管理員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9c26c-139">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
-   [<span data-ttu-id="9c26c-140">註解 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9c26c-140">Annotations &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/annotations-master-data-services.md)  
  
  
