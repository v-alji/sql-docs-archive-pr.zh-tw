---
title: REPLACENULL (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f10bb6ef6102076fe7b1cc236461e2358ad96372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701419"
---
# <a name="replacenull-ssis-expression"></a><span data-ttu-id="3cf31-102">REPLACENULL (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="3cf31-102">REPLACENULL (SSIS Expression)</span></span>
  <span data-ttu-id="3cf31-103">如果第一個運算式參數的值為 NULL，則會傳回第二個運算式參數的值，否則會傳回第一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="3cf31-103">Returns the value of second expression parameter if the value of first expression parameter is NULL; otherwise, returns the value of first expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf31-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cf31-104">Syntax</span></span>  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cf31-105">引數</span><span class="sxs-lookup"><span data-stu-id="3cf31-105">Arguments</span></span>  
 <span data-ttu-id="3cf31-106">*運算式 1*</span><span class="sxs-lookup"><span data-stu-id="3cf31-106">*expression 1*</span></span>  
 <span data-ttu-id="3cf31-107">檢查此運算式的結果是否為 NULL。</span><span class="sxs-lookup"><span data-stu-id="3cf31-107">The result of this expression is checked against NULL.</span></span>  
  
 <span data-ttu-id="3cf31-108">*運算式 2*</span><span class="sxs-lookup"><span data-stu-id="3cf31-108">*expression 2*</span></span>  
 <span data-ttu-id="3cf31-109">如果第一個運算式評估為 NULL，則傳回此運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="3cf31-109">The result of this expression is returned if the first expression evaluates to NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3cf31-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="3cf31-110">Result Types</span></span>  
 <span data-ttu-id="3cf31-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="3cf31-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cf31-112">備註</span><span class="sxs-lookup"><span data-stu-id="3cf31-112">Remarks</span></span>  
  
-   <span data-ttu-id="3cf31-113">*expression 2* 的長度可以為零。</span><span class="sxs-lookup"><span data-stu-id="3cf31-113">The length of *expression 2* may be zero.</span></span>  
  
-   <span data-ttu-id="3cf31-114">如果任何引數為 Null，則 REPLACENULL 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="3cf31-114">REPLACENULL returns a null result if any argument is null.</span></span>  
  
-   <span data-ttu-id="3cf31-115">任一參數都不支援 BLOB 資料行 (DT_TEXT、DT_NTEXT、DT_IMAGE)。</span><span class="sxs-lookup"><span data-stu-id="3cf31-115">BLOB columns (DT_TEXT, DT_NTEXT, DT_IMAGE) are not supported for either parameter.</span></span>  
  
-   <span data-ttu-id="3cf31-116">兩個運算式應該有相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="3cf31-116">The two expressions are expected to have the same return type.</span></span> <span data-ttu-id="3cf31-117">如果不相同，則函式嘗試將第二個運算式轉換成第一個運算式的傳回類型，如果資料類型不相容，這可能會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cf31-117">If they do not, the function attempts to cast the 2nd expression to the return type of the 1st expression, which may result in an error if the data types are incompatible.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="3cf31-118">運算式範例</span><span class="sxs-lookup"><span data-stu-id="3cf31-118">Expression Examples</span></span>  
 <span data-ttu-id="3cf31-119">下列範例會將資料庫資料行中的任何 NULL 值取代成字串 (1900-01-01)。</span><span class="sxs-lookup"><span data-stu-id="3cf31-119">The following example replaces any NULL value in a database column with a string (1900-01-01).</span></span> <span data-ttu-id="3cf31-120">在您要將 NULL 值取代成其他任何值的通用衍生資料行圖樣中，特別會使用此函式。</span><span class="sxs-lookup"><span data-stu-id="3cf31-120">This function is especially used in common Derived Column patterns where you want to replace NULL values with something else.</span></span>  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3cf31-121">下列範例會示範 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]的作法。</span><span class="sxs-lookup"><span data-stu-id="3cf31-121">The following example shows how it was done in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].</span></span>  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
