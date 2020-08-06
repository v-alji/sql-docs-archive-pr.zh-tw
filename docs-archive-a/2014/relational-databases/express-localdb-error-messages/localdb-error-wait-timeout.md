---
title: LOCALDB_ERROR_WAIT_TIMEOUT |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: e5b55efa-daa1-4c39-aa71-eeb7707ed601
author: stevestein
ms.author: sstein
ms.openlocfilehash: e3668b32fb48a3e12c33dc15224467307c696af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686940"
---
# <a name="localdb_error_wait_timeout"></a><span data-ttu-id="0567a-102">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0567a-102">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>
    
## <a name="details"></a><span data-ttu-id="0567a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0567a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0567a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0567a-104">Product Name</span></span>|<span data-ttu-id="0567a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0567a-105">SQL Server</span></span>|  
|<span data-ttu-id="0567a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0567a-106">Event ID</span></span>|<span data-ttu-id="0567a-107">277</span><span class="sxs-lookup"><span data-stu-id="0567a-107">277</span></span>|  
|<span data-ttu-id="0567a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0567a-108">Event Source</span></span>|<span data-ttu-id="0567a-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="0567a-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="0567a-110">元件</span><span class="sxs-lookup"><span data-stu-id="0567a-110">Component</span></span>|<span data-ttu-id="0567a-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="0567a-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="0567a-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0567a-112">Message Text</span></span>|<span data-ttu-id="0567a-113">本機資料庫執行個體 API 方法內發生逾時。</span><span class="sxs-lookup"><span data-stu-id="0567a-113">Timeout occurred inside the Local Database instance API method.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0567a-114">說明</span><span class="sxs-lookup"><span data-stu-id="0567a-114">Explanation</span></span>  
 <span data-ttu-id="0567a-115">嘗試取得同步處理鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="0567a-115">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0567a-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0567a-116">User Action</span></span>  
 <span data-ttu-id="0567a-117">請再次重試要求的作業。</span><span class="sxs-lookup"><span data-stu-id="0567a-117">Retry the requested operation again.</span></span>  
  
  
