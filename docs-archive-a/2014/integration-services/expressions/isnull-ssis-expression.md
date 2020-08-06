---
title: ISNULL (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701431"
---
# <a name="isnull-ssis-expression"></a><span data-ttu-id="ae1fa-102">ISNULL (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="ae1fa-102">ISNULL (SSIS Expression)</span></span>
  <span data-ttu-id="ae1fa-103">依據運算式是否為 Null 來傳回布林結果。</span><span class="sxs-lookup"><span data-stu-id="ae1fa-103">Returns a Boolean result based on whether an expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae1fa-104">Syntax</span></span>  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae1fa-105">引數</span><span class="sxs-lookup"><span data-stu-id="ae1fa-105">Arguments</span></span>  
 <span data-ttu-id="ae1fa-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="ae1fa-106">*expression*</span></span>  
 <span data-ttu-id="ae1fa-107">為任何資料類型的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="ae1fa-107">Is a valid expression of any data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ae1fa-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="ae1fa-108">Result Types</span></span>  
 <span data-ttu-id="ae1fa-109">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="ae1fa-109">DT_BOOL</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ae1fa-110">運算式範例</span><span class="sxs-lookup"><span data-stu-id="ae1fa-110">Expression Examples</span></span>  
 <span data-ttu-id="ae1fa-111">如果 **DiscontinuedDate** 資料行包含 Null 值，則此範例會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="ae1fa-111">This example returns TRUE if the **DiscontinuedDate** column contains a null value.</span></span>  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 <span data-ttu-id="ae1fa-112">如果 **LastName** 資料行中的值為 Null，則此範例會傳回「Unknown last name」，否則會傳回 **LastName**中的值。</span><span class="sxs-lookup"><span data-stu-id="ae1fa-112">This example returns "Unknown last name" if the value in the **LastName** column is null, otherwise it returns the value in **LastName**.</span></span>  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 <span data-ttu-id="ae1fa-113">如果 **DaysToManufacture** 資料行為 Null，無論 **AddDays**變數的值為何，此範例會固定傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="ae1fa-113">This example always returns TRUE if the **DaysToManufacture** column is null, regardless of the value of the variable **AddDays**.</span></span>  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae1fa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1fa-114">See Also</span></span>  
 <span data-ttu-id="ae1fa-115">[函數 &#40;SSIS 運算式&#41;](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ae1fa-115">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 [<span data-ttu-id="ae1fa-116">COALESCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ae1fa-116">COALESCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
