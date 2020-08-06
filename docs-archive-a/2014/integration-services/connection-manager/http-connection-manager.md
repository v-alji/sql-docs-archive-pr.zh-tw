---
title: HTTP 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10c9f0778faa25aff8db4ad54ecaa8d3ccc5b359
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707709"
---
# <a name="http-connection-manager"></a><span data-ttu-id="d5340-102">HTTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="d5340-102">HTTP Connection Manager</span></span>
  <span data-ttu-id="d5340-103">HTTP 連接讓封裝得以經由使用 HTTP 傳送或接收檔案，存取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5340-103">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="d5340-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的「Web 服務」工作會使用此連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d5340-104">The Web Service task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="d5340-105">當您將 HTTP 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立連接管理員，用來在執行階段解析為 HTTP 連接、設定連接管理員屬性，以及將連接管理員加入封裝的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="d5340-105">When you add an HTTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an HTTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="d5340-106">連接管理員的 `ConnectionManagerType` 屬性會設定為 `HTTP.`。</span><span class="sxs-lookup"><span data-stu-id="d5340-106">The `ConnectionManagerType` property of the connection manager is set to `HTTP.`</span></span>  
  
 <span data-ttu-id="d5340-107">您可以利用下列方式設定 HTTP 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="d5340-107">You can configure the HTTP connection manager the following ways:</span></span>  
  
-   <span data-ttu-id="d5340-108">使用認證。</span><span class="sxs-lookup"><span data-stu-id="d5340-108">Use credentials.</span></span> <span data-ttu-id="d5340-109">如果連接管理員使用認證，其屬性會包含使用者名稱、密碼與網域。</span><span class="sxs-lookup"><span data-stu-id="d5340-109">If the connection manager uses credentials, its properties include the user name, password, and domain.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d5340-110">HTTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="d5340-110">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="d5340-111">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d5340-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="d5340-112">使用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="d5340-112">Use a client certificate.</span></span> <span data-ttu-id="d5340-113">如果連接管理員使用用戶端憑證，其屬性會包含憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="d5340-113">If the connection manager uses a client certificate, its properties include the certificate name.</span></span>  
  
-   <span data-ttu-id="d5340-114">提供連接到伺服器的逾時以及寫入資料的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="d5340-114">Provide a time-out for connecting to the server and a chunk size for writing data.</span></span>  
  
-   <span data-ttu-id="d5340-115">使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5340-115">Use a proxy server.</span></span> <span data-ttu-id="d5340-116">Proxy 伺服器也可設定為使用認證，以及設定為略過 Proxy 伺服器並改用本機位址。</span><span class="sxs-lookup"><span data-stu-id="d5340-116">The proxy server can also be configured to use credentials and to bypass the proxy server and use local addresses instead.</span></span>  
  
## <a name="configuration-of-the-http-connection-manager"></a><span data-ttu-id="d5340-117">設定 HTTP 連接管理員</span><span class="sxs-lookup"><span data-stu-id="d5340-117">Configuration of the HTTP Connection Manager</span></span>  
 <span data-ttu-id="d5340-118">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d5340-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d5340-119">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="d5340-119">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d5340-120">HTTP 連線管理員編輯器 &#40;伺服器頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d5340-120">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../http-connection-manager-editor-server-page.md)  
  
-   [<span data-ttu-id="d5340-121">HTTP 連接管理員編輯器 &#40;Proxy 頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d5340-121">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../http-connection-manager-editor-proxy-page.md)  
  
 <span data-ttu-id="d5340-122">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>。</span><span class="sxs-lookup"><span data-stu-id="d5340-122">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5340-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5340-123">See Also</span></span>  
 <span data-ttu-id="d5340-124">[Web 服務工作](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="d5340-124">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="d5340-125">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="d5340-125">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
