---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595062"
---
# <a name="mssqlserver_33028"></a><span data-ttu-id="d772a-102">MSSQLSERVER_33028</span><span class="sxs-lookup"><span data-stu-id="d772a-102">MSSQLSERVER_33028</span></span>
    
## <a name="details"></a><span data-ttu-id="d772a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d772a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d772a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d772a-104">Product Name</span></span>|<span data-ttu-id="d772a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d772a-105">SQL Server</span></span>|  
|<span data-ttu-id="d772a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d772a-106">Event ID</span></span>|<span data-ttu-id="d772a-107">33028</span><span class="sxs-lookup"><span data-stu-id="d772a-107">33028</span></span>|  
|<span data-ttu-id="d772a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d772a-108">Event Source</span></span>|<span data-ttu-id="d772a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d772a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d772a-110">元件</span><span class="sxs-lookup"><span data-stu-id="d772a-110">Component</span></span>|<span data-ttu-id="d772a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d772a-111">SQLEngine</span></span>|  
|<span data-ttu-id="d772a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d772a-112">Symbolic Name</span></span>|<span data-ttu-id="d772a-113">SEC_CRYPTOPROV_CANTOPENSESSION</span><span class="sxs-lookup"><span data-stu-id="d772a-113">SEC_CRYPTOPROV_CANTOPENSESSION</span></span>|  
|<span data-ttu-id="d772a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d772a-114">Message Text</span></span>|<span data-ttu-id="d772a-115">無法為 %S_MSG '%.\*ls' 開啟工作階段。</span><span class="sxs-lookup"><span data-stu-id="d772a-115">Cannot open session for %S_MSG '%.\*ls'.</span></span> <span data-ttu-id="d772a-116">提供者錯誤碼: %d。</span><span class="sxs-lookup"><span data-stu-id="d772a-116">Provider error code: %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d772a-117">說明</span><span class="sxs-lookup"><span data-stu-id="d772a-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d772a-118">無法開啟錯誤訊息中所列的密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d772a-118">was unable to open the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="d772a-119">此密碼編譯提供者提供了所列的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d772a-119">The cryptographic provider supplied the error code listed.</span></span> <span data-ttu-id="d772a-120">如需有關此錯誤的詳細資訊，您可能必須連絡密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d772a-120">You may need to contact your cryptographic provider for more information about the error.</span></span>  
  
|<span data-ttu-id="d772a-121">錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d772a-121">Error code</span></span>|<span data-ttu-id="d772a-122">描述</span><span class="sxs-lookup"><span data-stu-id="d772a-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d772a-123">0</span><span class="sxs-lookup"><span data-stu-id="d772a-123">0</span></span>|<span data-ttu-id="d772a-124">成功。</span><span class="sxs-lookup"><span data-stu-id="d772a-124">Success.</span></span> <span data-ttu-id="d772a-125">沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="d772a-125">No error.</span></span>|  
|<span data-ttu-id="d772a-126">1</span><span class="sxs-lookup"><span data-stu-id="d772a-126">1</span></span>|<span data-ttu-id="d772a-127">失敗。</span><span class="sxs-lookup"><span data-stu-id="d772a-127">Failure.</span></span> <span data-ttu-id="d772a-128">發生未指定或意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d772a-128">An unspecified or unexpected error occurred.</span></span> <span data-ttu-id="d772a-129">沒有其他資訊可用。</span><span class="sxs-lookup"><span data-stu-id="d772a-129">Additional information is not available.</span></span>|  
|<span data-ttu-id="d772a-130">2</span><span class="sxs-lookup"><span data-stu-id="d772a-130">2</span></span>|<span data-ttu-id="d772a-131">緩衝區不足。</span><span class="sxs-lookup"><span data-stu-id="d772a-131">Insufficient Buffer.</span></span> <span data-ttu-id="d772a-132">無法針對密碼編譯提供者配置空間。</span><span class="sxs-lookup"><span data-stu-id="d772a-132">Space could not be allocated for the cryptographic provider.</span></span>|  
|<span data-ttu-id="d772a-133">3</span><span class="sxs-lookup"><span data-stu-id="d772a-133">3</span></span>|<span data-ttu-id="d772a-134">不支援。</span><span class="sxs-lookup"><span data-stu-id="d772a-134">Not Supported.</span></span> <span data-ttu-id="d772a-135">這個版本不支援此密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d772a-135">The cryptographic provider is not supported by this release.</span></span> <span data-ttu-id="d772a-136">請選取另一個密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d772a-136">Select another cryptographic provider.</span></span>|  
|<span data-ttu-id="d772a-137">4</span><span class="sxs-lookup"><span data-stu-id="d772a-137">4</span></span>|<span data-ttu-id="d772a-138">找不到。</span><span class="sxs-lookup"><span data-stu-id="d772a-138">Not Found.</span></span> <span data-ttu-id="d772a-139">指定的密碼編譯提供者不存在，或者您沒有存取這些檔案的授權。</span><span class="sxs-lookup"><span data-stu-id="d772a-139">The specified cryptographic provider is not present or you do not have authorization to access the files.</span></span>|  
|<span data-ttu-id="d772a-140">5</span><span class="sxs-lookup"><span data-stu-id="d772a-140">5</span></span>|<span data-ttu-id="d772a-141">授權失敗。</span><span class="sxs-lookup"><span data-stu-id="d772a-141">Authorization Failure.</span></span> <span data-ttu-id="d772a-142">可能是因為在建立認證時提供了不正確的密碼或使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d772a-142">Can result from providing an incorrect password or username when creating the credential.</span></span> <span data-ttu-id="d772a-143">如果此認證不存在，也可能會造成這種情況。</span><span class="sxs-lookup"><span data-stu-id="d772a-143">Can result if the credential does not exist.</span></span>|  
|<span data-ttu-id="d772a-144">6</span><span class="sxs-lookup"><span data-stu-id="d772a-144">6</span></span>|<span data-ttu-id="d772a-145">無效的引數。</span><span class="sxs-lookup"><span data-stu-id="d772a-145">Invalid Argument.</span></span> <span data-ttu-id="d772a-146">將無效的引數傳遞給密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d772a-146">An invalid argument was passed to the cryptographic provider.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="d772a-147">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d772a-147">User Action</span></span>  
 <span data-ttu-id="d772a-148">解決此錯誤，或者連絡密碼編譯提供者以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d772a-148">Resolve the error, or contact the cryptographic provider for more information.</span></span>  
  
  
