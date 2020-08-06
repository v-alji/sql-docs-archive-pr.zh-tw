---
title: 選項 (文字編輯器： XML：定位點頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 3047d6c05ffb88d07a4bf2e5b1d4143412046c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686466"
---
# <a name="options-text-editorxmltabs-page"></a><span data-ttu-id="9f037-102">選項 (文字編輯器：XML：定位點頁面)</span><span class="sxs-lookup"><span data-stu-id="9f037-102">Options (Text Editor:XML:Tabs Page)</span></span>
  <span data-ttu-id="9f037-103">這個對話方塊可以讓您變更在 XML 編輯器中按下 Tab 鍵的移動行為，這個編輯器會用來編輯 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="9f037-103">This dialog box lets you change the tabbing behavior of the XML Editor, which is used to edit XML documents.</span></span> <span data-ttu-id="9f037-104">若要顯示這些設定，請按一下 **[工具]** 功能表上的 **[選項]** ，展開 **[文字編輯器]** 資料夾，展開 **[XML]** 子資料夾，然後按一下 **[定位點]**。</span><span class="sxs-lookup"><span data-stu-id="9f037-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **XML** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="9f037-105">在多個位置設定選項</span><span class="sxs-lookup"><span data-stu-id="9f037-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="9f037-106">XML 編輯器的選項也可以在 **[所有語言 - 一般]** 對話方塊中設定。</span><span class="sxs-lookup"><span data-stu-id="9f037-106">Options for the XML Editor can also be set in the **All Languages General** dialog.</span></span> <span data-ttu-id="9f037-107">如果您使用 **[所有語言]** 對話方塊為其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 編輯器 (例如 DMX 或 MDX 編輯器) 設定不同的選項，則必須使用這個對話方塊重設 XML 編輯器選項。</span><span class="sxs-lookup"><span data-stu-id="9f037-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the XML Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="9f037-108">縮排</span><span class="sxs-lookup"><span data-stu-id="9f037-108">Indenting</span></span>  
 <span data-ttu-id="9f037-109">**None**</span><span class="sxs-lookup"><span data-stu-id="9f037-109">**None**</span></span>  
 <span data-ttu-id="9f037-110">如果選取此選項，當您按下 ENTER 時所建立的新行就不會縮排。</span><span class="sxs-lookup"><span data-stu-id="9f037-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="9f037-111">資料指標會放在新行的第一個資料行上。</span><span class="sxs-lookup"><span data-stu-id="9f037-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="9f037-112">**封鎖**</span><span class="sxs-lookup"><span data-stu-id="9f037-112">**Block**</span></span>  
 <span data-ttu-id="9f037-113">如果選取此選項，當您按下 ENTER 鍵時所建立的新行就會自動縮排與上一行相同的距離。</span><span class="sxs-lookup"><span data-stu-id="9f037-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="9f037-114">**智慧型**</span><span class="sxs-lookup"><span data-stu-id="9f037-114">**Smart**</span></span>  
 <span data-ttu-id="9f037-115">如果選取此選項，當您按下 ENTER 時所建立之新行的位置，就會根據內容而定。</span><span class="sxs-lookup"><span data-stu-id="9f037-115">When this option is selected, the new line created when you press ENTER is positioned according to the context.</span></span> <span data-ttu-id="9f037-116">例如，在左大括號 ({) 之後，其中的行會自動增加一個定位點的縮排距離。</span><span class="sxs-lookup"><span data-stu-id="9f037-116">For example, after an opening brace ({), the included lines are automatically indented an extra tab stop.</span></span> <span data-ttu-id="9f037-117">對應的右大括號 (}) 則與左大括號重新對齊。</span><span class="sxs-lookup"><span data-stu-id="9f037-117">The matching closing brace (}) is realigned with its opening brace.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="9f037-118">索引標籤</span><span class="sxs-lookup"><span data-stu-id="9f037-118">Tabs</span></span>  
 <span data-ttu-id="9f037-119">**定位點大小**</span><span class="sxs-lookup"><span data-stu-id="9f037-119">**Tab size**</span></span>  
 <span data-ttu-id="9f037-120">以空格數目，設定各定位點之間的距離。</span><span class="sxs-lookup"><span data-stu-id="9f037-120">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="9f037-121">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="9f037-121">The default is four spaces.</span></span>  
  
 <span data-ttu-id="9f037-122">**縮排大小**</span><span class="sxs-lookup"><span data-stu-id="9f037-122">**Indent size**</span></span>  
 <span data-ttu-id="9f037-123">以空格數目，設定自動縮排的大小。</span><span class="sxs-lookup"><span data-stu-id="9f037-123">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="9f037-124">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="9f037-124">The default is four spaces.</span></span> <span data-ttu-id="9f037-125">會插入定位字元、空格字元或兩者，以填滿指定的大小。</span><span class="sxs-lookup"><span data-stu-id="9f037-125">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="9f037-126">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="9f037-126">**Insert spaces**</span></span>  
 <span data-ttu-id="9f037-127">如果選取此選項，縮排作業僅會插入空格字元，而非定位字元。</span><span class="sxs-lookup"><span data-stu-id="9f037-127">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="9f037-128">例如，如果 [**縮排大小**] 設為5，則每當您按下 TAB 鍵或在主視窗的工具列上按一下 [**增加縮排**] 按鈕時，就會插入五個空白字元 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9f037-128">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="9f037-129">**保留定位點**</span><span class="sxs-lookup"><span data-stu-id="9f037-129">**Keep tabs**</span></span>  
 <span data-ttu-id="9f037-130">如果選取此選項，縮排作業會儘可能插入最多的定位字元。</span><span class="sxs-lookup"><span data-stu-id="9f037-130">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="9f037-131">每個定位字元會填滿 **[定位點大小]** 中所指定的空格數目。</span><span class="sxs-lookup"><span data-stu-id="9f037-131">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="9f037-132">如果 **[縮排大小]** 不是 **[定位點大小]** 的倍數，就會加入空格字元以填滿差異。</span><span class="sxs-lookup"><span data-stu-id="9f037-132">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
