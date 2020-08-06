---
title: 在維度中設定屬性的自訂成員公式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
ms.openlocfilehash: 112f8944bd20b2b6a464b0d84fb8ac1a0e89d976
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593663"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a><span data-ttu-id="0db6b-102">在維度中設定屬性的自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="0db6b-102">Set Custom Member Formulas for Attributes in a Dimension</span></span>
  <span data-ttu-id="0db6b-103">將自訂成員公式增強功能加入至 Cube 或維度以取代預設彙總，預設彙總與使用多維度運算式 (MDX) 運算式之結果的維度成員相關聯。</span><span class="sxs-lookup"><span data-stu-id="0db6b-103">Add a custom member formula enhancement to a cube or dimension to replace the default aggregation that is associated with a dimension member with the results of a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="0db6b-104">(在維度中，此增強功能會於指定的屬性上設定 `CustomRollupColumn` 屬性)。</span><span class="sxs-lookup"><span data-stu-id="0db6b-104">(This enhancement sets the `CustomRollupColumn` property on a specified attribute in a dimension.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0db6b-105">只有以現有資料來源為基礎的維度，才可以使用自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="0db6b-105">A custom member formula is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="0db6b-106">針對不使用資料來源而建立的維度，您必須執行結構描述產生精靈來建立資料來源檢視後，才能加入自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="0db6b-106">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding a custom member formula.</span></span>  
  
 <span data-ttu-id="0db6b-107">若要加入自訂成員公式，您可使用 [商業智慧精靈]，並於 [選擇增強功能]\*\*\*\* 頁面上選取 [建立自訂成員公式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="0db6b-107">To add a custom member formula, you use the Business Intelligence Wizard, and select the **Create a custom member formula** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="0db6b-108">然後，此精靈會引導您逐步完成選取要套用自訂成員公式的維度，並啟用自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="0db6b-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom member formula and enabling the custom member formula.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="0db6b-109">選取維度</span><span class="sxs-lookup"><span data-stu-id="0db6b-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="0db6b-110">在精靈的第一個 [建立自訂成員公式]\*\*\*\* 頁面上，您指定要套用自訂成員公式的維度。</span><span class="sxs-lookup"><span data-stu-id="0db6b-110">On the first **Create a Custom Member Formula** page of the wizard, you specify the dimension to which you want to apply a custom member formula.</span></span> <span data-ttu-id="0db6b-111">加入到此選取維度的自訂成員公式增強功能，會造成維度的變更。</span><span class="sxs-lookup"><span data-stu-id="0db6b-111">The custom member formula enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="0db6b-112">包含選取之維度的所有 Cube，都會繼承這些變更。</span><span class="sxs-lookup"><span data-stu-id="0db6b-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="enabling-a-custom-member-formula"></a><span data-ttu-id="0db6b-113">啟用自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="0db6b-113">Enabling a Custom Member Formula</span></span>  
 <span data-ttu-id="0db6b-114">在第二個 [建立自訂成員公式]\*\*\*\* 頁面上，您將包含自訂成員公式的來源資料行與維度中的一個或多個屬性相關聯。</span><span class="sxs-lookup"><span data-stu-id="0db6b-114">On the second **Create a Custom Member Formula** page, you associate the source column that contains the custom member formula with one or more attributes in the dimension.</span></span> <span data-ttu-id="0db6b-115">在 [屬性]\*\*\*\* 資料行中，選取您要與自訂成員公式資料行相關聯之屬性旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0db6b-115">In the **Attribute** column, select the check box next to the attribute that you want to associate with the custom member formula column.</span></span> <span data-ttu-id="0db6b-116">選取每個屬性之後，精靈會顯示 [選取資料行]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0db6b-116">After you select each attribute, the wizard displays the **Select a Column** dialog box.</span></span> <span data-ttu-id="0db6b-117">在此對話方塊中，按一下包含公式之維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="0db6b-117">In this dialog box, click the column in the dimension table that contains the formula.</span></span> <span data-ttu-id="0db6b-118">如果您要在關閉 [選取資料行]\*\*\*\* 對話方塊後變更選取項目，請按一下您要變更的 [來源資料行]\*\*\*\* 資料格，然後按一下省略符號 ([...]\*\*\*\*) 再次開啟 [選取資料行]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0db6b-118">If you want to change a selection after you close the **Select a Column** dialog box, click the **Source Column** cell that you want to change, and then click the ellipsis (**...**) to open the **Select a Column** dialog box again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db6b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db6b-119">See Also</span></span>  
 [<span data-ttu-id="0db6b-120">使用商業智慧精靈增強維度</span><span class="sxs-lookup"><span data-stu-id="0db6b-120">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  
