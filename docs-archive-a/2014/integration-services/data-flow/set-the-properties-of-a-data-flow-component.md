---
title: 設定資料流程元件的屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1fd045ba076eed2d65d801015b881a477976f5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599118"
---
# <a name="set-the-properties-of-a-data-flow-component"></a><span data-ttu-id="8a467-102">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="8a467-102">Set the Properties of a Data Flow Component</span></span>
  <span data-ttu-id="8a467-103">若要設定資料流程元件的屬性 (包括來源、目的地和轉換)，請使用下列其中一個功能：</span><span class="sxs-lookup"><span data-stu-id="8a467-103">To set the properties of data flow components, which include sources, destinations, and transformations, use one of the following features:</span></span>  
  
-   <span data-ttu-id="8a467-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的元件編輯器。</span><span class="sxs-lookup"><span data-stu-id="8a467-104">The component editors that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="8a467-105">這些編輯器僅包括每個資料流程元件的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="8a467-105">These editors include only the custom properties of each data flow component.</span></span>  
  
-   <span data-ttu-id="8a467-106">[屬性]  視窗會列出每個元素的元件層級自訂屬性，以及所有資料流程元素通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="8a467-106">The **Properties** window lists the component-level custom properties of each element, as well as the properties common to all data flow elements.</span></span>  
  
-   <span data-ttu-id="8a467-107">[進階編輯器]  對話方塊可讓您存取每一個元件的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="8a467-107">The **Advanced Editor** dialog box provides access to custom properties for each component.</span></span> <span data-ttu-id="8a467-108">[進階編輯器]  對話方塊也可讓您存取所有資料流程元件的屬性，也就是輸入、輸出、錯誤輸出、資料行和外部資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="8a467-108">The **Advanced Editor** dialog box also provides access to the properties common to all data flow components-the properties of inputs, outputs, error outputs, columns, and external columns.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a><span data-ttu-id="8a467-109">使用元件編輯器設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="8a467-109">To set the properties of a data flow component by using a component editor</span></span>  
  
1.  <span data-ttu-id="8a467-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8a467-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8a467-111">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8a467-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8a467-112">按一下 [控制流程]  索引標籤，然後按兩下包含資料流程 (具有您要檢視及修改其屬性之元件) 的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="8a467-112">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow with the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="8a467-113">按兩下資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="8a467-113">Double-click the data flow component.</span></span>  
  
5.  <span data-ttu-id="8a467-114">在元件編輯器中，檢視或修改屬性值，然後關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="8a467-114">In the component editor, view or modify the property values, and then close the editor.</span></span>  
  
6.  <span data-ttu-id="8a467-115">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-115">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a><span data-ttu-id="8a467-116">使用屬性視窗設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="8a467-116">To set the properties of a data flow component by using the Properties window</span></span>  
  
1.  <span data-ttu-id="8a467-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8a467-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8a467-118">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8a467-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8a467-119">按一下 [控制流程]  索引標籤，然後按兩下包含您要檢視及修改其屬性之元件的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="8a467-119">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="8a467-120">以滑鼠右鍵按一下資料流程元件，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-120">Right-click the data flow component, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="8a467-121">檢視或修改屬性值，然後關閉 [屬性]  視窗。</span><span class="sxs-lookup"><span data-stu-id="8a467-121">View or modify the property values, and then close the **Properties** window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a467-122">許多屬性都是唯讀的，因此無法修改。</span><span class="sxs-lookup"><span data-stu-id="8a467-122">Many properties are read-only, and cannot be modified.</span></span>  
  
6.  <span data-ttu-id="8a467-123">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-123">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a><span data-ttu-id="8a467-124">使用進階編輯器設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="8a467-124">To set the properties of a data flow component by using the Advanced Editor</span></span>  
  
1.  <span data-ttu-id="8a467-125">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8a467-125">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8a467-126">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8a467-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8a467-127">按一下 [控制流程]  索引標籤，然後按兩下包含您要檢視或修改之元件的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="8a467-127">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component you want to view or modify.</span></span>  
  
4.  <span data-ttu-id="8a467-128">在資料流程設計師中，以滑鼠右鍵按一下資料流程元件，然後按一下 [顯示進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-128">In the data flow designer, right-click the data flow component, and then click **Show Advanced Editor**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a467-129">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，支援多個輸入的資料流程元件無法使用 [進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data flow components that support multiple inputs cannot use the **Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="8a467-130">在 [進階編輯器]  對話方塊中，執行下列任何一個步驟：</span><span class="sxs-lookup"><span data-stu-id="8a467-130">In the **Advanced Editor** dialog box, do any of the following steps:</span></span>  
  
    -   <span data-ttu-id="8a467-131">若要檢視及指定此元件所使用的連接，請按一下 [連線管理員]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a467-131">To view and specify the connection that the component uses, click the **Connection Managers** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8a467-132">[連線管理員]  索引標籤只可用於使用連線管理員連接到資料來源 (例如檔案和資料庫) 的資料流程元件</span><span class="sxs-lookup"><span data-stu-id="8a467-132">The **Connection Managers** tab is available only to data flow components that use connection managers to connect to data sources such as files and databases</span></span>  
  
    -   <span data-ttu-id="8a467-133">若要檢視和修改元件層級屬性，請按一下 [元件屬性]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a467-133">To view and modify component-level properties, click the **Component Properties** tab.</span></span>  
  
    -   <span data-ttu-id="8a467-134">若要檢視和修改外部資料行與可用輸出之間的對應，請按一下 [資料行對應]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a467-134">To view and modify mappings between external columns and the available output, click the **Column Mappings** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8a467-135">[資料行對應]  索引標籤只能在檢視或編輯來源或目的地時使用。</span><span class="sxs-lookup"><span data-stu-id="8a467-135">The **Column Mappings** tab is available only when viewing or editing sources or destinations.</span></span>  
  
    -   <span data-ttu-id="8a467-136">若要檢視可用輸入資料行的清單並更新輸出資料行的名稱，請按一下 [輸入資料行]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a467-136">To view a list of the available input columns and to update the names of output columns, click the **Input Columns** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8a467-137">[輸入資料行] 索引標籤僅在使用轉換或目的地時可用。</span><span class="sxs-lookup"><span data-stu-id="8a467-137">The Input Columns tab is available only when working with transformations or destinations.</span></span> <span data-ttu-id="8a467-138">如需詳細資訊，請參閱 [Integration Services 轉換](transformations/integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="8a467-138">For more information, see [Integration Services Transformations](transformations/integration-services-transformations.md).</span></span>  
  
    -   <span data-ttu-id="8a467-139">若要檢視和修改輸入、輸出及錯誤輸出的屬性，以及檢視和修改其包含之資料行的屬性，請按一下 [輸入與輸出屬性]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8a467-139">To view and modify the properties of inputs, outputs, and error outputs, and the properties of the columns they contain, click the **Input and Output Properties** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8a467-140">來源沒有輸入。</span><span class="sxs-lookup"><span data-stu-id="8a467-140">Sources have no inputs.</span></span> <span data-ttu-id="8a467-141">除了選擇性的錯誤輸出之外，目的地沒有輸出。</span><span class="sxs-lookup"><span data-stu-id="8a467-141">Destinations have no outputs, except for an optional error output.</span></span>  
  
6.  <span data-ttu-id="8a467-142">檢視或修改屬性值。</span><span class="sxs-lookup"><span data-stu-id="8a467-142">View or modify the property values.</span></span>  
  
7.  <span data-ttu-id="8a467-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-143">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="8a467-144">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="8a467-144">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a467-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a467-145">See Also</span></span>  
 [<span data-ttu-id="8a467-146">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="8a467-146">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
