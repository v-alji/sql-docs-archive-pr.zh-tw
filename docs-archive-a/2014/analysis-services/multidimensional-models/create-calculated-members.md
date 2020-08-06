---
title: 建立匯出成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated members [Analysis Services]
- custom measures [Analysis Services]
- members [Analysis Services], calculated
- calculations [Analysis Services], calculated members
ms.assetid: 820e4b18-9c3a-4b12-a126-ca16d8364a00
author: minewiskan
ms.author: owend
ms.openlocfilehash: c45ef3cf720e6a3cc43156b032d91d205d6334bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585642"
---
# <a name="create-calculated-members"></a><span data-ttu-id="caff6-102">建立導出成員</span><span class="sxs-lookup"><span data-stu-id="caff6-102">Create Calculated Members</span></span>
  <span data-ttu-id="caff6-103">您可以結合 Cube 資料、算術運算子、數字和函數，來建立自訂的量值或維度成員，稱為導出成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-103">You can create customized measures or dimension members, called calculated members, by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="caff6-104">例如，您可以建立一個名為 Euros 的導出成員，藉由將現有的美金量值乘以轉換比率，來將美金轉換為歐元。</span><span class="sxs-lookup"><span data-stu-id="caff6-104">For example, you can create a calculated member named Euros that converts dollars to euros by multiplying an existing dollar measure by a conversion rate.</span></span> <span data-ttu-id="caff6-105">然後可以在另一個資料列或資料行中，向一般使用者顯示歐元。</span><span class="sxs-lookup"><span data-stu-id="caff6-105">Euros can then be displayed to end users in a separate row or column.</span></span>  
  
 <span data-ttu-id="caff6-106">導出成員定義將會被儲存，但是它們的值只存在於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="caff6-106">Calculated member definitions are stored, but their values exist only in memory.</span></span> <span data-ttu-id="caff6-107">在前述的範例中，會對一般使用者顯示歐元值但不會儲存為 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="caff6-107">In the preceding example, values in marks are displayed to end users but are not stored as cube data.</span></span>  
  
 <span data-ttu-id="caff6-108">您在 Cube 中建立導出成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-108">You create calculated members in cubes.</span></span> <span data-ttu-id="caff6-109">若要建立導出成員，請在 Cube 設計師的 [計算]\*\*\*\* 索引標籤上，按一下工具列上的 [新增導出成員]\*\*\*\* 圖示。</span><span class="sxs-lookup"><span data-stu-id="caff6-109">To create a calculated member, in Cube Designer, on the **Calculations** tab, click the **New Calculated Member** icon on the toolbar.</span></span> <span data-ttu-id="caff6-110">此命令會顯示一個表單，以指定導出成員的下列選項：</span><span class="sxs-lookup"><span data-stu-id="caff6-110">This command displays a form to specify the following options for the calculated member:</span></span>  
  
 <span data-ttu-id="caff6-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="caff6-111">**Name**</span></span>  
 <span data-ttu-id="caff6-112">選取導出成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="caff6-112">Select the name of the calculated member.</span></span> <span data-ttu-id="caff6-113">當一般使用者瀏覽 Cube 時，此名稱會顯示為導出成員值的資料行或資料列標題。</span><span class="sxs-lookup"><span data-stu-id="caff6-113">This name appears as the column or row heading for the calculated member values when end users browse the cube.</span></span>  
  
 <span data-ttu-id="caff6-114">**父階層**</span><span class="sxs-lookup"><span data-stu-id="caff6-114">**Parent hierarchy**</span></span>  
 <span data-ttu-id="caff6-115">選取要包含在導出成員中的父階層。</span><span class="sxs-lookup"><span data-stu-id="caff6-115">Select the parent hierarchy to include in the calculated member.</span></span> <span data-ttu-id="caff6-116">階層是維度的描述性類別目錄，利用階層即可將 Cube 中的數值資料 (亦即，量值) 分開以便分析。</span><span class="sxs-lookup"><span data-stu-id="caff6-116">Hierarchies are descriptive categories of a dimension by which the numeric data (that is, measures) in a cube can be separated for analysis.</span></span> <span data-ttu-id="caff6-117">在表格式瀏覽器中，階層會提供資料行和資料列標題，一般使用者瀏覽 Cube 中的資料時，會向一般使用者顯示這些標題。</span><span class="sxs-lookup"><span data-stu-id="caff6-117">In tabular browsers, hierarchies provide the column and row headings displayed to end users when they browse data in a cube.</span></span> <span data-ttu-id="caff6-118">(在圖形化瀏覽器中，階層會提供其他類型的描述性標籤，不過功能和表格式瀏覽器中相同。)導出成員在您所選取的父維度中提供新的標題 (或標籤)。</span><span class="sxs-lookup"><span data-stu-id="caff6-118">(In graphical browsers, they provide other types of descriptive labels, but they have the same function as in tabular browsers.) A calculated member provides a new heading (or label) in the parent dimension you select.</span></span>  
  
 <span data-ttu-id="caff6-119">或者，您可以在量值中 (而非維度中) 包含導出成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-119">Alternatively, you can include the calculated member in the measures instead of in a dimension.</span></span> <span data-ttu-id="caff6-120">此選項也會提供新資料行或資料列標題，但它會附加至瀏覽器中的量值。</span><span class="sxs-lookup"><span data-stu-id="caff6-120">This option also provides a new column or row heading, but it is attached to measures in the browser.</span></span>  
  
 <span data-ttu-id="caff6-121">**父成員**</span><span class="sxs-lookup"><span data-stu-id="caff6-121">**Parent member**</span></span>  
 <span data-ttu-id="caff6-122">按一下 [變更]\*\*\*\*，即可選取要包含導出成員的父成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-122">Click **Change** to select a parent member to include the calculated member.</span></span> <span data-ttu-id="caff6-123">如果您選取單層階層或 MEASURES 做為父維度，則無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="caff6-123">This option is unavailable if you select a one-level hierarchy or MEASURES as the parent dimension.</span></span>  
  
 <span data-ttu-id="caff6-124">階層劃分為包含成員的層級。</span><span class="sxs-lookup"><span data-stu-id="caff6-124">Hierarchies are divided into levels that contain members.</span></span> <span data-ttu-id="caff6-125">每一個成員產生一個標題。</span><span class="sxs-lookup"><span data-stu-id="caff6-125">Each member produces a heading.</span></span> <span data-ttu-id="caff6-126">瀏覽 Cube 中的資料時，一般使用者可以從選取的標題，向下鑽研至先前未顯示的從屬標題。</span><span class="sxs-lookup"><span data-stu-id="caff6-126">While browsing data in a cube, end users can drill down from a selected heading to previously undisplayed subordinate headings.</span></span> <span data-ttu-id="caff6-127">導出成員的標題會直接加入在您所選取的父成員之下的層級。</span><span class="sxs-lookup"><span data-stu-id="caff6-127">The heading for the calculated member is added at the level directly below the parent member you select.</span></span>  
  
 <span data-ttu-id="caff6-128">**運算式**</span><span class="sxs-lookup"><span data-stu-id="caff6-128">**Expression**</span></span>  
 <span data-ttu-id="caff6-129">指定產生導出成員之值的運算式。</span><span class="sxs-lookup"><span data-stu-id="caff6-129">Specify the expression that produces the values of the calculated member.</span></span> <span data-ttu-id="caff6-130">此運算式可以使用多維度運算式 (MDX) 撰寫。</span><span class="sxs-lookup"><span data-stu-id="caff6-130">This expression can be written in Multidimensional Expressions (MDX).</span></span> <span data-ttu-id="caff6-131">運算式可以包含下列任一項：</span><span class="sxs-lookup"><span data-stu-id="caff6-131">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="caff6-132">顯示 Cube 元件的資料運算式，例如維度、層級、量值等等</span><span class="sxs-lookup"><span data-stu-id="caff6-132">Data expressions that represent cube components such as dimensions, levels, measures, and so on</span></span>  
  
-   <span data-ttu-id="caff6-133">算術運算子</span><span class="sxs-lookup"><span data-stu-id="caff6-133">Arithmetic operators</span></span>  
  
-   <span data-ttu-id="caff6-134">數字</span><span class="sxs-lookup"><span data-stu-id="caff6-134">Numbers</span></span>  
  
-   <span data-ttu-id="caff6-135">函數</span><span class="sxs-lookup"><span data-stu-id="caff6-135">Functions</span></span>  
  
 <span data-ttu-id="caff6-136">您可以從 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤中，拖曳或複製 Cube 元件，以快速將這些元件加入至運算式。</span><span class="sxs-lookup"><span data-stu-id="caff6-136">You can drag or copy cube components from the **Metadata** tab of the **Calculation Tools** pane to quickly add them to an expression.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="caff6-137">導出成員若要用於另一個導出成員的值運算式中，就必須在使用該成員的導出成員之前建立。</span><span class="sxs-lookup"><span data-stu-id="caff6-137">Any calculated member that is to be used in the value expression of another calculated member must be created before the calculated member that uses it.</span></span>  
  
 <span data-ttu-id="caff6-138">格式字串</span><span class="sxs-lookup"><span data-stu-id="caff6-138">Format String</span></span>  
 <span data-ttu-id="caff6-139">指定根據導出成員之資料格值的格式。</span><span class="sxs-lookup"><span data-stu-id="caff6-139">Specifies the format of cell values that are based on the calculated member.</span></span> <span data-ttu-id="caff6-140">此屬性接受的值與量值的 `Display Format` 屬性相同。</span><span class="sxs-lookup"><span data-stu-id="caff6-140">This property accepts the same values as the `Display Format` property for measures.</span></span> <span data-ttu-id="caff6-141">如需有關顯示格式的詳細資訊，請參閱 [設定量值屬性](configure-measure-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="caff6-141">For more information about display formats, see [Configure Measure Properties](configure-measure-properties.md).</span></span>  
  
 <span data-ttu-id="caff6-142">可見</span><span class="sxs-lookup"><span data-stu-id="caff6-142">Visible</span></span>  
 <span data-ttu-id="caff6-143">決定擷取 Cube 中繼資料時是要看到或隱藏導出成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-143">Determines whether the calculated member is visible or hidden when cube metadata is retrieved.</span></span> <span data-ttu-id="caff6-144">如果隱藏導出成員，則仍可將它用於 MDX 運算式、陳述式和指令碼，但是它在用戶端使用者介面中並不會顯示為可選取的物件。</span><span class="sxs-lookup"><span data-stu-id="caff6-144">If the calculated member is hidden, it can still be used in MDX expressions, statements, and scripts, but it is not displayed as a selectable object in client user interfaces.</span></span>  
  
 <span data-ttu-id="caff6-145">非空白行為</span><span class="sxs-lookup"><span data-stu-id="caff6-145">Non-empty Behavior</span></span>  
 <span data-ttu-id="caff6-146">儲存量值的名稱，用來在 MDX 中解析 NON EMPTY 查詢。</span><span class="sxs-lookup"><span data-stu-id="caff6-146">Stores the names of measures used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="caff6-147">如果這個屬性空白，則必須重複評估導出成員來決定成員是否為空白。</span><span class="sxs-lookup"><span data-stu-id="caff6-147">If this property is blank, the calculated member must be evaluated repeatedly to determine whether a member is empty.</span></span> <span data-ttu-id="caff6-148">如果這個屬性包含一或多個量值的名稱，則在所有指定的量值都為空白時，會將導出成員視為空白。</span><span class="sxs-lookup"><span data-stu-id="caff6-148">If this property contains the name of one or more measures, the calculated member is treated as empty if all the specified measures are empty.</span></span> <span data-ttu-id="caff6-149">這個屬性是最佳化提示，要 Analysis Services 只傳回非 NULL 的記錄。</span><span class="sxs-lookup"><span data-stu-id="caff6-149">This property is an optimization hint to Analysis Services to return only non-NULL records.</span></span> <span data-ttu-id="caff6-150">如果只傳回非 NULL 記錄，將會改善利用 NON EMPTY 運算子或 NonEmpty 函數或是必須計算資料格值之 MDX 查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="caff6-150">Returning only non-NULL records improves the performance of MDX queries that utilize the NON EMPTY operator or the NonEmpty function, or that require the calculation of cell values.</span></span> <span data-ttu-id="caff6-151">為了在計算資料格時獲得最佳效能，請盡可能只指定單一成員。</span><span class="sxs-lookup"><span data-stu-id="caff6-151">For best performance with cell calculations, specify only a single member when possible.</span></span>  
  
 <span data-ttu-id="caff6-152">色彩運算式</span><span class="sxs-lookup"><span data-stu-id="caff6-152">Color Expressions</span></span>  
 <span data-ttu-id="caff6-153">指定 MDX 運算式，以根據導出成員的值來動態設定資料格的前景和背景顏色。</span><span class="sxs-lookup"><span data-stu-id="caff6-153">Specifies MDX expressions that dynamically set the foreground and background colors of cells based on the value of the calculated member.</span></span> <span data-ttu-id="caff6-154">如果用戶端應用程式不支援，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="caff6-154">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="caff6-155">字型運算式</span><span class="sxs-lookup"><span data-stu-id="caff6-155">Font Expressions</span></span>  
 <span data-ttu-id="caff6-156">指定 MDX 運算式，以根據導出成員的值來動態設定資料格的字型、字型大小和字型屬性。</span><span class="sxs-lookup"><span data-stu-id="caff6-156">Specifies MDX expressions that dynamically set the font, font size, and font attributes for cells based on the value of the calculated member.</span></span> <span data-ttu-id="caff6-157">如果用戶端應用程式不支援，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="caff6-157">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="caff6-158">您可以從 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤中，複製或拖曳 Cube 元件至 [計算運算式] 窗格裡的 [運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="caff6-158">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span> <span data-ttu-id="caff6-159">您可以從 [計算工具]\*\*\*\* 窗格的 [函數]\*\*\*\* 索引標籤中，複製或拖曳函數至 [計算運算式] 窗格裡的 [運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="caff6-159">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span>  
  
## <a name="addressing-calculated-members"></a><span data-ttu-id="caff6-160">定址導出成員</span><span class="sxs-lookup"><span data-stu-id="caff6-160">Addressing Calculated Members</span></span>  
 <span data-ttu-id="caff6-161">您在 Cube 設計師\*\*\*\* 的 [計算]\*\*\*\* 索引標籤上建立導出成員時，會指定要儲存導出成員的父階層。</span><span class="sxs-lookup"><span data-stu-id="caff6-161">When you create a calculated member on the **Calculations** tab of **Cube Designer**, you specify the parent hierarchy in which the calculated member is stored.</span></span> <span data-ttu-id="caff6-162">父階層會依據下列規則決定如何定址導出成員：</span><span class="sxs-lookup"><span data-stu-id="caff6-162">The parent hierarchy determines how a calculated member can be addressed, according to the following rules:</span></span>  
  
-   <span data-ttu-id="caff6-163">如果導出成員是建立在量值維度中，則導出成員可以在該維度中定址。</span><span class="sxs-lookup"><span data-stu-id="caff6-163">If a calculated member is created in the measures dimension, the calculated member is addressable in that dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caff6-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caff6-164">See Also</span></span>  
 [<span data-ttu-id="caff6-165">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="caff6-165">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
