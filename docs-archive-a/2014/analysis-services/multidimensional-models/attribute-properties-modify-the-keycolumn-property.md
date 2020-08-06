---
title: 修改屬性（Attribute）的 KeyColumn 屬性（Property） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3367a7aec84ba59efd118a56745bb76fc5266061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708793"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a><span data-ttu-id="02afe-102">修改屬性 (attribute) 的 KeyColumn 屬性 (property)</span><span class="sxs-lookup"><span data-stu-id="02afe-102">Modify the KeyColumn Property of an Attribute</span></span>
  <span data-ttu-id="02afe-103">您可以修改屬性 (Attribute) 的 **KeyColumns** 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="02afe-103">You can modify the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="02afe-104">例如，您可能要為屬性指定複合索引鍵，而不是單一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="02afe-104">For example, you might want to specify a composite key instead of a single key as the key for the attribute.</span></span>  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a><span data-ttu-id="02afe-105">修改屬性 (Attribute) 的 KeyColumns 屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="02afe-105">To modify the KeyColumns property of an attribute</span></span>  
  
1.  <span data-ttu-id="02afe-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟您要在其中修改 **KeyColumns** 屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="02afe-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project in which you want to modify the **KeyColumns** property.</span></span>  
  
2.  <span data-ttu-id="02afe-107">執行下列其中一個程序，開啟 [維度設計師]：</span><span class="sxs-lookup"><span data-stu-id="02afe-107">Open Dimension Designer by doing one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="02afe-108">在**方案總管**中，以滑鼠右鍵按一下 [維度]\*\*\*\* 資料夾中的維度，然後按一下 [開啟]\*\*\*\* 或 [檢視表設計工具]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02afe-108">In **Solution Explorer**, right-click the dimension in the **Dimensions** folder, and then either click **Open** or **View Designer**.</span></span>  
  
         <span data-ttu-id="02afe-109">-或-</span><span class="sxs-lookup"><span data-stu-id="02afe-109">-or-</span></span>  
  
    -   <span data-ttu-id="02afe-110">在 [Cube 設計師] 的 [ **Cube 結構**] 索引標籤上，展開 [**維度**] 窗格中的 Cube 維度，然後按一下 [\*\*編輯 \<dimension> \*\*]。</span><span class="sxs-lookup"><span data-stu-id="02afe-110">In Cube Designer, on the **Cube Structure** tab, expand the cube dimension in the **Dimensions** pane and click **Edit \<dimension>**.</span></span>  
  
3.  <span data-ttu-id="02afe-111">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格中，按一下要修改其 **KeyColumns** 屬性 (Property) 的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="02afe-111">On the **Dimension Structure** tab, in the **Attributes** pane, click the attribute whose **KeyColumns** property you want to modify.</span></span>  
  
4.  <span data-ttu-id="02afe-112">在 [屬性]\*\*\*\* 視窗中，按一下 **KeyColumns** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="02afe-112">In the **Properties** window, click the value for the **KeyColumns** property.</span></span>  
  
5.  <span data-ttu-id="02afe-113">按一下屬性方塊之值資料格中的瀏覽按鈕 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="02afe-113">Click the browse **(...)** button that appears in the value cell of the property box.</span></span>  
  
     <span data-ttu-id="02afe-114">[索引鍵資料行]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="02afe-114">The **Key Columns** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="02afe-115">若要從 [索引鍵資料行]\*\*\*\* 清單中移除現有的索引鍵資料行，請選取資料行，然後按一下 [\<]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="02afe-115">To remove an existing key column, in the **Key Columns** list, select the column, and then click the **\<** button.</span></span>  
  
7.  <span data-ttu-id="02afe-116">若要在 [可用的資料行]\*\*\*\* 清單中加入索引鍵資料行，請選取資料行，然後按一下 [>]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="02afe-116">To add a key column, in the **Available Columns** list, select the column, and then click the **>** button.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="02afe-117">如果您要定義數個索引鍵資料行，這些資料行出現在 [索引鍵資料行]\*\*\*\* 清單中的順序會影響顯示順序。</span><span class="sxs-lookup"><span data-stu-id="02afe-117">If you define multiple key columns, the order in which those columns appear in the **Key Columns** list affects the display order.</span></span> <span data-ttu-id="02afe-118">例如，月份屬性有兩個索引鍵資料行：月和年。</span><span class="sxs-lookup"><span data-stu-id="02afe-118">For example, a month attribute has two key columns: month and year.</span></span> <span data-ttu-id="02afe-119">如果年份資料行出現在月份資料行前的清單中， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將會先依照年份排序，然後再依照月份排序。</span><span class="sxs-lookup"><span data-stu-id="02afe-119">If the year column appears in the list before the month column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by year and then by month.</span></span> <span data-ttu-id="02afe-120">如果月份資料行出現在年份資料行前， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將會先依照月份排序，然後再依照年份排序。</span><span class="sxs-lookup"><span data-stu-id="02afe-120">If the month column appears before the year column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by month and then by year.</span></span>  
  
8.  <span data-ttu-id="02afe-121">若要變更索引鍵資料行的順序，請選取資料行，然後按一下 [向上]\*\*\*\* 或 [向下]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="02afe-121">To change the order of key columns, select a column, and then click the **Up** or **Down** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02afe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02afe-122">See Also</span></span>  
 [<span data-ttu-id="02afe-123">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="02afe-123">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
