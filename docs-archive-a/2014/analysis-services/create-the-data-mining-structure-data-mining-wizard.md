---
title: 建立資料採礦結構 (資料採礦嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectminingtechnique.f1
ms.assetid: d1ff17b2-fff3-4ed7-a5d6-42d131e59f93
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9f738cff974bc0064fc9e93c86221f0b10c6e80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594865"
---
# <a name="create-the-data-mining-structure-data-mining-wizard"></a><span data-ttu-id="d7edf-102">建立資料採礦結構 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="d7edf-102">Create the Data Mining Structure (Data Mining Wizard)</span></span>
  <span data-ttu-id="d7edf-103">使用 [建立資料採礦結構]\*\*\*\* 頁面建立資料採礦結構，並選擇性地建立與該結構建立關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d7edf-103">Use the **Create the Data Mining Structure** page to create a data mining structure and optionally create an associated mining model.</span></span>  
  
 <span data-ttu-id="d7edf-104">如果選擇建立採礦模型，則也必須指定您要使用的資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="d7edf-104">If you choose to create a mining model, you must also specify the data mining algorithm that you want to use.</span></span> <span data-ttu-id="d7edf-105">如果現在只建立結構，則可稍後在結構中加入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="d7edf-105">If you create only the structure now, you can add a mining model to the structure later.</span></span>  
  
 <span data-ttu-id="d7edf-106">**如需詳細資訊，請參閱** [資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)、[資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="d7edf-106">**For More Information:** [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7edf-107">選項</span><span class="sxs-lookup"><span data-stu-id="d7edf-107">Options</span></span>  
 <span data-ttu-id="d7edf-108">**建立具有採礦模型的採礦結構**</span><span class="sxs-lookup"><span data-stu-id="d7edf-108">**Create mining structure with a mining model**</span></span>  
 <span data-ttu-id="d7edf-109">選取建立採礦結構，然後建立相關聯的模型。</span><span class="sxs-lookup"><span data-stu-id="d7edf-109">Select to create a mining structure and then create an associated model.</span></span>  
  
 <span data-ttu-id="d7edf-110">**您要使用哪一種資料採礦技術？**</span><span class="sxs-lookup"><span data-stu-id="d7edf-110">**Which data mining technique do you want to use?**</span></span>  
 <span data-ttu-id="d7edf-111">選取此模型要使用的資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="d7edf-111">Select the data mining algorithm to use with this model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7edf-112">演算法的清單是從您在其上建立採礦結構的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體，來加以擴展。</span><span class="sxs-lookup"><span data-stu-id="d7edf-112">The list of algorithms is populated from the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] on which you are creating the mining structure.</span></span> <span data-ttu-id="d7edf-113">如果無法使用伺服器，就只能使用預設演算法。</span><span class="sxs-lookup"><span data-stu-id="d7edf-113">If the server is not available, only the default algorithms will be available.</span></span>  
  
 <span data-ttu-id="d7edf-114">**建立沒有模型的採礦結構**</span><span class="sxs-lookup"><span data-stu-id="d7edf-114">**Create mining structure with no models**</span></span>  
 <span data-ttu-id="d7edf-115">選取只建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="d7edf-115">Select to create only a mining structure.</span></span>  
  
 <span data-ttu-id="d7edf-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="d7edf-116">**Description**</span></span>  
 <span data-ttu-id="d7edf-117">顯示所選取演算法的描述。</span><span class="sxs-lookup"><span data-stu-id="d7edf-117">Displays a description of the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7edf-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7edf-118">See Also</span></span>  
 <span data-ttu-id="d7edf-119">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d7edf-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d7edf-120">[選取資料來源視圖 &#40;資料採礦嚮導&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="d7edf-120">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="d7edf-121">選取定義方法 &#40;資料採礦嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="d7edf-121">Select the Definition Method &#40;Data Mining Wizard&#41;</span></span>](select-the-definition-method-data-mining-wizard.md)  
  
  
