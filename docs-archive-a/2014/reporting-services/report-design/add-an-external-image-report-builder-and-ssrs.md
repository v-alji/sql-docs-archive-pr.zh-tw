---
title: 新增外部影像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d0030c8f29b14b2c62048be306daa15948cd8d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687454"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a><span data-ttu-id="088f7-102">加入外部影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="088f7-102">Add an External Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="088f7-103">外部影像可以位於原生模式或 SharePoint 整合模式的報表伺服器上，也可以位於其他任何網站上。</span><span class="sxs-lookup"><span data-stu-id="088f7-103">External images can be on a report server in native mode or SharePoint integrated mode, or on any other Web site.</span></span> <span data-ttu-id="088f7-104">當您在報表中加入外部影像時，您必須確認此影像存在，而且報表讀者有權存取此影像。</span><span class="sxs-lookup"><span data-stu-id="088f7-104">When you include external images in your report, you must verify that the image exists and that the report reader has permissions to access the image.</span></span> <span data-ttu-id="088f7-105">如需詳細資訊，請參閱[影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="088f7-105">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a><span data-ttu-id="088f7-106">若要加入外部影像</span><span class="sxs-lookup"><span data-stu-id="088f7-106">To add an external image</span></span>  
  
1.  <span data-ttu-id="088f7-107">在報表設計檢視的 **[插入]** 索引標籤上，按一下 **[影像]** 。</span><span class="sxs-lookup"><span data-stu-id="088f7-107">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="088f7-108">在設計介面上，按一下然後將方塊拖曳至所需的影像大小。</span><span class="sxs-lookup"><span data-stu-id="088f7-108">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="088f7-109">在 **[影像屬性]** 對話方塊的 **[一般]** 索引標籤上，於 **[名稱]** 文字方塊內輸入名稱，或是接受預設值。</span><span class="sxs-lookup"><span data-stu-id="088f7-109">On the **General** tab of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="088f7-110">(選擇性) 在 [工具提示]  文字方塊中，鍵入您希望使用者將滑鼠停留在轉譯成 HTML 之報表內的影像上方時，所要顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="088f7-110">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in a report rendered for HTML.</span></span>  
  
5.  <span data-ttu-id="088f7-111">在 **[選取影像來源]** 中，選取 **[外部]** 。</span><span class="sxs-lookup"><span data-stu-id="088f7-111">In **Select the image source**, select **External**.</span></span>  
  
     <span data-ttu-id="088f7-112">若影像位在處於原生模式的報表伺服器上，請在 [使用此影像]  方塊中鍵入影像的相對路徑，例如 ../images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="088f7-112">For an image on a report server in native mode, type a relative path to the image in the **Use this image** box-for example, ../images/image1.jpg.</span></span>  
  
     <span data-ttu-id="088f7-113">若為 SharePoint 整合模式之報表伺服器上的影像，或任何其他網站，請在 [**使用此影像**] 方塊中輸入影像的完整 URL，例如 HTTP:// \<SharePointservername> / \<site> /Documents/images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="088f7-113">For an image on a report server in SharePoint integrated mode, or any other Web site, type a full URL to the image in the **Use this image** box-for example, http://\<SharePointservername>/\<site>/Documents/images/image1.jpg.</span></span>  
  
     <span data-ttu-id="088f7-114">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="088f7-114">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="088f7-115">(選擇性) 按一下 [大小]  、[可見度]  、[動作]  或 [框線]  ，為影像報表項目設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="088f7-115">(Optional) Click **Size**, **Visibility**, **Action**, or **Border** to set additional properties for the image report item.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="088f7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="088f7-116">See Also</span></span>  
 <span data-ttu-id="088f7-117">[在報表中內嵌影像 &#40;報表產生器及 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="088f7-117">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="088f7-118">[新增背景影像 &#40;報表產生器及 SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="088f7-118">[Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="088f7-119">影像屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="088f7-119">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
