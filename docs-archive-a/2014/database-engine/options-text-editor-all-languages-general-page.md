---
title: 選項 (文字編輯器-所有語言-一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
author: rothja
ms.author: jroth
ms.openlocfilehash: 9510ff7c8d28a084ac250c937ec01458b612ac60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599174"
---
# <a name="options-text-editor---all-languages---general-page"></a><span data-ttu-id="985cb-102">選項 (文字編輯器 - 所有語言 - 一般頁面)</span><span class="sxs-lookup"><span data-stu-id="985cb-102">Options (Text Editor - All Languages - General Page)</span></span>
  <span data-ttu-id="985cb-103">使用這個對話方塊可設定 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，全部五個編輯器的一般編輯選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-103">Use this dialog box to set general editing options in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="985cb-104">若要顯示這些選項，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="985cb-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="985cb-105">選取 [文字編輯器]\*\*\*\* 資料夾，展開 [所有語言]\*\*\*\* 資料夾，然後按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="985cb-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **General**.</span></span>  
  
## <a name="option-settings-by-editor"></a><span data-ttu-id="985cb-106">依編輯器的選項設定</span><span class="sxs-lookup"><span data-stu-id="985cb-106">Option Settings by Editor</span></span>  
 <span data-ttu-id="985cb-107">您必須使用 [所有語言]\*\*\*\* 對話方塊設定 DMX、MDX 和 SQL Server Compact 編輯器的選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="985cb-108">在此處設定的選項也會套用至純文字、Transact-SQL 和 XML 編輯器，不過，藉由展開這些語言的子資料夾，然後選取其選項頁面，您就可以個別為這些編輯器設定選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="985cb-109">如果您使用這個對話方塊設定選項，但是想要為純文字、Transact-SQL 或 XML 編輯器進行不同的設定，則必須先在 [所有語言]\*\*\*\* 對話方塊中套用您的選取範圍，再設定這些編輯器的選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-109">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="985cb-110">某些編輯器可能不支援此頁面中列出的全部選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-110">Some editors may not support all of the options listed on this page.</span></span> <span data-ttu-id="985cb-111">有些程式語言在 [選項]\*\*\*\* 對話方塊的 [一般]\*\*\*\* 頁面上，已經選取的選項會顯示灰色核取記號，但有些程式語言則不會。</span><span class="sxs-lookup"><span data-stu-id="985cb-111">A shaded check mark is displayed when an option has been selected on the **General** page of the **Options** dialog box for some programming languages, but not for others.</span></span>  
  
## <a name="statement-completion"></a><span data-ttu-id="985cb-112">陳述式完成</span><span class="sxs-lookup"><span data-stu-id="985cb-112">Statement Completion</span></span>  
 <span data-ttu-id="985cb-113">**自動列出成員**</span><span class="sxs-lookup"><span data-stu-id="985cb-113">**Auto list members**</span></span>  
 <span data-ttu-id="985cb-114">顯示您在編輯器中輸入的可用成員、屬性或值的快顯清單。</span><span class="sxs-lookup"><span data-stu-id="985cb-114">Display pop-up lists of available members, properties, or values as you type in the editor.</span></span> <span data-ttu-id="985cb-115">從快顯清單中選擇任何項目，以將項目插入程式碼。</span><span class="sxs-lookup"><span data-stu-id="985cb-115">Choose any item from the pop-up list to insert the item into your code.</span></span> <span data-ttu-id="985cb-116">選取此核取方塊會啟用 [隱藏進階成員]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-116">Selecting this check box enables the **Hide advanced members** option.</span></span>  
  
 <span data-ttu-id="985cb-117">**隱藏進階成員**</span><span class="sxs-lookup"><span data-stu-id="985cb-117">**Hide advanced members**</span></span>  
 <span data-ttu-id="985cb-118">透過只顯示那些最常使用的項目來縮短快顯陳述式完成清單。</span><span class="sxs-lookup"><span data-stu-id="985cb-118">Shorten pop-up statement completion lists by displaying only those items most commonly used.</span></span> <span data-ttu-id="985cb-119">從清單中篩選其他項目。</span><span class="sxs-lookup"><span data-stu-id="985cb-119">Other items are filtered from the list.</span></span> <span data-ttu-id="985cb-120">如果沒有成員標示為進階成員，就不能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-120">This option will not be available if no members are marked as advanced members.</span></span>  
  
 <span data-ttu-id="985cb-121">**參數資訊**</span><span class="sxs-lookup"><span data-stu-id="985cb-121">**Parameter information**</span></span>  
 <span data-ttu-id="985cb-122">將目前宣告或程序的完整語法及其所有可用的參數顯示在編輯器插入點的左邊。</span><span class="sxs-lookup"><span data-stu-id="985cb-122">Display the complete syntax for the current declaration or procedure to the left of the insertion point in the editor with all of its available parameters.</span></span> <span data-ttu-id="985cb-123">您可以指派的下一個參數會以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="985cb-123">The next parameter you can assign is displayed in bold.</span></span>  
  
## <a name="settings"></a><span data-ttu-id="985cb-124">設定</span><span class="sxs-lookup"><span data-stu-id="985cb-124">Settings</span></span>  
 <span data-ttu-id="985cb-125">**啟用虛擬空間**</span><span class="sxs-lookup"><span data-stu-id="985cb-125">**Enable virtual space**</span></span>  
 <span data-ttu-id="985cb-126">將註解放在程式碼旁邊的一致位置上。</span><span class="sxs-lookup"><span data-stu-id="985cb-126">Position comments at a consistent point next to your code.</span></span> <span data-ttu-id="985cb-127">選取這個核取方塊時，您可將游標放在資料列的最後一個字元後面。</span><span class="sxs-lookup"><span data-stu-id="985cb-127">When this check box is selected, you can position the cursor beyond the last character in the row.</span></span> <span data-ttu-id="985cb-128">輸入時，會自動在插入點加入 Tab 鍵或空格，以完成資料列。</span><span class="sxs-lookup"><span data-stu-id="985cb-128">When you type, tabs or spaces are automatically added to complete the row to the insertion point.</span></span>  
  
 <span data-ttu-id="985cb-129">**自動換行**</span><span class="sxs-lookup"><span data-stu-id="985cb-129">**Word wrap**</span></span>  
 <span data-ttu-id="985cb-130">在下一行顯示横向超出可檢視編輯器區域之行的任何部分。</span><span class="sxs-lookup"><span data-stu-id="985cb-130">Display on the next line any portion of a line that extends horizontally beyond the viewable editor area.</span></span> <span data-ttu-id="985cb-131">選取這個核取方塊將啟用 **[顯示自動換行的視覺化圖像]** 選項。</span><span class="sxs-lookup"><span data-stu-id="985cb-131">Selecting this check box enables the **Show visual glyphs for word wrap** option.</span></span>  
  
 <span data-ttu-id="985cb-132">**顯示自動換行的視覺化圖像**</span><span class="sxs-lookup"><span data-stu-id="985cb-132">**Show visual glyphs for word wrap**</span></span>  
 <span data-ttu-id="985cb-133">顯示換行箭頭指標，其中過長的行就會自動換行到第二行。</span><span class="sxs-lookup"><span data-stu-id="985cb-133">Display a return-arrow indicator where a long line wraps onto a second line.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="985cb-134">這些提醒箭頭不會加入您的程式碼中，且不會列印。</span><span class="sxs-lookup"><span data-stu-id="985cb-134">These reminder arrows are not added to your code, and they do not print.</span></span> <span data-ttu-id="985cb-135">它們僅供參考。</span><span class="sxs-lookup"><span data-stu-id="985cb-135">They are for reference only.</span></span> <span data-ttu-id="985cb-136">不是所有類型的編輯器都有此功能。</span><span class="sxs-lookup"><span data-stu-id="985cb-136">This feature is not available in all types of editors.</span></span>  
  
 <span data-ttu-id="985cb-137">**沒有選取項目時，請套用剪下/複製命令至空白行**</span><span class="sxs-lookup"><span data-stu-id="985cb-137">**Apply Cut/Copy commands to blank lines when there is no selection**</span></span>  
 <span data-ttu-id="985cb-138">設定當您將插入點放置在空白行上、不選取任何內容，然後按一下 **[複製]** 或 **[剪下]** 時的編輯器行為。</span><span class="sxs-lookup"><span data-stu-id="985cb-138">Set the behavior of the editor when you place the insertion point on a blank line, select nothing, and then click **Copy** or **Cut**.</span></span>  
  
 <span data-ttu-id="985cb-139">如果選取此核取方塊，就會複製或剪下空白行。</span><span class="sxs-lookup"><span data-stu-id="985cb-139">When this check box is selected, the blank line is copied or cut.</span></span> <span data-ttu-id="985cb-140">接著，如果您按一下 **[貼上]**，就會插入一個新的空白行。</span><span class="sxs-lookup"><span data-stu-id="985cb-140">If you then click **Paste**, a new, blank line is inserted.</span></span>  
  
 <span data-ttu-id="985cb-141">如果清除此核取方塊，就不會複製或剪下任何內容。</span><span class="sxs-lookup"><span data-stu-id="985cb-141">When this check box is cleared, nothing is copied or cut.</span></span> <span data-ttu-id="985cb-142">接著，您按一下 **[貼上]**，就會貼上最近複製的內容。</span><span class="sxs-lookup"><span data-stu-id="985cb-142">If you then click **Paste**, the content most recently copied is pasted.</span></span> <span data-ttu-id="985cb-143">如果沒有進行複製，就不會有貼上動作。</span><span class="sxs-lookup"><span data-stu-id="985cb-143">If nothing has been copied, nothing is pasted.</span></span>  
  
 <span data-ttu-id="985cb-144">當行不是空白時，此設定對 [複製]\*\*\*\* 或 [剪下]\*\*\*\* 命令沒有作用。</span><span class="sxs-lookup"><span data-stu-id="985cb-144">This setting has no effect on the **Copy** or **Cut** commands when a line is not blank.</span></span> <span data-ttu-id="985cb-145">如果沒有選取內容，就會複製或剪下整個行。</span><span class="sxs-lookup"><span data-stu-id="985cb-145">If nothing is selected, the entire line is copied or cut.</span></span> <span data-ttu-id="985cb-146">接著，如果您按一下 **[貼上]**，就會貼上整行的文字與其結束字元。</span><span class="sxs-lookup"><span data-stu-id="985cb-146">If you then click **Paste**, the text of the entire line and its end line character are pasted.</span></span>  
  
## <a name="display"></a><span data-ttu-id="985cb-147">顯示</span><span class="sxs-lookup"><span data-stu-id="985cb-147">Display</span></span>  
 <span data-ttu-id="985cb-148">**行號**</span><span class="sxs-lookup"><span data-stu-id="985cb-148">**Line numbers**</span></span>  
 <span data-ttu-id="985cb-149">在每一行程式碼旁邊顯示行號。</span><span class="sxs-lookup"><span data-stu-id="985cb-149">Display a line number next to each line of code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="985cb-150">這些行號不會加入您的程式碼中，且不會列印。</span><span class="sxs-lookup"><span data-stu-id="985cb-150">These line numbers are not added to your code, and they do not print.</span></span> <span data-ttu-id="985cb-151">它們僅供參考。</span><span class="sxs-lookup"><span data-stu-id="985cb-151">They are for reference only.</span></span>  
  
 <span data-ttu-id="985cb-152">**啟用按一下方式的 URL 導覽**</span><span class="sxs-lookup"><span data-stu-id="985cb-152">**Enable single-click URL navigation**</span></span>  
 <span data-ttu-id="985cb-153">當游標在編輯器的 URL 上方時，會變成手指符號。</span><span class="sxs-lookup"><span data-stu-id="985cb-153">Change the cursor to a symbol of a pointing hand when it passes over a URL in the editor.</span></span> <span data-ttu-id="985cb-154">按一下 URL 即可在 Web 瀏覽器中顯示該頁面。</span><span class="sxs-lookup"><span data-stu-id="985cb-154">You can click the URL to display the indicated page in your Web browser.</span></span>  
  
 <span data-ttu-id="985cb-155">**巡覽列**</span><span class="sxs-lookup"><span data-stu-id="985cb-155">**Navigation bar**</span></span>  
 <span data-ttu-id="985cb-156">在程式碼編輯器頂端顯示導覽列。</span><span class="sxs-lookup"><span data-stu-id="985cb-156">Display a navigation bar at the top of the Code Editor.</span></span> <span data-ttu-id="985cb-157">使用其 [物件]\*\*\*\* 與 [程序]\*\*\*\* 下拉式清單來選擇程式碼中的特定物件，從它的程序中選取，然後插入選取之程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="985cb-157">Use its **Objects**and **Procedures** drop-down lists to choose a particular object in your code, select from its procedures, and insert an instance of the selected procedure.</span></span> <span data-ttu-id="985cb-158">並非所有的程式碼類型都可以使用導覽列。</span><span class="sxs-lookup"><span data-stu-id="985cb-158">The navigation baris not available for all code types.</span></span>  
  
  
