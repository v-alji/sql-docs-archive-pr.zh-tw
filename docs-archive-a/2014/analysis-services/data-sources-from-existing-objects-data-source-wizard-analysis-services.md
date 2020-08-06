---
title: 現有物件中的資料來源 (資料來源 Wizard)  (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 621c938f4902c95dee1e2fcccb0f292597a565f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702112"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a><span data-ttu-id="02510-102">從現有物件建立資料來源 (資料來源精靈) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="02510-102">Data sources from existing objects (Data Source Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="02510-103">使用 **[從現有物件中建立資料來源]** 頁面，即可指定新資料來源將依據的現有資料來源或專案。</span><span class="sxs-lookup"><span data-stu-id="02510-103">Use the **Data sources from existing objects** page to specify an existing data source or project on which to base the new data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="02510-104">選項</span><span class="sxs-lookup"><span data-stu-id="02510-104">Options</span></span>  
 <span data-ttu-id="02510-105">**依據您方案中現有的資料來源建立資料來源。**</span><span class="sxs-lookup"><span data-stu-id="02510-105">**Create a data source based on an existing data source in your solution**</span></span>  
 <span data-ttu-id="02510-106">選取即可將方案中的現有資料來源，作為新資料來源的依據。</span><span class="sxs-lookup"><span data-stu-id="02510-106">Select to base the new data source on an existing data source in the solution.</span></span> <span data-ttu-id="02510-107">建立、重新整理，或部署了使用新資料來源的專案之後，新的資料來源就會從您選取此選項時所指定的資料來源取得設定。</span><span class="sxs-lookup"><span data-stu-id="02510-107">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires the settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="02510-108">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="02510-108">**Data source**</span></span>  
 <span data-ttu-id="02510-109">從資料來源的清單 (清單是依專案來分組) 中，選取新資料來源將依據的資料來源。</span><span class="sxs-lookup"><span data-stu-id="02510-109">Select a data source on which you want to base the new data source from the list of data sources, which is grouped by project.</span></span>  
  
 <span data-ttu-id="02510-110">**依據 Analysis Services 專案建立資料來源。**</span><span class="sxs-lookup"><span data-stu-id="02510-110">**Create a data source based on an Analysis Services project**</span></span>  
 <span data-ttu-id="02510-111">選取即可建立參考 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 目前方案中另一個專案的新資料來源 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02510-111">Select to create a new data source that references another [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in the current solution.</span></span> <span data-ttu-id="02510-112">新資料來源會從所選取專案的 `TargetServer` 和 `TargetDatabase` 屬性中取得設定。</span><span class="sxs-lookup"><span data-stu-id="02510-112">The new data source acquires settings from the `TargetServer` and `TargetDatabase` properties of the selected project.</span></span> <span data-ttu-id="02510-113">建立、重新整理，或部署了使用新資料來源的專案之後，新的資料來源就會從您選取此選項時所指定的資料來源取得設定。</span><span class="sxs-lookup"><span data-stu-id="02510-113">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="02510-114">**專案**</span><span class="sxs-lookup"><span data-stu-id="02510-114">**Project**</span></span>  
 <span data-ttu-id="02510-115">在新的資料來源中選取您要參考的專案。</span><span class="sxs-lookup"><span data-stu-id="02510-115">Select the project that you want to reference in the new data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02510-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02510-116">See Also</span></span>  
 <span data-ttu-id="02510-117">[資料來源 Wizard F1 說明 &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="02510-117">[Data Source Wizard F1 Help &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span></span>  
 <span data-ttu-id="02510-118">[多維度模型中的資料來源](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="02510-118">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="02510-119">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="02510-119">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
