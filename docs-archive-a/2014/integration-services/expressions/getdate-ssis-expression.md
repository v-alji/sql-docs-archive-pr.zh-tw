---
title: GETDATE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594604"
---
# <a name="getdate-ssis-expression"></a><span data-ttu-id="78959-102">GETDATE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="78959-102">GETDATE (SSIS Expression)</span></span>
  <span data-ttu-id="78959-103">以 DT_DBTIMESTAMP 格式傳回目前的系統日期。</span><span class="sxs-lookup"><span data-stu-id="78959-103">Returns the current date of the system in a DT_DBTIMESTAMP format.</span></span> <span data-ttu-id="78959-104">GETDATE 函數不採用引數。</span><span class="sxs-lookup"><span data-stu-id="78959-104">The GETDATE function takes no arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78959-105">從 GETDATE 函數傳回結果的長度為 29 個字元。</span><span class="sxs-lookup"><span data-stu-id="78959-105">The length of the return result from the GETDATE function is 29 characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78959-106">語法</span><span class="sxs-lookup"><span data-stu-id="78959-106">Syntax</span></span>  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a><span data-ttu-id="78959-107">引數</span><span class="sxs-lookup"><span data-stu-id="78959-107">Arguments</span></span>  
 <span data-ttu-id="78959-108">None</span><span class="sxs-lookup"><span data-stu-id="78959-108">None</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="78959-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="78959-109">Result Types</span></span>  
 <span data-ttu-id="78959-110">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="78959-110">DT_DBTIMESTAMP</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="78959-111">運算式範例</span><span class="sxs-lookup"><span data-stu-id="78959-111">Expression Examples</span></span>  
 <span data-ttu-id="78959-112">此範例會傳回目前日期的年。</span><span class="sxs-lookup"><span data-stu-id="78959-112">This example returns the year of the current date.</span></span>  
  
```  
DATEPART("year",GETDATE())  
```  
  
 <span data-ttu-id="78959-113">此範例會傳回 **ModifiedDate** 資料行中日期與目前日期之間的天數。</span><span class="sxs-lookup"><span data-stu-id="78959-113">This example returns the number of days between a date in the **ModifiedDate** column and the current date.</span></span>  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 <span data-ttu-id="78959-114">此範例會對目前日期加上三個月。</span><span class="sxs-lookup"><span data-stu-id="78959-114">This example adds three months to the current date.</span></span>  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="78959-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78959-115">See Also</span></span>  
 <span data-ttu-id="78959-116">[GETUTCDATE &#40;SSIS 運算式&#41;](getutcdate-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="78959-116">[GETUTCDATE &#40;SSIS Expression&#41;](getutcdate-ssis-expression.md) </span></span>  
 [<span data-ttu-id="78959-117">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="78959-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
