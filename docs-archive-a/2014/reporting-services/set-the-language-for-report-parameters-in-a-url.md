---
title: 在 URL 中設定報表參數的語言 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8087a181906517bb60d4cd6839eed0681f52a5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700759"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a><span data-ttu-id="74bf2-102">設定 URL 中報表參數的語言</span><span class="sxs-lookup"><span data-stu-id="74bf2-102">Set the Language for Report Parameters in a URL</span></span>
  <span data-ttu-id="74bf2-103">*rs:ParameterLanguage* URL 存取參數會緩和問題，其中區分文化特性的報表參數 (例如、日期、時間、貨幣和數字) 會使用瀏覽器語言進行解譯。</span><span class="sxs-lookup"><span data-stu-id="74bf2-103">The *rs:ParameterLanguage* URL access parameter alleviates a problem in which culture-sensitive report parameters, such as dates, times, currency, and numbers, are interpreted using the browser language.</span></span> <span data-ttu-id="74bf2-104">透過 *rs:ParameterLanguage*，現在可以獨立於瀏覽器之外解譯 URL。</span><span class="sxs-lookup"><span data-stu-id="74bf2-104">With *rs:ParameterLanguage*, the URL is now interpreted independently of the browser.</span></span> <span data-ttu-id="74bf2-105">例如，如果將報表伺服器設定為德文的區域設定，但是使用者是透過使用設定為英文 (美國) 的瀏覽器之 URL 來存取報表，則傳遞到報表伺服器的參數值將會被誤解。</span><span class="sxs-lookup"><span data-stu-id="74bf2-105">For example, if the report server is set to a regional setting of German, but a user is accessing a report via a URL using a browser that is set to English-United States, parameter values that are passed to a report server will be misinterpreted.</span></span>  
  
 <span data-ttu-id="74bf2-106">請考慮下列存取報表的 URL：</span><span class="sxs-lookup"><span data-stu-id="74bf2-106">Consider the following URL to a report:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 <span data-ttu-id="74bf2-107">在上述情況中，在 "de-de" 的文化特性之下執行的伺服器，會透過電子郵件訂閱或是超連結產生 URL。</span><span class="sxs-lookup"><span data-stu-id="74bf2-107">In the above case, the server, running under a culture of "de-de", generates a URL either through an e-mail subscription or a hyperlink.</span></span> <span data-ttu-id="74bf2-108">超連結指出報表應該根據德文的日期/時間標準，以 2008 年 10 月 4 日的開始日期與 2008 年 10 月 11 日的結束日期來參數化。</span><span class="sxs-lookup"><span data-stu-id="74bf2-108">The hyperlink indicates that the report should be parameterized by a start date of October 4, 2008 and an end date of October 11, 2008 according to German date/time standards.</span></span> <span data-ttu-id="74bf2-109">不過，透過設定為 "en-us" 的瀏覽器來存取 URL 的使用者，會強制伺服器在美國英文日期/時間的標準之下，將值解譯為 2008 年 4 月 10 日與 2008 年 11 月 10 日。</span><span class="sxs-lookup"><span data-stu-id="74bf2-109">However, a user that is accessing the URL through a browser set to "en-us" forces the server to interpret the values as April 10, 2008 and November 10, 2008 under United States English date/time standards.</span></span> <span data-ttu-id="74bf2-110">若要修正問題， *rs:ParameterLanguage* 可用以覆寫用於參數解譯的瀏覽器語言：</span><span class="sxs-lookup"><span data-stu-id="74bf2-110">To fix the problem, *rs:ParameterLanguage* can be used to override the browser language for parameter interpretation:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 <span data-ttu-id="74bf2-111">除了 URL 存取參數 **rc:Parameters** 的 **true** 和 *false*值之外，您現在可以傳遞 **Collapsed**的值。</span><span class="sxs-lookup"><span data-stu-id="74bf2-111">In addition to a value of **true** and **false** for the URL access parameter *rc:Parameters*, you can now pass a value of **Collapsed**.</span></span> <span data-ttu-id="74bf2-112">在 URL 上使用 *rc:Parameters*=**Collapsed** 時，會摺疊 HTML 檢視器的參數提示區域使其看不到，但是使用者仍然可以切換它。</span><span class="sxs-lookup"><span data-stu-id="74bf2-112">When using *rc:Parameters*=**Collapsed** on a URL, the parameter prompt area of the HTML viewer is collapsed out of sight, but can still be toggled by the user.</span></span> <span data-ttu-id="74bf2-113">值為 **false** 時，會從 HTML 檢視器工具列移除參數提示區域，並使其無法供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="74bf2-113">A value of **false** removes the parameter prompt area from the HTML viewer toolbar and makes it unavailable to the end-user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bf2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74bf2-114">See Also</span></span>  
 <span data-ttu-id="74bf2-115">[URL 存取 &#40;SSRS&#41;](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="74bf2-115">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="74bf2-116">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="74bf2-116">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
