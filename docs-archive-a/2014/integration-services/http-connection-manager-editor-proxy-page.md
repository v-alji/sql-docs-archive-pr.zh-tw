---
title: HTTP 連線管理員編輯器 (Proxy 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8269dbbeb226ffa3f56c226e1a416d99c1e3f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592130"
---
# <a name="http-connection-manager-editor-proxy-page"></a><span data-ttu-id="2647c-102">HTTP 連接管理員編輯器 (Proxy 頁面)</span><span class="sxs-lookup"><span data-stu-id="2647c-102">HTTP Connection Manager Editor (Proxy Page)</span></span>
  <span data-ttu-id="2647c-103">使用 **[HTTP 連接管理員編輯器]** 對話方塊的 **[Proxy]** 索引標籤，來設定 HTTP 連接管理員使用 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2647c-103">Use the **Proxy** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager to use a proxy server.</span></span> <span data-ttu-id="2647c-104">HTTP 連接讓封裝得以經由使用 HTTP 傳送或接收檔案，存取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2647c-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span>  
  
 <span data-ttu-id="2647c-105">若要深入了解 HTTP 連接管理員，請參閱＜ [HTTP Connection Manager](connection-manager/http-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2647c-105">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="2647c-106">若要深入了解 HTTP 連接管理員的常見使用案例，請參閱＜ [Web Service Task](control-flow/web-service-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2647c-106">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2647c-107">選項</span><span class="sxs-lookup"><span data-stu-id="2647c-107">Options</span></span>  
 <span data-ttu-id="2647c-108">**使用 Proxy**</span><span class="sxs-lookup"><span data-stu-id="2647c-108">**Use proxy**</span></span>  
 <span data-ttu-id="2647c-109">指定 HTTP 連接管理員是否要透過 Proxy 伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="2647c-109">Specify whether you want the HTTP Connection Manager to connect through a proxy server.</span></span>  
  
 <span data-ttu-id="2647c-110">**Proxy URL**</span><span class="sxs-lookup"><span data-stu-id="2647c-110">**Proxy URL**</span></span>  
 <span data-ttu-id="2647c-111">輸入 Proxy 伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="2647c-111">Type the URL for the proxy server.</span></span>  
  
 <span data-ttu-id="2647c-112">**在本機上略過 Proxy**</span><span class="sxs-lookup"><span data-stu-id="2647c-112">**Bypass proxy on local**</span></span>  
 <span data-ttu-id="2647c-113">針對本機位址，指定 HTTP 連接管理員是否要略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2647c-113">Specify whether you want the HTTP Connection Manager to bypass the proxy server for local addresses.</span></span>  
  
 <span data-ttu-id="2647c-114">**使用認證**</span><span class="sxs-lookup"><span data-stu-id="2647c-114">**Use credentials**</span></span>  
 <span data-ttu-id="2647c-115">針對 Proxy 伺服器，指定 HTTP 連接管理員是否要使用安全性認證。</span><span class="sxs-lookup"><span data-stu-id="2647c-115">Specify whether you want the HTTP Connection Manager to use security credentials for the proxy server.</span></span>  
  
 <span data-ttu-id="2647c-116">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2647c-116">**User name**</span></span>  
 <span data-ttu-id="2647c-117">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="2647c-117">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="2647c-118">**密碼**</span><span class="sxs-lookup"><span data-stu-id="2647c-118">**Password**</span></span>  
 <span data-ttu-id="2647c-119">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="2647c-119">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="2647c-120">**網域**</span><span class="sxs-lookup"><span data-stu-id="2647c-120">**Domain**</span></span>  
 <span data-ttu-id="2647c-121">如果 HTTP 連接管理員使用認證，您必須指定使用者名稱、密碼，以及網域。</span><span class="sxs-lookup"><span data-stu-id="2647c-121">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="2647c-122">**Proxy 略過清單**</span><span class="sxs-lookup"><span data-stu-id="2647c-122">**Proxy bypass list**</span></span>  
 <span data-ttu-id="2647c-123">輸入您想要略過之 Proxy 伺服器的位址清單。</span><span class="sxs-lookup"><span data-stu-id="2647c-123">The list of addresses for which  you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="2647c-124">**加入**</span><span class="sxs-lookup"><span data-stu-id="2647c-124">**Add**</span></span>  
 <span data-ttu-id="2647c-125">輸入您想要針對它略過 Proxy 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="2647c-125">Type an address for which you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="2647c-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="2647c-126">**Remove**</span></span>  
 <span data-ttu-id="2647c-127">選取一個位址，然後按一下 [移除]\*\*\*\* 來移除它。</span><span class="sxs-lookup"><span data-stu-id="2647c-127">Select an address, and then remove it by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2647c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2647c-128">See Also</span></span>  
 <span data-ttu-id="2647c-129">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2647c-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="2647c-130">HTTP 連線管理員編輯器 &#40;伺服器頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2647c-130">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
  
