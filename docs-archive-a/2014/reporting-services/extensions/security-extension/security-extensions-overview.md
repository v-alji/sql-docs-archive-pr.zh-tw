---
title: 安全性延伸模組概觀 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9cd6c2a1518b724a7faafecdb2926505694e9707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596511"
---
# <a name="security-extensions-overview"></a><span data-ttu-id="3bdf1-102">安全性延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="3bdf1-102">Security Extensions Overview</span></span>
  <span data-ttu-id="3bdf1-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全性延伸模組會啟用使用者或群組的驗證和授權；也就是說，它會讓不同的使用者登入到報表伺服器，並根據其識別執行不同的工作或作業。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-103">A [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension enables the authentication and authorization of users or groups; that is, it enables different users to log on to a report server and, based on their identities, perform different tasks or operations.</span></span> <span data-ttu-id="3bdf1-104">依預設，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 會使用 Windows 架構的驗證延伸模組，此模組使用 Windows 帳戶通訊協定來確認宣稱在系統上具有帳戶之使用者的識別。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-104">By default, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a Windows-based authentication extension, which uses Windows account protocols to verify the identities of users who claim to have accounts on the system.</span></span> <span data-ttu-id="3bdf1-105">以 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 會使用以角色為基礎的安全性系統來授權使用者。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a role-based security system to authorize users.</span></span> <span data-ttu-id="3bdf1-106">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 以角色為基礎的安全性模型類似於其他技術以角色為基礎的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-106">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] role-based security model is similar to the role-based security models of other technologies.</span></span>

 <span data-ttu-id="3bdf1-107">因為安全性延伸模組是以開放且可延伸的 API 為基礎，所以您可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中建立新的驗證和授權延伸模組。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-107">Because security extensions are based on an open and extensible API, you can create new authentication and authorization extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3bdf1-108">以下是一般安全性延伸模組實作的範例，此實作會使用以表單為基礎的驗證和授權：</span><span class="sxs-lookup"><span data-stu-id="3bdf1-108">The following is an example of a typical security extension implementation that uses Forms-based authentication and authorization:</span></span>

 <span data-ttu-id="3bdf1-109">![Reporting Services 安全性延伸模組處理序](../../media/rosettasecurityextensionflow.gif "Reporting Services 安全性延伸模組處理序")</span><span class="sxs-lookup"><span data-stu-id="3bdf1-109">![Reporting Services security extension process](../../media/rosettasecurityextensionflow.gif "Reporting Services security extension process")</span></span>

 <span data-ttu-id="3bdf1-110">如下圖所顯示，驗證和授權的進行方式如下：</span><span class="sxs-lookup"><span data-stu-id="3bdf1-110">As shown in the illustration, authentication and authorization occur as follows:</span></span>

1.  <span data-ttu-id="3bdf1-111">使用者使用 URL 來嘗試存取報表管理員，然後被重新導向至針對用戶端應用程式而收集使用者認證的表單。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-111">A user tries to access Report Manager by using a URL and is redirected to a form that collects user credentials for the client application.</span></span>

2.  <span data-ttu-id="3bdf1-112">使用者將認證提交給表單。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-112">The user submits credentials to the form.</span></span>

3.  <span data-ttu-id="3bdf1-113">使用者認證透過 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法提交給 Reporting Services Web 服務。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-113">The user credentials are submitted to the Reporting Services Web service through the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span>

4.  <span data-ttu-id="3bdf1-114">Web 服務呼叫客戶所提供的安全性延伸模組，並且確認自訂的安全性授權中具有使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-114">The Web service calls the customer-supplied security extension and verifies that the user name and password exist in the custom security authority.</span></span>

5.  <span data-ttu-id="3bdf1-115">在進行驗證後，Web 服務會建立驗證 Ticket (也稱為 "Cookie")、管理 Ticket，然後針對報表管理員的首頁確認使用者的角色。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-115">After authentication, the Web service creates an authentication ticket (known as a "cookie"), manages the ticket, and verifies the user's role for the Home page of Report Manager.</span></span>

6.  <span data-ttu-id="3bdf1-116">Web 服務將 Cookie 傳回給瀏覽器，並在報表管理員中顯示適當的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-116">The Web service returns the cookie to the browser and displays the appropriate user interface in Report Manager.</span></span>

7.  <span data-ttu-id="3bdf1-117">在使用者經過驗證後，瀏覽器會以 HTTP 標頭傳送 Cookie 以對報表管理員提出要求。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-117">After the user is authenticated, the browser makes requests to Report Manager while transmitting the cookie in the HTTP header.</span></span> <span data-ttu-id="3bdf1-118">這些要求是用於回應報表管理員應用程式中的使用者動作。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-118">These requests are in response to user actions within the Report Manager application.</span></span>

8.  <span data-ttu-id="3bdf1-119">Cookie 會在 HTTP 標頭中，與所要求的使用者作業一起傳送給 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-119">The cookie is transmitted in the HTTP header to the Web service along with the requested user operation.</span></span>

9. <span data-ttu-id="3bdf1-120">對 Cookie 進行驗證，如為有效，則報表伺服器會從報表伺服器資料庫傳回安全性描述項，以及與所要求作業相關的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-120">The cookie is validated, and if it is valid, the report server returns the security descriptor and other information relating to the requested operation from the report server database.</span></span>

10. <span data-ttu-id="3bdf1-121">如果 Cookie 有效，則報表伺服器會呼叫安全性延伸模組，以檢查是否授權使用者執行特定的作業。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-121">If the cookie is valid, the report server makes a call to the security extension to check if the user is authorized to perform the specific operation.</span></span>

11. <span data-ttu-id="3bdf1-122">如果使用者已獲得授權，則報表伺服器會執行要求的作業，並將控制項傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-122">If the user is authorized, the report server performs the requested operation and returns control to the caller.</span></span>

12. <span data-ttu-id="3bdf1-123">在使用者經過驗證後，對報表伺服器的 URL 存取會使用相同的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-123">After the user is authenticated, URL access to the report server uses the same cookie.</span></span> <span data-ttu-id="3bdf1-124">Cookie 會以 HTTP 標頭傳輸。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-124">The cookie is transmitted in the HTTP header.</span></span>

13. <span data-ttu-id="3bdf1-125">使用者會繼續在報表伺服器上要求作業，直到工作階段結束。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-125">The user continues to request operations on the report server until the session has ended.</span></span>

## <a name="when-to-implement-a-security-extension"></a><span data-ttu-id="3bdf1-126">何時實作安全性延伸模組</span><span class="sxs-lookup"><span data-stu-id="3bdf1-126">When to Implement a Security Extension</span></span>
 <span data-ttu-id="3bdf1-127">我們建議您盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-127">We recommend that you use Windows Authentication if at all possible.</span></span> <span data-ttu-id="3bdf1-128">不過，下列兩個案例可能比較適合 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的自訂驗證和授權：</span><span class="sxs-lookup"><span data-stu-id="3bdf1-128">However, custom authentication and authorization for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] may be appropriate in the following two cases:</span></span>

-   <span data-ttu-id="3bdf1-129">您具有無法使用 Windows 帳戶的網際網路或外部網路應用程式。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-129">You have an Internet or extranet application that cannot use Windows accounts.</span></span>

-   <span data-ttu-id="3bdf1-130">您具有自訂的使用者和角色，而且需要在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中提供相符的授權配置。</span><span class="sxs-lookup"><span data-stu-id="3bdf1-130">You have custom-defined users and roles and need to provide a matching authorization scheme in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="3bdf1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bdf1-131">See Also</span></span>
 <span data-ttu-id="3bdf1-132">[執行安全性延伸](../security-extension/implementing-a-security-extension.md)模組[設定報表管理員傳遞自訂驗證 cookie](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span><span class="sxs-lookup"><span data-stu-id="3bdf1-132">[Implementing a Security Extension](../security-extension/implementing-a-security-extension.md) [Configure Report Manager to Pass Custom Authentication Cookies](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)</span></span>


