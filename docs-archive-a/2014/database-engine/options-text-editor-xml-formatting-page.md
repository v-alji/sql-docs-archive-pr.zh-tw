---
title: " (文字編輯器的選項-XML-格式化頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
ms.openlocfilehash: dce36142fe9974c0167fca700c509642e05d89b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701539"
---
# <a name="options-text-editor---xml---formatting-page"></a><span data-ttu-id="9f077-102">選項 (文字編輯器 - XML - 格式化頁面)</span><span class="sxs-lookup"><span data-stu-id="9f077-102">Options (Text Editor - XML - Formatting Page)</span></span>

<span data-ttu-id="9f077-103">此對話方塊允許您指定 XML 編輯器的格式化設定。</span><span class="sxs-lookup"><span data-stu-id="9f077-103">This dialog box allows you to specify the formatting settings for the XML Editor.</span></span> <span data-ttu-id="9f077-104">您可以從 [工具]\*\*\*\* 功能表存取 [選項]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9f077-104">You can access the **Options** dialog box from the **Tools** menu.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="9f077-105">在選取 [文字編輯器]\*\*\*\* 資料夾、[XML]\*\*\*\* 資料夾，然後從 [選項]\*\*\*\* 對話方塊中選取 [格式化]\*\*\*\* 選項時，均可以使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="9f077-105">These settings are available when you select the **Text Editor** folder, the **XML** folder, and then the **Formatting** option from the **Options** dialog box.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="9f077-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9f077-106">Attributes</span></span>  
 <span data-ttu-id="9f077-107">**保留手動屬性格式化**</span><span class="sxs-lookup"><span data-stu-id="9f077-107">**Preserve manual attribute formatting**</span></span>  
 <span data-ttu-id="9f077-108">不要重新格式化屬性。</span><span class="sxs-lookup"><span data-stu-id="9f077-108">Do not reformat attributes.</span></span> <span data-ttu-id="9f077-109">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9f077-109">This is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f077-110">如果屬性在多行中，編輯器就會縮排每一個屬性行，以符合父元素的縮排。</span><span class="sxs-lookup"><span data-stu-id="9f077-110">If the attributes are on multiple lines, the editor indents each line of attributes to match the indentation of the parent element.</span></span>  
  
 <span data-ttu-id="9f077-111">**在個別的行上對齊每一個屬性**</span><span class="sxs-lookup"><span data-stu-id="9f077-111">**Align attributes each on a separate line**</span></span>  
 <span data-ttu-id="9f077-112">將第二個和後續的屬性垂直對齊，以符合第一個屬性的縮排。</span><span class="sxs-lookup"><span data-stu-id="9f077-112">Align the second and subsequent attributes vertically to match the indentation of the first attribute.</span></span> <span data-ttu-id="9f077-113">下列 XML 文字是如何對齊屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="9f077-113">The following XML text is an example of how the attributes would be aligned.</span></span>  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a><span data-ttu-id="9f077-114">自動重新格式化</span><span class="sxs-lookup"><span data-stu-id="9f077-114">Auto Reformat</span></span>  
 <span data-ttu-id="9f077-115">**從剪貼簿貼上時**</span><span class="sxs-lookup"><span data-stu-id="9f077-115">**On paste from clipboard.**</span></span>  
 <span data-ttu-id="9f077-116">重新格式化從剪貼簿貼上的 XML 文字。</span><span class="sxs-lookup"><span data-stu-id="9f077-116">Reformat XML text pasted from the clipboard.</span></span>  
  
 <span data-ttu-id="9f077-117">**完成結束標記時**</span><span class="sxs-lookup"><span data-stu-id="9f077-117">**On completion of end tag**</span></span>  
 <span data-ttu-id="9f077-118">完成結束標記時重新格式化元素。</span><span class="sxs-lookup"><span data-stu-id="9f077-118">Reformat the element when the end tag is completed.</span></span>  
  
## <a name="mixed-content"></a><span data-ttu-id="9f077-119">混合內容</span><span class="sxs-lookup"><span data-stu-id="9f077-119">Mixed Content</span></span>  
 <span data-ttu-id="9f077-120">**依預設，格式化混合內容。**</span><span class="sxs-lookup"><span data-stu-id="9f077-120">**Format mixed content by default.**</span></span>  
 <span data-ttu-id="9f077-121">嘗試重新格式化混合內容，但是在 `xml:space="preserve"` 範圍中找到的內容除外。</span><span class="sxs-lookup"><span data-stu-id="9f077-121">Attempt to reformat mixed content, except when the content is found in an `xml:space="preserve"` scope.</span></span> <span data-ttu-id="9f077-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9f077-122">This is the default.</span></span>  
  
 <span data-ttu-id="9f077-123">如果元素包含文字與標記的混合，則內容會被視為混合內容。</span><span class="sxs-lookup"><span data-stu-id="9f077-123">If an element contains a mix of text and markup, the contents are considered to be mixed content.</span></span> <span data-ttu-id="9f077-124">下列是具有混合內容之元素的範例。</span><span class="sxs-lookup"><span data-stu-id="9f077-124">Following is an example of an element with mixed content.</span></span>  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a><span data-ttu-id="9f077-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f077-125">See Also</span></span>  
 [<span data-ttu-id="9f077-126">XML 編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9f077-126">XML Editor &#40;SQL Server Management Studio&#41;</span></span>](../ssms/sql-server-management-studio-ssms.md)  
