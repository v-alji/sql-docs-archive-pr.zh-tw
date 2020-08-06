---
title: " (XMLA) 管理連接和會話 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bfe876f6874193fd0885f16d91caa9f6fe8b172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594770"
---
# <a name="managing-connections-and-sessions-xmla"></a><span data-ttu-id="a4be9-102">管理連接與工作階段 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="a4be9-102">Managing Connections and Sessions (XMLA)</span></span>
  <span data-ttu-id="a4be9-103">*Statefulness*是伺服器在方法呼叫之間保留用戶端身分識別和內容的條件。</span><span class="sxs-lookup"><span data-stu-id="a4be9-103">*Statefulness* is a condition during which the server preserves the identity and context of a client between method calls.</span></span> <span data-ttu-id="a4be9-104">*Statelessness*是一種情況，在此情況中，伺服器不會在方法呼叫完成之後記住用戶端的身分識別和內容。</span><span class="sxs-lookup"><span data-stu-id="a4be9-104">*Statelessness* is a condition during which the server does not remember the identity and context of a client after a method call finishes.</span></span>  
  
 <span data-ttu-id="a4be9-105">為了提供 statefulness，XML for Analysis (XMLA) 支援允許一系列語句一起執行的*會話*。</span><span class="sxs-lookup"><span data-stu-id="a4be9-105">To provide statefulness, XML for Analysis (XMLA) supports *sessions* that allow a series of statements to be performed together.</span></span> <span data-ttu-id="a4be9-106">這樣一系列的陳述式範例，將會建立用於後續查詢的導出成員。</span><span class="sxs-lookup"><span data-stu-id="a4be9-106">An example of such a series of statements would be the creation of a calculated member that is to be used in subsequent queries.</span></span>  
  
 <span data-ttu-id="a4be9-107">一般而言，在 XMLA 中的工作階段會遵循 OLE DB 2.6 規格所述的下列行為：</span><span class="sxs-lookup"><span data-stu-id="a4be9-107">In general, sessions in XMLA follow the following behavior outlined by the OLE DB 2.6 specification:</span></span>  
  
-   <span data-ttu-id="a4be9-108">工作階段定義交易和命令內容範圍。</span><span class="sxs-lookup"><span data-stu-id="a4be9-108">Sessions define transaction and command context scope.</span></span>  
  
-   <span data-ttu-id="a4be9-109">在單一工作階段的內容中可以執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="a4be9-109">Multiple commands can be run in the context of a single session.</span></span>  
  
-   <span data-ttu-id="a4be9-110">XMLA 內容中的交易支援是透過與[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法一起傳送的提供者特定命令。</span><span class="sxs-lookup"><span data-stu-id="a4be9-110">Support for transactions in the XMLA context is through provider-specific commands sent with the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
 <span data-ttu-id="a4be9-111">XMLA 定義了一個方法，可支援在 Web 環境中的工作階段，其所使用的模式類似於分散式撰寫及版本處理 (DAV) 通訊協定所使用的方法，可在鬆散偶合的環境中實作鎖定。</span><span class="sxs-lookup"><span data-stu-id="a4be9-111">XMLA defines a way to support sessions in a Web environment in a mode similar to the approach used by the Distributed Authoring and Versioning (DAV) protocol to implement locking in a loosely coupled environment.</span></span> <span data-ttu-id="a4be9-112">這個實作與 DAV 相似，因為其允許提供者基於各種理由 (例如，逾時或是連接錯誤) 使工作階段過期。</span><span class="sxs-lookup"><span data-stu-id="a4be9-112">This implementation parallels DAV in that the provider is allowed to expire sessions for various reasons (for example, a timeout or connection error).</span></span> <span data-ttu-id="a4be9-113">當再度支援工作階段時，Web 服務必須知道並準備處理必須重新啟動之中斷的命令集。</span><span class="sxs-lookup"><span data-stu-id="a4be9-113">When sessions are supported, Web services must be aware and ready to handle interrupted sets of commands that must be restarted.</span></span>  
  
 <span data-ttu-id="a4be9-114">World Wide Web Consortium (W3C) 簡易物件存取通訊協定 (SOAP) 規格建議使用 SOAP 標頭，在 SOAP 訊息上面建立新的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a4be9-114">The World Wide Web Consortium (W3C) Simple Object Access Protocol (SOAP) specification recommends using SOAP headers for building up new protocols on top of SOAP messages.</span></span> <span data-ttu-id="a4be9-115">下表列出 XMLA 為起始、維護和關閉工作階段，所定義的 SOAP 標頭元素與屬性。</span><span class="sxs-lookup"><span data-stu-id="a4be9-115">The following table lists the SOAP header elements and attributes that XMLA defines for initiating, maintaining, and closing a session.</span></span>  
  
|<span data-ttu-id="a4be9-116">SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="a4be9-116">SOAP header</span></span>|<span data-ttu-id="a4be9-117">描述</span><span class="sxs-lookup"><span data-stu-id="a4be9-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a4be9-118">BeginSession</span><span class="sxs-lookup"><span data-stu-id="a4be9-118">BeginSession</span></span>|<span data-ttu-id="a4be9-119">此標頭要求提供者建立新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="a4be9-119">This header requests the provider to create a new session.</span></span> <span data-ttu-id="a4be9-120">提供者應該建構新的工作階段，並在 SOAP 回應中，將工作階段識別碼與 Session 標頭一起傳回。</span><span class="sxs-lookup"><span data-stu-id="a4be9-120">The provider should respond by constructing a new session and returning the session ID as part of the Session header in the SOAP response.</span></span>|  
|<span data-ttu-id="a4be9-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="a4be9-121">SessionId</span></span>|<span data-ttu-id="a4be9-122">值區域包含的工作階段識別碼，必須用於工作階段其餘部分的每個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="a4be9-122">The value area contains the session ID that must be used in each method call for the rest of the session.</span></span> <span data-ttu-id="a4be9-123">在 SOAP 回應中的提供者會傳送這個標記，而用戶端也必須將這個屬性與每個 Session 標頭元素一起傳送。</span><span class="sxs-lookup"><span data-stu-id="a4be9-123">The provider in the SOAP response sends this tag and the client must also send this attribute with each Session header element.</span></span>|  
|<span data-ttu-id="a4be9-124">工作階段</span><span class="sxs-lookup"><span data-stu-id="a4be9-124">Session</span></span>|<span data-ttu-id="a4be9-125">對於每個發生在工作階段的方法呼叫，都必須使用這個標頭，而且在標頭的值區域中必須包括工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="a4be9-125">For every method call that occurs in the session, this header must be used, and the session ID must be included in the value area of the header.</span></span>|  
|<span data-ttu-id="a4be9-126">EndSession</span><span class="sxs-lookup"><span data-stu-id="a4be9-126">EndSession</span></span>|<span data-ttu-id="a4be9-127">若要結束工作階段，請使用這個標頭。</span><span class="sxs-lookup"><span data-stu-id="a4be9-127">To terminate the session, use this header.</span></span> <span data-ttu-id="a4be9-128">值區域必須包括工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="a4be9-128">The session ID must be included with the value area.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a4be9-129">工作階段識別碼並不保證工作階段會維持有效狀態。</span><span class="sxs-lookup"><span data-stu-id="a4be9-129">A session ID does not guarantee that a session stays valid.</span></span> <span data-ttu-id="a4be9-130">如果工作階段過期 (例如，如果逾時或是連接中斷)，提供者可以選擇結束和回復該工作階段的動作。</span><span class="sxs-lookup"><span data-stu-id="a4be9-130">If the session expires (for example, if it times out or the connection is lost), the provider can choose to end and roll back that session's actions.</span></span> <span data-ttu-id="a4be9-131">因此，所有後續從用戶端對工作階段識別碼發出的方法呼叫都會失敗，並產生指出工作階段無效的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4be9-131">As a result, all subsequent method calls from the client on a session ID fail with an error signaling a session that is not valid.</span></span> <span data-ttu-id="a4be9-132">用戶端應該要處理這個狀況，並準備從頭開始，重新傳送工作階段方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="a4be9-132">A client should handle this condition and be prepared to resend the session method calls from the beginning.</span></span>  
  
## <a name="legacy-code-example"></a><span data-ttu-id="a4be9-133">舊版程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a4be9-133">Legacy Code Example</span></span>  
 <span data-ttu-id="a4be9-134">以下範例將示範如何支援工作階段。</span><span class="sxs-lookup"><span data-stu-id="a4be9-134">The following example shows how sessions are supported.</span></span>  
  
1.  <span data-ttu-id="a4be9-135">若要開始工作階段，請將 SOAP 中的 BeginSession 標頭從用戶端加入輸出 XMLA 方法。</span><span class="sxs-lookup"><span data-stu-id="a4be9-135">To begin the session, add a BeginSession header in SOAP to the outbound XMLA method call from the client.</span></span> <span data-ttu-id="a4be9-136">值區域一開始是空白的，因為還不知道工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="a4be9-136">The value area is initially blank because the session ID is not yet known.</span></span>  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  <span data-ttu-id="a4be9-137">來自提供者的 SOAP 回應訊息會使用 XMLA 標頭標記，將會話識別碼包含在傳回標頭區域中 \<SessionId> 。</span><span class="sxs-lookup"><span data-stu-id="a4be9-137">The SOAP response message from the provider includes the session ID in the return header area, using the XMLA header tag \<SessionId>.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  <span data-ttu-id="a4be9-138">工作階段中的每個方法呼叫都必須加入 Session 標頭，以包含從提供者傳回的工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="a4be9-138">For each method call in the session, the Session header must be added, containing the session ID returned from the provider.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  <span data-ttu-id="a4be9-139">當會話完成時， \<EndSession> 會使用標記，其中包含相關的會話識別碼值。</span><span class="sxs-lookup"><span data-stu-id="a4be9-139">When the session is complete, the \<EndSession> tag is used, containing the related session ID value.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a4be9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4be9-140">See Also</span></span>  
 [<span data-ttu-id="a4be9-141">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="a4be9-141">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
