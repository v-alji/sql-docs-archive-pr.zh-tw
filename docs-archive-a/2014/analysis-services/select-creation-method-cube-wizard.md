---
title: 選取建立方法 (Cube Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: c8c4d611e00a2b3f5d115ea5749b1e494a44bf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599194"
---
# <a name="select-creation-method-cube-wizard"></a><span data-ttu-id="6f25f-102">選取建立方法 (Cube 精靈)</span><span class="sxs-lookup"><span data-stu-id="6f25f-102">Select Creation Method (Cube Wizard)</span></span>
  <span data-ttu-id="6f25f-103">使用 **[選取建立方法]** 頁面，即可指定建立 Cube 的方式。</span><span class="sxs-lookup"><span data-stu-id="6f25f-103">Use the **Select Creation Method** page to specify how to create the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6f25f-104">選項</span><span class="sxs-lookup"><span data-stu-id="6f25f-104">Options</span></span>  
 <span data-ttu-id="6f25f-105">**使用現有的資料表**</span><span class="sxs-lookup"><span data-stu-id="6f25f-105">**Use existing tables**</span></span>  
 <span data-ttu-id="6f25f-106">選取此選項，即可使用資料來源中的現有資料表來建立 Cube。</span><span class="sxs-lookup"><span data-stu-id="6f25f-106">Select to create a cube by using existing tables in a data source.</span></span> <span data-ttu-id="6f25f-107">這個精靈將引導您完成根據現有資料表選取並定義量值群組和維度，以便建立新 Cube 的程序。</span><span class="sxs-lookup"><span data-stu-id="6f25f-107">The wizard will guide you through the process of selecting and defining measure groups and dimensions based on existing tables to build your new cube.</span></span>  
  
 <span data-ttu-id="6f25f-108">**建立空白 Cube**</span><span class="sxs-lookup"><span data-stu-id="6f25f-108">**Create an empty cube**</span></span>  
 <span data-ttu-id="6f25f-109">選取此選項，即可建立空白的 Cube。</span><span class="sxs-lookup"><span data-stu-id="6f25f-109">Select to create an empty cube.</span></span> <span data-ttu-id="6f25f-110">當您想要手動建立所有項目，或者 Cube 中的所有量值群組都是連結的量值群組時，這個選項就很有用。</span><span class="sxs-lookup"><span data-stu-id="6f25f-110">This option is useful when you want to create everything manually, or when all measure groups in the cube are linked measure groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f25f-111">只有當您使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案時，才能使用這個選項，但是當您直接連接至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫時，則無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="6f25f-111">This option is only available when you are working with an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and not when you are connected directly to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="6f25f-112">**在資料來源中建立資料表**</span><span class="sxs-lookup"><span data-stu-id="6f25f-112">**Generate tables in the data source**</span></span>  
 <span data-ttu-id="6f25f-113">選取此選項，即可先建立 Cube，然後根據 Cube 定義，在資料來源中產生新的資料表。</span><span class="sxs-lookup"><span data-stu-id="6f25f-113">Select to create a cube first and then generate new tables in the data source based on the cube definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f25f-114">若要使用這個選項，您必須擁有在基礎資料來源中建立物件的權限。</span><span class="sxs-lookup"><span data-stu-id="6f25f-114">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="6f25f-115">選取此選項將使 **[範本]** 選項成為可用。</span><span class="sxs-lookup"><span data-stu-id="6f25f-115">Selecting this option will make the **Template** option available.</span></span>  
  
 <span data-ttu-id="6f25f-116">**範本**</span><span class="sxs-lookup"><span data-stu-id="6f25f-116">**Template**</span></span>  
 <span data-ttu-id="6f25f-117">選取您想要用來建立 Cube 的範本。</span><span class="sxs-lookup"><span data-stu-id="6f25f-117">Select the template that you want to use to create the cube.</span></span> <span data-ttu-id="6f25f-118">範本會提供一組以特定商業用途為目標的定義。</span><span class="sxs-lookup"><span data-stu-id="6f25f-118">Templates provide a set of definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f25f-119">只有在您已經選取 [在資料來源中建立資料表]\*\*\*\* 時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="6f25f-119">This option is only available when the **Generate tables in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f25f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f25f-120">See Also</span></span>  
 <span data-ttu-id="6f25f-121">[Cube 物件 &#40;Analysis Services 多維度資料&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6f25f-121">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="6f25f-122">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="6f25f-122">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="6f25f-123">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="6f25f-123">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
