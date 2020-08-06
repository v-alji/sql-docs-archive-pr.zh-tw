---
title: " (文字編輯器的選項-Transact-sql-一般頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: rothja
ms.author: jroth
ms.openlocfilehash: f008d0d84a15cfbf0bfa988232015e6619f4f5c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597998"
---
# <a name="options-text-editor---transact-sql--general-page"></a><span data-ttu-id="5e9d4-102"> (文字編輯器的選項-Transact-sql-一般頁面) </span><span class="sxs-lookup"><span data-stu-id="5e9d4-102">Options (Text Editor - Transact-SQL- General Page)</span></span>
  <span data-ttu-id="5e9d4-103">使用 **[一般]** 選項對話方塊可以變更 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器的一般編輯行為，這個編輯器會用來編輯 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-103">Use the **General** options dialog box to change the general editing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to edit [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="5e9d4-104">若要顯示這些設定，請在 [工具]\*\*\*\* 功能表上按一下 [選項]\*\*\*\*，展開 [Transact-SQL]\*\*\*\* 子資料夾，然後按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-104">To display these settings, click **Options** on the **Tools** menu, expand the **Transact-SQL** subfolder, and then click **General**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="5e9d4-105">在多個位置設定選項</span><span class="sxs-lookup"><span data-stu-id="5e9d4-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="5e9d4-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器的選項也可以在 **[所有語言 - 一般]** 對話方塊中設定。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="5e9d4-107">如果您使用 **[所有語言]** 對話方塊為其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 編輯器 (例如 DMX 或 MDX 編輯器) 設定不同的選項，則必須使用這個對話方塊重設 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器選項。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="5e9d4-108">陳述式完成</span><span class="sxs-lookup"><span data-stu-id="5e9d4-108">Statement Completion</span></span>  
 <span data-ttu-id="5e9d4-109">**自動列出成員**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-109">**Auto list members**</span></span>  
 <span data-ttu-id="5e9d4-110">選取此核取方塊時，當您在編輯器中輸入時將會顯示可用的資料庫和結構描述物件、資料行、資料表值函式或函數的清單。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-110">When this check box is selected, lists of available database and schema objects, columns, table-valued functions, or functions are displayed as you type in the editor.</span></span> <span data-ttu-id="5e9d4-111">從快顯清單擇取任何項目，以將其插入程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-111">Choose any item from the pop-up list to insert it into your code.</span></span>  
  
 <span data-ttu-id="5e9d4-112">**隱藏進階成員**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-112">**Hide advanced members**</span></span>  
 <span data-ttu-id="5e9d4-113">無法使用此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-113">This check box is unavailable.</span></span>  
  
 <span data-ttu-id="5e9d4-114">**參數資訊**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-114">**Parameter information**</span></span>  
 <span data-ttu-id="5e9d4-115">如果選取此核取方塊，將會顯示緊接在插入點 (游標) 左邊之預存程序或函數的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-115">When this check box is selected, parameter information is displayed for a stored procedure or function that is immediately to the left of the insertion point (cursor).</span></span> <span data-ttu-id="5e9d4-116">此資訊包括可用參數的清單 (包含其名稱和資料類型)。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-116">The information includes a list of the available parameters with their names and data types.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="5e9d4-117">設定</span><span class="sxs-lookup"><span data-stu-id="5e9d4-117">Settings</span></span>  
 <span data-ttu-id="5e9d4-118">**啟用虛擬空間**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-118">**Enable virtual space**</span></span>  
 <span data-ttu-id="5e9d4-119">選取這個核取方塊時，您可以按一下程式碼行結尾之外的任何位置，然後輸入內容。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-119">When this check box is selected, you can click anywhere beyond the end of a line of code and type.</span></span> <span data-ttu-id="5e9d4-120">選取此核取方塊，即可在程式碼旁的一致位置上放置註解。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-120">Select this check box to position comments at a consistent point next to your code.</span></span> <span data-ttu-id="5e9d4-121">選取這個核取方塊就會停用 **[自動換行]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-121">Selecting this check box disables the **Word wrap** check box.</span></span>  
  
 <span data-ttu-id="5e9d4-122">**自動換行**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-122">**Word wrap**</span></span>  
 <span data-ttu-id="5e9d4-123">如果選取此核取方塊，超出可檢視的編輯器區域的行之任何部份，就會自動顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-123">When this check box is selected, any portion of a line that extends horizontally beyond the viewable editor area is automatically displayed on the next line.</span></span> <span data-ttu-id="5e9d4-124">選取此核取方塊會啟用 **[顯示自動換行的視覺化圖像]** 核取方塊並停用 **[啟用虛擬空間]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-124">Selecting this check box enables the **Show visual glyphs for word wrap** check box and disables the **Enable virtual space** check box.</span></span>  
  
 <span data-ttu-id="5e9d4-125">**顯示自動換行的視覺化圖像**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-125">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="5e9d4-126">如果選取此核取方塊，就會顯示換行箭頭標記，其中過長的行就會自動換行到下一行。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-126">When this check box is selected, a return arrow indicator is displayed where a long line wraps to the next line.</span></span>  
  
 <span data-ttu-id="5e9d4-127">**沒有選取項目時，請套用剪下/複製命令至空白行**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-127">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="5e9d4-128">當您在空白行上放置插入點、不選取任何內容，然後按一下 **[複製]** 或 **[剪下]** 時，此核取方塊就會設定編輯器的行為。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-128">This check box sets the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="5e9d4-129">如果選取此核取方塊，就會複製或剪下空白行。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-129">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="5e9d4-130">接著，如果您按一下 **[貼上]**，就會插入一個新的空白行。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-130">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="5e9d4-131">如果清除此核取方塊，就不會複製或剪下任何內容。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-131">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="5e9d4-132">接著，您按一下 **[貼上]**，就會貼上最近複製的內容。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-132">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="5e9d4-133">如果先前沒有進行複製，就不會有貼上動作。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-133">If nothing has been copied previously, nothing is pasted.</span></span>  
  
 <span data-ttu-id="5e9d4-134">當行不是空白時，此設定對 **[複製]** 或 **[剪下]** 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-134">This setting has no effect on **Copy** or **Cut** when a line is not blank.</span></span> <span data-ttu-id="5e9d4-135">如果沒有選取內容，就會複製或剪下整個行。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-135">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="5e9d4-136">接著，如果您按一下 **[貼上]**，就會貼上整行的文字與其結束字元。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-136">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="5e9d4-137">顯示</span><span class="sxs-lookup"><span data-stu-id="5e9d4-137">Display</span></span>  
 <span data-ttu-id="5e9d4-138">**行號**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-138">**Line numbers**</span></span>  
 <span data-ttu-id="5e9d4-139">如果選取此核取方塊，行號就會出現在每一行程式碼的旁邊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-139">When this check box is selected, a line number appears next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e9d4-140">這些行號不會加入您的程式碼中，且不會列印。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-140">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="5e9d4-141">它們僅供參考。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-141">They are for reference only.</span></span>  
  
 <span data-ttu-id="5e9d4-142">**啟用按一下方式的 URL 導覽**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-142">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="5e9d4-143">如果選取此核取方塊，當游標在編輯器中的 URL 上方時會變成手指符號。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-143">When this check box is selected, the cursor changes to a pointing hand as it passes over a URL in the editor.</span></span> <span data-ttu-id="5e9d4-144">按一下 URL 即可在 Web 瀏覽器中顯示該頁面。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-144">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="5e9d4-145">**巡覽列**</span><span class="sxs-lookup"><span data-stu-id="5e9d4-145">**Navigation bar**</span></span>  
 <span data-ttu-id="5e9d4-146">無法使用此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5e9d4-146">This check box is unavailable.</span></span>  
  
  
