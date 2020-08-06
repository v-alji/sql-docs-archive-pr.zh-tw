---
title: 進階 Integration Services 運算式範例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb1e8dc6f9bffd22c917414f80f6ba9f257b25b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595218"
---
# <a name="examples-of-advanced-integration-services-expressions"></a><span data-ttu-id="2f493-102">進階 Integration Services 運算式範例</span><span class="sxs-lookup"><span data-stu-id="2f493-102">Examples of Advanced Integration Services Expressions</span></span>
  <span data-ttu-id="2f493-103">本節提供組合多個運算子和函數的進階運算式範例。</span><span class="sxs-lookup"><span data-stu-id="2f493-103">This section provides examples of advanced expressions that combine multiple operators and functions.</span></span> <span data-ttu-id="2f493-104">如果在優先順序條件約束或「條件式分割」轉換中使用運算式，則評估結果必須為布林。</span><span class="sxs-lookup"><span data-stu-id="2f493-104">If an expression is used in a precedence constraint or the Conditional Split transformation, it must evaluate to a Boolean.</span></span> <span data-ttu-id="2f493-105">不過，該條件約束不會套用至屬性運算式、變數、「衍生的資料行」轉換，或「For 迴圈」容器中使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="2f493-105">That restriction, however, does not apply to expressions used in property expressions, variables, the Derived Column transformation, or the For Loop container.</span></span>  
  
 <span data-ttu-id="2f493-106">下列範例使用 **AdventureWorks** 和 [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f493-106">The following examples use the **AdventureWorks** and the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="2f493-107">各範例代表其使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-107">Each example identifies the tables it uses.</span></span>  
  
## <a name="boolean-expressions"></a><span data-ttu-id="2f493-108">布林運算式</span><span class="sxs-lookup"><span data-stu-id="2f493-108">Boolean Expressions</span></span>  
  
-   <span data-ttu-id="2f493-109">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-109">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-110">運算式會評估 **SellStartDate** 資料行中的月份項目，而如果月份為六月或更晚的月份，則傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2f493-110">The expression evaluates the month entry in the **SellStartDate** column and returns TRUE if the month is June or later.</span></span>  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   <span data-ttu-id="2f493-111">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-111">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-112">運算式會評估 **ListPrice** 資料行除以 **StandardCost** 資料行的進位結果，而如果結果大於 1.5，則傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2f493-112">The expression evaluates the rounded result of dividing the **ListPrice** column by the **StandardCost** column, and returns TRUE if the result is greater than 1.5.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   <span data-ttu-id="2f493-113">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-113">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-114">如果三項運算的評估結果均為 TRUE，則運算式會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2f493-114">The expression returns TRUE if all three operations evaluate to TRUE.</span></span> <span data-ttu-id="2f493-115">如果 **Size** 資料行和 **BikeSize** 變數的資料類型不相容，則運算式需要明確轉換，如第二個範例所示。</span><span class="sxs-lookup"><span data-stu-id="2f493-115">If the **Size** column and the **BikeSize** variable have incompatible data types, the expression requires an explicit cast as shown the second example.</span></span> <span data-ttu-id="2f493-116">轉換為 DT_WSTR 包括字串長度。</span><span class="sxs-lookup"><span data-stu-id="2f493-116">The cast to DT_WSTR includes the length of the string.</span></span>  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   <span data-ttu-id="2f493-117">此範例使用 **CurrencyRate** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-117">This example uses the **CurrencyRate** table.</span></span> <span data-ttu-id="2f493-118">運算式會比較資料表中和變數的值。</span><span class="sxs-lookup"><span data-stu-id="2f493-118">The expression compares values in tables and variables.</span></span> <span data-ttu-id="2f493-119">如果 **FromCurrencyCode** 或 **ToCurrencyCode** 資料行中的項目等於變數值，且 **AverageRate** 中的值大於 **EndOfDayRate**中的值，則會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2f493-119">It returns TRUE if entries in the **FromCurrencyCode** or **ToCurrencyCode** columns are equal to variable values and if the value in **AverageRate** is greater that the value in **EndOfDayRate**.</span></span>  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   <span data-ttu-id="2f493-120">此範例使用 **Currency** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-120">This example uses the **Currency** table.</span></span> <span data-ttu-id="2f493-121">如果 **Name** 中的第一個字元不是 a 或 A，則運算式會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="2f493-121">The expression returns TRUE if the first character in the **Name** column is not a or A.</span></span>  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     <span data-ttu-id="2f493-122">下列運算式提供相同的結果，但更有效率，因為只會將一個字元轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="2f493-122">The following expression provides the same results, but it is more efficient because only one character is converted to uppercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a><span data-ttu-id="2f493-123">非布林運算式</span><span class="sxs-lookup"><span data-stu-id="2f493-123">Non-Boolean Expressions</span></span>  
 <span data-ttu-id="2f493-124">非布林運算式可用於「衍生的資料行」轉換、屬性運算式，以及「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="2f493-124">Non-Boolean expressions are used in the Derived Column transformation, property expressions, and the For Loop container.</span></span>  
  
-   <span data-ttu-id="2f493-125">這個範例使用 **Contact** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-125">This example uses the **Contact** table.</span></span> <span data-ttu-id="2f493-126">運算式會移除 **FirstName**、 **MiddleName**和 **LastName** 資料行中開頭和尾端的空格。</span><span class="sxs-lookup"><span data-stu-id="2f493-126">The expression removes leading and trailing spaces from the **FirstName**, **MiddleName**, and **LastName** columns.</span></span> <span data-ttu-id="2f493-127">如果不是 Null，則會擷取 **MiddleName** 資料行的第一個字母、串連中間的縮寫與 **FirstName** 和 **LastName**中的值，以及在各值之間插入適當的空格。</span><span class="sxs-lookup"><span data-stu-id="2f493-127">It extracts the first letter of the **MiddleName** column if it is not null, concatenates the middle initial and the values in **FirstName** and **LastName**, and inserts appropriate spaces between values.</span></span>  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   <span data-ttu-id="2f493-128">這個範例使用 **Contact** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-128">This example uses the **Contact** table.</span></span> <span data-ttu-id="2f493-129">運算式會驗證 **Salutation** 資料行中的項目。</span><span class="sxs-lookup"><span data-stu-id="2f493-129">The expression validates entries in the **Salutation** column.</span></span> <span data-ttu-id="2f493-130">它會傳回 **Salutation** 項目或空白字串。</span><span class="sxs-lookup"><span data-stu-id="2f493-130">It returns a **Salutation** entry or an empty string.</span></span>  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   <span data-ttu-id="2f493-131">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-131">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-132">運算式會將 **Color** 資料行中的第一個字元轉換成大寫，並將其餘字元轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="2f493-132">The expression converts the first character in the **Color** column to uppercase and converts remaining characters to lowercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   <span data-ttu-id="2f493-133">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-133">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-134">運算式會計算產品售出的月數，而且如果 **SellStartDate** 或 **SellEndDate** 資料行包含 NULL，則會傳回「Unknown」字串。</span><span class="sxs-lookup"><span data-stu-id="2f493-134">The expression calculates the number of months a product has been sold and returns the string "Unknown" if either the **SellStartDate** or the **SellEndDate** column contains NULL.</span></span>  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   <span data-ttu-id="2f493-135">這個範例使用 **Product** 資料表。</span><span class="sxs-lookup"><span data-stu-id="2f493-135">This example uses the **Product** table.</span></span> <span data-ttu-id="2f493-136">運算式會計算 **StandardCost** 資料行上的標記，並將結果進位至兩位有效位數。</span><span class="sxs-lookup"><span data-stu-id="2f493-136">The expression calculates the markup on the **StandardCost** column and rounds the result to a precision of two.</span></span> <span data-ttu-id="2f493-137">此結果會以百分比表示。</span><span class="sxs-lookup"><span data-stu-id="2f493-137">The result is presented as a percentage.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a><span data-ttu-id="2f493-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="2f493-138">Related Tasks</span></span>  
 [<span data-ttu-id="2f493-139">在資料流程元件中使用運算式</span><span class="sxs-lookup"><span data-stu-id="2f493-139">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="2f493-140">相關內容</span><span class="sxs-lookup"><span data-stu-id="2f493-140">Related Content</span></span>  
 <span data-ttu-id="2f493-141">pragmaticworks.com 上的技術文件： [SSIS 運算式小抄](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="2f493-141">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
