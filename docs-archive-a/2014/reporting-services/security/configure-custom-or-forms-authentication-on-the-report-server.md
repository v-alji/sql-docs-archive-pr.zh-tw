---
title: 設定報表伺服器上的自訂或表單驗證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1447e1e695f0e59dbc07b7e19f4df335a1220a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593267"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a><span data-ttu-id="b0336-102">設定報表伺服器上的自訂或表單驗證</span><span class="sxs-lookup"><span data-stu-id="b0336-102">Configure Custom or Forms Authentication on the Report Server</span></span>
  <span data-ttu-id="b0336-103">Reporting Services 提供可延伸的架構，可以讓您插入自訂或表單型驗證延伸模組。</span><span class="sxs-lookup"><span data-stu-id="b0336-103">Reporting Services provides an extensible architecture that allows you to plug in custom or forms-based authentication modules.</span></span> <span data-ttu-id="b0336-104">如果部署需求不包含 Windows 整合式安全性或基本驗證，您可能會考慮實作自訂驗證延伸模組。</span><span class="sxs-lookup"><span data-stu-id="b0336-104">You might consider implementing a custom authentication extension if deployment requirements do not include Windows integrated security or Basic authentication.</span></span> <span data-ttu-id="b0336-105">使用自訂驗證最常見的狀況是支援網際網路或外部網路對 Web 應用程式的存取。</span><span class="sxs-lookup"><span data-stu-id="b0336-105">The most common scenario for using custom authentication is to support Internet or extranet access to a Web application.</span></span> <span data-ttu-id="b0336-106">以自訂的驗證延伸模組取代預設的 Windows 驗證延伸模組時，可讓您進一步控制如何授與外部使用者存取報表伺服器的權限。</span><span class="sxs-lookup"><span data-stu-id="b0336-106">Replacing the default Windows Authentication extension with a custom authentication extension gives you more control over how external users are granted access to the report server.</span></span>  
  
 <span data-ttu-id="b0336-107">實際上，部署自訂驗證延伸模組所需的多個步驟包括複製組件和應用程式檔案、修改組態檔，以及測試。</span><span class="sxs-lookup"><span data-stu-id="b0336-107">In practice, deploying a custom authentication extension requires multiple steps that include copying assemblies and application files, modifying configuration files, and testing.</span></span> <span data-ttu-id="b0336-108">本主題只著重於您在組態檔中所指定的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="b0336-108">This topic focuses on just the authentication settings that you specify in the configuration files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0336-109">建立自訂驗證延伸模組時，需要自訂的程式碼和 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 安全性的專業知識。</span><span class="sxs-lookup"><span data-stu-id="b0336-109">Creating a custom authentication extension requires custom code and expertise in [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] security.</span></span> <span data-ttu-id="b0336-110">如果您不想要建立自訂驗證延伸模組，可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory 群組與帳戶，但必須大幅縮減報表伺服器部署的範圍。</span><span class="sxs-lookup"><span data-stu-id="b0336-110">If you do not want to create a custom authentication extension, you can use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory groups and accounts, but you should greatly reduce the scope of a report server deployment.</span></span> <span data-ttu-id="b0336-111">如需自訂驗證的詳細資訊，請參閱 [實作安全性延伸模組](../extensions/security-extension/implementing-a-security-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="b0336-111">For more information about custom authentication, see [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
 <span data-ttu-id="b0336-112">此外，如果想要在與 SharePoint 產品整合的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 環境中，使用表單驗證或自訂驗證延伸模組，必須將 SharePoint 網站設定為使用您選擇的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="b0336-112">Additionally, if you want to use Forms authentication or a custom authentication extension in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environment that is integrated with a SharePoint product, you must configure the SharePoint site to use the authentication method that you choose.</span></span> <span data-ttu-id="b0336-113">如需在 SharePoint 中設定驗證的詳細資訊，請參閱 [Developer Network (MSDN) 上的](https://go.microsoft.com/fwlink/?LinkId=115575) 驗證範例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b0336-113">For more information about configuring authentication in SharePoint, see [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) on [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a><span data-ttu-id="b0336-114">設定報表伺服器以使用自訂驗證</span><span class="sxs-lookup"><span data-stu-id="b0336-114">To configure a report server to use Custom authentication</span></span>  
  
1.  <span data-ttu-id="b0336-115">在文字編輯器中開啟 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="b0336-115">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="b0336-116">尋找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="b0336-116">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="b0336-117">複製下列 XML 結構：</span><span class="sxs-lookup"><span data-stu-id="b0336-117">Copy the following XML structure:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  <span data-ttu-id="b0336-118">將它貼到 <> 的現有專案上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="b0336-118">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="b0336-119">請注意，您無法搭配其他驗證類型使用 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="b0336-119">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="b0336-120">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b0336-120">Save the file.</span></span>  
  
6.  <span data-ttu-id="b0336-121">開啟報表伺服器的 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="b0336-121">Open the Web.config file for the report server.</span></span> <span data-ttu-id="b0336-122">根據預設，它位於 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer。</span><span class="sxs-lookup"><span data-stu-id="b0336-122">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.</span></span>  
  
7.  <span data-ttu-id="b0336-123">尋找 `authentication mode` 並將其設定為 `Forms`。</span><span class="sxs-lookup"><span data-stu-id="b0336-123">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  <span data-ttu-id="b0336-124">尋找 `identity impersonate` 並將其設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="b0336-124">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. <span data-ttu-id="b0336-125">開啟報表管理員的 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="b0336-125">Open the Web.config file for Report Manager.</span></span> <span data-ttu-id="b0336-126">根據預設，它位於 \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager。</span><span class="sxs-lookup"><span data-stu-id="b0336-126">By default, it is located at \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.</span></span>  
  
10. <span data-ttu-id="b0336-127">尋找 `authentication mode` 並將其設定為 `Forms`。</span><span class="sxs-lookup"><span data-stu-id="b0336-127">Find `authentication mode` and set it `Forms`.</span></span>  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. <span data-ttu-id="b0336-128">尋找 `identity impersonate` 並將其設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="b0336-128">Find `identity impersonate` and set it to `False`.</span></span>  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. <span data-ttu-id="b0336-129">將 `PassThroughCookies` 元素結構加入至組態檔中。</span><span class="sxs-lookup"><span data-stu-id="b0336-129">Add the `PassThroughCookies` element structure to the configuration file.</span></span> <span data-ttu-id="b0336-130">如需詳細資訊，請參閱 [設定報表管理員傳遞自訂驗證 Cookie](configure-the-web-portal-to-pass-custom-authentication-cookies.md)。</span><span class="sxs-lookup"><span data-stu-id="b0336-130">For more information, see [Configure Report Manager to Pass Custom Authentication Cookies](configure-the-web-portal-to-pass-custom-authentication-cookies.md).</span></span>  
  
13. <span data-ttu-id="b0336-131">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b0336-131">Save the file.</span></span>  
  
14. <span data-ttu-id="b0336-132">如果您設定了向外延展部署，請針對部署中的其他報表伺服器重複先前所有的步驟。</span><span class="sxs-lookup"><span data-stu-id="b0336-132">If you configured a scale-out deployment, repeat all of the previous steps for other report servers in the deployment.</span></span>  
  
15. <span data-ttu-id="b0336-133">重新啟動報表伺服器，清除目前開啟的任何工作階段。</span><span class="sxs-lookup"><span data-stu-id="b0336-133">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0336-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0336-134">See Also</span></span>  
 <span data-ttu-id="b0336-135">[實作安全性延伸模組](../extensions/security-extension/implementing-a-security-extension.md) </span><span class="sxs-lookup"><span data-stu-id="b0336-135">[Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md) </span></span>  
 <span data-ttu-id="b0336-136">[使用報表伺服器驗證](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b0336-136">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="b0336-137">[Rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="b0336-137">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="b0336-138">[在報表伺服器上設定基本驗證](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b0336-138">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="b0336-139">設定報表伺服器上的 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="b0336-139">Configure Windows Authentication on the Report Server</span></span>](configure-windows-authentication-on-the-report-server.md)  
  
  
