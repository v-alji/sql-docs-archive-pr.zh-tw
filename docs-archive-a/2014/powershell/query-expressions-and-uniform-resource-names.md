---
title: 查詢運算式和統一資源名稱 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- query expressions
- unique resource names
- URN
ms.assetid: e0d30dbe-7daf-47eb-8412-1b96792b6fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: db6e311dd7d8a824b0e2f22e538e15eefa9fd9ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595157"
---
# <a name="query-expressions-and-uniform-resource-names"></a><span data-ttu-id="503c8-102">查詢運算式和統一的資源名稱</span><span class="sxs-lookup"><span data-stu-id="503c8-102">Query Expressions and Uniform Resource Names</span></span>
  <span data-ttu-id="503c8-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理物件 (SMO) 模型和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 嵌入式管理單元會使用與 XPath 運算式類似的兩種運算式字串類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object (SMO) models and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins use two types of expression strings that are similar to XPath expressions.</span></span> <span data-ttu-id="503c8-104">查詢運算式是字串，其中指定一組用來列舉物件模型階層中之一個或多個物件的準則。</span><span class="sxs-lookup"><span data-stu-id="503c8-104">Query expressions are strings that specify a set of criteria used to enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="503c8-105">統一資源名稱 (URN) 是可唯一識別單一物件的特定查詢運算式字串類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-105">A Uniform Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503c8-106">語法</span><span class="sxs-lookup"><span data-stu-id="503c8-106">Syntax</span></span>  
  
```
      Object1  
      [<FilterExpression1>]/ ... /ObjectN[<FilterExpressionN>]<FilterExpression>::=  
<PropertyExpression> [and <PropertyExpression>][...n]  
  
<PropertyExpression>::=@BooleanPropertyName=true()  
 | @BooleanPropertyName=false()  
 | contains(@StringPropertyName, 'PatternString')  
  | @StringPropertyName='String'  
 | @DatePropertyName=datetime('DateString')  
 | is_null(@PropertyName)  
 | not(<PropertyExpression>)  
```  
  
## <a name="arguments"></a><span data-ttu-id="503c8-107">引數</span><span class="sxs-lookup"><span data-stu-id="503c8-107">Arguments</span></span>  
 <span data-ttu-id="503c8-108">*Object*</span><span class="sxs-lookup"><span data-stu-id="503c8-108">*Object*</span></span>  
 <span data-ttu-id="503c8-109">指定運算式字串之該節點所代表的物件類型。</span><span class="sxs-lookup"><span data-stu-id="503c8-109">Specifies the type of object that is represented at that node of the expression string.</span></span> <span data-ttu-id="503c8-110">每個物件都代表這些 SMO 物件模型命名空間的集合類別：</span><span class="sxs-lookup"><span data-stu-id="503c8-110">Each object represents a collection class from these SMO object model namespaces:</span></span>  
  
 <xref:Microsoft.SqlServer.Management.Smo>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Agent>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Mail>  
  
 <xref:Microsoft.SqlServer.Management.Dmf>  
  
 <xref:Microsoft.SqlServer.Management.Facets>  
  
 <xref:Microsoft.SqlServer.Management.RegisteredServers>  
  
 <xref:Microsoft.SqlServer.Management.Smo.RegSvrEnum>  
  
 <span data-ttu-id="503c8-111">例如，您可以指定 Server 來代表 **ServerCollection** 類別，或指定 Database 來代表 **DatabaseCollection** 類別。</span><span class="sxs-lookup"><span data-stu-id="503c8-111">For example, specify Server for the **ServerCollection** class, Database for the **DatabaseCollection** class.</span></span>  
  
 <span data-ttu-id="503c8-112">\@*PropertyName*</span><span class="sxs-lookup"><span data-stu-id="503c8-112">\@*PropertyName*</span></span>  
 <span data-ttu-id="503c8-113">指定與 *Object*中指定物件相關聯之類別的其中一個屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="503c8-113">Specifies the name of one of the properties of the class that is associated with the object specified in *Object*.</span></span> <span data-ttu-id="503c8-114">屬性的名稱必須以 \@ 字元當作前置詞。</span><span class="sxs-lookup"><span data-stu-id="503c8-114">The name of the property must be prefixed with the \@ character.</span></span> <span data-ttu-id="503c8-115">例如，針對 \@ [**資料庫**類別] 屬性 [ **IsAnsiNull**] 指定 IsAnsiNull。</span><span class="sxs-lookup"><span data-stu-id="503c8-115">For example, specify \@IsAnsiNull for the **Database** class property **IsAnsiNull**.</span></span>  
  
 <span data-ttu-id="503c8-116">\@*BooleanPropertyName*= true ( # A1</span><span class="sxs-lookup"><span data-stu-id="503c8-116">\@*BooleanPropertyName*=true()</span></span>  
 <span data-ttu-id="503c8-117">列舉指定之布林屬性設定為 TRUE 的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-117">Enumerates all objects where the specified Boolean property is set to TRUE.</span></span>  
  
 <span data-ttu-id="503c8-118">\@*BooleanPropertyName*= false ( # A1</span><span class="sxs-lookup"><span data-stu-id="503c8-118">\@*BooleanPropertyName*=false()</span></span>  
 <span data-ttu-id="503c8-119">列舉指定之布林屬性設定為 FALSE 的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-119">Enumerates all objects where the specified Boolean property is set to FALSE.</span></span>  
  
 <span data-ttu-id="503c8-120">contains(\@*StringPropertyName*, '*PatternString*')</span><span class="sxs-lookup"><span data-stu-id="503c8-120">contains(\@*StringPropertyName*, '*PatternString*')</span></span>  
 <span data-ttu-id="503c8-121">列舉指定之字串屬性包含至少一個 '*PatternString*' 中指定之字元集的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-121">Enumerates all objects where the specified string property contains at least one occurrence of the set of characters that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="503c8-122">\@*StringPropertyName*='*PatternString*'</span><span class="sxs-lookup"><span data-stu-id="503c8-122">\@*StringPropertyName*='*PatternString*'</span></span>  
 <span data-ttu-id="503c8-123">列舉指定之字串屬性值與 '*PatternString*' 中指定之字元模式完全相同的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-123">Enumerates all objects where the value of the specified string property is exactly the same as the character pattern that is specified in '*PatternString*'.</span></span>  
  
 <span data-ttu-id="503c8-124">\@*DatePropertyName*= datetime('*DateString*')</span><span class="sxs-lookup"><span data-stu-id="503c8-124">\@*DatePropertyName*= datetime('*DateString*')</span></span>  
 <span data-ttu-id="503c8-125">列舉指定之日期屬性值與 '*DateString*' 中指定之日期相符的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-125">Enumerates all objects where the value of the specified date property matches the date that is specified in '*DateString*'.</span></span> <span data-ttu-id="503c8-126">*DateString* 必須遵循格式 yyyy-mm-dd hh:mi:ss.mmm。</span><span class="sxs-lookup"><span data-stu-id="503c8-126">*DateString* must follow the format yyyy-mm-dd hh:mi:ss.mmm</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="503c8-127">yyyy</span><span class="sxs-lookup"><span data-stu-id="503c8-127">yyyy</span></span>|<span data-ttu-id="503c8-128">四位數的年份。</span><span class="sxs-lookup"><span data-stu-id="503c8-128">Four digit year.</span></span>|  
|<span data-ttu-id="503c8-129">mm</span><span class="sxs-lookup"><span data-stu-id="503c8-129">mm</span></span>|<span data-ttu-id="503c8-130">兩位數的月份 (01 到 12)。</span><span class="sxs-lookup"><span data-stu-id="503c8-130">Two digit month (01 through 12).</span></span>|  
|<span data-ttu-id="503c8-131">dd</span><span class="sxs-lookup"><span data-stu-id="503c8-131">dd</span></span>|<span data-ttu-id="503c8-132">兩位數的日期 (01 到 31)。</span><span class="sxs-lookup"><span data-stu-id="503c8-132">Two digit date (01 through 31).</span></span>|  
|<span data-ttu-id="503c8-133">hh</span><span class="sxs-lookup"><span data-stu-id="503c8-133">hh</span></span>|<span data-ttu-id="503c8-134">兩位數的小時，使用 24 小時制 (01 到 23)。</span><span class="sxs-lookup"><span data-stu-id="503c8-134">Two digit hour using a 24 hour clock (01 through 23).</span></span>|  
|<span data-ttu-id="503c8-135">mi</span><span class="sxs-lookup"><span data-stu-id="503c8-135">mi</span></span>|<span data-ttu-id="503c8-136">兩位數的分鐘 (01 到 59)。</span><span class="sxs-lookup"><span data-stu-id="503c8-136">Two digit minutes (01 through 59).</span></span>|  
|<span data-ttu-id="503c8-137">ss</span><span class="sxs-lookup"><span data-stu-id="503c8-137">ss</span></span>|<span data-ttu-id="503c8-138">兩位數的秒鐘 (01 到 59)。</span><span class="sxs-lookup"><span data-stu-id="503c8-138">Two digit seconds (01 through 59).</span></span>|  
|<span data-ttu-id="503c8-139">mmm</span><span class="sxs-lookup"><span data-stu-id="503c8-139">mmm</span></span>|<span data-ttu-id="503c8-140">毫秒數 (001 到 999)。</span><span class="sxs-lookup"><span data-stu-id="503c8-140">Number of milliseconds (001 through 999).</span></span>|  
  
 <span data-ttu-id="503c8-141">您可以針對儲存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的任何日期格式，評估使用這種格式所指定的日期。</span><span class="sxs-lookup"><span data-stu-id="503c8-141">The dates that are specified in this format can be evaluated against any date format that is stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="503c8-142">is_null(\@*PropertyName*)</span><span class="sxs-lookup"><span data-stu-id="503c8-142">is_null(\@*PropertyName*)</span></span>  
 <span data-ttu-id="503c8-143">列舉指定之屬性具有 NULL 值的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-143">Enumerates all objects where the specified property has a value of NULL.</span></span>  
  
 <span data-ttu-id="503c8-144">不 (\<*PropertyExpression*>) </span><span class="sxs-lookup"><span data-stu-id="503c8-144">not(\<*PropertyExpression*>)</span></span>  
 <span data-ttu-id="503c8-145">執行 *PropertyExpression*評估值的否定運算，並且列舉不符合 *PropertyExpression*中指定之條件的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-145">Negates the evaluation value of the *PropertyExpression*, enumerating all objects that do not match the condition specified in *PropertyExpression*.</span></span> <span data-ttu-id="503c8-146">例如，not(contains(\@Name, 'xyz')) 會列舉名稱中沒有 xyz 字串的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-146">For example, not(contains(\@Name, 'xyz')) enumerates all objects that do not have the string xyz in their names.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="503c8-147">備註</span><span class="sxs-lookup"><span data-stu-id="503c8-147">Remarks</span></span>  
 <span data-ttu-id="503c8-148">查詢運算式是列舉 SMO 模型階層中之節點的字串。</span><span class="sxs-lookup"><span data-stu-id="503c8-148">Query expressions are strings that enumerate the nodes in an SMO model hierarchy.</span></span> <span data-ttu-id="503c8-149">每個節點都具有指定準則的篩選運算式，用於決定要列舉位於該節點的哪些物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-149">Each node has a filter expression that specifies the criteria for determining which objects at that node are enumerated.</span></span> <span data-ttu-id="503c8-150">查詢運算式是以 XPath 運算式語言建立模型。</span><span class="sxs-lookup"><span data-stu-id="503c8-150">Query expressions are modeled on the XPath expression language.</span></span> <span data-ttu-id="503c8-151">查詢運算式會實作 XPath 所支援之運算式的小型子集，而且也具有在 XPath 中找不到的某些延伸模組。</span><span class="sxs-lookup"><span data-stu-id="503c8-151">Query expressions implement a small subset of the expressions that are supported by XPath, and also have some extensions that are not found in XPath.</span></span> <span data-ttu-id="503c8-152">XPath 運算式是字串，其中指定一組用來列舉 XML 文件之一個或多個標記的準則。</span><span class="sxs-lookup"><span data-stu-id="503c8-152">XPath expressions are strings that specify a set of criteria that are used to enumerate one or more of the tags in an XML document.</span></span> <span data-ttu-id="503c8-153">如需有關 XPath 的詳細資訊，請參閱 [W3C XPath Language](http://www.w3.org/TR/xpath20/)(W3C XPath 語言)。</span><span class="sxs-lookup"><span data-stu-id="503c8-153">For more information about XPath, see [W3C XPath Language](http://www.w3.org/TR/xpath20/).</span></span>  
  
 <span data-ttu-id="503c8-154">查詢運算式必須以伺服器物件的絕對參考為開頭。</span><span class="sxs-lookup"><span data-stu-id="503c8-154">Query expressions must start with an absolute reference to the Server object.</span></span> <span data-ttu-id="503c8-155">不允許使用含有前置 / 的相對運算式。</span><span class="sxs-lookup"><span data-stu-id="503c8-155">Relative expressions with a leading / are not allowed.</span></span> <span data-ttu-id="503c8-156">在查詢運算式中指定之物件的順序必須遵循相關聯物件模型中之集合物件的階層。</span><span class="sxs-lookup"><span data-stu-id="503c8-156">The sequence of objects that are specified in a query expression must follow the hierarchy of collection objects in the associated object model.</span></span> <span data-ttu-id="503c8-157">例如，在 Microsoft.SqlServer.Management.Smo 命名空間中參考物件的查詢運算式必須以伺服器節點為開頭，後面接著資料庫節點等項目。</span><span class="sxs-lookup"><span data-stu-id="503c8-157">For example, a query expression that references objects in the Microsoft.SqlServer.Management.Smo namespace must start with a Server node followed by a Database node, and so on.</span></span>  
  
 <span data-ttu-id="503c8-158">如果 *\<FilterExpression>* 未指定物件的，則會列舉該節點上的所有物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-158">If a *\<FilterExpression>* is not specified for an object, all the objects at that node are enumerated.</span></span>  
  
## <a name="uniform-resource-names-urn"></a><span data-ttu-id="503c8-159">統一資源名稱 (URN)</span><span class="sxs-lookup"><span data-stu-id="503c8-159">Uniform Resource Names (URN)</span></span>  
 <span data-ttu-id="503c8-160">URN 是查詢運算式的子集。</span><span class="sxs-lookup"><span data-stu-id="503c8-160">URNs are a subset of query expressions.</span></span> <span data-ttu-id="503c8-161">每個 URN 都會構成單一物件的完整參考。</span><span class="sxs-lookup"><span data-stu-id="503c8-161">Each URN forms a fully-qualified reference to a single object.</span></span> <span data-ttu-id="503c8-162">一般的 URN 會使用 Name 屬性來識別位於每個節點的單一物件。</span><span class="sxs-lookup"><span data-stu-id="503c8-162">A typical URN uses the Name property to identify a single object at each node.</span></span> <span data-ttu-id="503c8-163">例如，這個 URN 會參考特定資料行：</span><span class="sxs-lookup"><span data-stu-id="503c8-163">For example, this URN refers to a specific column:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[@Name='SalesPerson' and @Schema='Sales']/Column[@Name='SalesPersonID']  
```  
  
## <a name="examples"></a><span data-ttu-id="503c8-164">範例</span><span class="sxs-lookup"><span data-stu-id="503c8-164">Examples</span></span>  
  
### <a name="a-enumerating-objects-using-false"></a><span data-ttu-id="503c8-165">A.</span><span class="sxs-lookup"><span data-stu-id="503c8-165">A.</span></span> <span data-ttu-id="503c8-166">使用 false() 列舉物件</span><span class="sxs-lookup"><span data-stu-id="503c8-166">Enumerating objects using false()</span></span>  
 <span data-ttu-id="503c8-167">這個查詢運算式會列舉在 **MyComputer** 的預設執行個體中將 **AutoClose**屬性設定為 false 的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="503c8-167">This query expression enumerates all the databases that have the **AutoClose** attribute set to false in the default instance on **MyComputer**.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@AutoClose=false()]  
```  
  
### <a name="b-enumerating-objects-using-contains"></a><span data-ttu-id="503c8-168">B.</span><span class="sxs-lookup"><span data-stu-id="503c8-168">B.</span></span> <span data-ttu-id="503c8-169">使用 contains 列舉物件</span><span class="sxs-lookup"><span data-stu-id="503c8-169">Enumerating objects using contains</span></span>  
 <span data-ttu-id="503c8-170">這個查詢運算式會列舉不區分大小寫而且名稱具有 'm' 字元的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="503c8-170">This query expression enumerates all the databases that are case-insensitive and have the character 'm' in their name.</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@CaseSensitive=false() and contains(@Name, 'm')]   
```  
  
### <a name="c-enumerating-objects-using-not"></a><span data-ttu-id="503c8-171">C.</span><span class="sxs-lookup"><span data-stu-id="503c8-171">C.</span></span> <span data-ttu-id="503c8-172">使用 not 列舉物件</span><span class="sxs-lookup"><span data-stu-id="503c8-172">Enumerating objects using not</span></span>  
 <span data-ttu-id="503c8-173">這個查詢運算式會列舉不在 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Production **結構描述中而且資料表名稱包含 History 一詞的所有** 資料表：</span><span class="sxs-lookup"><span data-stu-id="503c8-173">This query expression enumerates all of [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] tables that are not in the **Production** schema and contain the word History in the table name:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[not(@Schema='Production') and contains(@Name, 'History')]  
```  
  
### <a name="d-not-supplying-a-filter-expression-for-the-final-node"></a><span data-ttu-id="503c8-174">D.</span><span class="sxs-lookup"><span data-stu-id="503c8-174">D.</span></span> <span data-ttu-id="503c8-175">不會為最終節點提供篩選運算式</span><span class="sxs-lookup"><span data-stu-id="503c8-175">Not supplying a filter expression for the final node</span></span>  
 <span data-ttu-id="503c8-176">這個查詢運算式會列舉 **AdventureWorks2012.Sales.SalesPerson** 資料表中的所有資料行：</span><span class="sxs-lookup"><span data-stu-id="503c8-176">This query expression enumerates all the columns in the **AdventureWorks2012.Sales.SalesPerson** table:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@Schema='Sales' and @Name='SalesPerson']/Columns  
```  
  
### <a name="e-enumerating-objects-using-datetime"></a><span data-ttu-id="503c8-177">E.</span><span class="sxs-lookup"><span data-stu-id="503c8-177">E.</span></span> <span data-ttu-id="503c8-178">使用日期時間列舉物件</span><span class="sxs-lookup"><span data-stu-id="503c8-178">Enumerating objects using datetime</span></span>  
 <span data-ttu-id="503c8-179">這個查詢運算式會列舉於特定時間在 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中建立的所有資料表：</span><span class="sxs-lookup"><span data-stu-id="503c8-179">This query expression enumerates all the tables that are created in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database at a specific time:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@CreateDate=datetime('2008-03-21 19:49:32.647')]  
```  
  
### <a name="f-enumerating-objects-using-is_null"></a><span data-ttu-id="503c8-180">F.</span><span class="sxs-lookup"><span data-stu-id="503c8-180">F.</span></span> <span data-ttu-id="503c8-181">使用 is_null 列舉物件</span><span class="sxs-lookup"><span data-stu-id="503c8-181">Enumerating objects using is_null</span></span>  
 <span data-ttu-id="503c8-182">這個查詢運算式會列舉 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中上次修改日期屬性沒有 NULL 的所有資料表：</span><span class="sxs-lookup"><span data-stu-id="503c8-182">This query expression enumerates all the tables in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database that do not have NULL for their date last modified property:</span></span>  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[Not(is_null(@DateLastModified))]  
```  
  
## <a name="see-also"></a><span data-ttu-id="503c8-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503c8-183">See Also</span></span>  
 <span data-ttu-id="503c8-184">[Invoke-policyevaluation Cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span><span class="sxs-lookup"><span data-stu-id="503c8-184">[Invoke-PolicyEvaluation cmdlet](../database-engine/invoke-policyevaluation-cmdlet.md) </span></span>  
 [<span data-ttu-id="503c8-185">SQL Server Audit &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="503c8-185">SQL Server Audit &#40;Database Engine&#41;</span></span>](../relational-databases/security/auditing/sql-server-audit-database-engine.md)  
