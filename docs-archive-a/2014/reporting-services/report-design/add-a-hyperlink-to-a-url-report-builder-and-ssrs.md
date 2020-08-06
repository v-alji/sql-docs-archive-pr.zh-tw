---
title: 將超連結新增到 URL (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d3db3fc75feca1393e73e698f44db633f09e8dc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688589"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a><span data-ttu-id="f1426-102">將超連結加入到 URL (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f1426-102">Add a Hyperlink to a URL (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f1426-103">當您希望使用者能夠按一下報表中的連結，並開啟瀏覽器指向您所指定的 URL 時，可以將超連結加入到報表項目。</span><span class="sxs-lookup"><span data-stu-id="f1426-103">You can add a hyperlink to a report item when you want your users to be able to click a link in a report and open a browser to the URL that you specify.</span></span> <span data-ttu-id="f1426-104">超連結可以是靜態 URL，或是評估為 URL 的運算式。</span><span class="sxs-lookup"><span data-stu-id="f1426-104">A hyperlink can be a static URL or an expression that evaluates to a URL.</span></span> <span data-ttu-id="f1426-105">如果資料庫中有一個包含 URL 的欄位，運算式便能包含這個欄位，結果會在報表中產生超連結的動態清單。</span><span class="sxs-lookup"><span data-stu-id="f1426-105">If you have a field in a database that contains URLs, the expression can contain that field, resulting in a dynamic list of hyperlinks in the report.</span></span> <span data-ttu-id="f1426-106">您可以將超連結加入至文字方塊、影像、圖表和量測計。</span><span class="sxs-lookup"><span data-stu-id="f1426-106">You can add hyperlinks to text boxes, images, charts, and gauges.</span></span> <span data-ttu-id="f1426-107">您必須確定使用者可存取您提供的 URL。</span><span class="sxs-lookup"><span data-stu-id="f1426-107">You must ensure that the user has access to the URL that you provide.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="f1426-108">您也可以在您和您的使用者有權使用報表伺服器之 URL 要求進行檢視的任何報表伺服器上指定報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="f1426-108">You can also specify URLs to reports on any report server that you and your users have permission to view using URL requests to the report server.</span></span> <span data-ttu-id="f1426-109">例如，您可以指定報表，並在使用者最初檢視報表時為他們隱藏文件引導模式。</span><span class="sxs-lookup"><span data-stu-id="f1426-109">For example, you can specify a report and hide the document map for the user when they first view the report.</span></span> <span data-ttu-id="f1426-110">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312)的 [URL 存取 &#40;SSRS&#41;](../url-access-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f1426-110">For more information, see [URL Access &#40;SSRS&#41;](../url-access-ssrs.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="f1426-111">您可以將 URL 的超連結加入到具有 **[動作]** 屬性的任何項目，例如報表中的文字方塊、影像或導出數列。</span><span class="sxs-lookup"><span data-stu-id="f1426-111">You can add a hyperlink to a URL to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="f1426-112">當使用者按一下該報表項目時，就會發生您定義的動作。</span><span class="sxs-lookup"><span data-stu-id="f1426-112">When the user clicks that report item, the action that you define takes place.</span></span> <span data-ttu-id="f1426-113">如需詳細資訊，請參閱[動作屬性對話方塊 &#40;報表產生器及 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) 和[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f1426-113">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) and [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f1426-114">若要快速開始使用，請參閱[教學課程：格式化文字 &#40;報表產生器&#41;](../tutorial-format-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f1426-114">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1426-115">繫結至資料集欄位的連結可能很容易受到惡意竄改。</span><span class="sxs-lookup"><span data-stu-id="f1426-115">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="f1426-116">如需詳細資訊，請參閱 msdn.microsoft.com 上《 [線上叢書》](../security/secure-reports-and-resources.md) 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][保護報表和資源的安全](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="f1426-116">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
### <a name="to-add-a-hyperlink"></a><span data-ttu-id="f1426-117">若要加入超連結</span><span class="sxs-lookup"><span data-stu-id="f1426-117">To add a hyperlink</span></span>  
  
1.  <span data-ttu-id="f1426-118">在報表設計檢視中，以滑鼠右鍵按一下要加入連結的文字方塊、影像或圖表，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f1426-118">In report design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f1426-119">在 [屬性] 對話方塊中，按一下 **[動作]**。</span><span class="sxs-lookup"><span data-stu-id="f1426-119">In the Properties dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="f1426-120">選取 **[移至 URL]**。</span><span class="sxs-lookup"><span data-stu-id="f1426-120">Select **Go to URL**.</span></span> <span data-ttu-id="f1426-121">此對話方塊中會出現這個選項的其他區段。</span><span class="sxs-lookup"><span data-stu-id="f1426-121">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="f1426-122">在 **[選取 URL]** 中，輸入或選取 URL 或是評估為 URL 的運算式，或者按下拉式箭號，再按一下含有 URL 之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="f1426-122">In **Select URL**, type or select a URL or an expression that evaluates to a URL, or click the drop-down arrow and click the name of a field that contains a URL.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="f1426-123">(選擇性) 文字不會自動格式化為連結。</span><span class="sxs-lookup"><span data-stu-id="f1426-123">(Optional) The text is not automatically formatted as a link.</span></span> <span data-ttu-id="f1426-124">如果是文字，則變更文字色彩及效果來指示該文字為連結，將會是很有協助的作法。</span><span class="sxs-lookup"><span data-stu-id="f1426-124">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="f1426-125">例如，在 [功能區] 的 [主資料夾] 索引標籤上設定 **[字型]** 區段，將色彩變更為藍色並加上底線效果。</span><span class="sxs-lookup"><span data-stu-id="f1426-125">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="f1426-126">若要測試連結，請按一下 **[執行]** 預覽報表，然後按一下這個連結設定所在的報表項目。</span><span class="sxs-lookup"><span data-stu-id="f1426-126">To test the link, click **Run** to preview the report, and then click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1426-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1426-127">See Also</span></span>  
 <span data-ttu-id="f1426-128">[互動式排序、檔引導模式及 &#40;報表產生器和 SSRS 的連結&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f1426-128">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f1426-129">建立文件引導模式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f1426-129">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
  
  
