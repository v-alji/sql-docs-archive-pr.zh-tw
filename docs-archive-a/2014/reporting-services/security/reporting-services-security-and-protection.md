---
title: Reporting Services 安全性與保護 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f8c7a4186c5236260fb27d8de107ce8c97bd363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606066"
---
# <a name="reporting-services-security-and-protection"></a><span data-ttu-id="9db02-102">Reporting Services 安全性與保護</span><span class="sxs-lookup"><span data-stu-id="9db02-102">Reporting Services Security and Protection</span></span>
  <span data-ttu-id="9db02-103">您可以使用本節的資訊，了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9db02-103">You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9db02-104">本節也將說明 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中所支援的授權模型和驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="9db02-104">This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="9db02-105">驗證擴充保護</span><span class="sxs-lookup"><span data-stu-id="9db02-105">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="9db02-106">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]開始，就有驗證擴充保護的支援可以使用。</span><span class="sxs-lookup"><span data-stu-id="9db02-106">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="9db02-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能可支援使用通道繫結和服務繫結，以增強驗證的保護。</span><span class="sxs-lookup"><span data-stu-id="9db02-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="9db02-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能需要搭配支援擴充保護的作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="9db02-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> <span data-ttu-id="9db02-109">如需詳細資訊，請參閱 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9db02-109">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
## <a name="authentication-and-authorization"></a><span data-ttu-id="9db02-110">驗證和授權</span><span class="sxs-lookup"><span data-stu-id="9db02-110">Authentication and Authorization</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9db02-111">會提供不同的使用者驗證類型和用戶端應用程式，便於使用報表伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="9db02-111">provides different authentication types for users and client applications to authenticate with the report server.</span></span> <span data-ttu-id="9db02-112">為您的報表伺服器使用正確的驗證類型可讓組織獲得組織所需之適當的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="9db02-112">Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization.</span></span> <span data-ttu-id="9db02-113">如需詳細資訊，請參閱 [Authentication with the Report Server](authentication-with-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9db02-113">For more information, see [Authentication with the Report Server](authentication-with-the-report-server.md).</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9db02-114">也會採用角色和權限，控制使用者在報表伺服器目錄中的內容存取 (換句話說，可存取的人員以及存取的方式)。</span><span class="sxs-lookup"><span data-stu-id="9db02-114">also employs roles and permissions to control user access to content in the report server catalog (in other words, who can access what, and how s/he can access it).</span></span> <span data-ttu-id="9db02-115">如需詳細資訊，請參閱[角色與權限 &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9db02-115">For more information, see [Roles and Permissions &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9db02-116">相關工作</span><span class="sxs-lookup"><span data-stu-id="9db02-116">Related Tasks</span></span>  
  
|<span data-ttu-id="9db02-117">工作描述</span><span class="sxs-lookup"><span data-stu-id="9db02-117">Task Descriptions</span></span>|<span data-ttu-id="9db02-118">連結</span><span class="sxs-lookup"><span data-stu-id="9db02-118">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="9db02-119">設定 Secure Socket Layer (SSL) 可保護連線至報表伺服器的用戶端。</span><span class="sxs-lookup"><span data-stu-id="9db02-119">Configure the Secure Socket Layer (SSL) to secure client connections to the report server.</span></span>|[<span data-ttu-id="9db02-120">在原生模式報表伺服器上設定 SSL 連線</span><span class="sxs-lookup"><span data-stu-id="9db02-120">Configure SSL Connections on a Native Mode Report Server</span></span>](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
