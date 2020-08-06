---
title: 定義帳戶智慧 (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90871e2299d1531db1b678b1f4b16ddd7f1db767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598054"
---
# <a name="define-account-intelligence-dimension-wizard"></a><span data-ttu-id="97aa5-102">定義帳戶智慧 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="97aa5-102">Define Account Intelligence (Dimension Wizard)</span></span>
  <span data-ttu-id="97aa5-103">使用 **[定義帳戶智慧]** 頁面，即可將 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上定義的帳戶類型，對應至維度屬性上所定義的帳戶類型，這些帳戶類型與維度中的 **[帳戶類型]** 屬性類型相關聯。</span><span class="sxs-lookup"><span data-stu-id="97aa5-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined in the dimension attribute associated with the **Account Type** attribute type in the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97aa5-104"> 只有在您已選取 **[選取維度類型]** 頁面上的 **[標準維度]** ，而且已將維度屬性對應至 **[指定維度類型]** 頁面上的 **[Account Type]** 屬性類型時，才會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="97aa5-104">This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page and if you mapped a dimension attribute to the **Account Type** attribute type on the **Specify Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97aa5-105">選項</span><span class="sxs-lookup"><span data-stu-id="97aa5-105">Options</span></span>  
 <span data-ttu-id="97aa5-106">**來源資料表帳戶類型**</span><span class="sxs-lookup"><span data-stu-id="97aa5-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="97aa5-107">顯示已指派給 [指定維度索引鍵和類型]\*\*\*\* 頁面中的 [帳戶類型]\*\*\*\* 屬性類型之維度屬性中所含的值。</span><span class="sxs-lookup"><span data-stu-id="97aa5-107">Displays the values contained in the dimension attribute assigned to the **Account Type** attribute type in the **Specify Dimension Key and Type** page.</span></span>  
  
 <span data-ttu-id="97aa5-108">**內建帳戶類型**</span><span class="sxs-lookup"><span data-stu-id="97aa5-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="97aa5-109">選取在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上定義，且對應至來源資料表帳戶類型的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="97aa5-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="97aa5-110">下表列出在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上定義的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="97aa5-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="97aa5-111">值</span><span class="sxs-lookup"><span data-stu-id="97aa5-111">Value</span></span>|<span data-ttu-id="97aa5-112">描述</span><span class="sxs-lookup"><span data-stu-id="97aa5-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97aa5-113">**資產**</span><span class="sxs-lookup"><span data-stu-id="97aa5-113">**Asset**</span></span>|<span data-ttu-id="97aa5-114">擁有之事物在特定時間點的價值。</span><span class="sxs-lookup"><span data-stu-id="97aa5-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="97aa5-115">**餘額**</span><span class="sxs-lookup"><span data-stu-id="97aa5-115">**Balance**</span></span>|<span data-ttu-id="97aa5-116">某項目在特定時間點的計數。</span><span class="sxs-lookup"><span data-stu-id="97aa5-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="97aa5-117">**費用**</span><span class="sxs-lookup"><span data-stu-id="97aa5-117">**Expense**</span></span>|<span data-ttu-id="97aa5-118">花費之事物的價值。</span><span class="sxs-lookup"><span data-stu-id="97aa5-118">Value of things spent.</span></span>|  
|<span data-ttu-id="97aa5-119">**Flow**</span><span class="sxs-lookup"><span data-stu-id="97aa5-119">**Flow**</span></span>|<span data-ttu-id="97aa5-120">事物的累加計數。</span><span class="sxs-lookup"><span data-stu-id="97aa5-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="97aa5-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="97aa5-121">**Income**</span></span>|<span data-ttu-id="97aa5-122">收到之事物的價值。</span><span class="sxs-lookup"><span data-stu-id="97aa5-122">Value of things received.</span></span>|  
|<span data-ttu-id="97aa5-123">**負債**</span><span class="sxs-lookup"><span data-stu-id="97aa5-123">**Liability**</span></span>|<span data-ttu-id="97aa5-124">所欠之事物在特定時間點的價值。</span><span class="sxs-lookup"><span data-stu-id="97aa5-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="97aa5-125">**統計**</span><span class="sxs-lookup"><span data-stu-id="97aa5-125">**Statistical**</span></span>|<span data-ttu-id="97aa5-126">某項目的計算比率，或者無法彙總之項目的計數。</span><span class="sxs-lookup"><span data-stu-id="97aa5-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97aa5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97aa5-127">See Also</span></span>  
 <span data-ttu-id="97aa5-128">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="97aa5-128">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="97aa5-129">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="97aa5-129">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="97aa5-130">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="97aa5-130">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
