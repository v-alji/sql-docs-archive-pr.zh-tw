---
title: 新增資料繫結影像 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585048"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a><span data-ttu-id="9203a-102">加入資料繫結影像 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9203a-102">Add a Data-Bound Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9203a-103">報表可以包含儲存在資料庫內之影像的參考。</span><span class="sxs-lookup"><span data-stu-id="9203a-103">A report can include a reference to an image that is stored in a database.</span></span> <span data-ttu-id="9203a-104">這類影像稱為「資料繫結影像」  。</span><span class="sxs-lookup"><span data-stu-id="9203a-104">Such an image is known as a *data-bound image*.</span></span> <span data-ttu-id="9203a-105">出現在產品清單中產品名稱旁邊的圖片就是資料繫結影像的範例。</span><span class="sxs-lookup"><span data-stu-id="9203a-105">The pictures that appear alongside product names in a product list are examples of data-bound images.</span></span>  
  
 <span data-ttu-id="9203a-106">將資料繫結影像加入至頁首或頁尾時，需要其他步驟。</span><span class="sxs-lookup"><span data-stu-id="9203a-106">Adding a data-bound image to a page header or page footer requires additional steps.</span></span> <span data-ttu-id="9203a-107">如需詳細資訊，請參閱[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9203a-107">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a><span data-ttu-id="9203a-108">若要加入資料繫結影像</span><span class="sxs-lookup"><span data-stu-id="9203a-108">To add a data-bound image</span></span>  
  
1.  <span data-ttu-id="9203a-109">在報表設計檢視中，建立具有資料來源連線的資料表，以及具有包含二進位影像資料之欄位的資料集。</span><span class="sxs-lookup"><span data-stu-id="9203a-109">In report design view, create a table with a data source connection and a dataset with a field that contains binary image data.</span></span> <span data-ttu-id="9203a-110">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9203a-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="9203a-111">將資料行插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="9203a-111">Insert a column in your table.</span></span> <span data-ttu-id="9203a-112">如需詳細資訊，請參閱[插入或刪除資料行 &#40;報表產生器及 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9203a-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="9203a-113">在 **[插入]** 功能表上，按一下 **[插入]** ，然後按一下新資料行的資料列。</span><span class="sxs-lookup"><span data-stu-id="9203a-113">On the **Insert** menu, click **Image**, and then click in the data row of the new column.</span></span>  
  
4.  <span data-ttu-id="9203a-114">在 **[影像屬性]** 對話方塊的 [一般] 頁面上，於 **[名稱]** 文字方塊內輸入名稱，或是接受預設值。</span><span class="sxs-lookup"><span data-stu-id="9203a-114">On the General page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
5.  <span data-ttu-id="9203a-115">(選擇性) 在 [工具提示]  文字方塊中，鍵入您希望使用者將滑鼠停留在轉譯成 HTML 之報表內的影像上方時，所要顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="9203a-115">(Optional) In the **Tooltip** text box, type text to display when the user hovers over the image in the report rendered for HTML.</span></span>  
  
6.  <span data-ttu-id="9203a-116">在 **[選取影像來源]** 中，選取 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="9203a-116">In **Select the image source**, select **Database**.</span></span>  
  
7.  <span data-ttu-id="9203a-117">在 **[使用此欄位]** 中，選取包含您報表中之影像的欄位。</span><span class="sxs-lookup"><span data-stu-id="9203a-117">In **Use this Field**, select the field that contains images in your report.</span></span>  
  
8.  <span data-ttu-id="9203a-118">在 [使用此 MIME 類型]  中，選取影像的 MIME 類型或檔案格式，例如 bmp。</span><span class="sxs-lookup"><span data-stu-id="9203a-118">In **Use this MIME type**, select the MIME type, or file format, of the image-for example, bmp.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="9203a-119">影像預留位置會出現在報表設計介面上。</span><span class="sxs-lookup"><span data-stu-id="9203a-119">An image placeholder appears on the report design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9203a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9203a-120">See Also</span></span>  
 <span data-ttu-id="9203a-121">[影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9203a-121">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9203a-122">[在報表中內嵌影像 &#40;報表產生器及 SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9203a-122">[Embed an Image in a Report &#40;Report Builder and SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9203a-123">[加入外部影像 &#40;報表產生器及 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9203a-123">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9203a-124">影像屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9203a-124">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
