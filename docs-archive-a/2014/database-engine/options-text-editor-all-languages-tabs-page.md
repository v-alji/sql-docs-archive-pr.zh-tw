---
title: 選項 (文字編輯器-所有語言-索引標籤頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 13f791e34b2099e8c0492c25886ee6b37ef1a1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599173"
---
# <a name="options-text-editor---all-languages--tabs-page"></a><span data-ttu-id="e53db-102">選項 (文字編輯器 - 所有語言 - 定位點頁面)</span><span class="sxs-lookup"><span data-stu-id="e53db-102">Options (Text Editor - All Languages -Tabs Page)</span></span>
  <span data-ttu-id="e53db-103">使用這個對話方塊可設定在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的全部五個編輯器中按下 Tab 鍵的移動行為。</span><span class="sxs-lookup"><span data-stu-id="e53db-103">Use this dialog box to set the tabbing behavior in all five of the editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e53db-104">若要顯示這些選項，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e53db-104">To display these options, click **Options** on the **Tools** menu.</span></span> <span data-ttu-id="e53db-105">選取 [文字編輯器]\*\*\*\* 資料夾，展開 [所有語言]\*\*\*\* 資料夾，然後按一下 [索引標籤]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e53db-105">Select the **Text Editor** folder, expand the **All Languages** folder and then click **Tabs**.</span></span>  
  
## <a name="tabbing-options-by-editor"></a><span data-ttu-id="e53db-106">依編輯器的 Tab 鍵移動選項</span><span class="sxs-lookup"><span data-stu-id="e53db-106">Tabbing Options by Editor</span></span>  
 <span data-ttu-id="e53db-107">您必須使用 [所有語言]\*\*\*\* 對話方塊設定 DMX、MDX 和 SQL Server Compact 編輯器的選項。</span><span class="sxs-lookup"><span data-stu-id="e53db-107">You must use the **All Languages** dialogs to set options for the DMX, MDX, and SQL Server Compact editors.</span></span> <span data-ttu-id="e53db-108">在此處設定的選項也會套用至純文字、Transact-SQL 和 XML 編輯器，不過，藉由展開這些語言的子資料夾，然後選取其選項頁面，您就可以個別為這些編輯器設定選項。</span><span class="sxs-lookup"><span data-stu-id="e53db-108">Options set here are also applied to the Plain Text, Transact-SQL, and XML editors, but you can set options separately for those editors by expanding the subfolders for those languages and selecting their option pages.</span></span> <span data-ttu-id="e53db-109">某些語言不支援所有 Tab 鍵移動選項。</span><span class="sxs-lookup"><span data-stu-id="e53db-109">Some languages do not support all of the tabbing options.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e53db-110">如果您使用這個對話方塊設定選項，但是想要為純文字、Transact-SQL 或 XML 編輯器進行不同的設定，則必須先在 [所有語言]\*\*\*\* 對話方塊中套用您的選取範圍，再設定這些編輯器的選項。</span><span class="sxs-lookup"><span data-stu-id="e53db-110">If you set an option using this dialog, but want a different setting for the Plain Text, Transact-SQL, or XML editors, you must set the options for those editors after applying your selections in the **All Languages** dialog.</span></span>  
  
 <span data-ttu-id="e53db-111">當您為特定編輯器選取不同設定時，會顯示「個別文字格式的縮排 (或 Tab) 設定相衝突」訊息。</span><span class="sxs-lookup"><span data-stu-id="e53db-111">The message "The indentation (or tab) settings for individual text formats conflict with each other" is displayed when different settings have been selected for particular editors.</span></span> <span data-ttu-id="e53db-112">例如，如果針對 [純文字]\*\*\*\* 選取 [Block indenting (封鎖縮排)]\*\*\*\* 選項，而針對 [XML]\*\*\*\* 選取 [無]\*\*\*\*，就會顯示此提醒。</span><span class="sxs-lookup"><span data-stu-id="e53db-112">For example, this reminder is displayed if the **Block indenting** option is selected for **Plain Text**, but **None** is selected for **XML**.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="e53db-113">縮排</span><span class="sxs-lookup"><span data-stu-id="e53db-113">Indenting</span></span>  
 <span data-ttu-id="e53db-114">**None**</span><span class="sxs-lookup"><span data-stu-id="e53db-114">**None**</span></span>  
 <span data-ttu-id="e53db-115">如果選取此選項，當您按下 ENTER 時所建立的新行就不會縮排。</span><span class="sxs-lookup"><span data-stu-id="e53db-115">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="e53db-116">資料指標會放在新行的第一個資料行上。</span><span class="sxs-lookup"><span data-stu-id="e53db-116">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="e53db-117">**封鎖**</span><span class="sxs-lookup"><span data-stu-id="e53db-117">**Block**</span></span>  
 <span data-ttu-id="e53db-118">如果選取此選項，當您按下 ENTER 鍵時所建立的新行就會自動縮排與上一行縮排相同的距離。</span><span class="sxs-lookup"><span data-stu-id="e53db-118">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line was indented.</span></span>  
  
 <span data-ttu-id="e53db-119">**智慧型**</span><span class="sxs-lookup"><span data-stu-id="e53db-119">**Smart**</span></span>  
 <span data-ttu-id="e53db-120">如果選取此選項，當您按下 ENTER 時所建立之新行的位置，就會根據內容而定。</span><span class="sxs-lookup"><span data-stu-id="e53db-120">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="e53db-121">索引標籤</span><span class="sxs-lookup"><span data-stu-id="e53db-121">Tabs</span></span>  
 <span data-ttu-id="e53db-122">**定位點大小**</span><span class="sxs-lookup"><span data-stu-id="e53db-122">**Tab size**</span></span>  
 <span data-ttu-id="e53db-123">以空格數目，設定各定位點之間的距離。</span><span class="sxs-lookup"><span data-stu-id="e53db-123">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="e53db-124">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="e53db-124">The default is four spaces.</span></span>  
  
 <span data-ttu-id="e53db-125">**縮排大小**</span><span class="sxs-lookup"><span data-stu-id="e53db-125">**Indent size**</span></span>  
 <span data-ttu-id="e53db-126">以空格數目，設定自動縮排的大小。</span><span class="sxs-lookup"><span data-stu-id="e53db-126">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="e53db-127">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="e53db-127">The default is four spaces.</span></span> <span data-ttu-id="e53db-128">將會插入定位字元、空格字元或兩者，以填滿指定的大小。</span><span class="sxs-lookup"><span data-stu-id="e53db-128">Tab characters, space characters, or both will be inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="e53db-129">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="e53db-129">**Insert spaces**</span></span>  
 <span data-ttu-id="e53db-130">如果選取此選項，縮排作業僅會插入空格字元，而非定位字元。</span><span class="sxs-lookup"><span data-stu-id="e53db-130">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="e53db-131">例如，若 [縮排大小]\*\*\*\* 設定為 5，在您按下 TAB 鍵或在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 主視窗的工具列上按一下 [增加縮排]\*\*\*\* 按鈕時，就會插入五個空格字元。</span><span class="sxs-lookup"><span data-stu-id="e53db-131">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] main window.</span></span>  
  
 <span data-ttu-id="e53db-132">**保留定位點**</span><span class="sxs-lookup"><span data-stu-id="e53db-132">**Keep tabs**</span></span>  
 <span data-ttu-id="e53db-133">如果選取此選項，縮排作業會儘可能插入最多的定位字元。</span><span class="sxs-lookup"><span data-stu-id="e53db-133">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="e53db-134">每個定位字元會填滿 **[定位點大小]** 中所指定的空格數目。</span><span class="sxs-lookup"><span data-stu-id="e53db-134">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="e53db-135">如果 **[縮排大小]** 不是 **[定位點大小]** 的倍數，就會加入空格字元以填滿差異。</span><span class="sxs-lookup"><span data-stu-id="e53db-135">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
