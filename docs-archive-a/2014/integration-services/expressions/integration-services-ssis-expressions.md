---
title: Integration Services (SSIS) 運算式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff0bd46034108537ebede7567b042997c94871ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701437"
---
# <a name="integration-services-ssis-expressions"></a><span data-ttu-id="b6acf-102">Integration Services (SSIS) 運算式</span><span class="sxs-lookup"><span data-stu-id="b6acf-102">Integration Services (SSIS) Expressions</span></span>
  <span data-ttu-id="b6acf-103">運算式是產生單一資料值的符號組合 (識別碼、常值、函數和運算子)。</span><span class="sxs-lookup"><span data-stu-id="b6acf-103">An expression is a combination of symbols-identifiers, literals, functions, and operators-that yields a single data value.</span></span> <span data-ttu-id="b6acf-104">簡單的運算式可以是單一常數、變數或函數。</span><span class="sxs-lookup"><span data-stu-id="b6acf-104">Simple expressions can be a single constant, variable, or function.</span></span> <span data-ttu-id="b6acf-105">通常運算式都比較複雜，更常使用多個運算子和函數，並參考多個資料行和變數。</span><span class="sxs-lookup"><span data-stu-id="b6acf-105">More frequently, expressions are complex, using multiple operators and functions and referencing multiple columns and variables.</span></span> <span data-ttu-id="b6acf-106">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，運算式可用於定義 CASE 陳述式的條件、建立和更新資料行中的值、指派值到變數、在執行階段更新或擴展屬性、定義優先順序條件約束中的條件約束和提供「For 迴圈」容器所使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="b6acf-106">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expressions can be used to define conditions for CASE statements, create and update values in data columns, assign values to variables, update or populate properties at run time, define constraints in precedence constraints, and provide the expressions used by the For Loop container.</span></span>  
  
 <span data-ttu-id="b6acf-107">運算式以運算式語言和運算式評估工具為基礎。</span><span class="sxs-lookup"><span data-stu-id="b6acf-107">Expressions are based on an expression language, and the expression evaluator.</span></span> <span data-ttu-id="b6acf-108">運算式評估工具會剖析運算式，並判斷運算式是否遵循運算式語言的規則。</span><span class="sxs-lookup"><span data-stu-id="b6acf-108">The expression evaluator parses the expression and determines whether the expression follows the rules of the expression language.</span></span> <span data-ttu-id="b6acf-109">如需有關運算式語法以及支援的常值和識別碼的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="b6acf-109">For more information about the expression syntax and supported literals and identifiers, see the following topics.</span></span>  
  
-   [<span data-ttu-id="b6acf-110">語法 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="b6acf-110">Syntax &#40;SSIS&#41;</span></span>](syntax-ssis.md)  
  
-   [<span data-ttu-id="b6acf-111">常值 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="b6acf-111">Literals &#40;SSIS&#41;</span></span>](numeric-string-and-boolean-literals.md)  
  
-   [<span data-ttu-id="b6acf-112">識別項 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="b6acf-112">Identifiers &#40;SSIS&#41;</span></span>](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a><span data-ttu-id="b6acf-113">使用運算式的元件</span><span class="sxs-lookup"><span data-stu-id="b6acf-113">Components that Use Expressions</span></span>  
 <span data-ttu-id="b6acf-114">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的下列元素可使用運算式：</span><span class="sxs-lookup"><span data-stu-id="b6acf-114">The following elements in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can use expressions:</span></span>  
  
-   <span data-ttu-id="b6acf-115">「條件式分割」轉換是以運算式為基礎，實作決策結構以將資料列導向不同的目的地。</span><span class="sxs-lookup"><span data-stu-id="b6acf-115">The Conditional Split transformation implements a decision structure based on expressions to direct data rows to different destinations.</span></span> <span data-ttu-id="b6acf-116">「條件式分割」轉換中使用的運算式必須評估為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6acf-116">Expressions used in a Conditional Split transformation must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b6acf-117">例如，可以將運算式 "Column1 > Column2" 中符合條件的資料列傳送至不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="b6acf-117">For example, rows that meet the condition in the expression "Column1 > Column2" can be routed to a separate output.</span></span>  
  
-   <span data-ttu-id="b6acf-118">「衍生的資料行」轉換會利用透過使用擴展資料流程中新資料行或更新現有資料行之運算式所建立的值。</span><span class="sxs-lookup"><span data-stu-id="b6acf-118">The Derived Column transformation uses values created by using expressions either to populate new columns in a data flow, or to update existing columns.</span></span> <span data-ttu-id="b6acf-119">例如，運算式 Column1 + " ABC" 可用於更新值或建立具有串連字串的新值。</span><span class="sxs-lookup"><span data-stu-id="b6acf-119">For example, the expression Column1 + " ABC" can be used to update a value or to create a new value with the concatenated string.</span></span>  
  
-   <span data-ttu-id="b6acf-120">變數會使用運算式來設定其值。</span><span class="sxs-lookup"><span data-stu-id="b6acf-120">Variables use an expression to set their value.</span></span> <span data-ttu-id="b6acf-121">例如，GETDATE() 會將變數值設為目前的日期。</span><span class="sxs-lookup"><span data-stu-id="b6acf-121">For example, GETDATE() sets the value of the variable to the current date.</span></span>  
  
-   <span data-ttu-id="b6acf-122">優先順序條件約束可使用運算式，指定決定受條件約束的工作或封裝中的容器是否執行的條件。</span><span class="sxs-lookup"><span data-stu-id="b6acf-122">Precedence constraints can use expressions to specify the conditions that determine whether the constrained task or container in a package runs.</span></span> <span data-ttu-id="b6acf-123">優先順序條件約束中使用的運算式必須評估為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6acf-123">Expressions used in a precedence constraint must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b6acf-124">例如，運算式 \@A > \@B 將兩個使用者定義變數進行比較，以決定受條件約束的工作是否執行。</span><span class="sxs-lookup"><span data-stu-id="b6acf-124">For example, the expression \@A > \@B compares two user-defined variables to determine whether the constrained task runs.</span></span>  
  
-   <span data-ttu-id="b6acf-125">「For 迴圈」容器可使用運算式建立迴圈結果使用的初始化、評估和累加陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6acf-125">The For Loop container can use expressions to build the initialization, evaluation, and the incrementing statements that the looping structure uses.</span></span> <span data-ttu-id="b6acf-126">例如，運算式 \@Counter = 1 會初始化迴圈計數器。</span><span class="sxs-lookup"><span data-stu-id="b6acf-126">For example, the expression \@Counter = 1 initializes the loop counter.</span></span>  
  
 <span data-ttu-id="b6acf-127">運算式還可用於更新封裝、容器 (例如「For 迴圈」和「Foreach 迴圈」)、工作、封裝和專案層級之連接管理員、記錄提供者和 Foreach 列舉值的屬性值。</span><span class="sxs-lookup"><span data-stu-id="b6acf-127">Expressions can also be used to update the values of properties of packages, containers such as the For Loop and Foreach Loop, tasks, package and project level connection managers, log providers, and Foreach enumerators.</span></span> <span data-ttu-id="b6acf-128">例如，使用屬性運算式，可將字串 "Localhost.AdventureWorks" 指派到「執行 SQL」工作的 ConnectionName 屬性。</span><span class="sxs-lookup"><span data-stu-id="b6acf-128">For example, using a property expression, the string "Localhost.AdventureWorks" can be assigned to the ConnectionName property of the Execute SQL task.</span></span> <span data-ttu-id="b6acf-129">如需詳細資訊，請參閱 [在封裝中使用屬性運算式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="b6acf-129">For more information, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="icon-markers-for-expressions"></a><span data-ttu-id="b6acf-130">運算式的圖示標記</span><span class="sxs-lookup"><span data-stu-id="b6acf-130">Icon Markers for Expressions</span></span>  
 <span data-ttu-id="b6acf-131">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，已經設定運算式的連接管理員、變數和工作旁，會顯示一個特殊的圖示標記。</span><span class="sxs-lookup"><span data-stu-id="b6acf-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a special icon marker displays next to connection managers, variables, and tasks that have expressions set on them.</span></span> <span data-ttu-id="b6acf-132">所有支援運算式的 SSIS 物件，都可以使用 **HasExpressions** 屬性，但不包括變數。</span><span class="sxs-lookup"><span data-stu-id="b6acf-132">The **HasExpressions** property is available on all SSIS objects that support expresions, with the exception of variables.</span></span> <span data-ttu-id="b6acf-133">這個屬性可讓您輕易地識別哪些物件具有運算式。</span><span class="sxs-lookup"><span data-stu-id="b6acf-133">The property enables you to easily identy which objects have expressions.</span></span>  
  
## <a name="expression-builder"></a><span data-ttu-id="b6acf-134">運算式產生器</span><span class="sxs-lookup"><span data-stu-id="b6acf-134">Expression Builder</span></span>  
 <span data-ttu-id="b6acf-135">運算式產生器是可以用於建立運算式的圖形工具。</span><span class="sxs-lookup"><span data-stu-id="b6acf-135">The expression builder is a graphical tool for building expressions.</span></span> <span data-ttu-id="b6acf-136">其位於 **[條件式分割轉換編輯器]** 、 **[衍生的資料行轉換編輯器]** 對話方塊及 **[運算式產生器]** 對話方塊中，是可以用於建立運算式的圖形工具。</span><span class="sxs-lookup"><span data-stu-id="b6acf-136">It is available in the **Conditional Split Transformation Editor**, **Derived Column Transformation Editor** dialog boxes, and in the **Expression Builder** dialog box, is a graphical tool for building expressions.</span></span>  
  
 <span data-ttu-id="b6acf-137">運算式產生器會提供包含封裝特定之元素的資料夾和包含運算式語言所提供之函數、類型轉換和運算子的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6acf-137">The expression builder provides folders that contain package-specific elements, and folders that contain the functions, type casts, and operators that the expression language provides.</span></span> <span data-ttu-id="b6acf-138">封裝特定的元素包括系統變數和使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="b6acf-138">The package-specific elements include system variables and user-defined variables.</span></span> <span data-ttu-id="b6acf-139">在 **[條件式分割轉換編輯器]** 和 **[衍生的資料行轉換編輯器]** 對話方塊中，還可以檢視資料行。</span><span class="sxs-lookup"><span data-stu-id="b6acf-139">In the **Conditional Split Transformation Editor** and **Derived Column Transformation Editor** dialog boxes, you can also view data columns.</span></span> <span data-ttu-id="b6acf-140">若要建立轉換的運算式，可以將項目從資料夾拖曳至 **[條件]** 或 **[運算式]** 資料行，或直接在資料行中輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="b6acf-140">To build expressions for the transformations, you can drag items from the folders to the **Condition** or **Expression** column or you can type the expression directly in the column.</span></span> <span data-ttu-id="b6acf-141">運算式產生器會自動加入必要的語法元素，例如變數名稱的前置詞 \@。</span><span class="sxs-lookup"><span data-stu-id="b6acf-141">The expression builder automatically adds needed syntax elements such as the \@ prefix on variable names.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6acf-142">使用者定義變數和系統變數的名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b6acf-142">The names of user-defined and system variables are case-sensitive.</span></span>  
  
 <span data-ttu-id="b6acf-143">變數有範圍，並且運算式產生器中的 **[Variables]** 資料夾只會列出處於範圍中的可用變數。</span><span class="sxs-lookup"><span data-stu-id="b6acf-143">Variables have scope, and the **Variables** folder in the expression builder lists only variables that are in scope and available to use.</span></span> <span data-ttu-id="b6acf-144">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b6acf-144">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b6acf-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="b6acf-145">Related Tasks</span></span>  
 [<span data-ttu-id="b6acf-146">在資料流程元件中使用運算式</span><span class="sxs-lookup"><span data-stu-id="b6acf-146">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="b6acf-147">相關內容</span><span class="sxs-lookup"><span data-stu-id="b6acf-147">Related Content</span></span>  
 <span data-ttu-id="b6acf-148">social.technet.microsoft.com 上的技術文件： [SSIS 運算式範例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="b6acf-148">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6acf-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6acf-149">See Also</span></span>  
 [<span data-ttu-id="b6acf-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="b6acf-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
