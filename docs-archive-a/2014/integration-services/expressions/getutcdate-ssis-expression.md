---
title: GETUTCDATE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f157ab5641e521a42cb3c96c96446b31de5dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701467"
---
# <a name="getutcdate-ssis-expression"></a><span data-ttu-id="8c445-102">GETUTCDATE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="8c445-102">GETUTCDATE (SSIS Expression)</span></span>
  <span data-ttu-id="8c445-103">使用 DT_DBTIMESTAMP 格式，傳回 UTC 時間格式 (世界標準時間或格林威治標準時間) 的系統目前日期。</span><span class="sxs-lookup"><span data-stu-id="8c445-103">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time) using a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="8c445-104">GETUTCDATE 函數不接受引數。</span><span class="sxs-lookup"><span data-stu-id="8c445-104">The GETUTCDATE function takes no arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c445-105">語法</span><span class="sxs-lookup"><span data-stu-id="8c445-105">Syntax</span></span>  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c445-106">引數</span><span class="sxs-lookup"><span data-stu-id="8c445-106">Arguments</span></span>  
 <span data-ttu-id="8c445-107">None</span><span class="sxs-lookup"><span data-stu-id="8c445-107">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8c445-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="8c445-108">Result Types</span></span>  
 <span data-ttu-id="8c445-109">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="8c445-109">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8c445-110">運算式範例</span><span class="sxs-lookup"><span data-stu-id="8c445-110">Expression Examples</span></span>  
 <span data-ttu-id="8c445-111">此範例會傳回 UTC 時間格式的目前日期之年份。</span><span class="sxs-lookup"><span data-stu-id="8c445-111">This example returns the year of the current date in UTC time.</span></span>  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 <span data-ttu-id="8c445-112">此範例會傳回 **ModifiedDate** 資料行中的日期與目前 UTC 日期之間的天數。</span><span class="sxs-lookup"><span data-stu-id="8c445-112">This example returns the number of days between a date in the **ModifiedDate** column and the current UTC date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 <span data-ttu-id="8c445-113">此範例會將目前的 UTC 日期加上三個月。</span><span class="sxs-lookup"><span data-stu-id="8c445-113">This example adds three months to the current UTC date.</span></span>  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c445-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c445-114">See Also</span></span>  
 <span data-ttu-id="8c445-115">[GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="8c445-115">[GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="8c445-116">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="8c445-116">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
