---
title: 選取建立方法 (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensiondefinition.f1
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6338a0bde7865482fb7a98d7ec36ba5a71feb806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687254"
---
# <a name="select-creation-method-dimension-wizard"></a><span data-ttu-id="9643d-102">選取建立方法 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="9643d-102">Select Creation Method (Dimension Wizard)</span></span>
  <span data-ttu-id="9643d-103">使用 **[選取建立方法]** 頁面，即可選取建立維度的方式。</span><span class="sxs-lookup"><span data-stu-id="9643d-103">Use the **Select Creation Method** page to select how to create the dimension.</span></span>  
  
 <span data-ttu-id="9643d-104">**開啟維度精靈**</span><span class="sxs-lookup"><span data-stu-id="9643d-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="9643d-105">在方案總管\*\*\*\* 的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案的 [維度]\*\*\*\* 資料夾，然後按一下 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9643d-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9643d-106">選項</span><span class="sxs-lookup"><span data-stu-id="9643d-106">Options</span></span>  
 <span data-ttu-id="9643d-107">**使用現有的資料表**</span><span class="sxs-lookup"><span data-stu-id="9643d-107">**Use an existing table**</span></span>  
 <span data-ttu-id="9643d-108">根據資料來源中的一個或多個資料表，建立維度。</span><span class="sxs-lookup"><span data-stu-id="9643d-108">Create a dimension from one or more tables in a data source.</span></span> <span data-ttu-id="9643d-109">適用於維度的屬性將會因資料表中資料的結構而不同。</span><span class="sxs-lookup"><span data-stu-id="9643d-109">The attributes that are available for the dimension will depend on the structure of the data in the table.</span></span>  
  
 <span data-ttu-id="9643d-110">如需詳細資訊，請參閱 [使用現有的資料表建立維度](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)。</span><span class="sxs-lookup"><span data-stu-id="9643d-110">For more information, see [Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md).</span></span>  
  
 <span data-ttu-id="9643d-111">**在資料來源中產生時間資料表**</span><span class="sxs-lookup"><span data-stu-id="9643d-111">**Generate a time table in the data source**</span></span>  
 <span data-ttu-id="9643d-112">在基礎資料來源中建立時間資料表，然後使用該資料表來建立時間維度。</span><span class="sxs-lookup"><span data-stu-id="9643d-112">Create a time table in the underlying data source and then use that table to create a time dimension.</span></span> <span data-ttu-id="9643d-113">沒有這類資料表存在，而且您不想要使用指令碼來建立資料表時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="9643d-113">Use this option when no such table exists and you do not want to use a script to create one.</span></span> <span data-ttu-id="9643d-114">新的時間資料表將包含您在精靈中指定之日期範圍、屬性和日曆的資料。</span><span class="sxs-lookup"><span data-stu-id="9643d-114">The new time table will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9643d-115">若要使用這個選項，您必須擁有在基礎資料來源中建立物件的權限。</span><span class="sxs-lookup"><span data-stu-id="9643d-115">To use this option, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="9643d-116">如果您沒有在資料來源上建立物件的權限，請嘗試改用 **[在伺服器上產生時間資料表]** 選項。</span><span class="sxs-lookup"><span data-stu-id="9643d-116">If you do not have permission to create objects on the data source, try to use the **Generate a time table on the server** option instead.</span></span>  
  
 <span data-ttu-id="9643d-117">如需詳細資訊，請參閱 [產生時間資料表來建立時間維度](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)。</span><span class="sxs-lookup"><span data-stu-id="9643d-117">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="9643d-118">**[在伺服器上產生時間資料表]**</span><span class="sxs-lookup"><span data-stu-id="9643d-118">**Generate a time table on the server**</span></span>  
 <span data-ttu-id="9643d-119">直接在伺服器上建立時間資料表，然後使用該資料表來建立時間維度。</span><span class="sxs-lookup"><span data-stu-id="9643d-119">Create a time table directly on the server and then use that table to create a time dimension.</span></span> <span data-ttu-id="9643d-120">如果您沒有在基礎資料來源中建立物件的權限，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="9643d-120">Use this option if you do not have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="9643d-121">新的時間維度將包含您在精靈中指定之日期範圍、屬性和日曆的資料。</span><span class="sxs-lookup"><span data-stu-id="9643d-121">The new time dimension will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
 <span data-ttu-id="9643d-122">如需詳細資訊，請參閱 [產生時間資料表來建立時間維度](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)。</span><span class="sxs-lookup"><span data-stu-id="9643d-122">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="9643d-123">**在資料來源中產生非時間資料表**</span><span class="sxs-lookup"><span data-stu-id="9643d-123">**Generate a non-time table in the data source**</span></span>  
 <span data-ttu-id="9643d-124">定義不含基礎關聯式資料來源的維度，然後針對資料來源產生必要的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9643d-124">Design the dimension without an underlying relational data source, and then generate the necessary schema for the data source.</span></span> <span data-ttu-id="9643d-125">這種方法稱為由上而下的模型。</span><span class="sxs-lookup"><span data-stu-id="9643d-125">This approach is known as top-down modeling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9643d-126">若要使用這個選項，您必須擁有在基礎資料來源中建立物件的權限。</span><span class="sxs-lookup"><span data-stu-id="9643d-126">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="9643d-127">您可以使用或不使用範本來建立維度。</span><span class="sxs-lookup"><span data-stu-id="9643d-127">You can build the dimension with or without a template.</span></span> <span data-ttu-id="9643d-128">若要使用範本來建立維度，請從 **[範本]** 清單中選取範本。</span><span class="sxs-lookup"><span data-stu-id="9643d-128">To build the dimension with a template, select the template from the **Template** list.</span></span>  
  
 <span data-ttu-id="9643d-129">如需詳細資訊，請參閱 [在資料來源中產生非時間資料表來建立維度](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="9643d-129">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md).</span></span>  
  
 <span data-ttu-id="9643d-130">**範本**</span><span class="sxs-lookup"><span data-stu-id="9643d-130">**Template**</span></span>  
 <span data-ttu-id="9643d-131">選取您想要用來建立維度的範本。</span><span class="sxs-lookup"><span data-stu-id="9643d-131">Select the template that you want to use to create the dimension.</span></span> <span data-ttu-id="9643d-132">範本會提供一組以特定商業用途為目標的完整屬性和階層定義。</span><span class="sxs-lookup"><span data-stu-id="9643d-132">Templates provide a complete set of attribute and hierarchy definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9643d-133">只有在您已經選取 [在資料來源中產生非時間資料表]\*\*\*\* 時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="9643d-133">This option is only available when the **Generate a non-time table in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9643d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9643d-134">See Also</span></span>  
 <span data-ttu-id="9643d-135">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="9643d-135">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="9643d-136">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="9643d-136">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="9643d-137">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="9643d-137">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
