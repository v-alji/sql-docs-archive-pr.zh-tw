---
title: 快速監看式對話方塊
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 48e4bda558b75bec0c81815c90feff9d6500a803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606203"
---
# <a name="quickwatch-dialog-box"></a><span data-ttu-id="c81bf-102">快速監看式對話方塊</span><span class="sxs-lookup"><span data-stu-id="c81bf-102">QuickWatch Dialog Box</span></span>
  <span data-ttu-id="c81bf-103">使用 [快速監看式] 對話方塊可在偵錯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼時，快速檢視一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式的資料類型和值，例如變數或參數。</span><span class="sxs-lookup"><span data-stu-id="c81bf-103">Use the **QuickWatch** dialog box to quickly view the data type and value of one [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, such as a variable or parameter, when you are debugging [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="c81bf-104">若要監看多個運算式，您也可以將此運算式加入到 [監看式]  視窗。</span><span class="sxs-lookup"><span data-stu-id="c81bf-104">To watch multiple expressions, you can also add the expression to a **Watch** window.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="c81bf-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="c81bf-105">Task List</span></span>  
 <span data-ttu-id="c81bf-106">**存取快速監看式對話方塊**</span><span class="sxs-lookup"><span data-stu-id="c81bf-106">**To access the QuickWatch dialog box**</span></span>  
  
-   <span data-ttu-id="c81bf-107">按一下 [偵錯]  功能表上的 [快速監看式]  。</span><span class="sxs-lookup"><span data-stu-id="c81bf-107">On the **Debug** menu, click **QuickWatch**.</span></span>  
  
 <span data-ttu-id="c81bf-108">**檢視有關運算式的資訊**</span><span class="sxs-lookup"><span data-stu-id="c81bf-108">**To view the information about an expression**</span></span>  
  
1.  <span data-ttu-id="c81bf-109">在 [運算式]  中，輸入或選取您想要的運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-109">In the **Expression** list box, type or select the expression that you want.</span></span> <span data-ttu-id="c81bf-110">以下為支援的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式：</span><span class="sxs-lookup"><span data-stu-id="c81bf-110">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions are supported:</span></span>  
  
    -   <span data-ttu-id="c81bf-111">變數。</span><span class="sxs-lookup"><span data-stu-id="c81bf-111">Variables.</span></span>  
  
    -   <span data-ttu-id="c81bf-112">參數。</span><span class="sxs-lookup"><span data-stu-id="c81bf-112">Parameters.</span></span>  
  
    -   <span data-ttu-id="c81bf-113">名稱開頭為 @@ 的系統函式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-113">System functions whose name starts with @@.</span></span>  
  
    -   <span data-ttu-id="c81bf-114">透過將運算子套用至一或多個變數、參數或系統函式 (例如 @IntegerCounter + 1 或 FirstName + LastName) 的方式建立的運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-114">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
    -   <span data-ttu-id="c81bf-115">傳回單一值的 Transact-SQL 陳述式，例如 SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="c81bf-115">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
2.  <span data-ttu-id="c81bf-116">按一下 [重新評估]  。</span><span class="sxs-lookup"><span data-stu-id="c81bf-116">Click **Reevaluate**.</span></span>  
  
 <span data-ttu-id="c81bf-117">**將快速監看式運算式加入至監看式視窗**</span><span class="sxs-lookup"><span data-stu-id="c81bf-117">**To add the QuickWatch expression to a Watch window**</span></span>  
  
-   <span data-ttu-id="c81bf-118">按一下 [加入監看式]  。</span><span class="sxs-lookup"><span data-stu-id="c81bf-118">Click **Add Watch**.</span></span>  
  
 <span data-ttu-id="c81bf-119">**變更快速監看式運算式的值**</span><span class="sxs-lookup"><span data-stu-id="c81bf-119">**To change the value of the QuickWatch expression**</span></span>  
  
-   <span data-ttu-id="c81bf-120">以滑鼠右鍵按一下運算式，然後選取 [編輯值]  。</span><span class="sxs-lookup"><span data-stu-id="c81bf-120">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c81bf-121">選項。</span><span class="sxs-lookup"><span data-stu-id="c81bf-121">Options</span></span>  
 <span data-ttu-id="c81bf-122">**運算式清單**</span><span class="sxs-lookup"><span data-stu-id="c81bf-122">**Expression list**</span></span>  
 <span data-ttu-id="c81bf-123">顯示目前選取的運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-123">Displays the currently selected expression.</span></span> <span data-ttu-id="c81bf-124">此下拉式清單包含您可以選擇顯示的一組運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-124">The drop-down list contains a set of expressions that you can select to display.</span></span> <span data-ttu-id="c81bf-125">此清單中的運算式就是目前在 [呼叫堆疊]  視窗內選取之堆疊框架範圍內提供的運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-125">The expressions in the list are those available in the scope of the stack frame that is currently selected in the **Call Stack** window.</span></span> <span data-ttu-id="c81bf-126">若要顯示不同的運算式，請輸入運算式或是從清單中選取。</span><span class="sxs-lookup"><span data-stu-id="c81bf-126">To display a different expression, either enter the expression or select it from list.</span></span> <span data-ttu-id="c81bf-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具支援以下運算式：名稱以 @@ 開頭的變數、參數和系統函式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports the following expressions: variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="c81bf-128">**值格線**</span><span class="sxs-lookup"><span data-stu-id="c81bf-128">**Value grid**</span></span>  
 <span data-ttu-id="c81bf-129">顯示目前所監看之運算式的屬性。</span><span class="sxs-lookup"><span data-stu-id="c81bf-129">Displays the properties of the expression that is currently being watched.</span></span>  
  
 <span data-ttu-id="c81bf-130">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c81bf-130">**Name**</span></span>  
 <span data-ttu-id="c81bf-131">正在監看的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="c81bf-131">Is the [!INCLUDE[tsql](../../includes/tsql-md.md)] expression being watched.</span></span>  
  
 <span data-ttu-id="c81bf-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c81bf-132">**Value**</span></span>  
 <span data-ttu-id="c81bf-133">顯示目前指派給運算式的值。</span><span class="sxs-lookup"><span data-stu-id="c81bf-133">Displays the value that is currently assigned to the expression.</span></span> <span data-ttu-id="c81bf-134">當運算式目前沒有任何值時會顯示空白。</span><span class="sxs-lookup"><span data-stu-id="c81bf-134">A blank is displayed when the expression currently has no value.</span></span>  
  
 <span data-ttu-id="c81bf-135">如果運算式的長度超過 **[值]** 資料行的寬度，當您將指標放在該運算式的 **[值]** 資料格上方時，工具提示會顯示完整的值。</span><span class="sxs-lookup"><span data-stu-id="c81bf-135">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="c81bf-136">**[值]** 資料格內的放大鏡圖示表示可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="c81bf-136">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="c81bf-137">在此清單中，您可以指定 **[文字視覺化檢視]** 、 **[XML 視覺化檢視]** 或 **[HTML 視覺化檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="c81bf-137">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="c81bf-138">若要啟動偵錯工具視覺化檢視，請按一下放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="c81bf-138">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="c81bf-139">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具會開啟一個對話方塊，其中會以對資料類型適合的格式顯示資料。</span><span class="sxs-lookup"><span data-stu-id="c81bf-139">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="c81bf-140">**型別**</span><span class="sxs-lookup"><span data-stu-id="c81bf-140">**Type**</span></span>  
 <span data-ttu-id="c81bf-141">顯示此運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c81bf-141">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81bf-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c81bf-142">See Also</span></span>  
 <span data-ttu-id="c81bf-143">[Transact-SQL 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="c81bf-143">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="c81bf-144">[Transact-SQL 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="c81bf-144">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="c81bf-145">[監看式視窗](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="c81bf-145">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="c81bf-146">[本機視窗](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="c81bf-146">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="c81bf-147">[呼叫堆疊視窗](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="c81bf-147">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 [<span data-ttu-id="c81bf-148">運算式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c81bf-148">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
