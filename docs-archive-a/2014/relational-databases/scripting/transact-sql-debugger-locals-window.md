---
title: 本機視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606205"
---
# <a name="locals-window"></a><span data-ttu-id="e2450-102">本機視窗</span><span class="sxs-lookup"><span data-stu-id="e2450-102">Locals Window</span></span>
  <span data-ttu-id="e2450-103">[區域變數]  視窗會顯示有關 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具目前範圍中之區域運算式的資訊。</span><span class="sxs-lookup"><span data-stu-id="e2450-103">The **Locals** window displays information about the local expressions in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="e2450-104">此範圍會設定為 [呼叫堆疊]  視窗內選取的目前呼叫堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="e2450-104">The scope is set to the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="e2450-105">您必須在偵錯模式中，才能顯示本機運算式。</span><span class="sxs-lookup"><span data-stu-id="e2450-105">You must be in debug mode to display the local expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="e2450-106">工作清單</span><span class="sxs-lookup"><span data-stu-id="e2450-106">Task List</span></span>  
 <span data-ttu-id="e2450-107">**存取區域變數視窗**</span><span class="sxs-lookup"><span data-stu-id="e2450-107">**To access the Locals window**</span></span>  
  
-   <span data-ttu-id="e2450-108">在 [偵錯]  功能表中，按一下 [視窗]  ，然後按一下 [區域變數]  。</span><span class="sxs-lookup"><span data-stu-id="e2450-108">On the **Debug** menu, click **Windows**, and then click **Locals**.</span></span>  
  
 <span data-ttu-id="e2450-109">**變更運算式的值**</span><span class="sxs-lookup"><span data-stu-id="e2450-109">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="e2450-110">以滑鼠右鍵按一下運算式，然後選取 [編輯值]  。</span><span class="sxs-lookup"><span data-stu-id="e2450-110">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="e2450-111">資料行</span><span class="sxs-lookup"><span data-stu-id="e2450-111">Columns</span></span>  
 <span data-ttu-id="e2450-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e2450-112">**Name**</span></span>  
 <span data-ttu-id="e2450-113">為本機運算式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e2450-113">Is the name of the local expression.</span></span> <span data-ttu-id="e2450-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具會列出名稱以 @@ 開頭的變數、參數和系統函式。</span><span class="sxs-lookup"><span data-stu-id="e2450-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger lists variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="e2450-115">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e2450-115">**Value**</span></span>  
 <span data-ttu-id="e2450-116">顯示目前指派給本機運算式的值。</span><span class="sxs-lookup"><span data-stu-id="e2450-116">Displays the value that is currently assigned to the local expression.</span></span> <span data-ttu-id="e2450-117">當沒有任何值指派給運算式時，此資料行會是空白的。</span><span class="sxs-lookup"><span data-stu-id="e2450-117">This column is blank when no value has been assigned to the expression.</span></span>  
  
 <span data-ttu-id="e2450-118">如果運算式的長度超過 **[值]** 資料行的寬度，當您將指標放在該運算式的 **[值]** 資料格上方時，工具提示會顯示完整的值。</span><span class="sxs-lookup"><span data-stu-id="e2450-118">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="e2450-119">**[值]** 資料格內的放大鏡圖示表示可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="e2450-119">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="e2450-120">在此清單中，您可以指定 **[文字視覺化檢視]** 、 **[XML 視覺化檢視]** 或 **[HTML 視覺化檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="e2450-120">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="e2450-121">若要啟動偵錯工具視覺化檢視，請按一下放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="e2450-121">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="e2450-122">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具會開啟一個對話方塊，其中會以對資料類型適合的格式顯示資料。</span><span class="sxs-lookup"><span data-stu-id="e2450-122">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="e2450-123">**型別**</span><span class="sxs-lookup"><span data-stu-id="e2450-123">**Type**</span></span>  
 <span data-ttu-id="e2450-124">顯示此運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e2450-124">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2450-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2450-125">See Also</span></span>  
 <span data-ttu-id="e2450-126">[Transact-SQL 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e2450-126">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="e2450-127">[Transact-SQL 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="e2450-127">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="e2450-128">[監看式視窗](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="e2450-128">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="e2450-129">[呼叫堆疊視窗](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="e2450-129">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="e2450-130">[快速監看式對話方塊](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="e2450-130">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="e2450-131">運算式 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2450-131">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
