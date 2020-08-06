---
title: 建立父子式類型維度的財務帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba10e642425628426d9183be2b8d2c4ff751c3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698689"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a><span data-ttu-id="244a8-102">建立父子式類型維度的財務帳戶</span><span class="sxs-lookup"><span data-stu-id="244a8-102">Create a Finance Account of parent-child type Dimension</span></span>
  <span data-ttu-id="244a8-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，帳戶類型維度是其屬性代表財務報表用途之帳戶圖表的維度。</span><span class="sxs-lookup"><span data-stu-id="244a8-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an account type dimension is a dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="244a8-104">帳戶維度可讓您選擇性地管理帳戶經過一段時間之後的彙總行為。</span><span class="sxs-lookup"><span data-stu-id="244a8-104">An account dimension lets you selectively manage aggregation behavior across accounts over time.</span></span> <span data-ttu-id="244a8-105">帳戶維度也可讓您使用標準機制，來解決通常發生在處理財務資料之商業智慧方案中的大部份非標準彙總問題。</span><span class="sxs-lookup"><span data-stu-id="244a8-105">An account dimension also lets use a standard mechanism to resolve most of the nonstandard aggregation issues typically encountered in business intelligence solutions that handle financial data.</span></span> <span data-ttu-id="244a8-106">如果您沒有這樣的標準機制，要解決這些非標準彙總問題，您需要自訂積存公式、導出成員或多維度運算式 (MDX) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="244a8-106">If you did not have such a standard mechanism, resolving these nonstandard aggregation issues would require custom rollup formulas, calculated members, or Multidimensional Expressions (MDX) scripts.</span></span>  
  
 <span data-ttu-id="244a8-107">若要將維度識別為帳戶維度，請將維度的 `Type` 屬性設定為 `Accounts`。</span><span class="sxs-lookup"><span data-stu-id="244a8-107">To identify a dimension as an account dimension, set the `Type` property of the dimension to `Accounts`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="244a8-108">維度結構</span><span class="sxs-lookup"><span data-stu-id="244a8-108">Dimension Structure</span></span>  
 <span data-ttu-id="244a8-109">帳戶維度至少包含兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="244a8-109">An account dimension contains, at least, two attributes:</span></span>  
  
-   <span data-ttu-id="244a8-110">索引鍵屬性-識別帳戶維度之維度資料表中個別帳戶的屬性。</span><span class="sxs-lookup"><span data-stu-id="244a8-110">A key attribute-an attribute that identifies individual accounts in the dimension table for the account dimension.</span></span>  
  
-   <span data-ttu-id="244a8-111">帳戶屬性-描述帳戶如何以階層方式排列在帳戶維度中的父屬性。</span><span class="sxs-lookup"><span data-stu-id="244a8-111">An account attribute-a parent attribute that describes how accounts are hierarchically arranged in the account dimension.</span></span>  
  
     <span data-ttu-id="244a8-112">若要將屬性 (Attribute) 識別為帳戶屬性，請將屬性 (Attribute) 的 `Type` 屬性 (Property) 設定為 `Account` 和 `Usage` 屬性 (Property) 設定為 `Parent`。</span><span class="sxs-lookup"><span data-stu-id="244a8-112">To identify an attribute as an account attribute, set the `Type` property of the attribute to `Account` and the `Usage` property to `Parent`.</span></span>  
  
 <span data-ttu-id="244a8-113">帳戶維度可選擇性地包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="244a8-113">Account dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="244a8-114">帳戶類型屬性-定義維度中每個帳戶之帳戶類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="244a8-114">An account type attribute-an attribute that defines the account type for each account in the dimension.</span></span> <span data-ttu-id="244a8-115">帳戶類型屬性的成員名稱會對應到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫或專案之已定義的帳戶類型，並指出 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 針對那些帳戶使用的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="244a8-115">The member names of the account type attribute map to the account types defined for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and indicate the aggregation function used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for those accounts.</span></span> <span data-ttu-id="244a8-116">您也可以使用一元運算子或自訂積存公式來決定帳戶屬性的彙總行為，但帳戶類型可讓您輕易地將一致的行為套用至帳戶的圖表中，而不需要變更基礎關聯式資料庫。</span><span class="sxs-lookup"><span data-stu-id="244a8-116">You can also use unary operators or custom rollup formulas to determine aggregation behavior for account attributes, but account types let you to easily apply consistent behavior to a chart of accounts without requiring changes to the underlying relational database.</span></span>  
  
     <span data-ttu-id="244a8-117">若要識別帳戶類型屬性 (Attribute)，請將屬性 (Attribute) 的 `Type` 屬性 (Property) 設定為 `AccountType`。</span><span class="sxs-lookup"><span data-stu-id="244a8-117">To identify an account type attribute, set the `Type` property of the attribute to `AccountType`.</span></span>  
  
-   <span data-ttu-id="244a8-118">帳戶名稱屬性-用於報告用途的屬性。</span><span class="sxs-lookup"><span data-stu-id="244a8-118">An account name attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="244a8-119">若要識別帳戶名稱屬性 (Attribute)，請將屬性 (Attribute) 的 `Type` 屬性 (Property) 設定為 `AccountName`。</span><span class="sxs-lookup"><span data-stu-id="244a8-119">You identify an account name attribute by setting the `Type` property of the attribute to `AccountName`.</span></span>  
  
-   <span data-ttu-id="244a8-120">帳戶號碼屬性-用於報告用途的屬性。</span><span class="sxs-lookup"><span data-stu-id="244a8-120">An account number attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="244a8-121">若要識別帳戶號碼屬性 (Attribute)，請將屬性 (Attribute) 的 `Type` 屬性 (Property) 設定為 `AccountNumber`。</span><span class="sxs-lookup"><span data-stu-id="244a8-121">You identify an account number attribute by setting the `Type` property of the attribute to `AccountNumber`.</span></span>  
  
 <span data-ttu-id="244a8-122">如需屬性類型的詳細資訊，請參閱 [設定屬性類型](attribute-properties-configure-attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="244a8-122">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="244a8-123">使用商業智慧精靈加入帳戶智慧</span><span class="sxs-lookup"><span data-stu-id="244a8-123">Adding Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="244a8-124">在定義帳戶維度並將該維度加入至 Cube 之後，您可以使用商業智慧精靈來將帳戶智慧功能 (例如識別和對應帳戶類型) 加入至維度。</span><span class="sxs-lookup"><span data-stu-id="244a8-124">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to adding account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="244a8-125">如需詳細資訊，請參閱 [將帳戶智慧加入至維度中](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="244a8-125">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244a8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="244a8-126">See Also</span></span>  
 <span data-ttu-id="244a8-127">[屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="244a8-127">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="244a8-128">[商業智慧 Wizard F1 說明](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="244a8-128">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="244a8-129">維度類型</span><span class="sxs-lookup"><span data-stu-id="244a8-129">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
