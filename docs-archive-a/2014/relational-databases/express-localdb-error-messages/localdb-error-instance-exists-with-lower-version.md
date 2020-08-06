---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa6db2af138bb2aeefb1a922e55db56c4ea821f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710649"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a><span data-ttu-id="2393f-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="2393f-102">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>
    
## <a name="details"></a><span data-ttu-id="2393f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2393f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2393f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2393f-104">Product Name</span></span>|<span data-ttu-id="2393f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2393f-105">SQL Server</span></span>|  
|<span data-ttu-id="2393f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2393f-106">Event ID</span></span>|<span data-ttu-id="2393f-107">258</span><span class="sxs-lookup"><span data-stu-id="2393f-107">258</span></span>|  
|<span data-ttu-id="2393f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2393f-108">Event Source</span></span>|<span data-ttu-id="2393f-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="2393f-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="2393f-110">元件</span><span class="sxs-lookup"><span data-stu-id="2393f-110">Component</span></span>|<span data-ttu-id="2393f-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="2393f-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="2393f-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2393f-112">Message Text</span></span>|<span data-ttu-id="2393f-113">無法以指定的版本建立本機資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="2393f-113">Unable to create the Local Database instance with specified version.</span></span> <span data-ttu-id="2393f-114">已存在相同名稱之執行個體，但其版本較指定的版本舊。</span><span class="sxs-lookup"><span data-stu-id="2393f-114">An instance with the same name already exists, but it has lower version than the specified version.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2393f-115">說明</span><span class="sxs-lookup"><span data-stu-id="2393f-115">Explanation</span></span>  
 <span data-ttu-id="2393f-116">指定的執行個體已經存在，但是其版本低於要求的版本。</span><span class="sxs-lookup"><span data-stu-id="2393f-116">The specified instance already exists but its version is lower than requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2393f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2393f-117">User Action</span></span>  
 <span data-ttu-id="2393f-118">請刪除現有的執行個體，然後再重試作業。</span><span class="sxs-lookup"><span data-stu-id="2393f-118">Delete the existing instance and retry the operation.</span></span>  
  
  
