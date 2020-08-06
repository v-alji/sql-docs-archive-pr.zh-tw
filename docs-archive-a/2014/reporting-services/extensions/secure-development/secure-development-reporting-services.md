---
title: 安全開發 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ba284b9013c5da6b03cce06ec72deccb045cfad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607269"
---
# <a name="secure-development-reporting-services"></a><span data-ttu-id="afa93-102">安全開發 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="afa93-102">Secure Development (Reporting Services)</span></span>
  <span data-ttu-id="afa93-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供了強固的安全性系統，可在嚴格控制、管理員定義的安全性環境中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="afa93-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a robust security system that can run code in tightly constrained, administrator-defined security contexts.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="afa93-104">會使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 安全性系統，也稱為程式碼存取安全性 (或是證據型安全性)。</span><span class="sxs-lookup"><span data-stu-id="afa93-104">uses the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] security system, known as code access security (or evidence-based security).</span></span> <span data-ttu-id="afa93-105">在程式碼存取安全性之下，系統會信任使用者存取資源，但是如果使用者執行的程式碼未獲得信任，該資源的存取將會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="afa93-105">Under code access security, a user may be trusted to access a resource, but if the code the user executes is not trusted, access to the resource will be denied.</span></span>  
  
 <span data-ttu-id="afa93-106">根據程式碼的安全性 (相對於特定使用者) 可允許針對 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 開發的自訂組件或資料、傳遞、轉譯和安全性延伸模組來表示安全性。</span><span class="sxs-lookup"><span data-stu-id="afa93-106">Security based on code, as opposed to specific users, permits security to be expressed for custom assemblies or data, delivery, rendering, and security extensions that you develop for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="afa93-107">您的延伸模組程式碼可由任意數目的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用者來執行，這些使用者在開發時間都是未知的。</span><span class="sxs-lookup"><span data-stu-id="afa93-107">Your extension code may be executed by any number of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] users, all of whom are unknown at development time.</span></span> <span data-ttu-id="afa93-108">您所開發的自訂組件或延伸模組需要 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的特定安全性原則。</span><span class="sxs-lookup"><span data-stu-id="afa93-108">The custom assemblies or extensions that you develop require specific security policies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="afa93-109">這些安全性原則會表示為 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的類型。</span><span class="sxs-lookup"><span data-stu-id="afa93-109">These security policies are represented as types in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="afa93-110">如需有關程式碼存取安全性的詳細資訊，請參閱 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 文件集中的「程式碼存取安全性」。</span><span class="sxs-lookup"><span data-stu-id="afa93-110">For a more information about code access security, see "Code Access Security" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afa93-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="afa93-111">In This Section</span></span>  
 [<span data-ttu-id="afa93-112">Reporting Services 中的程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="afa93-112">Code Access Security in Reporting Services</span></span>](code-access-security-in-reporting-services.md)  
 <span data-ttu-id="afa93-113">介紹 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中自訂組件和延伸模組的程式碼存取安全性和原則組態。</span><span class="sxs-lookup"><span data-stu-id="afa93-113">Introduces code access security and policy configuration for custom assemblies and extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="afa93-114">了解安全性原則</span><span class="sxs-lookup"><span data-stu-id="afa93-114">Understanding Security Policies</span></span>](understanding-security-policies.md)  
 <span data-ttu-id="afa93-115">描述 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的各種組件類型，以及程式碼存取安全性如何影響程式碼權限。</span><span class="sxs-lookup"><span data-stu-id="afa93-115">Describes the various assembly types in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and how code access security affects code permissions.</span></span>  
  
 [<span data-ttu-id="afa93-116">使用 Reporting Services 安全性原則檔</span><span class="sxs-lookup"><span data-stu-id="afa93-116">Using Reporting Services Security Policy Files</span></span>](using-reporting-services-security-policy-files.md)  
 <span data-ttu-id="afa93-117">描述不同的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 元件及對應的原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="afa93-117">Describes the different [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components and the corresponding policy configuration files.</span></span>  
  
  
