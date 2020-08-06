---
title: '[錯誤清單] 視窗'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- error list window
- SQL Server Management Studio [SQL Server], error list window
ms.assetid: fae6327d-e268-44ae-a474-4a8f8f843129
author: rothja
ms.author: jroth
ms.openlocfilehash: 00455c339344b7b38a48500c49d139aa52df6116
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606208"
---
# <a name="error-list-window-management-studio"></a><span data-ttu-id="cf9b0-102">錯誤清單視窗 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cf9b0-102">Error List Window (Management Studio)</span></span>
  <span data-ttu-id="cf9b0-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [錯誤清單]  會顯示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中有哪些 IntelliSense 程式碼產生的語法和語意錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Error List** displays the syntax and semantic errors that are generated from the IntelliSense code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="features-of-the-error-list"></a><span data-ttu-id="cf9b0-104">錯誤清單的功能</span><span class="sxs-lookup"><span data-stu-id="cf9b0-104">Features of the Error List</span></span>  
 <span data-ttu-id="cf9b0-105">[錯誤清單]  提供了以下功能：</span><span class="sxs-lookup"><span data-stu-id="cf9b0-105">The **Error List** provides the following functionality:</span></span>  
  
-   <span data-ttu-id="cf9b0-106">當您編輯指令碼時，[錯誤清單]  會顯示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中由 IntelliSense 產生的錯誤和警告。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-106">As you edit scripts, the **Error List** displays the errors and warnings produced by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="cf9b0-107">您可以按兩下任何錯誤訊息項目，將焦點放在產生錯誤之指令碼檔案的索引標籤上，然後移動到錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-107">You can double-click any error message entry to focus on the tab for the script file that generated the error, and move to the error location.</span></span>  
  
-   <span data-ttu-id="cf9b0-108">您可以篩選您想要顯示的項目，以及每個項目所要顯示的資訊欄。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-108">You can filter which entries you want to display, and which columns of information you want appear for each entry.</span></span>  
  
-   <span data-ttu-id="cf9b0-109">當您修正錯誤之後，此錯誤項目就會從 [錯誤清單]  中移除。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-109">After you fix an error, the error entry is removed from the **Error List**.</span></span>  
  
-   <span data-ttu-id="cf9b0-110">當您關閉 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案的索引標籤時，該檔案的錯誤就會從 [錯誤清單]  中移除。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-110">When you close the tab for a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file, the errors for that file are removed from the **Error List**.</span></span>  
  
## <a name="working-with-the-error-list"></a><span data-ttu-id="cf9b0-111">使用錯誤清單</span><span class="sxs-lookup"><span data-stu-id="cf9b0-111">Working with the Error List</span></span>  
 <span data-ttu-id="cf9b0-112">若要顯示 [錯誤清單]  ，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cf9b0-112">To display the **Error List**, do one of the following:</span></span>  
  
-   <span data-ttu-id="cf9b0-113">在 [檢視]  功能表上，按一下 [錯誤清單]  。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-113">On the **View** menu, click **Error List**.</span></span>  
  
-   <span data-ttu-id="cf9b0-114">輸入鍵盤快速鍵 CTRL+\\、CTRL+E。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-114">Enter the keyboard shortcut CTRL+\\, CTRL+E.</span></span>  
  
 <span data-ttu-id="cf9b0-115">在您開啟 [錯誤清單]  之後，您可以執行下列動作來自訂您的檢視：</span><span class="sxs-lookup"><span data-stu-id="cf9b0-115">After you open the **Error List**, you can customize your view by performing the following actions:</span></span>  
  
-   <span data-ttu-id="cf9b0-116">若要排序清單，請按一下任何資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-116">To sort the list, click any column header.</span></span> <span data-ttu-id="cf9b0-117">若要以另一個資料行來重新排序，請按住 SHIFT 鍵，然後按一下另一個資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-117">To sort again by an additional column, press and hold the SHIFT key, and then click another column header.</span></span>  
  
-   <span data-ttu-id="cf9b0-118">若要選取哪些資料行要顯示和哪些要隱藏，請從捷徑功能表中選取 [顯示資料行]  。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-118">To select which columns are displayed and which are hidden, select **Show Columns** from the shortcut menu.</span></span>  
  
-   <span data-ttu-id="cf9b0-119">若要變更已顯示之資料行的順序，請將任一資料行標頭拖曳到左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-119">To change the order in which columns are displayed, drag any column header to the left or right.</span></span>  
  
 <span data-ttu-id="cf9b0-120">[錯誤清單]  不會連結到有關特定錯誤的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-120">The **Error List** does not link to additional information about specific errors.</span></span>  
  
## <a name="transact-sql-errors-in-management-studio"></a><span data-ttu-id="cf9b0-121">Management Studio 中的 Transact-SQL 錯誤</span><span class="sxs-lookup"><span data-stu-id="cf9b0-121">Transact-SQL Errors in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="cf9b0-122">會在以下位置顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼的錯誤：</span><span class="sxs-lookup"><span data-stu-id="cf9b0-122">displays errors for [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in the following locations:</span></span>  
  
-   <span data-ttu-id="cf9b0-123">[錯誤清單]  包含 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 編輯器中 IntelliSense 所找到的所有語法和語意錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-123">The **Error List** contains all syntax and semantic errors found by IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor.</span></span> <span data-ttu-id="cf9b0-124">當您編輯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼時，會動態更新這份錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-124">This list of errors is dynamically updated as you edit [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="cf9b0-125">此清單包含編輯器在每一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼中找到的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-125">The list includes all errors that the editor has found in each [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="cf9b0-126">編輯器在發現指令碼中的錯誤之後，不會停止剖析檔案。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-126">The editor does not stop parsing a file after encountering errors in a script.</span></span> <span data-ttu-id="cf9b0-127">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 編輯器中的 IntelliSense 不會支援所有的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法元素。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-127">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IntelliSense in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Editor does not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax elements.</span></span> <span data-ttu-id="cf9b0-128">[錯誤清單]  只包含 IntelliSense 支援之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-128">The **Error List** contains only errors from the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that is supported by IntelliSense.</span></span>  
  
-   <span data-ttu-id="cf9b0-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗底端的 [訊息] 索引標籤會顯示當執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼時，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 所傳回的所有錯誤和訊息。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-129">The **Messages** tab at the bottom of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window displays all errors and messages that are returned by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] when a [!INCLUDE[tsql](../../includes/tsql-md.md)] script is executed.</span></span> <span data-ttu-id="cf9b0-130">此清單要等到您再次執行此指令碼之後，才會變更。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-130">This list does not change until you execute the script again.</span></span> <span data-ttu-id="cf9b0-131">當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 找到一或兩個編譯錯誤之後，就會停止剖析批次；因此，[訊息]  索引標籤可能不會列出指令碼中的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-131">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stops parsing a batch after it finds one or two compile errors; therefore, the **Messages** tab might not list all errors in a script.</span></span>  
  
 <span data-ttu-id="cf9b0-132">有時錯誤會同時列在兩個位置。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-132">Sometimes errors are listed in both locations.</span></span> <span data-ttu-id="cf9b0-133">例如，指令碼檔案可能會有一個語法錯誤列在 [錯誤清單]  中。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-133">For example, a script file might have a syntax error that is listed in the **Error List**.</span></span> <span data-ttu-id="cf9b0-134">如果您在更正錯誤之前執行此指令碼，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 剖析器可以偵測到相同的狀況，並在 [訊息]  索引標籤上傳回此錯誤訊息的另一個複本。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-134">If you execute the script before you correct the error, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] parser can detect the same condition and return another copy of the error message in the **Messages** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf9b0-135">[錯誤清單]  只會顯示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中的錯誤，而不會顯示 MDX、DMX 或 XML/A 編輯器中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-135">The **Error List** only displays errors from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor; it does not display errors from the MDX, DMX, or XML/A Editors.</span></span> <span data-ttu-id="cf9b0-136">所有的 MDX、DMX 和 XML/A 錯誤都會顯示在這些編輯器的 [訊息]  索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-136">All MDX, DMX, and XML/A errors are displayed in the **Messages** tab in those editors.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="cf9b0-137">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="cf9b0-137">UI element list</span></span>  
 <span data-ttu-id="cf9b0-138">當 [錯誤清單]  開啟時，資訊會顯示在以下欄中：</span><span class="sxs-lookup"><span data-stu-id="cf9b0-138">When the **Error List** is open, the information is displayed in the following columns:</span></span>  
  
 <span data-ttu-id="cf9b0-139">**預設順序**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-139">**Default Order**</span></span>  
 <span data-ttu-id="cf9b0-140">顯示指示項目產生順序的整數。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-140">Displays an integer that indicates the order in which an entry was generated.</span></span>  
  
 <span data-ttu-id="cf9b0-141">**說明**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-141">**Description**</span></span>  
 <span data-ttu-id="cf9b0-142">顯示錯誤項目的文字。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-142">Displays the text of the error entry.</span></span> <span data-ttu-id="cf9b0-143">冗長的描述會切換到下一行。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-143">Lengthy descriptions wrap onto additional lines.</span></span>  
  
 <span data-ttu-id="cf9b0-144">**檔案**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-144">**File**</span></span>  
 <span data-ttu-id="cf9b0-145">顯示產生錯誤的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-145">Displays the name of the script file that generated the error.</span></span>  
  
 <span data-ttu-id="cf9b0-146">**線條**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-146">**Line**</span></span>  
 <span data-ttu-id="cf9b0-147">顯示指示包含錯誤之程式碼行的整數。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-147">Displays an integer that indicates which line of the code includes the error.</span></span>  
  
 <span data-ttu-id="cf9b0-148">**資料行**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-148">**Column**</span></span>  
 <span data-ttu-id="cf9b0-149">顯示指示程式碼行中之錯誤位置的整數。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-149">Displays an integer that indicates the position of the error in the line of code.</span></span>  
  
 <span data-ttu-id="cf9b0-150">**專案**</span><span class="sxs-lookup"><span data-stu-id="cf9b0-150">**Project**</span></span>  
 <span data-ttu-id="cf9b0-151">顯示包含指令碼檔案的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="cf9b0-151">Displays the name of the project that includes the script file.</span></span>  
