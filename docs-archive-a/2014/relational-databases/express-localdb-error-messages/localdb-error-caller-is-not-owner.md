---
title: LOCALDB_ERROR_CALLER_IS_NOT_OWNER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: f3303072-2b44-4443-936c-f024b0b2a8c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce4fd6d84929ce7d1338f5fd688d3c24f1e1858a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606347"
---
# <a name="localdb_error_caller_is_not_owner"></a><span data-ttu-id="31c48-102">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31c48-102">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>
    
## <a name="details"></a><span data-ttu-id="31c48-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31c48-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31c48-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="31c48-104">Product Name</span></span>|<span data-ttu-id="31c48-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="31c48-105">SQL Server</span></span>|  
|<span data-ttu-id="31c48-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="31c48-106">Event ID</span></span>|<span data-ttu-id="31c48-107">282</span><span class="sxs-lookup"><span data-stu-id="31c48-107">282</span></span>|  
|<span data-ttu-id="31c48-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="31c48-108">Event Source</span></span>|<span data-ttu-id="31c48-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="31c48-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="31c48-110">元件</span><span class="sxs-lookup"><span data-stu-id="31c48-110">Component</span></span>|<span data-ttu-id="31c48-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="31c48-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="31c48-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="31c48-112">Message Text</span></span>|<span data-ttu-id="31c48-113">API 呼叫端不是本機資料庫執行個體擁有者。</span><span class="sxs-lookup"><span data-stu-id="31c48-113">API caller is not Local Database instance owner.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="31c48-114">說明</span><span class="sxs-lookup"><span data-stu-id="31c48-114">Explanation</span></span>  
 <span data-ttu-id="31c48-115">使用者必須是執行階段擁有者，才能執行要求的作業。</span><span class="sxs-lookup"><span data-stu-id="31c48-115">User needs to be the instance owner to be able to execute the requested operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="31c48-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="31c48-116">User Action</span></span>  
 <span data-ttu-id="31c48-117">請連絡執行階段擁有者請求協助。</span><span class="sxs-lookup"><span data-stu-id="31c48-117">Contact the instance owner for help.</span></span>  
  
  
