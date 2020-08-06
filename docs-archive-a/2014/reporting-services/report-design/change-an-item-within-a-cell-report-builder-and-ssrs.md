---
title: 變更資料格內的項目 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 80ef171713e6505867e00e343ce17b70cab9045a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710197"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a><span data-ttu-id="1a11c-102">變更資料格內的項目 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1a11c-102">Change an Item Within a Cell (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a11c-103">只有非容器項目 (例如文字方塊、線條或影像) 才能以新報表項目來取代。</span><span class="sxs-lookup"><span data-stu-id="1a11c-103">Only a non-container item, such as a text box, line, or image, can be replaced by a new report item.</span></span> <span data-ttu-id="1a11c-104">例如，您可以將資料表拖曳到文字方塊，即可以資料表取代文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1a11c-104">For example, you can drag a table into a text box to replace the text box with a table.</span></span>  
  
 <span data-ttu-id="1a11c-105">如果資料格含有矩形、清單、資料表或矩陣等容器項目，就會將新項目加入至包含項目中而非取代它。</span><span class="sxs-lookup"><span data-stu-id="1a11c-105">If the cell contains a container item such as a rectangle, list, table, or matrix, the new item is added to the containing item instead of replacing it.</span></span> <span data-ttu-id="1a11c-106">若要以新的項目取代容器，請刪除此容器。</span><span class="sxs-lookup"><span data-stu-id="1a11c-106">To replace a container item with a new item, delete the container.</span></span> <span data-ttu-id="1a11c-107">刪除容器項目會以文字方塊來取代它，然後您可以用其他項目來取代此文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1a11c-107">Deleting the container item replaces it with a text box, which you can then replace with another item.</span></span>  
  
 <span data-ttu-id="1a11c-108">根據預設，資料表、矩陣或清單資料區內的所有資料格都有包含文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1a11c-108">By default, all cells in a table, matrix, or list data region contain a text box.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a><span data-ttu-id="1a11c-109">若要變更資料格內的項目</span><span class="sxs-lookup"><span data-stu-id="1a11c-109">To change an item within a cell</span></span>  
  
-   <span data-ttu-id="1a11c-110">在 **[插入]** 索引標籤的 **[資料區域]** 或 **[報表項目]** 群組中，按一下您想要加入至報表的項目，然後按一下報表。</span><span class="sxs-lookup"><span data-stu-id="1a11c-110">On the **Insert** tab, in the **Data Regions** or **Report Items** group, click the item that you want to add to the report, and then click the report.</span></span> <span data-ttu-id="1a11c-111">如此項目就會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="1a11c-111">The item is added to the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a11c-112">當您將影像報表項目拖曳至資料格時，[影像屬性]  對話方塊即會開啟，讓您設定屬性；例如，影像新增至資料格前的影像來源。</span><span class="sxs-lookup"><span data-stu-id="1a11c-112">The **Image Properties** dialog box opens when you drag an image report item to a cell, where you can set properties such as the source of the image before the image is added to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a11c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a11c-113">See Also</span></span>  
 <span data-ttu-id="1a11c-114">[影像、文字方塊、矩形和線條 &#40;報表產生器及 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a11c-114">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a11c-115">清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1a11c-115">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
