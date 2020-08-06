---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585420"
---
# <a name="localdb_error_too_many_shared_instances"></a><span data-ttu-id="c7254-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="c7254-102">LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES</span></span>
    
## <a name="details"></a><span data-ttu-id="c7254-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7254-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7254-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c7254-104">Product Name</span></span>|<span data-ttu-id="c7254-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7254-105">SQL Server</span></span>|  
|<span data-ttu-id="c7254-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c7254-106">Event ID</span></span>|<span data-ttu-id="c7254-107">287</span><span class="sxs-lookup"><span data-stu-id="c7254-107">287</span></span>|  
|<span data-ttu-id="c7254-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c7254-108">Event Source</span></span>|<span data-ttu-id="c7254-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="c7254-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="c7254-110">元件</span><span class="sxs-lookup"><span data-stu-id="c7254-110">Component</span></span>|<span data-ttu-id="c7254-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="c7254-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="c7254-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c7254-112">Message Text</span></span>|<span data-ttu-id="c7254-113">共用的執行個體太多，無法產生唯一的使用者執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="c7254-113">There are too many shared instance and we cannot generate unique User Instance Name.</span></span> <span data-ttu-id="c7254-114">請取消共用部分現有的共用執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7254-114">Unshare some of the existing shared instances.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7254-115">說明</span><span class="sxs-lookup"><span data-stu-id="c7254-115">Explanation</span></span>  
 <span data-ttu-id="c7254-116">共用的執行個體太多，無法產生唯一的使用者執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="c7254-116">There are too many shared instance and we cannot generate unique User Instance Name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7254-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c7254-117">User Action</span></span>  
 <span data-ttu-id="c7254-118">請取消共用一個或多個共用的本機資料庫執行階段執行個體，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c7254-118">Unshare one or more of the shared Local Database Runtime instances and try again.</span></span>  
  
  
