---
title: 屬性資料翻譯對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
author: minewiskan
ms.author: owend
ms.openlocfilehash: b61022ec2cb8726fc034e13a0d63e432df6ec151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593175"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="a6254-102">屬性資料翻譯對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="a6254-102">Attribute Data Translation Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a6254-103">使用 [屬性資料翻譯]\*\*\*\* 對話方塊，即可設定包含翻譯標題資料的資料行，以及要用於翻譯資料的定序和排序次序。</span><span class="sxs-lookup"><span data-stu-id="a6254-103">Use the **Attribute Data Translation** dialog box to set the column that contains the translation caption data, as well as the collation and sort order to be used with the translated data.</span></span> <span data-ttu-id="a6254-104">您可依下列方式顯示 [屬性資料翻譯]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="a6254-104">You can display the **Attribute Data Translation** dialog box by:</span></span>  
  
-   <span data-ttu-id="a6254-105">從 [維度設計師]\*\*\*\* 之 [翻譯]\*\*\*\* 索引標籤上的 [工具列]\*\*\*\* 窗格，按一下 [新增標題資料行]\*\*\*\* 或 [編輯標題資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a6254-105">Clicking **New caption column** or **Edit caption column** from the **Toolbar** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="a6254-106">以滑鼠右鍵按一下 [維度設計師]\*\*\*\* 之 [翻譯]\*\*\*\* 索引標籤上的 [翻譯詳細資料]\*\*\*\* 窗格，然後選取 [新增標題資料行]\*\*\*\* 或 [編輯標題資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a6254-106">Right-clicking the **Translation Details** pane on the **Translations** tab of **Dimension Designer** and selecting **New caption column** or **Edit caption column**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6254-107">選項</span><span class="sxs-lookup"><span data-stu-id="a6254-107">Options</span></span>  
 <span data-ttu-id="a6254-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a6254-108">**Attribute**</span></span>  
 <span data-ttu-id="a6254-109">顯示選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6254-109">Displays the selected attribute.</span></span>  
  
 <span data-ttu-id="a6254-110">**語言**</span><span class="sxs-lookup"><span data-stu-id="a6254-110">**Language**</span></span>  
 <span data-ttu-id="a6254-111">顯示選取的語言。</span><span class="sxs-lookup"><span data-stu-id="a6254-111">Displays the selected language.</span></span>  
  
 <span data-ttu-id="a6254-112">**已翻譯標題**</span><span class="sxs-lookup"><span data-stu-id="a6254-112">**Translated caption**</span></span>  
 <span data-ttu-id="a6254-113">設定所選屬性的目前已翻譯標題。</span><span class="sxs-lookup"><span data-stu-id="a6254-113">Sets the current translated caption for the selected attribute.</span></span>  
  
 <span data-ttu-id="a6254-114">**翻譯資料行**</span><span class="sxs-lookup"><span data-stu-id="a6254-114">**Translation columns**</span></span>  
 <span data-ttu-id="a6254-115">設定儲存翻譯標題資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="a6254-115">Sets the column where the translation caption data is stored.</span></span> <span data-ttu-id="a6254-116">只能選取一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a6254-116">Only one column can be selected.</span></span> <span data-ttu-id="a6254-117">將會顯示主維度資料表所參考的所有相關資料表。</span><span class="sxs-lookup"><span data-stu-id="a6254-117">All related tables that are referred to by the primary dimension table will be displayed.</span></span>  
  
 <span data-ttu-id="a6254-118">**定序指示項**</span><span class="sxs-lookup"><span data-stu-id="a6254-118">**Collation designator**</span></span>  
 <span data-ttu-id="a6254-119">設定所選屬性的定序指示項。</span><span class="sxs-lookup"><span data-stu-id="a6254-119">Sets the collation designator for the selected attribute.</span></span> <span data-ttu-id="a6254-120">依預設，會選取目前的 Windows 定序。</span><span class="sxs-lookup"><span data-stu-id="a6254-120">By default, the current Windows collation is selected.</span></span> <span data-ttu-id="a6254-121">按一下向下箭頭即可從可用的定序中選取定序。</span><span class="sxs-lookup"><span data-stu-id="a6254-121">Click the down arrow to select from the available collations.</span></span>  
  
 <span data-ttu-id="a6254-122">**二進位**</span><span class="sxs-lookup"><span data-stu-id="a6254-122">**Binary**</span></span>  
 <span data-ttu-id="a6254-123">選取此選項，即可根據為每個字元定義的位元模式來排序和比較資料。</span><span class="sxs-lookup"><span data-stu-id="a6254-123">Select this option to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="a6254-124">二進位排序順序有區分大小寫，亦即小寫優先於大寫，而且有區分腔調字。</span><span class="sxs-lookup"><span data-stu-id="a6254-124">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="a6254-125">這是最快的排序順序。</span><span class="sxs-lookup"><span data-stu-id="a6254-125">This is the fastest sorting order.</span></span>  
  
 <span data-ttu-id="a6254-126">如果沒有選取此選項， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會遵循相關聯之語言或字母字典中所定義的排序和比較規則。</span><span class="sxs-lookup"><span data-stu-id="a6254-126">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6254-127">如果選取此選項，會停用 [區分大小寫]\*\*\*\*、[區分腔調字]\*\*\*\*、[區分假名]\*\*\*\* 和 [區分全半形]\*\*\*\* 等選項。</span><span class="sxs-lookup"><span data-stu-id="a6254-127">If this option is selected, the **Case sensitive**, **Accent sensitive**, **Kana sensitive**, and **Width sensitive** options are disabled.</span></span>  
  
 <span data-ttu-id="a6254-128">**區分大小寫**</span><span class="sxs-lookup"><span data-stu-id="a6254-128">**Case sensitive**</span></span>  
 <span data-ttu-id="a6254-129">選取此選項，即可根據為關聯之語言或字母提供的字典規則來排序和比較資料，以及區別大寫和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="a6254-129">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
 <span data-ttu-id="a6254-130">如果未選取，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會將大小寫字母視為相同。</span><span class="sxs-lookup"><span data-stu-id="a6254-130">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="a6254-131">未選取 [區分**大小寫**] 時，不會定義小寫字母是否會以較低或較高的方式排序。</span><span class="sxs-lookup"><span data-stu-id="a6254-131">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
 <span data-ttu-id="a6254-132">**區分腔調字**</span><span class="sxs-lookup"><span data-stu-id="a6254-132">**Accent sensitive**</span></span>  
 <span data-ttu-id="a6254-133">選取此選項，即可根據為關聯之語言或字母提供的字典規則來排序和比較資料，以及區別有腔調和無腔調字元。</span><span class="sxs-lookup"><span data-stu-id="a6254-133">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="a6254-134">例如，'a' 不等於 'á'。</span><span class="sxs-lookup"><span data-stu-id="a6254-134">For example, 'a' is not equal to 'á'.</span></span>  
  
 <span data-ttu-id="a6254-135">如果未選取， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會將有腔調與無腔調的字母視為相同。</span><span class="sxs-lookup"><span data-stu-id="a6254-135">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
 <span data-ttu-id="a6254-136">**區分假名**</span><span class="sxs-lookup"><span data-stu-id="a6254-136">**Kana sensitive**</span></span>  
 <span data-ttu-id="a6254-137">選取此選項，即可根據為關聯之語言或字母提供的字典規則來排序和比較資料，以及區別兩種日文假名字元：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="a6254-137">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
 <span data-ttu-id="a6254-138">如果未選取， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會將平假名與片假名字元視為相同。</span><span class="sxs-lookup"><span data-stu-id="a6254-138">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
 <span data-ttu-id="a6254-139">**區分全半形**</span><span class="sxs-lookup"><span data-stu-id="a6254-139">**Width sensitive**</span></span>  
 <span data-ttu-id="a6254-140">選取此選項，即可根據為關聯之語言或字母提供的字典規則來排序和比較資料，以及區別單一位元組字元 (半形) 和使用雙位元組字元 (全形) 表示的相同字元。</span><span class="sxs-lookup"><span data-stu-id="a6254-140">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
 <span data-ttu-id="a6254-141">如果未選取， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會將相同字元的單一位元組與雙位元組表示方式視為相同。</span><span class="sxs-lookup"><span data-stu-id="a6254-141">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6254-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6254-142">See Also</span></span>  
 <span data-ttu-id="a6254-143">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a6254-143">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a6254-144">[翻譯詳細資料 &#40;[翻譯] 索引標籤、[維度設計師]&#41; &#40;Analysis Services 多維度資料&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="a6254-144">[Translation Details &#40;Translations Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
