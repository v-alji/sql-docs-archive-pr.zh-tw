---
title: CLR 整合安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d99d32a061d8fe78a8ac3642a503cceb45f3809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594585"
---
# <a name="clr-integration-security"></a><span data-ttu-id="6cfe6-102">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="6cfe6-102">CLR Integration Security</span></span>
  <span data-ttu-id="6cfe6-103">通用語言執行平臺 (CLR) 的安全性模型，可 [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] 管理及保護在 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 語句或伺服器中執行之另一個 clr 物件的不同類型 clr 和非 CLR 物件之間的存取。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-103">The security model of the [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] statement or another CLR object running in the server.</span></span> <span data-ttu-id="6cfe6-104">這些物件之間的呼叫稱為連結。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-104">The calls between objects are referred to as links.</span></span> <span data-ttu-id="6cfe6-105">針對這些物件所執行的安全性檢查類型會因所涉及的連結類型而不同。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-105">The types of security checks performed on these objects depend on the types of links involved.</span></span>  
  
 <span data-ttu-id="6cfe6-106">CLR 整合安全性模型具有下列目標：</span><span class="sxs-lookup"><span data-stu-id="6cfe6-106">The CLR integration security model has the following goals:</span></span>  
  
-   <span data-ttu-id="6cfe6-107">根據預設，在上執行 managed 使用者程式碼 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-107">By default, running managed user code on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6cfe6-108">執行可能危害 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 健全性的作業應該透過適當的高層級權限保護。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-108">Performing operations that potentially compromise the robustness of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should be protected by appropriate high-level permissions.</span></span>  
  
-   <span data-ttu-id="6cfe6-109">Managed 使用者程式碼不應該取得資料庫中使用者資料或其他使用者程式碼的未經授權存取權。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-109">Managed user code should not gain unauthorized access to user data or other user code in the database.</span></span> <span data-ttu-id="6cfe6-110">使用者定義程式碼應該在叫用它之使用者工作階段的安全性內容底下執行，而且使用該安全性內容的正確權限執行。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-110">User-defined code should run under the security context of the user-session that invoked it, and with the correct privileges for that security context.</span></span>  
  
-   <span data-ttu-id="6cfe6-111">應該要有一些控制項來限制使用者程式碼存取伺服器外部的任何資源，並且針對本機資料存取和計算嚴格使用。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-111">There should be controls for restricting user code from accessing any resources outside the server, using it strictly for local data access and computation.</span></span>  
  
-   <span data-ttu-id="6cfe6-112">使用者定義程式碼不應該透過在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序中執行，取得系統資源的未經授權存取權。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-112">User-defined code should not be able to gain unauthorized access to system resources by virtue of running in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="6cfe6-113">使用 CLR 以程式碼存取為基礎的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-113">with the code access-based security model of the CLR.</span></span> <span data-ttu-id="6cfe6-114">本節將討論這種結合方法對於安全性的一些優點。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-114">Some of the advantages of this combined approach to security are discussed in this section.</span></span>  
  
 <span data-ttu-id="6cfe6-115">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-115">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="6cfe6-116">CLR 整合程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="6cfe6-116">CLR Integration Code Access Security</span></span>](clr-integration-code-access-security.md)  
 <span data-ttu-id="6cfe6-117">討論 Managed 程式碼的程式碼存取安全性 (CAS) 模型。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-117">Discusses the code access security (CAS) model for managed code.</span></span>  
  
 [<span data-ttu-id="6cfe6-118">主機保護屬性和 CLR 整合程式設計</span><span class="sxs-lookup"><span data-stu-id="6cfe6-118">Host Protection Attributes and CLR Integration Programming</span></span>](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 <span data-ttu-id="6cfe6-119">提供不允許在 SAFE 和 EXTERNAL_ACCESS 組件中使用之主機保護屬性 (HPA) 值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-119">Provides information about the host protection attribute (HPA) values that are disallowed in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
 [<span data-ttu-id="6cfe6-120">CLR 整合安全性中的連結</span><span class="sxs-lookup"><span data-stu-id="6cfe6-120">Links in CLR Integration Security</span></span>](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 <span data-ttu-id="6cfe6-121">描述使用者程式碼片段如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-121">Describes how pieces of user-code can call each other in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="6cfe6-122">模擬和 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="6cfe6-122">Impersonation and CLR Integration Security</span></span>](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 <span data-ttu-id="6cfe6-123">討論 Managed 程式碼如何使用模擬來存取外部資源。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-123">Discusses how managed code accesses external resources using impersonation.</span></span>  
  
 [<span data-ttu-id="6cfe6-124">允許部分信任的呼叫端</span><span class="sxs-lookup"><span data-stu-id="6cfe6-124">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 <span data-ttu-id="6cfe6-125">討論 Managed 方法叫用其他組件所包含之類別中的方法時所引發的問題。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-125">Discusses issues that arise when a managed method invokes a method in a class contained in another assembly.</span></span>  
  
 [<span data-ttu-id="6cfe6-126">應用程式網域和 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="6cfe6-126">Application Domains and CLR Integration Security</span></span>](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 <span data-ttu-id="6cfe6-127">描述如何將組件載入應用程式網域中。</span><span class="sxs-lookup"><span data-stu-id="6cfe6-127">Describes how assemblies are loaded into application domains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfe6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cfe6-128">See Also</span></span>  
 [<span data-ttu-id="6cfe6-129">管理 CLR 整合組件</span><span class="sxs-lookup"><span data-stu-id="6cfe6-129">Managing CLR Integration Assemblies</span></span>](../assemblies/managing-clr-integration-assemblies.md)  
  
  
