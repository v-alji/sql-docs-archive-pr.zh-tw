---
title: 變更指標圖示和指標集合 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 398d21319ab6da22f2b10c3607baf8f110d6e65b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706206"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a><span data-ttu-id="32bc6-102">變更指標圖示和指標集合 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="32bc6-102">Change Indicator Icons and Indicator Sets (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="32bc6-103">會提供預先設定的指標集合，這個指標集合在已傳遞的報表中可能不一定會有效地描述您的資料，運作也不一定良好。</span><span class="sxs-lookup"><span data-stu-id="32bc6-103">provides preconfigured indicators sets, which might not always depict your data effectively and work well in the delivered report.</span></span> <span data-ttu-id="32bc6-104">本主題提供變更指標圖示外觀，以及變更指標集合以加入不同、更多或更少之指標圖示的程序。</span><span class="sxs-lookup"><span data-stu-id="32bc6-104">This topic provides procedures to change the appearance of indicator icons and change the indicator sets to include different, more, or fewer indicator icons.</span></span>  
  
 <span data-ttu-id="32bc6-105">您可以使用運算式來設定選項，如色彩。</span><span class="sxs-lookup"><span data-stu-id="32bc6-105">Options such as colors can be set by using expressions.</span></span> <span data-ttu-id="32bc6-106">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="32bc6-106">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-color-of-an-indicator-icon"></a><span data-ttu-id="32bc6-107">若要變更指標圖示的色彩</span><span class="sxs-lookup"><span data-stu-id="32bc6-107">To change the color of an indicator icon</span></span>  
  
1.  <span data-ttu-id="32bc6-108">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-108">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32bc6-109">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="32bc6-109">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32bc6-110">在您要變更的圖示旁邊按一下 [色彩]  資料行中的向下箭號，然後按一下要使用的色彩：[無色彩]  或 [更多色彩]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-110">Click the down arrow in the **Color** column next to the icon that you want to change and click the color to use, **No Color**, or **More colors**.</span></span>  
  
     <span data-ttu-id="32bc6-111">您可以選擇按一下 **「運算式」** \(*fx*) 按鈕來編輯設定 **[色彩]** 選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="32bc6-111">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Color** option.</span></span>  
  
     <span data-ttu-id="32bc6-112">如果您按一下 [更多色彩]  ，[選取色彩]  對話方塊隨即開啟，讓您從中選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="32bc6-112">If you clicked **More Colors**, the **Select Color** dialog box opens, where you can choose from a wide array of colors.</span></span> <span data-ttu-id="32bc6-113">如需其選項的詳細資訊，請參閱[選取色彩對話方塊 &#40;報表產生器及 SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="32bc6-113">For more information about its options, see [Select Color Dialog Box &#40;Report Builder and SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="32bc6-114">按一下 [確定]  關閉 [選取色彩]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="32bc6-114">Click **OK** to close the **Select Color** dialog box.</span></span>  
  
4.  <span data-ttu-id="32bc6-115">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-115">Click **OK**.</span></span>  
  
### <a name="to-change-the-icon"></a><span data-ttu-id="32bc6-116">若要變更圖示</span><span class="sxs-lookup"><span data-stu-id="32bc6-116">To change the icon</span></span>  
  
1.  <span data-ttu-id="32bc6-117">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-117">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32bc6-118">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="32bc6-118">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32bc6-119">按一下您要變更之圖示旁邊的向下鍵，然後選取不同的圖示。</span><span class="sxs-lookup"><span data-stu-id="32bc6-119">Click the down arrow next to the icon that you want to change and select a different icon.</span></span>  
  
     <span data-ttu-id="32bc6-120">您可以選擇按一下 **「運算式」** \(*fx*) 按鈕來編輯設定 **[圖示]** 選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="32bc6-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Icon** option.</span></span>  
  
4.  <span data-ttu-id="32bc6-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-121">Click **OK**.</span></span>  
  
### <a name="to-use-a-custom-image-as-an-indicator-icon"></a><span data-ttu-id="32bc6-122">若要使用自訂影像做為指標圖示</span><span class="sxs-lookup"><span data-stu-id="32bc6-122">To use a custom image as an indicator icon</span></span>  
  
1.  <span data-ttu-id="32bc6-123">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32bc6-124">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="32bc6-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32bc6-125">在您要變更的圖示旁邊按一下向下箭號，然後選取 [影像]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-125">Click the down arrow next to the icon that you wan to change and select **Image**.</span></span>  
  
4.  <span data-ttu-id="32bc6-126">在 [選取影像來源]  清單中，按一下 [外部]  、[內嵌]  或 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-126">In the **Select the image source** list, click **External**, **Embedded**, or **Database**.</span></span>  
  
5.  <span data-ttu-id="32bc6-127">根據影像的來源，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="32bc6-127">Depending on the source of the image, do the one of the following:</span></span>  
  
    -   <span data-ttu-id="32bc6-128">若要使用儲存在報表外部的影像，按一下 [瀏覽]  ，然後找出影像。</span><span class="sxs-lookup"><span data-stu-id="32bc6-128">To use an image that is stored externally to the report, click **Browse** and locate the image.</span></span> <span data-ttu-id="32bc6-129">報表將包含影像的參考。</span><span class="sxs-lookup"><span data-stu-id="32bc6-129">The report will include a reference to the image.</span></span>  
  
    -   <span data-ttu-id="32bc6-130">若要使用內嵌在報表中的影像，按一下 [匯入]  ，然後找出影像。</span><span class="sxs-lookup"><span data-stu-id="32bc6-130">To use an image that is embedded in the report, click **Import** and locate the image.</span></span> <span data-ttu-id="32bc6-131">影像會加入至報告定義，並與它一起儲存。</span><span class="sxs-lookup"><span data-stu-id="32bc6-131">The image will be added to the report definition and saved with it.</span></span>  
  
    -   <span data-ttu-id="32bc6-132">若要使用資料庫中的影像，請在 [使用此欄位]  清單中，</span><span class="sxs-lookup"><span data-stu-id="32bc6-132">To use an image that is in a database, in the **Use this field** list.</span></span> <span data-ttu-id="32bc6-133">選取清單中的欄位，然後在 [使用此 MIME 類型]  清單中，選取影像的 MIME 類型。</span><span class="sxs-lookup"><span data-stu-id="32bc6-133">select the field from the list and then in the **Use this MIME type** list, select the MIME type of the image.</span></span>  
  
6.  <span data-ttu-id="32bc6-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-134">Click **OK**.</span></span>  
  
### <a name="to-add-an-icon-to-the-indicator-set"></a><span data-ttu-id="32bc6-135">若要將圖示加入至指標集合</span><span class="sxs-lookup"><span data-stu-id="32bc6-135">To add an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="32bc6-136">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-136">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32bc6-137">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="32bc6-137">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32bc6-138">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-138">Click **Add**.</span></span> <span data-ttu-id="32bc6-139">指標隨即使用預設圖示與 [無色彩]  選項新增。</span><span class="sxs-lookup"><span data-stu-id="32bc6-139">An indicator is added, using the default icon and the **No Color** option.</span></span>  
  
     <span data-ttu-id="32bc6-140">設定指標使用您想要的圖示和色彩。</span><span class="sxs-lookup"><span data-stu-id="32bc6-140">Configure the indictor to use the icon and color you want.</span></span> <span data-ttu-id="32bc6-141">本主題稍早的程序描述執行這項操作的步驟。</span><span class="sxs-lookup"><span data-stu-id="32bc6-141">Procedures earlier in this topic describe the steps to do this.</span></span>  
  
4.  <span data-ttu-id="32bc6-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-142">Click **OK**.</span></span>  
  
### <a name="to-delete-an-icon-to-the-indicator-set"></a><span data-ttu-id="32bc6-143">若要從指標集合刪除圖示</span><span class="sxs-lookup"><span data-stu-id="32bc6-143">To delete an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="32bc6-144">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-144">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="32bc6-145">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="32bc6-145">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="32bc6-146">選取要刪除的圖示，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-146">Select the icon to delete, and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="32bc6-147">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="32bc6-147">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bc6-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32bc6-148">See Also</span></span>  
 [<span data-ttu-id="32bc6-149">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32bc6-149">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
