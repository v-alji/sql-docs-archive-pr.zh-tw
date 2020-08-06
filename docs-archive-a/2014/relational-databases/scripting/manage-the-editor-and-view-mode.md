---
title: 管理編輯器和檢視模式
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], managing window behavior
- workbench view modes [SQL Server Management Studio]
- full screen mode [SQL Server Management Studio]
- fonts [SQL Server Management Studio]
- word wraps [SQL Server Management Studio]
- virtual space mode [SQL Server Management Studio]
- splitting document views
- displaying line numbers
- view modes [SQL Server Management Studio]
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
author: rothja
ms.author: jroth
ms.openlocfilehash: 36788b1fe831a6c15c4aa0668d1759c088fcaa73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599467"
---
# <a name="manage-the-editor-and-view-mode"></a><span data-ttu-id="aab5f-102">管理編輯器和檢視模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-102">Manage the Editor and View Mode</span></span>
  <span data-ttu-id="aab5f-103">編輯器提供了許多用來控制程式碼檢視的方式。</span><span class="sxs-lookup"><span data-stu-id="aab5f-103">The Editor gives you a number of ways to control the view of your code.</span></span>  
  
## <a name="changing-the-view-mode"></a><span data-ttu-id="aab5f-104">變更檢視模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-104">Changing the View Mode</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="aab5f-105">有一個稱為 **[索引標籤文件]** 的檢視模式，您可以利用這個模式來同時開啟多個編輯器和多份文件，並利用編輯器頂端的索引標籤來存取它們。</span><span class="sxs-lookup"><span data-stu-id="aab5f-105">features a view mode called **Tabbed Documents**, which allows you to open multiple editors and documents simultaneously and access them through tabs at the top of the Editor.</span></span> <span data-ttu-id="aab5f-106">另外，您也可以在多重文件介面 (MDI) 模式中開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 環境，此時會將不含索引標籤的各個視窗聯結起來，您可以並排這些視窗、將它們最小化...等等。</span><span class="sxs-lookup"><span data-stu-id="aab5f-106">You can alternatively open the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] environment in Multiple Document Interface (MDI) mode, which joins windows without the tabs, and allows each window to be tiled, minimized, and so on.</span></span>  
  
#### <a name="to-switch-between-view-modes"></a><span data-ttu-id="aab5f-107">切換檢視模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-107">To switch between view modes</span></span>  
  
1.  <span data-ttu-id="aab5f-108">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-108">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="aab5f-109">按一下 **[環境]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-109">Click **Environment**.</span></span> <span data-ttu-id="aab5f-110">按一下 **[一般]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-110">Click **General**.</span></span>  
  
3.  <span data-ttu-id="aab5f-111">按一下 **[索引標籤文件]** 或 **[MDI 環境]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-111">Click **Tabbed documents** or **MDI environment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aab5f-112">您必須重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="aab5f-112">The changes will not take effect until [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is restarted.</span></span>  
  
## <a name="splitting-the-view"></a><span data-ttu-id="aab5f-113">分割檢視</span><span class="sxs-lookup"><span data-stu-id="aab5f-113">Splitting the View</span></span>  
 <span data-ttu-id="aab5f-114">您可以將 [編輯器] 視窗分割成兩個部份，使編輯工作更容易進行。</span><span class="sxs-lookup"><span data-stu-id="aab5f-114">An Editor window can be split into two separate parts for easier editing.</span></span>  
  
#### <a name="to-split-a-window"></a><span data-ttu-id="aab5f-115">分割視窗</span><span class="sxs-lookup"><span data-stu-id="aab5f-115">To split a window</span></span>  
  
1.  <span data-ttu-id="aab5f-116">按一下分割線 (在捲軸上面)。</span><span class="sxs-lookup"><span data-stu-id="aab5f-116">Click the splitter bar (located above the scroll bar).</span></span>  
  
2.  <span data-ttu-id="aab5f-117">向下拖曳分割線。</span><span class="sxs-lookup"><span data-stu-id="aab5f-117">Drag the splitter bar downward.</span></span>  
  
3.  <span data-ttu-id="aab5f-118">若要返回單一窗格，請按兩下用來分隔兩個窗格的分割線。</span><span class="sxs-lookup"><span data-stu-id="aab5f-118">To go back to a single pane, double-click the splitter bar dividing the two panes.</span></span>  
  
 <span data-ttu-id="aab5f-119">新的窗格包含相同的文件，只要窗格是顯示文件中的相同位置，一個窗格中的變更，也會反映在另一個窗格中。</span><span class="sxs-lookup"><span data-stu-id="aab5f-119">The new pane contains the same document, and any changes made to one pane are reflected in the other pane as long as that pane displays the same place in the document.</span></span>  
  
## <a name="word-wrap"></a><span data-ttu-id="aab5f-120">自動換行</span><span class="sxs-lookup"><span data-stu-id="aab5f-120">Word Wrap</span></span>  
 <span data-ttu-id="aab5f-121">當您啟動自動換行時，會移除水平捲軸，您不需要捲動視窗，超出編輯器視窗寬度的各行程式碼會自動折行。</span><span class="sxs-lookup"><span data-stu-id="aab5f-121">When you activate Word Wrap, the horizontal scrollbar is removed and lines of code that exceed the width of the Editor's window size automatically wraps to the next displayed line rather than scrolling off the side of the window.</span></span>  
  
#### <a name="to-activate-word-wrap"></a><span data-ttu-id="aab5f-122">啟動自動換行</span><span class="sxs-lookup"><span data-stu-id="aab5f-122">To activate word wrap</span></span>  
  
1.  <span data-ttu-id="aab5f-123">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-123">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="aab5f-124">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-124">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="aab5f-125">開啟適當語言資料夾 (或 [所有語言]  ，這會影響所有語言)。</span><span class="sxs-lookup"><span data-stu-id="aab5f-125">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="aab5f-126">選取 **[自動換行]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-126">Select **Word wrap**.</span></span>  
  
## <a name="enabling-virtual-space-mode"></a><span data-ttu-id="aab5f-127">啟用虛擬空間模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-127">Enabling Virtual Space Mode</span></span>  
 <span data-ttu-id="aab5f-128">在 **[虛擬空間]** 模式中，編輯器的行為會如同各行尾端之後的空間填滿了無數個空格，可讓各行程式碼延伸到超出可見螢幕區的側邊。</span><span class="sxs-lookup"><span data-stu-id="aab5f-128">In **Virtual Space** mode, the Editor acts as if the space past the end of each line is filled with an infinite number of spaces, allowing code lines to continue off the side of the visible screen area.</span></span>  
  
#### <a name="to-enable-virtual-space-mode"></a><span data-ttu-id="aab5f-129">啟用虛擬空間模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-129">To enable Virtual Space mode</span></span>  
  
1.  <span data-ttu-id="aab5f-130">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-130">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="aab5f-131">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-131">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="aab5f-132">開啟適當語言資料夾 (或 [所有語言]  ，這會影響所有語言)。</span><span class="sxs-lookup"><span data-stu-id="aab5f-132">Open the appropriate language folder (or **All Languages** to affect all languages).</span></span>  
  
4.  <span data-ttu-id="aab5f-133">選取 **[啟用虛擬空間]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-133">Select **Enable virtual space**.</span></span>  
  
 <span data-ttu-id="aab5f-134">當啟用虛擬空間模式時，游標會從行尾折返到下一行的第一個字元，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="aab5f-134">When Virtual Space mode is not enabled, the cursor wraps from the end of one line to the first character of the next line and vice-versa.</span></span>  
  
## <a name="displaying-line-numbers"></a><span data-ttu-id="aab5f-135">顯示行號</span><span class="sxs-lookup"><span data-stu-id="aab5f-135">Displaying Line Numbers</span></span>  
 <span data-ttu-id="aab5f-136">您可以在程式碼中開啟顯示行號的功能。</span><span class="sxs-lookup"><span data-stu-id="aab5f-136">You can turn on line numbering in your code.</span></span> <span data-ttu-id="aab5f-137">在導覽程式碼時，行號非常有用。</span><span class="sxs-lookup"><span data-stu-id="aab5f-137">Line numbers are useful for navigating code.</span></span> <span data-ttu-id="aab5f-138">如需詳細資訊，請參閱 [導覽程式碼與文字](navigate-code-and-text.md)。</span><span class="sxs-lookup"><span data-stu-id="aab5f-138">For more information, see [Navigate Code and Text](navigate-code-and-text.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aab5f-139">開啟顯示行號的功能，不表示列印文件時會有行號。</span><span class="sxs-lookup"><span data-stu-id="aab5f-139">Turning on line numbering does not mean that the document will print with line numbers.</span></span> <span data-ttu-id="aab5f-140">若要列印行號，您必須在 **[檔案]** 功能表的 **[版面設定]** 命令中，選取 **[行號]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="aab5f-140">For line numbers to print, you must select the **Line numbers** check box in the **Page Setup** command on the **File** menu.</span></span>  
  
#### <a name="to-display-line-numbers-in-code"></a><span data-ttu-id="aab5f-141">在程式碼中顯示行號</span><span class="sxs-lookup"><span data-stu-id="aab5f-141">To display line numbers in code</span></span>  
  
1.  <span data-ttu-id="aab5f-142">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-142">Click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="aab5f-143">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-143">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="aab5f-144">按一下 **[所有語言]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-144">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="aab5f-145">按一下 **[一般]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-145">Click **General**.</span></span>  
  
5.  <span data-ttu-id="aab5f-146">選取 **[行號]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-146">Select **Line numbers**.</span></span>  
  
 <span data-ttu-id="aab5f-147">如果只要針對某些程式設計語言指定顯示行號的功能，請在適當資料夾中選取 **[行號]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-147">To specify line numbering for only some programming languages, select **Line Numbers** in the appropriate folder.</span></span>  
  
## <a name="enabling-full-screen-mode"></a><span data-ttu-id="aab5f-148">啟用全螢幕模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-148">Enabling Full Screen Mode</span></span>  
 <span data-ttu-id="aab5f-149">您可以選擇隱藏所有工具視窗，啟用全螢幕模式來專門檢視文件視窗。</span><span class="sxs-lookup"><span data-stu-id="aab5f-149">You can choose to hide all tool windows and view only document windows by enabling Full Screen mode.</span></span>  
  
#### <a name="to-enable-full-screen-mode"></a><span data-ttu-id="aab5f-150">啟用全螢幕模式</span><span class="sxs-lookup"><span data-stu-id="aab5f-150">To enable Full Screen mode</span></span>  
  
1.  <span data-ttu-id="aab5f-151">按 ALT+SHIFT+ENTER 來切換全螢幕模式。</span><span class="sxs-lookup"><span data-stu-id="aab5f-151">Press ALT+SHIFT+ENTER to toggle Full Screen mode.</span></span>  
  
## <a name="using-auto-hide-all"></a><span data-ttu-id="aab5f-152">使用 [自動全部隱藏]</span><span class="sxs-lookup"><span data-stu-id="aab5f-152">Using Auto Hide All</span></span>  
  
#### <a name="to-hide-all-the-tool-windows-at-once"></a><span data-ttu-id="aab5f-153">同時隱藏所有工具視窗</span><span class="sxs-lookup"><span data-stu-id="aab5f-153">To hide all the tool windows at once</span></span>  
  
1.  <span data-ttu-id="aab5f-154">在 **[視窗]** 功能表上，按一下 **[自動全部隱藏]** 。</span><span class="sxs-lookup"><span data-stu-id="aab5f-154">Select **Auto Hide All** on the **Window** menu.</span></span>  
  
  
