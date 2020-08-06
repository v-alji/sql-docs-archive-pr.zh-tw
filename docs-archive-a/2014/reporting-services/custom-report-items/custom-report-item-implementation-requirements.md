---
title: 自訂報表項目實作需求 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69fdf58eb385e819b524b9c5b5178997257c797c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709002"
---
# <a name="custom-report-item-implementation-requirements"></a><span data-ttu-id="78870-102">自訂報表項目實作需求</span><span class="sxs-lookup"><span data-stu-id="78870-102">Custom Report Item Implementation Requirements</span></span>
  <span data-ttu-id="78870-103">本主題將討論開發和部署自訂報表項目的必要條件。</span><span class="sxs-lookup"><span data-stu-id="78870-103">This topic will discuss the prerequisites for developing and deploying custom report items.</span></span>  
  
## <a name="development-and-deployment-requirements"></a><span data-ttu-id="78870-104">開發和部署需求</span><span class="sxs-lookup"><span data-stu-id="78870-104">Development and Deployment Requirements</span></span>  
 <span data-ttu-id="78870-105">為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 開發自訂報表項目需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="78870-105">Developing a custom report item for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requires the following:</span></span>  
  
-   <span data-ttu-id="78870-106">使用和執行之伺服器的系統管理存取權 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="78870-106">Administrative access to a server running [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]<span data-ttu-id="78870-107">或更新版本，且 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 已安裝軟體發展工具組 (SDK) 。</span><span class="sxs-lookup"><span data-stu-id="78870-107">or above with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] software development kit (SDK) installed.</span></span>  
  
-   <span data-ttu-id="78870-108">存取 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集。</span><span class="sxs-lookup"><span data-stu-id="78870-108">Access to the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
-   <span data-ttu-id="78870-109">熟悉 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的元件製做與元件模型命名空間。</span><span class="sxs-lookup"><span data-stu-id="78870-109">Familiarity with component authoring and the component model namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="78870-110">如需相關資訊，請參閱 msdn.microsoft.com 上面的＜元件撰寫＞與＜在 Visual Studio 中的元件模型命名空間＞。</span><span class="sxs-lookup"><span data-stu-id="78870-110">For more information, see "Component Authoring" and "Component Model Namespaces in Visual Studio" on msdn.microsoft.com.</span></span>  
  
## <a name="language-and-namespace-requirements"></a><span data-ttu-id="78870-111">語言與命名空間需求</span><span class="sxs-lookup"><span data-stu-id="78870-111">Language and Namespace Requirements</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="78870-112">自訂報表項目完全支援 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="78870-112">custom report items fully support the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="78870-113">您可以使用所選的 .NET 相容語言來開發自訂報表項目。</span><span class="sxs-lookup"><span data-stu-id="78870-113">You can develop custom report items using your choice of .NET-compliant languages.</span></span>  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="78870-114">提供開發人員許多工具與功能，以簡化和加速程式碼撰寫、偵錯和測試的反覆循環，並使部署更加容易。</span><span class="sxs-lookup"><span data-stu-id="78870-114">offers the developer many tools and features to simplify and accelerate the iterative cycles of coding, debugging, and testing and to make deployment easier.</span></span> <span data-ttu-id="78870-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 包括 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 與 C# 編譯器及相關工具。</span><span class="sxs-lookup"><span data-stu-id="78870-115">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK includes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and C# compilers and related tools.</span></span>  
  
-   <span data-ttu-id="78870-116">自訂報表項目使用 `Microsoft.ReportDesigner` 與 <xref:Microsoft.ReportingServices.Interfaces> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="78870-116">Custom report items use the `Microsoft.ReportDesigner` and <xref:Microsoft.ReportingServices.Interfaces> namespaces.</span></span> <span data-ttu-id="78870-117">這些是儲存在 Microsoft.ReportingServices.Designer.DLL 與 Microsoft.ReportingServices.Interfaces.DLL 組件中，是以 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的一部分來安裝。</span><span class="sxs-lookup"><span data-stu-id="78870-117">These are stored in the Microsoft.ReportingServices.Designer.DLL and Microsoft.ReportingServices.Interfaces.DLL assemblies, which are installed as part of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="78870-118">自訂報表項目設計階段元件需要從 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中的 <xref:System.ComponentModel> 命名空間實作介面。</span><span class="sxs-lookup"><span data-stu-id="78870-118">Custom report item design-time components need to implement interfaces from the <xref:System.ComponentModel> namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="78870-119"><xref:System.ComponentModel> 記載於 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集中。</span><span class="sxs-lookup"><span data-stu-id="78870-119">The <xref:System.ComponentModel> is documented in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78870-120">依預設，[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 會隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起安裝，但是不會安裝 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。</span><span class="sxs-lookup"><span data-stu-id="78870-120">By default, the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK is not.</span></span> <span data-ttu-id="78870-121">除非已在電腦上安裝 SDK，而且 SDK 文件集是包含在線上叢書集合中，否則本節中的 SDK 內容連結將不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="78870-121">Unless the SDK is installed on the computer and the SDK documentation is included in the Books Online collection, links to SDK content in this section will not work.</span></span> <span data-ttu-id="78870-122">在安裝 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 之後，您可以遵循[新增或移除 SQL Server 的產品文件集](../../index.yml)中的指示，將 SDK 文件集新增至線上叢書集合和目錄。</span><span class="sxs-lookup"><span data-stu-id="78870-122">After you have installed the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, you can add the SDK documentation to the Books Online collection and table of contents by following the instructions in [Add or Remove Product Documentation for SQL Server](../../index.yml).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78870-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78870-123">See Also</span></span>  
 <span data-ttu-id="78870-124">[建立自訂報表專案執行時間元件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="78870-124">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="78870-125">[建立自訂報表專案設計階段元件](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="78870-125">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="78870-126">[如何：部署自訂報表專案](how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="78870-126">[How to: Deploy a Custom Report Item](how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="78870-127">自訂報表項目類別庫</span><span class="sxs-lookup"><span data-stu-id="78870-127">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
