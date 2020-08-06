---
title: ) 商業智慧 Wizard (定義當地貨幣參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: bcd5c01839ecc7ae120089f17a1b909f18464e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703413"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a><span data-ttu-id="8cb4f-102">定義本地貨幣參考 (商業智慧精靈)</span><span class="sxs-lookup"><span data-stu-id="8cb4f-102">Define Local Currency Reference (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="8cb4f-103">使用 [定義本地貨幣參考]\*\*\*\* 頁面，即可定義貨幣轉換功能的本地貨幣，這會涵蓋 [選取轉換類型]\*\*\*\* 頁面上指定的多對多或多對一轉換類型。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-103">Use the **Define Local Currency Reference** page to define the local currencies for currency conversion functionality that covers the many-to-many or many-to-one conversion types specified on the **Select Conversion Type** page.</span></span> <span data-ttu-id="8cb4f-104">本地貨幣為 **[選取量值]** 頁面中，選取之量值用於儲存交易的貨幣。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cb4f-105">如果 [商業智慧精靈] 是從 [維度設計師] 啟動，或是在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中方案總管的某維度上按一下滑鼠右鍵來啟動，則不會出現此頁面。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-105">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8cb4f-106">如果選取 [選取轉換類型]\*\*\*\* 頁面上的 [一對多]\*\*\*\*，這個頁面也不會出現。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-106">This page also does not appear if **One-to-Many** was selected on the **Select Conversion Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8cb4f-107">選項</span><span class="sxs-lookup"><span data-stu-id="8cb4f-107">Options</span></span>  
 <span data-ttu-id="8cb4f-108">**事實資料表中的識別碼**</span><span class="sxs-lookup"><span data-stu-id="8cb4f-108">**Identifiers in the fact table**</span></span>  
 <span data-ttu-id="8cb4f-109">選取即可指定屬性，在包含 [選取量值]\*\*\*\* 頁面上所選取量值的事實資料表所參考的貨幣維度中，提供本地貨幣的貨幣識別碼</span><span class="sxs-lookup"><span data-stu-id="8cb4f-109">Select to specify an attribute that provides currency identifiers for local currencies in a currency dimension referenced by the fact table that contains the measures selected on the **Select Measures** page.</span></span> <span data-ttu-id="8cb4f-110"> (一個 `Type` 屬性設為*currency*的貨幣維度。 ) </span><span class="sxs-lookup"><span data-stu-id="8cb4f-110">(A currency dimension in one whose `Type` property is set to *Currency*.)</span></span>  
  
 <span data-ttu-id="8cb4f-111">當交易自行決定該交易的本地貨幣時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-111">Use this option when the transaction itself determines the local currency for that transaction.</span></span> <span data-ttu-id="8cb4f-112">例如，在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 範例資料庫中， [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] [網際網路銷售] 量值群組與 [貨幣] 維度具有一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-112">For example, in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="8cb4f-113">該量值群組的事實資料表包含外部索引鍵資料行，此資料行參考該維度之維度資料表中的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-113">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span>  
  
 <span data-ttu-id="8cb4f-114">**事實資料所參考的貨幣維度與屬性**</span><span class="sxs-lookup"><span data-stu-id="8cb4f-114">**Currency dimension and attribute referenced by the fact data**</span></span>  
 <span data-ttu-id="8cb4f-115">在貨幣維度中選取貨幣屬性，其成員代表本地貨幣的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-115">Select the currency attribute within a currency dimension whose members represent currency identifiers for local currencies.</span></span> <span data-ttu-id="8cb4f-116"> (貨幣屬性，其 `Type` 屬性設定為*currency*。 ) </span><span class="sxs-lookup"><span data-stu-id="8cb4f-116">(A currency attribute is one whose `Type` property is set to *Currency*.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cb4f-117"> 若未選取 **[事實資料表中的識別碼]** 選項，則無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-117">This option is not available if the **Identifiers in the fact table** option is not selected.</span></span>  
  
 <span data-ttu-id="8cb4f-118">**維度資料表中的屬性**</span><span class="sxs-lookup"><span data-stu-id="8cb4f-118">**Attributes in the dimension table**</span></span>  
 <span data-ttu-id="8cb4f-119">選取即可從與量值群組相關的維度中指定屬性，該量值群組包含本地貨幣的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-119">Select to specify an attribute from a dimension related to the measure group that contains currency identifiers for local currencies.</span></span>  
  
 <span data-ttu-id="8cb4f-120">當交易與其他商務實體 (例如位置) 間的關聯性，會決定該交易的本地貨幣時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-120">Use this option when the relationship between a transaction and another business entity, such as a location, determines the local currency for that transaction.</span></span> <span data-ttu-id="8cb4f-121">例如，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 範例資料庫中， [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 財務報表量值群組會透過組織維度，與貨幣維度有參考的維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-121">For example, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="8cb4f-122">也就是說，財務報表量值群組的事實資料表中包含的外部索引鍵資料行，參考到組織維度之維度資料表中的成員。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-122">That is, the fact table for the Financial Reporting measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="8cb4f-123">而組織維度的維度資料表包含外部索引鍵資料行，此資料行參考貨幣維度之維度資料表中的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-123">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span>  
  
 <span data-ttu-id="8cb4f-124">**參考貨幣的維度屬性**</span><span class="sxs-lookup"><span data-stu-id="8cb4f-124">**Dimension attribute that references currency**</span></span>  
 <span data-ttu-id="8cb4f-125">在維度中選取屬性，其成員參考本地貨幣的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-125">Select the attribute within a dimension whose members reference the currency identifiers for local currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cb4f-126"> 若未選取 **[維度資料表中的屬性]** 選項，則無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8cb4f-126">This option is not available if the **Attributes in the dimension table** option is not selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb4f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cb4f-127">See Also</span></span>  
 <span data-ttu-id="8cb4f-128">[商業智慧 Wizard F1 說明](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8cb4f-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="8cb4f-129">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8cb4f-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8cb4f-130">維度設計師 &#40;Analysis Services 多維資料&#41;</span><span class="sxs-lookup"><span data-stu-id="8cb4f-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
