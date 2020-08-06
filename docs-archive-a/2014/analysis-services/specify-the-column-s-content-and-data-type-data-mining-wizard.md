---
title: 指定資料行&#39;的內容，並將資料類型 (資料採礦嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifycontentdatatype.f1
ms.assetid: 7061f674-e806-46f2-8c15-e260a3c69a17
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66af7280e444036468b9cc33a131993524d3586d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598546"
---
# <a name="specify-the-column39s-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="03040-102">指定資料行&#39;的內容，並將資料類型 (資料採礦嚮導) </span><span class="sxs-lookup"><span data-stu-id="03040-102">Specify the Column&#39;s Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="03040-103">使用 [指定資料行的內容和資料類型]\*\*\*\* 頁面，即可修改精靈已經設定的資料行和內容類型。</span><span class="sxs-lookup"><span data-stu-id="03040-103">Use the **Specify the Column's Content and Data Type** page to modify the column and content types that have already been set by the wizard.</span></span> <span data-ttu-id="03040-104">精靈會使用來源資料行的資料類型和選取之演算法的功能，來決定每個資料行的預設資料和內容類型。</span><span class="sxs-lookup"><span data-stu-id="03040-104">The wizard uses the data types of the source columns and the capabilities of the selected algorithm to determine the default data and content types for each column.</span></span>  
  
 <span data-ttu-id="03040-105">**如需詳細資訊，請參閱** [資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="03040-105">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="03040-106">選項</span><span class="sxs-lookup"><span data-stu-id="03040-106">Options</span></span>  
 <span data-ttu-id="03040-107">**資料行**</span><span class="sxs-lookup"><span data-stu-id="03040-107">**Columns**</span></span>  
 <span data-ttu-id="03040-108">精靈之 [指定培訓資料]\*\*\*\* 頁面中定義的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="03040-108">A list of the columns that are defined in the **Specify the Training Data** page of the wizard.</span></span>  
  
 <span data-ttu-id="03040-109">**內容類型**</span><span class="sxs-lookup"><span data-stu-id="03040-109">**Content Type**</span></span>  
 <span data-ttu-id="03040-110">指派給每個資料行的內容類型。</span><span class="sxs-lookup"><span data-stu-id="03040-110">The content type that is assigned to each column.</span></span> <span data-ttu-id="03040-111">按一下資料格內部，即可變更內容類型。</span><span class="sxs-lookup"><span data-stu-id="03040-111">Click inside a cell to change the content type.</span></span> <span data-ttu-id="03040-112">如需內容類型的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="03040-112">For more information about content types, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="03040-113">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="03040-113">**Data Type**</span></span>  
 <span data-ttu-id="03040-114">指派給每個資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="03040-114">The data types that are assigned to each column.</span></span> <span data-ttu-id="03040-115">按一下資料格內部，即可變更資料類型。</span><span class="sxs-lookup"><span data-stu-id="03040-115">Click inside a cell to change the data type.</span></span> <span data-ttu-id="03040-116">如需資料類型的詳細資訊，請參閱[資料類型 &#40;資料採礦&#41;](data-mining/data-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="03040-116">For more information about data types, see [Data Types &#40;Data Mining&#41;](data-mining/data-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="03040-117">**偵測**</span><span class="sxs-lookup"><span data-stu-id="03040-117">**Detect**</span></span>  
 <span data-ttu-id="03040-118">按一下即可自動偵測數值資料行的連續和分隔內容類型。</span><span class="sxs-lookup"><span data-stu-id="03040-118">Click to automatically detect the continuous and discrete content types for numeric column.</span></span> <span data-ttu-id="03040-119">此選項不適用於以 OLAP 資料來源為基礎的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="03040-119">This does not apply to mining structures that are based on OLAP data sources.</span></span> <span data-ttu-id="03040-120">針對 OLAP 採礦結構，精靈會自動偵測內容類型並選擇與選取之演算法相容的類型。</span><span class="sxs-lookup"><span data-stu-id="03040-120">For OLAP mining structures, the wizard automatically detects content types and chooses a type that is compatible with the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03040-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03040-121">See Also</span></span>  
 <span data-ttu-id="03040-122">[正在完成 Wizard &#40;資料採礦嚮導&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="03040-122">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="03040-123">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="03040-123">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="03040-124">指定定型資料 &#40;資料採礦嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="03040-124">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
