---
title: 原始檔案自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7614c03fbf44f37597e586549e306d01c28b523d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593470"
---
# <a name="raw-file-custom-properties"></a><span data-ttu-id="3a41f-102">原始檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3a41f-102">Raw File Custom Properties</span></span>
  <span data-ttu-id="3a41f-103">**來源自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="3a41f-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="3a41f-104">原始檔案來源同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-104">The Raw File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="3a41f-105">下表描述的是原始檔案來源的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-105">The following table describes the custom properties of the Raw File source.</span></span> <span data-ttu-id="3a41f-106">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="3a41f-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="3a41f-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="3a41f-107">Property name</span></span>|<span data-ttu-id="3a41f-108">資料類型</span><span class="sxs-lookup"><span data-stu-id="3a41f-108">Data Type</span></span>|<span data-ttu-id="3a41f-109">描述</span><span class="sxs-lookup"><span data-stu-id="3a41f-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="3a41f-110">AccessMode</span><span class="sxs-lookup"><span data-stu-id="3a41f-110">AccessMode</span></span>|<span data-ttu-id="3a41f-111">整數 (列舉)</span><span class="sxs-lookup"><span data-stu-id="3a41f-111">Integer (enumeration)</span></span>|<span data-ttu-id="3a41f-112">用來存取原始資料的模式。</span><span class="sxs-lookup"><span data-stu-id="3a41f-112">The mode used to access the raw data.</span></span> <span data-ttu-id="3a41f-113">可能的值為 `File name` (0) 和 `File name from variable` (1)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-113">The possible values are `File name` (0) and `File name from variable` (1).</span></span> <span data-ttu-id="3a41f-114">預設值為 `File name` (0)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-114">The default value is `File name` (0).</span></span>|  
|<span data-ttu-id="3a41f-115">FileName</span><span class="sxs-lookup"><span data-stu-id="3a41f-115">FileName</span></span>|<span data-ttu-id="3a41f-116">String</span><span class="sxs-lookup"><span data-stu-id="3a41f-116">String</span></span>|<span data-ttu-id="3a41f-117">來源檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3a41f-117">The path and file name of the source file.</span></span>|  
  
 <span data-ttu-id="3a41f-118">原始檔案來源的輸出和輸出資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-118">The output and the output columns of the Raw File source have no custom properties.</span></span>  
  
 <span data-ttu-id="3a41f-119">如需相關資訊，請參閱 [Raw File Source](raw-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-119">For more information, see [Raw File Source](raw-file-source.md).</span></span>  
  
 <span data-ttu-id="3a41f-120">**目的地自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="3a41f-120">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="3a41f-121">原始檔案目的地同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-121">The Raw File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="3a41f-122">下表描述的是原始檔案目的地的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-122">The following table describes the custom properties of the Raw File destination.</span></span> <span data-ttu-id="3a41f-123">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="3a41f-123">All properties are read/write.</span></span>  
  
|<span data-ttu-id="3a41f-124">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="3a41f-124">Property name</span></span>|<span data-ttu-id="3a41f-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="3a41f-125">Data Type</span></span>|<span data-ttu-id="3a41f-126">描述</span><span class="sxs-lookup"><span data-stu-id="3a41f-126">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="3a41f-127">AccessMode</span><span class="sxs-lookup"><span data-stu-id="3a41f-127">AccessMode</span></span>|<span data-ttu-id="3a41f-128">整數 (列舉)</span><span class="sxs-lookup"><span data-stu-id="3a41f-128">Integer (enumeration)</span></span>|<span data-ttu-id="3a41f-129">一個值，指定 FileName 屬性包含檔案名稱，或包含檔案名稱之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a41f-129">A value that specifies whether the FileName property contains a file name, or the name of a variable that contains a file name.</span></span> <span data-ttu-id="3a41f-130">這些選項包括 `File name` (0) 和 `File name from variable` (1)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-130">The options are `File name` (0) and `File name from variable` (1).</span></span>|  
|<span data-ttu-id="3a41f-131">FileName</span><span class="sxs-lookup"><span data-stu-id="3a41f-131">FileName</span></span>|<span data-ttu-id="3a41f-132">String</span><span class="sxs-lookup"><span data-stu-id="3a41f-132">String</span></span>|<span data-ttu-id="3a41f-133">原始檔案目的地寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3a41f-133">The name of the file to which the Raw File destination writes.</span></span>|  
|<span data-ttu-id="3a41f-134">WriteOption</span><span class="sxs-lookup"><span data-stu-id="3a41f-134">WriteOption</span></span>|<span data-ttu-id="3a41f-135">整數 (列舉)</span><span class="sxs-lookup"><span data-stu-id="3a41f-135">Integer (enumeration)</span></span>|<span data-ttu-id="3a41f-136">一個值，指定原始檔案目的地是否會刪除具有相同名稱的現有檔案。</span><span class="sxs-lookup"><span data-stu-id="3a41f-136">A value that specifies whether the Raw File destination deletes an existing file that has the same name.</span></span> <span data-ttu-id="3a41f-137">這些選項包括 `Create Always` (0)、`Create Once` (1)、`Truncate and Append` (3) 和 `Append` (2)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-137">The options are `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), and `Append` (2).</span></span> <span data-ttu-id="3a41f-138">此屬性的預設值為 `Create Always` (0)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-138">The default value of this property is `Create Always` (0).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3a41f-139">附加作業要求已附加資料的中繼資料與檔案中已有資料的中繼資料相符。</span><span class="sxs-lookup"><span data-stu-id="3a41f-139">An append operation requires the metadata of the appended data to match the metadata of the data already present in the file.</span></span>  
  
 <span data-ttu-id="3a41f-140">原始檔案目的地的輸入和輸入資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3a41f-140">The input and the input columns of the Raw File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="3a41f-141">如需相關資訊，請參閱 [Raw File Destination](raw-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="3a41f-141">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a41f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a41f-142">See Also</span></span>  
 [<span data-ttu-id="3a41f-143">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3a41f-143">Common Properties</span></span>](../common-properties.md)  
  
  
