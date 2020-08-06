---
title: 瀏覽報表組件及設定預設資料夾 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6605a23732799ec07b3dbe8481e88c91b18ebe5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592451"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a><span data-ttu-id="b3a93-102">瀏覽報表組件及設定預設資料夾 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b3a93-102">Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b3a93-103">建立報表最簡單的方式，就是從報表組件庫將現有的報表組件 (如資料表和圖表) 加入到您的報表。</span><span class="sxs-lookup"><span data-stu-id="b3a93-103">The easiest way to create a report is to add existing report parts, such as tables and charts, to your report from the Report Part Gallery.</span></span> <span data-ttu-id="b3a93-104">當您將報表組件加入到報表時，您也會加入此組件運作所必須擁有的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b3a93-104">When you add a report part to your report, you are also adding everything it must have to work.</span></span> <span data-ttu-id="b3a93-105">例如，顯示資料的所有報表組件都取決於資料集，也就是資料來源的查詢和連接。</span><span class="sxs-lookup"><span data-stu-id="b3a93-105">For example, any report part that displays data depends on a dataset, that is, a query and a connection to a data source.</span></span> <span data-ttu-id="b3a93-106">當您將報表組件加入至報表之後，您可以盡量修改它。</span><span class="sxs-lookup"><span data-stu-id="b3a93-106">After you add the report part to your report, you can modify it as much as you need.</span></span>  
  
 <span data-ttu-id="b3a93-107">您可以設定預設資料夾，以便將報表組件發行到報表伺服器或與報表伺服器整合的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="b3a93-107">You can set a default folder to publish report parts to the report server or SharePoint site integrated with a report server.</span></span>  
  
 <span data-ttu-id="b3a93-108">如需詳細資訊，請參閱 [報表組件 &#40;報表產生器及 SSRS&#41;](../report-parts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b3a93-108">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-browse-for-report-parts"></a><span data-ttu-id="b3a93-109">若要瀏覽報表組件</span><span class="sxs-lookup"><span data-stu-id="b3a93-109">To browse for report parts</span></span>  
  
1.  <span data-ttu-id="b3a93-110">在 [插入]  功能表上，按一下 [報表組件]  。</span><span class="sxs-lookup"><span data-stu-id="b3a93-110">On the **Insert** menu, click **Report Parts**.</span></span>  
  
     <span data-ttu-id="b3a93-111">如果您尚未連線，請按一下 [連線到報表伺服器]  ，並輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="b3a93-111">If you are not already connected, click **Connect to a report server**, and enter the name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b3a93-112">您必須連接到報表伺服器，才能瀏覽報表組件。</span><span class="sxs-lookup"><span data-stu-id="b3a93-112">You must be connected to a report server to browse for report parts.</span></span>  
  
2.  <span data-ttu-id="b3a93-113">您可以指定報表組件的詳細資料來縮小搜尋範圍。</span><span class="sxs-lookup"><span data-stu-id="b3a93-113">You can narrow your search by specifying details about the report part.</span></span> <span data-ttu-id="b3a93-114">請在 [搜尋]  方塊中鍵入完整名稱或名稱的一部分和描述，或是按一下 [新增準則]  並針對任何欄位或所有欄位新增值：</span><span class="sxs-lookup"><span data-stu-id="b3a93-114">Type all or part of the name and description in the **Search** box, or click **Add Criteria** and add values for any or all of these fields:</span></span>  
  
    -   <span data-ttu-id="b3a93-115">建立者</span><span class="sxs-lookup"><span data-stu-id="b3a93-115">Created by</span></span>  
  
    -   <span data-ttu-id="b3a93-116">建立日期</span><span class="sxs-lookup"><span data-stu-id="b3a93-116">Date created</span></span>  
  
    -   <span data-ttu-id="b3a93-117">上次修改日期</span><span class="sxs-lookup"><span data-stu-id="b3a93-117">Date last modified</span></span>  
  
    -   <span data-ttu-id="b3a93-118">上次修改者</span><span class="sxs-lookup"><span data-stu-id="b3a93-118">Last modified by</span></span>  
  
    -   <span data-ttu-id="b3a93-119">伺服器資料夾</span><span class="sxs-lookup"><span data-stu-id="b3a93-119">Server folder</span></span>  
  
    -   <span data-ttu-id="b3a93-120">類型</span><span class="sxs-lookup"><span data-stu-id="b3a93-120">Type</span></span>  
  
     <span data-ttu-id="b3a93-121">例如，若要尋找影像，請按一下 [新增準則]  ，然後按一下 [類型]  。</span><span class="sxs-lookup"><span data-stu-id="b3a93-121">For example, to find an image, click **Add Criteria**, and then click **Type**.</span></span> <span data-ttu-id="b3a93-122">在下拉式方塊中，選取 [影像]  核取方塊，按 ENTER ，然後按一下「搜尋」放大鏡。</span><span class="sxs-lookup"><span data-stu-id="b3a93-122">In the dropdown box, select the **Image** check box, press ENTER, and then click the Search magnifying glass.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b3a93-123">針對 [建立者]  和 [上次修改者]  值，搜尋此人員在報表伺服器上所代表的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b3a93-123">For the **Created by** and **Last modified by** values, search for the person's user name as it is represented on the report server.</span></span>  
  
### <a name="to-set-a-default-folder-for-report-parts"></a><span data-ttu-id="b3a93-124">若要設定報表組件的預設資料夾</span><span class="sxs-lookup"><span data-stu-id="b3a93-124">To set a default folder for report parts</span></span>  
  
1.  <span data-ttu-id="b3a93-125">按一下 [報表產生器]  ，然後按一下 [選項]  。</span><span class="sxs-lookup"><span data-stu-id="b3a93-125">Click **Report Builder**, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="b3a93-126">在 [選項]  對話方塊的 [設定]  索引標籤上，於 [將報表組件預設發行到此資料夾]  文字方塊中鍵入資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b3a93-126">In the **Options** dialog box, on the **Settings** tab, type a folder name in the **Publish report parts to this folder by default** textbox.</span></span>  
  
 <span data-ttu-id="b3a93-127">如果此資料夾尚未存在，而且您有權在報表伺服器上建立資料夾，報表產生器將會建立這個資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3a93-127">Report Builder will create this folder if you have permissions to create folders on the report server and the folder does not exist yet.</span></span>  
  
 <span data-ttu-id="b3a93-128">您不需要重新啟動報表產生器，這項設定也會生效。</span><span class="sxs-lookup"><span data-stu-id="b3a93-128">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a93-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3a93-129">See Also</span></span>  
 <span data-ttu-id="b3a93-130">[檢查是否有更新，或關閉 &#40;報表產生器和 SSRS 的更新&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b3a93-130">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b3a93-131">[報表組件 &#40;報表產生器及 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b3a93-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b3a93-132">[報表產生器中的報表組件和資料集](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b3a93-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="b3a93-133">[&#40;報表產生器和 SSRS&#41;疑難排解報表元件](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b3a93-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b3a93-134">發行與重新發行報表組件 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b3a93-134">Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;</span></span>](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
