---
title: 選取維度屬性 (維度 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4961092517ce1d38cfd4086ec083a939242652d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593643"
---
# <a name="select-dimension-attributes-dimension-wizard"></a><span data-ttu-id="ad9fe-102">選取維度屬性 (維度精靈)</span><span class="sxs-lookup"><span data-stu-id="ad9fe-102">Select Dimension Attributes (Dimension Wizard)</span></span>
  <span data-ttu-id="ad9fe-103">使用 **[選取維度屬性]** 頁面，即可選取和修改要建立之維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-103">Use the **Select Dimension Attributes** page to select and modify the attributes for the dimension to be created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad9fe-104">如果您無法讀取任何資料行的值，請將精靈視窗最大化，然後變更每個資料行標題的寬度，直到可以讀取這些值為止。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-104">If you cannot read the values for any column, maximize the wizard window and change the width of each column heading until you can read the values.</span></span>  
  
 <span data-ttu-id="ad9fe-105">**開啟維度精靈**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-105">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="ad9fe-106">在方案總管\*\*\*\* 的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案的 [維度]\*\*\*\* 資料夾，然後按一下 [新增維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ad9fe-107">選項</span><span class="sxs-lookup"><span data-stu-id="ad9fe-107">Options</span></span>  
 <span data-ttu-id="ad9fe-108">(具有核取方塊的資料行)</span><span class="sxs-lookup"><span data-stu-id="ad9fe-108">(Column with check boxes)</span></span>  
 <span data-ttu-id="ad9fe-109">選取即可將屬性包含在維度中。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-109">Select to include an attribute in the dimension.</span></span>  
  
 <span data-ttu-id="ad9fe-110">若要包含特定屬性，請選取該屬性的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-110">To include a specific attribute, select the check box for that attribute.</span></span>  
  
 <span data-ttu-id="ad9fe-111">若要包含所有屬性，請選取資料行標頭中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-111">To include all attributes, select the check box in the column header.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad9fe-112">您無法清除索引鍵屬性的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-112">The check box for the key attribute cannot be cleared.</span></span>  
  
 <span data-ttu-id="ad9fe-113">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-113">**Attribute Name**</span></span>  
 <span data-ttu-id="ad9fe-114">列出可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-114">Lists the available attributes.</span></span>  
  
 <span data-ttu-id="ad9fe-115">若要變更屬性的名稱，請按一下屬性名稱，然後輸入屬性的新名稱。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-115">To change the name of an attribute, click the attribute name and type a new name for the attribute.</span></span>  
  
 <span data-ttu-id="ad9fe-116">**啟用瀏覽**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-116">**Enable Browsing**</span></span>  
 <span data-ttu-id="ad9fe-117">選取即可讓屬性供使用者用來瀏覽和篩選。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-117">Select to make the attribute available to the end user for browsing and filtering.</span></span> <span data-ttu-id="ad9fe-118">您必須針對索引鍵屬性選取 **[啟用瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-118">**Enable Browsing** must be selected for the key attribute.</span></span> <span data-ttu-id="ad9fe-119">若為非索引鍵屬性 (Attribute)，預設值是不選取 [啟用瀏覽]\*\*\*\*，因而導致非索引鍵屬性 (Attribute) 只能顯示為成員屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-119">For non-key attributes, the default is not to have **Enable Browsing** selected, which causes the non-key attributes to be shown only as member properties.</span></span>  
  
 <span data-ttu-id="ad9fe-120">在大部分情況下，您可以透過分別將 `AttributeHierarchyEnabled` 屬性 (Property) 設定為 `True` 或 `False`，讓屬性 (Attribute) 可以或無法用於瀏覽。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-120">In most cases, the attribute is made available or not available for browsing by setting the `AttributeHierarchyEnabled` property to `True` or `False`, respectively.</span></span> <span data-ttu-id="ad9fe-121">不過，在下列三個情況中，精靈會使用不同的設定。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-121">However, in the following three cases, the wizard uses different settings.</span></span>  
  
|<span data-ttu-id="ad9fe-122">案例</span><span class="sxs-lookup"><span data-stu-id="ad9fe-122">Case</span></span>|<span data-ttu-id="ad9fe-123">設定</span><span class="sxs-lookup"><span data-stu-id="ad9fe-123">Settings</span></span>|  
|----------|--------------|  
|<span data-ttu-id="ad9fe-124">維度包含父子式階層而且沒有選取 [啟用瀏覽]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ad9fe-124">A dimension contains a parent-child hierarchy and **Enable Browsing** is not selected</span></span>|<span data-ttu-id="ad9fe-125">精靈會維持 `AttributeHierarchyEnabled` 屬性 (Property) 設定為 `True`，並將索引鍵屬性 (Attribute) 的 `AttributeHierarchyVisible` 屬性 (Attribute) 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-125">The wizard leaves the `AttributeHierarchyEnabled` property set to `True`, and sets the `AttributeHierarchyVisible` attribute to `False` for the key attribute.</span></span>|  
|<span data-ttu-id="ad9fe-126">維度中的資料表包含指向不在維度中之資料表的外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="ad9fe-126">A table in a dimension contains a foreign key to a table that is not in the dimension</span></span>|<span data-ttu-id="ad9fe-127">雖然精靈會選取外部索引鍵當做要包含的屬性，但是不會選取 **[啟用瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-127">The wizard selects the foreign key as an attribute to be included, but will not select **Enable Browsing**.</span></span> <span data-ttu-id="ad9fe-128">如果您保留這些設定，屬性 (Attribute) 的 `AttributeHiearchyEnabled` 屬性 (Property) 將設定為 `True`，而且 `AttributeHierarchyVisible` 屬性 (Property) 將設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-128">If you keep these settings, the `AttributeHiearchyEnabled` property of the attribute will be set to `True`, and the `AttributeHierarchyVisible` property will be set to `False`.</span></span>|  
|<span data-ttu-id="ad9fe-129">維度包含透過可為 Null 之外部索引鍵資料行存取的雪花資料表</span><span class="sxs-lookup"><span data-stu-id="ad9fe-129">A dimension contains snowflake tables that are reached through nullable foreign key columns</span></span><br /><br /> <span data-ttu-id="ad9fe-130">-和-</span><span class="sxs-lookup"><span data-stu-id="ad9fe-130">-and-</span></span><br /><br /> <span data-ttu-id="ad9fe-131">沒有針對以雪花資料表之索引鍵為基礎的屬性選取 [啟用瀏覽]</span><span class="sxs-lookup"><span data-stu-id="ad9fe-131">Enable Browsing for the attribute that is based on the key of the snowflake table is not selected</span></span>|<span data-ttu-id="ad9fe-132">精靈將會建立新的屬性 (Attribute)，其中 `AttributeHiearchyEnabled` 屬性 (Property) 設定為 `True`，而且 `AttributeHierarchyVisible` 屬性 (Property) 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-132">The wizard will create the new attribute that has the `AttributeHiearchyEnabled` property set to `True`, and the `AttributeHierarchyVisible` property set to `False`.</span></span>|  
  
 <span data-ttu-id="ad9fe-133">**屬性類型**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-133">**Attribute Type**</span></span>  
 <span data-ttu-id="ad9fe-134">(選擇性) 設定屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-134">(Optional) Set the type for the attribute.</span></span> <span data-ttu-id="ad9fe-135">預設值是 **[一般]**。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-135">The default value is **Regular**.</span></span> <span data-ttu-id="ad9fe-136">屬性類型會將屬性可能包含之資訊的相關指引提供給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-136">The attribute type provides guidance to client applications on what information the attribute might contain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9fe-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad9fe-137">See Also</span></span>  
 <span data-ttu-id="ad9fe-138">[維度嚮導 F1 說明](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ad9fe-138">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="ad9fe-139">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ad9fe-139">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="ad9fe-140">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="ad9fe-140">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
