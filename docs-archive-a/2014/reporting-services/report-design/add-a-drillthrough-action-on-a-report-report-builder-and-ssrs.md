---
title: 在報表上新增鑽研動作 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 153729c4-d01e-4629-b78f-0cfd5a7f83da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a429380f677a309e4e1437a2e3c5036bb4e8a455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593807"
---
# <a name="add-a-drillthrough-action-on-a-report-report-builder-and-ssrs"></a><span data-ttu-id="19699-102">在報表上加入鑽研動作 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="19699-102">Add a Drillthrough Action on a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="19699-103">當您按一下主報表中的連結所開啟的報表稱為 *「鑽研報表」* (Drillthrough Report)。</span><span class="sxs-lookup"><span data-stu-id="19699-103">The report that opens when you click the link in the main report is known as a *drillthrough report*.</span></span> <span data-ttu-id="19699-104">此鑽研連結會啟用一個鑽研動作。</span><span class="sxs-lookup"><span data-stu-id="19699-104">This drillthrough link enables a drillthrough action.</span></span>  
  
 <span data-ttu-id="19699-105">鑽研報表必須與主報表發行至相同的報表伺服器，但是可位於不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="19699-105">Drillthrough reports must be published to the same report server as the main report, but they can be in different folders.</span></span> <span data-ttu-id="19699-106">您可以將鑽研連結加入到具有 **Action** 屬性的任何項目，例如文字方塊、影像或是圖表的資料點。</span><span class="sxs-lookup"><span data-stu-id="19699-106">You can add a drillthrough link to any item that has an **Action** property, such as a text box, an image, or data points on a chart.</span></span>  
  
 <span data-ttu-id="19699-107">若要將鑽研連結加入到報表，您必須先建立主報表將連結的鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="19699-107">To add a drillthrough link to a report, you must first create the drillthrough report that the main report will link to.</span></span> <span data-ttu-id="19699-108">鑽研報表通常包含有關原始摘要報表之項目的詳細資料，而且經常包含參數，這些參數會根據主報表傳遞過來的參數來篩選鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="19699-108">A drillthrough report commonly contains details about an item that is contained in the original summary report, and often contains parameters that filter the drillthrough report based on parameters passed to it from the main report.</span></span> <span data-ttu-id="19699-109">如需建立鑽研報表的詳細資訊，請參閱[鑽研報表 &#40;報表產生器和 SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19699-109">For more information on creating the drillthrough report, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-drillthrough-action"></a><span data-ttu-id="19699-110">若要加入鑽研動作</span><span class="sxs-lookup"><span data-stu-id="19699-110">To add a drillthrough action</span></span>  
  
1.  <span data-ttu-id="19699-111">在 [設計] 檢視中，以滑鼠右鍵按一下要新增連結的文字方塊、影像或圖表，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="19699-111">In Design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="19699-112">在項目的 **[屬性]** 對話方塊中，按一下 **[動作]** 。</span><span class="sxs-lookup"><span data-stu-id="19699-112">In the item's **Properties** dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="19699-113">選取 **[移至報表]** 。</span><span class="sxs-lookup"><span data-stu-id="19699-113">Select **Go to report**.</span></span> <span data-ttu-id="19699-114">對話方塊中會出現這個選項的其他區段。</span><span class="sxs-lookup"><span data-stu-id="19699-114">Additional sections appear in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="19699-115">在 **[指定報表]** 中，按一下 **[瀏覽]** ，找出您想要跳至的報表，或輸入報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="19699-115">In **Specify a report**, click **Browse** to locate the report that you want to jump to, or type the name of the report.</span></span> <span data-ttu-id="19699-116">或者，您也可以按一下運算式 (**fx**) 按鈕來建立報表名稱的運算式。</span><span class="sxs-lookup"><span data-stu-id="19699-116">Alternatively, click the expression (**fx**) button to create an expression for the report name.</span></span>  
  
     <span data-ttu-id="19699-117">鑽研報表的路徑格式會因原生和 SharePoint 整合模式而不同。</span><span class="sxs-lookup"><span data-stu-id="19699-117">The format of the path to the drillthrough report differs for native and SharePoint integrated mode.</span></span> <span data-ttu-id="19699-118">如果您瀏覽至報表，就會提供正確格式的路徑。</span><span class="sxs-lookup"><span data-stu-id="19699-118">If you browse to the report, a path of the correct format is provided.</span></span> <span data-ttu-id="19699-119">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19699-119">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="19699-120">如果您必須指定鑽研報表的參數，請遵循下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="19699-120">If you have to specify parameters for the drillthrough report, follow the next step.</span></span>  
  
5.  <span data-ttu-id="19699-121">在 **[使用這些參數執行報表]** 中，按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="19699-121">In **Use these parameters to run the report**, click **Add**.</span></span> <span data-ttu-id="19699-122">新的資料列就會加入至參數方格。</span><span class="sxs-lookup"><span data-stu-id="19699-122">A new row is added to the parameter grid.</span></span>  
  
    -   <span data-ttu-id="19699-123">在 [名稱]  文字方塊中，按一下下拉式清單或鍵入鑽研報表內的報表參數名稱。</span><span class="sxs-lookup"><span data-stu-id="19699-123">In the **Name** text box, click the drop-down list or type the name of the report parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="19699-124">參數清單中的名稱必須與目標報表中預期的參數完全相符。</span><span class="sxs-lookup"><span data-stu-id="19699-124">The names in the parameter list must match the expected parameters in the target report exactly.</span></span> <span data-ttu-id="19699-125">例如，參數名稱的大小寫必須相符。</span><span class="sxs-lookup"><span data-stu-id="19699-125">For example, parameter names must match by case.</span></span> <span data-ttu-id="19699-126">如果名稱不相符，或是未列出預期的參數，鑽研報表就會失敗。</span><span class="sxs-lookup"><span data-stu-id="19699-126">If the names do not match, or if an expected parameter is not listed, the drillthrough report fails.</span></span>  
  
    -   <span data-ttu-id="19699-127">在 **[值]** 中，輸入或選取要傳遞給鑽研報表內之參數的值。</span><span class="sxs-lookup"><span data-stu-id="19699-127">In **Value**, type or select the value to pass to the parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="19699-128">值可以包含運算式，此運算式必須評估為傳遞至報表參數的值。</span><span class="sxs-lookup"><span data-stu-id="19699-128">Values can contain an expression that evaluates to a value to pass to the report parameter.</span></span> <span data-ttu-id="19699-129">值清單中的運算式包含目前報表的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="19699-129">The expressions in the value list include the field list for the current report.</span></span>  
  
     <span data-ttu-id="19699-130">如需如何隱藏報表中參數的資訊，請參閱[新增、變更或刪除報表參數 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19699-130">For information on how to hide parameters in reports, see [Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="19699-131">(選擇性) 如果是文字方塊，在 [功能區] 的 [主資料夾]  索引標籤上變更文字的色彩和效果，向使用者指示該文字為連結，將會很有協助。</span><span class="sxs-lookup"><span data-stu-id="19699-131">(Optional) For text boxes, it is helpful to indicate to the user that the text is a link by changing the color and effect of the text on the **Home** tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="19699-132">若要測試連結，請執行報表，然後按一下這個連結設定所在的報表項目。</span><span class="sxs-lookup"><span data-stu-id="19699-132">To test the link, run the report and click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19699-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19699-133">See Also</span></span>  
 <span data-ttu-id="19699-134">[動作屬性對話方塊 &#40;報表產生器和 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19699-134">[Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="19699-135">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19699-135">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="19699-136">在數列上顯示工具提示 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="19699-136">Show ToolTips on a Series &#40;Report Builder and SSRS&#41;</span></span>](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
  
