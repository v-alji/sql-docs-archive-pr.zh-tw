---
title: SSAS 表格式) 的屬性 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a59d3448-8619-4044-923b-8effba926dfa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d8c77ffbe8e185e15b716819498fe48295348e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687180"
---
# <a name="properties-ssas-tabular"></a><span data-ttu-id="380ac-102">屬性 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="380ac-102">Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="380ac-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的表格式模型專案包含各種屬性，可定義專案、模型、報表及部署的行為。</span><span class="sxs-lookup"><span data-stu-id="380ac-103">Tabular model projects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] have various properties that define behaviors for the project, model, reporting, and deployment.</span></span> <span data-ttu-id="380ac-104">屬性設定會以 XML 格式儲存在 Model.bim 檔案中，但是本節所述的所有屬性都可以在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的 [屬性]\*\*\*\* 視窗中設定。</span><span class="sxs-lookup"><span data-stu-id="380ac-104">Property settings are stored in XML format in the Model.bim file, however, all of the properties described in this section can be configured in the **Properties** windows in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="380ac-105">相關工作</span><span class="sxs-lookup"><span data-stu-id="380ac-105">Related Tasks</span></span>  
  
|<span data-ttu-id="380ac-106">主題</span><span class="sxs-lookup"><span data-stu-id="380ac-106">Topic</span></span>|<span data-ttu-id="380ac-107">描述</span><span class="sxs-lookup"><span data-stu-id="380ac-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="380ac-108">Power View 報表屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-108">Power View Reporting Properties &#40;SSAS Tabular&#41;</span></span>](power-view-reporting-properties-ssas-tabular.md)|<span data-ttu-id="380ac-109">本節中的主題針對將連接到 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]和從中進行瀏覽的表格式模型提供說明和組態選項。</span><span class="sxs-lookup"><span data-stu-id="380ac-109">Topics in this section provide descriptions and configuration options for tabular models that will be connected to and browsed from [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>|  
|[<span data-ttu-id="380ac-110">專案屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-110">Project Properties &#40;SSAS Tabular&#41;</span></span>](project-properties-ssas-tabular.md)|<span data-ttu-id="380ac-111">提供專案屬性的說明。</span><span class="sxs-lookup"><span data-stu-id="380ac-111">Provides descriptions for project properties.</span></span> <span data-ttu-id="380ac-112">專案屬性包含專案檔案和部署選項設定。</span><span class="sxs-lookup"><span data-stu-id="380ac-112">Project properties include project file and deployment options settings.</span></span>|  
|[<span data-ttu-id="380ac-113">模型屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-113">Model Properties &#40;SSAS Tabular&#41;</span></span>](model-properties-ssas-tabular.md)|<span data-ttu-id="380ac-114">提供模型屬性的說明。</span><span class="sxs-lookup"><span data-stu-id="380ac-114">Provides descriptions for model properties.</span></span> <span data-ttu-id="380ac-115">模型屬性會在模型製作期間影響模型專案的建置動作、備份及工作空間資料庫。</span><span class="sxs-lookup"><span data-stu-id="380ac-115">Model properties affect the model project's build actions, backup, and workspace database during model authoring.</span></span>|  
|[<span data-ttu-id="380ac-116">資料表屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-116">Table Properties &#40;SSAS Tabular&#41;</span></span>](table-properties-ssas-tabular.md)|<span data-ttu-id="380ac-117">提供基本資料表屬性的說明。</span><span class="sxs-lookup"><span data-stu-id="380ac-117">Provides descriptions for basic table properties.</span></span> <span data-ttu-id="380ac-118">這裡所述的資料表屬性與 [編輯資料表屬性] 對話方塊中的屬性不同，前者會顯示並允許選擇及篩選來源的資料行。</span><span class="sxs-lookup"><span data-stu-id="380ac-118">Table properties described here are different from those in the Edit Table Properties dialog box, which display and allow selection and filtering of columns from the source,</span></span>|  
|[<span data-ttu-id="380ac-119">資料行屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-119">Column Properties &#40;SSAS Tabular&#41;</span></span>](column-properties-ssas-tabular.md)|<span data-ttu-id="380ac-120">提供資料行屬性的說明。</span><span class="sxs-lookup"><span data-stu-id="380ac-120">Provides descriptions for column properties.</span></span> <span data-ttu-id="380ac-121">資料行屬性會定義資料行的資料類型、格式和隱藏設定。</span><span class="sxs-lookup"><span data-stu-id="380ac-121">Column properties define a column's data type, format, and hiding settings.</span></span>|  
|[<span data-ttu-id="380ac-122">設定預設的資料模型和部署屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="380ac-122">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)|<span data-ttu-id="380ac-123">提供預設模型和部署屬性的說明及組態步驟。</span><span class="sxs-lookup"><span data-stu-id="380ac-123">Provides descriptions and configuration steps for default modeling and deployment properties.</span></span> <span data-ttu-id="380ac-124">預設屬性會套用至新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="380ac-124">Default properties apply to new tabular model projects.</span></span> <span data-ttu-id="380ac-125">建立專案之後，這些屬性可依據您的需求針對特定模型專案進行變更。</span><span class="sxs-lookup"><span data-stu-id="380ac-125">After a project is created, these properties can be changed for a particular model project depending on your requirements.</span></span>|  
  
  
