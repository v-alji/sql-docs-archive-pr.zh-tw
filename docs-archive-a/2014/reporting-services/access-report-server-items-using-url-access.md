---
title: 使用 URL 存取權存取報表伺服器項目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6693419490c1b3770ccb41b2645cbdba8996630a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597669"
---
# <a name="access-report-server-items-using-url-access"></a><span data-ttu-id="73d53-102">使用 URL 存取權存取報表伺服器項目</span><span class="sxs-lookup"><span data-stu-id="73d53-102">Access Report Server Items Using URL Access</span></span>
  <span data-ttu-id="73d53-103">本主題描述如何使用 *rs:Command*=*Value*，來存取報表伺服器資料庫或 SharePoint 網站中不同類型的目錄項目。</span><span class="sxs-lookup"><span data-stu-id="73d53-103">This topic describes how to access catalog items of different types in a report server data base or in a SharePoint site using *rs:Command*=*Value*.</span></span>  
  
 <span data-ttu-id="73d53-104">您不需要加入此參數字串。</span><span class="sxs-lookup"><span data-stu-id="73d53-104">It is not necessary to add this parameter string.</span></span> <span data-ttu-id="73d53-105">如果您省略此參數字串，報表伺服器會評估項目類型並自動選取適當的參數值。</span><span class="sxs-lookup"><span data-stu-id="73d53-105">If you omit it, the report server evaluates the item type and selects the appropriate parameter value automatically.</span></span> <span data-ttu-id="73d53-106">不過，在 URL 中使用 *rs:Command*=*Value* 字串可改善報表伺服器的效能。</span><span class="sxs-lookup"><span data-stu-id="73d53-106">However, using the *rs:Command*=*Value* string in the URL improves the performance of the report server.</span></span>  
  
 <span data-ttu-id="73d53-107">請注意下列範例中的 `_vti_bin` Proxy 語法。</span><span class="sxs-lookup"><span data-stu-id="73d53-107">Note the `_vti_bin` proxy syntax in the examples below.</span></span> <span data-ttu-id="73d53-108">如需使用 Proxy 語法的詳細資訊，請參閱 [URL 存取參數參考](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="73d53-108">For more information about using the proxy syntax, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="access-a-report"></a><span data-ttu-id="73d53-109">存取報表</span><span class="sxs-lookup"><span data-stu-id="73d53-109">Access a Report</span></span>  
 <span data-ttu-id="73d53-110">若要在瀏覽器中查看報表，請使用*rs： Command* = *Render*參數。</span><span class="sxs-lookup"><span data-stu-id="73d53-110">To view a report in the browser, use the *rs:Command*=*Render* parameter.</span></span> <span data-ttu-id="73d53-111">例如：</span><span class="sxs-lookup"><span data-stu-id="73d53-111">For example:</span></span>  
  
 <span data-ttu-id="73d53-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="73d53-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
 <span data-ttu-id="73d53-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="73d53-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="73d53-114">請務必讓 URL 包含 `_vti_bin` Proxy 語法，以便透過 SharePoint 和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP Proxy 路由傳送要求。</span><span class="sxs-lookup"><span data-stu-id="73d53-114">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="73d53-115">此 Proxy 會將某些內容加入至 HTTP 要求，也就是確保針對 SharePoint 模式報表伺服器正確執行報表所需的內容。</span><span class="sxs-lookup"><span data-stu-id="73d53-115">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
## <a name="access-a-resource"></a><span data-ttu-id="73d53-116">存取資源</span><span class="sxs-lookup"><span data-stu-id="73d53-116">Access a Resource</span></span>  
 <span data-ttu-id="73d53-117">若要存取資源，請使用*rs： Command* = *GetResourceContents*參數。如果資源與瀏覽器相容，例如影像，則會在瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="73d53-117">To access a resource, use the *rs:Command*=*GetResourceContents* parameter.If the resource is compatible with the browser, such as an image, it is opened in the browser.</span></span> <span data-ttu-id="73d53-118">否則，系統會提示您開啟檔案或資源，或是將其儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="73d53-118">Otherwise, you are prompted to open or save the file or resource to disk.</span></span>  
  
 <span data-ttu-id="73d53-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="73d53-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span></span>  
  
 <span data-ttu-id="73d53-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="73d53-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span></span>  
  
## <a name="access-a-data-source"></a><span data-ttu-id="73d53-121">存取資料來源</span><span class="sxs-lookup"><span data-stu-id="73d53-121">Access a Data Source</span></span>  
 <span data-ttu-id="73d53-122">若要存取資料來源，請使用*rs： Command* = *GetDataSourceContents*參數。</span><span class="sxs-lookup"><span data-stu-id="73d53-122">To access a data source, use the *rs:Command*=*GetDataSourceContents* parameter.</span></span> <span data-ttu-id="73d53-123">如果您的瀏覽器支援 XML，當您是具有資料來源之 `Read Contents` 權限的已驗證使用者時，會顯示資料來源定義。</span><span class="sxs-lookup"><span data-stu-id="73d53-123">If your browser supports XML, the data source definition is displayed if you are an authenticated user with `Read Contents` permission on the data source.</span></span> <span data-ttu-id="73d53-124">例如：</span><span class="sxs-lookup"><span data-stu-id="73d53-124">For example:</span></span>  
  
 <span data-ttu-id="73d53-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="73d53-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="73d53-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="73d53-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="73d53-127">XML 結構可能類似於下列範例：</span><span class="sxs-lookup"><span data-stu-id="73d53-127">The XML structure might look similar to the following example:</span></span>  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 <span data-ttu-id="73d53-128">根據報表伺服器的 **SecureConnectionLevel** 設定傳回連接字串。</span><span class="sxs-lookup"><span data-stu-id="73d53-128">The connection string is returned based on the **SecureConnectionLevel** setting of the report server.</span></span> <span data-ttu-id="73d53-129">如需 **SecureConnectionLevel** 設定的詳細資訊，請參閱 [使用安全的 Web 服務方法](report-server-web-service/net-framework/using-secure-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="73d53-129">For more information about the **SecureConnectionLevel** setting, see [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).</span></span>  
  
## <a name="access-the-contents-of-a-folder"></a><span data-ttu-id="73d53-130">存取資料夾的內容</span><span class="sxs-lookup"><span data-stu-id="73d53-130">Access the Contents of a Folder</span></span>  
 <span data-ttu-id="73d53-131">若要存取資料夾的內容，請使用*rs： Command* = *GetChildren*參數。</span><span class="sxs-lookup"><span data-stu-id="73d53-131">To access the contents of a folder, use the *rs:Command*=*GetChildren* parameter.</span></span> <span data-ttu-id="73d53-132">隨即會傳回一般資料夾巡覽頁面，其中包含在要求資料夾中所含的子資料夾、報表、資料來源與資源的連結。</span><span class="sxs-lookup"><span data-stu-id="73d53-132">A generic folder-navigation page is returned that contains links to the subfolders, reports, data sources, and resources in the requested folder.</span></span> <span data-ttu-id="73d53-133">例如：</span><span class="sxs-lookup"><span data-stu-id="73d53-133">For example:</span></span>  
  
 <span data-ttu-id="73d53-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="73d53-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="73d53-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="73d53-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="73d53-136">您看到的使用者介面類似於 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS) 所使用的目錄瀏覽模式。</span><span class="sxs-lookup"><span data-stu-id="73d53-136">The user interface you see is similar to the directory browsing mode used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS).</span></span> <span data-ttu-id="73d53-137">報表伺服器的版本號碼 (包括組建編號) 也會顯示在資料夾清單下面。</span><span class="sxs-lookup"><span data-stu-id="73d53-137">The version number, including the build number, of the report server is also displayed below the folder listing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d53-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73d53-138">See Also</span></span>  
 <span data-ttu-id="73d53-139">[&#40;SSRS&#41;的 URL 存取](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="73d53-139">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="73d53-140">URL 存取參數參考</span><span class="sxs-lookup"><span data-stu-id="73d53-140">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
