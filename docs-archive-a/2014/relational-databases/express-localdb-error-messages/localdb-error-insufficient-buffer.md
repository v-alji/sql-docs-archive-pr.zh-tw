---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 934683cfca1a9a9c0596071824c21a0045e6ebab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606332"
---
# <a name="localdb_error_insufficient_buffer"></a><span data-ttu-id="1381d-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1381d-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>
    
## <a name="details"></a><span data-ttu-id="1381d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1381d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1381d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1381d-104">Product Name</span></span>|<span data-ttu-id="1381d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1381d-105">SQL Server</span></span>|  
|<span data-ttu-id="1381d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1381d-106">Event ID</span></span>|<span data-ttu-id="1381d-107">276</span><span class="sxs-lookup"><span data-stu-id="1381d-107">276</span></span>|  
|<span data-ttu-id="1381d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1381d-108">Event Source</span></span>|<span data-ttu-id="1381d-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="1381d-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="1381d-110">元件</span><span class="sxs-lookup"><span data-stu-id="1381d-110">Component</span></span>|<span data-ttu-id="1381d-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="1381d-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="1381d-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1381d-112">Message Text</span></span>|<span data-ttu-id="1381d-113">傳遞至本機資料庫執行個體 API 方法的緩衝區之大小不足。</span><span class="sxs-lookup"><span data-stu-id="1381d-113">The buffer passed to the Local Database instance API method has insufficient size.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1381d-114">說明</span><span class="sxs-lookup"><span data-stu-id="1381d-114">Explanation</span></span>  
 <span data-ttu-id="1381d-115">輸入緩衝區太短，且未要求截斷。</span><span class="sxs-lookup"><span data-stu-id="1381d-115">The input buffer is too short, and truncation was not requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1381d-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1381d-116">User Action</span></span>  
 <span data-ttu-id="1381d-117">請提供指定大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1381d-117">Provide a buffer of the specified size.</span></span>  
  
  
