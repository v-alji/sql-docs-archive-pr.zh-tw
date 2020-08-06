---
title: " (商業智慧 Wizard) 的 [選取轉換類型] |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f83fdf566b52a5fe79bea7a4a676274423d1091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592891"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a><span data-ttu-id="5bc1b-102">選取轉換類型 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="5bc1b-102">Select Conversion Type (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="5bc1b-103">使用 **[選取轉換類型]** 頁面，即可針對以多種貨幣儲存的交易，定義本地貨幣和報表貨幣之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-103">Use the **Select Conversion Type** page to define the relationship between local currencies and reporting currencies for transactions stored in multiple currencies.</span></span> <span data-ttu-id="5bc1b-104">本地貨幣為 **[選取量值]** 頁面中，選取之量值用於儲存交易的貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span> <span data-ttu-id="5bc1b-105">報表貨幣是用於轉換 **[選取量值]** 頁面中所選取交易的貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-105">A reporting currency is the currency in which the transactions selected in the **Select Measures** page are translated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bc1b-106">如果 [商業智慧精靈] 是從 [維度設計師] 啟動，或是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中方案總管的某維度上按一下滑鼠右鍵來啟動，則不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-106">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="5bc1b-107">選項</span><span class="sxs-lookup"><span data-stu-id="5bc1b-107">Options</span></span>  
 <span data-ttu-id="5bc1b-108">**多對多**</span><span class="sxs-lookup"><span data-stu-id="5bc1b-108">**Many-to-many**</span></span>  
 <span data-ttu-id="5bc1b-109">使用本地貨幣儲存交易。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-109">Stores transactions using local currencies.</span></span> <span data-ttu-id="5bc1b-110">貨幣轉換功能會先將這類交易轉換為 **[設定貨幣轉換選項]** 頁面中指定的樞紐貨幣，再轉換為一或多種其他的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-110">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
 <span data-ttu-id="5bc1b-111">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表則以歐元 (EUR)、澳幣 (AUD) 和墨西哥披索 (MXN) 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-111">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5bc1b-112">選取此選項會將這些交易從指定的本地貨幣轉換為樞紐貨幣，然後再次將已轉換的交易從樞紐貨幣轉換為指定的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-112">Selecting this option converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5bc1b-113">如此一來，交易就可以儲存為指定的本地貨幣，並以指定的樞紐貨幣來檢視，或以 **[指定報表貨幣]** 頁面中指定的任何報表貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-113">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
 <span data-ttu-id="5bc1b-114">**多對一**</span><span class="sxs-lookup"><span data-stu-id="5bc1b-114">**Many-to-one**</span></span>  
 <span data-ttu-id="5bc1b-115">使用本地貨幣儲存交易。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-115">Stores transactions using local currencies.</span></span> <span data-ttu-id="5bc1b-116">貨幣轉換功能會將這類交易轉換為 **[設定貨幣轉換選項]** 頁面中指定的樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-116">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page.</span></span> <span data-ttu-id="5bc1b-117">樞紐貨幣是唯一指定的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-117">The pivot currency serves as the only specified reporting currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bc1b-118">如果選取此選項，[指定報表貨幣]\*\*\*\* 頁面就不會出現。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-118">If this option is selected, the **Specify Reporting Currencies** page does not appear.</span></span>  
  
 <span data-ttu-id="5bc1b-119">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表則以歐元 (EUR)、澳幣 (AUD) 和墨西哥披索 (MXN) 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-119">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5bc1b-120">選取此選項會將這些交易從指定的本地貨幣轉換為樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-120">Selecting this option converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="5bc1b-121">如此一來，交易就可以儲存為指定的本地貨幣，並以指定的樞紐貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-121">The result is that transactions can be stored in the specified local currencies and viewed in the specified pivot currency.</span></span>  
  
 <span data-ttu-id="5bc1b-122">**一對多**</span><span class="sxs-lookup"><span data-stu-id="5bc1b-122">**One-to-many**</span></span>  
 <span data-ttu-id="5bc1b-123">使用 [設定貨幣轉換選項]\*\*\*\* 頁面中指定的樞紐貨幣來儲存交易，然後轉換成一或多種其他的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-123">Store transactions using the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bc1b-124">如果選取此選項，[定義本地貨幣參考]\*\*\*\* 頁面就不會出現。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-124">If this option is selected, the **Define Local Currency Reference** page does not appear.</span></span>  
  
 <span data-ttu-id="5bc1b-125">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表將以 USD 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-125">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="5bc1b-126">選取此選項會將這些交易從樞紐貨幣轉換為指定的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-126">Selecting this option converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5bc1b-127">如此一來，交易就可以儲存為指定的樞紐貨幣，並以指定的樞紐貨幣來檢視，或以 **[指定報表貨幣]** 頁面中指定的任何報表貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="5bc1b-127">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc1b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bc1b-128">See Also</span></span>  
 <span data-ttu-id="5bc1b-129">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5bc1b-129">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="5bc1b-130">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5bc1b-130">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5bc1b-131">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="5bc1b-131">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
