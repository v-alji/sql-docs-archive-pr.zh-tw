---
title: 正在完成 Wizard (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.finish.f1
ms.assetid: 1137740d-3063-4ab1-9cfe-8319194db937
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61f6bf16ea38ab88995ff06ba31a06feb976d900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593669"
---
# <a name="completing-the-wizard-dimension-wizard"></a><span data-ttu-id="3e556-102">正在完成精靈 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="3e556-102">Completing the Wizard (Dimension Wizard)</span></span>
  <span data-ttu-id="3e556-103">使用 **[正在完成精靈]** 頁面，即可進行下列程序：</span><span class="sxs-lookup"><span data-stu-id="3e556-103">Use the **Completing the Wizard** page to do the following procedures:</span></span>  
  
-   <span data-ttu-id="3e556-104">為維度命名。</span><span class="sxs-lookup"><span data-stu-id="3e556-104">Name the dimension.</span></span>  
  
-   <span data-ttu-id="3e556-105">檢閱按一下 **[完成]** 時所做的變更。</span><span class="sxs-lookup"><span data-stu-id="3e556-105">Review the changes that will be made when **Finish** is clicked.</span></span>  
  
-   <span data-ttu-id="3e556-106">必要時，產生支援維度所需的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3e556-106">If necessary, generate the schema needed to support the dimension.</span></span>  
  
 <span data-ttu-id="3e556-107">**開啟維度精靈**</span><span class="sxs-lookup"><span data-stu-id="3e556-107">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="3e556-108">在方案總管\*\*\*\* 的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案的 [維度]\*\*\*\* 資料夾，然後按一下 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3e556-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3e556-109">選項。</span><span class="sxs-lookup"><span data-stu-id="3e556-109">Options</span></span>  
 <span data-ttu-id="3e556-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="3e556-110">**Name**</span></span>  
 <span data-ttu-id="3e556-111">鍵入新維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e556-111">Type the name of the new dimension.</span></span>  
  
 <span data-ttu-id="3e556-112">**預覽**</span><span class="sxs-lookup"><span data-stu-id="3e556-112">**Preview**</span></span>  
 <span data-ttu-id="3e556-113">顯示要為新維度建立的維度屬性和階層。</span><span class="sxs-lookup"><span data-stu-id="3e556-113">Displays the dimension attributes and hierarchies to be created for the new dimension.</span></span>  
  
 <span data-ttu-id="3e556-114">**立即產生結構描述**</span><span class="sxs-lookup"><span data-stu-id="3e556-114">**Generate schema now**</span></span>  
 <span data-ttu-id="3e556-115">選取即可產生支援維度所需的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3e556-115">Select to generate the schema needed to support the dimension.</span></span> <span data-ttu-id="3e556-116">選取此選項會開啟結構描述產生精靈。</span><span class="sxs-lookup"><span data-stu-id="3e556-116">Selecting this option opens the Schema Generation Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e556-117">只有在 [選取建立方法]\*\*\*\* 頁面上選取了 [在資料來源中產生時間資料表]\*\*\*\* 或 [在資料來源中產生非時間資料表]\*\*\*\* 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="3e556-117">This option appears only if you selected **Generate a time table in the data source** or **Generate a non-time table in the data source** on the **Select Creation Method** page.</span></span> <span data-ttu-id="3e556-118">如需詳細資訊，請參閱 [Select Creation Method &#40;Dimension Wizard&#41;](select-creation-method-dimension-wizard.md) (選取建立方法 (維度精靈))。</span><span class="sxs-lookup"><span data-stu-id="3e556-118">For more information, see [Select Creation Method &#40;Dimension Wizard&#41;](select-creation-method-dimension-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e556-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e556-119">See Also</span></span>  
 <span data-ttu-id="3e556-120">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3e556-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="3e556-121">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3e556-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3e556-122">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="3e556-122">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
