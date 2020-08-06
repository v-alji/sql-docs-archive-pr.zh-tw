---
title: 快速剖析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 343b8b8b74338512dbf29b3d2efd436df1ffa8ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704309"
---
# <a name="fast-parse"></a><span data-ttu-id="47abf-102">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="47abf-102">Fast Parse</span></span>
  <span data-ttu-id="47abf-103">快速剖析提供一組快速、簡單的常式用以剖析資料。</span><span class="sxs-lookup"><span data-stu-id="47abf-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="47abf-104">這些常式並不區分地區設定，而且只支援一組日期、時間和整數格式的子集。</span><span class="sxs-lookup"><span data-stu-id="47abf-104">These routines are not locale-sensitive and they support only a subset of date, time, and integer formats.</span></span>  
  
## <a name="requirements-and-limitations"></a><span data-ttu-id="47abf-105">需求和限制</span><span class="sxs-lookup"><span data-stu-id="47abf-105">Requirements and Limitations</span></span>  
 <span data-ttu-id="47abf-106">實作快速剖析時，封裝將無法解譯使用特定地區設定格式與許多常用之 ISO 8601 基本格式與擴充格式的日期、時間和數值資料，但卻可以提高封裝的效能。</span><span class="sxs-lookup"><span data-stu-id="47abf-106">By implementing fast parse, a package forfeits its ability to interpret date, time, and numeric data in locale-specific formats and many frequently used ISO 8601 basic and extended formats, but the package enhances its performance.</span></span> <span data-ttu-id="47abf-107">例如，快速剖析僅支援最常用的日期格式表示法 (例如 YYYYMMDD 和 YYYY-MM-DD)，不會執行地區設定特定的剖析，也不會識別貨幣資料中的特殊字元，且無法轉換以十六進位表示或以科學記號表示的整數。</span><span class="sxs-lookup"><span data-stu-id="47abf-107">For example, fast parse supports only the most commonly used date format representations such as YYYYMMDD and YYYY-MM-DD, does not perform locale-specific parsing, does not recognize special characters in currency data, and cannot convert hexadecimal or scientific representation of integers.</span></span>  
  
 <span data-ttu-id="47abf-108">只有在使用「一般檔案」來源或「資料轉換」時，才能夠使用快速剖析。</span><span class="sxs-lookup"><span data-stu-id="47abf-108">Fast parse is available only when you use the Flat File source or the Data Conversion transformation.</span></span> <span data-ttu-id="47abf-109">效能的提高可能會很顯著，因此如果可能，您應該考慮在這些資料流程元件中使用快速剖析。</span><span class="sxs-lookup"><span data-stu-id="47abf-109">The increase in performance can be significant, and you should consider using fast parse in these data flow components if you can.</span></span>  
  
 <span data-ttu-id="47abf-110">如果封裝中的資料流程需要區分地區設定的剖析，則建議使用標準剖析來代替快速剖析。</span><span class="sxs-lookup"><span data-stu-id="47abf-110">If the data flow in the package requires locale-sensitive parsing, standard parse is recommended instead of fast parse.</span></span> <span data-ttu-id="47abf-111">例如，快速剖析不會識別區分地區設定的資料，包括十進位符號 (例如逗號)、非年-月-日格式的日期格式以及貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="47abf-111">For example, fast parse does not recognize locale-sensitive data that includes decimal symbols such as the comma, date formats other than year-month-date formats, and currency symbols.</span></span>  
  
 <span data-ttu-id="47abf-112">快速剖析不會識別隱含一或多個日期部分 (例如紀元、年或月) 的截斷表示法。</span><span class="sxs-lookup"><span data-stu-id="47abf-112">Truncated representations that imply one or more date parts, such as a century, a year, or a month, are not recognized by fast parse.</span></span> <span data-ttu-id="47abf-113">例如，快速剖析無法識別以隱含紀元方式指定年份和月份的 '**-YYMM**' 格式，也無法識別以隱含年份方式指定月份的 '**--MM**' 格式。</span><span class="sxs-lookup"><span data-stu-id="47abf-113">For example, fast parse recognizes neither the '**-YYMM**' format, which specifies a year and month in an implied century, nor '**--MM**', which specifies a month in an implied year.</span></span> <span data-ttu-id="47abf-114">不過，可以識別已降低有效位數的某些表示法。</span><span class="sxs-lookup"><span data-stu-id="47abf-114">However, some representations with reduced precision are recognized.</span></span> <span data-ttu-id="47abf-115">例如，快速剖析可識別僅指出小時和分鐘的「hhmm;」格式，以及僅指出年份的「**YYYY**」格式。</span><span class="sxs-lookup"><span data-stu-id="47abf-115">For example, fast parse recognizes the 'hhmm;' format, which indicates hour and minute only, and '**YYYY**', which indicates year only.</span></span>  
  
 <span data-ttu-id="47abf-116">快速剖析在資料行層級指定。</span><span class="sxs-lookup"><span data-stu-id="47abf-116">Fast parse is specified at the column level.</span></span> <span data-ttu-id="47abf-117">在「一般檔案」來源和「資料轉換」轉換中，可以在輸出資料行上指定「快速剖析」。</span><span class="sxs-lookup"><span data-stu-id="47abf-117">In the Flat File source and the Data Conversion transformation, you can specify Fast parse on output columns.</span></span> <span data-ttu-id="47abf-118">輸入和輸出均可包含區分地區設定和不區分地區設定的資料行。</span><span class="sxs-lookup"><span data-stu-id="47abf-118">Inputs and outputs can include both locale-sensitive and locale-insensitive columns.</span></span>  
  
 <span data-ttu-id="47abf-119">如需有關「快速剖析」支援之資料格式的詳細資訊，請參閱＜ [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) ＞及＜ [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md)＞。</span><span class="sxs-lookup"><span data-stu-id="47abf-119">For more information about the data formats that Fast parse supports, see [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) and [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="47abf-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="47abf-120">Related Tasks</span></span>  
 [<span data-ttu-id="47abf-121">設定快速剖析</span><span class="sxs-lookup"><span data-stu-id="47abf-121">Set Fast Parse</span></span>](../../2014/integration-services/set-fast-parse.md)  
  
  
