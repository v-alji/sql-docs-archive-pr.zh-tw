---
title: 從報表產生資料摘要 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340191396aaaa92fe14fe8c3c6b42539a713eb45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585106"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a><span data-ttu-id="7c008-102">從報表產生資料摘要 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7c008-102">Generate Data Feeds from a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7c008-103">您可以從報表產生符合 Atom 的資料摘要，然後在可取用資料摘要的應用程式（例如 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 用戶端）中使用資料摘要。</span><span class="sxs-lookup"><span data-stu-id="7c008-103">You can generate Atom-compliant data feeds from reports, and then use the data feeds in applications, such as the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client, that can consume data feeds.</span></span>  
  
 <span data-ttu-id="7c008-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom 轉譯延伸模組會產生 Atom 服務文件，其中會列出可從報表取得的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="7c008-104">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report.</span></span> <span data-ttu-id="7c008-105">此文件至少會列出報表中每個資料區的一個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="7c008-105">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="7c008-106">根據資料區的類型以及該資料區顯示的資料， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可能會產生來自某個資料區的多個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="7c008-106">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span>  
  
 <span data-ttu-id="7c008-107">Atom 服務文件會針對每個資料摘要包含一個唯一的識別碼，而您可以在 URL 中使用該識別碼來檢視資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="7c008-107">Atom service document contains a unique identifier for each the data feed and you use the identifier in a URL to view the content of the data feed.</span></span>  
  
 <span data-ttu-id="7c008-108">如需詳細資訊，請參閱 [從多個報表產生資料摘要 &#40;報表產生器及 SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)中使用這項資料。</span><span class="sxs-lookup"><span data-stu-id="7c008-108">For more information, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a><span data-ttu-id="7c008-109">若要產生 Atom 服務文件</span><span class="sxs-lookup"><span data-stu-id="7c008-109">To generate an Atom service document</span></span>  
  
1.  <span data-ttu-id="7c008-110">從報表管理員的 **[主資料夾]** 頁面上，導覽至您要從其中產生資料摘要的報表。</span><span class="sxs-lookup"><span data-stu-id="7c008-110">From the Report Manager **Home** page, navigate to the report from which you want to generate data feeds.</span></span>  
  
2.  <span data-ttu-id="7c008-111">按一下報表。</span><span class="sxs-lookup"><span data-stu-id="7c008-111">Click the report.</span></span>  
  
     <span data-ttu-id="7c008-112">報表隨即執行。</span><span class="sxs-lookup"><span data-stu-id="7c008-112">The report is run.</span></span>  
  
3.  <span data-ttu-id="7c008-113">在工具列上，按一下 [匯出至資料摘要] 圖示。</span><span class="sxs-lookup"><span data-stu-id="7c008-113">On the toolbar, click the Export to Data Feed icon.</span></span>  
  
     <span data-ttu-id="7c008-114">此時會出現一個訊息，詢問您要開啟還是儲存包含資料摘要的 Atom 文件。</span><span class="sxs-lookup"><span data-stu-id="7c008-114">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
4.  <span data-ttu-id="7c008-115">按一下 **[儲存]** ，將文件儲存至檔案系統，或按一下 **[開啟]** ，在儲存前檢視文件內容。</span><span class="sxs-lookup"><span data-stu-id="7c008-115">Click **Save** to save the document to the file system, or click **Open** to view the document content before saving.</span></span> <span data-ttu-id="7c008-116">**依預設，文件會在瀏覽器中開啟。**</span><span class="sxs-lookup"><span data-stu-id="7c008-116">**By default, the document opens in a browser.**</span></span>  
  
5.  <span data-ttu-id="7c008-117">瀏覽至要儲存文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7c008-117">Browse to the location to save the document.</span></span>  
  
6.  <span data-ttu-id="7c008-118">您可以選擇變更文件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-118">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c008-119">依預設，文件名稱就是報表名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-119">By default, the document name is the report name.</span></span>  
  
7.  <span data-ttu-id="7c008-120">確認文件類型為 **[ATOMSVC 檔]**，然後按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="7c008-120">Verify the document type is **ATOMSVC File**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="7c008-121">或者，在瀏覽器或者文字或 XML 編輯器中開啟 .atomsvc 檔。</span><span class="sxs-lookup"><span data-stu-id="7c008-121">Optionally, open the .atomsvc file in a browser or text or XML editor.</span></span>  
  
### <a name="to-view-an-atom-compliant-data-feed"></a><span data-ttu-id="7c008-122">若要檢視符合 Atom 的資料摘要</span><span class="sxs-lookup"><span data-stu-id="7c008-122">To view an Atom-compliant data feed</span></span>  
  
1.  <span data-ttu-id="7c008-123">如果尚未開啟 Atom 服務文件，請找出該文件並在瀏覽器 (例如 Internet Explorer) 中開啟。</span><span class="sxs-lookup"><span data-stu-id="7c008-123">If the Atom service document is not already open, locate it and open it in a browser such as Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="7c008-124">將您要檢視的資料摘要 URL 從 Atom 服務文件複製到瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="7c008-124">Copy the URL of the data feed that you want to view from the Atom service document to the browser.</span></span>  
  
     <span data-ttu-id="7c008-125">URL 的格式為：</span><span class="sxs-lookup"><span data-stu-id="7c008-125">The format of the URL is the following:</span></span>  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  <span data-ttu-id="7c008-126">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7c008-126">Press ENTER.</span></span>  
  
     <span data-ttu-id="7c008-127">此時會出現一個訊息，詢問您要開啟還是儲存包含資料摘要的 Atom 文件。</span><span class="sxs-lookup"><span data-stu-id="7c008-127">A message appears asking you if you want to save or open the atom document that contains the data feed.</span></span>  
  
2.  <span data-ttu-id="7c008-128">按一下 **[儲存]** ，將文件儲存至檔案系統，或按一下 **[開啟]** ，在儲存前檢視資料摘要。</span><span class="sxs-lookup"><span data-stu-id="7c008-128">Click **Save** to save the document to the file system, or click **Open** to view the data feed before saving.</span></span>  
  
3.  <span data-ttu-id="7c008-129">瀏覽至要儲存文件的位置。</span><span class="sxs-lookup"><span data-stu-id="7c008-129">Browse to the location to save the document.</span></span>  
  
4.  <span data-ttu-id="7c008-130">您可以選擇變更文件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-130">Optionally, change the name of the document.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c008-131">依預設，文件名稱就是報表名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-131">By default the document name is the report name.</span></span> <span data-ttu-id="7c008-132">如果 Atom 服務文件有多個摘要，預設全部都使用相同的名稱，也就是報表名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-132">If the Atom service document has multiple feeds, by default all use the same name, the report name.</span></span> <span data-ttu-id="7c008-133">若要區別這些摘要，請加以重新命名以使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c008-133">To differentiate them, rename them to use meaningful names.</span></span>  
  
5.  <span data-ttu-id="7c008-134">確認文件類型為 **[ATOM 檔]**，然後按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="7c008-134">Verify the document type is **ATOM File**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="7c008-135">或者，在瀏覽器或者文字編輯器或 XML 編輯器中開啟 .atom 檔。</span><span class="sxs-lookup"><span data-stu-id="7c008-135">Optionally, open the .atom file in a browser or text editor or XML editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c008-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c008-136">See Also</span></span>  
 [<span data-ttu-id="7c008-137">匯出報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7c008-137">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
