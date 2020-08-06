---
title: 建立貨幣類型維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91123fb5fda898e90056057114295335fbd1d32c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698683"
---
# <a name="create-a-currency-type-dimension"></a><span data-ttu-id="a6102-102">建立貨幣類型維度</span><span class="sxs-lookup"><span data-stu-id="a6102-102">Create a Currency type Dimension</span></span>
  <span data-ttu-id="a6102-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，貨幣類型維度是其屬性代表財務報表用途之貨幣清單的維度。</span><span class="sxs-lookup"><span data-stu-id="a6102-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a currency type dimension is a dimension whose attributes represent a list of currencies for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="a6102-104">貨幣維度可讓您將貨幣轉換功能加入至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="a6102-104">A currency dimension lets you add currency conversion capabilities to a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a6102-105">若要將貨幣轉換加入至 Cube，您可以使用商業智慧精靈定義多維度運算式 (MDX) 指令碼命令，將貨幣量值轉換成適合用戶端應用程式地區設定的值。</span><span class="sxs-lookup"><span data-stu-id="a6102-105">To add currency conversion to a cube, you use the Business Intelligence Wizard define a Multidimensional Expressions (MDX) script command that converts currency measures to values that are appropriate for the locale of the client application.</span></span> <span data-ttu-id="a6102-106">若要建立這個 MDX 指令碼，商業智慧精靈需要下列資訊：</span><span class="sxs-lookup"><span data-stu-id="a6102-106">To create this MDX script, the Business Intelligence Wizard needs the following information:</span></span>  
  
-   <span data-ttu-id="a6102-107">代表來源貨幣的貨幣維度。</span><span class="sxs-lookup"><span data-stu-id="a6102-107">A currency dimension that represents source currencies.</span></span> <span data-ttu-id="a6102-108">(此維度是來源貨幣維度)。</span><span class="sxs-lookup"><span data-stu-id="a6102-108">(This dimension is the source currency dimension.)</span></span>  
  
-   <span data-ttu-id="a6102-109">代表要使用之匯率的量值群組。</span><span class="sxs-lookup"><span data-stu-id="a6102-109">A measure group that represents the exchange rates that will be used.</span></span>  
  
 <span data-ttu-id="a6102-110">商業智慧精靈可利用此資訊設計一個貨幣轉換程序，來識別適當的目的地貨幣維度 (代表目的地貨幣的貨幣維度)。</span><span class="sxs-lookup"><span data-stu-id="a6102-110">From this information, the Business Intelligence Wizard will design a currency conversion process that identifies the appropriate destination currency dimension (the currency dimension that represents destination currencies).</span></span> <span data-ttu-id="a6102-111">視商業智慧方案需要的貨幣轉換數目而定，商業智慧精靈可定義多個目的地貨幣維度。</span><span class="sxs-lookup"><span data-stu-id="a6102-111">Depending on the number of currency conversions that your business intelligence solution requires, the Business Intelligence Wizard can define multiple destination currency dimensions.</span></span> <span data-ttu-id="a6102-112">如需定義貨幣轉換的詳細資訊，請參閱[貨幣轉換 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a6102-112">For more information about defining currency conversions, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="a6102-113">若要將維度識別為貨幣維度，請將維度的 `Type` 屬性設定為 `Currency`。</span><span class="sxs-lookup"><span data-stu-id="a6102-113">To identify a dimension as a currency dimension, set the `Type` property of the dimension to `Currency`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="a6102-114">維度結構</span><span class="sxs-lookup"><span data-stu-id="a6102-114">Dimension Structure</span></span>  
 <span data-ttu-id="a6102-115">貨幣維度會包含至少一個索引鍵屬性，來識別貨幣維度之維度資料表中的個別貨幣。</span><span class="sxs-lookup"><span data-stu-id="a6102-115">A currency dimension contains, at least, a key attribute identifying individual currencies in the dimension table for the currency dimension.</span></span> <span data-ttu-id="a6102-116">在來源和目的地貨幣維度中，索引鍵屬性的值是不同的：</span><span class="sxs-lookup"><span data-stu-id="a6102-116">The value of the key attribute is different in both source and destination currency dimensions:</span></span>  
  
-   <span data-ttu-id="a6102-117">若要將屬性識別為來源貨幣維度的索引鍵屬性，請將該屬性的 `Type` 屬性設定為 `CurrencySource`。</span><span class="sxs-lookup"><span data-stu-id="a6102-117">To identify an attribute as the key attribute of a source currency dimension, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="a6102-118">若要將屬性識別為目的地貨幣維度，請將屬性的 `Type` 屬性設定為 `CurrencyDestination`。</span><span class="sxs-lookup"><span data-stu-id="a6102-118">To identify an attribute as the destination currency dimension, set the `Type` property of the attribute to `CurrencyDestination`.</span></span>  
  
 <span data-ttu-id="a6102-119">基於報表用途，來源和目的地貨幣維度都可選擇性地包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a6102-119">For reporting purposes, both source and destination currency dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="a6102-120">貨幣名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="a6102-120">A currency name attribute.</span></span>  
  
     <span data-ttu-id="a6102-121">若要將屬性識別為貨幣名稱屬性，請將屬性的 `Type` 屬性設定為 `CurrencyName`。</span><span class="sxs-lookup"><span data-stu-id="a6102-121">To identify an attribute as a currency name attribute, set the `Type` property of the attribute to `CurrencyName`.</span></span>  
  
-   <span data-ttu-id="a6102-122">貨幣來源屬性。</span><span class="sxs-lookup"><span data-stu-id="a6102-122">A currency source attribute.</span></span>  
  
     <span data-ttu-id="a6102-123">若要將屬性識別為貨幣來源屬性，請將屬性的 `Type` 屬性設定為 `CurrencySource`。</span><span class="sxs-lookup"><span data-stu-id="a6102-123">To identify an attribute as a currency source attribute, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="a6102-124">貨幣國際標準組織 (ISO) 代碼。</span><span class="sxs-lookup"><span data-stu-id="a6102-124">A currency International Standards Organization (ISO) code.</span></span>  
  
     <span data-ttu-id="a6102-125">若要將屬性識別為貨幣 ISO 代碼屬性，請將屬性的 `Type` 屬性設定為 `CurrencyIsoCode`。</span><span class="sxs-lookup"><span data-stu-id="a6102-125">To identify an attribute as a currency ISO code attribute, set the `Type` property of the attribute to `CurrencyIsoCode`.</span></span>  
  
 <span data-ttu-id="a6102-126">如需屬性類型的詳細資訊，請參閱 [設定屬性類型](attribute-properties-configure-attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a6102-126">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="a6102-127">使用商業智慧精靈定義帳戶智慧</span><span class="sxs-lookup"><span data-stu-id="a6102-127">Defining Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="a6102-128">在定義帳戶維度並將該維度加入至 Cube 之後，您就可以使用商業智慧精靈來加入帳戶智慧功能，例如識別及對應帳戶類型至維度。</span><span class="sxs-lookup"><span data-stu-id="a6102-128">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="a6102-129">如需詳細資訊，請參閱 [將帳戶智慧加入至維度中](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="a6102-129">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6102-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6102-130">See Also</span></span>  
 <span data-ttu-id="a6102-131">[屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="a6102-131">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="a6102-132">[商業智慧 Wizard F1 說明](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a6102-132">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="a6102-133">維度類型</span><span class="sxs-lookup"><span data-stu-id="a6102-133">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
