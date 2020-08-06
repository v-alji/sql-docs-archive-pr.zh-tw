---
title: 為報表參數新增、變更或刪除可用的值 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportparameters.availablevalues.f1
- "10455"
- "10071"
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 985ab3e8dc1d74f94e7242ff57f46ffe4fba9586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595757"
---
# <a name="add-change-or-delete-available-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="80279-102">為報表參數加入、變更或刪除可用的值 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="80279-102">Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="80279-103">當您建立報表參數之後，可以指定要對使用者顯示的可用值清單。</span><span class="sxs-lookup"><span data-stu-id="80279-103">After you create a report parameter, you can specify a list of available values to display to the user.</span></span> <span data-ttu-id="80279-104">可用值清單會將使用者可以做的選擇限制為參數的有效值。</span><span class="sxs-lookup"><span data-stu-id="80279-104">An available values list limits the choices a user can make to only valid values for the parameter.</span></span>  
  
 <span data-ttu-id="80279-105">當執行報表時，可用的值會出現在工具列上報表參數旁邊的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="80279-105">Available values appear in a drop-down list next to the report parameter on the toolbar when the report runs.</span></span> <span data-ttu-id="80279-106">報表參數可代表一個值或多個值。</span><span class="sxs-lookup"><span data-stu-id="80279-106">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="80279-107">如果是多個值，清單的最開頭是 **[全選]** 功能，好讓使用者只需按一下就可以選取或清除所有值。</span><span class="sxs-lookup"><span data-stu-id="80279-107">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span>  
  
 <span data-ttu-id="80279-108">您可以提供靜態值清單或是報表資料集中的清單。</span><span class="sxs-lookup"><span data-stu-id="80279-108">You can provide a static list of values or a list from a report dataset.</span></span> <span data-ttu-id="80279-109">您可以選擇指定標籤欄位來提供值的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="80279-109">You can optionally provide a friendly name for values by specifying a label field.</span></span> <span data-ttu-id="80279-110">例如，如果是根據 `ProductID` 欄位的參數，您可以在參數標籤中顯示 `ProductName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="80279-110">For example, for a parameter based on a `ProductID` field, you can display the `ProductName` field in the parameter label.</span></span> <span data-ttu-id="80279-111">當報表執行時，使用者可以從產品名稱中進行選擇，但是實際選擇的值會是對應的 `ProductID`。</span><span class="sxs-lookup"><span data-stu-id="80279-111">When the report runs, the user can choose from the product names, but the actual chosen value is the corresponding `ProductID`.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="80279-112">在您發行報表之後，可以在報表伺服器上設定參數屬性值，藉以覆寫您在報表撰寫工具中定義於報表的可用值。</span><span class="sxs-lookup"><span data-stu-id="80279-112">After you publish a report, you can override the available values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="80279-113">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="80279-113">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="to-add-or-change-the-available-values-for-a-report-parameter"></a><span data-ttu-id="80279-114">為報表參數加入或變更可用的值</span><span class="sxs-lookup"><span data-stu-id="80279-114">To add or change the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="80279-115">在 [報表資料] 窗格中，展開 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="80279-115">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="80279-116">以滑鼠右鍵按一下參數，然後按一下 [參數屬性]  。</span><span class="sxs-lookup"><span data-stu-id="80279-116">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="80279-117">**[報表參數屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80279-117">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80279-118">如果看不到 [報表資料] 窗格，請按一下 [檢視]  ，然後按一下 [報表資料]  。</span><span class="sxs-lookup"><span data-stu-id="80279-118">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="80279-119">按一下 **[可用的值]** 。</span><span class="sxs-lookup"><span data-stu-id="80279-119">Click **Available Values**.</span></span> <span data-ttu-id="80279-120">選取可用的值選項：</span><span class="sxs-lookup"><span data-stu-id="80279-120">Select an available values option:</span></span>  
  
    -   <span data-ttu-id="80279-121">按一下 [指定值]  ，以手動方式提供值的清單，並可選擇提供值的易記名稱 (標籤)。</span><span class="sxs-lookup"><span data-stu-id="80279-121">Click **Specify values** to manually provide a list of values, and optionally, friendly names (the labels) for the values.</span></span>  
  
         <span data-ttu-id="80279-122">按一下 **[加入]** ，然後在 **[值]** 文字方塊中輸入值，並選擇在 **[標籤]** 文字方塊內輸入標籤。</span><span class="sxs-lookup"><span data-stu-id="80279-122">Click **Add** and then enter the value in the **Value** text box, and optionally, the label in the **Label** text box.</span></span> <span data-ttu-id="80279-123">若未提供標籤，就會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="80279-123">If you do not provide a label, the value is used.</span></span> <span data-ttu-id="80279-124">您可以撰寫值的運算式。</span><span class="sxs-lookup"><span data-stu-id="80279-124">You can write an expression for a value.</span></span> <span data-ttu-id="80279-125">資料類型必須符合參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80279-125">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="80279-126">欄位名稱不能用於參數的運算式。</span><span class="sxs-lookup"><span data-stu-id="80279-126">Field names cannot be used in an expression for a parameter.</span></span> <span data-ttu-id="80279-127">如需範例，請參閱[常用的篩選 &#40;報表產生器及 SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="80279-127">For examples, see [Commonly Used Filters &#40;Report Builder and SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="80279-128">請重複這個步驟，盡量提供您想要的值。</span><span class="sxs-lookup"><span data-stu-id="80279-128">Repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="80279-129">您在這個清單中看到的項目順序會決定使用者在下拉式清單中看到它們的順序。</span><span class="sxs-lookup"><span data-stu-id="80279-129">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="80279-130">若要變更某個項目在清單中的順序，請按一下 **[值]** 或 **[標籤]** 文字方塊來選取此項目，然後使用向上箭頭和向下箭頭按鈕，將此項目移到清單中的更高或更低位置。</span><span class="sxs-lookup"><span data-stu-id="80279-130">To change the order of an item in the list, click a **Value** or **Label** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="80279-131">按一下 **[從查詢取得值]** 可提供現有資料集名稱 (該資料集會擷取值)，並可選擇為這個參數提供易記名稱。</span><span class="sxs-lookup"><span data-stu-id="80279-131">Click **Get values from a query** to provide the name of an existing dataset that retrieves the values, and optionally, the friendly names for this parameter.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="80279-132">如果相同資料集包含報表參數的對應查詢參數，報表就會在您嘗試執行時顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="80279-132">If the same dataset contains the corresponding query parameter for the report parameter, the report will display an error message when you try to run it.</span></span> <span data-ttu-id="80279-133">使用不同資料集來擷取值，即可解決這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="80279-133">You resolve this error by using a different dataset to retrieve the values.</span></span>  
  
         <span data-ttu-id="80279-134">在 **[資料集]** 中，選擇此資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="80279-134">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="80279-135">在 **[值欄位]** 中，選擇可提供參數值的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="80279-135">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
         <span data-ttu-id="80279-136">在 **[標籤欄位]** 中，選擇可為參數提供易記名稱的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="80279-136">In **Label field**, choose the name of the field that provides the friendly names for the parameter.</span></span> <span data-ttu-id="80279-137">如果易記名稱沒有個別的欄位，請選擇與 **[值]** 欄位相同的欄位。</span><span class="sxs-lookup"><span data-stu-id="80279-137">If there is no separate field for friendly names, choose the same field as you chose for the **Value** field.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="80279-138">當您預覽報表時，您會看到此參數之可用值的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="80279-138">When you preview the report, you see a drop-down list of available values for the parameter.</span></span>  
  
### <a name="to-remove-the-available-values-for-a-report-parameter"></a><span data-ttu-id="80279-139">移除報表參數的可用值</span><span class="sxs-lookup"><span data-stu-id="80279-139">To remove the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="80279-140">在 [報表資料] 窗格中，展開 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="80279-140">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="80279-141">以滑鼠右鍵按一下參數，然後按一下 [參數屬性]  。</span><span class="sxs-lookup"><span data-stu-id="80279-141">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="80279-142">**[報表參數]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80279-142">The **Report Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="80279-143">按一下 **[可用的值]** 。</span><span class="sxs-lookup"><span data-stu-id="80279-143">Click **Available Values**.</span></span>  
  
3.  <span data-ttu-id="80279-144">在 **[選取下列其中一個選項]** 中，按一下 **[無]** 。</span><span class="sxs-lookup"><span data-stu-id="80279-144">In **Select from one of the following options**, click **None**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="80279-145">當您預覽報表時，此參數之可用值的下拉式清單便不再出現。</span><span class="sxs-lookup"><span data-stu-id="80279-145">When you preview the report, you the drop-down list of available values for the parameter no longer appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80279-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80279-146">See Also</span></span>  
 <span data-ttu-id="80279-147">[變更報表參數的順序 &#40;報表產生器及 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80279-147">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80279-148">[加入、變更或刪除報表參數 &#40;報表產生器及 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80279-148">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80279-149">[將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80279-149">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80279-150">[為報表參數新增、變更或刪除預設值 &#40;報表產生器及 SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="80279-150">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="80279-151">[參數集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="80279-151">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="80279-152">[教學課程：將參數新增至報表 &#40;報表產生器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="80279-152">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="80279-153">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="80279-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
