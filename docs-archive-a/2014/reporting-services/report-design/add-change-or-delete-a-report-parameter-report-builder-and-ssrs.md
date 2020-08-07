---
title: 新增、變更或刪除報表參數 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 231cd51d7ed0a481f004b39a2e8819df3fc33748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595769"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="fa38d-102">加入、變更或刪除報表參數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fa38d-102">Add, Change, or Delete a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fa38d-103">報表參數可讓您選擇報表資料、將相關的報表連接在一起，以及變更報表呈現方式。</span><span class="sxs-lookup"><span data-stu-id="fa38d-103">A report parameter provides a way to choose report data, connect related reports together, and vary the report presentation.</span></span> <span data-ttu-id="fa38d-104">您可以提供預設值和可用值的清單，而且使用者可以變更選取範圍。</span><span class="sxs-lookup"><span data-stu-id="fa38d-104">You can provide a default value and a list of available values, and the user can change the selection.</span></span>  
  
 <span data-ttu-id="fa38d-105">在您發行報表之後，可以在報表伺服器上變更報表參數的預設值、可用值，以及其他屬性。</span><span class="sxs-lookup"><span data-stu-id="fa38d-105">After you publish a report, you can change the default values, the available values, and other properties for a report parameter on the report server.</span></span> <span data-ttu-id="fa38d-106">您可以建立連結報表來提供多組預設參數值。</span><span class="sxs-lookup"><span data-stu-id="fa38d-106">You can provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="fa38d-107">如需詳細資訊，請參閱《 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 線上叢書 [》中](https://go.microsoft.com/fwlink/?linkid=120955)文件集的＜設定已發行報表的參數屬性＞。</span><span class="sxs-lookup"><span data-stu-id="fa38d-107">For more information, see "Setting Parameter Properties for a Published Report" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a><span data-ttu-id="fa38d-108">若要加入或編輯報表參數</span><span class="sxs-lookup"><span data-stu-id="fa38d-108">To add or edit a report parameter</span></span>  
  
1.  <span data-ttu-id="fa38d-109">在 **[報表資料]** 窗格中，以滑鼠右鍵按一下 **[參數]** 節點，然後按一下 **[加入參數]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-109">In the **Report Data** pane, right-click the **Parameters** node and click **Add Parameter**.</span></span> <span data-ttu-id="fa38d-110">**[報表參數屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fa38d-110">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="fa38d-111">在 **[名稱]** 中，輸入參數的名稱或接受預設的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa38d-111">In **Name**, type the name of the parameter or accept the default name.</span></span>  
  
3.  <span data-ttu-id="fa38d-112">在 **[提示]** 中，輸入使用者執行報表時，在參數文字方塊旁邊顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="fa38d-112">In **Prompt**, type the text that appears next to the parameter text box when the user runs the report.</span></span>  
  
4.  <span data-ttu-id="fa38d-113">在 **[資料類型]** 中，選取參數值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fa38d-113">In **Data type**, select the data type for the parameter value.</span></span>  
  
5.  <span data-ttu-id="fa38d-114">如果參數可以包含空白值，請選取 **[允許空白值]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-114">If the parameter can contain a blank value, select **Allow blank value**.</span></span>  
  
6.  <span data-ttu-id="fa38d-115">如果參數可以包含 Null 值，請選取 **[允許 Null 值]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-115">If the parameter can contain a null value, select **Allow null value**.</span></span>  
  
7.  <span data-ttu-id="fa38d-116">若要允許使用者針對參數選取多個值，請選取 **[允許多個值]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-116">To allow a user to select more than one value for the parameter, select **Allow multiple values**.</span></span>  
  
8.  <span data-ttu-id="fa38d-117">設定可見性選項。</span><span class="sxs-lookup"><span data-stu-id="fa38d-117">Set the visibility option.</span></span>  
  
    -   <span data-ttu-id="fa38d-118">若要在報表頂端的工具列上顯示此參數，請選取 **[可見]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-118">To show the parameter on the toolbar at the top of the report, select **Visible**.</span></span>  
  
    -   <span data-ttu-id="fa38d-119">若要隱藏此參數而不顯示在工具列上，請選取 **[隱藏]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-119">To hide the parameter so that it does not display on the toolbar, select **Hidden**.</span></span>  
  
    -   <span data-ttu-id="fa38d-120">若要隱藏此參數並且防止任何人在發行報表之後於報表伺服器上修改此參數，請選取 **[內部]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-120">To hide the parameter and protect it from being modified on the report server after the report is published, select **Internal**.</span></span> <span data-ttu-id="fa38d-121">然後，報表參數就只能在報表定義中檢視。</span><span class="sxs-lookup"><span data-stu-id="fa38d-121">The report parameter can then only be viewed in the report definition.</span></span> <span data-ttu-id="fa38d-122">若要使用此選項，您必須設定預設值或允許參數接受 Null 值。</span><span class="sxs-lookup"><span data-stu-id="fa38d-122">For this option, you must set a default value or allow the parameter to accept a null value.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a><span data-ttu-id="fa38d-123">若要刪除報表參數</span><span class="sxs-lookup"><span data-stu-id="fa38d-123">To delete a report parameter</span></span>  
  
1.  <span data-ttu-id="fa38d-124">在 **[報表資料]** 窗格中，展開 **[參數]** 節點。</span><span class="sxs-lookup"><span data-stu-id="fa38d-124">In the **Report Data** pane, expand the **Parameters** node.</span></span>  
  
2.  <span data-ttu-id="fa38d-125">以滑鼠右鍵按一下報表參數，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="fa38d-125">Right-click the report parameter and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa38d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa38d-126">See Also</span></span>  
 <span data-ttu-id="fa38d-127">[為報表參數新增、變更或刪除可用的值 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-127">[Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="fa38d-128">[為報表參數新增、變更或刪除預設值 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-128">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="fa38d-129">[變更報表參數 &#40;報表產生器和 SSRS 的順序&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-129">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fa38d-130">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-130">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="fa38d-131">[對話方塊、窗格和嚮導的報表產生器說明](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-131">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="fa38d-132">[將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-132">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fa38d-133">[教學課程：將參數加入至您的報表 &#40;報表產生器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-133">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="fa38d-134">[教學課程 &#40;報表產生器&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-134">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="fa38d-135">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-135">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="fa38d-136">[參數集合參考 &#40;報表產生器和 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="fa38d-136">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 [<span data-ttu-id="fa38d-137">將多值參數加入至報表</span><span class="sxs-lookup"><span data-stu-id="fa38d-137">Add a multi-value parameter to a Report</span></span>](add-a-multi-value-parameter-to-a-report.md)  
  
  
