---
title: 衍生資料行轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bbdc46f2e67b1b859fcfa446c584373cfbeca0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585512"
---
# <a name="derived-column-transformation"></a><span data-ttu-id="3c9ba-102">衍生的資料行轉換</span><span class="sxs-lookup"><span data-stu-id="3c9ba-102">Derived Column Transformation</span></span>
  <span data-ttu-id="3c9ba-103">「衍生的資料行」轉換會將運算式套用至轉換輸入資料行，藉此建立新的資料行值。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-103">The Derived Column transformation creates new column values by applying expressions to transformation input columns.</span></span> <span data-ttu-id="3c9ba-104">運算式可包含來自轉換輸入之變數、函數、運算子和資料行的任意組合。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-104">An expression can contain any combination of variables, functions, operators, and columns from the transformation input.</span></span> <span data-ttu-id="3c9ba-105">結果可加入做為新的資料行，或插入現有資料行做為取代值。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-105">The result can be added as a new column or inserted into an existing column as a replacement value.</span></span> <span data-ttu-id="3c9ba-106">「衍生的資料行」轉換可定義多個衍生的資料行，且任何變數或輸入資料行都可在多個運算式中出現。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-106">The Derived Column transformation can define multiple derived columns, and any variable or input columns can appear in multiple expressions.</span></span>  
  
 <span data-ttu-id="3c9ba-107">您可以使用此轉換執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3c9ba-107">You can use this transformation to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3c9ba-108">將不同資料行的資料串連至衍生的資料行中。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-108">Concatenate data from different columns into a derived column.</span></span> <span data-ttu-id="3c9ba-109">例如，您可以使用運算式 **，將** FirstName **和** LastName **資料行的值結合到名為**FullName `FirstName + " " + LastName`的單一衍生資料行中。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-109">For example, you can combine values from the **FirstName** and **LastName** columns into a single derived column named **FullName**, by using the expression `FirstName + " " + LastName`.</span></span>  
  
-   <span data-ttu-id="3c9ba-110">使用如 SUBSTRING 的函數從字串資料擷取字元，然後將結果儲存到衍生的資料行中。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-110">Extract characters from string data by using functions such as SUBSTRING, and then store the result in a derived column.</span></span> <span data-ttu-id="3c9ba-111">例如，您可以使用運算式 **，從** FirstName `SUBSTRING(FirstName,1,1)`資料行中擷取人員的名字縮寫。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-111">For example, you can extract a person's initial from the **FirstName** column, by using the expression `SUBSTRING(FirstName,1,1)`.</span></span>  
  
-   <span data-ttu-id="3c9ba-112">套用數學函數至數值資料，然後將結果儲存到衍生的資料行中。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-112">Apply mathematical functions to numeric data and store the result in a derived column.</span></span> <span data-ttu-id="3c9ba-113">例如，您可以使用運算式 **，將數值資料行**SalesTax `ROUND(SalesTax, 2)`的長度和有效位數變更為含有兩位小數的數字。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-113">For example, you can change the length and precision of a numeric column, **SalesTax**, to a number with two decimal places, by using the expression `ROUND(SalesTax, 2)`.</span></span>  
  
-   <span data-ttu-id="3c9ba-114">建立比較輸入資料行和變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-114">Create expressions that compare input columns and variables.</span></span> <span data-ttu-id="3c9ba-115">例如，您可以使用運算式 **，對照** ProductVersion **資料行中的資料比較變數**Version **，並根據比較結果，使用** Version **或**ProductVersion `ProductVersion == @Version? ProductVersion : @Version`的值。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-115">For example, you can compare the variable **Version** against the data in the column **ProductVersion**, and depending on the comparison result, use the value of either **Version** or **ProductVersion**, by using the expression `ProductVersion == @Version? ProductVersion : @Version`.</span></span>  
  
-   <span data-ttu-id="3c9ba-116">擷取日期時間值的部分。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-116">Extract parts of a datetime value.</span></span> <span data-ttu-id="3c9ba-117">例如，您可以使用運算式 `DATEPART("year",GETDATE())`，利用 GETDATE 和 DATEPART 函數擷取目前的年份。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-117">For example, you can use the GETDATE and DATEPART functions to extract the current year, by using the expression `DATEPART("year",GETDATE())`.</span></span>  
  
-   <span data-ttu-id="3c9ba-118">使用運算式將日期字串轉換成特定格式。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-118">Convert date strings to a specific format using an expression.</span></span>  
  
## <a name="configuration-of-the-derived-column-transformation"></a><span data-ttu-id="3c9ba-119">設定衍生資料行轉換</span><span class="sxs-lookup"><span data-stu-id="3c9ba-119">Configuration of the Derived Column Transformation</span></span>  
 <span data-ttu-id="3c9ba-120">您可以利用下列方式設定「衍生的資料行」轉換：</span><span class="sxs-lookup"><span data-stu-id="3c9ba-120">You can configure the Derived column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="3c9ba-121">為每一個要變更的輸入資料行或新資料行提供運算式。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-121">Provide an expression for each input column or new column that will be changed.</span></span> <span data-ttu-id="3c9ba-122">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)為止。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c9ba-123">如果運算式參考「衍生的資料行」轉換所覆寫的輸入資料行，則運算式會使用資料行的原始值，而非衍生的值。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-123">If an expression references an input column that is overwritten by the Derived Column transformation, the expression uses the original value of the column, not the derived value.</span></span>  
  
-   <span data-ttu-id="3c9ba-124">若要將結果加入新資料行，並且資料類型是 `string`，請指定字碼頁。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-124">If adding results to new columns and the data type is `string`, specify a code page.</span></span> <span data-ttu-id="3c9ba-125">如需詳細資訊，請參閱 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-125">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="3c9ba-126">衍生的資料行轉換包括 FriendlyExpression 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-126">The Derived Column transformation includes the FriendlyExpression custom property.</span></span> <span data-ttu-id="3c9ba-127">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-127">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="3c9ba-128">如需詳細資訊，請參閱 [在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和 [轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-128">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="3c9ba-129">這個轉換有一個輸入、一個規則輸出及一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-129">This transformation has one input, one regular output, and one error output.</span></span>  
  
 <span data-ttu-id="3c9ba-130">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-130">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3c9ba-131">如需可在 [衍生的資料行轉換編輯器] \*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱 [衍生的資料行轉換編輯器](../../derived-column-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-131">For more information about the properties that you can set in the **Derived Column Transformation Editor** dialog box, see [Derived Column Transformation Editor](../../derived-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="3c9ba-132">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-132">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="3c9ba-133">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="3c9ba-133">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3c9ba-134">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3c9ba-134">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="3c9ba-135">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3c9ba-135">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="3c9ba-136">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="3c9ba-136">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3c9ba-137">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="3c9ba-137">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3c9ba-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="3c9ba-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3c9ba-139">使用衍生的資料行轉換來衍生資料行值</span><span class="sxs-lookup"><span data-stu-id="3c9ba-139">Derive Column Values by Using the Derived Column Transformation</span></span>](derived-column-transformation.md)  
  
## <a name="related-content"></a><span data-ttu-id="3c9ba-140">相關內容</span><span class="sxs-lookup"><span data-stu-id="3c9ba-140">Related Content</span></span>  
 <span data-ttu-id="3c9ba-141">social.technet.microsoft.com 上的技術文件： [SSIS 運算式範例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="3c9ba-141">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
 <span data-ttu-id="3c9ba-142">Blog，[如何使用 SSIS 分割資料行資料](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html)。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-142">Blog, [How to Split Column Data using SSIS](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html).</span></span>  
  
  
