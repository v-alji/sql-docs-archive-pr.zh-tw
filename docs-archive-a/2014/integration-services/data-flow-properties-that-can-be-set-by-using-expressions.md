---
title: 可以使用運算式設定的資料流程屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1763a531b1d91a60d2bb3775ae9fbe9942c6b7e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688082"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a><span data-ttu-id="db55f-102">可以使用運算式設定的資料流程屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-102">Data Flow Properties that Can Be Set by Using Expressions</span></span>
  <span data-ttu-id="db55f-103">可使用「資料流程」工作容器上提供的屬性運算式，以指定資料流程物件的某些屬性值。</span><span class="sxs-lookup"><span data-stu-id="db55f-103">The values of certain properties of data flow objects can be specified by using property expressions available on the Data Flow task container.</span></span>  
  
 <span data-ttu-id="db55f-104">如需使用屬性運算式的資訊，請參閱 [在封裝中使用屬性運算式](expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="db55f-104">For information about using property expressions, see [Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="db55f-105">您可以使用屬性運算式來為封裝之每個部署的執行個體自訂組態。</span><span class="sxs-lookup"><span data-stu-id="db55f-105">You can use property expressions to customize configurations for each deployed instance of a package.</span></span> <span data-ttu-id="db55f-106">您也可以使用屬性運算式來指定封裝的執行階段條件約束，其方法是搭配 **dtexec** 命令提示字元公用程式使用 **/set** 選項。</span><span class="sxs-lookup"><span data-stu-id="db55f-106">You can also use property expressions to specify run-time constraints for a package by using the **/set** option with the **dtexec** command prompt utility.</span></span> <span data-ttu-id="db55f-107">例如，您可以約束「排序」轉換所使用的 `MaximumThreads`，或是「模糊群組」和「模糊查閱」轉換所使用的 `MaxMemoryUsage`。</span><span class="sxs-lookup"><span data-stu-id="db55f-107">For example, you can constrain the `MaximumThreads` used by the Sort transformation, or the `MaxMemoryUsage` of the Fuzzy Grouping and Fuzzy Lookup transformations.</span></span> <span data-ttu-id="db55f-108">如果未受到約束，這些轉換可能會在記憶體中快取大量的資料。</span><span class="sxs-lookup"><span data-stu-id="db55f-108">If unconstrained, these transformations may cache large amounts of data in memory.</span></span>  
  
 <span data-ttu-id="db55f-109">若要針對本主題所列的其中一個資料流程物件屬性指定屬性運算式，請顯示資料流程工作的 [屬性]\*\*\*\* 視窗，其方式是在設計工具的 [控制流程]\*\*\*\* 介面上選取資料流程工作，或是選取設計工具的 [資料流程]\*\*\*\* 索引標籤，而不需選取任何個別的元件或路徑。</span><span class="sxs-lookup"><span data-stu-id="db55f-109">To specify a property expression for one of the properties of data flow objects listed in this topic, display the **Properties** window for the Data Flow task by selecting the Data Flow task on the **Control Flow** surface of the designer, or by selecting the **Data Flow** tab of the designer without selecting any individual component or path.</span></span> <span data-ttu-id="db55f-110">選取 [運算式]\*\*\*\* 屬性，然後按一下省略符號 (...)，顯示 [屬性運算式編輯器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db55f-110">Select the **Expressions** property and click the ellipsis (...) to display the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="db55f-111">下拉 [屬性]\*\*\*\* 清單來選取屬性，然後在 [運算式]\*\*\*\* 文字方塊中輸入運算式，或是按一下省略符號 (...) 以顯示 [運算式產生器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db55f-111">Drop down the **Property** list to select a property, then type an expression in the **Expression** text box, or click the ellipsis (...) to display the **Expression Builder** dialog box.</span></span>  
  
 <span data-ttu-id="db55f-112">[屬性]\*\*\*\* 清單只會針對您已經放在設計工具之 [資料流程]\*\*\*\* 介面上的那些資料流程物件來顯示可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="db55f-112">The **Property** list displays available properties for only those data flow objects that you have already placed on the **Data Flow** surface of the designer.</span></span> <span data-ttu-id="db55f-113">因此，您無法使用 [屬性]\*\*\*\* 清單來檢視支援屬性運算式之資料流程物件的所有可能屬性。</span><span class="sxs-lookup"><span data-stu-id="db55f-113">Therefore, you cannot use the **Property** list to view all the possible properties of data flow objects that support property expressions.</span></span> <span data-ttu-id="db55f-114">例如，如果您已在設計工具介面上放置 ADO NET 來源，則 [**屬性**] 清單會包含屬性的專案 `[ADO NET Source].[SqlCommand]` 。</span><span class="sxs-lookup"><span data-stu-id="db55f-114">For example, if you have placed an ADO NET source on the designer surface, the **Property** list contains an entry for the `[ADO NET Source].[SqlCommand]` property.</span></span> <span data-ttu-id="db55f-115">此清單也會顯示資料流程工作本身的許多屬性。</span><span class="sxs-lookup"><span data-stu-id="db55f-115">The list also displays many properties of the Data Flow task itself.</span></span>  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a><span data-ttu-id="db55f-116">支援屬性運算式之資料流程物件的屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-116">Properties of Data Flow Objects That Support Property Expressions</span></span>  
 <span data-ttu-id="db55f-117">可以使用屬性運算式來指定下列清單中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="db55f-117">The values of the properties in the following list can be specified by using property expressions.</span></span>  
  
### <a name="data-flow-sources"></a><span data-ttu-id="db55f-118">資料流程來源</span><span class="sxs-lookup"><span data-stu-id="db55f-118">Data Flow Sources</span></span>  
  
|<span data-ttu-id="db55f-119">資料流程物件</span><span class="sxs-lookup"><span data-stu-id="db55f-119">Data Flow object</span></span>|<span data-ttu-id="db55f-120">屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-120">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="db55f-121">ADO NET 來源</span><span class="sxs-lookup"><span data-stu-id="db55f-121">ADO NET source</span></span>|<span data-ttu-id="db55f-122">TableOrViewName 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-122">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="db55f-123">SqlCommand 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-123">SqlCommand property</span></span>|  
|<span data-ttu-id="db55f-124">XML 來源</span><span class="sxs-lookup"><span data-stu-id="db55f-124">XML source</span></span>|<span data-ttu-id="db55f-125">XMLData 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-125">XMLData property</span></span><br /><br /> <span data-ttu-id="db55f-126">XMLSchemaDefinition 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-126">XMLSchemaDefinition property</span></span>|  
  
### <a name="data-flow-transformations"></a><span data-ttu-id="db55f-127">資料流程轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-127">Data Flow Transformations</span></span>  
 <span data-ttu-id="db55f-128">如需這些自訂屬性的詳細資訊，請參閱 [轉換自訂屬性](data-flow/transformations/transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="db55f-128">For more information about these custom properties, see [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
|<span data-ttu-id="db55f-129">資料流程物件</span><span class="sxs-lookup"><span data-stu-id="db55f-129">Data Flow object</span></span>|<span data-ttu-id="db55f-130">屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-130">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="db55f-131">條件式分割轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-131">Conditional Split transformation</span></span>|<span data-ttu-id="db55f-132">FriendlyExpression 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-132">FriendlyExpression property</span></span>|  
|<span data-ttu-id="db55f-133">衍生的資料行轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-133">Derived Column transformation</span></span>|<span data-ttu-id="db55f-134">FriendlyExpression 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-134">FriendlyExpression property</span></span>|  
|<span data-ttu-id="db55f-135">模糊群組轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-135">Fuzzy Grouping transformation</span></span>|<span data-ttu-id="db55f-136">MaxMemoryUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-136">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="db55f-137">模糊查閱轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-137">Fuzzy Lookup transformation</span></span>|<span data-ttu-id="db55f-138">MaxMemoryUsage 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-138">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="db55f-139">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-139">Lookup transformation</span></span>|<span data-ttu-id="db55f-140">SqlCommand 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-140">SqlCommand property</span></span><br /><br /> <span data-ttu-id="db55f-141">SqlCommandParam 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-141">SqlCommandParam property</span></span>|  
|<span data-ttu-id="db55f-142">OLE DB 命令轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-142">OLE DB Command transformation</span></span>|<span data-ttu-id="db55f-143">SqlCommand 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-143">SqlCommand property</span></span>|  
|<span data-ttu-id="db55f-144">百分比取樣轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-144">Percentage Sampling transformation</span></span>|<span data-ttu-id="db55f-145">SamplingValue 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-145">SamplingValue property</span></span>|  
|<span data-ttu-id="db55f-146">樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-146">Pivot transformation</span></span>|<span data-ttu-id="db55f-147">PivotKeyValue 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-147">PivotKeyValue property</span></span>|  
|<span data-ttu-id="db55f-148">資料列取樣轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-148">Row Sampling transformation</span></span>|<span data-ttu-id="db55f-149">SamplingValue 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-149">SamplingValue property</span></span>|  
|<span data-ttu-id="db55f-150">排序轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-150">Sort transformation</span></span>|<span data-ttu-id="db55f-151">MaximumThreads 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-151">MaximumThreads property</span></span>|  
|<span data-ttu-id="db55f-152">取消樞紐轉換</span><span class="sxs-lookup"><span data-stu-id="db55f-152">Unpivot transformation</span></span>|<span data-ttu-id="db55f-153">PivotKeyValue 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-153">PivotKeyValue property</span></span>|  
  
### <a name="data-flow-destinations"></a><span data-ttu-id="db55f-154">資料流程目的地</span><span class="sxs-lookup"><span data-stu-id="db55f-154">Data Flow Destinations</span></span>  
  
|<span data-ttu-id="db55f-155">資料流程物件</span><span class="sxs-lookup"><span data-stu-id="db55f-155">Data Flow object</span></span>|<span data-ttu-id="db55f-156">屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-156">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="db55f-157">ADO NET 目的地</span><span class="sxs-lookup"><span data-stu-id="db55f-157">ADO NET Destination</span></span>|<span data-ttu-id="db55f-158">TableOrViewName 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-158">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="db55f-159">BatchSize 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-159">BatchSize property</span></span><br /><br /> <span data-ttu-id="db55f-160">CommandTimeout 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-160">CommandTimeout property</span></span>|  
|<span data-ttu-id="db55f-161">一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="db55f-161">Flat File destination</span></span>|<span data-ttu-id="db55f-162">Header 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-162">Header property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="db55f-163">Compact 目的地</span><span class="sxs-lookup"><span data-stu-id="db55f-163">Compact destination</span></span>|<span data-ttu-id="db55f-164">TableName 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-164">TableName property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="db55f-165">目的地</span><span class="sxs-lookup"><span data-stu-id="db55f-165">destination</span></span>|<span data-ttu-id="db55f-166">BulkInsertTableName 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-166">BulkInsertTableName property</span></span><br /><br /> <span data-ttu-id="db55f-167">BulkInsertFirstRow 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-167">BulkInsertFirstRow property</span></span><br /><br /> <span data-ttu-id="db55f-168">BulkInsertLastRow 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-168">BulkInsertLastRow property</span></span><br /><br /> <span data-ttu-id="db55f-169">BulkInsertOrder 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-169">BulkInsertOrder property</span></span><br /><br /> <span data-ttu-id="db55f-170">Timeout 屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-170">Timeout property</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="db55f-171">相關工作</span><span class="sxs-lookup"><span data-stu-id="db55f-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="db55f-172">加入或變更屬性運算式</span><span class="sxs-lookup"><span data-stu-id="db55f-172">Add or Change a Property Expression</span></span>](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a><span data-ttu-id="db55f-173">相關內容</span><span class="sxs-lookup"><span data-stu-id="db55f-173">Related Content</span></span>  
 <span data-ttu-id="db55f-174">pragmaticworks.com 上的技術文件： [SSIS 運算式小抄](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="db55f-174">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db55f-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db55f-175">See Also</span></span>  
 <span data-ttu-id="db55f-176">[在封裝中使用屬性運算式](expressions/use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="db55f-176">[Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="db55f-177">[通用屬性](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="db55f-177">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="db55f-178">[轉換自訂屬性](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="db55f-178">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="db55f-179">路徑屬性</span><span class="sxs-lookup"><span data-stu-id="db55f-179">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
  
