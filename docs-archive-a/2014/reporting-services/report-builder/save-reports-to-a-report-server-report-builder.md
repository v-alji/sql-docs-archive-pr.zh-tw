---
title: 將報表儲存到報表伺服器 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48dfef01-ed8c-4f23-90c3-de67c90a97dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80e35c447593e89d422e72ea31ec6be34c3619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707197"
---
# <a name="save-reports-to-a-report-server-report-builder"></a><span data-ttu-id="e39f8-102">將報表儲存到報表伺服器 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="e39f8-102">Save Reports to a Report Server (Report Builder)</span></span>
  <span data-ttu-id="e39f8-103">在報表產生器中，您可以將報表定義儲存至報表伺服器 (也稱為發行報表)。</span><span class="sxs-lookup"><span data-stu-id="e39f8-103">In Report Builder, you can save a report definition to a report server (also known as publishing a report).</span></span> <span data-ttu-id="e39f8-104">當報表儲存至報表伺服器時，其他使用者就可以檢視此報表。</span><span class="sxs-lookup"><span data-stu-id="e39f8-104">When the report is saved to a report server, other users can view the report.</span></span> <span data-ttu-id="e39f8-105">每當您執行已發行的報表時，您將會擷取最新的資料。</span><span class="sxs-lookup"><span data-stu-id="e39f8-105">Each time you run the published report, you will retrieve the most current data.</span></span> <span data-ttu-id="e39f8-106">若要儲存已轉譯之報表的靜態複本，請將此報表匯出到另一個檔案格式並儲存起來，或是使用報表記錄功能來儲存已轉譯的報表版本。</span><span class="sxs-lookup"><span data-stu-id="e39f8-106">To save a static copy of a rendered report, export the report to a different file format and save it or use the report history feature to save versions of rendered reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e39f8-107">儲存報表定義的位置不會影響當您預覽報表時，報表是在伺服器上處理或在本機處理。</span><span class="sxs-lookup"><span data-stu-id="e39f8-107">The location of the saved report definition does not affect whether the report is processed on the server or processed locally when you preview the report.</span></span>  
  
### <a name="to-save-a-report-to-a-report-server"></a><span data-ttu-id="e39f8-108">若要將報表儲存到報表伺服器</span><span class="sxs-lookup"><span data-stu-id="e39f8-108">To save a report to a report server</span></span>  
  
1.  <span data-ttu-id="e39f8-109">在報表產生器的按鈕中，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="e39f8-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="e39f8-110">[**另存**新檔 _\<Report Item\>_ ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e39f8-110">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e39f8-111">如果您重新儲存報表，報表會自動重新儲存到之前的位置。</span><span class="sxs-lookup"><span data-stu-id="e39f8-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="e39f8-112">使用 [另存新檔] 選項可變更位置。</span><span class="sxs-lookup"><span data-stu-id="e39f8-112">Use the Save As option to change location.</span></span>  
  
2.  <span data-ttu-id="e39f8-113">您也可以選擇按一下 **[最近使用的網站和伺服器]** 來顯示最近使用過的報表伺服器和 SharePoint 網站清單。</span><span class="sxs-lookup"><span data-stu-id="e39f8-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="e39f8-114">瀏覽至您想要儲存報表的報表伺服器位置。</span><span class="sxs-lookup"><span data-stu-id="e39f8-114">Browse to the report server location where you want to save the report.</span></span>  
  
4.  <span data-ttu-id="e39f8-115">在 **[名稱]** 中，輸入報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e39f8-115">In **Name**, type the name of the report.</span></span>  
  
5.  <span data-ttu-id="e39f8-116">在 **[下列類型的項目]** 中，選取您要儲存的報表項目類型。</span><span class="sxs-lookup"><span data-stu-id="e39f8-116">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="e39f8-117">報表的類型為報表 (\*.rdl)。</span><span class="sxs-lookup"><span data-stu-id="e39f8-117">The type for reports is Reports(\*.rdl).</span></span>  
  
### <a name="to-save-a-report-as-a-different-name"></a><span data-ttu-id="e39f8-118">若要將報表儲存成不同的名稱</span><span class="sxs-lookup"><span data-stu-id="e39f8-118">To save a report as a different name</span></span>  
  
1.  <span data-ttu-id="e39f8-119">在 [報表產生器] 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="e39f8-119">From the Report Builder button, click **Save As**.</span></span> <span data-ttu-id="e39f8-120">[**另存**新檔 _\<Report Item\>_ ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e39f8-120">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e39f8-121">瀏覽至報表伺服器位置，或您想要儲存報表的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="e39f8-121">Browse to the report server location or to the file share where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="e39f8-122">在 **[名稱]** 中，輸入報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e39f8-122">In **Name**, type the name of the report.</span></span>  
  
4.  <span data-ttu-id="e39f8-123">在 **[下列類型的項目]** 中，選取您要儲存的報表項目類型。</span><span class="sxs-lookup"><span data-stu-id="e39f8-123">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="e39f8-124">報表的類型為報表 (\*.rdl)。</span><span class="sxs-lookup"><span data-stu-id="e39f8-124">The type for reports is Reports(\*.rdl).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39f8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e39f8-125">See Also</span></span>  
 <span data-ttu-id="e39f8-126">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e39f8-126">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e39f8-127">[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e39f8-127">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e39f8-128">[將報表儲存 &#40;報表產生器&#41;](saving-reports-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e39f8-128">[Saving Reports &#40;Report Builder&#41;](saving-reports-report-builder.md) </span></span>  
 [<span data-ttu-id="e39f8-129">將報表匯出為其他檔案類型 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="e39f8-129">Export a Report as Another File Type &#40;Report Builder and SSRS&#41;</span></span>](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)  
  
  
