---
title: 轉譯資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a458fdf9-fb2a-4fee-9fbd-b38f36e91753
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc2757d308529c8b5a03e206a827fce7028edbfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704898"
---
# <a name="rendering-data-report-builder-and-ssrs"></a><span data-ttu-id="42ee6-102">轉譯資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="42ee6-102">Rendering Data (Report Builder and SSRS)</span></span>
  <span data-ttu-id="42ee6-103">使用配置轉譯器 (例如 HTML、MHTML、Word、Excel、PDF 或影像) 時，資料及其組織會保持不變。</span><span class="sxs-lookup"><span data-stu-id="42ee6-103">When using layout renderers, such as HTML, MHTML, Word, Excel, PDF or Image, the data and its organization remains unchanged.</span></span> <span data-ttu-id="42ee6-104">使用資料轉譯器格式 (例如，逗號分隔值 (CSV) 或 XML) 匯出時，不會轉譯任何視覺化配置元素。</span><span class="sxs-lookup"><span data-stu-id="42ee6-104">When exporting using a data renderer format, such as Comma-Separated Value (CSV) or XML, no visual layout elements are rendered.</span></span> <span data-ttu-id="42ee6-105">轉譯報表時，CSV 和 XML 會將某些規則套用到報表主體及其內容。</span><span class="sxs-lookup"><span data-stu-id="42ee6-105">CSV and XML apply certain rules to the report body and its contents when rendering the report.</span></span> <span data-ttu-id="42ee6-106">這些規則決定了如何以這些格式轉譯資料。</span><span class="sxs-lookup"><span data-stu-id="42ee6-106">These rules determine how the data is rendered in these formats.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="42ee6-107">您可以使用資料轉譯器：</span><span class="sxs-lookup"><span data-stu-id="42ee6-107">You can use data renderers to:</span></span>  
  
-   <span data-ttu-id="42ee6-108">匯入到資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ee6-108">Import to a database.</span></span> <span data-ttu-id="42ee6-109">CSV 是種常見的格式，能夠利用多種資料庫應用程式輕鬆匯入，包括 SQL Server 和 Microsoft Access。</span><span class="sxs-lookup"><span data-stu-id="42ee6-109">CSV is a common format that is easily importable by many database applications including SQL Server and Microsoft Access.</span></span>  
  
-   <span data-ttu-id="42ee6-110">匯入到 Excel。</span><span class="sxs-lookup"><span data-stu-id="42ee6-110">Import to Excel.</span></span> <span data-ttu-id="42ee6-111">使用 CSV 轉譯器，將您的資料匯出到沒有視覺化配置的 Excel。</span><span class="sxs-lookup"><span data-stu-id="42ee6-111">Use the CSV renderer to export your data to Excel without the visual layout.</span></span> <span data-ttu-id="42ee6-112">在您的資料匯到 Excel 後，您就可以使用 Excel 的標準工具，例如，圖表、公式以及樞紐資料表。</span><span class="sxs-lookup"><span data-stu-id="42ee6-112">After your data is in Excel, you can take advantage of standard Excel tools such as charts, formulas, and pivot tables.</span></span>  
  
-   <span data-ttu-id="42ee6-113">XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="42ee6-113">XSLT transformations.</span></span> <span data-ttu-id="42ee6-114">XSLT 可以套用到 XML 轉譯器的輸出。</span><span class="sxs-lookup"><span data-stu-id="42ee6-114">An XSLT can be applied to the output of the XML renderer.</span></span> <span data-ttu-id="42ee6-115">這個伺服器端的轉換是一種非常強大的技術，可以將您的資料實際上轉換為任何格式。</span><span class="sxs-lookup"><span data-stu-id="42ee6-115">This server-side transformation is a powerful technique to transform your data to virtually any format.</span></span>  
  
-   <span data-ttu-id="42ee6-116">資料交換/EDI。</span><span class="sxs-lookup"><span data-stu-id="42ee6-116">Data exchange/EDI.</span></span> <span data-ttu-id="42ee6-117">這是一種外部程序，可以要求報表進行 CSV 或 XML 轉譯，並取用該資料。</span><span class="sxs-lookup"><span data-stu-id="42ee6-117">An external process can request a CSV or XML rendering of a report and consume that data.</span></span>  
  
 <span data-ttu-id="42ee6-118">資料轉譯器格式是由一組不同於配置轉譯器的屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="42ee6-118">Data renderer formats are controlled by a different set of properties than layout renderers.</span></span> <span data-ttu-id="42ee6-119">下列是在 [屬性]  窗格中設定的屬性清單，這些屬性僅適用於資料轉譯器：</span><span class="sxs-lookup"><span data-stu-id="42ee6-119">The following is a list of properties set in the **Properties** pane that apply only to data renderers:</span></span>  
  
-   <span data-ttu-id="42ee6-120">DataElementOutput 屬性控制匯出時是否要在資料中顯示特定的項目。</span><span class="sxs-lookup"><span data-stu-id="42ee6-120">The DataElementOutput property controls whether or not a specific item is present in the data when exported.</span></span>  
  
-   <span data-ttu-id="42ee6-121">DataElementName 屬性控制資料元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="42ee6-121">The DataElementName property controls the name of the data element.</span></span> <span data-ttu-id="42ee6-122">在 CSV 中，這個屬性控制 CSV 資料行標頭的名稱。</span><span class="sxs-lookup"><span data-stu-id="42ee6-122">In CSV, this controls the name of the CSV column header.</span></span> <span data-ttu-id="42ee6-123">在 XML 中，這個屬性則會變成 XML 元素的名稱或項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="42ee6-123">In XML, this becomes the name of the XML element or attribute for the item.</span></span>  
  
-   <span data-ttu-id="42ee6-124">DataElementStyle 屬性控制報表項目在 XML 中是否要轉譯為元素或屬性。</span><span class="sxs-lookup"><span data-stu-id="42ee6-124">The DataElementStyle property controls, in XML, whether or not the report item is rendered as an element or an attribute.</span></span>  
  
 <span data-ttu-id="42ee6-125">CSV 匯出選項會將報表資料儲存為逗號分隔的純文字檔案，沒有任何格式。</span><span class="sxs-lookup"><span data-stu-id="42ee6-125">The CSV export option saves report data as comma-delimited plain text files, without any formatting.</span></span> <span data-ttu-id="42ee6-126">根據預設，此檔案使用逗號 (,) 來分隔欄位與資料列，但是此設定可以使用 [裝置資訊設定] 設定。</span><span class="sxs-lookup"><span data-stu-id="42ee6-126">By default, the file uses a comma (,) to delimit fields and rows but this setting is configurable using the Device Information Settings.</span></span> <span data-ttu-id="42ee6-127">產生的檔案可以使用試算表程式 (例如 Office SharePoint Server) 開啟，或用來當做其他程式的匯入格式。</span><span class="sxs-lookup"><span data-stu-id="42ee6-127">The resulting file can be opened in a spreadsheet program like Office SharePoint Server or used as an import format for other programs.</span></span> <span data-ttu-id="42ee6-128">.csv 檔案可以使用文字編輯器 (例如 [記事本]) 開啟。</span><span class="sxs-lookup"><span data-stu-id="42ee6-128">The .csv file opens in a text editor such as Notepad.</span></span> <span data-ttu-id="42ee6-129">如果以 URL 存取，則 .csv 檔案會傳回 **text/csv**類型的 MIME。</span><span class="sxs-lookup"><span data-stu-id="42ee6-129">If accessed as a URL, the .csv file returns a MIME type of **text/csv**.</span></span> <span data-ttu-id="42ee6-130">檔案的 MIME 版本為 1.0。</span><span class="sxs-lookup"><span data-stu-id="42ee6-130">The files are MIME version 1.0.</span></span> <span data-ttu-id="42ee6-131">如需以 CSV 檔案類型轉譯報表的詳細資訊，請參閱[匯出至 CSV 檔案 &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="42ee6-131">For more information about rendering your report in the CSV file type, see [Exporting to a CSV File &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="42ee6-132">具有報表資料的 XML 檔案匯出選項會將報表儲存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="42ee6-132">The XML file with report data export option saves a report as an XML file.</span></span> <span data-ttu-id="42ee6-133">報表的 XML 結構描述為報表特有的。</span><span class="sxs-lookup"><span data-stu-id="42ee6-133">The XML schema for the report is specific to the report.</span></span> <span data-ttu-id="42ee6-134">XML 匯出選項不會儲存報表配置資訊。</span><span class="sxs-lookup"><span data-stu-id="42ee6-134">The report layout information is not saved by the XML export option.</span></span> <span data-ttu-id="42ee6-135">使用此選項產生的 XML 可以匯入資料庫 (當做 XML 資料訊息)，或傳送到自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="42ee6-135">The XML generated using this option can be imported into a database, used as an XML data message, or sent to a custom application.</span></span> <span data-ttu-id="42ee6-136">如需以 XML 檔案類型轉譯報表的詳細資訊，請參閱[匯出至 XML &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-xml-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="42ee6-136">For more information about rendering your report in the XML file type, see [Exporting to XML &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-xml-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ee6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42ee6-137">See Also</span></span>  
 <span data-ttu-id="42ee6-138">[Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42ee6-138">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="42ee6-139">[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42ee6-139">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="42ee6-140">[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器及 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="42ee6-140">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="42ee6-141">[轉譯報表項目 &#40;報表產生器及 SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42ee6-141">[Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="42ee6-142">[列出 &#40;報表產生器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42ee6-142">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="42ee6-143">Reporting Services 裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="42ee6-143">Reporting Services Device Information Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=102515)  
  
  
