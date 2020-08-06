---
title: Web 服務工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2f719a6fb0076a3bb286865199a9cf6a008d32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592800"
---
# <a name="web-service-task"></a><span data-ttu-id="427eb-102">Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="427eb-102">Web Service Task</span></span>
  <span data-ttu-id="427eb-103">「Web 服務」工作執行一個 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="427eb-103">The Web Service task executes a Web service method.</span></span> <span data-ttu-id="427eb-104">您可將「Web 服務」工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="427eb-104">You can use the Web Service task for the following purposes:</span></span>  
  
-   <span data-ttu-id="427eb-105">將 Web 服務方法傳回的值寫入變數。</span><span class="sxs-lookup"><span data-stu-id="427eb-105">Writing to a variable the values that a Web service method returns.</span></span> <span data-ttu-id="427eb-106">例如，您可以使用 Web 服務方法取得一天的最高溫度，然後使用該值來更新在設定資料行值之運算式中所使用的變數。</span><span class="sxs-lookup"><span data-stu-id="427eb-106">For example, you could obtain the highest temperature of the day from a Web service method, and then use that value to update a variable that is used in an expression that sets a column value.</span></span>  
  
-   <span data-ttu-id="427eb-107">將 Web 服務方法傳回的值寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="427eb-107">Writing to a file the values that a Web service method returns.</span></span> <span data-ttu-id="427eb-108">例如，可以將潛在客戶清單寫入檔案，該檔案之後將用作封裝中的資料來源，此封裝會在資料寫入資料庫之前清除它們。</span><span class="sxs-lookup"><span data-stu-id="427eb-108">For example, a list of potential customers can be written to a file and the file then used as a data source in a package that cleans the data before it is written to a database.</span></span>  
  
## <a name="wsdl-file"></a><span data-ttu-id="427eb-109">WSDL 檔案</span><span class="sxs-lookup"><span data-stu-id="427eb-109">WSDL File</span></span>  
 <span data-ttu-id="427eb-110">Web 服務工作使用 HTTP 連接管理員，以連接到 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="427eb-110">The Web Service task uses an HTTP connection manager to connect to the Web service.</span></span> <span data-ttu-id="427eb-111">會在 Web 服務工作以外另行設定 HTTP 連接管理員，然後在工作中參考。</span><span class="sxs-lookup"><span data-stu-id="427eb-111">The HTTP connection manager is configured separately from the Web Service task, and is referenced in the task.</span></span> <span data-ttu-id="427eb-112">HTTP 連接管理員會指定伺服器 Proxy 設定，例如伺服器 URL、用於存取 Web 服務伺服器的認證以及逾時長度。</span><span class="sxs-lookup"><span data-stu-id="427eb-112">The HTTP connection manager specifies the server proxy settings such as the server URL, credentials for accessing the Web services server, and time-out length.</span></span> <span data-ttu-id="427eb-113">如需詳細資訊，請參閱 [HTTP 連線管理員](../connection-manager/http-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="427eb-113">For more information, see [HTTP Connection Manager](../connection-manager/http-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="427eb-114">HTTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="427eb-114">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="427eb-115">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="427eb-115">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="427eb-116">HTTP 連接管理員可指向網站或「Web 服務描述語言」(WSDL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="427eb-116">The HTTP connection manager can point to a Web site or to a Web Service Description Language (WSDL) file.</span></span> <span data-ttu-id="427eb-117">指向 WSDL 檔案之 HTTP 連接管理員的 URL 包含 `?WSDL` 參數：例如 `http://MyServer/MyWebService/MyPage.asmx?WSDL`。</span><span class="sxs-lookup"><span data-stu-id="427eb-117">The URL of the HTTP connection manager that points to a WSDL file includes the `?WSDL` parameter: for example, `http://MyServer/MyWebService/MyPage.asmx?WSDL`.</span></span>  
  
 <span data-ttu-id="427eb-118">WSDL 檔案必須可以在本機上使用，這樣才能使用 **設計師提供的 [Web 服務工作編輯器]** [!INCLUDE[ssIS](../../includes/ssis-md.md)] 對話方塊設定 Web 服務工作。</span><span class="sxs-lookup"><span data-stu-id="427eb-118">The WSDL file must be available locally to configure the Web Service task using the **Web Service Task Editor** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span>  
  
-   <span data-ttu-id="427eb-119">如果 HTTP 連接管理員指向網站，則必須手動將 WSDL 檔案複製到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="427eb-119">If the HTTP connection manager points to a Web site, the WSDL file must be copied manually to a local computer.</span></span>  
  
-   <span data-ttu-id="427eb-120">如果 HTTP 連接管理員指向 WSDL 檔案，則可透過 Web 服務工作從網站下載該檔案到本機檔案。</span><span class="sxs-lookup"><span data-stu-id="427eb-120">If the HTTP connection manager points to a WSDL file, the file can be downloaded from the Web site to a local file by the Web Service task.</span></span>  
  
 <span data-ttu-id="427eb-121">WSDL 檔案會列出 Web 服務提供的方法、方法需要的輸入參數、方法傳回的回應，以及如何與 Web 服務通訊。</span><span class="sxs-lookup"><span data-stu-id="427eb-121">The WSDL file lists the methods that the Web service offers, the input parameters that the methods require, the responses that the methods return, and how to communicate with the Web service.</span></span>  
  
 <span data-ttu-id="427eb-122">如果方法使用輸入參數，則 Web 服務工作需要參數值。</span><span class="sxs-lookup"><span data-stu-id="427eb-122">If the method uses input parameters, the Web Service task requires parameter values.</span></span> <span data-ttu-id="427eb-123">例如，某個 Web 服務方法依據您的身高建議應購買之滑雪板的長度，則該方法需要在輸入參數中提交您的身高。</span><span class="sxs-lookup"><span data-stu-id="427eb-123">For example, a Web service method that recommends the length of skis you should purchase based on your height requires that your height be submitted in an input parameter.</span></span> <span data-ttu-id="427eb-124">參數值可由在工作中定義的字串，或是由在工作或父容器範圍中定義的變數提供。</span><span class="sxs-lookup"><span data-stu-id="427eb-124">The parameter values can be provided either by strings that are defined in the task, or by variables defined in the scope of the task or a parent container.</span></span> <span data-ttu-id="427eb-125">使用變數的優點就是可讓您利用封裝組態或指令碼，以動態方式更新參數值。</span><span class="sxs-lookup"><span data-stu-id="427eb-125">The advantage of using variables is that they let you dynamically update the parameter values by using package configurations or scripts.</span></span> <span data-ttu-id="427eb-126">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[封裝組態](../package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="427eb-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Package Configurations](../package-configurations.md).</span></span>  
  
 <span data-ttu-id="427eb-127">許多 Web 服務方法都不使用輸入參數。</span><span class="sxs-lookup"><span data-stu-id="427eb-127">Many Web service methods do not use input parameters.</span></span> <span data-ttu-id="427eb-128">例如，某個 Web 服務方法取得出生於目前月份之總統的姓名，該方法不需要輸入參數，因為 Web 服務可以從本機決定目前月份。</span><span class="sxs-lookup"><span data-stu-id="427eb-128">For example, a Web service method that gets the names of presidents who were born in the current month would not require an input parameter because the Web service can determine the current month locally.</span></span>  
  
 <span data-ttu-id="427eb-129">Web 服務方法的結果可以寫入變數或檔案。</span><span class="sxs-lookup"><span data-stu-id="427eb-129">The results of the Web service method can be written to a variable or to a file.</span></span> <span data-ttu-id="427eb-130">您可以使用「檔案」連接管理員，以指定要寫入結果的檔案或提供要寫入結果的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="427eb-130">You use the File connection manager either to specify the file or to provide the name of the variable to write the results to.</span></span> <span data-ttu-id="427eb-131">如需詳細資訊，請參閱[檔案連線管理員](../connection-manager/file-connection-manager.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="427eb-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a><span data-ttu-id="427eb-132">Web 服務工作上可用的自訂記錄訊息</span><span class="sxs-lookup"><span data-stu-id="427eb-132">Custom Logging Messages Available on the Web Service Task</span></span>  
 <span data-ttu-id="427eb-133">下表列出您可以為 Web 服務工作啟用的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="427eb-133">The following table lists the custom log entries that you can enable for the Web Service task.</span></span> <span data-ttu-id="427eb-134">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="427eb-134">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="427eb-135">記錄項目</span><span class="sxs-lookup"><span data-stu-id="427eb-135">Log entry</span></span>|<span data-ttu-id="427eb-136">描述</span><span class="sxs-lookup"><span data-stu-id="427eb-136">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="427eb-137">工作已經開始存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="427eb-137">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="427eb-138">工作已經完成 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="427eb-138">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="427eb-139">關於工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="427eb-139">Descriptive information about the task.</span></span>|  
  
## <a name="configuration-of-the-web-service-task"></a><span data-ttu-id="427eb-140">設定 Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="427eb-140">Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="427eb-141">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="427eb-141">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="427eb-142">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="427eb-142">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="427eb-143">[Web 服務工作編輯器 &#40;[一般] 頁面&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="427eb-143">[Web Service Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="427eb-144">[Web 服務工作編輯器 &#40;[輸入] 頁面&#41;](../web-service-task-editor-input-page.md)</span><span class="sxs-lookup"><span data-stu-id="427eb-144">[Web Service Task Editor &#40;Input Page&#41;](../web-service-task-editor-input-page.md)</span></span>  
  
-   <span data-ttu-id="427eb-145">[Web 服務工作編輯器 &#40;[輸出] 頁面&#41;](../web-service-task-editor-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="427eb-145">[Web Service Task Editor &#40;Output Page&#41;](../web-service-task-editor-output-page.md)</span></span>  
  
-   [<span data-ttu-id="427eb-146">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="427eb-146">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="427eb-147">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="427eb-147">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="427eb-148">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="427eb-148">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a><span data-ttu-id="427eb-149">以程式設計方式設定 Web 服務工作</span><span class="sxs-lookup"><span data-stu-id="427eb-149">Programmatic Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="427eb-150">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="427eb-150">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a><span data-ttu-id="427eb-151">相關內容</span><span class="sxs-lookup"><span data-stu-id="427eb-151">Related Content</span></span>  
 <span data-ttu-id="427eb-152">影片，[如何：technet.microsoft.com 上的影片：使用 Web 服務工作呼叫 Web 服務) (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=259642) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="427eb-152">Video, [How to: Call a Web Service by Using the Web Service Task (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=259642), on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="427eb-153">[如何透過 SSIS 套件使用 Web 服務](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/)。</span><span class="sxs-lookup"><span data-stu-id="427eb-153">[How To Consume Web Service Through SSIS Package](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/).</span></span>  
  
  
