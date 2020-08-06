---
title: 實作安全性延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e5cf1fa6ce0e0a02a52e6a27f693c152d1f97152
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596513"
---
# <a name="implementing-a-security-extension"></a><span data-ttu-id="27bac-102">實作安全性延伸模組</span><span class="sxs-lookup"><span data-stu-id="27bac-102">Implementing a Security Extension</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="27bac-103">Windows 驗證是保護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中報表的主要系統。</span><span class="sxs-lookup"><span data-stu-id="27bac-103">Windows Authentication is the primary system for securing reports in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="27bac-104">不過，在某些情況下，您可能需要擴充 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全性系統，以配合企業中的自訂安全性。</span><span class="sxs-lookup"><span data-stu-id="27bac-104">In certain cases, however, you may need to extend the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security system to accommodate custom security in your enterprise.</span></span> <span data-ttu-id="27bac-105">您可以使用 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API 提供的開發平台來完成這項動作。</span><span class="sxs-lookup"><span data-stu-id="27bac-105">You can do this using the development platform provided by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="27bac-106">本節將提供 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中安全性延伸模組的概觀。</span><span class="sxs-lookup"><span data-stu-id="27bac-106">This section will present an overview of security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="27bac-107">如需實作、部署和移除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 安全性延伸模組的完整詳細資訊，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="27bac-107">For complete details about implementing, deploying, and removing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension, please see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27bac-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="27bac-108">In This Section</span></span>  
 [<span data-ttu-id="27bac-109">安全性延伸模組概觀</span><span class="sxs-lookup"><span data-stu-id="27bac-109">Security Extensions Overview</span></span>](security-extensions-overview.md)  
 <span data-ttu-id="27bac-110">提供 Reporting Services 安全性延伸模組的概觀。</span><span class="sxs-lookup"><span data-stu-id="27bac-110">Provides an overview of Reporting Services Security Extensions.</span></span>  
  
 [<span data-ttu-id="27bac-111">Reporting Services 中的驗證</span><span class="sxs-lookup"><span data-stu-id="27bac-111">Authentication in Reporting Services</span></span>](authentication-in-reporting-services.md)  
 <span data-ttu-id="27bac-112">討論在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的驗證。</span><span class="sxs-lookup"><span data-stu-id="27bac-112">Discusses authentication in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="27bac-113">Reporting Services 中的授權</span><span class="sxs-lookup"><span data-stu-id="27bac-113">Authorization in Reporting Services</span></span>](authorization-in-reporting-services.md)  
 <span data-ttu-id="27bac-114">涵蓋 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的授權。</span><span class="sxs-lookup"><span data-stu-id="27bac-114">Covers authorization in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bac-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27bac-115">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="27bac-116">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="27bac-116">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="27bac-117">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="27bac-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
