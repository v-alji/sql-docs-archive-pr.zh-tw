---
title: " (商業智慧 Wizard) 中設定維度屬性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d2e9bc83b7a6d83b6d2808b472d67169266ff07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593046"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a><span data-ttu-id="3b787-102">設定維度屬性 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="3b787-102">Configure Dimension Attributes (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="3b787-103">使用 **[設定維度屬性]** 頁面將維度屬性對應到屬性類型， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會使用這些屬性類型來識別帳戶維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b787-103">Use the **Configure Dimension Attributes** page to map the dimension attributes to the attribute types that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to identify attributes for account dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3b787-104">選項</span><span class="sxs-lookup"><span data-stu-id="3b787-104">Options</span></span>  
 <span data-ttu-id="3b787-105">**維度類型**</span><span class="sxs-lookup"><span data-stu-id="3b787-105">**Dimension type**</span></span>  
 <span data-ttu-id="3b787-106">顯示選取的維度類型。</span><span class="sxs-lookup"><span data-stu-id="3b787-106">Displays the selected dimension type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b787-107">此選項無法使用，因為 `Type` 維度的屬性無法變更為帳戶維度之*帳戶*以外的值。</span><span class="sxs-lookup"><span data-stu-id="3b787-107">This option is not available because the `Type` property of the dimension cannot be changed to a value other than *Account* for account dimensions.</span></span>  
  
 <span data-ttu-id="3b787-108">**[維度屬性]**</span><span class="sxs-lookup"><span data-stu-id="3b787-108">**Dimension attributes**</span></span>  
 <span data-ttu-id="3b787-109">顯示可對應到維度中現有維度屬性的有效屬性類型。</span><span class="sxs-lookup"><span data-stu-id="3b787-109">Displays the valid attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="3b787-110">**涉及**</span><span class="sxs-lookup"><span data-stu-id="3b787-110">**Include**</span></span>  
 <span data-ttu-id="3b787-111">選取核取方塊以包含維度中對應的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="3b787-111">Select a check box to include the corresponding attribute type in the dimension.</span></span>  
  
 <span data-ttu-id="3b787-112">**屬性類型**</span><span class="sxs-lookup"><span data-stu-id="3b787-112">**Attribute Type**</span></span>  
 <span data-ttu-id="3b787-113">列出可對應到維度中現有維度屬性的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="3b787-113">Lists the attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="3b787-114">**維度屬性**</span><span class="sxs-lookup"><span data-stu-id="3b787-114">**Dimension Attribute**</span></span>  
 <span data-ttu-id="3b787-115">選取應該對應到對應屬性類型的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="3b787-115">Select the dimension attribute that should be mapped to the corresponding attribute type.</span></span>  
  
 <span data-ttu-id="3b787-116">**根據帳戶類型，將量值設定為局部加總**</span><span class="sxs-lookup"><span data-stu-id="3b787-116">**Set measures to be semiadditive based on account type**</span></span>  
 <span data-ttu-id="3b787-117">選取此選項，即可根據帳戶類型來變更與這個要彙總之維度相關聯的每個量值。</span><span class="sxs-lookup"><span data-stu-id="3b787-117">Select to change every measure associated with this dimension to be aggregated by account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b787-118">如果商業智慧精靈是從維度設計師啟動，或是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中之 [方案總管] 的某維度上按一下滑鼠右鍵來啟動，則不會出現此選項。</span><span class="sxs-lookup"><span data-stu-id="3b787-118">This option does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b787-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b787-119">See Also</span></span>  
 <span data-ttu-id="3b787-120">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3b787-120">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="3b787-121">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3b787-121">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3b787-122">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="3b787-122">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
