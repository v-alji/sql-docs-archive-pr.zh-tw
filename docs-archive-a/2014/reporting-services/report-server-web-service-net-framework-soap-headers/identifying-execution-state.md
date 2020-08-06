---
title: 識別執行狀態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe53254a5da39c4e7d003ba37d5812ad130293e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599338"
---
# <a name="identifying-execution-state"></a><span data-ttu-id="1566d-102">識別執行狀態</span><span class="sxs-lookup"><span data-stu-id="1566d-102">Identifying Execution State</span></span>
  <span data-ttu-id="1566d-103">超文字傳輸協定 (HTTP) 是一種無連接且沒有狀態 (Stateless) 的通訊協定，也就是說它不會自動指出不同的要求是否全都來自相同的用戶端，也不會自動指出某個特定瀏覽器執行個體是否仍在主動檢視網頁或網站。</span><span class="sxs-lookup"><span data-stu-id="1566d-103">Hypertext Transfer Protocol (HTTP) is a connectionless and stateless protocol, which means that it does not automatically indicate whether different requests come from the same client or even whether a single browser instance is still actively viewing a page or site.</span></span> <span data-ttu-id="1566d-104">工作階段會建立邏輯連接以透過 HTTP 維護伺服器與用戶端之間的狀態。</span><span class="sxs-lookup"><span data-stu-id="1566d-104">Sessions create a logical connection to maintain state between server and client over HTTP.</span></span> <span data-ttu-id="1566d-105">與特定工作階段相關的使用者特定資訊又稱為工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="1566d-105">The user-specific information relevant to a particular session is known as the session state.</span></span>

 <span data-ttu-id="1566d-106">工作階段管理需要將 HTTP 要求與從相同工作階段產生的其他舊要求相互關聯。</span><span class="sxs-lookup"><span data-stu-id="1566d-106">Session management involves correlating an HTTP request with other previous requests generated from the same session.</span></span> <span data-ttu-id="1566d-107">若沒有工作階段管理，由於 HTTP 通訊協定的無連接與無狀態的本質，這些要求會顯得與報表伺服器 Web 服務不相關。</span><span class="sxs-lookup"><span data-stu-id="1566d-107">Without session management, these requests appear unrelated to the Report Server Web service because of the connectionless and stateless nature of the HTTP protocol.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1566d-108">並不會公開工作階段狀態的整體概念，例如由 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 所公開。</span><span class="sxs-lookup"><span data-stu-id="1566d-108">does not expose a holistic concept of session state such as that exposed by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="1566d-109">不過，當執行報表時，報表伺服器會以**執行**的形式在方法呼叫之間維護狀態。</span><span class="sxs-lookup"><span data-stu-id="1566d-109">However, when executing reports, the report server maintains state between method calls in the form of an **execution**.</span></span> <span data-ttu-id="1566d-110">執行可讓使用者以數種方式和報表互動，包括從報表伺服器載入報表、設定報表的認證與參數，以及轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="1566d-110">An execution allows the user to interact with the report in several ways - including loading the report from the report server, setting credentials and parameters for the report, and rendering the report.</span></span>

 <span data-ttu-id="1566d-111">在與報表伺服器進行通訊時，用戶端會使用執行來管理報表檢視以及對報表中其他頁面的使用者導覽，並顯示或是隱藏報表的區段。</span><span class="sxs-lookup"><span data-stu-id="1566d-111">While they are communicating to a report server, clients use the execution to manage report viewing and user navigation to other pages in a report, and to show or hide sections of a report.</span></span> <span data-ttu-id="1566d-112">用戶端應用程式正在執行的每個報表，會有唯一的執行。</span><span class="sxs-lookup"><span data-stu-id="1566d-112">A unique execution exists for each report the client application is running.</span></span>

 <span data-ttu-id="1566d-113">一般而言，當使用者導覽至瀏覽器或是用戶端應用程式，並選取要檢視的報表時，執行的存留期間會開始。</span><span class="sxs-lookup"><span data-stu-id="1566d-113">In general, the lifetime of an execution starts when a user navigates to a browser or client application and selects a report to view.</span></span> <span data-ttu-id="1566d-114">在已經收到對執行的上一個要求之後，將會在簡短的逾時期間之後捨棄執行 (預設逾時是 20 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="1566d-114">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="1566d-115">從 Web 服務觀點來看，當呼叫報表伺服器 Web 服務 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 或是 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法時，存留期間即開始。</span><span class="sxs-lookup"><span data-stu-id="1566d-115">From a Web service perspective, the lifetime starts when the Report Server Web service <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>, or <xref:ReportExecution2005.ReportExecutionService.Render%2A> methods are called.</span></span> <span data-ttu-id="1566d-116">應用程式可以使用其他方法來操作使用中執行 (例如，設定參數和設定資料來源)。</span><span class="sxs-lookup"><span data-stu-id="1566d-116">The application can use other methods to manipulate the active execution (for example, setting parameters and setting data sources).</span></span> <span data-ttu-id="1566d-117">在已經收到對執行的上一個要求之後，將會在簡短的逾時期間之後捨棄執行 (預設逾時是 20 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="1566d-117">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="1566d-118">應用程式會儲存 <xref:ReportExecution2005.ReportExecutionService.Render%2A>，以便從 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 與 <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A> 方法在 SOAP 標頭中傳回，來對 Web 服務 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 和 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 方法之間的呼叫持續追蹤多個使用中執行。</span><span class="sxs-lookup"><span data-stu-id="1566d-118">An application keep track of multiple active executions between calls to the Web service <xref:ReportExecution2005.ReportExecutionService.Render%2A> and <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> methods by saving the <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>, which is returned in the SOAP header from the <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> and <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> methods.</span></span>

 <span data-ttu-id="1566d-119">下圖顯示報表的處理和轉譯路徑。</span><span class="sxs-lookup"><span data-stu-id="1566d-119">The following diagram shows the processing and rendering path for reports.</span></span>

 <span data-ttu-id="1566d-120">![報表處理/轉譯路徑](../../../2014/reporting-services/media/rs-render-process-diagram.gif "報表處理/轉譯路徑")</span><span class="sxs-lookup"><span data-stu-id="1566d-120">![Report processing/rendering path](../../../2014/reporting-services/media/rs-render-process-diagram.gif "Report processing/rendering path")</span></span>

 <span data-ttu-id="1566d-121">為了支援上述功能，已將目前的 SOAP Render 方法分成多個方法，以包含執行初始化、處理和轉譯階段。</span><span class="sxs-lookup"><span data-stu-id="1566d-121">To support the functions described above, the current SOAP Render method has been split into multiple methods encompassing execution initialization, processing, and rendering phases.</span></span>

 <span data-ttu-id="1566d-122">若要以程式設計的方式轉譯報表，您必須：</span><span class="sxs-lookup"><span data-stu-id="1566d-122">To programmatically render a report, you must:</span></span>

-   <span data-ttu-id="1566d-123">使用 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 來載入報表或是報表定義。</span><span class="sxs-lookup"><span data-stu-id="1566d-123">Load the report or the report definition using <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.</span></span>

-   <span data-ttu-id="1566d-124">查看報表是否需要認證或是參數，方法是檢查由 <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> 或 <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> 傳回的 <xref:ReportExecution2005.ExecutionInfo> 物件之 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 與 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1566d-124">Check to see if the report needs credentials or parameters by checking the values of the <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> and <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> properties of the <xref:ReportExecution2005.ExecutionInfo> object returned by <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A></span></span>

-   <span data-ttu-id="1566d-125">若有需要，請使用 <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> 與 <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> 方法來設定認證和/或參數。</span><span class="sxs-lookup"><span data-stu-id="1566d-125">If necessary, set the credentials and/or parameters using the <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> and <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> methods.</span></span>

-   <span data-ttu-id="1566d-126">呼叫 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 方法以轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="1566d-126">Call the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to render the report.</span></span>

 <span data-ttu-id="1566d-127">當報表是在工作階段中時，儲存在報表伺服器資料庫中的基礎報表有可能會變更。</span><span class="sxs-lookup"><span data-stu-id="1566d-127">While a report is in session, the underlying report stored in the report server database can change.</span></span> <span data-ttu-id="1566d-128">例如，報表定義有可能會變更，報表有可能會刪除或是移動，而且使用者權限也可能會變更。</span><span class="sxs-lookup"><span data-stu-id="1566d-128">For example, the report definition can change, the report can be deleted or moved, and user permissions can change.</span></span> <span data-ttu-id="1566d-129">如果報表是在使用中工作階段，它不會受到對基礎報表變更的影響 (也就是說，報表會儲存在報表伺服器資料庫中)。</span><span class="sxs-lookup"><span data-stu-id="1566d-129">If the report is in an active session, it is not affected by changes made to the underlying report (that is, the report stored in the report server database).</span></span>

 <span data-ttu-id="1566d-130">您也可以使用 URL 存取命令來管理報表工作階段。</span><span class="sxs-lookup"><span data-stu-id="1566d-130">You can also manage a report session using URL access commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="1566d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1566d-131">See Also</span></span>
 <span data-ttu-id="1566d-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A>[使用 REPORTING SERVICES SOAP 標頭](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md) [&#40;SSRS&#41;的技術參考](../../../2014/reporting-services/technical-reference-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="1566d-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A> [Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) [Using Reporting Services SOAP Headers](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)</span></span>


