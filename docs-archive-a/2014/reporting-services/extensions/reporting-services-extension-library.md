---
title: Reporting Services 延伸模組程式庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d09464ce4a61903a3e9b74711482d2ce07bd0c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596528"
---
# <a name="reporting-services-extension-library"></a><span data-ttu-id="e2759-102">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="e2759-102">Reporting Services Extension Library</span></span>
  <span data-ttu-id="e2759-103">Reporting Services 延伸模組程式庫是一組包括在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的類別、介面和值類型。</span><span class="sxs-lookup"><span data-stu-id="e2759-103">The Reporting Services Extension Library is a set of classes, interfaces, and value types that are included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e2759-104">這個程式庫可以用來存取系統功能，且設計為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 應用程式可用以擴充 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的基礎。</span><span class="sxs-lookup"><span data-stu-id="e2759-104">This library provides access to system functionality and is designed to be the foundation on which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] applications can be used to extend [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span>  
  
## <a name="namespaces"></a><span data-ttu-id="e2759-105">命名空間</span><span class="sxs-lookup"><span data-stu-id="e2759-105">Namespaces</span></span>  
 <span data-ttu-id="e2759-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 延伸程式庫提供下列命名空間。</span><span class="sxs-lookup"><span data-stu-id="e2759-106">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extension library provides the following namespaces.</span></span>  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 <span data-ttu-id="e2759-107">包含的類別與介面可讓您建立元件並擴充 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的資料處理功能。</span><span class="sxs-lookup"><span data-stu-id="e2759-107">Contains classes and interfaces that enable you to build components that extend the data processing capability of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 <span data-ttu-id="e2759-108">包含的類別與介面，可讓您透過自己的傳遞延伸模組建構和傳送自訂通知給使用者，並為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 建立自訂安全性延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e2759-108">Contains classes and interfaces that enable you to construct and send custom notifications to users through your own delivery extensions, and to build custom security extensions for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 `Microsoft.ReportingServices.ReportRendering`  
 <span data-ttu-id="e2759-109">包含的類別與介面可讓您擴充 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的轉譯功能。</span><span class="sxs-lookup"><span data-stu-id="e2759-109">Contains classes and interfaces that enable you to extending the rendering capabilities of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e2759-110">透過使用此命名空間的成員以及 <xref:Microsoft.ReportingServices.Interfaces> 命名空間的成員，就可以為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 建立自己的自訂轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e2759-110">Using the members of this namespace along with members of the <xref:Microsoft.ReportingServices.Interfaces> namespace, you can build your own, custom rendering extensions for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2759-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2759-111">See Also</span></span>  
 [<span data-ttu-id="e2759-112">Reporting Services 延伸模組</span><span class="sxs-lookup"><span data-stu-id="e2759-112">Reporting Services Extensions</span></span>](reporting-services-extensions.md)  
  
  
