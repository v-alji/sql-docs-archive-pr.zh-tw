---
title: 設定工作或容器的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], properties
ms.assetid: 52d47ca4-fb8c-493d-8b2b-48bb269f859b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0a4c556b94af02c2f874f2740a70b1294c35e653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709733"
---
# <a name="set-the-properties-of-a-task-or-container"></a><span data-ttu-id="678f8-102">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="678f8-102">Set the Properties of a Task or Container</span></span>
  <span data-ttu-id="678f8-103">您可以使用 [屬性]\*\*\*\* 視窗來設定工作和容器的大部分屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-103">You can set most properties of tasks and containers by using the **Properties** window.</span></span> <span data-ttu-id="678f8-104">例外的是工作集合的屬性，以及因太複雜而無法使用 [屬性]\*\*\*\* 視窗設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-104">The exceptions are properties of task collections and properties that are too complex to set by using the **Properties** window.</span></span> <span data-ttu-id="678f8-105">例如，您無法在 [屬性]\*\*\*\* 視窗中設定「Foreach 迴圈」容器所使用的列舉值。</span><span class="sxs-lookup"><span data-stu-id="678f8-105">For example, you cannot configure the enumerator that the Foreach Loop container uses in the **Properties** window.</span></span> <span data-ttu-id="678f8-106">您必須使用工作或容器編輯器來設定這些複雜屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-106">You must use a task or container editor to set these complex properties.</span></span> <span data-ttu-id="678f8-107">大部分工作和容器編輯器都具有多個節點，而且每個節點都包含相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-107">Most task and container editors have multiple nodes and each node contains related properties.</span></span> <span data-ttu-id="678f8-108">節點的名稱表示此節點所包含之屬性的主旨。</span><span class="sxs-lookup"><span data-stu-id="678f8-108">The name of the node indicates the subject of the properties that the node contains.</span></span>  
  
 <span data-ttu-id="678f8-109">下列程序將描述如何使用 [屬性]\*\*\*\* 視窗或對應的工作或容器編輯器來設定工作或容器的屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-109">The following procedures describe how to set the properties of a task or container by using either the **Properties** windows, or the corresponding task or container editor.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-the-properties-window"></a><span data-ttu-id="678f8-110">使用屬性視窗來設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="678f8-110">To set the properties of a task or container by using the Properties window</span></span>  
  
1.  <span data-ttu-id="678f8-111">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="678f8-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="678f8-112">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="678f8-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="678f8-113">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="678f8-113">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="678f8-114">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，以滑鼠右鍵按一下工作或容器，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="678f8-114">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="678f8-115">在 [屬性]\*\*\*\* 視窗中更新屬性值。</span><span class="sxs-lookup"><span data-stu-id="678f8-115">In the **Properties** window, update the property value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="678f8-116">大部分的屬性都可以經由直接在文字方塊中輸入某個值，或從清單中選取某個值予以設定。</span><span class="sxs-lookup"><span data-stu-id="678f8-116">Most properties can be set by typing a value directly in the text box, or by selecting a value from a list.</span></span> <span data-ttu-id="678f8-117">不過，有些屬性比較複雜，並具有自訂屬性編輯器。</span><span class="sxs-lookup"><span data-stu-id="678f8-117">However, some properties are more complex and have a custom property editor.</span></span> <span data-ttu-id="678f8-118">若要設定這種屬性，請按一下文字方塊，然後按一下建立 ([...])\*\*\*\* 按鈕開啟自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="678f8-118">To set the property, click in the text box, and then click the build **(...)** button to open the custom editor.</span></span>  
  
6.  <span data-ttu-id="678f8-119">(選擇性) 建立屬性運算式，以動態方式更新工作或容器的屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-119">Optionally, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="678f8-120">如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="678f8-120">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="678f8-121">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="678f8-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-a-task-or-container-editor"></a><span data-ttu-id="678f8-122">使用工作或容器編輯器來設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="678f8-122">To set the properties of a task or container by using a task or container editor</span></span>  
  
1.  <span data-ttu-id="678f8-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="678f8-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="678f8-124">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="678f8-124">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="678f8-125">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="678f8-125">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="678f8-126">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，以滑鼠右鍵按一下工作或容器，然後按一下 [編輯]\*\*\*\* 開啟對應的工作或容器編輯器。</span><span class="sxs-lookup"><span data-stu-id="678f8-126">On the design surface of the **Control Flow** tab, right-click the task or container, and then click **Edit** to open the corresponding task or container editor.</span></span>  
  
     <span data-ttu-id="678f8-127">如需如何設定「For 迴圈」容器的資訊，請參閱[設定 For 迴圈容器](control-flow/for-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="678f8-127">For information about how to configure the For Loop container, see [Configure a For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
     <span data-ttu-id="678f8-128">如需如何設定Foreach 迴圈容器的資訊，請參閱 [設定 Foreach 迴圈容器](control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="678f8-128">For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="678f8-129">「時序」容器沒有任何自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="678f8-129">The Sequence container has no custom editor.</span></span>  
  
5.  <span data-ttu-id="678f8-130">如果工作或容器編輯器具有多個節點，請按一下包含您要設定之屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="678f8-130">If the task or container editor has multiple nodes, click the node that contains the property that you want to set.</span></span>  
  
6.  <span data-ttu-id="678f8-131">(選擇性) 按一下 [運算式]\*\*\*\*，然後在 [運算式]\*\*\*\* 頁面上建立屬性運算式，以動態方式更新工作或容器的屬性。</span><span class="sxs-lookup"><span data-stu-id="678f8-131">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions to dynamically update the properties of the task or container.</span></span> <span data-ttu-id="678f8-132">如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="678f8-132">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="678f8-133">更新屬性值。</span><span class="sxs-lookup"><span data-stu-id="678f8-133">Update the property value.</span></span>  
  
8.  <span data-ttu-id="678f8-134">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="678f8-134">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678f8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="678f8-135">See Also</span></span>  
 <span data-ttu-id="678f8-136">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="678f8-136">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="678f8-137">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="678f8-137">Integration Services Containers</span></span>](control-flow/integration-services-containers.md)  
  
  
