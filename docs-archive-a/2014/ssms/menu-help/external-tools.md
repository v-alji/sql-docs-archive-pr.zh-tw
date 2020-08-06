---
title: 外部工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- External Tools dialog box
ms.assetid: d7dae88f-0781-4162-96cd-d3a3a4d82035
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39cd0d139e81c02a7d2a58fae4e74221be7f78e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700567"
---
# <a name="external-tools"></a><span data-ttu-id="c0dca-102">外部工具</span><span class="sxs-lookup"><span data-stu-id="c0dca-102">External Tools</span></span>
  <span data-ttu-id="c0dca-103">使用此對話方塊可將外部工具 (例如 SQL Server 組態管理員或記事本) 新增到 [工具]  功能表。</span><span class="sxs-lookup"><span data-stu-id="c0dca-103">Use this dialog box to add external tools, such as SQL Server Configuration Manager or Notepad, to the **Tools** menu.</span></span> <span data-ttu-id="c0dca-104">加入外部工具可以讓您在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中工作時，輕易地啟動其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0dca-104">Adding external tools allows you to easily launch other applications while working in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c0dca-105">啟動工具時，您可以指定引數和工作目錄。</span><span class="sxs-lookup"><span data-stu-id="c0dca-105">You can specify arguments and a working directory when launching the tool.</span></span> <span data-ttu-id="c0dca-106">除此之外，某些工具的輸出也可以顯示在 [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="c0dca-106">In addition, the outputs from some tools can be displayed in the Output window.</span></span> <span data-ttu-id="c0dca-107">[外部工具]  對話方塊可以透過 [工具]  功能表使用。</span><span class="sxs-lookup"><span data-stu-id="c0dca-107">The **External Tools** dialog box is available on the **Tools** menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0dca-108">選項。</span><span class="sxs-lookup"><span data-stu-id="c0dca-108">Options</span></span>  
 <span data-ttu-id="c0dca-109">**功能表內容**</span><span class="sxs-lookup"><span data-stu-id="c0dca-109">**Menu Contents**</span></span>  
 <span data-ttu-id="c0dca-110">列出目前已新增至 [工具]  功能表之項目的標題。</span><span class="sxs-lookup"><span data-stu-id="c0dca-110">Lists the titles of the items currently added to the **Tools** menu.</span></span> <span data-ttu-id="c0dca-111">使用 [上移]  與 [下移]  箭頭，可變更功能表上所示項目的順序。</span><span class="sxs-lookup"><span data-stu-id="c0dca-111">Use the **Move Up** and **Move Down** arrows to change the order the items that appear on the menu.</span></span> <span data-ttu-id="c0dca-112">使用 [刪除]  按鈕可從功能表中移除項目。</span><span class="sxs-lookup"><span data-stu-id="c0dca-112">Use the **Delete** button to remove an item from the menu.</span></span>  
  
 <span data-ttu-id="c0dca-113">**上移**</span><span class="sxs-lookup"><span data-stu-id="c0dca-113">**Move Up**</span></span>  
 <span data-ttu-id="c0dca-114">在 [工具]  功能表所顯示的工具清單中，將所選的工具向上移動至較前面的位置。</span><span class="sxs-lookup"><span data-stu-id="c0dca-114">Move the selected tool higher in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="c0dca-115">**下移**</span><span class="sxs-lookup"><span data-stu-id="c0dca-115">**Move Down**</span></span>  
 <span data-ttu-id="c0dca-116">在 [工具]  功能表所顯示的工具清單中，將所選的工具向下移動至較後面的位置。</span><span class="sxs-lookup"><span data-stu-id="c0dca-116">Move the selected tool lower in the list of tools that appear on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="c0dca-117">**加入**</span><span class="sxs-lookup"><span data-stu-id="c0dca-117">**Add**</span></span>  
 <span data-ttu-id="c0dca-118">清除文字方塊，讓您指定新的工具。</span><span class="sxs-lookup"><span data-stu-id="c0dca-118">Clear the text boxes so you can specify a new tool.</span></span>  
  
 <span data-ttu-id="c0dca-119">**刪除**</span><span class="sxs-lookup"><span data-stu-id="c0dca-119">**Delete**</span></span>  
 <span data-ttu-id="c0dca-120">從 [功能表內容]  清單及 [工具]  功能表中移除工具或命令。</span><span class="sxs-lookup"><span data-stu-id="c0dca-120">Remove the tool or command from the **Menu Contents** list as well as from the **Tools** menu.</span></span>  
  
 <span data-ttu-id="c0dca-121">**Title** (標題)</span><span class="sxs-lookup"><span data-stu-id="c0dca-121">**Title**</span></span>  
 <span data-ttu-id="c0dca-122">出現在 [工具]  功能表之 [外部工具]  子功能表上的工具名稱或命令名稱。</span><span class="sxs-lookup"><span data-stu-id="c0dca-122">The name of the tool or command that will appear on the **External Tools** submenu of the **Tools** menu.</span></span> <span data-ttu-id="c0dca-123">將連字號 (&) 放在工具名稱中的字母前，即可使用該字母作為工具的加速鍵。</span><span class="sxs-lookup"><span data-stu-id="c0dca-123">Place an ampersand before a letter in the name of the tool to use that letter as an accelerator key for the tool.</span></span> <span data-ttu-id="c0dca-124">例如 `&Spy++` 在 [工具]  功能表上會顯示為 **Spy++** 。</span><span class="sxs-lookup"><span data-stu-id="c0dca-124">For example, `&Spy++` would display **Spy++** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="c0dca-125">**命令**</span><span class="sxs-lookup"><span data-stu-id="c0dca-125">**Command**</span></span>  
 <span data-ttu-id="c0dca-126">指定 .exe、.com、.pif、.bat、.cmd，或其他您想要啟動之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c0dca-126">Specify the path to the .exe, .com, .pif, .bat, .cmd, or other file that you intend to launch.</span></span> <span data-ttu-id="c0dca-127">若選取 [使用輸出視窗] 核取方塊，即可在輸出視窗中檢視 `.bat``.com` 及其他檔案的輸出。</span><span class="sxs-lookup"><span data-stu-id="c0dca-127">The output from `.bat`, `.com`, and other files can be viewed in the Output window if you select the **Use output window** check box.</span></span>  
  
 <span data-ttu-id="c0dca-128">**引數**</span><span class="sxs-lookup"><span data-stu-id="c0dca-128">**Arguments**</span></span>  
 <span data-ttu-id="c0dca-129">在功能表上選取工具時，指定會傳遞至該工具的變數。</span><span class="sxs-lookup"><span data-stu-id="c0dca-129">Specify the variables that are passed to the tool when the tool is selected on the menu.</span></span> <span data-ttu-id="c0dca-130">啟動工具或命令時，引數可以指定會傳遞至該工具或命令的值。</span><span class="sxs-lookup"><span data-stu-id="c0dca-130">Arguments can specify values that are passed to the tool or command when it is launched.</span></span> <span data-ttu-id="c0dca-131">例如，值可以指定檔案名稱或目錄。</span><span class="sxs-lookup"><span data-stu-id="c0dca-131">For example, a value can specify a file name or directory.</span></span> <span data-ttu-id="c0dca-132">使用 **箭號** 按鈕，可從預先定義的引數清單中選取引數。</span><span class="sxs-lookup"><span data-stu-id="c0dca-132">Use the **Arrow** button to select from a list of predefined arguments.</span></span> <span data-ttu-id="c0dca-133">您可以加入一個以上。</span><span class="sxs-lookup"><span data-stu-id="c0dca-133">You can add more than one.</span></span> <span data-ttu-id="c0dca-134">如需預先定義的引數及其定義的完整清單，請參閱 [外部工具的引數](external-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c0dca-134">For a complete list of predefined arguments and their definitions, see [Arguments for External Tools](external-tools.md).</span></span> <span data-ttu-id="c0dca-135">視您所使用的命令或工具而定，還可以輸入自訂引數 (例如，命令提示字元參數)。</span><span class="sxs-lookup"><span data-stu-id="c0dca-135">You can also enter custom arguments (command-prompt switches, for example), depending on the command or tool you use.</span></span>  
  
 <span data-ttu-id="c0dca-136">**初始目錄**</span><span class="sxs-lookup"><span data-stu-id="c0dca-136">**Initial directory**</span></span>  
 <span data-ttu-id="c0dca-137">指定工具的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="c0dca-137">Specify the working directory of the tool.</span></span> <span data-ttu-id="c0dca-138">使用 **箭號** 按鈕可選取目錄。</span><span class="sxs-lookup"><span data-stu-id="c0dca-138">Use the **Arrow** button to select directories.</span></span> <span data-ttu-id="c0dca-139">您可以選取一個以上。</span><span class="sxs-lookup"><span data-stu-id="c0dca-139">You can select more than one.</span></span>  
  
 <span data-ttu-id="c0dca-140">**使用輸出視窗**</span><span class="sxs-lookup"><span data-stu-id="c0dca-140">**Use output Window**</span></span>  
 <span data-ttu-id="c0dca-141">指定工具的結果是否要顯示在 [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="c0dca-141">Specify whether or not results from the tool are displayed in the Output window.</span></span> <span data-ttu-id="c0dca-142">此選項僅適用於通常會在命令提示視窗中顯示輸出的檔案 (例如 .bat 和 .com 檔案)。</span><span class="sxs-lookup"><span data-stu-id="c0dca-142">This option is only available for files, such as .bat and .com files, that normally display output in the command prompt window.</span></span> <span data-ttu-id="c0dca-143">若啟用此選項，當您要追蹤工具的進度時，此選項可以簡化視窗的管理。</span><span class="sxs-lookup"><span data-stu-id="c0dca-143">When enabled, this option eases window management when you are following the progress of a tool.</span></span>  
  
 <span data-ttu-id="c0dca-144">**提示提供引數**</span><span class="sxs-lookup"><span data-stu-id="c0dca-144">**Prompt for arguments**</span></span>  
 <span data-ttu-id="c0dca-145">顯示 [引數]  對話方塊，讓您每次啟動外部工具時，都能輸入或編輯引數的值。</span><span class="sxs-lookup"><span data-stu-id="c0dca-145">Display the **Arguments** dialog box to enable you to enter or edit values for the arguments each time you launch the external tool.</span></span>  
  
 <span data-ttu-id="c0dca-146">**將輸出視為 Unicode**</span><span class="sxs-lookup"><span data-stu-id="c0dca-146">**Treat output as Unicode**</span></span>  
 <span data-ttu-id="c0dca-147">允許 [輸出] 視窗接受 Unicode。</span><span class="sxs-lookup"><span data-stu-id="c0dca-147">Allow the Output window to accept Unicode.</span></span>  
  
 <span data-ttu-id="c0dca-148">**結束時關閉**</span><span class="sxs-lookup"><span data-stu-id="c0dca-148">**Close On Exit**</span></span>  
 <span data-ttu-id="c0dca-149">關閉工具時也關閉該工具所開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="c0dca-149">Close the window opened by the tool when the tool is closed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0dca-150">範例</span><span class="sxs-lookup"><span data-stu-id="c0dca-150">Example</span></span>  
  
#### <a name="to-add-sql-server-configuration-manager-to-the-tools-menu"></a><span data-ttu-id="c0dca-151">將 SQL Server 組態管理員新增到工具功能表</span><span class="sxs-lookup"><span data-stu-id="c0dca-151">To add SQL Server Configuration Manager to the Tools menu</span></span>  
  
1.  <span data-ttu-id="c0dca-152">在 [工具]  功能表上按一下 [外部工具]  。</span><span class="sxs-lookup"><span data-stu-id="c0dca-152">On the **Tools** menu, click **External Tools**.</span></span>  
  
2.  <span data-ttu-id="c0dca-153">在 [標題]  方塊中，輸入 SQL Server 組態管理員  。</span><span class="sxs-lookup"><span data-stu-id="c0dca-153">In the **Title** box, type **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="c0dca-154">在 [**命令**] 方塊中，輸入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理主控台可執行檔的路徑，例如`C:\WINNT\system32\mmc.exe`</span><span class="sxs-lookup"><span data-stu-id="c0dca-154">In the **Command** box, type the path to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console executable, such as `C:\WINNT\system32\mmc.exe`</span></span>  
  
4.  <span data-ttu-id="c0dca-155">在 [**引數**] 方塊中，輸入 .msc 檔案的路徑，例如`"C:\WINNT\system32\SQLServerManager.msc"`</span><span class="sxs-lookup"><span data-stu-id="c0dca-155">In the **Arguments** box, type the path to the .msc file, such as `"C:\WINNT\system32\SQLServerManager.msc"`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0dca-156">檢視 [開始][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**功能表上之**  捷徑的屬性，以確認這些檔案在您電腦上的位置。</span><span class="sxs-lookup"><span data-stu-id="c0dca-156">View the properties of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] shortcut on the **Start** menu to confirm the location of the files on your computer.</span></span>  
