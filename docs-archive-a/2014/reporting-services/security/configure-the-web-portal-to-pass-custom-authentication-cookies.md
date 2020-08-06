---
title: 設定報表管理員以傳遞自訂驗證 Cookie |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90e8798fb91152ec64e7f290dc1522fc8eaa451c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593264"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a><span data-ttu-id="3d75a-102">設定報表管理員傳遞自訂驗證 Cookie</span><span class="sxs-lookup"><span data-stu-id="3d75a-102">Configure Report Manager to Pass Custom Authentication Cookies</span></span>
  <span data-ttu-id="3d75a-103">如果您要使用自訂驗證延伸模組，您應配置報表管理員來傳送自訂驗證 Cookie。</span><span class="sxs-lookup"><span data-stu-id="3d75a-103">If you are using a custom authentication extension, you should configure Report Manager to transmit custom authentication cookies.</span></span> <span data-ttu-id="3d75a-104">否則，報表管理員只能透過報表伺服器特定的 HTTP 要求來傳送 Cookie。</span><span class="sxs-lookup"><span data-stu-id="3d75a-104">Otherwise, Report Manager will only transmit cookies through HTTP requests specific to the report server.</span></span> <span data-ttu-id="3d75a-105">如果您要傳送其他 Cookie，就必須修改 RSReportServer.Config 檔。</span><span class="sxs-lookup"><span data-stu-id="3d75a-105">If you want to transmit additional cookies, you must modify the RSReportServer.Config file.</span></span>  
  
## <a name="modifying-the-rsreportserverconfig-file"></a><span data-ttu-id="3d75a-106">修改 RSReportServer.Config 檔</span><span class="sxs-lookup"><span data-stu-id="3d75a-106">Modifying the RSReportServer.Config File</span></span>  
 <span data-ttu-id="3d75a-107">您可以藉由將 <> 專案新增 `PassThroughCookies` 至 RSReportServer.config 檔案中的報表管理員設定，讓報表管理員將額外的 cookie 傳送至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="3d75a-107">You can enable Report Manager to transmit additional cookies through to the report server by adding a <`PassThroughCookies`> element to the Report Manager configuration settings in the RSReportServer.config file.</span></span> <span data-ttu-id="3d75a-108">當單一登入驗證方案不僅需要報表伺服器驗證 Cookie，同時也需要協力廠商驗證系統提供的 Cookie 時，傳送其他 Cookie 這項功能就顯得非常有用。</span><span class="sxs-lookup"><span data-stu-id="3d75a-108">Transmitting additional cookies is helpful in a single sign-on authentication solution that requires not only the report server authentication cookies, but also cookies from a third-party authentication system.</span></span>  
  
 <span data-ttu-id="3d75a-109">使用報表管理員時，若要能夠透過 HTTP 要求來傳送其他 Cookie，則必須在 RSReportServer.config 檔中設定下列元素：</span><span class="sxs-lookup"><span data-stu-id="3d75a-109">To enable additional cookies to be transmitted through HTTP requests when using Report Manager, set the following elements in the RSReportServer.config file:</span></span>  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d75a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d75a-110">See Also</span></span>  
 <span data-ttu-id="3d75a-111">[使用報表伺服器驗證](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="3d75a-111">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="3d75a-112">[Rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="3d75a-112">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="3d75a-113">[安全性延伸模組概觀](../extensions/security-extension/security-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3d75a-113">[Security Extensions Overview](../extensions/security-extension/security-extensions-overview.md) </span></span>  
 [<span data-ttu-id="3d75a-114">設定和管理報表伺服器 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="3d75a-114">Configure and Administer a Report Server &#40;SSRS Native Mode&#41;</span></span>](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
