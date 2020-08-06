---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd3bfa1213f0569293991d6bd759619c6e7b596
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707590"
---
# <a name="mssqlserver_21892"></a><span data-ttu-id="aad58-102">MSSQLSERVER_21892</span><span class="sxs-lookup"><span data-stu-id="aad58-102">MSSQLSERVER_21892</span></span>
    
## <a name="details"></a><span data-ttu-id="aad58-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aad58-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aad58-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aad58-104">Product Name</span></span>|<span data-ttu-id="aad58-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aad58-105">SQL Server</span></span>|  
|<span data-ttu-id="aad58-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aad58-106">Event ID</span></span>|<span data-ttu-id="aad58-107">21892</span><span class="sxs-lookup"><span data-stu-id="aad58-107">21892</span></span>|  
|<span data-ttu-id="aad58-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aad58-108">Event Source</span></span>|<span data-ttu-id="aad58-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aad58-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aad58-110">元件</span><span class="sxs-lookup"><span data-stu-id="aad58-110">Component</span></span>|<span data-ttu-id="aad58-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aad58-111">SQLEngine</span></span>|  
|<span data-ttu-id="aad58-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aad58-112">Symbolic Name</span></span>|<span data-ttu-id="aad58-113">SQLErrorNum21892</span><span class="sxs-lookup"><span data-stu-id="aad58-113">SQLErrorNum21892</span></span>|  
|<span data-ttu-id="aad58-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aad58-114">Message Text</span></span>|<span data-ttu-id="aad58-115">無法在與虛擬網路名稱 '%s' 相關聯的可用性群組主要複本中，針對成員複本的伺服器名稱查詢 sys.availability_replicas：錯誤 = %d，錯誤訊息 = %s。</span><span class="sxs-lookup"><span data-stu-id="aad58-115">Unable to query sys.availability_replicas at the availability group primary associated with virtual network name '%s' for the server names of the member replicas: error = %d, error message = %s.',</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aad58-116">說明</span><span class="sxs-lookup"><span data-stu-id="aad58-116">Explanation</span></span>  
 <span data-ttu-id="aad58-117">`sp_validate_replica_hosts_as_publishers` 會查詢與重新導向發行者相關聯之可用性群組的目前主要複本，以便判斷裝載成員複本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="aad58-117">`sp_validate_replica_hosts_as_publishers` queries the current primary of the availability group associated with the redirected publisher, to determine the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that host the member replicas.</span></span>  <span data-ttu-id="aad58-118">當此查詢失敗時，就會傳回錯誤 21892。</span><span class="sxs-lookup"><span data-stu-id="aad58-118">When this query fails, error 21892 is returned.</span></span>  
  
 <span data-ttu-id="aad58-119">`sp_validate_replica_hosts_as_publishers` 通常是在第一次使用暫時連結的伺服器時進行，因此如果發生連接問題，這些問題可能會先與 `sp_validate_replica_hosts_as_publishers` 一起顯示。</span><span class="sxs-lookup"><span data-stu-id="aad58-119">`sp_validate_replica_hosts_as_publishers` is typically on of the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with `sp_validate_replica_hosts_as_publishers`.</span></span> <span data-ttu-id="aad58-120">與 `sp_validate_redirected_publisher` 不同之處在於，`sp_validate_replica_hosts_as_publishers` 所使用的連結伺服器一定會在連接到任何可用性群組複本主機時使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="aad58-120">Unlike `sp_validate_redirected_publisher`, the linked server used by `sp_validate_replica_hosts_as_publishers` always uses the credentials of the caller when connecting to any of the availability group replica hosts.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aad58-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aad58-121">User Action</span></span>  
 <span data-ttu-id="aad58-122">執行此預存程序時，請確定您從所有複本上有效的登入執行。</span><span class="sxs-lookup"><span data-stu-id="aad58-122">When running this stored procedure, made certain that you run from a login that is valid on all of the replicas.</span></span> <span data-ttu-id="aad58-123">此登入需要足夠的授權，才能查詢可用性群組中繼資料資料表，以及查詢發行者資料庫複本中的訂閱中繼資料資料表。</span><span class="sxs-lookup"><span data-stu-id="aad58-123">The login will require sufficient authorization to query availability group metadata tables as well as to query the subscription metadata tables in the publisher database replica.</span></span>  
  
 <span data-ttu-id="aad58-124">請檢查原始的參考錯誤，以便判斷失敗的原因以及適當的更正動作。</span><span class="sxs-lookup"><span data-stu-id="aad58-124">Examine the original referenced error to determine the cause of the failure and appropriate corrective action.</span></span>  
  
  
