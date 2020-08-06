---
title: 監看式視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: rothja
ms.author: jroth
ms.openlocfilehash: c2a3db9b095902fcb5620af91fb86d80f773d606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598262"
---
# <a name="watch-window"></a><span data-ttu-id="4bd63-102">監看式視窗</span><span class="sxs-lookup"><span data-stu-id="4bd63-102">Watch Window</span></span>
  <span data-ttu-id="4bd63-103">**[監看式]** 視窗會顯示有關您已選取之運算式的資訊。</span><span class="sxs-lookup"><span data-stu-id="4bd63-103">The **Watch** window displays information about the expressions that you have selected.</span></span> <span data-ttu-id="4bd63-104">最多可以有四個監看式視窗： **Watch 1**、 **Watch 2、Watch 3**和 **Watch 4**。</span><span class="sxs-lookup"><span data-stu-id="4bd63-104">There can be up to four watch windows: **Watch 1**, **Watch 2, Watch 3**, and **Watch 4**.</span></span> <span data-ttu-id="4bd63-105">運算式會在 **[呼叫堆疊]** 視窗內選取的目前呼叫堆疊框架範圍內評估。</span><span class="sxs-lookup"><span data-stu-id="4bd63-105">The expressions are evaluated within the scope of the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="4bd63-106">您必須在偵錯模式下，才能監看變數和運算式。</span><span class="sxs-lookup"><span data-stu-id="4bd63-106">You must be in debug mode to watch variables and expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="4bd63-107">工作清單</span><span class="sxs-lookup"><span data-stu-id="4bd63-107">Task List</span></span>  
 <span data-ttu-id="4bd63-108">**存取監看式視窗**</span><span class="sxs-lookup"><span data-stu-id="4bd63-108">**To access the Watch windows**</span></span>  
  
-   <span data-ttu-id="4bd63-109">在 **[偵錯]** 功能表上，按一下 **[視窗]** ，再按一下 **[監看式]** ，然後按一下 **Watch 1**、 **Watch 2、Watch 3**或 **Watch 4**。</span><span class="sxs-lookup"><span data-stu-id="4bd63-109">On the **Debug** menu, click **Windows**, click **Watch**, and then click **Watch 1**, **Watch 2, Watch 3**, or **Watch 4**.</span></span>  
  
 <span data-ttu-id="4bd63-110">**變更運算式的值**</span><span class="sxs-lookup"><span data-stu-id="4bd63-110">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="4bd63-111">以滑鼠右鍵按一下運算式，然後選取 [編輯值]  。</span><span class="sxs-lookup"><span data-stu-id="4bd63-111">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="4bd63-112">資料行</span><span class="sxs-lookup"><span data-stu-id="4bd63-112">Columns</span></span>  
 <span data-ttu-id="4bd63-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4bd63-113">**Name**</span></span>  
 <span data-ttu-id="4bd63-114">為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具所列出的運算式。</span><span class="sxs-lookup"><span data-stu-id="4bd63-114">Are the expressions that are listed by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="4bd63-115">以下為支援的運算式：</span><span class="sxs-lookup"><span data-stu-id="4bd63-115">The following expressions are supported:</span></span>  
  
-   <span data-ttu-id="4bd63-116">變數。</span><span class="sxs-lookup"><span data-stu-id="4bd63-116">Variables.</span></span>  
  
-   <span data-ttu-id="4bd63-117">參數。</span><span class="sxs-lookup"><span data-stu-id="4bd63-117">Parameters.</span></span>  
  
-   <span data-ttu-id="4bd63-118">名稱開頭為 @@ 的系統函式。</span><span class="sxs-lookup"><span data-stu-id="4bd63-118">System functions whose name starts with @@.</span></span>  
  
-   <span data-ttu-id="4bd63-119">透過將運算子套用至一或多個變數、參數或系統函式 (例如 @IntegerCounter + 1 或 FirstName + LastName) 的方式建立的運算式。</span><span class="sxs-lookup"><span data-stu-id="4bd63-119">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
-   <span data-ttu-id="4bd63-120">傳回單一值的 Transact-SQL 陳述式，例如 SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="4bd63-120">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="4bd63-121">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="4bd63-121">**Value**</span></span>  
 <span data-ttu-id="4bd63-122">顯示當 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具評估 [名稱]  內指定的運算式以後所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4bd63-122">Displays the value that is returned after the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger evaluates the expression specified in **Name**.</span></span>  
  
 <span data-ttu-id="4bd63-123">如果運算式的長度超過 **[值]** 資料行的寬度，當您將指標放在該運算式的 **[值]** 資料格上方時，工具提示會顯示完整的值。</span><span class="sxs-lookup"><span data-stu-id="4bd63-123">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="4bd63-124">**[值]** 資料格內的放大鏡圖示表示可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="4bd63-124">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="4bd63-125">在此清單中，您可以指定 **[文字視覺化檢視]** 、 **[XML 視覺化檢視]** 或 **[HTML 視覺化檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="4bd63-125">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="4bd63-126">若要啟動偵錯工具視覺化檢視，請按一下放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="4bd63-126">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="4bd63-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具會開啟一個對話方塊，其中會以對資料類型適合的格式顯示資料。</span><span class="sxs-lookup"><span data-stu-id="4bd63-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="4bd63-128">**型別**</span><span class="sxs-lookup"><span data-stu-id="4bd63-128">**Type**</span></span>  
 <span data-ttu-id="4bd63-129">顯示此運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bd63-129">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd63-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd63-130">See Also</span></span>  
 <span data-ttu-id="4bd63-131">[Transact-SQL 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="4bd63-131">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="4bd63-132">[Transact-SQL 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="4bd63-132">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="4bd63-133">[本機視窗](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="4bd63-133">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="4bd63-134">[呼叫堆疊視窗](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="4bd63-134">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="4bd63-135">[快速監看式對話方塊](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="4bd63-135">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="4bd63-136">運算式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4bd63-136">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
