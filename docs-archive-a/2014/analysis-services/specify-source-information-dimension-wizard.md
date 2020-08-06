---
title: " (維度 Wizard) 中指定來源資訊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 99bbaac0bdf24a18dcde455e779f056b98106dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598550"
---
# <a name="specify-source-information-dimension-wizard"></a><span data-ttu-id="b0949-102">指定來源資訊 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="b0949-102">Specify Source Information (Dimension Wizard)</span></span>
  <span data-ttu-id="b0949-103">使用 **[選取主維度資料表]** 頁面，即可針對要建立的維度，選取資料來源檢視、主維度資料表、索引鍵資料行和成員名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="b0949-103">Use the **Select the Main Dimension Table** page to select the data source view, main dimension table, key columns, and member name column for the dimension to be created.</span></span>  
  
 <span data-ttu-id="b0949-104">**開啟維度精靈**</span><span class="sxs-lookup"><span data-stu-id="b0949-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="b0949-105">在方案總管\*\*\*\* 的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案的 [維度]\*\*\*\* 資料夾，然後按一下 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0949-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b0949-106">選項</span><span class="sxs-lookup"><span data-stu-id="b0949-106">Options</span></span>  
 <span data-ttu-id="b0949-107">**資料來源視圖**</span><span class="sxs-lookup"><span data-stu-id="b0949-107">**Data source view**</span></span>  
 <span data-ttu-id="b0949-108">選取資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="b0949-108">Select a data source view.</span></span>  
  
 <span data-ttu-id="b0949-109">**主資料表**</span><span class="sxs-lookup"><span data-stu-id="b0949-109">**Main table**</span></span>  
 <span data-ttu-id="b0949-110">從選取的資料來源檢視中選取資料表，用來作為維度的主資料表。</span><span class="sxs-lookup"><span data-stu-id="b0949-110">Select a table from the selected data source view to use as the main table for the dimension.</span></span>  
  
 <span data-ttu-id="b0949-111">**索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="b0949-111">**Key columns**</span></span>  
 <span data-ttu-id="b0949-112">從 [主資料表]\*\*\*\* 指定的資料表中選取索引鍵資料行，作為維度的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="b0949-112">Select the key columns from the table specified in **Main table** for the key attribute of the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0949-113">可以選取一個以上的資料行。</span><span class="sxs-lookup"><span data-stu-id="b0949-113">More than one column can be selected.</span></span> <span data-ttu-id="b0949-114">如果資料表包含複合主索引鍵，請選取複合主索引鍵包含的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="b0949-114">If the table contains a composite primary key, select all the columns included in the composite primary key.</span></span> <span data-ttu-id="b0949-115">索引鍵資料行的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="b0949-115">The order of the key columns is important.</span></span>  
  
 <span data-ttu-id="b0949-116">**名稱資料行**</span><span class="sxs-lookup"><span data-stu-id="b0949-116">**Name column**</span></span>  
 <span data-ttu-id="b0949-117">從 [主資料表]\*\*\*\* 指定的資料表中選取資料行，此資料行提供維度的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="b0949-117">Select the column from the table specified in **Main table** that provides the member names for the dimension.</span></span> <span data-ttu-id="b0949-118">使用複合索引鍵時，必須指定名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="b0949-118">A name column must be specified when a composite key is used.</span></span> <span data-ttu-id="b0949-119">若要針對複合索引鍵建立名稱資料行，我們建議您在串連指定之索引鍵資料行的資料來源檢視中建立具名計算。</span><span class="sxs-lookup"><span data-stu-id="b0949-119">To create a name column for a composite key, we recommend that you create a named calculation in the data source view that concatenates the specified key columns.</span></span> <span data-ttu-id="b0949-120">使用單一索引鍵時，名稱資料行是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b0949-120">When a single key is used, the name column is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0949-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0949-121">See Also</span></span>  
 <span data-ttu-id="b0949-122">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b0949-122">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="b0949-123">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b0949-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b0949-124">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="b0949-124">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
