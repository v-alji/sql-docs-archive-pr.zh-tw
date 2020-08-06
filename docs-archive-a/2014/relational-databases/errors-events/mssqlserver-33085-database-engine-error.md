---
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d774ab115c2d0ddbbd7b35c7e32db17e39fcb2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595060"
---
# <a name="mssqlserver_33085"></a><span data-ttu-id="eb532-102">MSSQLSERVER_33085</span><span class="sxs-lookup"><span data-stu-id="eb532-102">MSSQLSERVER_33085</span></span>
    
## <a name="details"></a><span data-ttu-id="eb532-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eb532-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb532-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="eb532-104">Product Name</span></span>|<span data-ttu-id="eb532-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="eb532-105">SQL Server</span></span>|  
|<span data-ttu-id="eb532-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="eb532-106">Event ID</span></span>|<span data-ttu-id="eb532-107">33085</span><span class="sxs-lookup"><span data-stu-id="eb532-107">33085</span></span>|  
|<span data-ttu-id="eb532-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="eb532-108">Event Source</span></span>|<span data-ttu-id="eb532-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="eb532-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="eb532-110">元件</span><span class="sxs-lookup"><span data-stu-id="eb532-110">Component</span></span>|<span data-ttu-id="eb532-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="eb532-111">SQLEngine</span></span>|  
|<span data-ttu-id="eb532-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="eb532-112">Symbolic Name</span></span>|<span data-ttu-id="eb532-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="eb532-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span></span>|  
|<span data-ttu-id="eb532-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="eb532-114">Message Text</span></span>|<span data-ttu-id="eb532-115">在密碼編譯提供者程式庫 '%.\*ls' 中找不到一個或多個方法。</span><span class="sxs-lookup"><span data-stu-id="eb532-115">One or more methods cannot be found in cryptographic provider library '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eb532-116">說明</span><span class="sxs-lookup"><span data-stu-id="eb532-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eb532-117">無法使用錯誤訊息中所列的密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="eb532-117">was unable to use the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="eb532-118">此密碼編譯提供者不支援所需的方法。</span><span class="sxs-lookup"><span data-stu-id="eb532-118">The cryptographic provider did not support a required method.</span></span> <span data-ttu-id="eb532-119">錯誤的狀態表示找不到哪一個方法。</span><span class="sxs-lookup"><span data-stu-id="eb532-119">The state of the error indicates which method was not found.</span></span>  
  
|<span data-ttu-id="eb532-120">State</span><span class="sxs-lookup"><span data-stu-id="eb532-120">State</span></span>|<span data-ttu-id="eb532-121">描述</span><span class="sxs-lookup"><span data-stu-id="eb532-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb532-122">1</span><span class="sxs-lookup"><span data-stu-id="eb532-122">1</span></span>|<span data-ttu-id="eb532-123">SqlCryptInitializeProvider</span><span class="sxs-lookup"><span data-stu-id="eb532-123">SqlCryptInitializeProvider</span></span>|  
|<span data-ttu-id="eb532-124">2</span><span class="sxs-lookup"><span data-stu-id="eb532-124">2</span></span>|<span data-ttu-id="eb532-125">SqlCryptFreeProvider</span><span class="sxs-lookup"><span data-stu-id="eb532-125">SqlCryptFreeProvider</span></span>|  
|<span data-ttu-id="eb532-126">3</span><span class="sxs-lookup"><span data-stu-id="eb532-126">3</span></span>|<span data-ttu-id="eb532-127">SqlCryptOpenSession</span><span class="sxs-lookup"><span data-stu-id="eb532-127">SqlCryptOpenSession</span></span>|  
|<span data-ttu-id="eb532-128">4</span><span class="sxs-lookup"><span data-stu-id="eb532-128">4</span></span>|<span data-ttu-id="eb532-129">SqlCryptCloseSession</span><span class="sxs-lookup"><span data-stu-id="eb532-129">SqlCryptCloseSession</span></span>|  
|<span data-ttu-id="eb532-130">5</span><span class="sxs-lookup"><span data-stu-id="eb532-130">5</span></span>|<span data-ttu-id="eb532-131">SqlCryptGetProviderInfo</span><span class="sxs-lookup"><span data-stu-id="eb532-131">SqlCryptGetProviderInfo</span></span>|  
|<span data-ttu-id="eb532-132">6</span><span class="sxs-lookup"><span data-stu-id="eb532-132">6</span></span>|<span data-ttu-id="eb532-133">SqlCryptGetNextAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="eb532-133">SqlCryptGetNextAlgorithmId</span></span>|  
|<span data-ttu-id="eb532-134">7</span><span class="sxs-lookup"><span data-stu-id="eb532-134">7</span></span>|<span data-ttu-id="eb532-135">SqlCryptGetAlgorithmInfo</span><span class="sxs-lookup"><span data-stu-id="eb532-135">SqlCryptGetAlgorithmInfo</span></span>|  
|<span data-ttu-id="eb532-136">8</span><span class="sxs-lookup"><span data-stu-id="eb532-136">8</span></span>|<span data-ttu-id="eb532-137">SqlCryptCreateKey</span><span class="sxs-lookup"><span data-stu-id="eb532-137">SqlCryptCreateKey</span></span>|  
|<span data-ttu-id="eb532-138">9</span><span class="sxs-lookup"><span data-stu-id="eb532-138">9</span></span>|<span data-ttu-id="eb532-139">SqlCryptDropKey</span><span class="sxs-lookup"><span data-stu-id="eb532-139">SqlCryptDropKey</span></span>|  
|<span data-ttu-id="eb532-140">10</span><span class="sxs-lookup"><span data-stu-id="eb532-140">10</span></span>|<span data-ttu-id="eb532-141">SqlCryptGetNextKeyId</span><span class="sxs-lookup"><span data-stu-id="eb532-141">SqlCryptGetNextKeyId</span></span>|  
|<span data-ttu-id="eb532-142">11</span><span class="sxs-lookup"><span data-stu-id="eb532-142">11</span></span>|<span data-ttu-id="eb532-143">SqlCryptGetKeyInfoByKeyId</span><span class="sxs-lookup"><span data-stu-id="eb532-143">SqlCryptGetKeyInfoByKeyId</span></span>|  
|<span data-ttu-id="eb532-144">12</span><span class="sxs-lookup"><span data-stu-id="eb532-144">12</span></span>|<span data-ttu-id="eb532-145">SqlCryptGetKeyInfoByThumb</span><span class="sxs-lookup"><span data-stu-id="eb532-145">SqlCryptGetKeyInfoByThumb</span></span>|  
|<span data-ttu-id="eb532-146">13</span><span class="sxs-lookup"><span data-stu-id="eb532-146">13</span></span>|<span data-ttu-id="eb532-147">SqlCryptGetKeyInfoByName</span><span class="sxs-lookup"><span data-stu-id="eb532-147">SqlCryptGetKeyInfoByName</span></span>|  
|<span data-ttu-id="eb532-148">14</span><span class="sxs-lookup"><span data-stu-id="eb532-148">14</span></span>|<span data-ttu-id="eb532-149">SqlCryptExportKey</span><span class="sxs-lookup"><span data-stu-id="eb532-149">SqlCryptExportKey</span></span>|  
|<span data-ttu-id="eb532-150">15</span><span class="sxs-lookup"><span data-stu-id="eb532-150">15</span></span>|<span data-ttu-id="eb532-151">SqlCryptImportKey</span><span class="sxs-lookup"><span data-stu-id="eb532-151">SqlCryptImportKey</span></span>|  
|<span data-ttu-id="eb532-152">16</span><span class="sxs-lookup"><span data-stu-id="eb532-152">16</span></span>|<span data-ttu-id="eb532-153">SqlCryptEncrypt</span><span class="sxs-lookup"><span data-stu-id="eb532-153">SqlCryptEncrypt</span></span>|  
|<span data-ttu-id="eb532-154">17</span><span class="sxs-lookup"><span data-stu-id="eb532-154">17</span></span>|<span data-ttu-id="eb532-155">SqlCryptDecrypt</span><span class="sxs-lookup"><span data-stu-id="eb532-155">SqlCryptDecrypt</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="eb532-156">使用者動作</span><span class="sxs-lookup"><span data-stu-id="eb532-156">User Action</span></span>  
 <span data-ttu-id="eb532-157">如需詳細資訊，請連絡密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="eb532-157">Contact the cryptographic provider for more information.</span></span>  
  
  
