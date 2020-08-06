---
title: 選項 (環境-一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7712c568b478bd2ba958237ba3204246657b3a72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607213"
---
# <a name="options-environment-general-page"></a><span data-ttu-id="665e6-102">選項 (環境 - 一般頁面)</span><span class="sxs-lookup"><span data-stu-id="665e6-102">Options (Environment-General Page)</span></span>
  <span data-ttu-id="665e6-103">使用 [選項]  對話方塊來設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的啟動動作、一般視窗管理選項，以及其他一般設定。</span><span class="sxs-lookup"><span data-stu-id="665e6-103">Use the **Options** dialog box to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] startup actions, general window management options, and other general settings.</span></span> <span data-ttu-id="665e6-104">在 [工具]  功能表上按一下 [選項]  、展開 [環境]  資料夾，然後按一下 [一般]  。</span><span class="sxs-lookup"><span data-stu-id="665e6-104">On the **Tools** menu, click **Options**, expand the **Environment** folder, and then click **General**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="665e6-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="665e6-105">UI element list</span></span>  
 <span data-ttu-id="665e6-106">**啟動時**</span><span class="sxs-lookup"><span data-stu-id="665e6-106">**At startup**</span></span>  
 <span data-ttu-id="665e6-107">選取 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 啟動時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="665e6-107">Select the action for [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to perform when it is started.</span></span> <span data-ttu-id="665e6-108">可用選項包括：</span><span class="sxs-lookup"><span data-stu-id="665e6-108">The options are:</span></span>  
  
-   <span data-ttu-id="665e6-109">[開啟物件總管]  會提示進行連接，然後開啟物件總管。</span><span class="sxs-lookup"><span data-stu-id="665e6-109">**Open Object Explorer** prompts for a connection and then opens Object Explorer.</span></span>  
  
-   <span data-ttu-id="665e6-110">[開啟新增查詢視窗]  會提示進行連接，然後開啟 SQL 查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="665e6-110">**Open new query window** prompts for a connection and then opens SQL Query Editor.</span></span>  
  
-   <span data-ttu-id="665e6-111">[開啟物件總管和新增查詢]\*\*\*\* 會提示進行連接，然後使用該連接開啟物件總管和 SQL 查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="665e6-111">**Open Object Explorer and new query** prompts for a connection, then opens both Object Explorer and SQL Query Editor with that connection.</span></span>  
  
-   <span data-ttu-id="665e6-112">[開啟空白環境]  會開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，但沒有 SQL 查詢編輯器視窗，且不會將物件總管連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="665e6-112">**Open empty environment** opens [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] without a SQL Query editor window and without connecting Object Explorer to a server.</span></span>  
  
 <span data-ttu-id="665e6-113">**在 [物件總管] 中隱藏系統物件**</span><span class="sxs-lookup"><span data-stu-id="665e6-113">**Hide system objects in Object Explorer**</span></span>  
 <span data-ttu-id="665e6-114">選取此核取方塊，即可從 [物件總管] 中的樹狀檢視裡，移除系統資料庫、系統資料表、系統檢視，以及系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="665e6-114">Select this check box to remove the system databases, system tables, system views, and system stored procedures from tree view in Object Explorer.</span></span> <span data-ttu-id="665e6-115">系統函數與系統資料類型並未隱藏。</span><span class="sxs-lookup"><span data-stu-id="665e6-115">System functions and system data types are not hidden.</span></span> <span data-ttu-id="665e6-116">此選項僅適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，且不會影響在 [物件總管] 中已經連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="665e6-116">This option only applies to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and does not affect servers already connected in Object Explorer.</span></span>  
  
## <a name="environment-layout"></a><span data-ttu-id="665e6-117">環境配置</span><span class="sxs-lookup"><span data-stu-id="665e6-117">Environment Layout</span></span>  
 <span data-ttu-id="665e6-118">您必須關閉再重新開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，才能在索引標籤式文件與多重文件介面 (MDI) 環境模式之間變更。</span><span class="sxs-lookup"><span data-stu-id="665e6-118">You must close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change between tabbed document and multiple-document interface (MDI) environment mode.</span></span>  
  
 <span data-ttu-id="665e6-119">**索引標籤式文件**</span><span class="sxs-lookup"><span data-stu-id="665e6-119">**Tabbed documents**</span></span>  
 <span data-ttu-id="665e6-120">選取此選項即可顯示在編輯器內，以索引標籤組合在一起的多個文件視窗。</span><span class="sxs-lookup"><span data-stu-id="665e6-120">Select this option to display document windows that are tabbed together within editors.</span></span> <span data-ttu-id="665e6-121">索引標籤式文件視窗適用於組織多個開啟的文件以及在它們之間切換。</span><span class="sxs-lookup"><span data-stu-id="665e6-121">Tabbed document windows are useful for organizing and switching between multiple open documents.</span></span>  
  
 <span data-ttu-id="665e6-122">**MDI 環境**</span><span class="sxs-lookup"><span data-stu-id="665e6-122">**MDI environment**</span></span>  
 <span data-ttu-id="665e6-123">選取此選項即可在 MDI 環境中開啟文件。</span><span class="sxs-lookup"><span data-stu-id="665e6-123">Select this option to open documents in a MDI environment.</span></span> <span data-ttu-id="665e6-124">MDI 文件視窗可以讓螢幕空間更大，因為原來由索引標籤式文件環境中之索引標籤佔據的螢幕空間，也可以使用。</span><span class="sxs-lookup"><span data-stu-id="665e6-124">MDI document windows are useful for gaining the screen space that is otherwise taken up by the tabs in the tabbed documents environment.</span></span> <span data-ttu-id="665e6-125">以 MDI 模式工作時，您可以按下 CTRL+TAB，或使用位於 [視窗]\*\*\*\* 功能表上的並列選項，在文件之間切換。</span><span class="sxs-lookup"><span data-stu-id="665e6-125">When working in MDI mode, you can switch between documents by pressing CTRL+TAB, or you can use the tile options located on the **Window** menu.</span></span>  
  
## <a name="docked-tool-window-behavior"></a><span data-ttu-id="665e6-126">停駐工具視窗行為</span><span class="sxs-lookup"><span data-stu-id="665e6-126">Docked Tool Window Behavior</span></span>  
 <span data-ttu-id="665e6-127">**關閉按鈕只會影響使用中的索引標籤**</span><span class="sxs-lookup"><span data-stu-id="665e6-127">**Close button affects active tab only**</span></span>  
 <span data-ttu-id="665e6-128">指定若選取了此核取方塊，只會關閉目前具有焦點的工具視窗，而不會關閉停駐集內的所有工具視窗。</span><span class="sxs-lookup"><span data-stu-id="665e6-128">Specifies that when this check box is selected, only the tool window that has focus currently is closed and not all of the tool windows in the docked set.</span></span> <span data-ttu-id="665e6-129">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="665e6-129">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="665e6-130">**自動隱藏按鈕只會影響使用中的索引標籤**</span><span class="sxs-lookup"><span data-stu-id="665e6-130">**Auto Hide button affects active tab only**</span></span>  
 <span data-ttu-id="665e6-131">指定若選取了此核取方塊，只會自動隱藏目前具有焦點的工具視窗，而不會隱藏停駐集內的所有工具視窗。</span><span class="sxs-lookup"><span data-stu-id="665e6-131">Specifies that when this check box is selected, only the tool window that has focus currently is hidden automatically, not all of the tool windows in the docked set.</span></span> <span data-ttu-id="665e6-132">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="665e6-132">By default, this check box is cleared.</span></span>  
  
## <a name="display"></a><span data-ttu-id="665e6-133">顯示</span><span class="sxs-lookup"><span data-stu-id="665e6-133">Display</span></span>  
 <span data-ttu-id="665e6-134">**顯示最近使用清單中的 n 個檔案**</span><span class="sxs-lookup"><span data-stu-id="665e6-134">**Display n files in recently used list**</span></span>  
 <span data-ttu-id="665e6-135">自訂 [檔案]\*\*\*\* 功能表上所顯示之最近使用的專案與最近使用之檔案的數目。</span><span class="sxs-lookup"><span data-stu-id="665e6-135">Customizes the number of recent projects and recent files that appear on the **File** menu.</span></span> <span data-ttu-id="665e6-136">輸入介於 1 到 24 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="665e6-136">Type a number between 1 and 24.</span></span> <span data-ttu-id="665e6-137">預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="665e6-137">The default is 4.</span></span> <span data-ttu-id="665e6-138">這是方便用來擷取最近使用過的指令碼專案和檔案，以及編寫專案的方式。</span><span class="sxs-lookup"><span data-stu-id="665e6-138">This is an easy way to retrieve recently used script projects and files and script projects.</span></span>  
  
  
