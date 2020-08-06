---
title: NULL (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585504"
---
# <a name="null-ssis-expression"></a><span data-ttu-id="47a5c-102">NULL (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="47a5c-102">NULL (SSIS Expression)</span></span>
  <span data-ttu-id="47a5c-103">傳回所要求資料類型的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="47a5c-103">Returns a null value of a requested data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="47a5c-104">Syntax</span></span>  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a><span data-ttu-id="47a5c-105">引數</span><span class="sxs-lookup"><span data-stu-id="47a5c-105">Arguments</span></span>  
 <span data-ttu-id="47a5c-106">*typespec*</span><span class="sxs-lookup"><span data-stu-id="47a5c-106">*typespec*</span></span>  
 <span data-ttu-id="47a5c-107">是有效的資料類型。</span><span class="sxs-lookup"><span data-stu-id="47a5c-107">Is a valid data type.</span></span> <span data-ttu-id="47a5c-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="47a5c-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="47a5c-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="47a5c-109">Result Types</span></span>  
 <span data-ttu-id="47a5c-110">任何含有 Null 值的有效資料類型。</span><span class="sxs-lookup"><span data-stu-id="47a5c-110">Any valid data type with a null value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47a5c-111">備註</span><span class="sxs-lookup"><span data-stu-id="47a5c-111">Remarks</span></span>  
 <span data-ttu-id="47a5c-112">如果引數為 Null，則 NULL 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="47a5c-112">NULL returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="47a5c-113">某些資料類型需要使用參數才能要求 Null 值。</span><span class="sxs-lookup"><span data-stu-id="47a5c-113">Parameters are required to request a null value for some data types.</span></span> <span data-ttu-id="47a5c-114">下表列出這些資料類型及其參數。</span><span class="sxs-lookup"><span data-stu-id="47a5c-114">The following table lists these data types and their parameters.</span></span>  
  
|<span data-ttu-id="47a5c-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="47a5c-115">Data type</span></span>|<span data-ttu-id="47a5c-116">參數</span><span class="sxs-lookup"><span data-stu-id="47a5c-116">Parameter</span></span>|<span data-ttu-id="47a5c-117">範例</span><span class="sxs-lookup"><span data-stu-id="47a5c-117">Example</span></span>|  
|---------------|---------------|-------------|  
|<span data-ttu-id="47a5c-118">DT_STR</span><span class="sxs-lookup"><span data-stu-id="47a5c-118">DT_STR</span></span>|<span data-ttu-id="47a5c-119">*charcount*</span><span class="sxs-lookup"><span data-stu-id="47a5c-119">*charcount*</span></span><br /><br /> <span data-ttu-id="47a5c-120">*codepage*</span><span class="sxs-lookup"><span data-stu-id="47a5c-120">*codepage*</span></span>|<span data-ttu-id="47a5c-121">(DT_STR,30,1252) 會使用 1252 字碼頁將 30 個字元轉換成 DT_STR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="47a5c-121">(DT_STR,30,1252) casts 30 characters to the DT_STR data type using the 1252 code page.</span></span>|  
|<span data-ttu-id="47a5c-122">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="47a5c-122">DT_WSTR</span></span>|<span data-ttu-id="47a5c-123">*charcount*</span><span class="sxs-lookup"><span data-stu-id="47a5c-123">*charcount*</span></span>|<span data-ttu-id="47a5c-124">(DT_WSTR,20) 會將 20 個字元轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="47a5c-124">(DT_WSTR,20) casts 20 characters to the DT_WSTR data type.</span></span>|  
|<span data-ttu-id="47a5c-125">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="47a5c-125">DT_BYTES</span></span>|<span data-ttu-id="47a5c-126">*bytecount*</span><span class="sxs-lookup"><span data-stu-id="47a5c-126">*bytecount*</span></span>|<span data-ttu-id="47a5c-127">(DT_BYTES,50) 將 50 個位元組轉換為 DT_BYTES 資料類型。</span><span class="sxs-lookup"><span data-stu-id="47a5c-127">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|  
|<span data-ttu-id="47a5c-128">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="47a5c-128">DT_DECIMAL</span></span>|<span data-ttu-id="47a5c-129">*scale*</span><span class="sxs-lookup"><span data-stu-id="47a5c-129">*scale*</span></span>|<span data-ttu-id="47a5c-130">(DT_DECIMAL,2) 將數值轉換為 DT_DECIMAL 資料類型，使用 2 位小數位數。</span><span class="sxs-lookup"><span data-stu-id="47a5c-130">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|  
|<span data-ttu-id="47a5c-131">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="47a5c-131">DT_NUMERIC</span></span>|<span data-ttu-id="47a5c-132">*有效位數*</span><span class="sxs-lookup"><span data-stu-id="47a5c-132">*precision*</span></span><br /><br /> <span data-ttu-id="47a5c-133">*scale*</span><span class="sxs-lookup"><span data-stu-id="47a5c-133">*scale*</span></span>|<span data-ttu-id="47a5c-134">(DT_NUMERIC,10,3) 將數值轉換為 DT_NUMERIC 資料類型，使用 10 位有效位數與 3 位小數位數。</span><span class="sxs-lookup"><span data-stu-id="47a5c-134">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|  
|<span data-ttu-id="47a5c-135">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="47a5c-135">DT_TEXT</span></span>|<span data-ttu-id="47a5c-136">*codepage*</span><span class="sxs-lookup"><span data-stu-id="47a5c-136">*codepage*</span></span>|<span data-ttu-id="47a5c-137">(DT_TEXT,1252) 將值轉換為 DT_TEXT 資料類型，使用 1252 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="47a5c-137">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="47a5c-138">運算式範例</span><span class="sxs-lookup"><span data-stu-id="47a5c-138">Expression Examples</span></span>  
 <span data-ttu-id="47a5c-139">這些範例會傳回下列資料類型的 Null 值：DT_STR、DT_DATE 和 DT_BOOL。</span><span class="sxs-lookup"><span data-stu-id="47a5c-139">These examples return the null value of the data types: DT_STR, DT_DATE, and DT_BOOL.</span></span>  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="47a5c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47a5c-140">See Also</span></span>  
 <span data-ttu-id="47a5c-141">[ISNULL &#40;SSIS 運算式&#41;](null-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="47a5c-141">[ISNULL &#40;SSIS Expression&#41;](null-ssis-expression.md) </span></span>  
 [<span data-ttu-id="47a5c-142">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="47a5c-142">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
