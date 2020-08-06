---
title: Null 屬性和三值邏輯比較 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b8000c1c28d5a1d3d129b6e8d01c4ab2fbbbc7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709633"
---
# <a name="nullability-and-three-value-logic-comparisons"></a><span data-ttu-id="d4920-102">Null 屬性和三值邏輯比較</span><span class="sxs-lookup"><span data-stu-id="d4920-102">Nullability and Three-Value Logic Comparisons</span></span>
  <span data-ttu-id="d4920-103">如果您熟悉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，就會在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的 `System.Data.SqlTypes` 命名空間中找到類似的語意和有效位數。</span><span class="sxs-lookup"><span data-stu-id="d4920-103">If you are familiar with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, you will find similar semantics and precision in the `System.Data.SqlTypes` namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="d4920-104">不過，其中仍有一些差異，而且本主題將涵蓋最重要的差異。</span><span class="sxs-lookup"><span data-stu-id="d4920-104">There are some differences, however, and this topic covers the most important of these differences.</span></span>  
  
## <a name="null-values"></a><span data-ttu-id="d4920-105">NULL 值</span><span class="sxs-lookup"><span data-stu-id="d4920-105">NULL Values</span></span>  
 <span data-ttu-id="d4920-106">原生 Common Language Runtime (CLR) 資料類型與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型之間的主要差異是，前者不允許使用 NULL 值，而後者會提供完整的 NULL 語意。</span><span class="sxs-lookup"><span data-stu-id="d4920-106">A primary difference between native common language runtime (CLR) data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types is that the former do not allow for NULL values, while the latter provide full NULL semantics.</span></span>  
  
 <span data-ttu-id="d4920-107">比較會受到 NULL 值的影響。</span><span class="sxs-lookup"><span data-stu-id="d4920-107">Comparisons are affected by NULL values.</span></span> <span data-ttu-id="d4920-108">比較 x 和 y 這兩個值時，如果 x 或 y 為 NULL，則某些邏輯比較就會評估為 UNKNOWN 值，而非 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="d4920-108">When comparing two values x and y, if either x or y is NULL, then some logical comparisons evaluate to an UNKNOWN value rather than true or false.</span></span>  
  
## <a name="sqlboolean-data-type"></a><span data-ttu-id="d4920-109">SqlBoolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="d4920-109">SqlBoolean Data Type</span></span>  
 <span data-ttu-id="d4920-110">`System.Data.SqlTypes` 命名空間導入了 `SqlBoolean` 類型來代表這個 3 值邏輯。</span><span class="sxs-lookup"><span data-stu-id="d4920-110">The `System.Data.SqlTypes` namespace introduces a `SqlBoolean` type to represent this 3-value logic.</span></span> <span data-ttu-id="d4920-111">任何 `SqlTypes` 之間的比較都會傳回 `SqlBoolean` 值類型。</span><span class="sxs-lookup"><span data-stu-id="d4920-111">Comparisons between any `SqlTypes` return a `SqlBoolean` value type.</span></span> <span data-ttu-id="d4920-112">UNKNOWN 值是由 `SqlBoolean` 類型的 Null 值所代表。</span><span class="sxs-lookup"><span data-stu-id="d4920-112">The UNKNOWN value is represented by the null value of the `SqlBoolean` type.</span></span> <span data-ttu-id="d4920-113">系統提供了 `IsTrue`、`IsFalse` 和 `IsNull` 屬性來檢查 `SqlBoolean` 類型的值。</span><span class="sxs-lookup"><span data-stu-id="d4920-113">The properties `IsTrue`, `IsFalse`, and `IsNull` are provided to check the value of a `SqlBoolean` type.</span></span>  
  
## <a name="operations-functions-and-null-values"></a><span data-ttu-id="d4920-114">作業、函數和 NULL 值</span><span class="sxs-lookup"><span data-stu-id="d4920-114">Operations, Functions, and NULL Values</span></span>  
 <span data-ttu-id="d4920-115">所有算術運算子 (+、-、 \* 、/、% ) 、位運算子 (~、& 和 |) ，而且如果的任何運算元或引數為 null，大部分函數都會傳回 Null `SqlTypes` 。</span><span class="sxs-lookup"><span data-stu-id="d4920-115">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, and |), and most functions return NULL if any of the operands or arguments of `SqlTypes` are NULL.</span></span> <span data-ttu-id="d4920-116">`IsNull` 屬性一律會傳回 true 或 false 值。</span><span class="sxs-lookup"><span data-stu-id="d4920-116">The `IsNull` property always returns a true or false value.</span></span>  
  
## <a name="precision"></a><span data-ttu-id="d4920-117">精確度</span><span class="sxs-lookup"><span data-stu-id="d4920-117">Precision</span></span>  
 <span data-ttu-id="d4920-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 中的十進位資料類型與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的數值和十進位資料類型具有不同的最大值。</span><span class="sxs-lookup"><span data-stu-id="d4920-118">Decimal data types in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR have different maximum values than those of the numeric and decimal data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d4920-119">此外，[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 十進位資料類型會採用最大有效位數。</span><span class="sxs-lookup"><span data-stu-id="d4920-119">In addition, in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR decimal data types assume the maximum precision.</span></span> <span data-ttu-id="d4920-120">不過，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 CLR 中，`SqlDecimal` 會提供相同的最大有效位數和小數位數，以及與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中十進位資料類型相同的語意。</span><span class="sxs-lookup"><span data-stu-id="d4920-120">In the CLR for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], however, `SqlDecimal` provides the same maximum precision and scale, and the same semantics as the decimal data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="overflow-detection"></a><span data-ttu-id="d4920-121">溢位偵測</span><span class="sxs-lookup"><span data-stu-id="d4920-121">Overflow Detection</span></span>  
 <span data-ttu-id="d4920-122">在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 中，兩個非常龐大的數字相加可能不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4920-122">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR, the addition of two very large numbers may not throw an exception.</span></span> <span data-ttu-id="d4920-123">不過，如果沒有使用任何檢查運算子，傳回的結果可能會「循環使用」成為負整數。</span><span class="sxs-lookup"><span data-stu-id="d4920-123">Instead, if no check operator has been used, the returned result may "wrap around" as a negative integer.</span></span> <span data-ttu-id="d4920-124">在 `System.Data.SqlTypes` 中，系統會針對所有溢位和反向溢位錯誤，以及除以零的錯誤擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4920-124">In `System.Data.SqlTypes`, exceptions are thrown for all overflow and underflow errors, and divide-by-zero errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4920-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4920-125">See Also</span></span>  
 [<span data-ttu-id="d4920-126">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="d4920-126">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
