---
title: 貨幣轉換 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple currency conversions
- monetary data [SQL Server]
- currency [Analysis Services]
- converting currency
- one-to-many currency conversions
- many-to-many currency conversions [Analysis Services]
- many-to-one currency conversions [Analysis Services]
ms.assetid: e03f491c-7df8-46a0-ade9-f2e55b68db85
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4fee100dea2b3aff99516175bf688337a33592e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599286"
---
# <a name="currency-conversions-analysis-services"></a><span data-ttu-id="fd23f-102">貨幣轉換 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="fd23f-102">Currency Conversions (Analysis Services)</span></span>
  <span data-ttu-id="fd23f-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 僅限多維度</span><span class="sxs-lookup"><span data-stu-id="fd23f-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="fd23f-104">會使用多維度運算式 (MDX) 指令碼提供的一組功能，在支援多重貨幣的 Cube 中提供貨幣轉換支援。</span><span class="sxs-lookup"><span data-stu-id="fd23f-104">uses a combination of features, guided by Multidimensional Expressions (MDX) scripts, to provide currency conversion support in cubes supporting multiple currencies.</span></span>  
  
## <a name="currency-conversion-terminology"></a><span data-ttu-id="fd23f-105">貨幣轉換詞彙</span><span class="sxs-lookup"><span data-stu-id="fd23f-105">Currency Conversion Terminology</span></span>  
 <span data-ttu-id="fd23f-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會使用下列詞彙來描述貨幣轉換功能：</span><span class="sxs-lookup"><span data-stu-id="fd23f-106">The following terminology is used in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to describe currency conversion functionality:</span></span>  
  
 <span data-ttu-id="fd23f-107">樞紐貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-107">Pivot currency</span></span>  
 <span data-ttu-id="fd23f-108">在比率量值群組中輸入匯率來轉換的貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-108">The currency against which exchange rates are entered in the rate measure group.</span></span>  
  
 <span data-ttu-id="fd23f-109">本地貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-109">Local currency</span></span>  
 <span data-ttu-id="fd23f-110">用來存放交易的貨幣，轉換的量值以這些交易為基礎。</span><span class="sxs-lookup"><span data-stu-id="fd23f-110">The currency used to store transactions on which measures to be converted are based.</span></span>  
  
 <span data-ttu-id="fd23f-111">本地貨幣的識別方式包括：</span><span class="sxs-lookup"><span data-stu-id="fd23f-111">The local currency can be identified by either:</span></span>  
  
-   <span data-ttu-id="fd23f-112">與交易一併儲存在事實資料表中的貨幣識別碼，常見於銀行應用程式，其中交易本身即可識別交易貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-112">A currency identifier in the fact table stored with the transaction, as is commonly the case with banking applications where the transaction itself identifies the currency used for that transaction.</span></span>  
  
-   <span data-ttu-id="fd23f-113">與維度資料表中之屬性相關聯的貨幣識別碼，此資料表會與事實資料表中的交易相關聯，常見於財務應用程式，其中會由位置或其他識別碼 (例如分公司) 識別相關聯之交易所使用的貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-113">A currency identifier associated with an attribute in a dimension table that is then associated with a transaction in the fact table, as is commonly the case in financial applications where a location or other identifier, such as a subsidiary, identifies the currency used for an associated transaction.</span></span>  
  
 <span data-ttu-id="fd23f-114">報表貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-114">Reporting currency</span></span>  
 <span data-ttu-id="fd23f-115">交易從樞紐貨幣轉換而成的貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-115">The currency to which transactions are converted from the pivot currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd23f-116">針對多對一貨幣轉換，樞紐貨幣和報表貨幣相同。</span><span class="sxs-lookup"><span data-stu-id="fd23f-116">For many-to-one currency conversions, the pivot currency and reporting currency are the same.</span></span>  
  
 <span data-ttu-id="fd23f-117">貨幣維度</span><span class="sxs-lookup"><span data-stu-id="fd23f-117">Currency dimension</span></span>  
 <span data-ttu-id="fd23f-118">定義下列設定的資料庫維度：</span><span class="sxs-lookup"><span data-stu-id="fd23f-118">A database dimension defined with the following settings:</span></span>  
  
-   <span data-ttu-id="fd23f-119">維度的 `Type` 屬性會設定為 Currency。</span><span class="sxs-lookup"><span data-stu-id="fd23f-119">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="fd23f-120">維度的一個屬性 (Attribute) 的 `Type` 屬性 (Property) 會設定為 CurrencyName。</span><span class="sxs-lookup"><span data-stu-id="fd23f-120">The `Type` property of one attribute for the dimension is set to CurrencyName.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fd23f-121">此屬性的值必須用於所有應該包含貨幣識別碼的資料行。</span><span class="sxs-lookup"><span data-stu-id="fd23f-121">The values of this attribute must be used in all columns that should contain a currency identifier.</span></span>  
  
 <span data-ttu-id="fd23f-122">比率量值群組</span><span class="sxs-lookup"><span data-stu-id="fd23f-122">Rate measure group</span></span>  
 <span data-ttu-id="fd23f-123">Cube 中定義下列設定的量值群組：</span><span class="sxs-lookup"><span data-stu-id="fd23f-123">A measure group in a cube, defined with the following settings:</span></span>  
  
-   <span data-ttu-id="fd23f-124">貨幣維度和比率量值群組之間存在一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-124">A regular dimension relationship exists between a currency dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="fd23f-125">時間維度和比率量值群組之間存在一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-125">A regular dimension relationship exists between a time dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="fd23f-126">`Type` 屬性也可以設定為 ExchangeRate。</span><span class="sxs-lookup"><span data-stu-id="fd23f-126">Optionally, the `Type` property is set to ExchangeRate.</span></span> <span data-ttu-id="fd23f-127">雖然商業智慧精靈使用貨幣和時間維度之間的關聯性來識別可能的比率量值群組，如果將 `Type` 屬性設定為 ExchangeRate，用戶端應用程式就可以更容易地識別比率量值群組。</span><span class="sxs-lookup"><span data-stu-id="fd23f-127">While the Business Intelligence Wizard uses the relationships with the currency and time dimensions to identify likely rate measure groups, setting the `Type` property to ExchangeRate allows client applications to more easily identify rate measure groups.</span></span>  
  
-   <span data-ttu-id="fd23f-128">一或多個量值，代表比率量值群組所包含的匯率。</span><span class="sxs-lookup"><span data-stu-id="fd23f-128">One or more measures, representing the exchange rates contained by the rate measure group.</span></span>  
  
 <span data-ttu-id="fd23f-129">報表貨幣維度</span><span class="sxs-lookup"><span data-stu-id="fd23f-129">Reporting currency dimension</span></span>  
 <span data-ttu-id="fd23f-130">在定義貨幣轉換之後，由商業智慧精靈定義的維度，此維度包含該貨幣轉換的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-130">The dimension, defined by the Business Intelligence Wizard after a currency conversion is defined, that contains the reporting currencies for that currency conversion.</span></span> <span data-ttu-id="fd23f-131">報表貨幣維度以貨幣維度的維度主資料表中的具名查詢為基礎，此具名查詢是在與比率量值群組相關聯之貨幣維度所依據的資料來源檢視中定義。</span><span class="sxs-lookup"><span data-stu-id="fd23f-131">The reporting currency dimension is based on a named query, defined in the data source view on which the currency dimension associated with the rate measure group is based, from the dimension main table of the currency dimension.</span></span> <span data-ttu-id="fd23f-132">定義下列設定的維度：</span><span class="sxs-lookup"><span data-stu-id="fd23f-132">The dimension is defined with the following settings:</span></span>  
  
-   <span data-ttu-id="fd23f-133">維度的 `Type` 屬性會設定為 Currency。</span><span class="sxs-lookup"><span data-stu-id="fd23f-133">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="fd23f-134">維度的索引鍵屬性 (Attribute) 的 `Type` 屬性 (Property) 會設定為 CurrencyName。</span><span class="sxs-lookup"><span data-stu-id="fd23f-134">The `Type` property of the key attribute for the dimension is set to CurrencyName.</span></span>  
  
-   <span data-ttu-id="fd23f-135">維度內一個屬性 (Attribute) 的 `Type` 屬性 (Property) 會設定為 CurrencyDestination，且繫結至此屬性 (Attribute) 的資料行包含貨幣識別碼，代表貨幣轉換的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-135">The `Type` property of one attribute within the dimension is set to CurrencyDestination, and the column bound to the attribute contains the currency identifiers that represent the reporting currencies for the currency conversion.</span></span>  
  
## <a name="defining-currency-conversions"></a><span data-ttu-id="fd23f-136">定義貨幣轉換</span><span class="sxs-lookup"><span data-stu-id="fd23f-136">Defining Currency Conversions</span></span>  
 <span data-ttu-id="fd23f-137">您可以使用商業智慧精靈來定義 Cube 的貨幣轉換功能，或使用 MDX 指令碼來手動定義貨幣轉換。</span><span class="sxs-lookup"><span data-stu-id="fd23f-137">You can use the Business Intelligence Wizard to define currency conversion functionality for a cube, or you can manually define currency conversions using MDX scripts.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="fd23f-138">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fd23f-138">Prerequisites</span></span>  
 <span data-ttu-id="fd23f-139">您必須先定義至少一個貨幣維度、至少一個時間維度以及至少一個比率量值群組，才能使用商業智慧精靈來定義 Cube 中的貨幣轉換。</span><span class="sxs-lookup"><span data-stu-id="fd23f-139">Before you can define a currency conversion in a cube using the Business Intelligence Wizard, you must first define at least one currency dimension, at least one time dimension, and at least one rate measure group.</span></span> <span data-ttu-id="fd23f-140">從這些物件中，商業智慧精靈可以擷取資料和中繼資料，這些資料用來建構報表貨幣維度與提供貨幣轉換功能所需的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fd23f-140">From these objects, the Business Intelligence Wizard can retrieve the data and metadata used to construct the reporting currency dimension and MDX script needed to provide currency conversion functionality.</span></span>  
  
### <a name="decisions"></a><span data-ttu-id="fd23f-141">決策</span><span class="sxs-lookup"><span data-stu-id="fd23f-141">Decisions</span></span>  
 <span data-ttu-id="fd23f-142">您必須先完成下列決策，商業智慧精靈才能建構報表貨幣維度與提供貨幣轉換功能所需的 MDX 指令碼：</span><span class="sxs-lookup"><span data-stu-id="fd23f-142">You need to make the following decisions before the Business Intelligence Wizard can construct the reporting currency dimension and MDX script needed to provide currency conversion functionality:</span></span>  
  
-   <span data-ttu-id="fd23f-143">匯率方向</span><span class="sxs-lookup"><span data-stu-id="fd23f-143">Exchange rate direction</span></span>  
  
-   <span data-ttu-id="fd23f-144">轉換的成員</span><span class="sxs-lookup"><span data-stu-id="fd23f-144">Converted members</span></span>  
  
-   <span data-ttu-id="fd23f-145">轉換類型</span><span class="sxs-lookup"><span data-stu-id="fd23f-145">Conversion type</span></span>  
  
-   <span data-ttu-id="fd23f-146">本地貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-146">Local currencies</span></span>  
  
-   <span data-ttu-id="fd23f-147">報表貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-147">Reporting currencies</span></span>  
  
### <a name="exchange-rate-directions"></a><span data-ttu-id="fd23f-148">匯率方向</span><span class="sxs-lookup"><span data-stu-id="fd23f-148">Exchange Rate Directions</span></span>  
 <span data-ttu-id="fd23f-149">比率量值群組包含量值，代表本地貨幣和樞紐貨幣 (通常稱為公司的貨幣) 之間的匯率。</span><span class="sxs-lookup"><span data-stu-id="fd23f-149">The rate measure group contains measures representing exchange rates between local currencies and the pivot currency (commonly referred to as the corporate currency).</span></span> <span data-ttu-id="fd23f-150">匯率方向和轉換類型的組合，會決定在以商業智慧精靈產生的 MDX 指令碼所轉換之量值上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="fd23f-150">The combination of exchange rate direction and conversion type determines the operation performed on measures to be converted by the MDX script generated using the Business Intelligence Wizard.</span></span> <span data-ttu-id="fd23f-151">下表根據商業智慧精靈中可用的匯率方向選項和轉換方向，描述依據匯率方向和轉換類型而決定執行的作業。</span><span class="sxs-lookup"><span data-stu-id="fd23f-151">The following table describes the operations performed depending on the exchange rate direction and conversion type, based on the exchange rate direction options and conversion directions available in the Business Intelligence Wizard.</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="fd23f-152">匯率方向</span><span class="sxs-lookup"><span data-stu-id="fd23f-152">Exchange rate direction</span></span>|<span data-ttu-id="fd23f-153">**多對一**</span><span class="sxs-lookup"><span data-stu-id="fd23f-153">**Many-to-one**</span></span>|<span data-ttu-id="fd23f-154">**一對多**</span><span class="sxs-lookup"><span data-stu-id="fd23f-154">**One-to-many**</span></span>|<span data-ttu-id="fd23f-155">**多對多**</span><span class="sxs-lookup"><span data-stu-id="fd23f-155">**Many-to-many**</span></span>|  
|<span data-ttu-id="fd23f-156">**n 個樞紐貨幣至 1 個範例貨幣**</span><span class="sxs-lookup"><span data-stu-id="fd23f-156">**n pivot currency to 1 sample currency**</span></span>|<span data-ttu-id="fd23f-157">將待轉換的量值乘以本地貨幣的匯率量值，以轉換量值為樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-157">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="fd23f-158">將待轉換的量值除以報表貨幣的匯率量值，以轉換量值為報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-158">Divide the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="fd23f-159">將待轉換的量值乘以本地貨幣的匯率量值，以轉換量值為樞紐貨幣，再將已轉換的量值除以報表貨幣的匯率量值，以轉換量值為報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-159">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then divide the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
|<span data-ttu-id="fd23f-160">**n 個範例貨幣至 1 個樞紐貨幣**</span><span class="sxs-lookup"><span data-stu-id="fd23f-160">**n sample currency to 1 pivot currency**</span></span>|<span data-ttu-id="fd23f-161">將待轉換的量值除以本地貨幣的匯率量值，以轉換量值為樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-161">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="fd23f-162">將待轉換的量值乘以報表貨幣的匯率量值，以轉換量值為報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-162">Multiply the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="fd23f-163">將待轉換的量值除以本地貨幣的匯率量值，以轉換量值為樞紐貨幣，再將已轉換的量值乘以報表貨幣的匯率量值，以轉換量值為報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-163">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then multiply the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
  
 <span data-ttu-id="fd23f-164">請在商業智慧精靈的 **[設定貨幣轉換選項]** 頁面上選擇匯率方向。</span><span class="sxs-lookup"><span data-stu-id="fd23f-164">You choose the exchange rate direction on the **Set currency conversion options** page of the Business Intelligence Wizard.</span></span> <span data-ttu-id="fd23f-165">如需設定轉換方向的詳細資訊，請參閱[設定貨幣轉換選項 &#40;商業智慧精靈&#41;](set-currency-conversion-options-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="fd23f-165">For more information about setting conversion direction, see [Set Currency Conversion Options &#40;Business Intelligence Wizard&#41;](set-currency-conversion-options-business-intelligence-wizard.md).</span></span>  
  
### <a name="converted-members"></a><span data-ttu-id="fd23f-166">轉換的成員</span><span class="sxs-lookup"><span data-stu-id="fd23f-166">Converted Members</span></span>  
 <span data-ttu-id="fd23f-167">您可以使用商業智慧精靈，從比率量值群組中指定使用哪些量值來轉換下列的值：</span><span class="sxs-lookup"><span data-stu-id="fd23f-167">You can use the Business Intelligence Wizard to specify which measures from the rate measure group are used to convert values for:</span></span>  
  
-   <span data-ttu-id="fd23f-168">其他量值群組中的量值。</span><span class="sxs-lookup"><span data-stu-id="fd23f-168">Measures in other measure groups.</span></span>  
  
-   <span data-ttu-id="fd23f-169">資料庫維度中帳戶屬性之屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="fd23f-169">Members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
-   <span data-ttu-id="fd23f-170">資料庫維度中帳戶屬性的屬性階層之成員所使用的帳戶類型。</span><span class="sxs-lookup"><span data-stu-id="fd23f-170">Account types, used by members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
 <span data-ttu-id="fd23f-171">商業智慧精靈在精靈產生的 MDX 指令碼內會使用這項資訊，來決定貨幣轉換計算的範圍。</span><span class="sxs-lookup"><span data-stu-id="fd23f-171">The Business Intelligence Wizard uses this information within the MDX script generated by the wizard to determine the scope of the currency conversion calculation.</span></span> <span data-ttu-id="fd23f-172">如需指定貨幣轉換之成員的詳細資訊，請參閱[選取成員 &#40;商業智慧精靈&#41;](select-members-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="fd23f-172">For more information about specifying members for currency conversion, see [Select Members &#40;Business Intelligence Wizard&#41;](select-members-business-intelligence-wizard.md).</span></span>  
  
### <a name="conversion-types"></a><span data-ttu-id="fd23f-173">轉換類型</span><span class="sxs-lookup"><span data-stu-id="fd23f-173">Conversion Types</span></span>  
 <span data-ttu-id="fd23f-174">商業智慧精靈支援三種不同類型的貨幣轉換：</span><span class="sxs-lookup"><span data-stu-id="fd23f-174">The Business Intelligence Wizard supports three different types of currency conversion:</span></span>  
  
-   <span data-ttu-id="fd23f-175">**一對多**</span><span class="sxs-lookup"><span data-stu-id="fd23f-175">**One-to-many**</span></span>  
  
     <span data-ttu-id="fd23f-176">交易以樞紐貨幣儲存在事實資料表中，然後轉換為一或多種其他的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-176">Transactions are stored in the fact table in the pivot currency, and then converted to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="fd23f-177">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表將以 USD 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="fd23f-177">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="fd23f-178">此轉換類型會將這些交易從樞紐貨幣轉換為指定的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-178">This conversion type converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="fd23f-179">因此，交易可以儲存為指定的樞紐貨幣，並以指定的樞紐貨幣來檢視，或以貨幣轉換定義的報表貨幣維度中所指定的任何報表貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="fd23f-179">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any of the reporting currencies specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="fd23f-180">**多對一**</span><span class="sxs-lookup"><span data-stu-id="fd23f-180">**Many-to-one**</span></span>  
  
     <span data-ttu-id="fd23f-181">交易會以本地貨幣儲存在事實資料表中，然後轉換為樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-181">Transactions are stored in the fact table in local currencies, and then converted into the pivot currency.</span></span> <span data-ttu-id="fd23f-182">樞紐貨幣會作為報表貨幣維度中所指定的唯一報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-182">The pivot currency serves as the only specified reporting currency in the reporting currency dimension.</span></span>  
  
     <span data-ttu-id="fd23f-183">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表則以歐元 (EUR)、澳幣 (AUD) 和墨西哥披索 (MXN) 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="fd23f-183">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="fd23f-184">此轉換類型會將這些交易從指定的本地貨幣轉換為樞紐貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-184">This conversion type converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="fd23f-185">因此，交易可以儲存為指定的本地貨幣，並以貨幣轉換定義的報表貨幣維度中所指定的報表貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="fd23f-185">The result is that transactions can be stored in the specified local currencies and viewed in the pivot currency, which is specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="fd23f-186">**多對多**</span><span class="sxs-lookup"><span data-stu-id="fd23f-186">**Many-to-many**</span></span>  
  
     <span data-ttu-id="fd23f-187">交易會以本地貨幣儲存在事實資料表中。</span><span class="sxs-lookup"><span data-stu-id="fd23f-187">Transactions are stored in the fact table in local currencies.</span></span> <span data-ttu-id="fd23f-188">此貨幣轉換功能會將這類交易轉換為樞紐貨幣，然後再轉換為一或多種其他的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-188">The currency conversion functionality converts such transactions into the pivot currency, and then to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="fd23f-189">例如，樞紐貨幣可以設定為美元 (USD)，而事實資料表則以歐元 (EUR)、澳幣 (AUD) 和墨西哥披索 (MXN) 儲存交易。</span><span class="sxs-lookup"><span data-stu-id="fd23f-189">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="fd23f-190">此轉換類型會將這些交易從指定的本地貨幣轉換為樞紐貨幣，然後再次將已轉換的交易從樞紐貨幣轉換為指定的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-190">This conversion type converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="fd23f-191">因此，交易可以儲存為指定的本地貨幣，並以指定的樞紐貨幣來檢視，或以貨幣轉換定義的報表貨幣維度中所指定的任何報表貨幣來檢視。</span><span class="sxs-lookup"><span data-stu-id="fd23f-191">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any of the reporting currencies that are specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
 <span data-ttu-id="fd23f-192">指定轉換類型可讓商業智慧精靈定義報表貨幣維度的具名查詢和維度結構，以及貨幣轉換定義之 MDX 指令碼的結構。</span><span class="sxs-lookup"><span data-stu-id="fd23f-192">Specifying the conversion type allows the Business Intelligence Wizard to define the named query and dimension structure of the reporting currency dimension, as well as the structure of the MDX script defined for the currency conversion.</span></span>  
  
### <a name="local-currencies"></a><span data-ttu-id="fd23f-193">本地貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-193">Local Currencies</span></span>  
 <span data-ttu-id="fd23f-194">如果您選擇以多對多或多對一轉換類型執行貨幣轉換，您需要指定如何識別本地貨幣，供商業智慧精靈產生的 MDX 指令碼執行貨幣轉換計算。</span><span class="sxs-lookup"><span data-stu-id="fd23f-194">If you choose a many-to-many or many-to-one conversion type for your currency conversion, you need to specify how to identify the local currencies from which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="fd23f-195">事實資料表中交易的本地貨幣有下列兩種識別方式：</span><span class="sxs-lookup"><span data-stu-id="fd23f-195">The local currency for a transaction in a fact table can be identified in one of two ways:</span></span>  
  
-   <span data-ttu-id="fd23f-196">量值群組和貨幣維度之間存在一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-196">The measure group contains a regular dimension relationship to the currency dimension.</span></span> <span data-ttu-id="fd23f-197">例如，在 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 範例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中，網際網路銷售量值群組和貨幣維度之間存在一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-197">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="fd23f-198">該量值群組的事實資料表包含外部索引鍵資料行，此資料行參考該維度之維度資料表中的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd23f-198">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span> <span data-ttu-id="fd23f-199">在上述情形中，您可以從量值群組所參考的貨幣維度中選取屬性，來識別該量值群組在事實資料表中交易的本地貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-199">In this case, you can select the attribute from the currency dimension that is referenced by the measure group to identify the local currency for transactions in the fact table for that measure group.</span></span> <span data-ttu-id="fd23f-200">此情形常見於銀行應用程式，其中交易本身即會決定交易使用的貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-200">This situation most often occurs in banking applications, where the transaction itself determines the currency used within the transaction.</span></span>  
  
-   <span data-ttu-id="fd23f-201">量值群組和貨幣維度之間，透過直接參考貨幣維度的另一個維度，存在參考維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-201">The measure group contains a referenced dimension relationship to the currency dimension, through another dimension that directly references the currency dimension.</span></span> <span data-ttu-id="fd23f-202">例如，在 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 範例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中，財務報表量值群組是透過組織維度，而對貨幣維度有參考式維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-202">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="fd23f-203">該量值群組的事實資料表包含外部索引鍵資料行，此資料行參考組織維度之維度資料表中的成員。</span><span class="sxs-lookup"><span data-stu-id="fd23f-203">The fact table for that measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="fd23f-204">而組織維度的維度資料表包含外部索引鍵資料行，此資料行參考貨幣維度之維度資料表中的貨幣識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd23f-204">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span> <span data-ttu-id="fd23f-205">此情形常見於財務報表應用程式，其中交易的位置或分公司會決定交易的貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-205">This situation most often occurs in financial reporting applications, where the location or subsidiary for a transaction determines the currency for the transaction.</span></span> <span data-ttu-id="fd23f-206">在上述情形中，您可以從商務實體的維度中選取參考貨幣維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="fd23f-206">In this case, you can select the attribute that references the currency dimension from the dimension for the business entity.</span></span>  
  
### <a name="reporting-currencies"></a><span data-ttu-id="fd23f-207">報表貨幣</span><span class="sxs-lookup"><span data-stu-id="fd23f-207">Reporting Currencies</span></span>  
 <span data-ttu-id="fd23f-208">如果您選擇以多對多或一對多轉換類型執行貨幣轉換，您需要指定報表貨幣，供商業智慧精靈產生的 MDX 指令碼執行貨幣轉換計算。</span><span class="sxs-lookup"><span data-stu-id="fd23f-208">If you choose a many-to-many or one-to-many conversion type for your currency conversion, you need to specify the reporting currencies for which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="fd23f-209">您可以指定比率量值群組相關之貨幣維度的所有成員，或從維度中選取個別的成員。</span><span class="sxs-lookup"><span data-stu-id="fd23f-209">You can either specify all the members of the currency dimension related to the rate measure group, or select individual members from the dimension.</span></span>  
  
 <span data-ttu-id="fd23f-210">商業智慧精靈會根據使用選取之報表貨幣的貨幣維度，從該貨幣維度的維度資料表所建構的具名查詢來建立報表貨幣維度。</span><span class="sxs-lookup"><span data-stu-id="fd23f-210">The Business Intelligence Wizard creates a reporting currency dimension, based on a named query constructed from the dimension table for the currency dimension using the selected reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd23f-211">如果您選取一對多轉換類型，則也會建立報表貨幣維度。</span><span class="sxs-lookup"><span data-stu-id="fd23f-211">If you select the one-to-many conversion type, a reporting currency dimension is also created.</span></span> <span data-ttu-id="fd23f-212">此維度只包含一個成員代表樞紐貨幣，因為樞紐貨幣也作為一對多貨幣轉換的報表貨幣。</span><span class="sxs-lookup"><span data-stu-id="fd23f-212">The dimension contains only one member representing the pivot currency, because the pivot currency is also used as the reporting currency for a one-to-many currency conversion.</span></span>  
  
 <span data-ttu-id="fd23f-213">Cube 中定義的每一個貨幣轉換，均會定義個別的報表貨幣維度。</span><span class="sxs-lookup"><span data-stu-id="fd23f-213">A separate reporting currency dimension is defined for each currency conversion defined in a cube.</span></span> <span data-ttu-id="fd23f-214">報表貨幣維度在建立之後可以變更名稱，但如果名稱變更，您也必須更新該貨幣轉換產生的 MDX 指令碼，以確保在參考報表貨幣維度時，指令碼命令可以使用正確的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd23f-214">You can change the name of the reporting currency dimensions after creation, but if you do so you must also update the MDX script generated for that currency conversion to ensure that the correct name is used by the script command when referencing the reporting currency dimension.</span></span>  
  
## <a name="defining-multiple-currency-conversions"></a><span data-ttu-id="fd23f-215">定義多重貨幣轉換</span><span class="sxs-lookup"><span data-stu-id="fd23f-215">Defining Multiple Currency Conversions</span></span>  
 <span data-ttu-id="fd23f-216">利用商業智慧精靈，您可以依照商業智慧方案的需求，定義所需數量的貨幣轉換。</span><span class="sxs-lookup"><span data-stu-id="fd23f-216">Using the Business Intelligence Wizard, you can define as many currency conversions as needed for your business intelligence solution.</span></span> <span data-ttu-id="fd23f-217">您可以覆寫現有的貨幣轉換，或將新的貨幣轉換附加至 Cube 的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fd23f-217">You can either overwrite an existing currency conversion or append a new currency conversion to the MDX script for a cube.</span></span> <span data-ttu-id="fd23f-218">單一 Cube 中定義的多重貨幣轉換，讓報表需求複雜的商業智慧應用程式更有彈性，例如財務報表應用程式，即支援多個不同的國際報表的轉換需求。</span><span class="sxs-lookup"><span data-stu-id="fd23f-218">Multiple currency conversions defined in a single cube provide flexibility in business intelligence applications that have complex reporting requirements, such as financial reporting applications that support multiple, separate conversion requirements for international reporting.</span></span>  
  
### <a name="identifying-currency-conversions"></a><span data-ttu-id="fd23f-219">識別貨幣轉換</span><span class="sxs-lookup"><span data-stu-id="fd23f-219">Identifying Currency Conversions</span></span>  
 <span data-ttu-id="fd23f-220">商業智慧精靈會將貨幣轉換的指令碼命令包覆在下列註解中，來識別每一種貨幣轉換：</span><span class="sxs-lookup"><span data-stu-id="fd23f-220">The Business Intelligence Wizard identifies each currency conversion by framing the script commands for the currency conversion in the following comments:</span></span>  
  
 `//<Currency conversion>`  
  
 `...`  
  
 `[MDX statements for the currency conversion]`  
  
 `...`  
  
 `//</Currency conversion>`  
  
 <span data-ttu-id="fd23f-221">如果您變更或移除這些註解，商業智慧精靈將無法偵測貨幣轉換，所以您不應變更這些註解。</span><span class="sxs-lookup"><span data-stu-id="fd23f-221">If you change or remove these comments, the Business Intelligence Wizard is unable to detect the currency conversion, so you should not change these comments.</span></span>  
  
 <span data-ttu-id="fd23f-222">精靈也會將註解的中繼資料儲存在這些註解內，包括建立日期和時間、使用者以及轉換類型。</span><span class="sxs-lookup"><span data-stu-id="fd23f-222">The wizard also stores metadata in comments within these comments, including the creation date and time, the user, and the conversion type.</span></span> <span data-ttu-id="fd23f-223">也不應變更這些註解，因為商業智慧精靈在顯示現有的貨幣轉換時會使用此中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fd23f-223">These comments should also not be changed because the Business Intelligence Wizard uses this metadata when displaying existing currency conversions.</span></span>  
  
 <span data-ttu-id="fd23f-224">您可以視需要變更貨幣轉換中所包含的指令碼命令。</span><span class="sxs-lookup"><span data-stu-id="fd23f-224">You can change the script commands contained in a currency conversion as needed.</span></span> <span data-ttu-id="fd23f-225">不過，如果覆寫貨幣轉換，將會遺失您的變更。</span><span class="sxs-lookup"><span data-stu-id="fd23f-225">If you overwrite the currency conversion, however, your changes will be lost.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23f-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd23f-226">See Also</span></span>  
 [<span data-ttu-id="fd23f-227">Analysis Services 多維度的全球化案例</span><span class="sxs-lookup"><span data-stu-id="fd23f-227">Globalization scenarios for Analysis Services Multiidimensional</span></span>](globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
  
