---
title: 管理程式碼格式設定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- indenting code [SQL Server]
- displaying URLs
- code formatting [SQL Server Management Studio]
- collapsing text
- formats [SQL Server], code formatting in SQL Server Management Studio
- hiding text
- formats [SQL Server]
- text [SQL Server], code formats
- automatic indentation
- converting text to lower case
- Query Editor [SQL Server Management Studio], managing code formats
- URL displayed in code [SQL Server Management Studio]
- converting text to upper case
- text [SQL Server]
- unindenting code
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
author: rothja
ms.author: jroth
ms.openlocfilehash: 873848c8aee575b47f7a3d8c31d8392cba5ed12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606726"
---
# <a name="manage-code-formatting"></a><span data-ttu-id="ab329-102">管理程式碼格式設定</span><span class="sxs-lookup"><span data-stu-id="ab329-102">Manage Code Formatting</span></span>
  <span data-ttu-id="ab329-103">當使用編輯器時，您可以利用縮排、隱藏文字、URL...等，來建立程式碼的格式。</span><span class="sxs-lookup"><span data-stu-id="ab329-103">With the Editor you can format your code with indenting, hidden text, URLs, and so forth.</span></span> <span data-ttu-id="ab329-104">您也可以利用智慧型縮排 (Smart Indenting) 功能，在輸入程式碼的同時，自動建立程式碼的格式。</span><span class="sxs-lookup"><span data-stu-id="ab329-104">You can also auto-format your code as you type by using Smart Indenting.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="ab329-105">縮排</span><span class="sxs-lookup"><span data-stu-id="ab329-105">Indenting</span></span>  
 <span data-ttu-id="ab329-106">您可以選擇三種不同的文字縮排樣式。</span><span class="sxs-lookup"><span data-stu-id="ab329-106">You can choose three different styles of text indenting.</span></span> <span data-ttu-id="ab329-107">您也可以指定幾個空格組成單一縮排和定位點，以及編輯器在縮排時要使用定位字元或空格字元。</span><span class="sxs-lookup"><span data-stu-id="ab329-107">You can also specify how many spaces compose a single indentation or tab, and whether the Editor uses tabs or space characters when indenting.</span></span>  
  
#### <a name="to-choose-an-indenting-style"></a><span data-ttu-id="ab329-108">選擇縮排樣式</span><span class="sxs-lookup"><span data-stu-id="ab329-108">To choose an indenting style</span></span>  
  
1.  <span data-ttu-id="ab329-109">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="ab329-110">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-110">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ab329-111">按一下資料夾，選取 [所有語言]  來設定所有語言的縮排。</span><span class="sxs-lookup"><span data-stu-id="ab329-111">Click the folder, and select **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="ab329-112">按一下 [定位點]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-112">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="ab329-113">請按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="ab329-113">Click one of the following options:</span></span>  
  
    -   <span data-ttu-id="ab329-114">**None**：</span><span class="sxs-lookup"><span data-stu-id="ab329-114">**None**.</span></span> <span data-ttu-id="ab329-115">游標會移至下一行的開頭。</span><span class="sxs-lookup"><span data-stu-id="ab329-115">The cursor goes to the beginning of the next line.</span></span>  
  
    -   <span data-ttu-id="ab329-116">**封鎖**。</span><span class="sxs-lookup"><span data-stu-id="ab329-116">**Block**.</span></span> <span data-ttu-id="ab329-117">游標會對齊上下行。</span><span class="sxs-lookup"><span data-stu-id="ab329-117">The cursor aligns the next line with the previous line.</span></span>  
  
    -   <span data-ttu-id="ab329-118">[智慧型]  \(預設)。</span><span class="sxs-lookup"><span data-stu-id="ab329-118">**Smart** (Default).</span></span> <span data-ttu-id="ab329-119">語言服務會決定要使用的適當縮排樣式。</span><span class="sxs-lookup"><span data-stu-id="ab329-119">The language service determines the appropriate indenting style to use.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab329-120">有些語言並未完整提供這三個縮排選項。</span><span class="sxs-lookup"><span data-stu-id="ab329-120">Some languages do not offer all three indenting options.</span></span>  
  
#### <a name="to-change-indent-tab-settings"></a><span data-ttu-id="ab329-121">變更縮排程位點設定</span><span class="sxs-lookup"><span data-stu-id="ab329-121">To change indent tab settings</span></span>  
  
1.  <span data-ttu-id="ab329-122">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-122">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="ab329-123">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-123">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ab329-124">選取 [所有語言]  的資料夾來設定所有語言的縮排。</span><span class="sxs-lookup"><span data-stu-id="ab329-124">Select the folder for **All Languages** to set indenting for all languages.</span></span>  
  
4.  <span data-ttu-id="ab329-125">按一下 [定位點]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-125">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="ab329-126">若要指定縮排和定位作業的定位字元，請按一下 [保留定位點]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-126">To specify tab characters for tab and indent operations, click **Keep tabs**.</span></span> <span data-ttu-id="ab329-127">若要指定空格字元，請選取 [插入空格]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-127">To specify space characters, select **Insert spaces**.</span></span>  
  
     <span data-ttu-id="ab329-128">如果您選取 [插入空格]  ，請在 [定位點大小]  或 [縮排大小]  之下，分別輸入每個定位點或縮排所代表的空格字元數。</span><span class="sxs-lookup"><span data-stu-id="ab329-128">If you select **Insert Spaces**, enter the number of space characters each tab or indent represents under **Tab Size** or **Indent Size**, respectively.</span></span>  
  
#### <a name="to-indent-code"></a><span data-ttu-id="ab329-129">縮排程式碼</span><span class="sxs-lookup"><span data-stu-id="ab329-129">To indent code</span></span>  
  
1.  <span data-ttu-id="ab329-130">選取您要縮排的文字。</span><span class="sxs-lookup"><span data-stu-id="ab329-130">Select the text you want to indent.</span></span>  
  
2.  <span data-ttu-id="ab329-131">按 TAB 鍵，或按一下 [標準] 工具列上的 [縮排]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab329-131">Press TAB, or click the **Indent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-unindent-code"></a><span data-ttu-id="ab329-132">取消縮排程式碼</span><span class="sxs-lookup"><span data-stu-id="ab329-132">To unindent code</span></span>  
  
1.  <span data-ttu-id="ab329-133">選取您要取消縮排的文字。</span><span class="sxs-lookup"><span data-stu-id="ab329-133">Select the text you want to unindent.</span></span>  
  
2.  <span data-ttu-id="ab329-134">按 SHIFT+TAB 鍵，或按一下 [標準] 工具列上的 [取消縮排]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab329-134">Press SHIFT+TAB, or click the **Unindent** button on the Standard toolbar.</span></span>  
  
#### <a name="to-automatically-indent-all-of-your-code"></a><span data-ttu-id="ab329-135">自動縮排所有程式碼</span><span class="sxs-lookup"><span data-stu-id="ab329-135">To automatically indent all of your code</span></span>  
  
1.  <span data-ttu-id="ab329-136">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-136">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="ab329-137">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-137">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ab329-138">按一下 **[所有語言]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-138">Click **All Languages**.</span></span>  
  
4.  <span data-ttu-id="ab329-139">按一下 [定位點]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-139">Click **Tabs**.</span></span>  
  
5.  <span data-ttu-id="ab329-140">按一下 [智慧型]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-140">Click **Smart**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab329-141">有些語言無法使用 [智慧型]  選項。</span><span class="sxs-lookup"><span data-stu-id="ab329-141">The **Smart** option is not available for some languages.</span></span>  
  
#### <a name="to-convert-white-space-to-tabs"></a><span data-ttu-id="ab329-142">將空格轉換成定位點</span><span class="sxs-lookup"><span data-stu-id="ab329-142">To convert white space to tabs</span></span>  
  
1.  <span data-ttu-id="ab329-143">選取空格要轉換成定位點的文字。</span><span class="sxs-lookup"><span data-stu-id="ab329-143">Select the text whose white space you want to convert to tabs.</span></span>  
  
2.  <span data-ttu-id="ab329-144">在 [編輯]  功能表上，指向 [進階]  ，再按一下 [將選取範圍空白鍵轉定點]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-144">On the **Edit** menu, point to **Advanced**, and click **Tabify Selection**.</span></span>  
  
#### <a name="to-convert-tabs-to-spaces"></a><span data-ttu-id="ab329-145">將定位點轉換成空格</span><span class="sxs-lookup"><span data-stu-id="ab329-145">To convert tabs to spaces</span></span>  
  
1.  <span data-ttu-id="ab329-146">選取您要將定位點轉換成空格的文字。</span><span class="sxs-lookup"><span data-stu-id="ab329-146">Select the text whose tabs you want to convert to spaces.</span></span>  
  
2.  <span data-ttu-id="ab329-147">在 [編輯]  功能表上，指向 [進階]  ，再按一下 [將選取範圍定位點轉空白]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-147">On the **Edit** menu, point to **Advanced**, and click **Untabify Selection**.</span></span>  
  
 <span data-ttu-id="ab329-148">這些命令的行為會隨著 [選項]  對話方塊中的定位點設定而不同。</span><span class="sxs-lookup"><span data-stu-id="ab329-148">The behavior of these commands depends on the tab settings in the **Options** dialog box.</span></span> <span data-ttu-id="ab329-149">例如，如果定位點設定是 4，[將選取範圍空白鍵轉定點]  會每 4 個連續空格建立一個定位點，[選取範圍定位鍵轉空白鍵]  會每個定位點建立 4 個空格。</span><span class="sxs-lookup"><span data-stu-id="ab329-149">For example, if the tab setting is 4, **Tabify Selection** creates a tab for every 4 contiguous spaces, and **Untabify Selection** creates 4 spaces for every tab.</span></span>  
  
## <a name="converting-text-to-upper-and-lower-case"></a><span data-ttu-id="ab329-150">將文字轉換成大寫和小寫</span><span class="sxs-lookup"><span data-stu-id="ab329-150">Converting Text to Upper and Lower Case</span></span>  
 <span data-ttu-id="ab329-151">您可以利用命令，將文字轉換成全為大寫或小寫。</span><span class="sxs-lookup"><span data-stu-id="ab329-151">You can use commands to convert text to all uppercase or lower case.</span></span>  
  
#### <a name="to-switch-text-to-upper-or-lower-case"></a><span data-ttu-id="ab329-152">將文字切換成大寫或小寫</span><span class="sxs-lookup"><span data-stu-id="ab329-152">To switch text to upper or lower case</span></span>  
  
1.  <span data-ttu-id="ab329-153">選取您要轉換的文字。</span><span class="sxs-lookup"><span data-stu-id="ab329-153">Select the text you want to convert.</span></span>  
  
2.  <span data-ttu-id="ab329-154">若要將文字轉換成大寫，請按 CTRL+SHIFT+U，或按一下 [編輯] 功能表 [進階] 子功能表中的 [設成大寫]。</span><span class="sxs-lookup"><span data-stu-id="ab329-154">To convert text to uppercase, press CTRL+SHIFT+U, or click **Make Uppercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
3.  <span data-ttu-id="ab329-155">若要將文字轉換成小寫，請按 CTRL+SHIFT+L，或按一下 [編輯] 功能表 [進階] 子功能表中的 [設成小寫]。</span><span class="sxs-lookup"><span data-stu-id="ab329-155">To convert text to lowercase, press CTRL+SHIFT+L, or click **Make Lowercase** on the **Advanced** submenu of the **Edit** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab329-156">如需完整的鍵盤快速鍵清單，請參閱 [SQL Server Management Studio 鍵盤快速鍵](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="ab329-156">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="displaying-and-linking-to-urls"></a><span data-ttu-id="ab329-157">顯示和連結到 URL</span><span class="sxs-lookup"><span data-stu-id="ab329-157">Displaying and Linking to URLs</span></span>  
 <span data-ttu-id="ab329-158">您可以在程式碼中，建立和顯示可點按的 URL。</span><span class="sxs-lookup"><span data-stu-id="ab329-158">You can create and display clickable URLs in your code.</span></span> <span data-ttu-id="ab329-159">依預設，這些 URL：</span><span class="sxs-lookup"><span data-stu-id="ab329-159">By default, the URLs:</span></span>  
  
-   <span data-ttu-id="ab329-160">會附加底線。</span><span class="sxs-lookup"><span data-stu-id="ab329-160">Are underlined.</span></span>  
  
-   <span data-ttu-id="ab329-161">當滑鼠指標移到這些 URL 上時，滑鼠指標會變成手的形狀。</span><span class="sxs-lookup"><span data-stu-id="ab329-161">Change the mouse pointer to a hand when you move over them.</span></span>  
  
-   <span data-ttu-id="ab329-162">如果 URL 有效，當按一下 URL 時，會打開它。</span><span class="sxs-lookup"><span data-stu-id="ab329-162">Open the URL when clicked, if the URL is valid.</span></span>  
  
#### <a name="to-display-a-clickable-url"></a><span data-ttu-id="ab329-163">顯示可點按的 URL</span><span class="sxs-lookup"><span data-stu-id="ab329-163">To display a clickable URL</span></span>  
  
1.  <span data-ttu-id="ab329-164">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-164">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="ab329-165">按一下 **[文字編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="ab329-165">Click **Text Editor**.</span></span>  
  
3.  <span data-ttu-id="ab329-166">若要變更單一語言的選項，請按一下這個語言資料夾，再按一下 [一般]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-166">To change the option for only one language, click that language folder and then click **General**.</span></span> <span data-ttu-id="ab329-167">若要變更所有語言的選項，請按一下 [所有語言]  ，再按一下 [一般]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-167">To change the option for all languages, click **All Languages** and then click **General**.</span></span>  
  
4.  <span data-ttu-id="ab329-168">選取 [啟用按一下方式的 URL 導覽]  。</span><span class="sxs-lookup"><span data-stu-id="ab329-168">Select **Enable single-click URL navigation**.</span></span>  
  
  
