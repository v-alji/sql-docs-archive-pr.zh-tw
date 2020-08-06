---
title: 使用 URL 存取匯出報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69f340855e37ffde49aec0af096c094a142659d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686843"
---
# <a name="export-a-report-using-url-access"></a><span data-ttu-id="0b712-102">使用 URL 存取匯出報表</span><span class="sxs-lookup"><span data-stu-id="0b712-102">Export a Report Using URL Access</span></span>
  <span data-ttu-id="0b712-103">您可以使用*rs： format*參數，選擇性地指定用來轉譯報表的格式。</span><span class="sxs-lookup"><span data-stu-id="0b712-103">You can optionally specify the format in which to render a report by using the *rs:Format* parameter.</span></span> <span data-ttu-id="0b712-104">例如，直接從原生模式報表伺服器取得報表的 PDF 副本。</span><span class="sxs-lookup"><span data-stu-id="0b712-104">For example, to get a PDF copy of a report directly from a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 <span data-ttu-id="0b712-105">以及，從 SharePoint 整合模式報表伺服器：</span><span class="sxs-lookup"><span data-stu-id="0b712-105">And, from a SharePoint integrated mode report server:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 <span data-ttu-id="0b712-106">這個參數的有效值是以安裝在正在存取之報表伺服器上的報表轉譯延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="0b712-106">Valid values for this parameter are based on the report rendering extensions that are installed on the report server being accessed.</span></span> <span data-ttu-id="0b712-107">常見的延伸模組為 HTML4.0、MHTML、IMAGE、EXCEL、WORD、CSV、PDF、XML 及 NULL。</span><span class="sxs-lookup"><span data-stu-id="0b712-107">Common extensions are HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML, and NULL.</span></span> <span data-ttu-id="0b712-108">如果報表伺服器上未安裝指定的轉譯延伸模組，則報表不會轉譯，且錯誤會產生並顯示在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="0b712-108">If a specified rendering extension is not installed on the report server, the report is not rendered and an error is generated and displayed in the browser.</span></span>  
  
 <span data-ttu-id="0b712-109">如果您未將 *Format* 參數包含為 URL 的一部分，則報表伺服器會偵測瀏覽器，並以適當的 HTML 格式轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="0b712-109">If you do not include the *Format* parameter as part of the URL, the report server detects the browser and renders the report in the appropriate HTML format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b712-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b712-110">See Also</span></span>  
 <span data-ttu-id="0b712-111">[&#40;SSRS&#41;的 URL 存取](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0b712-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="0b712-112">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="0b712-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
