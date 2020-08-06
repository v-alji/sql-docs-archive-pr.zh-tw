---
title: 設定文字方塊方向 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d509f1df29203fa5def79b61b74ae9db8f40d204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585026"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a><span data-ttu-id="8dc73-102">設定文字方塊方向 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8dc73-102">Set Text Box Orientation (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8dc73-103">文字方塊可以有不同的方向：水平、垂直 (從上到下閱讀文字)，或是旋轉 270 度 (從下到上閱讀文字)。</span><span class="sxs-lookup"><span data-stu-id="8dc73-103">A text box can be oriented in different directions: horizontally, vertically (text reading from top to bottom), or rotated by 270 degrees (text reading from bottom to top).</span></span> <span data-ttu-id="8dc73-104">因為方向會設定在文字方塊而不是文字上，所以方向會套用到文字方塊中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="8dc73-104">Because orientation is set on the text box not the text, the orientation applies to all the text in the text box.</span></span> <span data-ttu-id="8dc73-105">您不能針對文字的各個部分指定不同的方向。</span><span class="sxs-lookup"><span data-stu-id="8dc73-105">You cannot specify different orientations for parts of the text.</span></span> <span data-ttu-id="8dc73-106">手動調整資料行寬度及資料列高度，以配合旋轉的文字大小。</span><span class="sxs-lookup"><span data-stu-id="8dc73-106">Size the column width and the row height manually to accommodate the rotated text.</span></span>  
  
 <span data-ttu-id="8dc73-107">您用來指定文字方向的 WritingMode 屬性無法在 [**文字方塊屬性**] 對話方塊中使用。</span><span class="sxs-lookup"><span data-stu-id="8dc73-107">The WritingMode property, which you use to specify text orientation, is not available in the **Text Box Properties** dialog box.</span></span> <span data-ttu-id="8dc73-108">您需要開啟 [屬性] 窗格，然後在該處設定屬性。</span><span class="sxs-lookup"><span data-stu-id="8dc73-108">You need to open the Properties pane and set the property there.</span></span> <span data-ttu-id="8dc73-109">WritingMode 屬性可用的值為**水準** (文字讀取向右) 、從上到下讀取的**垂直** (文字) 、從底部到頂端 (閱讀的**Rotate270**) 文字。</span><span class="sxs-lookup"><span data-stu-id="8dc73-109">The available values for the WritingMode property are **Horizontal** (text reading left to right), **Vertical** (text reading top to bottom), **Rotate270** (text reading bottom to top).</span></span> <span data-ttu-id="8dc73-110">您必須手動調整資料行寬度及資料列高度，以便容納文字。</span><span class="sxs-lookup"><span data-stu-id="8dc73-110">You must manually size the column width and the row height to accommodate the text.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a><span data-ttu-id="8dc73-111">若要設定文字方向</span><span class="sxs-lookup"><span data-stu-id="8dc73-111">To set text orientation</span></span>  
  
1.  <span data-ttu-id="8dc73-112">建立新的報表或開啟現有的報表。</span><span class="sxs-lookup"><span data-stu-id="8dc73-112">Create a new report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="8dc73-113">如果 [屬性] 窗格並未開啟，請按一下 **[檢視]** 索引標籤，並選取 **[屬性]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8dc73-113">If the Properties pane is not open, click the **View** tab and select the **Properties** check box.</span></span>  
  
3.  <span data-ttu-id="8dc73-114">按一下您想要變更文字方向的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8dc73-114">Click the text box for which you want to change text orientation.</span></span>  
  
4.  <span data-ttu-id="8dc73-115">在 [屬性] 窗格中找出 [WritingMode] 屬性，然後在下拉式清單中選取要套用到文字方塊的文字方向。</span><span class="sxs-lookup"><span data-stu-id="8dc73-115">Locate the WritingMode property in the Properties pane and in the drop-down list select the text orientation to apply to the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dc73-116">當 [屬性] 窗格中的屬性組織成類別目錄時，WritingMode 會位於 [當地語系化]\*\*\*\* 類別目錄中。</span><span class="sxs-lookup"><span data-stu-id="8dc73-116">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span>  
  
5.  <span data-ttu-id="8dc73-117">在清單方塊中，選取 **[Horizontal]**、 **[Vertical]** 或 **[Rotate270]**。</span><span class="sxs-lookup"><span data-stu-id="8dc73-117">In the list box, select **Horizontal**, **Vertical**, or **Rotate270**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc73-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dc73-118">See Also</span></span>  
 <span data-ttu-id="8dc73-119">[文字方塊 &#40;報表產生器和 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8dc73-119">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8dc73-120">教學課程：格式化文字 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="8dc73-120">Tutorial: Format Text &#40;Report Builder&#41;</span></span>](../tutorial-format-text-report-builder.md)  
  
  
