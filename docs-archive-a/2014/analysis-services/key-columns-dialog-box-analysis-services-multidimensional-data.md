---
title: 索引鍵資料行對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a72a9e137700ddee822e68901bfde971637d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592956"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f3c5c-102">索引鍵資料行對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f3c5c-102">Key Columns Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f3c5c-103">使用 [索引鍵資料行]\*\*\*\* 對話方塊，即可變更屬性 (Attribute) 的 **KeyColumns** 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-103">Use the **Key Columns** dialog box to change the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="f3c5c-104">如需詳細資訊，請參閱 [修改屬性 (Attribute) 的 KeyColumn 屬性 (Property)](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-104">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
 <span data-ttu-id="f3c5c-105">**顯示索引鍵資料行對話方塊**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-105">**To display the Key Columns dialog box**</span></span>  
  
-   <span data-ttu-id="f3c5c-106">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，選取屬性 (Attribute)，然後在 [屬性]\*\*\*\* 視窗中，按一下與該屬性 (Attribute) 之 **KeyColumns** 屬性 (Property) 相關聯的省略符號按鈕 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-106">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select an attribute, and in the **Properties** window, click the ellipsis button (**...**) associated with the **KeyColumns** property of that attribute.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3c5c-107">選項</span><span class="sxs-lookup"><span data-stu-id="f3c5c-107">Options</span></span>  
 <span data-ttu-id="f3c5c-108">**來源資料表**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-108">**Source table**</span></span>  
 <span data-ttu-id="f3c5c-109">選取您想要選取其索引鍵資料行的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-109">Select the source table for which you want to select its key columns.</span></span> <span data-ttu-id="f3c5c-110">您可以從 [資料來源檢視] 中所有資料表的清單中，選取來源資料表。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-110">You can select the source table from a list of all tables in the Data Source View.</span></span>  
  
 <span data-ttu-id="f3c5c-111">**可用的資料行**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-111">**Available Columns**</span></span>  
 <span data-ttu-id="f3c5c-112">選取您想要當做索引鍵資料行使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-112">Select the columns that you want to use as key columns.</span></span> <span data-ttu-id="f3c5c-113">您可以從指定之 [來源資料表]\*\*\*\* 的資料行清單中選取尚未選取成索引鍵資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-113">You can select the columns from a list of columns in the specified **Source table** that have not yet been selected as key columns.</span></span>  
  
 <span data-ttu-id="f3c5c-114">若要將選取的資料行加入至 [索引**鍵資料行**] 清單，請按一下該 **>** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-114">To add the selected columns to the **Key Columns** list, click the **>** button.</span></span>  
  
 <span data-ttu-id="f3c5c-115">**索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-115">**Key Columns**</span></span>  
 <span data-ttu-id="f3c5c-116">定義選取之索引鍵資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-116">Define the order of the selected key columns.</span></span> <span data-ttu-id="f3c5c-117">索引鍵資料行的順序在定義正確的複合索引鍵時很重要。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-117">The order of the key columns is important in defining the correct composite key.</span></span> <span data-ttu-id="f3c5c-118">若要排序或重新排序索引鍵資料行的清單，請選取資料行，然後按一下 [向上]\*\*\*\* 或 [向下]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-118">To order or reorder the list of key columns, select a column, and then click the **Up** or **Down** buttons.</span></span>  
  
 <span data-ttu-id="f3c5c-119">若要從 [索引**鍵資料行**] 清單中移除資料行，請選取資料行，然後按一下 **\<** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-119">To remove a column from the **Key Columns** list, select the column and click the **\<** button.</span></span>  
  
 <span data-ttu-id="f3c5c-120">**設定**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-120">**Up**</span></span>  
 <span data-ttu-id="f3c5c-121">按一下即可將 [索引鍵資料行]\*\*\*\* 中選取的資料行向上移動一個位置。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-121">Click to move the column selected in **Key Columns** up one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3c5c-122">只有當清單包含一個以上的資料行而且選取了資料行時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-122">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 <span data-ttu-id="f3c5c-123">**Down**</span><span class="sxs-lookup"><span data-stu-id="f3c5c-123">**Down**</span></span>  
 <span data-ttu-id="f3c5c-124">按一下即可將 [索引鍵資料行]\*\*\*\* 中選取的資料行向下移動一個位置。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-124">Click to move the column selected in **Key Columns** down one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3c5c-125">只有當清單包含一個以上的資料行而且選取了資料行時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-125">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 **>**  
 <span data-ttu-id="f3c5c-126">按一下即可將新資料行加入 [索引鍵資料行]\*\*\*\* 中列出之資料行的結尾處。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-126">Click to add a new column to the end of the columns listed in **Key Columns**.</span></span>  
  
 **<**  
 <span data-ttu-id="f3c5c-127">按一下即可從 [索引鍵資料行]\*\*\*\* 中列出的資料行中移除選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="f3c5c-127">Click to remove the selected column from the columns listed in **Key Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c5c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3c5c-128">See Also</span></span>  
 [<span data-ttu-id="f3c5c-129">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f3c5c-129">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
