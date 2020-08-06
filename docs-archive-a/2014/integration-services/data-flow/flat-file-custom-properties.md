---
title: 一般檔案自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b906e9268bf3a74ffcf5661953397ad7a24b77a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709781"
---
# <a name="flat-file-custom-properties"></a><span data-ttu-id="1ffc4-102">一般檔案自訂屬性</span><span class="sxs-lookup"><span data-stu-id="1ffc4-102">Flat File Custom Properties</span></span>
  <span data-ttu-id="1ffc4-103">**來源自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="1ffc4-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="1ffc4-104">一般檔案來源同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-104">The Flat File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="1ffc4-105">下表描述的是一般檔案來源的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-105">The following table describes the custom properties of the Flat File source.</span></span> <span data-ttu-id="1ffc4-106">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="1ffc4-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1ffc4-107">Property name</span></span>|<span data-ttu-id="1ffc4-108">資料類型</span><span class="sxs-lookup"><span data-stu-id="1ffc4-108">Data Type</span></span>|<span data-ttu-id="1ffc4-109">描述</span><span class="sxs-lookup"><span data-stu-id="1ffc4-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="1ffc4-110">FileNameColumnName</span><span class="sxs-lookup"><span data-stu-id="1ffc4-110">FileNameColumnName</span></span>|<span data-ttu-id="1ffc4-111">String</span><span class="sxs-lookup"><span data-stu-id="1ffc4-111">String</span></span>|<span data-ttu-id="1ffc4-112">包含檔案名稱之輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-112">The name of an output column that contains the file name.</span></span> <span data-ttu-id="1ffc4-113">如果沒有指定任何名稱，就不會產生包含檔案名稱的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-113">If no name is specified, no output column containing the file name will be generated.</span></span><br /><br /> <span data-ttu-id="1ffc4-114">注意：雖然您無法在 [一般檔案來源編輯器]  中使用這個屬性，但是可以使用 [進階編輯器]  來設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-114">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="1ffc4-115">RetainNulls</span><span class="sxs-lookup"><span data-stu-id="1ffc4-115">RetainNulls</span></span>|<span data-ttu-id="1ffc4-116">Boolean</span><span class="sxs-lookup"><span data-stu-id="1ffc4-116">Boolean</span></span>|<span data-ttu-id="1ffc4-117">一個值，指定當「資料轉換管線」引擎處理資料時，是否要將來源檔案的 Null 值保留成 Null 值。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-117">A value that specifies whether to retain Null values from the source file as Null values when the data is processed by the Data Transformation Pipeline engine.</span></span> <span data-ttu-id="1ffc4-118">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-118">The default value of this property is `False`.</span></span>|  
  
 <span data-ttu-id="1ffc4-119">一般檔案來源的輸出沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-119">The output of the Flat File source has no custom properties.</span></span>  
  
 <span data-ttu-id="1ffc4-120">下表描述的是一般檔案來源之輸出資料行的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-120">The following table describes the custom properties of the output columns of the Flat File source.</span></span> <span data-ttu-id="1ffc4-121">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-121">All properties are read/write.</span></span>  
  
|<span data-ttu-id="1ffc4-122">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1ffc4-122">Property name</span></span>|<span data-ttu-id="1ffc4-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="1ffc4-123">Data Type</span></span>|<span data-ttu-id="1ffc4-124">描述</span><span class="sxs-lookup"><span data-stu-id="1ffc4-124">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="1ffc4-125">FastParse</span><span class="sxs-lookup"><span data-stu-id="1ffc4-125">FastParse</span></span>|<span data-ttu-id="1ffc4-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="1ffc4-126">Boolean</span></span>|<span data-ttu-id="1ffc4-127">一個值，指出資料行會使用 DTS 所提供之速度更快但不區分地區設定的快速剖析常式，還是區分地區設定的標準剖析常式。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-127">A value that indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that DTS provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="1ffc4-128">如需詳細資訊，請參閱 [快速剖析](../fast-parse.md) 和 [標準剖析](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-128">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span> <span data-ttu-id="1ffc4-129">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-129">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="1ffc4-130">注意：雖然您無法在 [一般檔案來源編輯器]  中使用這個屬性，但是可以使用 [進階編輯器]  來設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-130">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
  
 <span data-ttu-id="1ffc4-131">如需詳細資訊，請參閱 [一般檔案來源](flat-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-131">For more information, see [Flat File Source](flat-file-source.md).</span></span>  
  
 <span data-ttu-id="1ffc4-132">**目的地自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="1ffc4-132">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="1ffc4-133">一般檔案目的地同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-133">The Flat File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="1ffc4-134">下表描述的是一般檔案目的地的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-134">The following table describes the custom properties of the Flat File destination.</span></span> <span data-ttu-id="1ffc4-135">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-135">All properties are read/write.</span></span>  
  
|<span data-ttu-id="1ffc4-136">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1ffc4-136">Property name</span></span>|<span data-ttu-id="1ffc4-137">資料類型</span><span class="sxs-lookup"><span data-stu-id="1ffc4-137">Data Type</span></span>|<span data-ttu-id="1ffc4-138">描述</span><span class="sxs-lookup"><span data-stu-id="1ffc4-138">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="1ffc4-139">頁首</span><span class="sxs-lookup"><span data-stu-id="1ffc4-139">Header</span></span>|<span data-ttu-id="1ffc4-140">String</span><span class="sxs-lookup"><span data-stu-id="1ffc4-140">String</span></span>|<span data-ttu-id="1ffc4-141">寫入任何資料之前插入檔案中的文字區塊。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-141">A block of text that is inserted in the file before any data is written.</span></span><br /><br /> <span data-ttu-id="1ffc4-142">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-142">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="1ffc4-143">Overwrite</span><span class="sxs-lookup"><span data-stu-id="1ffc4-143">Overwrite</span></span>|<span data-ttu-id="1ffc4-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="1ffc4-144">Boolean</span></span>|<span data-ttu-id="1ffc4-145">一個值，指定要覆寫或附加至具有相同名稱的現有目的地檔案。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-145">A value that specifies whether to overwrite or append to an existing destination file that has the same name.</span></span> <span data-ttu-id="1ffc4-146">此屬性的預設值為 `True`。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-146">The default value of this property is `True`.</span></span>|  
  
 <span data-ttu-id="1ffc4-147">一般檔案目的地的輸入和輸入資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-147">The input and the input columns of the Flat File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="1ffc4-148">如需詳細資訊，請參閱 [一般檔案目的地](flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffc4-148">For more information, see [Flat File Destination](flat-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffc4-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ffc4-149">See Also</span></span>  
 [<span data-ttu-id="1ffc4-150">Common Properties</span><span class="sxs-lookup"><span data-stu-id="1ffc4-150">Common Properties</span></span>](../common-properties.md)  
  
  
