---
title: Reporting Services 中的授權 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7420b45175ca0b0a5fc66da4a7939b07b79c75b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596518"
---
# <a name="authorization-in-reporting-services"></a><span data-ttu-id="e18fd-102">Reporting Services 中的授權</span><span class="sxs-lookup"><span data-stu-id="e18fd-102">Authorization in Reporting Services</span></span>
  <span data-ttu-id="e18fd-103">授權這項程序可決定是否應該將要求的存取權類型授與某個識別，允許其對於報表伺服器資料庫中特定資源進行存取。</span><span class="sxs-lookup"><span data-stu-id="e18fd-103">Authorization is the process of determining whether an identity should be granted the requested type of access to a given resource in the report server database.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e18fd-104">使用以角色為基礎的授權架構，會根據應用程式的使用者角色指派，將使用者存取權授與指定的資源。</span><span class="sxs-lookup"><span data-stu-id="e18fd-104">uses a role-based authorization architecture that grants a user access to a given resource based on the user's role assignment for the application.</span></span> <span data-ttu-id="e18fd-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的安全性延伸模組包含授權元件的實作，是用以在使用者通過報表伺服器上的驗證之後，授與存取權給他們。</span><span class="sxs-lookup"><span data-stu-id="e18fd-105">Security extensions for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contain an implementation of an authorization component that is used to grant access to users once they are authenticated on the report server.</span></span> <span data-ttu-id="e18fd-106">當使用者透過 SOAP API 與透過 URL 存取，嘗試在系統上或是報表伺服器項目執行作業時，就會叫用授權。</span><span class="sxs-lookup"><span data-stu-id="e18fd-106">Authorization is invoked when a user attempts to perform an operation on the system or a report server item through the SOAP API and via URL access.</span></span> <span data-ttu-id="e18fd-107">這可以透過安全性延伸模組介面**IAuthorizationExtension**來達成。</span><span class="sxs-lookup"><span data-stu-id="e18fd-107">This is made possible through the security extension interface **IAuthorizationExtension**.</span></span> <span data-ttu-id="e18fd-108">如前所述，您所部署的任何延伸模組都會自 **IExtension** 繼承基底介面。</span><span class="sxs-lookup"><span data-stu-id="e18fd-108">As stated previously, all extensions inherit from **IExtension** the base interface for any extension that you deploy.</span></span> <span data-ttu-id="e18fd-109">**IExtension**和**IAuthorizationExtension**是**microsoft.reportingservices.interfaces.dll**命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="e18fd-109">**IExtension** and **IAuthorizationExtension** are members of the **Microsoft.ReportingServices.Interfaces** namespace.</span></span>

## <a name="checking-access"></a><span data-ttu-id="e18fd-110">檢查存取</span><span class="sxs-lookup"><span data-stu-id="e18fd-110">Checking Access</span></span>
 <span data-ttu-id="e18fd-111">在授權中，任何自訂安全性實作的關鍵在於存取檢查，這個檢查是實作在 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法之中。</span><span class="sxs-lookup"><span data-stu-id="e18fd-111">In authorization, the key to any custom security implementation is the access check, which is implemented in the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span> <span data-ttu-id="e18fd-112">每次使用者嘗試在報表伺服器上執行作業時，就會呼叫 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>。</span><span class="sxs-lookup"><span data-stu-id="e18fd-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> is called each time a user attempts an operation on the report server.</span></span> <span data-ttu-id="e18fd-113">每個作業類型都會多載 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e18fd-113">The <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method is overloaded for each operation type.</span></span> <span data-ttu-id="e18fd-114">若是資料夾作業，存取檢查的範例可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="e18fd-114">For folder operations, an example of an access check might look like the following:</span></span>

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 <span data-ttu-id="e18fd-115">報表伺服器透過傳遞登入使用者的名稱、使用者 Token、項目的安全性描述項，以及要求的作業，來呼叫 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e18fd-115">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method by passing in the name of the logged-on user, a user token, the security descriptor for the item, and the requested operation.</span></span> <span data-ttu-id="e18fd-116">在這裡您將檢查使用者名稱的安全性描述項以及適當的權限以完成要求，然後傳回 `true` 以表示授與存取，或是傳回 `false` 來表示存取遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="e18fd-116">Here you would check the security descriptor for the user name and the appropriate permission to complete the request, then return `true` to signify that access is granted or `false` to signify access is denied.</span></span>

## <a name="security-descriptors"></a><span data-ttu-id="e18fd-117">安全性描述項</span><span class="sxs-lookup"><span data-stu-id="e18fd-117">Security Descriptors</span></span>
 <span data-ttu-id="e18fd-118">在報表伺服器資料庫中，設定項目上的授權原則時，用戶端應用程式 (例如報表管理員) 會將使用者資訊連同項目的安全性原則一起提交到安全性延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e18fd-118">When setting authorization policies on items in the report server database, a client application (such as Report Manager) submits the user information to the security extension along with a security policy for the item.</span></span> <span data-ttu-id="e18fd-119">這個安全性原則與使用者資訊統稱為安全性描述項。</span><span class="sxs-lookup"><span data-stu-id="e18fd-119">This security policy and user information are known collectively as a security descriptor.</span></span> <span data-ttu-id="e18fd-120">安全性描述項在報表伺服器資料庫中包含項目的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e18fd-120">A security descriptor contains the following information for an item in the report server database:</span></span>

-   <span data-ttu-id="e18fd-121">具有某些類型的權限以執行項目上之作業的群組或是使用者。</span><span class="sxs-lookup"><span data-stu-id="e18fd-121">The group or user that has some type of permission to perform operations on the item.</span></span>

-   <span data-ttu-id="e18fd-122">項目類型。</span><span class="sxs-lookup"><span data-stu-id="e18fd-122">The item's type.</span></span>

-   <span data-ttu-id="e18fd-123">控制項目存取的判別存取控制清單。</span><span class="sxs-lookup"><span data-stu-id="e18fd-123">A discretionary access control list controlling access to the item.</span></span>

 <span data-ttu-id="e18fd-124">使用 Web 服務 <xref:ReportService2010.ReportingService2010.SetPolicies%2A> 與 <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> 方法來建立安全性描述項。</span><span class="sxs-lookup"><span data-stu-id="e18fd-124">Security descriptors are created using the Web service <xref:ReportService2010.ReportingService2010.SetPolicies%2A> and <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> methods.</span></span>

### <a name="authorization-flow"></a><span data-ttu-id="e18fd-125">授權流程</span><span class="sxs-lookup"><span data-stu-id="e18fd-125">Authorization Flow</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e18fd-126">授權是由目前設定成在伺服器上執行的安全性延伸模組來控制。</span><span class="sxs-lookup"><span data-stu-id="e18fd-126">authorization is controlled by the security extension currently configured to run on the server.</span></span> <span data-ttu-id="e18fd-127">授權是以角色為基礎，並受限於 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全性架構提供的權限與作業。</span><span class="sxs-lookup"><span data-stu-id="e18fd-127">Authorization is role-based and limited to the permissions and operations supplied by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security architecture.</span></span> <span data-ttu-id="e18fd-128">下圖描述授權使用者的程序，以便在報表伺服器資料庫中的項目上操作：</span><span class="sxs-lookup"><span data-stu-id="e18fd-128">The following diagram depicts the process of authorizing users to operate on items in the report server database:</span></span>

 <span data-ttu-id="e18fd-129">![Reporting Services 安全性授權流程](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services 安全性授權流程")</span><span class="sxs-lookup"><span data-stu-id="e18fd-129">![Reporting Services security authorization flow](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services security authorization flow")</span></span>

 <span data-ttu-id="e18fd-130">如本圖所示，授權會遵循這個順序：</span><span class="sxs-lookup"><span data-stu-id="e18fd-130">As shown in this diagram, authorization follows this sequence:</span></span>

1.  <span data-ttu-id="e18fd-131">一旦驗證之後，用戶端應用程式會透過 Reporting Services Web 服務方法，來向報表伺服器提出要求。</span><span class="sxs-lookup"><span data-stu-id="e18fd-131">Once authenticated, client applications make requests to the report server through the Reporting Services Web service methods.</span></span> <span data-ttu-id="e18fd-132">驗證 Ticket 會以每個 Web 要求的 HTTP 標頭中之 Cookie 形式，傳遞到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="e18fd-132">An authentication ticket is passed to the report server in the form of a cookie in the HTTP header of each Web request.</span></span>

2.  <span data-ttu-id="e18fd-133">Cookie 會在進行任何存取檢查之前先驗證。</span><span class="sxs-lookup"><span data-stu-id="e18fd-133">The cookie is validated prior to any access check.</span></span>

3.  <span data-ttu-id="e18fd-134">一旦驗證 Cookie 之後，報表伺服器就會呼叫 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> 並提供識別給使用者。</span><span class="sxs-lookup"><span data-stu-id="e18fd-134">Once the cookie is validated, the report server calls <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> and the user is given an identity.</span></span>

4.  <span data-ttu-id="e18fd-135">使用者嘗試透過 Reporting Services Web 服務執行作業。</span><span class="sxs-lookup"><span data-stu-id="e18fd-135">The user attempts an operation through the Reporting Services Web service.</span></span>

5.  <span data-ttu-id="e18fd-136">報表伺服器會呼叫 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e18fd-136">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span>

6.  <span data-ttu-id="e18fd-137">會將安全性描述項擷取和傳遞到 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 的自訂安全性延伸模組實作。</span><span class="sxs-lookup"><span data-stu-id="e18fd-137">The security descriptor is retrieved and passed to a custom security extension implementation of <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.</span></span> <span data-ttu-id="e18fd-138">此時，會將使用者、群組或是電腦與被存取的項目之安全性描述項進行比較，並授權可執行要求的作業。</span><span class="sxs-lookup"><span data-stu-id="e18fd-138">At this point, the user, group, or computer is compared to the security descriptor of the item being accessed and is authorized to perform the requested operation.</span></span>

7.  <span data-ttu-id="e18fd-139">如果使用者已獲得授權，則 Web 服務會執行作業，並將回應傳回給呼叫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e18fd-139">If the user is authorized, the Web service performs the operation and returns a response to the calling application.</span></span>


