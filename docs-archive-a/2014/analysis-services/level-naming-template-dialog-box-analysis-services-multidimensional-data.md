---
title: 層級命名範本對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710934"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="7ce2b-102">層級命名範本對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="7ce2b-102">Level Naming Template Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7ce2b-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [層級命名範本]\*\*\*\* 對話方塊，即可建構維度中之父屬性的層級命名範本。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-103">Use the **Level Naming Template** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to construct the level naming template for a parent attribute in a dimension.</span></span> <span data-ttu-id="7ce2b-104">如需層級命名範本的詳細資訊，請參閱 [NamingTemplate 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-104">For more information about level naming templates, see [NamingTemplate Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl).</span></span> <span data-ttu-id="7ce2b-105">您可以在 **...** [維度設計師] 之 [翻譯] 索引標籤上的 [翻譯詳細資料] 窗格中，按一下屬性轉譯值的省略號按鈕 (...) ，來顯示 [**層級命名範本**] 對話方塊。 `NamingTemplate` **Translation Details** **Translations** **Dimension Designer**</span><span class="sxs-lookup"><span data-stu-id="7ce2b-105">You can display the **Level Naming Template** dialog box by clicking the ellipsis button (**...**) on the `NamingTemplate` value of a translation for an attribute in the **Translation Details** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7ce2b-106">選項</span><span class="sxs-lookup"><span data-stu-id="7ce2b-106">Options</span></span>  
  
|<span data-ttu-id="7ce2b-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="7ce2b-107">Term</span></span>|<span data-ttu-id="7ce2b-108">定義</span><span class="sxs-lookup"><span data-stu-id="7ce2b-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="7ce2b-109">**定義層級範本**</span><span class="sxs-lookup"><span data-stu-id="7ce2b-109">**Define the level template**</span></span>|<span data-ttu-id="7ce2b-110">顯示您可在其中設計父屬性之層級階層的方格。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-110">Displays a grid in which you can design the hierarchy of levels in the parent attribute.</span></span> <span data-ttu-id="7ce2b-111">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="7ce2b-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="7ce2b-112">**層級**：顯示在 [**名稱**] 中指定之名稱所用層級的序數位置。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-112">**Level**: Displays the ordinal position of the level for which the name specified in **Name** is used.</span></span> <span data-ttu-id="7ce2b-113">若要為層級加入新的命名範本，請在 [層級]\*\*\*\* 中包含星號 (\*) 的資料列上選取 [名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-113">To add a new naming template for a level, select **Name** on the row that contains an asterisk (\*) in **Level**.</span></span><br /><br /> <span data-ttu-id="7ce2b-114">**名稱**：包含用於 [**層級**] 中所指出之層級的命名範本。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-114">**Name**: Contains the naming template used for the level indicated in **Level**.</span></span> <span data-ttu-id="7ce2b-115">若要在命名範本中為層級序數位置加入預留位置，請加入單一星號 (\*)。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-115">To add a placeholder for the level ordinal position in the naming template, add a single asterisk (\*).</span></span> <span data-ttu-id="7ce2b-116">若要新增星號做為命名範本所建立之名稱的一部分，請將兩個星號新增 (\* \*) 。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-116">To add an asterisk as part of the name created by the naming template, add two asterisks (\*\*).</span></span>|  
|<span data-ttu-id="7ce2b-117">**全部清除**</span><span class="sxs-lookup"><span data-stu-id="7ce2b-117">**Clear All**</span></span>|<span data-ttu-id="7ce2b-118">選取即可移除 [定義層級範本]\*\*\*\* 中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-118">Select to remove all rows in **Define the level template**.</span></span>|  
|<span data-ttu-id="7ce2b-119">**結果**</span><span class="sxs-lookup"><span data-stu-id="7ce2b-119">**Result**</span></span>|<span data-ttu-id="7ce2b-120">顯示對話方塊所建構的層級命名範本。</span><span class="sxs-lookup"><span data-stu-id="7ce2b-120">Displays the level naming template constructed by the dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ce2b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ce2b-121">See Also</span></span>  
 <span data-ttu-id="7ce2b-122">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7ce2b-122">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7ce2b-123">翻譯 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="7ce2b-123">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
