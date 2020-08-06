---
title: Power View 報表屬性 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 51205c2d-b6ce-4b92-afd2-58e399a81691
author: minewiskan
ms.author: owend
ms.openlocfilehash: e85d91578e5c3f4b47f56eeb86aa738e37e8f59b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687193"
---
# <a name="power-view-reporting-properties-ssas-tabular"></a><span data-ttu-id="14673-102">Power View 報表屬性 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="14673-102">Power View Reporting Properties (SSAS Tabular)</span></span>
  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="14673-103">為商業使用者 (例如資料分析師、企業決策者和資訊工作者) 提供了直覺式的隨選報表。</span><span class="sxs-lookup"><span data-stu-id="14673-103">provides intuitive ad-hoc reporting for business users such as data analysts, business decision makers, and information workers.</span></span> <span data-ttu-id="14673-104">他們可以從根據 PowerPivot 圖庫中發行的 PowerPivot 活頁簿的表格式模型或是使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 撰寫的表格式模型，輕鬆地建立資料檢視並與其互動，然後將其部署到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14673-104">They can easily create and interact with views of data from tabular models based on PowerPivot workbooks published in a PowerPivot Gallery, or tabular models authored by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and then deployed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services instances.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="14673-105">是從 SharePoint Server 2010 或更新版本啟動的瀏覽器型 Silverlight 應用程式。</span><span class="sxs-lookup"><span data-stu-id="14673-105">is a browser-based Silverlight application launched from SharePoint Server 2010 or later.</span></span>  
  
 <span data-ttu-id="14673-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中撰寫表格式模型專案時，您可以設定 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表特有的某些報表屬性。</span><span class="sxs-lookup"><span data-stu-id="14673-106">When authoring tabular model projects in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can configure certain reporting properties unique to [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="14673-107">本節的主題描述如何最佳化模型來提升 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中的報告體驗。</span><span class="sxs-lookup"><span data-stu-id="14673-107">Topics in this section describe how to optimize a model to improve the reporting experience in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="14673-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="14673-108">Related Tasks</span></span>  
  
|<span data-ttu-id="14673-109">主題</span><span class="sxs-lookup"><span data-stu-id="14673-109">Topic</span></span>|<span data-ttu-id="14673-110">描述</span><span class="sxs-lookup"><span data-stu-id="14673-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="14673-111">設定 Power View 報表的預設欄位集 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="14673-111">Configure Default Field Set for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-default-field-set-for-reports.md)|<span data-ttu-id="14673-112">描述如何設定預設欄位集，這是預先定義的資料行和量值的清單，當您選取報表欄位清單中的資料表時，此清單會自動加入至 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表畫布。</span><span class="sxs-lookup"><span data-stu-id="14673-112">Describes how to configure a Default Field Set; a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span>|  
|[<span data-ttu-id="14673-113">設定 Power View 報表的資料表行為屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="14673-113">Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-table-behavior-properties-for-reports.md)|<span data-ttu-id="14673-114">描述如何設定資料表行為屬性，以更精細的層級來公開詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="14673-114">Describes how to configure table behavior properties that expose detail rows at a more granular level.</span></span> <span data-ttu-id="14673-115">設定資料表行為屬性會變更詳細資料列的群組行為，並讓識別資訊在圖格、卡片和圖表版面配置中有更好的預設位置。</span><span class="sxs-lookup"><span data-stu-id="14673-115">Setting table behavior properties changes the grouping behavior of detail rows and produces a better default placement of identifying information in tile, card, and chart layouts.</span></span>|  
  
  
