---
title: 設定編輯器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e94cdbcd310814081e146e3fd0dbe75260d1240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701002"
---
# <a name="configure-editors-sql-server-management-studio"></a><span data-ttu-id="b4e65-102">設定編輯器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b4e65-102">Configure Editors (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b4e65-103">您可以設定各個 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 編輯器的選項，以自訂其作業。</span><span class="sxs-lookup"><span data-stu-id="b4e65-103">You can customize the operation of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] editors by configuring the options for each editor.</span></span>  
  
## <a name="settng-editor-options"></a><span data-ttu-id="b4e65-104">設定編輯器選項</span><span class="sxs-lookup"><span data-stu-id="b4e65-104">Settng Editor Options</span></span>  
 <span data-ttu-id="b4e65-105">使用 [工具]  功能表並選取 [選項...]  來顯示 [選項]  對話方塊，即可設定大部分的編輯器選項。</span><span class="sxs-lookup"><span data-stu-id="b4e65-105">Most of the editor options are set by using the **Tools** menu and selecting **Options...** to display an **Options** dialog.</span></span> <span data-ttu-id="b4e65-106">在 **[選項]** 對話方塊於左窗格中開啟 **[文字編輯器]** 節點，可設定編碼與文字編輯選項。</span><span class="sxs-lookup"><span data-stu-id="b4e65-106">In the **Options** dialog, open the **Text Editor** node in the left pane to set code and text editing options.</span></span> <span data-ttu-id="b4e65-107">文字編輯器下的節點適用於特定的編輯器：</span><span class="sxs-lookup"><span data-stu-id="b4e65-107">The nodes under Text Editor apply to specific editors:</span></span>  
  
1.  <span data-ttu-id="b4e65-108">**所有語言** - 使用此節點設定的選項會套用至所有 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 編輯器。</span><span class="sxs-lookup"><span data-stu-id="b4e65-108">**All Languages** - options set using this node apply to all of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] editors.</span></span> <span data-ttu-id="b4e65-109">使用其他節點為特定的編輯器設定不同之選項，可以覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="b4e65-109">You can override these settings by using the other nodes to set different options for a specific editor.</span></span>  
  
2.  <span data-ttu-id="b4e65-110">**純文字** - 使用此節點設定的選項會套用至 MDX、DMX 與文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="b4e65-110">**Plain Text** - options set using this node apply to the MDX, DMX, and text editors.</span></span>  
  
3.  <span data-ttu-id="b4e65-111">**Transact-SQL** - 使用此節點設定的選項會套用至資料庫引擎查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="b4e65-111">**Transact-SQL** - options set using this node apply to the Database Engine Query Editor.</span></span>  
  
4.  <span data-ttu-id="b4e65-112">**XML**使用此節點設定的選項會套用至 XML for Analysis 編輯器。</span><span class="sxs-lookup"><span data-stu-id="b4e65-112">**XML** - options set using this node apply to the XML for Analysis editor.</span></span>  
  
 <span data-ttu-id="b4e65-113">開啟 **[查詢執行]** 或 **[查詢結果]** 節點，以自訂查詢的執行方式與結果的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="b4e65-113">Open the **Query Execution** or **Query Results** nodes to customize the execution of queries and how the results are displayed.</span></span>  
  
## <a name="editor-configuration-tasks"></a><span data-ttu-id="b4e65-114">編輯器配置工作</span><span class="sxs-lookup"><span data-stu-id="b4e65-114">Editor Configuration Tasks</span></span>  
  
|<span data-ttu-id="b4e65-115">工作描述</span><span class="sxs-lookup"><span data-stu-id="b4e65-115">Task Description</span></span>|<span data-ttu-id="b4e65-116">主題</span><span class="sxs-lookup"><span data-stu-id="b4e65-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="b4e65-117">描述如何指定在 [Windows 檔案總管] 中按兩下特定副檔名的檔案，自動開啟編輯器。</span><span class="sxs-lookup"><span data-stu-id="b4e65-117">Describes how to specify that an editor be opened by double-clicking on a file with a specified extension in Windows Explorer.</span></span>|[<span data-ttu-id="b4e65-118">使副檔名與程式碼編輯器相關聯</span><span class="sxs-lookup"><span data-stu-id="b4e65-118">Associate File Extensions to a Code Editor</span></span>](associate-file-extensions-to-a-code-editor.md)|  
|<span data-ttu-id="b4e65-119">描述如何自訂字型，讓程式碼與文字更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="b4e65-119">Describes how to customize fonts to make code and text more readable.</span></span>|[<span data-ttu-id="b4e65-120">變更字型色彩、大小與樣式</span><span class="sxs-lookup"><span data-stu-id="b4e65-120">Change Font Color, Size, and Style</span></span>](change-font-color-size-and-style.md)|  
|<span data-ttu-id="b4e65-121">描述如何檢視屬性。</span><span class="sxs-lookup"><span data-stu-id="b4e65-121">Describes how to view properties.</span></span>|[<span data-ttu-id="b4e65-122">在 Management Studio 中使用屬性視窗</span><span class="sxs-lookup"><span data-stu-id="b4e65-122">Use the Properties Window in Management Studio</span></span>](use-the-properties-window-in-management-studio.md)|  
|<span data-ttu-id="b4e65-123">編輯器選項對話方塊的 F1 說明頁面之位置。</span><span class="sxs-lookup"><span data-stu-id="b4e65-123">Location of the F1 help pages for the editor options dialogs.</span></span>|[<span data-ttu-id="b4e65-124">查詢選項頁面 F1 說明</span><span class="sxs-lookup"><span data-stu-id="b4e65-124">Query Options Pages F1 Help</span></span>](../../database-engine/query-options-pages-f1-help.md)|  
  
  
