---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92479d7727ac2300d6a60d02492667d99a69b022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598438"
---
# <a name="mssqlserver_21893"></a><span data-ttu-id="74ad0-102">MSSQLSERVER_21893</span><span class="sxs-lookup"><span data-stu-id="74ad0-102">MSSQLSERVER_21893</span></span>
    
## <a name="details"></a><span data-ttu-id="74ad0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="74ad0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74ad0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="74ad0-104">Product Name</span></span>|<span data-ttu-id="74ad0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="74ad0-105">SQL Server</span></span>|  
|<span data-ttu-id="74ad0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="74ad0-106">Event ID</span></span>|<span data-ttu-id="74ad0-107">21893</span><span class="sxs-lookup"><span data-stu-id="74ad0-107">21893</span></span>|  
|<span data-ttu-id="74ad0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="74ad0-108">Event Source</span></span>|<span data-ttu-id="74ad0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="74ad0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="74ad0-110">元件</span><span class="sxs-lookup"><span data-stu-id="74ad0-110">Component</span></span>|<span data-ttu-id="74ad0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="74ad0-111">SQLEngine</span></span>|  
|<span data-ttu-id="74ad0-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="74ad0-112">Symbolic Name</span></span>|<span data-ttu-id="74ad0-113">SQLErrorNum21893</span><span class="sxs-lookup"><span data-stu-id="74ad0-113">SQLErrorNum21893</span></span>|  
|<span data-ttu-id="74ad0-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="74ad0-114">Message Text</span></span>|<span data-ttu-id="74ad0-115">原始發行者 '%s' 的訂閱者 ( %s ) 並未在重新導向的發行者 '%s' 上顯示為遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="74ad0-115">The subscribers ( %s ) of original publisher '%s' do not appear as remote servers at redirected publisher '%s'.</span></span> <span data-ttu-id="74ad0-116">`sp_addlinkedserver`在重新導向的發行者上執行，將這些訂閱者新增為遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="74ad0-116">Run `sp_addlinkedserver` at the redirected publisher to add these subscribers as remote servers .</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74ad0-117">說明</span><span class="sxs-lookup"><span data-stu-id="74ad0-117">Explanation</span></span>  
 <span data-ttu-id="74ad0-118">`sp_validate_redirected_publisher` 會使用位於遠端伺服器之發行者資料庫的訂閱中繼資料資料表來識別其相關聯的訂閱者，並且確認訂閱者的 master.dbo.sysservers 中是否存在相關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="74ad0-118">`sp_validate_redirected_publisher` uses the subscription metadata tables of the publisher database at the remote server to identify its associated subscribers and verifies that there are associated entries in master.dbo.sysservers for the subscribers.</span></span> <span data-ttu-id="74ad0-119">如果任何識別的訂閱者不存在，就會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="74ad0-119">This error is returned if any of the identified subscribers are not present.</span></span>  
  
 <span data-ttu-id="74ad0-120">此錯誤不會被視為嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="74ad0-120">This error is not considered a fatal error.</span></span> <span data-ttu-id="74ad0-121">發生此錯誤的代理程式會將錯誤記錄成參考用訊息但不會終止，因為新的發行者沒有適當的訂閱者項目對於複寫所造成的影響很有限。</span><span class="sxs-lookup"><span data-stu-id="74ad0-121">Agents encountering this error will log the error as informational but will not terminate, since a failure to have appropriate subscriber entries at the new publisher has limited impact on replication.</span></span> <span data-ttu-id="74ad0-122">如果 sysservers 中沒有適當的訂閱者項目，透過 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行的某些訂閱管理活動可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="74ad0-122">Without an appropriate entry for a subscriber in sysservers, some subscription management activities may fail when executed through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="74ad0-123">不過，只要明確執行管理預存程序，就可以成功執行這些相同的活動。</span><span class="sxs-lookup"><span data-stu-id="74ad0-123">However, these same activities can be successfully performed by executing the management stored procedures explicitly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74ad0-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="74ad0-124">User Action</span></span>  
 <span data-ttu-id="74ad0-125">請在每個識別訂閱者的重新導向發行者上執行 `sp_addlinkedserver`，以便將它們加入做為遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="74ad0-125">Run `sp_addlinkedserver` at the redirected publisher for each of the identified subscribers to add them as remote servers.</span></span> <span data-ttu-id="74ad0-126">然後，請執行 `sp_serveroption` 以設定伺服器的訂閱者位元。</span><span class="sxs-lookup"><span data-stu-id="74ad0-126">Then, run `sp_serveroption` to set the subscriber bit for the server.</span></span>  
  
  
