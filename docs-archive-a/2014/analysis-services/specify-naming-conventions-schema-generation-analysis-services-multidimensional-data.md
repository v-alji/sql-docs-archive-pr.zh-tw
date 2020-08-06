---
title: 指定命名慣例 (架構產生嚮導)  (Analysis Services 多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.namingconventions.f1
ms.assetid: 02d830ea-5b1f-4485-9f94-d64b8bea592b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e9588b49331934041cad888142d29d189fc1a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598558"
---
# <a name="specify-naming-conventions-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="f2a26-102">指定命名慣例 (結構描述產生精靈) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f2a26-102">Specify Naming Conventions (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f2a26-103">使用 **[指定命名慣例]** 頁面，即可定義結構描述產生精靈建立結構描述物件時使用的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="f2a26-103">Use the **Specify Naming Conventions** page to define the naming conventions that the Schema Generation Wizard uses when creating schema objects.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2a26-104">選項</span><span class="sxs-lookup"><span data-stu-id="f2a26-104">Options</span></span>  
 <span data-ttu-id="f2a26-105">**選項**</span><span class="sxs-lookup"><span data-stu-id="f2a26-105">**Option**</span></span>  
 <span data-ttu-id="f2a26-106">指定命名慣例供精靈使用。</span><span class="sxs-lookup"><span data-stu-id="f2a26-106">Specify the naming conventions for the wizard to use.</span></span> <span data-ttu-id="f2a26-107">下表描述您可以指定的選項。</span><span class="sxs-lookup"><span data-stu-id="f2a26-107">The following table describes the options you can specify.</span></span>  
  
|<span data-ttu-id="f2a26-108">選項</span><span class="sxs-lookup"><span data-stu-id="f2a26-108">Option</span></span>|<span data-ttu-id="f2a26-109">描述</span><span class="sxs-lookup"><span data-stu-id="f2a26-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f2a26-110">**Separator**</span><span class="sxs-lookup"><span data-stu-id="f2a26-110">**Separator**</span></span>|<span data-ttu-id="f2a26-111">指定字元，用來分隔物件名稱中的單字。</span><span class="sxs-lookup"><span data-stu-id="f2a26-111">Specifies the character that separates words in an object name.</span></span> <span data-ttu-id="f2a26-112">在 **[值]** 資料行中，選取 **[底線]**、 **[空格]** 或 **[無]**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-112">In the **Value** column, select **Underscore**, **Space**, or **None**.</span></span> <span data-ttu-id="f2a26-113">預設值是 **[底線]**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-113">The default is **Underscore**.</span></span>|  
|<span data-ttu-id="f2a26-114">**主索引鍵資料行前置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-114">**Primary key column prefix**</span></span>|<span data-ttu-id="f2a26-115">指定字串，作為每一個主索引鍵資料行的名稱前置詞。</span><span class="sxs-lookup"><span data-stu-id="f2a26-115">Specifies the string to prefix the name of each primary key column.</span></span> <span data-ttu-id="f2a26-116">預設值是 **PK**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-116">The default is **PK**.</span></span>|  
|<span data-ttu-id="f2a26-117">**外部索引鍵資料行前置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-117">**Foreign key column prefix**</span></span>|<span data-ttu-id="f2a26-118">指定字串，作為每一個外部索引鍵資料行的名稱前置詞。</span><span class="sxs-lookup"><span data-stu-id="f2a26-118">Specifies the string to prefix the name of each foreign key column.</span></span> <span data-ttu-id="f2a26-119">預設值是 **FK**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-119">The default is **FK**.</span></span>|  
|<span data-ttu-id="f2a26-120">**屬性名稱後置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-120">**Attribute name suffix**</span></span>|<span data-ttu-id="f2a26-121">指定字串，用於附加至每一個屬性資料行的名稱後面。</span><span class="sxs-lookup"><span data-stu-id="f2a26-121">Specifies the string to be appended to the name of each attribute column.</span></span> <span data-ttu-id="f2a26-122">預設值是 **Name**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-122">The default is **Name**.</span></span>|  
|<span data-ttu-id="f2a26-123">**自訂積存後置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-123">**Custom rollup suffix**</span></span>|<span data-ttu-id="f2a26-124">指定字串，用於附加至每一個積存資料行的名稱後面。</span><span class="sxs-lookup"><span data-stu-id="f2a26-124">Specifies the string to be appended to the name of each rollup column.</span></span> <span data-ttu-id="f2a26-125">預設值是 **CustomRollup**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-125">The default is **CustomRollup**.</span></span>|  
|<span data-ttu-id="f2a26-126">**自訂積存屬性後置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-126">**Custom rollup Properties suffix**</span></span>|<span data-ttu-id="f2a26-127">指定字串，用於附加至每一個積存屬性資料行的名稱後面。</span><span class="sxs-lookup"><span data-stu-id="f2a26-127">Specifies the string to be appended to the name of each rollup property column.</span></span> <span data-ttu-id="f2a26-128">預設值是 **CustomRollupProperties**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-128">The default is **CustomRollupProperties**.</span></span>|  
|<span data-ttu-id="f2a26-129">**一元運算子後置詞**</span><span class="sxs-lookup"><span data-stu-id="f2a26-129">**Unary operator suffix**</span></span>|<span data-ttu-id="f2a26-130">指定字串，用於附加至每一個一元運算子資料行的名稱後面。</span><span class="sxs-lookup"><span data-stu-id="f2a26-130">Specifies the string to be appended to the name of each unary operator column.</span></span> <span data-ttu-id="f2a26-131">預設值是 **UnaryOperator**。</span><span class="sxs-lookup"><span data-stu-id="f2a26-131">The default is **UnaryOperator**.</span></span>|  
  
 <span data-ttu-id="f2a26-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="f2a26-132">**Value**</span></span>  
 <span data-ttu-id="f2a26-133">針對 [選項]\*\*\*\* 中所指定的選項指定一個值，亦即您要在產生結構描述時使用的值。</span><span class="sxs-lookup"><span data-stu-id="f2a26-133">Specify a value for the option specified in **Option** that you want to use when the schema is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a26-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a26-134">See Also</span></span>  
 <span data-ttu-id="f2a26-135">[架構產生嚮導 F1 說明 &#40;Analysis Services-多維度資料&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2a26-135">[Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f2a26-136">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="f2a26-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
