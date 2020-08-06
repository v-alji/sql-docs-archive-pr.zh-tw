---
title: 影像屬性對話方塊、一般 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10051"
- sql12.rtp.rptdesigner.pictureproperties.general.f1
ms.assetid: c2218b93-f7fe-46ef-995f-d7dadf9752ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e599a437ae367a38483dbde99ffff79f64b957ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710350"
---
# <a name="image-properties-dialog-box-general-report-builder-and-ssrs"></a><span data-ttu-id="a42e1-102">影像屬性對話方塊、一般 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a42e1-102">Image Properties Dialog Box, General (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a42e1-103">選取 [影像屬性]\*\*\*\* 對話方塊上的 [一般]\*\*\*\* 來加入圖片、變更影像的預設名稱，以及加入工具提示文字。</span><span class="sxs-lookup"><span data-stu-id="a42e1-103">Select **General** on the **Image Properties** dialog box to add a picture, change the default name of the image, and add ToolTip text.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a42e1-104">選項。</span><span class="sxs-lookup"><span data-stu-id="a42e1-104">Options</span></span>  
 <span data-ttu-id="a42e1-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a42e1-105">**Name**</span></span>  
 <span data-ttu-id="a42e1-106">輸入項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="a42e1-106">Type a name for the item.</span></span> <span data-ttu-id="a42e1-107">名稱在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a42e1-107">The name must be unique within the report.</span></span> <span data-ttu-id="a42e1-108">根據預設，系統會指派一個一般名稱 (例如，Image1 或 Image2)。</span><span class="sxs-lookup"><span data-stu-id="a42e1-108">By default, a general name, such as Image1 or Image2, is assigned.</span></span>  
  
 <span data-ttu-id="a42e1-109">**工具提示**</span><span class="sxs-lookup"><span data-stu-id="a42e1-109">**Tooltip**</span></span>  
 <span data-ttu-id="a42e1-110">輸入文字或評估為工具提示的運算式。</span><span class="sxs-lookup"><span data-stu-id="a42e1-110">Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="a42e1-111">按一下運算式 (*fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="a42e1-111">Click the Expression (*fx*) button to edit the expression.</span></span> <span data-ttu-id="a42e1-112">使用者在 HTML 報表中將指標暫停在項目上時，[工具提示]\*\*\*\* 會顯示。</span><span class="sxs-lookup"><span data-stu-id="a42e1-112">The **Tooltip** appears when the user pauses the pointer over the item in an HTML report.</span></span>  
  
 <span data-ttu-id="a42e1-113">**選取影像來源**</span><span class="sxs-lookup"><span data-stu-id="a42e1-113">**Select the image source**</span></span>  
 <span data-ttu-id="a42e1-114">指出影像儲存的位置，以便在轉譯報表時，讓報表處理器知道要從哪裡取得影像。</span><span class="sxs-lookup"><span data-stu-id="a42e1-114">Indicate where the image is stored so that when the report is rendered, the report processor will know where to get the image from.</span></span>  
  
-   <span data-ttu-id="a42e1-115">**外部** ：當您希望影像在報表伺服器或網頁伺服器上繼續當作檔案存在時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a42e1-115">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="a42e1-116">**內嵌** ：當您要將影片內嵌到報表中時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a42e1-116">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="a42e1-117">**資料庫** ：當您要加入的資料庫欄位名稱代表您要包含在報表中的影像時，選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a42e1-117">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="a42e1-118">**使用此影像**</span><span class="sxs-lookup"><span data-stu-id="a42e1-118">**Use this image**</span></span>  
 <span data-ttu-id="a42e1-119">此選項會在您選取 [內嵌]\*\*\*\* 或 [外部]\*\*\*\* 選項時出現。</span><span class="sxs-lookup"><span data-stu-id="a42e1-119">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="a42e1-120">如果您要內嵌影像，從下拉式清單中選擇您要加入報表的影像。</span><span class="sxs-lookup"><span data-stu-id="a42e1-120">If you are embedding the image, choose the image that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="a42e1-121">按一下 [匯入]\*\*\*\* 按鈕，將影像加入到下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="a42e1-121">Click the **Import** button to add the image to the drop-down list.</span></span>  
  
 <span data-ttu-id="a42e1-122">如果您選取 [外部]\*\*\*\* 選項，輸入影像的 URL。</span><span class="sxs-lookup"><span data-stu-id="a42e1-122">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="a42e1-123">對於發行到設定為原生模式之報表伺服器的報表，請使用完整或相對路徑，</span><span class="sxs-lookup"><span data-stu-id="a42e1-123">For a report published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="a42e1-124">例如，HTTP:// \<servername> /images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="a42e1-124">For example, http://\<servername>/images/image1.jpg.</span></span> <span data-ttu-id="a42e1-125">對於發行到設定為 SharePoint 整合模式之報表伺服器的報表，請使用完整 URL，</span><span class="sxs-lookup"><span data-stu-id="a42e1-125">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL.</span></span> <span data-ttu-id="a42e1-126">例如，HTTP:// \<*SharePointservername*> / \<*site*> /Documents/images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="a42e1-126">For example, http://\<*SharePointservername*>/\<*site*>/Documents/images/image1.jpg.</span></span>  
  
 <span data-ttu-id="a42e1-127">**匯入**</span><span class="sxs-lookup"><span data-stu-id="a42e1-127">**Import**</span></span>  
 <span data-ttu-id="a42e1-128">按一下此選項，即可將影像加入到 [使用此影像]\*\*\*\* 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="a42e1-128">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="a42e1-129">**使用此欄位**</span><span class="sxs-lookup"><span data-stu-id="a42e1-129">**Use this field**</span></span>  
 <span data-ttu-id="a42e1-130">此選項會在您選取 [資料庫]\*\*\*\* 選項時出現。</span><span class="sxs-lookup"><span data-stu-id="a42e1-130">This option appears if you select the **Database** option.</span></span> <span data-ttu-id="a42e1-131">選取欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="a42e1-131">Select the field name.</span></span>  
  
 <span data-ttu-id="a42e1-132">**使用此 MIME 類型**</span><span class="sxs-lookup"><span data-stu-id="a42e1-132">**Use this MIME type**</span></span>  
 <span data-ttu-id="a42e1-133">選擇資料庫中包含的適當影像格式 (例如，.bmp、.jpeg、.gif、.png 和 .x-png)。</span><span class="sxs-lookup"><span data-stu-id="a42e1-133">Choose the appropriate format of the images contained in the database, for example, .bmp, .jpeg, .gif, .png, and .x-png.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42e1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a42e1-134">See Also</span></span>  
 <span data-ttu-id="a42e1-135">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a42e1-135">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a42e1-136">[&#40;報表產生器和 SSRS&#41;的影像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a42e1-136">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a42e1-137">對話方塊、窗格和精靈的報表產生器說明</span><span class="sxs-lookup"><span data-stu-id="a42e1-137">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
