---
title: 翻譯詳細資料 ([翻譯] 索引標籤、[維度設計師])  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7cbe4a3c69111d0f82f96ff5125f80fe0c2c57f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706754"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="32268-102">翻譯詳細資料 (翻譯索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="32268-102">Translation Details (Translations Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="32268-103">在 [維度設計師] 的 **[翻譯]** 索引標籤中使用 **[翻譯詳細資料]** 窗格，即可定義和管理目前所選取維度的翻譯。</span><span class="sxs-lookup"><span data-stu-id="32268-103">Use the **Translation Details** pane on the **Translations** tab of Dimension Designer to define and manage translations for the currently selected dimension.</span></span>  
  
 <span data-ttu-id="32268-104">**顯示翻譯詳細資料窗格**</span><span class="sxs-lookup"><span data-stu-id="32268-104">**To display the Translations Details pane**</span></span>  
  
1.  <span data-ttu-id="32268-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案，然後開啟所需的維度。</span><span class="sxs-lookup"><span data-stu-id="32268-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then open the dimension that you want.</span></span>  
  
2.  <span data-ttu-id="32268-106">按一下 **[翻譯]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="32268-106">Click the **Translations** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="32268-107">選項</span><span class="sxs-lookup"><span data-stu-id="32268-107">Options</span></span>  
 <span data-ttu-id="32268-108">**預設語言**</span><span class="sxs-lookup"><span data-stu-id="32268-108">**Default Language**</span></span>  
 <span data-ttu-id="32268-109">以預設語言設定維度物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="32268-109">Sets the names of the dimension objects in the default language.</span></span>  
  
 <span data-ttu-id="32268-110">**物件類型**</span><span class="sxs-lookup"><span data-stu-id="32268-110">**Object Type**</span></span>  
 <span data-ttu-id="32268-111">顯示將翻譯的屬性。</span><span class="sxs-lookup"><span data-stu-id="32268-111">Displays the property that will be translated.</span></span> <span data-ttu-id="32268-112">只有已指定值的物件和屬性可以翻譯。</span><span class="sxs-lookup"><span data-stu-id="32268-112">Only objects and properties for which values have been specified can be translated.</span></span> <span data-ttu-id="32268-113">下列屬性可被翻譯：</span><span class="sxs-lookup"><span data-stu-id="32268-113">The following properties can be translated:</span></span>  
  
-   <span data-ttu-id="32268-114">維度</span><span class="sxs-lookup"><span data-stu-id="32268-114">Dimension</span></span>  
  
     <span data-ttu-id="32268-115">`Caption` 和 `AttributeAllMember` 屬性</span><span class="sxs-lookup"><span data-stu-id="32268-115">`Caption` and `AttributeAllMember` properties</span></span>  
  
-   <span data-ttu-id="32268-116">屬性</span><span class="sxs-lookup"><span data-stu-id="32268-116">Attribute</span></span>  
  
     <span data-ttu-id="32268-117">`Caption`、`AttributeHierarchyDisplayFolder` 和 `NamingTemplate` 屬性</span><span class="sxs-lookup"><span data-stu-id="32268-117">`Caption`, `AttributeHierarchyDisplayFolder`, and `NamingTemplate` properties</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32268-118">`NamingTemplate` 屬性 (Property) 僅適用於父屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="32268-118">The `NamingTemplate` property is available only for parent attributes.</span></span>  
  
-   <span data-ttu-id="32268-119">階層</span><span class="sxs-lookup"><span data-stu-id="32268-119">Hierarchy</span></span>  
  
     <span data-ttu-id="32268-120">`Caption` 和 `AllMemberName` 屬性</span><span class="sxs-lookup"><span data-stu-id="32268-120">`Caption` and `AllMemberName` properties</span></span>  
  
-   <span data-ttu-id="32268-121">層級</span><span class="sxs-lookup"><span data-stu-id="32268-121">Level</span></span>  
  
     <span data-ttu-id="32268-122">`Caption` 屬性</span><span class="sxs-lookup"><span data-stu-id="32268-122">`Caption` property</span></span>  
  
 **\<Language>**  
 <span data-ttu-id="32268-123">以選取的語言鍵入或選取維度物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="32268-123">Type or select the property value of the dimension object in the selected language.</span></span> <span data-ttu-id="32268-124">按一下省略符號按鈕 (**...**) 會依據所編輯的屬性開啟其他對話方塊：</span><span class="sxs-lookup"><span data-stu-id="32268-124">Clicking the ellipsis button (**...**) opens additional dialog boxes, depending on the property being edited:</span></span>  
  
-   <span data-ttu-id="32268-125">`NamingTemplate` 屬性</span><span class="sxs-lookup"><span data-stu-id="32268-125">`NamingTemplate` property</span></span>  
  
     <span data-ttu-id="32268-126">顯示 [[層級命名範本] 對話方塊 &#40;Analysis Services - 多維度資料&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="32268-126">Displays the [Level Naming Template Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
-   <span data-ttu-id="32268-127">`Caption` 屬性 (Property) (適用於屬性 (Attribute))</span><span class="sxs-lookup"><span data-stu-id="32268-127">`Caption` property (for attributes)</span></span>  
  
     <span data-ttu-id="32268-128">顯示 [[屬性資料翻譯] 對話方塊 &#40;Analysis Services - 多維度資料&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="32268-128">Displays the [Attribute Data Translation Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="shortcut-menu"></a><span data-ttu-id="32268-129">快速鍵功能表</span><span class="sxs-lookup"><span data-stu-id="32268-129">Shortcut Menu</span></span>  
 <span data-ttu-id="32268-130">以滑鼠右鍵按一下 [翻譯詳細資料]\*\*\*\* 窗格中的翻譯，即可顯示提供下列選項的捷徑功能表：</span><span class="sxs-lookup"><span data-stu-id="32268-130">The following options are available in the shortcut menu displayed by right-clicking a translation in the **Translation Details** pane:</span></span>  
  
 <span data-ttu-id="32268-131">**新翻譯**</span><span class="sxs-lookup"><span data-stu-id="32268-131">**New Translation**</span></span>  
 <span data-ttu-id="32268-132">選取即可顯示 [選取語言]\*\*\*\* 對話方塊並建立新的翻譯。</span><span class="sxs-lookup"><span data-stu-id="32268-132">Select to display the **Select Language** dialog box and create a new translation.</span></span> <span data-ttu-id="32268-133">翻譯將會在 **[翻譯詳細資料]** 方格中顯示為新的資料行。</span><span class="sxs-lookup"><span data-stu-id="32268-133">The translation will appear as a new column in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="32268-134">**刪除翻譯**</span><span class="sxs-lookup"><span data-stu-id="32268-134">**Delete Translation**</span></span>  
 <span data-ttu-id="32268-135">選取以刪除選取的翻譯。</span><span class="sxs-lookup"><span data-stu-id="32268-135">Select to delete the selected translation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32268-136">唯有在資料格上按一下滑鼠右鍵來刪除翻譯時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="32268-136">The option is enabled only if you right-clicked a cell to delete the translation.</span></span>  
  
 <span data-ttu-id="32268-137">**新增標題資料行**</span><span class="sxs-lookup"><span data-stu-id="32268-137">**New Caption Column**</span></span>  
 <span data-ttu-id="32268-138">在 [翻譯詳細資料]\*\*\*\* 方格中修改屬性時，選取即可顯示 [屬性資料翻譯]\*\*\*\* 對話方塊，並定義新的標題資料行。</span><span class="sxs-lookup"><span data-stu-id="32268-138">Select to display the **Attribute Data Translation** dialog box and define a new caption column when you modify an attribute in the **Translation Details** grid.</span></span> <span data-ttu-id="32268-139">若要啟用此選項，必須在 **[翻譯詳細資料]** 方格中選取屬性之翻譯資料行中的資料格。</span><span class="sxs-lookup"><span data-stu-id="32268-139">To enable this option, a cell in a translation column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32268-140">唯有在資料格上按一下滑鼠右鍵來刪除屬性的翻譯資料行時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="32268-140">The option is enabled only if you right-clicked a cell to delete the translation column of an attribute.</span></span>  
  
 <span data-ttu-id="32268-141">**編輯標題資料行**</span><span class="sxs-lookup"><span data-stu-id="32268-141">**Edit Caption Column**</span></span>  
 <span data-ttu-id="32268-142">在 [翻譯詳細資料]\*\*\*\* 方格中修改屬性時，選取即可顯示 [屬性資料翻譯]\*\*\*\* 對話方塊，並修改現有的標題資料行。</span><span class="sxs-lookup"><span data-stu-id="32268-142">Select to display the **Attribute Data Translation** dialog box and modify an existing caption column when you modify an attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32268-143"> 唯有選取 **[翻譯詳細資料]** 方格中的翻譯資料行中、包含屬性標題資料行的資料格時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="32268-143">The option is enabled only if a cell in a translation column that contains a caption column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="32268-144">**刪除標題資料行**</span><span class="sxs-lookup"><span data-stu-id="32268-144">**Delete Caption Column**</span></span>  
 <span data-ttu-id="32268-145">選取即可刪除 [翻譯詳細資料]\*\*\*\* 方格中所選取屬性的標題資料行。</span><span class="sxs-lookup"><span data-stu-id="32268-145">Select to delete the caption column for the selected attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32268-146">唯有在翻譯資料行中，以滑鼠右鍵按一下包含屬性標題資料行的資料格時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="32268-146">The option is enabled only if you right-clicked a cell in a translation column that contains a caption column for an attribute.</span></span>  
  
 <span data-ttu-id="32268-147">**顯示所有屬性**</span><span class="sxs-lookup"><span data-stu-id="32268-147">**Show All Attributes**</span></span>  
 <span data-ttu-id="32268-148">選取即可切換顯示所選取維度已定義的所有屬性，包括已停用屬性階層的屬性。</span><span class="sxs-lookup"><span data-stu-id="32268-148">Select to toggle the display of all attributes defined for the selected dimension, including attributes for which attribute hierarchies are disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32268-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32268-149">See Also</span></span>  
 [<span data-ttu-id="32268-150">翻譯 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="32268-150">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
