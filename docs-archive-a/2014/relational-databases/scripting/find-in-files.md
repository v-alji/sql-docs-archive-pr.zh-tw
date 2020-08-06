---
title: 檔案中尋找
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find in Files dialog box
ms.assetid: bf92770a-33df-43ef-85ad-5a9223649b98
author: rothja
ms.author: jroth
ms.openlocfilehash: a7bd3051817198fb22e2bf7e96393ddf2023b703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606225"
---
# <a name="find-in-files"></a><span data-ttu-id="d8723-102">檔案中尋找</span><span class="sxs-lookup"><span data-stu-id="d8723-102">Find in Files</span></span>
  <span data-ttu-id="d8723-103">[尋找和取代] 視窗的 [檔案中尋找]  索引標籤，可以讓您在指定檔案集的程式碼中搜尋字串或運算式。</span><span class="sxs-lookup"><span data-stu-id="d8723-103">The **Find in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression.</span></span> <span data-ttu-id="d8723-104">找到的相符結果與採取的動作會列在 [結果選項]  所選取的 [尋找結果] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="d8723-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="d8723-105">工具列按鈕與快速鍵也可用來開啟 **[尋找和取代]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d8723-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
 <span data-ttu-id="d8723-106">下列章節列出可在 [檔案中尋找]  索引標籤上使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="d8723-106">The sections that follow list controls available on the **Find in Files** tab.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="d8723-107">尋找目標</span><span class="sxs-lookup"><span data-stu-id="d8723-107">Find What</span></span>  
 <span data-ttu-id="d8723-108">[檔案中尋找]  索引標籤上的這些控制項，可以讓您指定將要比對的字串或運算式。</span><span class="sxs-lookup"><span data-stu-id="d8723-108">These controls on the **Find in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="d8723-109">**尋找目標**</span><span class="sxs-lookup"><span data-stu-id="d8723-109">**Find what**</span></span>  
 <span data-ttu-id="d8723-110">鍵入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="d8723-110">Type the text to search for.</span></span> <span data-ttu-id="d8723-111">對話方塊會使用在開啟對話方塊之前，資料指標所選取的文字、鄰近的文字，或先前搜尋過的文字，嘗試填入可能要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="d8723-111">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="d8723-112">您可以重複使用最後 20 個搜尋字串的其中之一，方法是從此下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="d8723-112">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="d8723-113">**[具有萬用字元的字串]**</span><span class="sxs-lookup"><span data-stu-id="d8723-113">**[string with wildcards]**</span></span>  
 <span data-ttu-id="d8723-114">如果您要在搜尋字串中，使用如星號 (`*`) 和問號 (`?`) 等的萬用字元，請選取 [尋找選項] 下的 [使用] 核取方塊，然後按一下 [萬用字元]。</span><span class="sxs-lookup"><span data-stu-id="d8723-114">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="d8723-115">**[規則運算式]**</span><span class="sxs-lookup"><span data-stu-id="d8723-115">**[regular expression]**</span></span>  
 <span data-ttu-id="d8723-116">若要讓搜尋引擎將搜尋字串解譯為規則運算式，請選取 [尋找選項] 下的 [使用] 核取方塊，然後按一下 [規則運算式]。</span><span class="sxs-lookup"><span data-stu-id="d8723-116">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="d8723-117">**運算式產生器**</span><span class="sxs-lookup"><span data-stu-id="d8723-117">**Expression Builder**</span></span>  
 <span data-ttu-id="d8723-118">當您在 [尋找選項] 中選取 [使用] 核取方塊時，即可使用 [尋找目標] 方塊旁的三角形按鈕。</span><span class="sxs-lookup"><span data-stu-id="d8723-118">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="d8723-119">按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。</span><span class="sxs-lookup"><span data-stu-id="d8723-119">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="d8723-120">在此清單中選擇任何項目，將它加入 [尋找目標]  字串。</span><span class="sxs-lookup"><span data-stu-id="d8723-120">Choosing any item from this list adds it to the **Find what** string.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="d8723-121">查詢</span><span class="sxs-lookup"><span data-stu-id="d8723-121">Look In</span></span>  
 <span data-ttu-id="d8723-122">從 [查詢]  下拉式清單中選擇的選項會決定 [檔案中尋找]  僅搜尋目前使用中的檔案，或搜尋儲存在特定資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d8723-122">The option chosen from the **Look in** drop-down list determines whether **Find in Files** searches only in currently active files or in all files stored within certain folders.</span></span> <span data-ttu-id="d8723-123">從清單中選取搜尋範圍，輸入資料夾路徑，或按一下 [瀏覽]  按鈕以顯示 [Custom Directory Set (自訂目錄集)]  對話方塊，然後選擇一組要搜尋的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d8723-123">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set Dialog Box** and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8723-124">如果所選的 [查詢]  選項導致您搜尋已從原始程式碼控制簽出的檔案，則系統僅會搜尋已下載至本機電腦的檔案版本。</span><span class="sxs-lookup"><span data-stu-id="d8723-124">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="d8723-125">**Look in**</span><span class="sxs-lookup"><span data-stu-id="d8723-125">**Look in**</span></span>  
 <span data-ttu-id="d8723-126">從清單中選取預先定義的搜尋範圍，或使用 [Custom Directory Set (自訂目錄集)]  對話方塊來輸入您自己的目錄集。</span><span class="sxs-lookup"><span data-stu-id="d8723-126">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="d8723-127">**目前的文件**</span><span class="sxs-lookup"><span data-stu-id="d8723-127">**Current Document**</span></span>  
 <span data-ttu-id="d8723-128">當文件在編輯器中開啟時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d8723-128">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="d8723-129">它只在使用中文件內搜尋 [尋找目標]  中的字串。</span><span class="sxs-lookup"><span data-stu-id="d8723-129">It searches only the active document for the string in **Find what**.</span></span>  
  
 <span data-ttu-id="d8723-130">**所有開啟的文件**</span><span class="sxs-lookup"><span data-stu-id="d8723-130">**All Open Documents**</span></span>  
 <span data-ttu-id="d8723-131">搜尋所有目前已開啟的檔案以供編輯。</span><span class="sxs-lookup"><span data-stu-id="d8723-131">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="d8723-132">**目前的專案**</span><span class="sxs-lookup"><span data-stu-id="d8723-132">**Current Project**</span></span>  
 <span data-ttu-id="d8723-133">搜尋使用中專案的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d8723-133">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="d8723-134">**整個方案**</span><span class="sxs-lookup"><span data-stu-id="d8723-134">**Entire Solution**</span></span>  
 <span data-ttu-id="d8723-135">搜尋使用中方案的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d8723-135">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="d8723-136">**包含子資料夾**</span><span class="sxs-lookup"><span data-stu-id="d8723-136">**Include subfolders**</span></span>  
 <span data-ttu-id="d8723-137">指定也要搜尋在 [查詢]  中指定之資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="d8723-137">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="d8723-138">這需要自訂目錄集。</span><span class="sxs-lookup"><span data-stu-id="d8723-138">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="d8723-139">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="d8723-139">**Browse**</span></span>  
 <span data-ttu-id="d8723-140">按一下此按鈕即可顯示 [Custom Directory Set (自訂目錄集)]  對話方塊，您可以在其中組合、編輯、儲存以及選取目錄的命名集，以輸入到 [查詢]  方塊中。</span><span class="sxs-lookup"><span data-stu-id="d8723-140">Click this button to display the **Custom Directory Set** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="d8723-141">[使用]</span><span class="sxs-lookup"><span data-stu-id="d8723-141">Find Options</span></span>  
 <span data-ttu-id="d8723-142">您可以展開或摺疊 **[尋找選項]** 區段。</span><span class="sxs-lookup"><span data-stu-id="d8723-142">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="d8723-143">您可以選取或清除下列選項。</span><span class="sxs-lookup"><span data-stu-id="d8723-143">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="d8723-144">**大小寫須相符**</span><span class="sxs-lookup"><span data-stu-id="d8723-144">**Match case**</span></span>  
 <span data-ttu-id="d8723-145">如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示內容和大小寫均與 [尋找目標]  中所指定之字串相符的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8723-145">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="d8723-146">例如，選取 [大小寫須相符] 核取方塊來搜尋 **MyObject**，將會傳回「MyObject」，但不會傳回「myobject」或「MYOBJECT」。</span><span class="sxs-lookup"><span data-stu-id="d8723-146">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="d8723-147">**全字拼寫須相符**</span><span class="sxs-lookup"><span data-stu-id="d8723-147">**Match whole word**</span></span>  
 <span data-ttu-id="d8723-148">如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示整個字串與 [尋找目標]  中所指定之字串相符的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8723-148">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="d8723-149">例如，搜尋 **MyObject** ，將會傳回「MyObject」，但不會傳回「CMyObject」或「MyObjectC」。</span><span class="sxs-lookup"><span data-stu-id="d8723-149">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="d8723-150">**使用**</span><span class="sxs-lookup"><span data-stu-id="d8723-150">**Use**</span></span>  
 <span data-ttu-id="d8723-151">指出如何解譯在 [尋找目標]  或 [取代成]  文字方塊中所輸入的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="d8723-151">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="d8723-152">選項包含 **[萬用字元]** 和 **[規則運算式]** 。</span><span class="sxs-lookup"><span data-stu-id="d8723-152">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="d8723-153">**[規則運算式]**</span><span class="sxs-lookup"><span data-stu-id="d8723-153">**Regular Expressions**</span></span>  
 <span data-ttu-id="d8723-154">定義要比對之文字模式的特殊標記法。</span><span class="sxs-lookup"><span data-stu-id="d8723-154">Special notations define patterns of text to match.</span></span> <span data-ttu-id="d8723-155">如需清單，請參閱 [使用規則運算式搜尋文字](search-text-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d8723-155">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="d8723-156">**萬用字元**</span><span class="sxs-lookup"><span data-stu-id="d8723-156">**Wildcards**</span></span>  
 <span data-ttu-id="d8723-157">例如星號 (`*`) 和問號 (`?`) 等特殊字元，代表一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="d8723-157">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="d8723-158">如需清單，請參閱 [使用萬用字元搜尋文字](search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="d8723-158">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="d8723-159">**尋找下列檔案類型**</span><span class="sxs-lookup"><span data-stu-id="d8723-159">**Look at these file types**</span></span>  
 <span data-ttu-id="d8723-160">此清單指出要在 [查詢]  所指定之目錄中搜尋的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="d8723-160">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="d8723-161">如果此欄位保留空白，則會搜尋 [查詢]  所指定之目錄中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d8723-161">If this field is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="d8723-162">若要尋找特定類型的檔案，請輸入星號萬用字元 (`*`) 作為檔案名稱，接著輸入半形句點 (`.`)，然後輸入副檔名。</span><span class="sxs-lookup"><span data-stu-id="d8723-162">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="d8723-163">若要尋找一個以上的檔案類型，請輸入多重搜尋字串，並以分號 (`;`) 分隔。</span><span class="sxs-lookup"><span data-stu-id="d8723-163">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="d8723-164">選取清單中的任何項目，即可輸入預先設定的搜尋字串，來尋找特定類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="d8723-164">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="d8723-165">結果選項</span><span class="sxs-lookup"><span data-stu-id="d8723-165">Result Options</span></span>  
 <span data-ttu-id="d8723-166">決定按一下 [全部尋找]  時結果的位置。</span><span class="sxs-lookup"><span data-stu-id="d8723-166">Determines the location of the results when you click **Find All**.</span></span> <span data-ttu-id="d8723-167">您可以展開或摺疊 **結果選項** 區段。</span><span class="sxs-lookup"><span data-stu-id="d8723-167">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="d8723-168">您可以選取或清除下列選項。</span><span class="sxs-lookup"><span data-stu-id="d8723-168">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="d8723-169">**尋找結果 1 視窗**</span><span class="sxs-lookup"><span data-stu-id="d8723-169">**Find Results 1 window**</span></span>  
 <span data-ttu-id="d8723-170">如果選取此核取方塊，目前搜尋的結果將會附加至 [尋找結果 1] 視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="d8723-170">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="d8723-171">此視窗會自動開啟，以顯示您的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="d8723-171">This window opens automatically to display your search results.</span></span> <span data-ttu-id="d8723-172">若要手動開啟此視窗，請按一下 [檢視] 功能表上的 [其他視窗]，然後按一下 [尋找結果 1]。</span><span class="sxs-lookup"><span data-stu-id="d8723-172">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="d8723-173">**尋找結果 2 視窗**</span><span class="sxs-lookup"><span data-stu-id="d8723-173">**Find Results 2 window**</span></span>  
 <span data-ttu-id="d8723-174">如果選取此核取方塊，目前搜尋的結果將會附加至 [尋找結果 2] 視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="d8723-174">When this check box is selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="d8723-175">此視窗會自動開啟，以顯示您的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="d8723-175">This window opens automatically to display your search results.</span></span> <span data-ttu-id="d8723-176">若要手動開啟此視窗，請按一下 [檢視] 功能表上的 [其他視窗]，然後按一下 [尋找結果 2]。</span><span class="sxs-lookup"><span data-stu-id="d8723-176">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="d8723-177">**僅顯示檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d8723-177">**Display file names only**</span></span>  
 <span data-ttu-id="d8723-178">在 [尋找結果 1] 或 [尋找結果 2] 視窗中，以檔案為單位顯示包含符合搜尋條件之項目，而非顯示每一個符合搜尋條件的項目。</span><span class="sxs-lookup"><span data-stu-id="d8723-178">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="d8723-179">此選項在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中無法使用。</span><span class="sxs-lookup"><span data-stu-id="d8723-179">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d8723-180">**全部取代後保持已修改檔案為開啟狀態**</span><span class="sxs-lookup"><span data-stu-id="d8723-180">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="d8723-181">如果選取，就會將有進行取代作業的所有檔案保持開啟，以便您恢復或儲存變更。</span><span class="sxs-lookup"><span data-stu-id="d8723-181">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="d8723-182">記憶體的容量可能會限制進行取代作業之後，能夠保持開啟的檔案數目。</span><span class="sxs-lookup"><span data-stu-id="d8723-182">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d8723-183">您僅能針對仍然保持開啟以供編輯的檔案執行 [恢復]  動作。</span><span class="sxs-lookup"><span data-stu-id="d8723-183">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="d8723-184">如果沒有選取此選項，沒有開啟以供編輯的檔案將會保持關閉狀態，且該些檔案就無法使用 [恢復]  選項。</span><span class="sxs-lookup"><span data-stu-id="d8723-184">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="d8723-185">尋找和取代檢視</span><span class="sxs-lookup"><span data-stu-id="d8723-185">Find and Replace Views</span></span>  
 <span data-ttu-id="d8723-186">[尋找和檢視] 視窗上方的索引標籤包含 **[檢視]** 功能表。</span><span class="sxs-lookup"><span data-stu-id="d8723-186">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="d8723-187">這些功能表可以讓您選擇要在使用中窗格裡顯示的一組欄位。</span><span class="sxs-lookup"><span data-stu-id="d8723-187">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="d8723-188">您可以讓 [尋找和取代] 視窗停駐在方便存取的位置，然後在各索引標籤之間和各檢視之間變更，以執行任何類型的尋找或取代作業。</span><span class="sxs-lookup"><span data-stu-id="d8723-188">You can leave the Find and Replace window docked in a convenient location and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="d8723-189">**切換至快速尋找**</span><span class="sxs-lookup"><span data-stu-id="d8723-189">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="d8723-190">此工具列索引標籤會將對話方塊變更為 [快速尋找]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d8723-190">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="d8723-191">**切換至檔案中尋找**</span><span class="sxs-lookup"><span data-stu-id="d8723-191">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="d8723-192">此工具列索引標籤會將對話方塊變更為 [檔案中尋找]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d8723-192">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="d8723-193">**切換至尋找符號**</span><span class="sxs-lookup"><span data-stu-id="d8723-193">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="d8723-194">此工具列索引標籤會將對話方塊變更為 [Find in Symbols (符號中尋找)]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d8723-194">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8723-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8723-195">See Also</span></span>  
 [<span data-ttu-id="d8723-196">SQL Server Management Studio 鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="d8723-196">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
