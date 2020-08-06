---
title: 指定外部項目的路徑 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 097a3566f914e7810039ee07bc3d3bf3185d7f06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585010"
---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a><span data-ttu-id="314ea-102">指定外部項目的路徑 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="314ea-102">Specifying Paths to External Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="314ea-103">您可以在報表項目屬性中指定路徑，以便參考位於報表定義檔案外部且儲存在報表伺服器上的項目，例如鑽研報表、子報表和影像檔。</span><span class="sxs-lookup"><span data-stu-id="314ea-103">You specify paths in report item properties to reference items such as drillthrough reports, subreports, and image files that are external to the report definition file and are stored on a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="314ea-104">在報表產生器中，項目的路徑必須指定報表伺服器上的項目。</span><span class="sxs-lookup"><span data-stu-id="314ea-104">In Report Builder, paths to items must specify items on a report server.</span></span> <span data-ttu-id="314ea-105">不支援檔案系統上之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="314ea-105">Paths to items on a file system are not supported.</span></span> <span data-ttu-id="314ea-106">只有當您已連接至項目所在的報表伺服器時，才能預覽使用這些項目的報表。</span><span class="sxs-lookup"><span data-stu-id="314ea-106">You can preview a report that uses these items only if you are connected to the report server where the items are located.</span></span>  
  
 <span data-ttu-id="314ea-107">當您在動作、子報表或影像的對話方塊中指定外部項目的路徑時，可以直接瀏覽至報表伺服器並選取此項目。</span><span class="sxs-lookup"><span data-stu-id="314ea-107">When you specify a path for an external item in a dialog box for actions, subreports, or images, you can browse directly to the report server and select the item.</span></span> <span data-ttu-id="314ea-108">直接瀏覽至項目並選取項目是指定鑽研報表或子報表的建議方式。</span><span class="sxs-lookup"><span data-stu-id="314ea-108">Browsing to an item and selecting it directly is the recommended way to specify a drillthrough report or subreport.</span></span> <span data-ttu-id="314ea-109">若使用這種方式，當您指定報表或子報表參數時，下拉式清單就會提供正確的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="314ea-109">That way the correct parameter names will be available in a drop-down list when you specify report or subreport parameters.</span></span> <span data-ttu-id="314ea-110">當您變更項目路徑來指向不同的項目時，則必須視需要手動更新正確的參數名稱和值。</span><span class="sxs-lookup"><span data-stu-id="314ea-110">When you change an item path to point to a different item, you must manually update the correct parameter names and values as needed.</span></span>  
  
 <span data-ttu-id="314ea-111">在設定為原生模式的報表伺服器上，請指定不含副檔名 .rdl 的鑽研報表名稱。</span><span class="sxs-lookup"><span data-stu-id="314ea-111">On a report server configured in native mode, specify a drillthrough report name without the file extension .rdl.</span></span>  
  
 <span data-ttu-id="314ea-112">在設定為 SharePoint 整合模式的報表伺服器上，您必須包含副檔名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="314ea-112">On a report server configured in SharePoint integrated mode, you must include the file extension .rdl.</span></span> <span data-ttu-id="314ea-113">路徑可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="314ea-113">The path can be one of the following:</span></span>  
  
-   <span data-ttu-id="314ea-114">**來自主報表之項目的相對路徑。**</span><span class="sxs-lookup"><span data-stu-id="314ea-114">**A relative path to the item from the main report.**</span></span> <span data-ttu-id="314ea-115">例如 ../AllSubreports/Subreport1。</span><span class="sxs-lookup"><span data-stu-id="314ea-115">For example, ../AllSubreports/Subreport1.</span></span> <span data-ttu-id="314ea-116">在此範例中， **..**</span><span class="sxs-lookup"><span data-stu-id="314ea-116">In this example, the **..**</span></span> <span data-ttu-id="314ea-117">表示主報表所在之資料夾上方的資料夾。</span><span class="sxs-lookup"><span data-stu-id="314ea-117">indicates the folder above the folder where the main report is located.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="314ea-118">在報表產生器內部執行報表時，不支援相對路徑。</span><span class="sxs-lookup"><span data-stu-id="314ea-118">Relative paths are not supported when the report is run inside Report Builder.</span></span> <span data-ttu-id="314ea-119">若要檢視使用外部項目之相對路徑的報表，請將報表儲存至報表伺服器，然後從中執行報表。</span><span class="sxs-lookup"><span data-stu-id="314ea-119">To view a report that uses relative paths to external items, save the report to the report server, and run the report from there</span></span>  
  
-   <span data-ttu-id="314ea-120">**項目的完整路徑。**</span><span class="sxs-lookup"><span data-stu-id="314ea-120">**A full path to the item.**</span></span>  
  
    -   <span data-ttu-id="314ea-121">**在報表伺服器上：** 路徑的開頭是 **/** ，亦即主資料夾。</span><span class="sxs-lookup"><span data-stu-id="314ea-121">**On a report server:** The path starts from **/**, the Home folder.</span></span> <span data-ttu-id="314ea-122">例如 /Reports/AllSubreports/Subreport1。</span><span class="sxs-lookup"><span data-stu-id="314ea-122">For example, /Reports/AllSubreports/Subreport1.</span></span>  
  
    -   <span data-ttu-id="314ea-123">**在 SharePoint 網站上：** 您必須在運算式中指定報表名稱，以及項目的完整 URL 和副檔名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="314ea-123">**On a SharePoint site:** You must specify the report name in an expression, with the full URL of the item and the file extension .rdl.</span></span> <span data-ttu-id="314ea-124">例如： `="http://server/site/library/folder/Report1.rdl"` 。</span><span class="sxs-lookup"><span data-stu-id="314ea-124">For example, `="http://server/site/library/folder/Report1.rdl"`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314ea-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="314ea-125">See Also</span></span>  
 <span data-ttu-id="314ea-126">[加入外部影像 &#40;報表產生器及 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="314ea-126">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="314ea-127">[新增子報表和參數 &#40;報表產生器及 SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="314ea-127">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="314ea-128">在報表上新增鑽研動作 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="314ea-128">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
