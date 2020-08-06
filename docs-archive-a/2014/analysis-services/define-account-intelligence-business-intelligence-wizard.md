---
title: ) 的商業智慧 Wizard (定義帳戶智慧Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17b8136e79097cd502d6b239ba6867c4e678c70f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687362"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a><span data-ttu-id="7e676-102">定義帳戶智慧 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="7e676-102">Define Account Intelligence (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="7e676-103">使用 **[定義帳戶智慧]** 頁面，即可將 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上所定義的帳戶類型，對應至資料來源中來源資料表所定義的帳戶類型，該來源資料表會提供帳戶維度的資料。</span><span class="sxs-lookup"><span data-stu-id="7e676-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined by a source table in the data source that supplies the data for the account dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e676-104">如果維度屬性在 [設定維度屬性]\*\*\*\* 頁面上，已對應至 [帳戶類型]\*\*\*\* 屬性類型，就會顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="7e676-104">This page will appear if a dimension attribute was mapped to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e676-105">選項</span><span class="sxs-lookup"><span data-stu-id="7e676-105">Options</span></span>  
 <span data-ttu-id="7e676-106">**來源資料表帳戶類型**</span><span class="sxs-lookup"><span data-stu-id="7e676-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="7e676-107">針對在 [設定維度屬性]\*\*\*\* 頁面上指派給 [帳戶類型]\*\*\*\* 屬性類型的維度屬性，顯示其中所包含的值。</span><span class="sxs-lookup"><span data-stu-id="7e676-107">Displays the values that are contained in the dimension attribute assigned to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
 <span data-ttu-id="7e676-108">**內建帳戶類型**</span><span class="sxs-lookup"><span data-stu-id="7e676-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="7e676-109">選取在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上定義，且對應至來源資料表帳戶類型的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="7e676-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="7e676-110">下表列出在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上定義的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="7e676-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="7e676-111">值</span><span class="sxs-lookup"><span data-stu-id="7e676-111">Value</span></span>|<span data-ttu-id="7e676-112">描述</span><span class="sxs-lookup"><span data-stu-id="7e676-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e676-113">**資產**</span><span class="sxs-lookup"><span data-stu-id="7e676-113">**Asset**</span></span>|<span data-ttu-id="7e676-114">擁有之事物在特定時間點的價值。</span><span class="sxs-lookup"><span data-stu-id="7e676-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="7e676-115">**餘額**</span><span class="sxs-lookup"><span data-stu-id="7e676-115">**Balance**</span></span>|<span data-ttu-id="7e676-116">某項目在特定時間點的計數。</span><span class="sxs-lookup"><span data-stu-id="7e676-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="7e676-117">**費用**</span><span class="sxs-lookup"><span data-stu-id="7e676-117">**Expense**</span></span>|<span data-ttu-id="7e676-118">花費之事物的價值。</span><span class="sxs-lookup"><span data-stu-id="7e676-118">Value of things spent.</span></span>|  
|<span data-ttu-id="7e676-119">**Flow**</span><span class="sxs-lookup"><span data-stu-id="7e676-119">**Flow**</span></span>|<span data-ttu-id="7e676-120">事物的累加計數。</span><span class="sxs-lookup"><span data-stu-id="7e676-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="7e676-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="7e676-121">**Income**</span></span>|<span data-ttu-id="7e676-122">收到之事物的價值。</span><span class="sxs-lookup"><span data-stu-id="7e676-122">Value of things received.</span></span>|  
|<span data-ttu-id="7e676-123">**負債**</span><span class="sxs-lookup"><span data-stu-id="7e676-123">**Liability**</span></span>|<span data-ttu-id="7e676-124">所欠之事物在特定時間點的價值。</span><span class="sxs-lookup"><span data-stu-id="7e676-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="7e676-125">**統計**</span><span class="sxs-lookup"><span data-stu-id="7e676-125">**Statistical**</span></span>|<span data-ttu-id="7e676-126">某項目的計算比率，或者無法彙總之項目的計數。</span><span class="sxs-lookup"><span data-stu-id="7e676-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e676-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e676-127">See Also</span></span>  
 <span data-ttu-id="7e676-128">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7e676-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="7e676-129">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7e676-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7e676-130">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="7e676-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
