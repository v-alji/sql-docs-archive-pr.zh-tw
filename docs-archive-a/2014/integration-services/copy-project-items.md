---
title: 複製專案專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596837"
---
# <a name="copy-project-items"></a><span data-ttu-id="a0a44-102">複製專案項目</span><span class="sxs-lookup"><span data-stu-id="a0a44-102">Copy Project Items</span></span>
  <span data-ttu-id="a0a44-103">本主題描述如何在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案內或在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案之間複製物件。</span><span class="sxs-lookup"><span data-stu-id="a0a44-103">This topic describes how to copy objects within an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="a0a44-104">您也可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 專案的其他類型之間、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]之間複製物件。</span><span class="sxs-lookup"><span data-stu-id="a0a44-104">You can also copy objects between the other types of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] projects, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a0a44-105">若要在兩個專案之間進行複製，專案必須在同一個 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 方案中。</span><span class="sxs-lookup"><span data-stu-id="a0a44-105">To copy between projects, the project must be part of the same [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] solution.</span></span> <span data-ttu-id="a0a44-106">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 專案](integration-services-ssis-projects-and-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a44-106">For more information, see [Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md).</span></span>  
  
### <a name="to-copy-project-level-items"></a><span data-ttu-id="a0a44-107">若要複製專案層級項目</span><span class="sxs-lookup"><span data-stu-id="a0a44-107">To copy project level items</span></span>  
  
1.  <span data-ttu-id="a0a44-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟您要使用的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案或方案。</span><span class="sxs-lookup"><span data-stu-id="a0a44-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or solution that you want to work with.</span></span>  
  
2.  <span data-ttu-id="a0a44-109">展開要從中進行複製的專案和項目資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0a44-109">Expand the project and item folder to copy from.</span></span>  
  
3.  <span data-ttu-id="a0a44-110">以滑鼠右鍵按一下項目，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0a44-110">Right-click the item and click **Copy**.</span></span>  
  
4.  <span data-ttu-id="a0a44-111">以滑鼠右鍵按一下要複製到其中的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，然後按一下 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0a44-111">Right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to copy to and click **Paste**.</span></span>  
  
     <span data-ttu-id="a0a44-112">這些項目會自動複製到正確的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0a44-112">The items are automatically copied to the correct folder.</span></span> <span data-ttu-id="a0a44-113">如果您將項目複製到不是封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，這些項目會複製到 **[其他]** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a0a44-113">If you copy items to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that are not packages, the items are copied to the **Miscellaneous** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a44-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a44-114">See Also</span></span>  
 <span data-ttu-id="a0a44-115">[Integration Services &#40;SSIS&#41; 封裝](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="a0a44-115">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="a0a44-116">複製封裝物件</span><span class="sxs-lookup"><span data-stu-id="a0a44-116">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
  
