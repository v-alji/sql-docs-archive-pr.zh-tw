---
title: 延伸模組的安全性考量 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- extensions [Reporting Services], security
- permissions [Reporting Services], extensions
ms.assetid: 58cbdfeb-1105-4a7d-a3b8-b897ff95f367
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e7819f4d6de2003c9982d33ab00cfa0d4030aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606638"
---
# <a name="security-considerations-for-extensions"></a><span data-ttu-id="acea2-102">延伸模組的安全性考量</span><span class="sxs-lookup"><span data-stu-id="acea2-102">Security Considerations for Extensions</span></span>
  <span data-ttu-id="acea2-103">以 Common Language Runtime (CLR) 為目標的每個應用程式，必須和 CLR 安全性系統互動。</span><span class="sxs-lookup"><span data-stu-id="acea2-103">Every application that targets the common language runtime (CLR) must interact with the CLR security system.</span></span> <span data-ttu-id="acea2-104">當這樣的應用程式執行時，CLR 會自動評估它並給與一組權限。</span><span class="sxs-lookup"><span data-stu-id="acea2-104">When such an application runs, it is automatically evaluated and given a set of permissions by the CLR.</span></span> <span data-ttu-id="acea2-105">視應用程式獲得的權限而定，它會繼續執行或是產生安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="acea2-105">Depending on the permissions that the application receives, it either continues running or generates a security exception.</span></span> <span data-ttu-id="acea2-106">特定報表伺服器之安全性原則組態檔中的本機安全性設定與原則，會定義組件獲得的程式碼權限。</span><span class="sxs-lookup"><span data-stu-id="acea2-106">The local security settings and policies in the security policy configuration files for a particular report server define the code permissions that an assembly receives.</span></span>  
  
 <span data-ttu-id="acea2-107">在要求權限之前，您需要知道延伸模組程式碼計劃使用的資源與保護作業，而且也需要知道哪些權限會保護這些資源與作業。</span><span class="sxs-lookup"><span data-stu-id="acea2-107">Before requesting permissions, you need to be aware of the resources and protected operations your extension code is planning to use, and you also need to know which permissions protect those resources and operations.</span></span> <span data-ttu-id="acea2-108">此外，您必須追蹤延伸模組元件呼叫的任何類別庫方法所存取的任何資源。</span><span class="sxs-lookup"><span data-stu-id="acea2-108">In addition, you need to keep track of any resources accessed by any class library methods that are called by the extension components.</span></span> <span data-ttu-id="acea2-109">如需詳細資訊，請參閱《[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 開發人員指南》中的＜要求權限＞。</span><span class="sxs-lookup"><span data-stu-id="acea2-109">For more information, see "Requesting Permissions" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
 <span data-ttu-id="acea2-110">部署到報表伺服器的延伸模組必須以完全信任的方式執行，這表示您的延伸模組必須是授與 **FullTrust** 權限集合之程式碼群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="acea2-110">Extensions deployed to a report server must run as fully trusted, meaning that your extension needs to be part of a code group that is granted the **FullTrust** permission set.</span></span> <span data-ttu-id="acea2-111">這也表示您的延伸模組可以存取透過 CLR 使用的某些伺服器資源與作業，端視為特定報表驗證的使用者而定。</span><span class="sxs-lookup"><span data-stu-id="acea2-111">This also means that your extension may have access to certain server resources and operations available through the CLR depending on the user that is being authenticated for a particular report.</span></span> <span data-ttu-id="acea2-112">如需程式碼群組和延伸模組的詳細資訊，請參閱 [Reporting Services 中的程式碼存取安全性](secure-development/code-access-security-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="acea2-112">For more information about code groups and extensions, see [Code Access Security in Reporting Services](secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="acea2-113">會為所有其延伸模組強制 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 安全性。</span><span class="sxs-lookup"><span data-stu-id="acea2-113">enforces [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security for all of its extensions.</span></span>  
  
 <span data-ttu-id="acea2-114">下列條件適用於在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中部署資料處理、傳遞、轉譯和安全性延伸模組：</span><span class="sxs-lookup"><span data-stu-id="acea2-114">The following conditions apply to the deployment of data processing, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="acea2-115">只有本機管理員有部署延伸模組的權限。</span><span class="sxs-lookup"><span data-stu-id="acea2-115">Only the local administrator has permission to deploy an extension.</span></span>  
  
-   <span data-ttu-id="acea2-116">只有具有適當讀取/寫入權限的使用者可以變更已擴充的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件之組態檔。</span><span class="sxs-lookup"><span data-stu-id="acea2-116">Only users with the appropriate read/write permissions can change the configuration files for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component that is being extended.</span></span>  
  
-   <span data-ttu-id="acea2-117">只有有權限的使用者才有編輯安全性原則檔案的權限，並且允許延伸模組的程式碼存取安全性。</span><span class="sxs-lookup"><span data-stu-id="acea2-117">Only privileged users have permission to edit the security policy files and enable code access security for an extension.</span></span>  
  
 <span data-ttu-id="acea2-118">如需 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 程式碼存取安全性的詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="acea2-118">For more information about code access security in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md).</span></span>  
  
 <span data-ttu-id="acea2-119">如需有關 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 安全性的詳細資訊，請參閱《[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 開發人員指南》中的＜.NET Framework 安全性＞。</span><span class="sxs-lookup"><span data-stu-id="acea2-119">For more information about [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security, see ".NET Framework Security" in your [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
## <a name="initialization-of-extension-assemblies"></a><span data-ttu-id="acea2-120">延伸模組組件的初始化</span><span class="sxs-lookup"><span data-stu-id="acea2-120">Initialization of Extension Assemblies</span></span>  
 <span data-ttu-id="acea2-121">當報表伺服器第一次將延伸模組載入記憶體時，這些延伸模組會使用服務帳戶認證，因為某些延伸模組組件需要特定權限才能存取系統資源、讀取組態檔以及載入其他的相依組件。</span><span class="sxs-lookup"><span data-stu-id="acea2-121">When extensions are first loaded into memory by the report server, they use the service account credentials, because some extension assemblies require specific permissions to access system resources, to read configuration files, and to load other, dependent assemblies.</span></span> <span data-ttu-id="acea2-122">不過，在載入和初始化組件之後，所有對延伸模組組件後續的呼叫，都會使用目前登入的使用者帳戶之認證。</span><span class="sxs-lookup"><span data-stu-id="acea2-122">After an assembly has been loaded and initialized, however, all subsequent calls to extension assemblies use the credentials of the user account that is currently logged on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acea2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acea2-123">See Also</span></span>  
 <span data-ttu-id="acea2-124">[Reporting Services 延伸模組](reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="acea2-124">[Reporting Services Extensions](reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="acea2-125">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="acea2-125">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
  
  
