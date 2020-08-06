---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 300f9753b721bc3e0a821a6b77929a9bec09312b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585426"
---
# <a name="localdb_error_instance_already_shared"></a><span data-ttu-id="d6de0-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="d6de0-102">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>
    
## <a name="details"></a><span data-ttu-id="d6de0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d6de0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6de0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d6de0-104">Product Name</span></span>|<span data-ttu-id="d6de0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d6de0-105">SQL Server</span></span>|  
|<span data-ttu-id="d6de0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d6de0-106">Event ID</span></span>|<span data-ttu-id="d6de0-107">284</span><span class="sxs-lookup"><span data-stu-id="d6de0-107">284</span></span>|  
|<span data-ttu-id="d6de0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d6de0-108">Event Source</span></span>|<span data-ttu-id="d6de0-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="d6de0-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="d6de0-110">元件</span><span class="sxs-lookup"><span data-stu-id="d6de0-110">Component</span></span>|<span data-ttu-id="d6de0-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="d6de0-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="d6de0-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d6de0-112">Message Text</span></span>|<span data-ttu-id="d6de0-113">已共用指定的本機資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6de0-113">The specified Local Database Instance is already shared.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d6de0-114">說明</span><span class="sxs-lookup"><span data-stu-id="d6de0-114">Explanation</span></span>  
 <span data-ttu-id="d6de0-115">指定的本機資料庫執行個體已用其他共用名稱共用。</span><span class="sxs-lookup"><span data-stu-id="d6de0-115">The specified Local Database Instance is already shared with a different shared name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d6de0-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d6de0-116">User Action</span></span>  
 <span data-ttu-id="d6de0-117">請先取消共用已共用的執行個體，然後再次使用不同的共用名稱來共用它。</span><span class="sxs-lookup"><span data-stu-id="d6de0-117">Unshare the shared instance before sharing it again with a different shared name.</span></span>  
  
  
