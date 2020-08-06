---
title: 使用合併聯結轉換來擴充資料集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a387c4ad840eb739d36023be9323c063dcb9a68e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592781"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a><span data-ttu-id="a35e8-102">使用合併聯結轉換來擴充資料集</span><span class="sxs-lookup"><span data-stu-id="a35e8-102">Extend a Dataset by Using the Merge Join Transformation</span></span>
  <span data-ttu-id="a35e8-103">若要加入和設定「合併聯結」轉換，封裝必須已包含至少一個「資料流程」工作，及兩個為「合併聯結」轉換提供輸入的資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="a35e8-103">To add and configure a Merge Join transformation, the package must already include at least one Data Flow task and two data flow components that provide inputs to the Merge Join transformation.</span></span>  
  
 <span data-ttu-id="a35e8-104">「合併聯結」轉換需要兩個經過排序的輸入。</span><span class="sxs-lookup"><span data-stu-id="a35e8-104">The Merge Join transformation requires two sorted inputs.</span></span> <span data-ttu-id="a35e8-105">如需詳細資訊，請參閱 [排序合併和合併聯結轉換的資料](sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="a35e8-105">For more information, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
### <a name="to-extend-a-dataset"></a><span data-ttu-id="a35e8-106">擴充資料集</span><span class="sxs-lookup"><span data-stu-id="a35e8-106">To extend a dataset</span></span>  
  
1.  <span data-ttu-id="a35e8-107">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a35e8-107">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a35e8-108">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="a35e8-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a35e8-109">按一下 [資料流程]  索引標籤，然後將「合併聯結」轉換從 [工具箱]  拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a35e8-109">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Merge Join transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="a35e8-110">將連接子從資料來源或前一個轉換拖曳至「合併聯結」轉換，以便將「合併聯結」轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="a35e8-110">Connect the Merge Join transformation to the data flow by dragging the connector from a data source or a previous transformation to the Merge Join transformation.</span></span>  
  
5.  <span data-ttu-id="a35e8-111">按兩下「合併聯結」轉換。</span><span class="sxs-lookup"><span data-stu-id="a35e8-111">Double-click the Merge Join transformation.</span></span>  
  
6.  <span data-ttu-id="a35e8-112">在 [合併聯結轉換編輯器]  對話方塊中，選取 [聯結類型]  清單中使用的聯結類型。</span><span class="sxs-lookup"><span data-stu-id="a35e8-112">In the **Merge Join Transformation Editor** dialog box, select the type of join to use in the **Join type** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a35e8-113">如果您選取 [左方外部聯結]  類型，則可以按一下 [交換輸入]  來切換輸入，並將左方外部聯結轉換成右方外部聯結。</span><span class="sxs-lookup"><span data-stu-id="a35e8-113">If you select the **Left outer join** type, you can click **Swap Inputs** to switch the inputs and convert the left outer join to a right outer join.</span></span>  
  
7.  <span data-ttu-id="a35e8-114">將左輸入中的資料行拖曳至右輸入中的資料行，以指定聯結資料行。</span><span class="sxs-lookup"><span data-stu-id="a35e8-114">Drag columns in the left input to columns in the right input to specify the join columns.</span></span> <span data-ttu-id="a35e8-115">如果這些資料行的名稱相同，則可以選取 [聯結索引鍵]  核取方塊，「合併聯結」轉換會自動建立聯結。</span><span class="sxs-lookup"><span data-stu-id="a35e8-115">If the columns have the same name, you can select the **Join Key** check box and the Merge Join transformation automatically creates the join.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a35e8-116">您可以只在排序位置相同的資料行之間建立聯結，而這些聯結必須以排序位置指定的順序建立。</span><span class="sxs-lookup"><span data-stu-id="a35e8-116">You can create joins only between columns that have the same sort position, and the joins must be created in the order specified by the sort position.</span></span> <span data-ttu-id="a35e8-117">如果您嘗試不按順序建立聯結，則 [合併聯結轉換編輯器]  會提示您為略過的排序次序位置建立其他聯結。</span><span class="sxs-lookup"><span data-stu-id="a35e8-117">If you attempt to create the joins out of order, the **Merge Join Transformation Editor** prompts you to create additional joins for the skipped sort order positions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a35e8-118">依預設，輸出會在聯結資料行上進行排序。</span><span class="sxs-lookup"><span data-stu-id="a35e8-118">By default, the output is sorted on the join columns.</span></span>  
  
8.  <span data-ttu-id="a35e8-119">在左右輸入中，選取其他資料行的核取方塊，使之包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="a35e8-119">In the left and right inputs, select the check boxes of additional columns to include in the output.</span></span> <span data-ttu-id="a35e8-120">依預設，會包含聯結資料行。</span><span class="sxs-lookup"><span data-stu-id="a35e8-120">Join columns are included by default.</span></span>  
  
9. <span data-ttu-id="a35e8-121">(選擇性) 在 [輸出別名]  資料行中更新輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="a35e8-121">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="a35e8-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a35e8-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="a35e8-123">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="a35e8-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35e8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a35e8-124">See Also</span></span>  
 <span data-ttu-id="a35e8-125">[合併聯結轉換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a35e8-125">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="a35e8-126">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a35e8-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a35e8-127">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a35e8-127">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a35e8-128">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="a35e8-128">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
