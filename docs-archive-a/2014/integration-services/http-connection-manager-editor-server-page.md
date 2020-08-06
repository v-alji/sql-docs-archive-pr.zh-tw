---
title: HTTP 連線管理員編輯器 (伺服器頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2349766b11b28ff258496dc966d554d49c7657b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592125"
---
# <a name="http-connection-manager-editor-server-page"></a><span data-ttu-id="fd370-102">HTTP 連接管理員編輯器 (伺服器頁面)</span><span class="sxs-lookup"><span data-stu-id="fd370-102">HTTP Connection Manager Editor (Server Page)</span></span>
  <span data-ttu-id="fd370-103">使用 [HTTP 連接管理員編輯器]\*\*\*\* 對話方塊的 [伺服器]\*\*\*\* 索引標籤指定各項屬性，例如 URL 和安全性認證，以設定 HTTP 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="fd370-103">Use the **Server** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager by specifying properties such as the URL and security credentials.</span></span> <span data-ttu-id="fd370-104">HTTP 連接讓封裝得以經由使用 HTTP 傳送或接收檔案，存取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd370-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="fd370-105">設定 HTTP 連接管理員之後，可以同時測試連接。</span><span class="sxs-lookup"><span data-stu-id="fd370-105">After configuring the HTTP Connection Manager, you can also test the connection.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd370-106">HTTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="fd370-106">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="fd370-107">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="fd370-107">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="fd370-108">若要深入了解 HTTP 連接管理員，請參閱＜ [HTTP Connection Manager](connection-manager/http-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fd370-108">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="fd370-109">若要深入了解 HTTP 連接管理員的常見使用案例，請參閱＜ [Web Service Task](control-flow/web-service-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fd370-109">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd370-110">選項</span><span class="sxs-lookup"><span data-stu-id="fd370-110">Options</span></span>  
 <span data-ttu-id="fd370-111">**伺服器 URL**</span><span class="sxs-lookup"><span data-stu-id="fd370-111">**Server URL**</span></span>  
 <span data-ttu-id="fd370-112">輸入伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="fd370-112">Type the URL for the server.</span></span>  
  
 <span data-ttu-id="fd370-113">如果您計劃使用 [Web 服務工作編輯器]\*\*\*\* 中 [一般]\*\*\*\* 頁面上的 [下載 WSDL]\*\*\*\* 按鈕來下載 WSDL 檔案，請輸入 WSDL 檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="fd370-113">If you plan to use the **Download WSDL** button on the **General** page of the **Web Service Task Editor** to download a WSDL file, type the URL for the WSDL file.</span></span> <span data-ttu-id="fd370-114">這個 URL 需以 "?wsdl" 結尾。</span><span class="sxs-lookup"><span data-stu-id="fd370-114">This URL ends with "?wsdl".</span></span>  
  
 <span data-ttu-id="fd370-115">**使用認證**</span><span class="sxs-lookup"><span data-stu-id="fd370-115">**Use credentials**</span></span>  
 <span data-ttu-id="fd370-116">指定 HTTP 連接管理員是否使用使用者的安全性認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="fd370-116">Specify whether you want the HTTP Connection Manager to use the user's security credentials for authentication.</span></span>  
  
 <span data-ttu-id="fd370-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="fd370-117">**User name**</span></span>  
 <span data-ttu-id="fd370-118">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="fd370-118">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="fd370-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="fd370-119">**Password**</span></span>  
 <span data-ttu-id="fd370-120">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="fd370-120">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="fd370-121">**網域**</span><span class="sxs-lookup"><span data-stu-id="fd370-121">**Domain**</span></span>  
 <span data-ttu-id="fd370-122">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="fd370-122">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="fd370-123">**使用用戶端憑證**</span><span class="sxs-lookup"><span data-stu-id="fd370-123">**Use client certificate**</span></span>  
 <span data-ttu-id="fd370-124">指定 HTTP 連接管理員是否使用用戶端憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="fd370-124">Specify whether you want the HTTP Connection Manager to use a client certificate for authentication.</span></span>  
  
 <span data-ttu-id="fd370-125">**[MSSQLSERVER 的通訊協定內容]**</span><span class="sxs-lookup"><span data-stu-id="fd370-125">**Certificate**</span></span>  
 <span data-ttu-id="fd370-126">使用 [選取憑證]\*\*\*\* 對話方塊，即可從清單中選取憑證。</span><span class="sxs-lookup"><span data-stu-id="fd370-126">Select a certificate from the list by using the **Select Certificate** dialog box.</span></span> <span data-ttu-id="fd370-127">文字方塊會顯示與此憑證相關聯的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd370-127">The text box displays the name associated with this certificate.</span></span>  
  
 <span data-ttu-id="fd370-128">**逾時 (以秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="fd370-128">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="fd370-129">提供連接到 Web 伺服器的逾時設定。</span><span class="sxs-lookup"><span data-stu-id="fd370-129">Provide a time-out for connecting to the Web server.</span></span> <span data-ttu-id="fd370-130">此屬性的預設值為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="fd370-130">The default value of this property is 30 seconds.</span></span>  
  
 <span data-ttu-id="fd370-131">**區塊大小 (以 KB 為單位)**</span><span class="sxs-lookup"><span data-stu-id="fd370-131">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="fd370-132">提供寫入資料的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="fd370-132">Provide a chunk size for writing data.</span></span>  
  
 <span data-ttu-id="fd370-133">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="fd370-133">**Test Connection**</span></span>  
 <span data-ttu-id="fd370-134">設定 HTTP 連接管理員之後，請按一下 [測試連接]\*\*\*\* 以確認可以看到連接。</span><span class="sxs-lookup"><span data-stu-id="fd370-134">After configuring the HTTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd370-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd370-135">See Also</span></span>  
 <span data-ttu-id="fd370-136">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fd370-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="fd370-137">HTTP 連接管理員編輯器 &#40;Proxy 頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fd370-137">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)  
  
  
