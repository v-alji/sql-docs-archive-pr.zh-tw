---
title: " (文字編輯器的選項-Transact-sql-索引標籤頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
author: rothja
ms.author: jroth
ms.openlocfilehash: 6caa659d13f8089fdd9f990a55e503657ef72a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597992"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a><span data-ttu-id="b0089-102"> (文字編輯器的選項-Transact-sql-索引標籤頁面) </span><span class="sxs-lookup"><span data-stu-id="b0089-102">Options (Text Editor - Transact-SQL - Tabs Page)</span></span>
  <span data-ttu-id="b0089-103">使用這個對話方塊可以變更在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器中按下 Tab 鍵的移動行為，這個編輯器會用來撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b0089-103">Use this dialog to change the tabbing behavior of the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor, which is used to program [!INCLUDE[tsql](../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="b0089-104">若要顯示這些設定，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*，並展開 [文字編輯器]\*\*\*\* 資料夾，再展開 [Transact-SQL]\*\*\*\* 子資料夾，然後按一下 [定位點]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0089-104">To display these settings, click **Options** on the **Tools** menu, expand the **Text Editor** folder, expand the **Transact-SQL** subfolder and then click **Tabs**.</span></span>  
  
## <a name="setting-options-in-multiple-locations"></a><span data-ttu-id="b0089-105">在多個位置設定選項</span><span class="sxs-lookup"><span data-stu-id="b0089-105">Setting Options in Multiple Locations</span></span>  
 <span data-ttu-id="b0089-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器的選項也可以在 [所有語言 - 索引標籤]\*\*\*\* 對話方塊中設定。</span><span class="sxs-lookup"><span data-stu-id="b0089-106">Options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor can also be set in the **All Languages Tabs** dialog.</span></span> <span data-ttu-id="b0089-107">如果您使用 **[所有語言]** 對話方塊為其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 編輯器 (例如 DMX 或 MDX 編輯器) 設定不同的選項，則必須使用這個對話方塊重設 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器選項。</span><span class="sxs-lookup"><span data-stu-id="b0089-107">If you use the **All Languages** dialogs to set different options for the other [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] editors, such as the DMX or MDX editors, you must reset the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor options using this dialog.</span></span>  
  
## <a name="indenting"></a><span data-ttu-id="b0089-108">縮排</span><span class="sxs-lookup"><span data-stu-id="b0089-108">Indenting</span></span>  
 <span data-ttu-id="b0089-109">**None**</span><span class="sxs-lookup"><span data-stu-id="b0089-109">**None**</span></span>  
 <span data-ttu-id="b0089-110">如果選取此選項，當您按下 ENTER 時所建立的新行就不會縮排。</span><span class="sxs-lookup"><span data-stu-id="b0089-110">When this option is selected, the new line created when you press ENTER is not indented.</span></span> <span data-ttu-id="b0089-111">資料指標會放在新行的第一個資料行上。</span><span class="sxs-lookup"><span data-stu-id="b0089-111">The cursor is placed at the first column of the new line.</span></span>  
  
 <span data-ttu-id="b0089-112">**封鎖**</span><span class="sxs-lookup"><span data-stu-id="b0089-112">**Block**</span></span>  
 <span data-ttu-id="b0089-113">如果選取此選項，當您按下 ENTER 鍵時所建立的新行就會自動縮排與上一行相同的距離。</span><span class="sxs-lookup"><span data-stu-id="b0089-113">When this option is selected, the new line created when you press ENTER is automatically indented the same distance as the previous line.</span></span>  
  
 <span data-ttu-id="b0089-114">**智慧型**</span><span class="sxs-lookup"><span data-stu-id="b0089-114">**Smart**</span></span>  
 <span data-ttu-id="b0089-115">此選項無法使用。</span><span class="sxs-lookup"><span data-stu-id="b0089-115">This option is unavailable.</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="b0089-116">索引標籤</span><span class="sxs-lookup"><span data-stu-id="b0089-116">Tabs</span></span>  
 <span data-ttu-id="b0089-117">**定位點大小**</span><span class="sxs-lookup"><span data-stu-id="b0089-117">**Tab size**</span></span>  
 <span data-ttu-id="b0089-118">以空格數目，設定各定位點之間的距離。</span><span class="sxs-lookup"><span data-stu-id="b0089-118">Sets the distance in spaces between tab stops.</span></span> <span data-ttu-id="b0089-119">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="b0089-119">The default is four spaces.</span></span>  
  
 <span data-ttu-id="b0089-120">**縮排大小**</span><span class="sxs-lookup"><span data-stu-id="b0089-120">**Indent size**</span></span>  
 <span data-ttu-id="b0089-121">以空格數目，設定自動縮排的大小。</span><span class="sxs-lookup"><span data-stu-id="b0089-121">Sets the size in spaces of an automatic indentation.</span></span> <span data-ttu-id="b0089-122">預設值為四個空格。</span><span class="sxs-lookup"><span data-stu-id="b0089-122">The default is four spaces.</span></span> <span data-ttu-id="b0089-123">會插入定位字元、空格字元或兩者，以填滿指定的大小。</span><span class="sxs-lookup"><span data-stu-id="b0089-123">Tab characters, space characters, or both are inserted to fill the specified size.</span></span>  
  
 <span data-ttu-id="b0089-124">**插入空格**</span><span class="sxs-lookup"><span data-stu-id="b0089-124">**Insert spaces**</span></span>  
 <span data-ttu-id="b0089-125">如果選取此選項，縮排作業僅會插入空格字元，而非定位字元。</span><span class="sxs-lookup"><span data-stu-id="b0089-125">When this option is selected, indent operations insert only space characters, not tab characters.</span></span> <span data-ttu-id="b0089-126">例如，如果 [**縮排大小**] 設為5，則每當您按下 TAB 鍵或在主視窗的工具列上按一下 [**增加縮排**] 按鈕時，就會插入五個空白字元 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b0089-126">If **Indent size** is set to 5, for example, then five space characters are inserted whenever you press the TAB key or click the **Increase Indent** button on the toolbar in the main [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] window.</span></span>  
  
 <span data-ttu-id="b0089-127">**保留定位點**</span><span class="sxs-lookup"><span data-stu-id="b0089-127">**Keep tabs**</span></span>  
 <span data-ttu-id="b0089-128">如果選取此選項，縮排作業會儘可能插入最多的定位字元。</span><span class="sxs-lookup"><span data-stu-id="b0089-128">When this option is selected, indent operations insert as many tab characters as possible.</span></span> <span data-ttu-id="b0089-129">每個定位字元會填滿 **[定位點大小]** 中所指定的空格數目。</span><span class="sxs-lookup"><span data-stu-id="b0089-129">Each tab character fills the number of spaces specified in **Tab size**.</span></span> <span data-ttu-id="b0089-130">如果 **[縮排大小]** 不是 **[定位點大小]** 的倍數，就會加入空格字元以填滿差異。</span><span class="sxs-lookup"><span data-stu-id="b0089-130">If **Indent size** is not an even multiple of **Tab size**, space characters are added to fill in the difference.</span></span>  
  
  
