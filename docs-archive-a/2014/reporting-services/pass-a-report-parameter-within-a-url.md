---
title: 在 URL 內傳遞報表參數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf41ed82728d5d7c840276e135937b08f83fb131
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707253"
---
# <a name="pass-a-report-parameter-within-a-url"></a><span data-ttu-id="991a9-102">在 URL 內傳遞報表參數</span><span class="sxs-lookup"><span data-stu-id="991a9-102">Pass a Report Parameter Within a URL</span></span>
  <span data-ttu-id="991a9-103">您可以在報表 URL 中包括報表參數，以便將它們傳遞給報表。</span><span class="sxs-lookup"><span data-stu-id="991a9-103">You can pass report parameters to a report by including them in a report URL.</span></span> <span data-ttu-id="991a9-104">這些 URL 參數不會加上前置詞，因為它們會直接傳遞給報表處理引擎。</span><span class="sxs-lookup"><span data-stu-id="991a9-104">These URL parameters are not prefixed because they are passed directly to the report processing engine.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="991a9-105">請務必讓 URL 包含 `_vti_bin` Proxy 語法，以便透過 SharePoint 和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP Proxy 路由傳送要求。</span><span class="sxs-lookup"><span data-stu-id="991a9-105">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="991a9-106">此 Proxy 會將某些內容加入至 HTTP 要求，也就是確保針對 SharePoint 模式報表伺服器正確執行報表所需的內容。</span><span class="sxs-lookup"><span data-stu-id="991a9-106">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
>   
>  <span data-ttu-id="991a9-107">如果您未包含 proxy 語法，則需要在參數前面加上*rp：*。</span><span class="sxs-lookup"><span data-stu-id="991a9-107">If you don't include the proxy syntax, then you need to prefix the parameter with *rp:*.</span></span>  
  
 <span data-ttu-id="991a9-108">所有查詢參數都可以有相對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="991a9-108">All query parameters can have corresponding report parameters.</span></span> <span data-ttu-id="991a9-109">您可以傳遞相對應的報表參數，即可傳遞查詢參數。</span><span class="sxs-lookup"><span data-stu-id="991a9-109">You pass a query parameter to a report by passing the corresponding report parameter.</span></span> <span data-ttu-id="991a9-110">如需詳細資訊，請參閱[在關聯式查詢設計工具中建立查詢 &#40;報表產生器和 SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="991a9-110">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="991a9-111">報表參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="991a9-111">Report parameters are case-sensitive.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="991a9-112">報表參數會區分大小寫，而且使用下列特殊字元：</span><span class="sxs-lookup"><span data-stu-id="991a9-112">Report parameters are case-sensitive and utilize the following special characters:</span></span>  
> 
>  -   <span data-ttu-id="991a9-113">根據 URL 編碼標準，在 URL 字串中的任何空格字元都會使用字元 "%20" 來取代。</span><span class="sxs-lookup"><span data-stu-id="991a9-113">Any space characters in the URL string are replaced with the characters "%20," according to URL encoding standards.</span></span>  
> -   <span data-ttu-id="991a9-114">URL 參數部分中的空格字元會取代成加號字元 (+)。</span><span class="sxs-lookup"><span data-stu-id="991a9-114">A space character in the parameter portion of the URL is replaced with a plus character (+).</span></span>  
> -   <span data-ttu-id="991a9-115">任何字串部分中的分號都會取代成 "%3A" 字元。</span><span class="sxs-lookup"><span data-stu-id="991a9-115">A semicolon in any portion of the string is replaced with the characters "%3A."</span></span>  
> -   <span data-ttu-id="991a9-116">瀏覽器應該會自動執行正確的 URL 編碼。</span><span class="sxs-lookup"><span data-stu-id="991a9-116">Browsers should automatically perform the proper URL encoding.</span></span> <span data-ttu-id="991a9-117">您不必手動編碼任何字元。</span><span class="sxs-lookup"><span data-stu-id="991a9-117">You do not have to encode any of the characters manually.</span></span>  
  
 <span data-ttu-id="991a9-118">若要設定 URL 內的報表參數，請使用以下語法：</span><span class="sxs-lookup"><span data-stu-id="991a9-118">To set a report parameter within a URL, use the following syntax:</span></span>  
  
```  
  
parameter=value  
```  
  
 <span data-ttu-id="991a9-119">例如，若要指定兩個定義在報表中的參數 ("ReportMonth" 和 'ReportYear")，請使用下列原生模式報表伺服器的 URL：</span><span class="sxs-lookup"><span data-stu-id="991a9-119">For example, to specify two parameters, "ReportMonth" and "ReportYear", defined in a report, use the following URL for a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="991a9-120">例如，若要指定定義在報表中的兩個相同參數，請將下列 URL 用於 SharePoint 整合模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="991a9-120">For example, to specify the same two parameters defined in a report, use the following URL for a SharePoint integrated mode report server.</span></span> <span data-ttu-id="991a9-121">請注意 `/_vti_bin`：</span><span class="sxs-lookup"><span data-stu-id="991a9-121">Note the `/_vti_bin`:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="991a9-122">若要為參數傳遞 Null 值，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="991a9-122">To pass a null value for a parameter, use the following syntax:</span></span>  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 <span data-ttu-id="991a9-123">例如</span><span class="sxs-lookup"><span data-stu-id="991a9-123">For example,</span></span>  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 <span data-ttu-id="991a9-124">若要傳遞 `Boolean` 值，請使用 0 表示 False，使用 1 表示 True。</span><span class="sxs-lookup"><span data-stu-id="991a9-124">To pass a `Boolean` value, use 0 for false and 1 for true.</span></span> <span data-ttu-id="991a9-125">若要傳遞 `Float` 值，請包含伺服器地區設定的小數分隔符號</span><span class="sxs-lookup"><span data-stu-id="991a9-125">To pass a `Float` value, include the decimal separator of the server locale</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="991a9-126">如果報表中包含具有預設值的報表參數，而且 `Prompt` 屬性的值是 `false` (也就是在報表管理員中未選取 [提示使用者] 屬性)，則您無法在 URL 內傳遞該報表參數的值。</span><span class="sxs-lookup"><span data-stu-id="991a9-126">If your report contains a report parameter that has a default value and the value of the `Prompt` property is `false` (that is, the Prompt User property is not selected in Report Manager), then you cannot pass a value for that report parameter within a URL.</span></span> <span data-ttu-id="991a9-127">這可讓管理員選擇防止使用者加入或修改某些報表參數值。</span><span class="sxs-lookup"><span data-stu-id="991a9-127">This provides administrators an option for preventing end users from adding or modifying the values of certain report parameters.</span></span>  
  
##  <a name="additional-examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="991a9-128">其他範例</span><span class="sxs-lookup"><span data-stu-id="991a9-128">Additional Examples</span></span>  
 <span data-ttu-id="991a9-129">下列 URL 範例包含空格和多個參數。</span><span class="sxs-lookup"><span data-stu-id="991a9-129">The following URL example includes spaces and multiple parameters</span></span>  
  
-   <span data-ttu-id="991a9-130">資料夾名稱 "SQL Server User Education Team" 包含空格，因此 "+" 會取代每個空格。</span><span class="sxs-lookup"><span data-stu-id="991a9-130">Folder name of "SQL Server User Education Team" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="991a9-131">"team project report" 的報表名稱包含空格，因此 "+" 會取代每個空格。</span><span class="sxs-lookup"><span data-stu-id="991a9-131">Report name of "team project report" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="991a9-132">傳遞兩個參數："teamgrouping2" 的值為 "xgroup"，"teamgrouping1" 的值為 "ygroup"。</span><span class="sxs-lookup"><span data-stu-id="991a9-132">Passes two parameters of "teamgrouping2" with a value of "xgroup" and "teamgrouping1" with a value of "ygroup".</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 <span data-ttu-id="991a9-133">下列 URL 範例包含多值參數 "OrderID"。</span><span class="sxs-lookup"><span data-stu-id="991a9-133">The following URL example includes a multi-value parameter "OrderID.</span></span> <span data-ttu-id="991a9-134">多值參數的格式是針對每個值重複參數名稱。</span><span class="sxs-lookup"><span data-stu-id="991a9-134">The format for a Multi-Value parameter is to repeat the parameter name for each value.</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 <span data-ttu-id="991a9-135">下列 URL 範例會針對原生模式報表伺服器，傳遞值為 "7/1/2005" 的單一參數*SellStartDate* 。</span><span class="sxs-lookup"><span data-stu-id="991a9-135">The following URL example passes a single parameter of *SellStartDate* with a value of "7/1/2005", for a native mode report server.</span></span>  
  
```  
http://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a><span data-ttu-id="991a9-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="991a9-136">See Also</span></span>  
 <span data-ttu-id="991a9-137">[&#40;SSRS&#41;的 URL 存取](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="991a9-137">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="991a9-138">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="991a9-138">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
