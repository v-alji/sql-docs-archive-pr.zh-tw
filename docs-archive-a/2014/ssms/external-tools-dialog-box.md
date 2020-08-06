---
title: 外部工具對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5789dc150e45c1a0364b7acc0ea7fda443efcf17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702321"
---
# <a name="external-tools-dialog-box"></a><span data-ttu-id="f51fb-102">外部工具對話方塊</span><span class="sxs-lookup"><span data-stu-id="f51fb-102">External Tools Dialog Box</span></span>
  <span data-ttu-id="f51fb-103">請利用 [外部工具]  對話方塊，將 SQLCMD 或 [記事本] 之類的外部工具新增至 [工具]  功能表。</span><span class="sxs-lookup"><span data-stu-id="f51fb-103">Use the **External Tools** dialog box to add external tools such as SQLCMD or Notepad to the **Tools** menu.</span></span> <span data-ttu-id="f51fb-104">當您新增外部工具時，即可在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境中工作時輕鬆地啟動其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="f51fb-104">Adding external tools allows you to easily launch other applications while working in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span> <span data-ttu-id="f51fb-105">啟動工具時，您可以指定引數和工作目錄。</span><span class="sxs-lookup"><span data-stu-id="f51fb-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="f51fb-106">此外，某些工具的輸出可以顯示在 [輸出]  視窗中。</span><span class="sxs-lookup"><span data-stu-id="f51fb-106">In addition, the output from some tools can be displayed in the **Output** window.</span></span> <span data-ttu-id="f51fb-107">[外部工具]  對話方塊可以透過 [工具]  功能表使用。</span><span class="sxs-lookup"><span data-stu-id="f51fb-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f51fb-108">選項。</span><span class="sxs-lookup"><span data-stu-id="f51fb-108">Options</span></span>  
 <span data-ttu-id="f51fb-109">**功能表內容**</span><span class="sxs-lookup"><span data-stu-id="f51fb-109">**Menu contents**</span></span>  
 <span data-ttu-id="f51fb-110">列出目前已新增至 [工具]  功能表之項目的標題。</span><span class="sxs-lookup"><span data-stu-id="f51fb-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="f51fb-111">使用 [上移]  與 [下移]  箭頭，可變更功能表上所示項目的順序。</span><span class="sxs-lookup"><span data-stu-id="f51fb-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="f51fb-112">使用 [刪除]  按鈕可從功能表中移除項目。</span><span class="sxs-lookup"><span data-stu-id="f51fb-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="f51fb-113">**上移**</span><span class="sxs-lookup"><span data-stu-id="f51fb-113">**Move Up**</span></span>  
 <span data-ttu-id="f51fb-114">在 [工具]  功能表所顯示的工具清單中，將所選的工具向上移動至較前面的位置。</span><span class="sxs-lookup"><span data-stu-id="f51fb-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="f51fb-115">**下移**</span><span class="sxs-lookup"><span data-stu-id="f51fb-115">**Move Down**</span></span>  
 <span data-ttu-id="f51fb-116">在 [工具]  功能表所顯示的工具清單中，將所選的工具向下移動至較後面的位置。</span><span class="sxs-lookup"><span data-stu-id="f51fb-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="f51fb-117">**加入**</span><span class="sxs-lookup"><span data-stu-id="f51fb-117">**Add**</span></span>  
 <span data-ttu-id="f51fb-118">清除文字方塊，讓您指定新的工具。</span><span class="sxs-lookup"><span data-stu-id="f51fb-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="f51fb-119">**刪除**</span><span class="sxs-lookup"><span data-stu-id="f51fb-119">**Delete**</span></span>  
 <span data-ttu-id="f51fb-120">從 [功能表內容]  清單及 [工具]  功能表中移除工具或命令。</span><span class="sxs-lookup"><span data-stu-id="f51fb-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="f51fb-121">**Title** (標題)</span><span class="sxs-lookup"><span data-stu-id="f51fb-121">**Title**</span></span>  
 <span data-ttu-id="f51fb-122">輸入會顯示在 [工具]  功能表之 [外部工具]  子功能表上的工具名稱或命令。</span><span class="sxs-lookup"><span data-stu-id="f51fb-122">Enter the name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="f51fb-123">將連字號 (&) 放在工具名稱的某個字母前，以指定該字母做為鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="f51fb-123">Place an ampersand (&) before a letter in the name of the tool to specify that letter as a keyboard shortcut.</span></span> <span data-ttu-id="f51fb-124">例如，"&SQLCMD" 會在 [工具]  功能表中顯示 SQLCMD。</span><span class="sxs-lookup"><span data-stu-id="f51fb-124">For example, "&SQLCMD" would display SQLCMD on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="f51fb-125">**命令**</span><span class="sxs-lookup"><span data-stu-id="f51fb-125">**Command**</span></span>  
 <span data-ttu-id="f51fb-126">指定要啟動的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="f51fb-126">Specify the path to the file to launch.</span></span>  
  
 <span data-ttu-id="f51fb-127">**引數**</span><span class="sxs-lookup"><span data-stu-id="f51fb-127">**Arguments**</span></span>  
 <span data-ttu-id="f51fb-128">在功能表上選取工具時，指定會傳遞至該工具的變數。</span><span class="sxs-lookup"><span data-stu-id="f51fb-128">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="f51fb-129">啟動工具或命令時，引數可以指定會傳遞至該工具或命令的值。</span><span class="sxs-lookup"><span data-stu-id="f51fb-129">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="f51fb-130">例如，值可以指定檔案名稱或目錄。</span><span class="sxs-lookup"><span data-stu-id="f51fb-130">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="f51fb-131">請利用箭頭按鈕，從預先定義的引數清單中選取。</span><span class="sxs-lookup"><span data-stu-id="f51fb-131">Use the arrow button to select from a list of predefined arguments.</span></span> <span data-ttu-id="f51fb-132">您可以加入一個以上。</span><span class="sxs-lookup"><span data-stu-id="f51fb-132">You can add more than one.</span></span> <span data-ttu-id="f51fb-133">如需預先定義的引數及其定義的完整清單，請參閱 [外部工具的引數](menu-help/external-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f51fb-133">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](menu-help/external-tools.md).</span></span> <span data-ttu-id="f51fb-134">您也可以視所使用的命令或工具來輸入自訂引數 (例如，命令列參數)。</span><span class="sxs-lookup"><span data-stu-id="f51fb-134">You can also enter custom arguments (for example, command line switches), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="f51fb-135">**使用輸出視窗**</span><span class="sxs-lookup"><span data-stu-id="f51fb-135">**Use Output window**</span></span>  
 <span data-ttu-id="f51fb-136">開啟 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的 [輸出] 視窗以顯示執行命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="f51fb-136">Opens the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Output window to display output of the command being run.</span></span> <span data-ttu-id="f51fb-137">並非所有的工具都能以 [輸出] 視窗中所顯示的格式來輸出。</span><span class="sxs-lookup"><span data-stu-id="f51fb-137">Not all tools present output in a format that can be presented in the Output window.</span></span> <span data-ttu-id="f51fb-138">如需詳細資訊，請參閱 [輸出視窗](../relational-databases/scripting/transact-sql-debugger-output-window.md)。</span><span class="sxs-lookup"><span data-stu-id="f51fb-138">For more information, see [Output Window](../relational-databases/scripting/transact-sql-debugger-output-window.md).</span></span>  
  
 <span data-ttu-id="f51fb-139">**將輸出視為 Unicode**</span><span class="sxs-lookup"><span data-stu-id="f51fb-139">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="f51fb-140">將輸出解譯為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="f51fb-140">Interprets the output as Unicode.</span></span>  
  
 <span data-ttu-id="f51fb-141">**初始目錄**</span><span class="sxs-lookup"><span data-stu-id="f51fb-141">**Initial directory**</span></span>  
 <span data-ttu-id="f51fb-142">指定工具的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="f51fb-142">Specify the working directory of the tool.</span></span> <span data-ttu-id="f51fb-143">請利用箭頭按鈕來選取目錄。</span><span class="sxs-lookup"><span data-stu-id="f51fb-143">Use the arrow button to select directories.</span></span> <span data-ttu-id="f51fb-144">您可以選取一個以上。</span><span class="sxs-lookup"><span data-stu-id="f51fb-144">You can select more than one.</span></span>  
  
 <span data-ttu-id="f51fb-145">**提示提供引數**</span><span class="sxs-lookup"><span data-stu-id="f51fb-145">**Prompt for arguments**</span></span>  
 <span data-ttu-id="f51fb-146">顯示 [引數]  對話方塊，讓您在每次啟動外部工具時，輸入或編輯引數的值。</span><span class="sxs-lookup"><span data-stu-id="f51fb-146">Display the **Arguments** dialog box to allow you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="f51fb-147">**結束時關閉**</span><span class="sxs-lookup"><span data-stu-id="f51fb-147">**Close on exit**</span></span>  
 <span data-ttu-id="f51fb-148">關閉工具時也關閉該工具所開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="f51fb-148">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f51fb-149">範例</span><span class="sxs-lookup"><span data-stu-id="f51fb-149">Example</span></span>  
 <span data-ttu-id="f51fb-150">在 [外部工具]  對話方塊中輸入下列值，將會建立標示為 DAC 的功能表項目；在選取該功能表項目時，會開啟命令提示字元，並使用專用管理員連接執行 **sqlcmd** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="f51fb-150">Entering the following values in the **External Tools** dialog box will create a menu item labeled "DAC" that when selected, opens a command prompt and runs the **sqlcmd** utility using the dedicated administrator connection.</span></span>  
  
|<span data-ttu-id="f51fb-151">Box</span><span class="sxs-lookup"><span data-stu-id="f51fb-151">Box</span></span>|<span data-ttu-id="f51fb-152">值</span><span class="sxs-lookup"><span data-stu-id="f51fb-152">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="f51fb-153">**Title** (標題)</span><span class="sxs-lookup"><span data-stu-id="f51fb-153">**Title**</span></span>|<span data-ttu-id="f51fb-154">DAC</span><span class="sxs-lookup"><span data-stu-id="f51fb-154">DAC</span></span>|  
|<span data-ttu-id="f51fb-155">**命令**</span><span class="sxs-lookup"><span data-stu-id="f51fb-155">**Command**</span></span>|[!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]<span data-ttu-id="f51fb-156">Tools\Binn\SQLCMD.exe</span><span class="sxs-lookup"><span data-stu-id="f51fb-156">Tools\Binn\SQLCMD.exe</span></span>|  
|<span data-ttu-id="f51fb-157">**引數**</span><span class="sxs-lookup"><span data-stu-id="f51fb-157">**Arguments**</span></span>|<span data-ttu-id="f51fb-158">-A</span><span class="sxs-lookup"><span data-stu-id="f51fb-158">-A</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f51fb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f51fb-159">See Also</span></span>  
 <span data-ttu-id="f51fb-160">[外部工具的引數](menu-help/external-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f51fb-160">[Arguments for External Tools](menu-help/external-tools.md) </span></span>  
 [<span data-ttu-id="f51fb-161">一般使用者介面元素</span><span class="sxs-lookup"><span data-stu-id="f51fb-161">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
