---
title: 物件系結對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
ms.openlocfilehash: a10c91e0222b826066aeede96aa665cc22540637
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597391"
---
# <a name="object-binding-dialog-box"></a><span data-ttu-id="9f89a-102">物件繫結對話方塊</span><span class="sxs-lookup"><span data-stu-id="9f89a-102">Object Binding Dialog Box</span></span>
  <span data-ttu-id="9f89a-103">使用 **中的** [物件繫結] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件屬性與資料來源檢視中之資料表或資料行之間的繫結。</span><span class="sxs-lookup"><span data-stu-id="9f89a-103">Use the **Object Binding** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define bindings between the property of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object and a table or column in a data source view.</span></span> <span data-ttu-id="9f89a-104">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [屬性]\*\*\*\* 視窗中，從下列 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件屬性值的下拉式清單中選取 [(新增)]\*\*\*\*，即可顯示 [物件繫結]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="9f89a-104">You can display the **Object Binding** dialog box by selecting **(new)** from the drop-down list for the value of the following properties of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   <span data-ttu-id="9f89a-105">NameColumn</span><span class="sxs-lookup"><span data-stu-id="9f89a-105">NameColumn</span></span>  
  
-   <span data-ttu-id="9f89a-106">ValueColumn</span><span class="sxs-lookup"><span data-stu-id="9f89a-106">ValueColumn</span></span>  
  
-   <span data-ttu-id="9f89a-107">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="9f89a-107">CustomRollupColumn</span></span>  
  
-   <span data-ttu-id="9f89a-108">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="9f89a-108">CustomRollupPropertiesColumn</span></span>  
  
-   <span data-ttu-id="9f89a-109">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="9f89a-109">UnaryOperatorColumn</span></span>  
  
## <a name="options"></a><span data-ttu-id="9f89a-110">選項</span><span class="sxs-lookup"><span data-stu-id="9f89a-110">Options</span></span>  
 <span data-ttu-id="9f89a-111">**系結類型**</span><span class="sxs-lookup"><span data-stu-id="9f89a-111">**Binding type**</span></span>  
 <span data-ttu-id="9f89a-112">選取要用於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的繫結。</span><span class="sxs-lookup"><span data-stu-id="9f89a-112">Select the binding to use for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="9f89a-113">可以使用下列類型的繫結：</span><span class="sxs-lookup"><span data-stu-id="9f89a-113">The following types of binding can be used:</span></span>  
  
 <span data-ttu-id="9f89a-114">資料行繫結</span><span class="sxs-lookup"><span data-stu-id="9f89a-114">Column binding</span></span>  
 <span data-ttu-id="9f89a-115">將物件繫結到資料來源檢視中的現有資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="9f89a-115">Binds the object to an existing table and column within a data source view.</span></span>  
  
 <span data-ttu-id="9f89a-116">產生資料行</span><span class="sxs-lookup"><span data-stu-id="9f89a-116">Generate column</span></span>  
 <span data-ttu-id="9f89a-117">指出要在資料來源檢視中定義新的資料行，然後建立資料行繫結與該資料行的關聯。</span><span class="sxs-lookup"><span data-stu-id="9f89a-117">Indicates that a new column is to be defined in the data source view, and a column binding is then associated with it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f89a-118">如果選取此選項，您就必須在部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件之前，先執行 [結構描述產生精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9f89a-118">If this option is selected, you must run the **Schema Generation Wizard** before deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="9f89a-119">資料列繫結</span><span class="sxs-lookup"><span data-stu-id="9f89a-119">Row binding</span></span>  
 <span data-ttu-id="9f89a-120">將物件繫結到事實資料表中的資料列，並可根據事實資料表中處理的資料列數提供計數量值。</span><span class="sxs-lookup"><span data-stu-id="9f89a-120">Binds the object to a row in a fact table and is used to facilitate count measures based on the number of rows processed in the fact table.</span></span>  
  
 <span data-ttu-id="9f89a-121">**來源資料表**</span><span class="sxs-lookup"><span data-stu-id="9f89a-121">**Source table**</span></span>  
 <span data-ttu-id="9f89a-122">顯示與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件相關聯之資料來源檢視中的資料表清單。</span><span class="sxs-lookup"><span data-stu-id="9f89a-122">Displays a list of tables in the data source view associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="9f89a-123">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="9f89a-123">**Source column**</span></span>  
 <span data-ttu-id="9f89a-124">顯示 [來源資料表]\*\*\*\* 中選取之資料表內的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="9f89a-124">Displays a list of columns in the table selected in **Source table**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f89a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f89a-125">See Also</span></span>  
 [<span data-ttu-id="9f89a-126">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="9f89a-126">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
