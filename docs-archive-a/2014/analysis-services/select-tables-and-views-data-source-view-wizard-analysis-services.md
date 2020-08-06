---
title: " (資料來源 View Wizard)  (Analysis Services) 中選取資料表和 Views |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac7159255ef526d871ed8906fc873d9f16d2eb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706833"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a><span data-ttu-id="df4b1-102">選取資料表和檢視 (資料來源檢視精靈) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="df4b1-102">Select Tables and Views (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="df4b1-103">使用 [選取資料表和檢視]\*\*\*\* 頁面，從您想要包含在資料來源檢視裡的資料來源中，選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="df4b1-103">Use the **Select Tables and Views** page to select the tables or views from the data source that you want to include in the data source view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df4b1-104">選項</span><span class="sxs-lookup"><span data-stu-id="df4b1-104">Options</span></span>  
 <span data-ttu-id="df4b1-105">**可用的物件**</span><span class="sxs-lookup"><span data-stu-id="df4b1-105">**Available objects**</span></span>  
 <span data-ttu-id="df4b1-106">列出資料來源結構描述中的資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="df4b1-106">Lists the tables and views in the data source schema.</span></span> <span data-ttu-id="df4b1-107">如果列出了一項以上的結構描述，每個物件的名稱都會以結構描述名稱為前置詞。</span><span class="sxs-lookup"><span data-stu-id="df4b1-107">The schema name prefixes the name of every object if more than one schema is listed.</span></span> <span data-ttu-id="df4b1-108">如果只列出一項結構描述，物件名稱就不會有結構描述的名稱作為前置詞。</span><span class="sxs-lookup"><span data-stu-id="df4b1-108">If only one schema is listed, the schema's name does not prefix the object names.</span></span>  
  
 <span data-ttu-id="df4b1-109">若要以遞增或遞減的順序重新排列清單，請按一下 [名稱]\*\*\*\* 或 [類型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="df4b1-109">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="df4b1-110">**包含的物件**</span><span class="sxs-lookup"><span data-stu-id="df4b1-110">**Included objects**</span></span>  
 <span data-ttu-id="df4b1-111">列出要包含在資料來源檢視中的資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="df4b1-111">Lists the tables and views to include in the data source view.</span></span>  
  
 <span data-ttu-id="df4b1-112">若要以遞增或遞減的順序重新排列清單，請按一下 [名稱]\*\*\*\* 或 [類型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="df4b1-112">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="df4b1-113">**Filter**</span><span class="sxs-lookup"><span data-stu-id="df4b1-113">**Filter**</span></span>  
 <span data-ttu-id="df4b1-114">篩選 [可用的物件]\*\*\*\* 之下所列的物件。</span><span class="sxs-lookup"><span data-stu-id="df4b1-114">Filters the objects listed under **Available objects**.</span></span> <span data-ttu-id="df4b1-115">鍵入字串，然後按一下 [篩選]\*\*\*\* 即可只列出包含指定字串的名稱。</span><span class="sxs-lookup"><span data-stu-id="df4b1-115">Type a string, and then click **Filter** to list only the names that contain a specified string.</span></span> <span data-ttu-id="df4b1-116">若要尋找完全相同的字元字串，請將字串置於雙引號之間。</span><span class="sxs-lookup"><span data-stu-id="df4b1-116">To find an exact string of characters, enclose the string between double quotation marks.</span></span> <span data-ttu-id="df4b1-117">篩選不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="df4b1-117">The filter is not case sensitive.</span></span>  
  
 <span data-ttu-id="df4b1-118">您可以將下表所列的萬用字元，包含在篩選字串中的任何地方。</span><span class="sxs-lookup"><span data-stu-id="df4b1-118">You can include the wildcard characters listed in the following table anywhere in the filter string.</span></span>  
  
|<span data-ttu-id="df4b1-119">萬用字元</span><span class="sxs-lookup"><span data-stu-id="df4b1-119">Wildcard character</span></span>|<span data-ttu-id="df4b1-120">值</span><span class="sxs-lookup"><span data-stu-id="df4b1-120">Value</span></span>|  
|------------------------|-----------|  
|**\***|<span data-ttu-id="df4b1-121">任何字元字串。</span><span class="sxs-lookup"><span data-stu-id="df4b1-121">Any string of characters</span></span>|  
|**%**|<span data-ttu-id="df4b1-122">任何字元字串。</span><span class="sxs-lookup"><span data-stu-id="df4b1-122">Any string of characters</span></span>|  
|<span data-ttu-id="df4b1-123">**?**</span><span class="sxs-lookup"><span data-stu-id="df4b1-123">**?**</span></span>|<span data-ttu-id="df4b1-124">單一字元。</span><span class="sxs-lookup"><span data-stu-id="df4b1-124">A single character</span></span>|  
|<span data-ttu-id="df4b1-125">**"** *string* **"**</span><span class="sxs-lookup"><span data-stu-id="df4b1-125">**"** *string* **"**</span></span>|<span data-ttu-id="df4b1-126">字元組成的常值字串</span><span class="sxs-lookup"><span data-stu-id="df4b1-126">A literal string of characters.</span></span> <span data-ttu-id="df4b1-127">此萬用字元會符合物件名稱裡的任何子字串。</span><span class="sxs-lookup"><span data-stu-id="df4b1-127">This wildcard character will match any substring within the object name.</span></span>|  
  
 <span data-ttu-id="df4b1-128">**顯示系統物件**</span><span class="sxs-lookup"><span data-stu-id="df4b1-128">**Show system objects**</span></span>  
 <span data-ttu-id="df4b1-129">顯示 [可用的物件]\*\*\*\* 之下的系統物件。</span><span class="sxs-lookup"><span data-stu-id="df4b1-129">Displays system objects under **Available objects**.</span></span> <span data-ttu-id="df4b1-130">唯有在資料來源提供者公開了系統物件之後，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="df4b1-130">This option is available only if the data source provider exposes system objects.</span></span> <span data-ttu-id="df4b1-131">從 [包含的物件]\*\*\*\* 清單中移除系統物件，就會自動選取此選項。</span><span class="sxs-lookup"><span data-stu-id="df4b1-131">Removing a system object from the **Included objects** list automatically selects this option.</span></span>  
  
 <span data-ttu-id="df4b1-132">**加入相關資料表**</span><span class="sxs-lookup"><span data-stu-id="df4b1-132">**Add related tables**</span></span>  
 <span data-ttu-id="df4b1-133">加入與 [包含的物件]\*\*\*\* 之下所列物件相關的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="df4b1-133">Adds all the tables that are related to those listed under **Included objects**.</span></span> <span data-ttu-id="df4b1-134">此選項不會加入檢視。</span><span class="sxs-lookup"><span data-stu-id="df4b1-134">This option does not add views.</span></span> <span data-ttu-id="df4b1-135">但是，此選項會加入已分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="df4b1-135">However, this option does add partitioned tables.</span></span> <span data-ttu-id="df4b1-136">如果在精靈的 [名稱比對]\*\*\*\* 頁面上選取了名稱比對準則，此選項還會依據您選取的準則，來包含邏輯上相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="df4b1-136">If you select name-matching criteria on the **Name Matching** page of the wizard, this option also includes logically related tables according to the criteria you select.</span></span> <span data-ttu-id="df4b1-137">如果資料表與新加入的相關資料表相關聯，且如果其具有與原來資料表相同的結構，則也會包含這些資料表。</span><span class="sxs-lookup"><span data-stu-id="df4b1-137">Tables are also included if they are related to the newly added related tables, and if they have an identical structure to the original table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4b1-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df4b1-138">See Also</span></span>  
 <span data-ttu-id="df4b1-139">[資料來源 View Wizard F1 說明 &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="df4b1-139">[Data Source View Wizard F1 Help &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span></span>  
 [<span data-ttu-id="df4b1-140">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="df4b1-140">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
