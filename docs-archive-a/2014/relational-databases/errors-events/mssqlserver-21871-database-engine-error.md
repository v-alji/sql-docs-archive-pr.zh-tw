---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f26211da21829a0a898dfb36ff9fefd453c7ad44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699652"
---
# <a name="mssqlserver_21871"></a><span data-ttu-id="62a0f-102">MSSQLSERVER_21871</span><span class="sxs-lookup"><span data-stu-id="62a0f-102">MSSQLSERVER_21871</span></span>
    
## <a name="details"></a><span data-ttu-id="62a0f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62a0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62a0f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="62a0f-104">Product Name</span></span>|<span data-ttu-id="62a0f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="62a0f-105">SQL Server</span></span>|  
|<span data-ttu-id="62a0f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="62a0f-106">Event ID</span></span>|<span data-ttu-id="62a0f-107">21871</span><span class="sxs-lookup"><span data-stu-id="62a0f-107">21871</span></span>|  
|<span data-ttu-id="62a0f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="62a0f-108">Event Source</span></span>|<span data-ttu-id="62a0f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="62a0f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="62a0f-110">元件</span><span class="sxs-lookup"><span data-stu-id="62a0f-110">Component</span></span>|<span data-ttu-id="62a0f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="62a0f-111">SQLEngine</span></span>|  
|<span data-ttu-id="62a0f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="62a0f-112">Symbolic Name</span></span>|<span data-ttu-id="62a0f-113">SQLErrorNum21871</span><span class="sxs-lookup"><span data-stu-id="62a0f-113">SQLErrorNum21871</span></span>|  
|<span data-ttu-id="62a0f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="62a0f-114">Message Text</span></span>|<span data-ttu-id="62a0f-115">尚未重新導向資料庫 %s 的發行者 %s。</span><span class="sxs-lookup"><span data-stu-id="62a0f-115">Publisher %s of database %s has not been redirected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62a0f-116">說明</span><span class="sxs-lookup"><span data-stu-id="62a0f-116">Explanation</span></span>  
 <span data-ttu-id="62a0f-117">`sp_validate_replica_hosts_as_publishers` 會檢查散發資料庫中的 MSredirected_publishers 資料表是否存在已識別發行者和發行者資料庫的項目。</span><span class="sxs-lookup"><span data-stu-id="62a0f-117">`sp_validate_replica_hosts_as_publishers` checks the table MSredirected_publishers in the distribution database for an entry for the identified publisher and publisher database.</span></span>  <span data-ttu-id="62a0f-118">找不到任何項目時，`sp_validate_replica_hosts_as_publishers` 就會傳回錯誤 21871。</span><span class="sxs-lookup"><span data-stu-id="62a0f-118">`sp_validate_replica_hosts_as_publishers` returns error 21871 when no entry is found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62a0f-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="62a0f-119">User Action</span></span>  
 <span data-ttu-id="62a0f-120">`sp_validate_replica_hosts_as_publishers` 只與重新導向的發行者有關。</span><span class="sxs-lookup"><span data-stu-id="62a0f-120">`sp_validate_replica_hosts_as_publishers` is only relevant for redirected publishers.</span></span> <span data-ttu-id="62a0f-121">如果發行者資料庫是可用性群組的成員，請使用 `sp_redirect_publisher` 預存程序，讓發行者和發行者資料庫與可用性群組的可用性群組接聽程式名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="62a0f-121">If the publisher database is a member of an availability group, use the stored procedure `sp_redirect_publisher` to associate the publisher and publisher database with the Availability Group Listener Name of the availability group.</span></span>  
  
  
