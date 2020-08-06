---
title: Cast (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CAST function
- cast operator
- converting data types [Integration Services]
- data types [Integration Services], expressions
- data types [Integration Services], converting
ms.assetid: d4e915cc-1c7b-4b2e-93b0-13a8b0cb9242
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65d60eca4340b65b8a82855c3f2b29a6cda56e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705353"
---
# <a name="cast-ssis-expression"></a><span data-ttu-id="2f6ab-102">Cast (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="2f6ab-102">Cast (SSIS Expression)</span></span>
  <span data-ttu-id="2f6ab-103">將運算式從一種資料類型明確轉換成另一種資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-103">Explicitly converts an expression from one data type to a different data type.</span></span> <span data-ttu-id="2f6ab-104">轉換運算子也可以當作截斷運算子使用。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-104">The cast operator can also function as a truncation operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f6ab-105">語法</span><span class="sxs-lookup"><span data-stu-id="2f6ab-105">Syntax</span></span>

```

(type_spec) expression

```

## <a name="arguments"></a><span data-ttu-id="2f6ab-106">引數</span><span class="sxs-lookup"><span data-stu-id="2f6ab-106">Arguments</span></span>
 <span data-ttu-id="2f6ab-107">*type_spec*是有效的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-107">*type_spec* Is a valid [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span>

 <span data-ttu-id="2f6ab-108">*運算式*這是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-108">*expression* Is a valid expression.</span></span>

## <a name="result-types"></a><span data-ttu-id="2f6ab-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="2f6ab-109">Result Types</span></span>
 <span data-ttu-id="2f6ab-110">*type_spec*的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-110">The data type of *type_spec*.</span></span> <span data-ttu-id="2f6ab-111">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-111">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="2f6ab-112">備註</span><span class="sxs-lookup"><span data-stu-id="2f6ab-112">Remarks</span></span>
 <span data-ttu-id="2f6ab-113">下列圖表顯示合法的轉換運算。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-113">The following diagram shows legal cast operations.</span></span>

 <span data-ttu-id="2f6ab-114">![資料類型之間的合法和不合法轉換](../media/data-conversion.gif "資料類型之間的合法和不合法轉換")</span><span class="sxs-lookup"><span data-stu-id="2f6ab-114">![Legal and not legal casts between data types](../media/data-conversion.gif "Legal and not legal casts between data types")</span></span>

 <span data-ttu-id="2f6ab-115">轉換成某些資料類型需要參數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-115">Casting to some data types requires parameters.</span></span> <span data-ttu-id="2f6ab-116">下表列出這些資料類型及其參數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-116">The following table lists these data types and their parameters.</span></span>

|<span data-ttu-id="2f6ab-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="2f6ab-117">Data type</span></span>|<span data-ttu-id="2f6ab-118">參數</span><span class="sxs-lookup"><span data-stu-id="2f6ab-118">Parameter</span></span>|<span data-ttu-id="2f6ab-119">範例</span><span class="sxs-lookup"><span data-stu-id="2f6ab-119">Example</span></span>|
|---------------|---------------|-------------|
|<span data-ttu-id="2f6ab-120">DT_STR</span><span class="sxs-lookup"><span data-stu-id="2f6ab-120">DT_STR</span></span>|<span data-ttu-id="2f6ab-121">*charcount*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-121">*charcount*</span></span><br /><br /> <span data-ttu-id="2f6ab-122">*頁*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-122">*codepage*</span></span>|<span data-ttu-id="2f6ab-123">(DT_STR,30,1252) 會使用 1252 字碼頁將 30 個位元組 (或 30 個單一字元) 轉換成 DT_STR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-123">(DT_STR,30,1252) casts 30 bytes, or 30 single characters, to the DT_STR data type using the 1252 code page.</span></span>|
|<span data-ttu-id="2f6ab-124">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="2f6ab-124">DT_WSTR</span></span>|<span data-ttu-id="2f6ab-125">*Charcount*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-125">*Charcount*</span></span>|<span data-ttu-id="2f6ab-126">(DT_WSTR,20) 會將成對的 20 個位元組 (或 20 個 Unicode 字元) 轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-126">(DT_WSTR,20) casts 20 byte pairs, or 20 Unicode characters, to the DT_WSTR data type.</span></span>|
|<span data-ttu-id="2f6ab-127">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="2f6ab-127">DT_BYTES</span></span>|<span data-ttu-id="2f6ab-128">*Bytecount*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-128">*Bytecount*</span></span>|<span data-ttu-id="2f6ab-129">(DT_BYTES,50) 將 50 個位元組轉換為 DT_BYTES 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-129">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|
|<span data-ttu-id="2f6ab-130">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="2f6ab-130">DT_DECIMAL</span></span>|<span data-ttu-id="2f6ab-131">*縮放比例*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-131">*Scale*</span></span>|<span data-ttu-id="2f6ab-132">(DT_DECIMAL,2) 將數值轉換為 DT_DECIMAL 資料類型，使用 2 位小數位數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-132">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|
|<span data-ttu-id="2f6ab-133">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="2f6ab-133">DT_NUMERIC</span></span>|<span data-ttu-id="2f6ab-134">*有效位數*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-134">*Precision*</span></span><br /><br /> <span data-ttu-id="2f6ab-135">*縮放比例*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-135">*Scale*</span></span>|<span data-ttu-id="2f6ab-136">(DT_NUMERIC,10,3) 將數值轉換為 DT_NUMERIC 資料類型，使用 10 位有效位數與 3 位小數位數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-136">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|
|<span data-ttu-id="2f6ab-137">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="2f6ab-137">DT_TEXT</span></span>|<span data-ttu-id="2f6ab-138">*頁*</span><span class="sxs-lookup"><span data-stu-id="2f6ab-138">*Codepage*</span></span>|<span data-ttu-id="2f6ab-139">(DT_TEXT,1252) 將值轉換為 DT_TEXT 資料類型，使用 1252 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-139">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|

 <span data-ttu-id="2f6ab-140">當字串轉換成 DT_DATE 或 DT_DATE 轉換成字串時，會使用轉換的地區設定。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-140">When a string is cast to a DT_DATE, or vice versa, the locale of the transformation is used.</span></span> <span data-ttu-id="2f6ab-141">不過，日期是使用 ISO 格式 YYYY-MM-DD，而不論地區設定的偏好設定是否使用 ISO 格式。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-141">However, the date is in the ISO format of YYYY-MM-DD, regardless of whether the locale preference uses the ISO format.</span></span>

> [!NOTE]
>  <span data-ttu-id="2f6ab-142">若要將字串轉換成 DT_DATE 以外的日期資料類型，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-142">To convert a string to a date data type other than DT_DATE, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="2f6ab-143">如果字碼頁為多位元組字元字碼頁，則位元組和字元的數目可能會不一樣。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-143">If the code page is a multibyte character code page, the number of bytes and characters may differ.</span></span> <span data-ttu-id="2f6ab-144">使用相同的 *charcount* 值從 DT_WSTR 轉換成 DT_STR，可能會截斷轉換完成字串中的最後幾個字元。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-144">Casting from a DT_WSTR to a DT_STR with the same *charcount* value may cause truncation of the final characters in the converted string.</span></span> <span data-ttu-id="2f6ab-145">如果目的地資料表的資料行中有足夠的儲存體，請將 *charcount* 參數的值設定為反映多位元組字碼頁所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-145">If sufficient storage is available in the column of the destination table, set the value of the *charcount* parameter to reflect the number of bytes that the multibyte code page requires.</span></span> <span data-ttu-id="2f6ab-146">例如，如果您使用 936 字碼頁將字元資料轉換成 DT_STR 資料類型，則應將 *charcount* 設定成最多為您希望資料包含的字元數之兩倍的值；如果使用 UTF-8 字碼頁轉換字元資料，則應將 *charcount* 設定為四倍。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-146">For example, if you cast character data to a DT_STR data type using the 936 code page, you should set *charcount* to a value up to two times greater than the number of characters that you expect the data to contain; if you cast character data using the UTF-8 code page, you should set *charcount* to a value up to four times greater.</span></span>

 <span data-ttu-id="2f6ab-147">如需日期資料類型結構的詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-147">For more information about the structure of date data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="ssis-expression-examples"></a><span data-ttu-id="2f6ab-148">SSIS 運算式範例</span><span class="sxs-lookup"><span data-stu-id="2f6ab-148">SSIS Expression Examples</span></span>
 <span data-ttu-id="2f6ab-149">此範例會將數值轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-149">This example casts a numeric value to an integer.</span></span>

```
(DT_I4) 3.57
```

 <span data-ttu-id="2f6ab-150">此範例會使用 1252 字碼頁將整數轉換成字元字串。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-150">This example casts an integer to a character string using the 1252 code page.</span></span>

```
(DT_STR,1,1252)5
```

 <span data-ttu-id="2f6ab-151">此範例會將 3 個字元的字串轉換成雙位元組字元。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-151">This example casts a three-character string to double-byte characters.</span></span>

```
(DT_WSTR,3)"Cat"
```

 <span data-ttu-id="2f6ab-152">此範例會將整數轉換成擁有 2 位小數位數的小數。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-152">This example casts an integer to a decimal with a scale of two.</span></span>

```
(DT_DECIMAl,2)500
```

 <span data-ttu-id="2f6ab-153">此範例會將整數轉換成擁有 7 位有效位數和 3 位小數位數的數值。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-153">This example casts an integer to a numeric with a precision of seven and scale of three.</span></span>

```
(DT_NUMERIC,7,3)4000
```

 <span data-ttu-id="2f6ab-154">此範例會使用 1252 字碼頁將 **FirstName** 資料行中，以 **nvarchar** 資料類型定義且長度為 50 的值轉換成字元字串。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-154">This example casts values in the **FirstName** column, defined with an **nvarchar** data type and a length of 50, to a character string using the 1252 code page.</span></span>

```
(DT_STR,50,1252)FirstName
```

 <span data-ttu-id="2f6ab-155">此範例會將 **DateFirstPurchase** 資料行中 DT_DBDATE 類型的值轉換成長度為 20 的 Unicode 字元字串。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-155">This example casts values in the **DateFirstPurchase** column of type DT_DBDATE, to a Unicode character string with a length of 20.</span></span>

```
(DT_WSTR,20)DateFirstPurchase
```

 <span data-ttu-id="2f6ab-156">此範例會將字串常值「True」轉換成布林。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-156">This example casts the string literal "True" to a Boolean.</span></span>

```
(DT_BOOL)"True"
```

 <span data-ttu-id="2f6ab-157">此範例會將字串常值轉換為 DT_DBDATE。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-157">This example casts a string literal to DT_DBDATE.</span></span>

```
(DT_DBDATE) "1999-10-11"
```

 <span data-ttu-id="2f6ab-158">此範例會將字串常值轉換為使用 5 位數毫秒的 DT_DBTIME2 資料類型</span><span class="sxs-lookup"><span data-stu-id="2f6ab-158">This example casts a string literal to the DT_DBTIME2 data type that uses 5 digits for fractional seconds.</span></span> <span data-ttu-id="2f6ab-159">(DT_DBTIME2 資料類型可以指定 0 到 7 位數之間的毫秒)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-159">(The DT_DBTIME2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIME2, 5) "16:34:52.12345"
```

 <span data-ttu-id="2f6ab-160">此範例會將字串常值轉換為使用 4 位數毫秒的 DT_DBTIMESTAMP2 資料類型</span><span class="sxs-lookup"><span data-stu-id="2f6ab-160">This example casts a string literal to the DT_DBTIMESTAMP2 data type that uses 4 digits for fractional seconds.</span></span> <span data-ttu-id="2f6ab-161">(DT_DBTIMESTAMP2 資料類型可以指定 0 到 7 位數之間的毫秒)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-161">(The DT_DBTIMESTAMP2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMP2, 4) "1999-10-11 16:34:52.1234"
```

 <span data-ttu-id="2f6ab-162">此範例會將字串常值轉換為使用 7 位數毫秒的 DT_DBTIMESTAMPOFFSET 資料類型</span><span class="sxs-lookup"><span data-stu-id="2f6ab-162">This example casts a string literal to the DT_DBTIMESTAMPOFFSET data type that uses 7 digits for fractional seconds.</span></span> <span data-ttu-id="2f6ab-163">(DT_DBTIMESTAMPOFFSET 資料類型可以指定 0 到 7 位數之間的毫秒)。</span><span class="sxs-lookup"><span data-stu-id="2f6ab-163">(The DT_DBTIMESTAMPOFFSET data typecan have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMPOFFSET, 7) "1999-10-11 16:34:52.1234567 + 5:35"
```

## <a name="see-also"></a><span data-ttu-id="2f6ab-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6ab-164">See Also</span></span>
 <span data-ttu-id="2f6ab-165">[運算子優先順序和關聯](operator-precedence-and-associativity.md)性[運算子 &#40;ssis 運算式&#41;](operators-ssis-expression.md) [Integration Services &#40;Ssis&#41;](integration-services-ssis-expressions.md)運算式[中 Integration Services 資料類型](integration-services-data-types-in-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="2f6ab-165">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)</span></span>


