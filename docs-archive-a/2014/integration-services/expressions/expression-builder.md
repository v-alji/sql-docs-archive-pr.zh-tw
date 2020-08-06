---
title: 運算式產生器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 812b0d744d415d5419d54176359ddcd5837dd206
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595216"
---
# <a name="expression-builder"></a><span data-ttu-id="f3310-102">運算式產生器</span><span class="sxs-lookup"><span data-stu-id="f3310-102">Expression Builder</span></span>
  <span data-ttu-id="f3310-103">使用 [運算式產生器]  對話方塊，即可藉由使用圖形化使用者介面列出變數以及提供函數的內建參考、類型轉換和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式語言所包含的運算子，來建立和編輯屬性運算式或撰寫可設定變數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="f3310-103">Use the **Expression Builder** dialog box to create and edit a property expression or write the expression that sets the value of a variable using a graphical user interface that lists variables and provides a built-in reference to the functions, type casts, and operators that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language includes.</span></span>  
  
 <span data-ttu-id="f3310-104">屬性運算式是指派給屬性的運算式。</span><span class="sxs-lookup"><span data-stu-id="f3310-104">A property expression is an expression that is assigned to a property.</span></span> <span data-ttu-id="f3310-105">在評估運算式時，會動態更新屬性以使用運算式的評估結果。</span><span class="sxs-lookup"><span data-stu-id="f3310-105">When the expression is evaluated, the property is dynamically updated to use the evaluation result of the expression.</span></span> <span data-ttu-id="f3310-106">同樣地，變數中所使用的運算式可使運算式的評估結果更新變數值。</span><span class="sxs-lookup"><span data-stu-id="f3310-106">Likewise, an expression that is used in a variable enables the variable value to be updated with the evaluation result of the expression.</span></span>  
  
 <span data-ttu-id="f3310-107">有許多使用運算式的方法。</span><span class="sxs-lookup"><span data-stu-id="f3310-107">There are many ways to use expressions:</span></span>  
  
-   <span data-ttu-id="f3310-108">**工作** 透過插入儲存在變數中的電子郵件地址，來更新「傳送郵件」工作所使用的「收件者」欄位；透過串連如 "Sales for:" 字串與 GETDATE 函數傳回的目前日期，來更新「主旨」欄位。</span><span class="sxs-lookup"><span data-stu-id="f3310-108">**Tasks** Update the To line that a Send Mail task uses by inserting an e-mail address that is stored in a variable; or update the Subject line by concatenating a string such as "Sales for: " and the current date returned by the GETDATE function.</span></span>  
  
-   <span data-ttu-id="f3310-109">**變數** 使用像 `DATEPART("mm",GETDATE())`之類的運算式來將變數的值設定為目前的月份；或是使用運算式 `"Today's date is " + (DT_WSTR,30)(GETDATE())`來串連字串常值和目前的日期，以設定字串值。</span><span class="sxs-lookup"><span data-stu-id="f3310-109">**Variables** Set the value of a variable to the current month by using an expression like `DATEPART("mm",GETDATE())`; or set the value of a string by concatenating the string literal and the current date by using the expression `"Today's date is " + (DT_WSTR,30)(GETDATE())`.</span></span>  
  
-   <span data-ttu-id="f3310-110">**連接管理員** 使用含有不同字碼頁識別碼的變數來設定一般檔案連接管理員的字碼頁；或是在運算式中輸入如 3 的正整數，以指定資料檔中要跳過的資料列數。</span><span class="sxs-lookup"><span data-stu-id="f3310-110">**Connection Managers** Set the code page of a Flat File connection manager by using a variable that contains a different code page identifier; or specify the number of rows in the data file to skip by entering a positive integer like 3 in the expression.</span></span>  
  
 <span data-ttu-id="f3310-111">若要深入了解屬性運算式以及撰寫運算式，請參閱[在封裝中使用屬性運算式](use-property-expressions-in-packages.md)和 [Integration Services &#40;SSIS&#41; 運算式](integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f3310-111">To learn more about property expressions and writing expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md) and [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3310-112">選項。</span><span class="sxs-lookup"><span data-stu-id="f3310-112">Options</span></span>  
  
|<span data-ttu-id="f3310-113">詞彙</span><span class="sxs-lookup"><span data-stu-id="f3310-113">Term</span></span>|<span data-ttu-id="f3310-114">定義</span><span class="sxs-lookup"><span data-stu-id="f3310-114">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f3310-115">**變數**</span><span class="sxs-lookup"><span data-stu-id="f3310-115">**Variables**</span></span>|<span data-ttu-id="f3310-116">展開 **[變數]** 資料夾，然後將變數拖曳至 **[運算式]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="f3310-116">Expand the **Variables** folder and drag variables to the **Expression** box.</span></span>|  
|<span data-ttu-id="f3310-117">**數學函式**</span><span class="sxs-lookup"><span data-stu-id="f3310-117">**Mathematical Functions**</span></span><br /><br /> <span data-ttu-id="f3310-118">**字串函式**</span><span class="sxs-lookup"><span data-stu-id="f3310-118">**String Functions**</span></span><br /><br /> <span data-ttu-id="f3310-119">**日期/時間函數**</span><span class="sxs-lookup"><span data-stu-id="f3310-119">**Date/Time Functions**</span></span><br /><br /> <span data-ttu-id="f3310-120">**NULL 函數**</span><span class="sxs-lookup"><span data-stu-id="f3310-120">**NULL Functions**</span></span><br /><br /> <span data-ttu-id="f3310-121">**類型轉換**</span><span class="sxs-lookup"><span data-stu-id="f3310-121">**Type Casts**</span></span><br /><br /> <span data-ttu-id="f3310-122">**運算子**</span><span class="sxs-lookup"><span data-stu-id="f3310-122">**Operators**</span></span>|<span data-ttu-id="f3310-123">展開資料夾，然後將函數、類型轉換和運算子拖曳至 **[運算式]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="f3310-123">Expand the folders and drag functions, type casts, and operators to the **Expression** box.</span></span>|  
|<span data-ttu-id="f3310-124">**運算式**</span><span class="sxs-lookup"><span data-stu-id="f3310-124">**Expression**</span></span>|<span data-ttu-id="f3310-125">編輯或輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="f3310-125">Edit or type an expression.\`</span></span>|  
|<span data-ttu-id="f3310-126">**評估值**</span><span class="sxs-lookup"><span data-stu-id="f3310-126">**Evaluated value**</span></span>|<span data-ttu-id="f3310-127">列出運算式的評估結果。</span><span class="sxs-lookup"><span data-stu-id="f3310-127">Lists the evaluation result of the expression.</span></span>|  
|<span data-ttu-id="f3310-128">**評估運算式**</span><span class="sxs-lookup"><span data-stu-id="f3310-128">**Evaluate Expression**</span></span>|<span data-ttu-id="f3310-129">按一下 **[評估運算式]** ，即可檢視運算式的評估結果。</span><span class="sxs-lookup"><span data-stu-id="f3310-129">Click **Evaluate Expression** to view the evaluation result of the expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3310-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3310-130">See Also</span></span>  
 <span data-ttu-id="f3310-131">[運算式頁面](expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="f3310-131">[Expressions Page](expressions-page.md) </span></span>  
 <span data-ttu-id="f3310-132">[屬性運算式編輯器](property-expressions-editor.md) </span><span class="sxs-lookup"><span data-stu-id="f3310-132">[Property Expressions Editor](property-expressions-editor.md) </span></span>  
 <span data-ttu-id="f3310-133">[Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="f3310-133">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="f3310-134">系統變數</span><span class="sxs-lookup"><span data-stu-id="f3310-134">System Variables</span></span>](../system-variables.md)  
  
  
