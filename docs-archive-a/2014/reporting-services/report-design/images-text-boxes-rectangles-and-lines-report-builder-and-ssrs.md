---
title: 影像、文字方塊、矩形和線條 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa7ad08f-dd49-401e-9619-522e27055bb9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fb9a47bb3b8d68d48be42f8f0a2adddfc3ba130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688582"
---
# <a name="images-text-boxes-rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="27a97-102">影像、文字方塊、矩形和線條 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="27a97-102">Images, Text Boxes, Rectangles, and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="27a97-103">除了資料表、矩陣和圖表之類的資料區外，報表也會使用其他的報表項目 (例如影像、文字方塊和矩形) 來加入視覺趣味、反白顯示主要資訊，或提供相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="27a97-103">In addition to data regions like tables, matrices, and charts, reports use other report items like images, text boxes, and rectangles to add visual interest, highlight key information, or provide related information.</span></span> <span data-ttu-id="27a97-104">您可以變更報表項目的格式。</span><span class="sxs-lookup"><span data-stu-id="27a97-104">You can change the formatting of a report item.</span></span> <span data-ttu-id="27a97-105">例如，您可以加入框線或填補、變更初始的可見性或方向，或指定項目的精確大小及位置。</span><span class="sxs-lookup"><span data-stu-id="27a97-105">For example, you can add a border or padding, change the initial visibility or direction, or specify an exact size and location for the item.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="27a97-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="27a97-106">In This Section</span></span>  
 [<span data-ttu-id="27a97-107">文字方塊 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="27a97-107">Text Boxes &#40;Report Builder and SSRS&#41;</span></span>](text-boxes-report-builder-and-ssrs.md)  
 <span data-ttu-id="27a97-108">文字方塊可以放在報表的任何地方，且可以包含標籤、欄位或導出資料。</span><span class="sxs-lookup"><span data-stu-id="27a97-108">Text boxes can be placed anywhere on a report and can contain labels, fields, or calculated data.</span></span> <span data-ttu-id="27a97-109">您可以利用運算式來定義檢視報表時在文字方塊中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="27a97-109">You use expressions to define the value to display in a text box when you view a report.</span></span>  
  
 <span data-ttu-id="27a97-110">資料表或矩陣中的每個資料格都是文字方塊，可讓您以格式化獨立文字方塊的方式進行格式化。</span><span class="sxs-lookup"><span data-stu-id="27a97-110">Every cell in a table or matrix is also a text box, which you can format in the same way that you format stand-alone text boxes.</span></span>  
  
 [<span data-ttu-id="27a97-111">矩形和線條 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="27a97-111">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
 <span data-ttu-id="27a97-112">**線條** 會以水平、垂直或對角線方式顯示。</span><span class="sxs-lookup"><span data-stu-id="27a97-112">**Lines** display horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="27a97-113">線條是由起點和終點定義，且可以指定各種樣式 (例如粗細和色彩)。</span><span class="sxs-lookup"><span data-stu-id="27a97-113">A line is defined with a start and end point and can have various styles (for example, weight and color) assigned to it.</span></span> <span data-ttu-id="27a97-114">線條沒有相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="27a97-114">A line has no data associated with it.</span></span>  
  
 <span data-ttu-id="27a97-115">**矩形** 可以當做圖形元素或其他報表項目的容器使用。</span><span class="sxs-lookup"><span data-stu-id="27a97-115">**Rectangles** can be used as a graphical element, or as a container for other report items.</span></span> <span data-ttu-id="27a97-116">當做圖形元素使用時，矩形擁有的屬性與線條相同。</span><span class="sxs-lookup"><span data-stu-id="27a97-116">As a graphical element, a rectangle has the same properties as a line.</span></span> <span data-ttu-id="27a97-117">當做容器使用時，矩形可以當做其中所有報表項目的父容器。</span><span class="sxs-lookup"><span data-stu-id="27a97-117">As a container, a rectangle acts as a parent container for all report items inside it.</span></span> <span data-ttu-id="27a97-118">將報表項目置於父容器，有助於控制這些項目在每個報表頁面上的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="27a97-118">Placing report items in a parent container helps control how they appear on each report page.</span></span>  
  
 [<span data-ttu-id="27a97-119">影像 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="27a97-119">Images &#40;Report Builder and SSRS&#41;</span></span>](images-report-builder-and-ssrs.md)  
 <span data-ttu-id="27a97-120">影像會顯示報表中的二進位影像資料。</span><span class="sxs-lookup"><span data-stu-id="27a97-120">Images display binary image data in a report.</span></span> <span data-ttu-id="27a97-121">您可以提供影像來源。</span><span class="sxs-lookup"><span data-stu-id="27a97-121">You provide the source for the image.</span></span> <span data-ttu-id="27a97-122">來源可以是 Web 伺服器上所儲存影像的 URL 參考、內嵌影像資料的參考，或資料庫中二進位影像資料的參考。</span><span class="sxs-lookup"><span data-stu-id="27a97-122">The source can be a URL reference to an image stored on a Web server, a reference to embedded image data, or a reference to binary image data in a database.</span></span> <span data-ttu-id="27a97-123">報表產生器和報表設計師支援 .bmp、.jpeg、.gif 和 .png 檔案。</span><span class="sxs-lookup"><span data-stu-id="27a97-123">Report Builder and Report Designer support .bmp, .jpeg, .gif, and .png files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a97-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27a97-124">See Also</span></span>  
 [<span data-ttu-id="27a97-125">設定報表項目的格式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="27a97-125">Formatting Report Items &#40;Report Builder and SSRS&#41;</span></span>](formatting-report-items-report-builder-and-ssrs.md)  
  
  
