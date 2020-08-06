---
title: 實作 IRenderingExtension 介面 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f57c4aa41ccfed165b69581cbf3917e4dfbb4960
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596532"
---
# <a name="implementing-the-irenderingextension-interface"></a><span data-ttu-id="f7a59-102">實作 IRenderingExtension 介面</span><span class="sxs-lookup"><span data-stu-id="f7a59-102">Implementing the IRenderingExtension Interface</span></span>
  <span data-ttu-id="f7a59-103">轉譯延伸模組會從與實際資料結合的報表定義取得結果，並將產生的資料轉譯成可用的格式。</span><span class="sxs-lookup"><span data-stu-id="f7a59-103">The rendering extension takes the results from a report definition that is combined with the actual data and renders the resulting data to a format that is useable.</span></span> <span data-ttu-id="f7a59-104">結合的資料與格式之轉換是利用實作 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 的 Common Language Runtime (CLR) 類別來完成。</span><span class="sxs-lookup"><span data-stu-id="f7a59-104">The transformation of the combined data and formatting is done by using a common language runtime (CLR) class that implements <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>.</span></span> <span data-ttu-id="f7a59-105">這可將物件模型轉換為檢視器、印表機或是其他輸出目標可取用的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="f7a59-105">This transforms the object model into an output format that is consumable by a viewer, printer, or other output target.</span></span>  
  
 <span data-ttu-id="f7a59-106"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> 具有三個必須撰寫程式碼的方法：</span><span class="sxs-lookup"><span data-stu-id="f7a59-106">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> has three methods that must be coded:</span></span>  
  
-   <span data-ttu-id="f7a59-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - 轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="f7a59-107"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> - renders the report.</span></span>  
  
-   <span data-ttu-id="f7a59-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - 從報表轉譯特定的資料流。</span><span class="sxs-lookup"><span data-stu-id="f7a59-108"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> - renders a specific stream from the report.</span></span>  
  
-   <span data-ttu-id="f7a59-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - 取得報表所需的其他資訊，例如圖示。</span><span class="sxs-lookup"><span data-stu-id="f7a59-109"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> - gets additional information, such as icons, that are required for the report.</span></span>  
  
 <span data-ttu-id="f7a59-110">下列各節針對這些方法進行更詳細的討論。</span><span class="sxs-lookup"><span data-stu-id="f7a59-110">The following sections discuss these methods in more detail.</span></span>  
  
## <a name="render-method"></a><span data-ttu-id="f7a59-111">Render 方法</span><span class="sxs-lookup"><span data-stu-id="f7a59-111">Render Method</span></span>  
 <span data-ttu-id="f7a59-112"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 方法包含代表下列物件的引數：</span><span class="sxs-lookup"><span data-stu-id="f7a59-112">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> method contains arguments that represent the following objects:</span></span>  
  
-   <span data-ttu-id="f7a59-113">您要轉譯的「報表」  。</span><span class="sxs-lookup"><span data-stu-id="f7a59-113">The *report* that you want to render.</span></span> <span data-ttu-id="f7a59-114">這個物件包含報表的屬性、資料與配置資訊。</span><span class="sxs-lookup"><span data-stu-id="f7a59-114">This object contains properties, data, and layout information for the report.</span></span> <span data-ttu-id="f7a59-115">報表是報表物件模型樹狀結構的根目錄。</span><span class="sxs-lookup"><span data-stu-id="f7a59-115">The report is the root of the report object model tree.</span></span>  
  
-   <span data-ttu-id="f7a59-116">包含字串字典物件的 *ServerParameters*，含報表伺服器的參數 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="f7a59-116">The *ServerParameters* that contain the string dictionary object, with the parameters for the report server, if any.</span></span>  
  
-   <span data-ttu-id="f7a59-117">包含裝置設定的 *deviceInfo* 參數。</span><span class="sxs-lookup"><span data-stu-id="f7a59-117">The *deviceInfo* parameter that contain the device settings.</span></span> <span data-ttu-id="f7a59-118">如需詳細資訊，請參閱[將裝置資訊設定傳遞至轉譯延伸模組](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="f7a59-118">For more information, see [Passing Device Information Settings to Rendering Extensions](../../report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
-   <span data-ttu-id="f7a59-119">包含 <xref:System.Collections.Specialized.NameValueCollection> 字典物件的 *clientCapabilities* 參數，該物件具有您要轉譯之目標用戶端的資訊。</span><span class="sxs-lookup"><span data-stu-id="f7a59-119">The *clientCapabilities* parameter that contains a <xref:System.Collections.Specialized.NameValueCollection> dictionary object that has information about the client to which you are rendering.</span></span>  
  
-   <span data-ttu-id="f7a59-120">包含轉譯結果相關資訊的 *RenderProperties*。</span><span class="sxs-lookup"><span data-stu-id="f7a59-120">The *RenderProperties* that contains information about the rendering result.</span></span>  
  
-   <span data-ttu-id="f7a59-121">*createAndRegisterStream* 是要呼叫的委派函式，以取得要轉譯成的資料流。</span><span class="sxs-lookup"><span data-stu-id="f7a59-121">The *createAndRegisterStream* is a delegate function to be called to get a stream to render into.</span></span>  
  
### <a name="deviceinfo-parameter"></a><span data-ttu-id="f7a59-122">deviceInfo 參數</span><span class="sxs-lookup"><span data-stu-id="f7a59-122">deviceInfo Parameter</span></span>  
 <span data-ttu-id="f7a59-123">*deviceInfo* 參數包含轉譯參數，而不是報表參數。</span><span class="sxs-lookup"><span data-stu-id="f7a59-123">The *deviceInfo* parameter contains rendering parameters, not report parameters.</span></span> <span data-ttu-id="f7a59-124">這些轉譯參數會傳遞給轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f7a59-124">These rendering parameters are passed to the rendering extension.</span></span> <span data-ttu-id="f7a59-125">報表伺服器會將 *deviceInfo* 值轉換為 <xref:System.Collections.Specialized.NameValueCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="f7a59-125">The *deviceInfo* values are converted into a <xref:System.Collections.Specialized.NameValueCollection> object by the report server.</span></span> <span data-ttu-id="f7a59-126">在 *deviceInfo* 參數中的項目會視為不區分大小寫的值。</span><span class="sxs-lookup"><span data-stu-id="f7a59-126">Items in the *deviceInfo* parameter are treated as case-insensitive values.</span></span> <span data-ttu-id="f7a59-127">如果轉譯要求是以 URL 存取的結果呈現，則 `rc:key=value` 格式的 URL 參數會轉換成 *deviceInfo* 字典物件中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="f7a59-127">If the render request came as a result of URL access, the URL parameters in the form `rc:key=value` are converted to key/value pairs in the *deviceInfo* dictionary object.</span></span> <span data-ttu-id="f7a59-128">瀏覽器偵測程式碼也在 *clientCapabilities* 字典中提供下列項目：EcmaScriptVersion、JavaScript、MajorVersion、MinorVersion、Win32、Type 及 AcceptLanguage。</span><span class="sxs-lookup"><span data-stu-id="f7a59-128">The browser detection code also provides the following items in the *clientCapabilities* dictionary: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type, and AcceptLanguage.</span></span> <span data-ttu-id="f7a59-129">會忽略在 *deviceInfo* 參數中轉譯延伸模組不了解的任何名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="f7a59-129">Any name/value pair in the *deviceInfo* parameter that is not understood by the rendering extension is ignored.</span></span> <span data-ttu-id="f7a59-130">下列程式碼範例顯示用來擷取圖示的範例 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="f7a59-130">The following code sample shows a sample <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method that retrieves icons:</span></span>  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a><span data-ttu-id="f7a59-131">RenderStream 方法</span><span class="sxs-lookup"><span data-stu-id="f7a59-131">RenderStream Method</span></span>  
 <span data-ttu-id="f7a59-132"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> 方法會從報表轉譯特定的資料流。</span><span class="sxs-lookup"><span data-stu-id="f7a59-132">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> method renders a particular stream from the report.</span></span> <span data-ttu-id="f7a59-133">在初始 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> 呼叫期間會建立所有的資料流，但是一開始不會將資料流傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="f7a59-133">All streams are created during the initial <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> call, but the streams are not returned to the client initially.</span></span> <span data-ttu-id="f7a59-134">這個方法是用於第二個資料流 (例如 HTML 轉譯中的影像) 或是多頁面轉譯延伸模組的其他頁面 (例如影像/EMF)。</span><span class="sxs-lookup"><span data-stu-id="f7a59-134">This method is used for secondary streams, such as images in HTML rendering, or additional pages of a multi-page rendering extension, such as Image/EMF.</span></span>  
  
## <a name="getrenderingresource-method"></a><span data-ttu-id="f7a59-135">GetRenderingResource 方法</span><span class="sxs-lookup"><span data-stu-id="f7a59-135">GetRenderingResource Method</span></span>  
 <span data-ttu-id="f7a59-136"><xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法會擷取資訊，而不需執行報表的完整轉譯。</span><span class="sxs-lookup"><span data-stu-id="f7a59-136">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method retrieves the information without executing an entire rendering of the report.</span></span> <span data-ttu-id="f7a59-137">有時報表需要的資訊，並不需要轉譯報表本身。</span><span class="sxs-lookup"><span data-stu-id="f7a59-137">There are times when the report requires information that does not require the report itself to be rendered.</span></span> <span data-ttu-id="f7a59-138">例如，如果您需要與轉譯延伸模組相關聯的圖示，請使用包含單一標記的*deviceInfo*參數 **\<Icon>** 。</span><span class="sxs-lookup"><span data-stu-id="f7a59-138">For example, if you need the icon associated with the rendering extension, use the *deviceInfo* parameter containing the single tag **\<Icon>**.</span></span> <span data-ttu-id="f7a59-139">在這些情況下，您可以使用 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f7a59-139">In these cases, you can use the <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a59-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a59-140">See Also</span></span>  
 <span data-ttu-id="f7a59-141">[實作轉譯延伸模組](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="f7a59-141">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 [<span data-ttu-id="f7a59-142">轉譯延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="f7a59-142">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
  
  
