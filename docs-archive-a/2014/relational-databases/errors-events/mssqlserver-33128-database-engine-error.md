---
title: MSSQLSERVER_33128 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33128 (Database Engine error)
ms.assetid: 12c1096f-d120-439b-85f3-f794859503c9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 158cc609a18cf3fe7b76708e351b78263cd80a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595059"
---
# <a name="mssqlserver_33128"></a><span data-ttu-id="35e7d-102">MSSQLSERVER_33128</span><span class="sxs-lookup"><span data-stu-id="35e7d-102">MSSQLSERVER_33128</span></span>
    
## <a name="details"></a><span data-ttu-id="35e7d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35e7d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35e7d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35e7d-104">Product Name</span></span>|<span data-ttu-id="35e7d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="35e7d-105">SQL Server</span></span>|  
|<span data-ttu-id="35e7d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35e7d-106">Event ID</span></span>|<span data-ttu-id="35e7d-107">33128</span><span class="sxs-lookup"><span data-stu-id="35e7d-107">33128</span></span>|  
|<span data-ttu-id="35e7d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="35e7d-108">Event Source</span></span>|<span data-ttu-id="35e7d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="35e7d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="35e7d-110">元件</span><span class="sxs-lookup"><span data-stu-id="35e7d-110">Component</span></span>|<span data-ttu-id="35e7d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="35e7d-111">SQLEngine</span></span>|  
|<span data-ttu-id="35e7d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35e7d-112">Symbolic Name</span></span>|<span data-ttu-id="35e7d-113">SEC_DEPRECATED_ALGO</span><span class="sxs-lookup"><span data-stu-id="35e7d-113">SEC_DEPRECATED_ALGO</span></span>|  
|<span data-ttu-id="35e7d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35e7d-114">Message Text</span></span>|<span data-ttu-id="35e7d-115">加密失敗。</span><span class="sxs-lookup"><span data-stu-id="35e7d-115">Encryption failed.</span></span> <span data-ttu-id="35e7d-116">金鑰使用已被取代而不再受支援的演算法 ' %.\* ls'。</span><span class="sxs-lookup"><span data-stu-id="35e7d-116">Key uses deprecated algorithm '%.\*ls' which is no longer supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35e7d-117">說明</span><span class="sxs-lookup"><span data-stu-id="35e7d-117">Explanation</span></span>  
 <span data-ttu-id="35e7d-118">參照 RC4 (或 RC4_128) 加密演算法時，會出現此訊息。</span><span class="sxs-lookup"><span data-stu-id="35e7d-118">This message occurs when referencing the RC4 (or RC4_128) encryption algorithm.</span></span> <span data-ttu-id="35e7d-119">RC4 與 RC4_128 加密演算法提供的保護很弱，已被取代。</span><span class="sxs-lookup"><span data-stu-id="35e7d-119">RC4 and RC4_128 are weak algorithms and are deprecated.</span></span> <span data-ttu-id="35e7d-120">請改用較強的演算法，例如其中一種 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="35e7d-120">Use a stronger algorithm such as one of the AES algorithms instead.</span></span>  
  
 <span data-ttu-id="35e7d-121">當資料庫相容性層級設定為 90 或 100 時，作業成功執行後會引發取代事件，接著只會於信號緩衝區中顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="35e7d-121">When the database compatibility level is 90 or 100, the operation succeeds, the deprecation event is raised, and the message appears only in the ring buffer.</span></span>  
  
 <span data-ttu-id="35e7d-122">當資料庫相容性層級為 110 以上時，取代作業成功後會引發取代事件，接著只會於信號緩衝區中顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="35e7d-122">When the database compatibility level is 110 or higher, decryption operations succeed, the deprecation event is raised, and the message appears only in the ring buffer.</span></span> <span data-ttu-id="35e7d-123">加密作業將會失敗並會引發取代事件，接著使用者會看見此訊息，而信號緩衝區中也會顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="35e7d-123">Encryption operations will fail, the deprecation event is raised, and the message is displayed for the user, and the message appears in the ring buffer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35e7d-124">信號緩衝區是一個內部元件，不會進行完整記錄，也並非供客戶之用。</span><span class="sxs-lookup"><span data-stu-id="35e7d-124">The ring buffer is an internal component which is not fully documented and is not intended to be used by customers.</span></span> <span data-ttu-id="35e7d-125">當您連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶支援時，信號緩衝區中的訊息將提供有用協助。</span><span class="sxs-lookup"><span data-stu-id="35e7d-125">Messages from the ring buffer are useful when contacting [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Support.</span></span> <span data-ttu-id="35e7d-126">若要檢視信號緩衝區，請查詢 sys.dm_os_ring_buffers 動態管理檢視。</span><span class="sxs-lookup"><span data-stu-id="35e7d-126">To view the ring buffer, query the sys.dm_os_ring_buffers dynamic management view.</span></span>  
  
|<span data-ttu-id="35e7d-127">State</span><span class="sxs-lookup"><span data-stu-id="35e7d-127">State</span></span>|<span data-ttu-id="35e7d-128">描述</span><span class="sxs-lookup"><span data-stu-id="35e7d-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35e7d-129">1</span><span class="sxs-lookup"><span data-stu-id="35e7d-129">1</span></span>|<span data-ttu-id="35e7d-130">內建的 encryptbykey() 函式中使用 RC4 金鑰。</span><span class="sxs-lookup"><span data-stu-id="35e7d-130">A RC4 key is used in the built-in encryptbykey() function.</span></span> <span data-ttu-id="35e7d-131">內建函數傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="35e7d-131">Built-in function returns NULL.</span></span> <span data-ttu-id="35e7d-132">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-132">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-133">2</span><span class="sxs-lookup"><span data-stu-id="35e7d-133">2</span></span>|<span data-ttu-id="35e7d-134">內建的 decryptbykey() 函式中使用 RC4 金鑰。</span><span class="sxs-lookup"><span data-stu-id="35e7d-134">A RC4 key is used in by the built-in decryptbykey() function.</span></span> <span data-ttu-id="35e7d-135">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-135">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-136">3</span><span class="sxs-lookup"><span data-stu-id="35e7d-136">3</span></span>|<span data-ttu-id="35e7d-137">已被取代的 RC4 金鑰正由對稱金鑰加密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-137">A deprecated RC4 key is being encrypted by a symmetric key.</span></span> <span data-ttu-id="35e7d-138">使用者可看見，也會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-138">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="35e7d-139">已被取代的 RC4 對稱金鑰不能改變相容性層級為 110。</span><span class="sxs-lookup"><span data-stu-id="35e7d-139">Deprecated RC4 symmetric keys cannot be altered in compatibility level 110.</span></span> <span data-ttu-id="35e7d-140">嘗試使用非 RC4 金鑰進行加密作業。</span><span class="sxs-lookup"><span data-stu-id="35e7d-140">Try to use non-RC4 keys for crypto operations.</span></span> <span data-ttu-id="35e7d-141">請視需要將回溯相容性層級設定為 90 或 100。</span><span class="sxs-lookup"><span data-stu-id="35e7d-141">If necessary, set backward compatibility level to a 90 or 100.</span></span>|  
|<span data-ttu-id="35e7d-142">4</span><span class="sxs-lookup"><span data-stu-id="35e7d-142">4</span></span>|<span data-ttu-id="35e7d-143">非 RC4 金鑰正由已被取代的 RC4 對稱金鑰加密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-143">A non-RC4 key is being encrypted by a deprecated RC4 symmetric key.</span></span> <span data-ttu-id="35e7d-144">使用者可看見，也會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-144">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="35e7d-145">將應用程式修改為使用非 RC4 對稱金鑰，或將回溯相容性層級設定為 90 或 100。</span><span class="sxs-lookup"><span data-stu-id="35e7d-145">Modify the application to use non-RC4 symmetric keys or set backward compatibility level to 90 or 100.</span></span>|  
|<span data-ttu-id="35e7d-146">5</span><span class="sxs-lookup"><span data-stu-id="35e7d-146">5</span></span>|<span data-ttu-id="35e7d-147">已被取代的 RC4 金鑰正由對稱金鑰解密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-147">A deprecated RC4 key is being decrypted by a symmetric key.</span></span> <span data-ttu-id="35e7d-148">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-148">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-149">6</span><span class="sxs-lookup"><span data-stu-id="35e7d-149">6</span></span>|<span data-ttu-id="35e7d-150">非 RC4 金鑰正由 RC4 對稱金鑰解密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-150">A non-RC4 key is being decrypted by an RC4 symmetric key.</span></span> <span data-ttu-id="35e7d-151">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-151">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-152">7</span><span class="sxs-lookup"><span data-stu-id="35e7d-152">7</span></span>|<span data-ttu-id="35e7d-153">RC4 對稱金鑰正由憑證加密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-153">A RC4 symmetric key is being encrypted by the certificate.</span></span> <span data-ttu-id="35e7d-154">使用者可看見，也會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-154">Seen by users and in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-155">8</span><span class="sxs-lookup"><span data-stu-id="35e7d-155">8</span></span>|<span data-ttu-id="35e7d-156">RC4 對稱金鑰正由憑證解密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-156">A RC4 symmetric key is being decrypted by the certificate.</span></span> <span data-ttu-id="35e7d-157">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-157">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="35e7d-158">9</span><span class="sxs-lookup"><span data-stu-id="35e7d-158">9</span></span>|<span data-ttu-id="35e7d-159">RC4 對稱金鑰正由 EKM 金鑰加密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-159">A RC4 symmetric key is being encrypted by the EKM key.</span></span>|  
|<span data-ttu-id="35e7d-160">10</span><span class="sxs-lookup"><span data-stu-id="35e7d-160">10</span></span>|<span data-ttu-id="35e7d-161">RC4 對稱金鑰正由 EKM 金鑰解密中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-161">A RC4 symmetric key is being decrypted by the EKM key.</span></span> <span data-ttu-id="35e7d-162">此訊息僅會顯示於信號緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35e7d-162">This message only appears in the ring buffer.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="35e7d-163">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35e7d-163">User Action</span></span>  
 <span data-ttu-id="35e7d-164">請改用較強的演算法，例如其中一種 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="35e7d-164">Use a stronger algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="35e7d-165">(建議使用)</span><span class="sxs-lookup"><span data-stu-id="35e7d-165">(Recommended)</span></span>  
  
 <span data-ttu-id="35e7d-166">使用 ALTER DATABASE SET COMPATIBILITY_LEVEL 將資料庫相容性層級設定為 100</span><span class="sxs-lookup"><span data-stu-id="35e7d-166">Use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 100.</span></span> <span data-ttu-id="35e7d-167">(不建議使用)。</span><span class="sxs-lookup"><span data-stu-id="35e7d-167">(Not recommended.)</span></span>  
  
  
