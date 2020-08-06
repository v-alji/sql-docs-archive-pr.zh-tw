---
title: 尋找和取代
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find and Replace dialog box
ms.assetid: 09297893-d80b-4c88-86b4-52bfb639e521
author: rothja
ms.author: jroth
ms.openlocfilehash: 9735c2c7271382e3b25ce2b50299153f16882ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606226"
---
# <a name="find-and-replace"></a><span data-ttu-id="7cfee-102">尋找和取代</span><span class="sxs-lookup"><span data-stu-id="7cfee-102">Find and Replace</span></span>
  <span data-ttu-id="7cfee-103">使用 **[尋找和取代]** 對話方塊尋找檔案內的文字，並選擇性地取代。</span><span class="sxs-lookup"><span data-stu-id="7cfee-103">Use the **Find and Replace** dialog box to locate text within a file and optionally replace it.</span></span> <span data-ttu-id="7cfee-104">**[尋找和取代]** 對話方塊的版本不同，選項也會有些微差異，視對話方塊以何種方式開啟而定。</span><span class="sxs-lookup"><span data-stu-id="7cfee-104">Versions of the **Find and Replace** dialog box with slightly different options can appear, depending on how the dialog box was opened.</span></span> <span data-ttu-id="7cfee-105">在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，然後按一下 **[快速尋找]** 以開啟有尋找選項，但沒有取代選項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-105">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find** to open the dialog box with find options, but without replace options.</span></span> <span data-ttu-id="7cfee-106">在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，然後按一下 **[快速取代]** 以開啟同時具有尋找和取代選項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-106">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Replace** to open the dialog box with both find options and replace options.</span></span>  
  
 <span data-ttu-id="7cfee-107">工具列按鈕與快速鍵也可用來開啟 **[尋找和取代]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-107">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="7cfee-108">尋找目標</span><span class="sxs-lookup"><span data-stu-id="7cfee-108">Find What</span></span>  
 <span data-ttu-id="7cfee-109">這些控制項可以讓您指定符合的字串或運算式。</span><span class="sxs-lookup"><span data-stu-id="7cfee-109">These controls enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="7cfee-110">**尋找目標**</span><span class="sxs-lookup"><span data-stu-id="7cfee-110">**Find what**</span></span>  
 <span data-ttu-id="7cfee-111">鍵入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="7cfee-111">Type the text to search for.</span></span> <span data-ttu-id="7cfee-112">對話方塊會使用在開啟對話方塊之前，資料指標所選取的文字、鄰近的文字，或先前搜尋過的文字，嘗試填入可能要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="7cfee-112">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="7cfee-113">您可以重複使用最後 20 個搜尋字串的其中之一，方法是從此下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="7cfee-113">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="7cfee-114">**[具有萬用字元的字串]**</span><span class="sxs-lookup"><span data-stu-id="7cfee-114">**[string with wildcards]**</span></span>  
 <span data-ttu-id="7cfee-115">如果您要在搜尋字串中，使用如星號 (`*`) 和問號 (`?`) 等的萬用字元，請選取 [尋找選項] 下的 [使用] 核取方塊，然後按一下 [萬用字元]。</span><span class="sxs-lookup"><span data-stu-id="7cfee-115">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="7cfee-116">**[規則運算式]**</span><span class="sxs-lookup"><span data-stu-id="7cfee-116">**[regular expression]**</span></span>  
 <span data-ttu-id="7cfee-117">若要讓搜尋引擎將搜尋字串解譯為規則運算式，請選取 [尋找選項] 下的 [使用] 核取方塊，然後按一下 [規則運算式]。</span><span class="sxs-lookup"><span data-stu-id="7cfee-117">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="7cfee-118">**運算式產生器**</span><span class="sxs-lookup"><span data-stu-id="7cfee-118">**Expression Builder**</span></span>  
 <span data-ttu-id="7cfee-119">當您在 [尋找選項] 中選取 [使用] 核取方塊時，即可使用 [尋找目標] 方塊旁的三角形按鈕。</span><span class="sxs-lookup"><span data-stu-id="7cfee-119">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="7cfee-120">按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。</span><span class="sxs-lookup"><span data-stu-id="7cfee-120">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="7cfee-121">在此清單中選擇任何項目，會加入 **[尋找目標]** 方塊中所指定的字串。</span><span class="sxs-lookup"><span data-stu-id="7cfee-121">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="7cfee-122">取代為</span><span class="sxs-lookup"><span data-stu-id="7cfee-122">Replace With</span></span>  
 <span data-ttu-id="7cfee-123">這些控制項可以讓您指定要插入的字串，以取代相符的字串或運算式。</span><span class="sxs-lookup"><span data-stu-id="7cfee-123">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="7cfee-124">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="7cfee-124">**Replace with**</span></span>  
 <span data-ttu-id="7cfee-125">若要以另一個字串來取代 [尋找目標]  中所指定之字串的執行個體，請在此欄位中輸入取代字串。</span><span class="sxs-lookup"><span data-stu-id="7cfee-125">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="7cfee-126">若要刪除 **[尋找目標]** 中所指定之文字的執行個體，請保留此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="7cfee-126">To delete instances of the text specified in **Find what**, leave this field blank.</span></span> <span data-ttu-id="7cfee-127">選取下拉式清單，即可顯示最後輸入的 20 個項目。</span><span class="sxs-lookup"><span data-stu-id="7cfee-127">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="7cfee-128">若要將規則運算式包含在 **[取代成]** 方塊裡所指定的字串中，請按一下 **[使用]** 核取方塊，然後按一下 **[規則運算式]** 。</span><span class="sxs-lookup"><span data-stu-id="7cfee-128">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span> <span data-ttu-id="7cfee-129">只有透過按一下 **[快速取代]** 的方式開啟此對話方塊，才會出現此方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-129">This box only appears if this dialog box was opened by clicked **Quick Replace**.</span></span>  
  
 <span data-ttu-id="7cfee-130">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="7cfee-130">**Replace with**</span></span>  
 <span data-ttu-id="7cfee-131">若要以另一個字串來取代 [尋找目標]  方塊中所指定之字串的執行個體，請在此欄位中輸入取代字串。</span><span class="sxs-lookup"><span data-stu-id="7cfee-131">To replace instances of the string specified in the **Find what** box with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="7cfee-132">若要刪除 **[尋找目標]** 方塊中所指定之字串的執行個體，請保留此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="7cfee-132">To delete instances of the string specified in the **Find what** box, leave this field blank.</span></span> <span data-ttu-id="7cfee-133">選取下拉式清單，即可顯示最後輸入的 20 個項目。</span><span class="sxs-lookup"><span data-stu-id="7cfee-133">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="7cfee-134">若要將規則運算式包含在 **[取代成]** 方塊裡所指定的字串中，請按一下 **[使用]** 核取方塊，然後按一下 **[規則運算式]** 。</span><span class="sxs-lookup"><span data-stu-id="7cfee-134">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="7cfee-135">**運算式產生器**</span><span class="sxs-lookup"><span data-stu-id="7cfee-135">**Expression Builder**</span></span>  
 <span data-ttu-id="7cfee-136">當您在 [尋找選項] 中選取 [使用] 核取方塊時，即可使用 [取代成] 方塊旁的三角形按鈕。</span><span class="sxs-lookup"><span data-stu-id="7cfee-136">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="7cfee-137">按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。</span><span class="sxs-lookup"><span data-stu-id="7cfee-137">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="7cfee-138">按一下此清單中的任何項目，將其加入 **[取代成]** 方塊中所指定的字串。</span><span class="sxs-lookup"><span data-stu-id="7cfee-138">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="7cfee-139">**Replace**</span><span class="sxs-lookup"><span data-stu-id="7cfee-139">**Replace**</span></span>  
 <span data-ttu-id="7cfee-140">按一下此按鈕，以 [取代成] 方塊中所指定的字串，取代 [尋找目標] 方塊中所指定之字串的目前執行個體，並於 [查詢] 中所指定的範圍內尋找下一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-140">Click this button to replace the current instance of the string specified in the **Find what** box with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="7cfee-141">**全部取代**</span><span class="sxs-lookup"><span data-stu-id="7cfee-141">**Replace all**</span></span>  
 <span data-ttu-id="7cfee-142">按一下此按鈕，即可在 [查詢] 方塊中所指定之範圍內的所有檔案中，以 [取代成] 方塊中所指定的字串，取代 [尋找目標] 方塊中所指定之字串的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-142">Click this button to replace all instances of the string specified in the **Find what** box with the string specified in the **Replace with** box, in all files within the scope specified in the **Look in** box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7cfee-143">確定 [查詢]  已設定為僅包含您要修改的那些檔案。</span><span class="sxs-lookup"><span data-stu-id="7cfee-143">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="7cfee-144">顯示的提醒會包含 **[保持已修改的檔案開啟]** 選項。</span><span class="sxs-lookup"><span data-stu-id="7cfee-144">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="7cfee-145">若要保留 **[恢復]** 選項，您必須選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7cfee-145">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="7cfee-146">**[恢復]** 功能僅適用於檔案在修改之後仍保持開啟可供編輯的檔案。</span><span class="sxs-lookup"><span data-stu-id="7cfee-146">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="7cfee-147">**略過檔案**</span><span class="sxs-lookup"><span data-stu-id="7cfee-147">**Skip File**</span></span>  
 <span data-ttu-id="7cfee-148">當 [查詢]  所指定的值包含多個檔案時，即可使用。</span><span class="sxs-lookup"><span data-stu-id="7cfee-148">Becomes available when the value specified for **Look in** includes multiple files.</span></span> <span data-ttu-id="7cfee-149">如果不要搜尋或修改目前的檔案，請按一下此按鈕。</span><span class="sxs-lookup"><span data-stu-id="7cfee-149">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="7cfee-150">搜尋會繼續在 **[查詢]** 清單中的下一個檔案進行。</span><span class="sxs-lookup"><span data-stu-id="7cfee-150">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="7cfee-151">查詢</span><span class="sxs-lookup"><span data-stu-id="7cfee-151">Look In</span></span>  
 <span data-ttu-id="7cfee-152">**Look in**</span><span class="sxs-lookup"><span data-stu-id="7cfee-152">**Look in**</span></span>  
 <span data-ttu-id="7cfee-153">選取位置以尋找 [尋找目標]  中指定的文字。</span><span class="sxs-lookup"><span data-stu-id="7cfee-153">Select the location to look for the text specified in **Find what**.</span></span> <span data-ttu-id="7cfee-154">選項包括 **[目前的文件]** ，這會搜尋開啟對話方塊時的焦點文件視窗；以及 **[所有開啟的文件]** ，就會搜尋目前在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中開啟的所有文件視窗。</span><span class="sxs-lookup"><span data-stu-id="7cfee-154">Options are **Current Document**, which searches the document window that had focus when the dialog box was opened, and **All Open Documents**, which searches all document windows that are currently open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="7cfee-155">[使用]</span><span class="sxs-lookup"><span data-stu-id="7cfee-155">Find Options</span></span>  
 <span data-ttu-id="7cfee-156">您可以展開或摺疊 **[尋找選項]** 區段。</span><span class="sxs-lookup"><span data-stu-id="7cfee-156">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="7cfee-157">您可以選取或清除下列選項。</span><span class="sxs-lookup"><span data-stu-id="7cfee-157">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="7cfee-158">**大小寫須相符**</span><span class="sxs-lookup"><span data-stu-id="7cfee-158">**Match case**</span></span>  
 <span data-ttu-id="7cfee-159">如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示內容和大小寫均與 [尋找目標]  中所指定之字串相符的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-159">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="7cfee-160">例如，選取 **[大小寫須相符]** 核取方塊來搜尋「 **MyObject** 」，將會傳回「MyObject」，但不會傳回「myobject」或「MYOBJECT」。</span><span class="sxs-lookup"><span data-stu-id="7cfee-160">For example, a search for "**MyObject**" with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="7cfee-161">**全字拼寫須相符**</span><span class="sxs-lookup"><span data-stu-id="7cfee-161">**Match whole word**</span></span>  
 <span data-ttu-id="7cfee-162">如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示整個字串與 [尋找目標]  中所指定之字串相符的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-162">When selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="7cfee-163">例如，搜尋 **MyObject** ，將會傳回「MyObject」，但不會傳回「CMyObject」或「MyObjectC」。</span><span class="sxs-lookup"><span data-stu-id="7cfee-163">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="7cfee-164">**向上搜尋**</span><span class="sxs-lookup"><span data-stu-id="7cfee-164">**Search up**</span></span>  
 <span data-ttu-id="7cfee-165">從游標位置朝文件開始處進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="7cfee-165">Search from the cursor location towards the beginning of the document.</span></span>  
  
 <span data-ttu-id="7cfee-166">**搜尋隱藏文字**</span><span class="sxs-lookup"><span data-stu-id="7cfee-166">**Search hidden text**</span></span>  
 <span data-ttu-id="7cfee-167">找出隱藏和摺疊文字的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-167">Locate instances of the text that are concealed and collapsed text.</span></span>  
  
 <span data-ttu-id="7cfee-168">**使用**</span><span class="sxs-lookup"><span data-stu-id="7cfee-168">**Use**</span></span>  
 <span data-ttu-id="7cfee-169">指出如何解譯在 [尋找目標]  或 [取代成]  文字方塊中所輸入的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="7cfee-169">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="7cfee-170">選項包含 **[萬用字元]** 和 **[規則運算式]** 。</span><span class="sxs-lookup"><span data-stu-id="7cfee-170">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="7cfee-171">**[規則運算式]**</span><span class="sxs-lookup"><span data-stu-id="7cfee-171">**Regular Expressions**</span></span>  
 <span data-ttu-id="7cfee-172">定義要比對之文字模式的特殊標記法。</span><span class="sxs-lookup"><span data-stu-id="7cfee-172">Special notations define patterns of text to match.</span></span> <span data-ttu-id="7cfee-173">如需清單，請參閱 [使用規則運算式搜尋文字](search-text-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7cfee-173">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="7cfee-174">**萬用字元**</span><span class="sxs-lookup"><span data-stu-id="7cfee-174">**Wildcards**</span></span>  
 <span data-ttu-id="7cfee-175">例如星號 (`*`) 和問號 (`?`) 等特殊字元，代表一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="7cfee-175">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="7cfee-176">如需清單，請參閱 [使用萬用字元搜尋文字](search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="7cfee-176">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="7cfee-177">**找下一個**</span><span class="sxs-lookup"><span data-stu-id="7cfee-177">**Find Next**</span></span>  
 <span data-ttu-id="7cfee-178">開始在 [尋找目標]  方塊中搜尋文字。</span><span class="sxs-lookup"><span data-stu-id="7cfee-178">Begins searching for the text in the **Find what** box.</span></span>  
  
 <span data-ttu-id="7cfee-179">**Replace**</span><span class="sxs-lookup"><span data-stu-id="7cfee-179">**Replace**</span></span>  
 <span data-ttu-id="7cfee-180">按一下此按鈕，以 [取代成] 中所指定的字串，取代 [尋找目標] 中所指定之字串的目前執行個體，並於 [查詢] 中所指定的範圍內尋找下一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-180">Click this button to replace the current instance of the string specified in **Find what** with the string specified in **Replace with**, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="7cfee-181">**Replace All**</span><span class="sxs-lookup"><span data-stu-id="7cfee-181">**Replace All**</span></span>  
 <span data-ttu-id="7cfee-182">選擇此按鈕，即可在 [查詢] 中所指定之範圍內的所有檔案中，以 [取代成] 中所指定的字串，取代 [尋找目標] 中所指定之字串的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cfee-182">Choose this button to replace all instances of the string specified in **Find what** with the string specified in **Replace with**, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7cfee-183">確定 [查詢]  已設定為僅包含您要修改的那些檔案。</span><span class="sxs-lookup"><span data-stu-id="7cfee-183">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="7cfee-184">尋找和取代檢視</span><span class="sxs-lookup"><span data-stu-id="7cfee-184">Find and Replace Views</span></span>  
 <span data-ttu-id="7cfee-185">[尋找和檢視] 視窗上方的索引標籤包含 **[檢視]** 功能表。</span><span class="sxs-lookup"><span data-stu-id="7cfee-185">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="7cfee-186">這些功能表可以讓您選擇要在使用中窗格裡顯示的一組欄位。</span><span class="sxs-lookup"><span data-stu-id="7cfee-186">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="7cfee-187">您可以讓 **[尋找和取代]** 視窗停駐在方便存取的位置，然後在各索引標籤之間和各檢視之間進行變更，以執行任何類型的尋找或取代作業。</span><span class="sxs-lookup"><span data-stu-id="7cfee-187">You can leave the **Find and Replace** window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="7cfee-188">**[快速尋找]**</span><span class="sxs-lookup"><span data-stu-id="7cfee-188">**Quick Find**</span></span>  
 <span data-ttu-id="7cfee-189">此工具列索引標籤會將對話方塊變更為 [快速尋找]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-189">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="7cfee-190">**檔案中尋找**</span><span class="sxs-lookup"><span data-stu-id="7cfee-190">**Find in Files**</span></span>  
 <span data-ttu-id="7cfee-191">此工具列索引標籤會將對話方塊變更為 [檔案中尋找]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cfee-191">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="7cfee-192">**[快速取代]**</span><span class="sxs-lookup"><span data-stu-id="7cfee-192">**Quick Replace**</span></span>  
 <span data-ttu-id="7cfee-193">此工具列索引標籤會將對話方塊變更為 [快速取代]  對話方塊</span><span class="sxs-lookup"><span data-stu-id="7cfee-193">This toolbar tab changes the dialog box to a **Quick Replace** dialog box</span></span>  
  
 <span data-ttu-id="7cfee-194">**檔案中取代**</span><span class="sxs-lookup"><span data-stu-id="7cfee-194">**Replace in Files**</span></span>  
 <span data-ttu-id="7cfee-195">此工具列索引標籤會將對話方塊變更為 [檔案中取代]  對話方塊</span><span class="sxs-lookup"><span data-stu-id="7cfee-195">This toolbar tab changes the dialog box to a **Replace in Files** dialog box</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfee-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cfee-196">See Also</span></span>  
 [<span data-ttu-id="7cfee-197">SQL Server Management Studio 鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="7cfee-197">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
