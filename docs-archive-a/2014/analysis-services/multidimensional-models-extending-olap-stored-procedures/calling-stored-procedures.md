---
title: 呼叫預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c9da6edef576a6ab25c183cbc87ff95cc056845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700441"
---
# <a name="calling-stored-procedures"></a><span data-ttu-id="e433b-102">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="e433b-102">Calling Stored Procedures</span></span>
  <span data-ttu-id="e433b-103">可以在伺服器上，或從用戶端應用程式呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="e433b-103">Stored procedures can be called on the server or from client application.</span></span> <span data-ttu-id="e433b-104">在這兩種情況下，預存程序永遠會在伺服器上執行，不論是伺服器或資料庫的內容。</span><span class="sxs-lookup"><span data-stu-id="e433b-104">In either case, stored procedures always run on the server, either the context of the server or of a database.</span></span> <span data-ttu-id="e433b-105">執行預存程序並不需要特殊的權限。</span><span class="sxs-lookup"><span data-stu-id="e433b-105">There are no special permissions required to execute a stored procedure.</span></span> <span data-ttu-id="e433b-106">組件將預存程序加入到伺服器或資料庫內容後，任何使用者都可以執行預存程序，只要使用者的角色允許該預存程序執行的動作。</span><span class="sxs-lookup"><span data-stu-id="e433b-106">Once a stored procedure is added by an assembly to the server or database context, any user can execute the stored procedure as long as the role for the user permits the actions performed by the stored procedure.</span></span>  
  
 <span data-ttu-id="e433b-107">在 MDX 中呼叫預存程序，與呼叫內建 MDX 函數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="e433b-107">Calling a stored procedure in MDX is done in the same manner as calling an intrinsic MDX function.</span></span> <span data-ttu-id="e433b-108">對於未採用參數的預存程序，則會使用程序名稱和空白的成對括號，如此處所示：</span><span class="sxs-lookup"><span data-stu-id="e433b-108">For a stored procedure that takes no parameters, the name of the procedure and an empty pair of parentheses are used, as shown here:</span></span>  
  
```  
MyStoredProcedure()  
```  
  
 <span data-ttu-id="e433b-109">如果預存程序有一或多個參數，則依序提供以逗號分隔的參數。</span><span class="sxs-lookup"><span data-stu-id="e433b-109">If the stored procedure takes one or more parameters, then the parameters are supplied, in order, separated by commas.</span></span> <span data-ttu-id="e433b-110">下例展示具有三個參數的預存程序範例：</span><span class="sxs-lookup"><span data-stu-id="e433b-110">The following example demonstrates a sample stored procedure with three parameters:</span></span>  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a><span data-ttu-id="e433b-111">在 MDX 查詢中呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="e433b-111">Calling Stored Procedures in MDX Queries</span></span>  
 <span data-ttu-id="e433b-112">在所有 MDX 查詢中，預存程序必須傳回 MDX 運算式所需的句法正確類型。</span><span class="sxs-lookup"><span data-stu-id="e433b-112">In all MDX queries, the stored procedure must return the syntactically correct type required by an MDX expression.</span></span> <span data-ttu-id="e433b-113">如果預存程序沒有傳回正確類型，就會發生 MDX 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e433b-113">If a stored procedure does not return the correct type, an MDX error occurs.</span></span> <span data-ttu-id="e433b-114">下列範例展示的預存程序會傳回數學運算的集合、成員和結果。</span><span class="sxs-lookup"><span data-stu-id="e433b-114">The following examples demonstrate stored procedures that return a set, a member, and the result of a mathematical operation.</span></span>  
  
### <a name="returning-a-set"></a><span data-ttu-id="e433b-115">傳回集合</span><span class="sxs-lookup"><span data-stu-id="e433b-115">Returning a Set</span></span>  
 <span data-ttu-id="e433b-116">下列範例實作名稱為 MySproc 的預存程序，它會傳回一個集合。</span><span class="sxs-lookup"><span data-stu-id="e433b-116">The following examples implement a stored procedure, called MySproc, that returns a set.</span></span> <span data-ttu-id="e433b-117">在第一個範例中，MySproc 會在 SELECT 運算式中直接傳回集合。</span><span class="sxs-lookup"><span data-stu-id="e433b-117">In the first example, MySproc returns the set directly in the SELECT expression.</span></span> <span data-ttu-id="e433b-118">其次的兩個範例中，MySproc 會將集合以 Crossjoin 和 DrilldownLevel 函數之引數的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="e433b-118">In the second two examples, MySproc returns the set as an argument for the Crossjoin and DrilldownLevel functions.</span></span>  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a><span data-ttu-id="e433b-119">傳回成員</span><span class="sxs-lookup"><span data-stu-id="e433b-119">Returning a Member</span></span>  
 <span data-ttu-id="e433b-120">下例顯示名稱為 MySproc 的函數，它會傳回一個成員：</span><span class="sxs-lookup"><span data-stu-id="e433b-120">The following example shows a function MySproc function that returns a member:</span></span>  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a><span data-ttu-id="e433b-121">傳回數學運算的結果</span><span class="sxs-lookup"><span data-stu-id="e433b-121">Returning the Result of a Math Operation</span></span>  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a><span data-ttu-id="e433b-122">使用 CALL 陳述式呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="e433b-122">Calling Stored Procedures with the Call Statement</span></span>  
 <span data-ttu-id="e433b-123">使用 MDX `Call` 陳述式，可以在 MDX 查詢內容的外部呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="e433b-123">Stored procedures can be called outside of the context of an MDX query using the MDX `Call` statement.</span></span>  
  
 <span data-ttu-id="e433b-124">您可使用這個方法具現化預存程序的副作用，或讓應用程式取得預存查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="e433b-124">You can use this method to either instantiate the side effects of a stored query or for the application to get the results of a stored query.</span></span> <span data-ttu-id="e433b-125">`Call` 陳述式的常見用法，是使用分析管理物件 (AMO) 來執行不會傳回結果的管理功能。</span><span class="sxs-lookup"><span data-stu-id="e433b-125">A common use of the `Call` statement would be to use Analysis Management Objects (AMO) to perform administrative functions that do not have a return result.</span></span> <span data-ttu-id="e433b-126">例如，下列命令會呼叫預存程序：</span><span class="sxs-lookup"><span data-stu-id="e433b-126">For example, the following command calls a stored procedure:</span></span>  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 <span data-ttu-id="e433b-127">在 `Call` 陳述式中，預存程序傳回的唯一支援類型是資料列集。</span><span class="sxs-lookup"><span data-stu-id="e433b-127">The only supported type returned from stored procedure in a `Call` statement is a rowset.</span></span> <span data-ttu-id="e433b-128">資料列集的序列化是由 XML for Analysis 定義的。</span><span class="sxs-lookup"><span data-stu-id="e433b-128">The serialization for a rowset is defined by XML for Analysis.</span></span> <span data-ttu-id="e433b-129">如果 `Call` 陳述式中的預存程序傳回任何其他的類型，則會被忽略，而且不會以 XML 的方式傳回給呼叫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e433b-129">If a stored procedure in a `Call` statement returns any other type, it is ignored and not returned in XML to the calling application.</span></span> <span data-ttu-id="e433b-130">如需有關 XML for Analysis 資料列集的詳細資訊，請參閱＜XML for Analysis 結構描述資料列集＞。</span><span class="sxs-lookup"><span data-stu-id="e433b-130">For more information about XML for Analysis rowsets, see, XML for Analysis Schema Rowsets.</span></span>  
  
 <span data-ttu-id="e433b-131">如果預存程序傳回 .NET 資料列集，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會將伺服器上的結果轉換成 XML for Analysis 資料列集。</span><span class="sxs-lookup"><span data-stu-id="e433b-131">If a stored procedure returns a .NET rowset, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] converts the result on the server to an XML for Analysis rowset.</span></span> <span data-ttu-id="e433b-132">XML for Analysis 資料列集一律由 `Call` 函數中的預存程序傳回。</span><span class="sxs-lookup"><span data-stu-id="e433b-132">The XML for Analysis rowset is always returned by a stored procedure in the `Call` function.</span></span> <span data-ttu-id="e433b-133">如果資料集包含的功能無法在 XML for Analysis 資料列集內表示，結果會失敗。</span><span class="sxs-lookup"><span data-stu-id="e433b-133">If a dataset contains features that cannot be expressed in the XML for Analysis rowset, a failure results.</span></span>  
  
 <span data-ttu-id="e433b-134">傳回空值的程序 (例如，Visual Basic 中的副程式) 也可以和 CALL 關鍵字一起使用。</span><span class="sxs-lookup"><span data-stu-id="e433b-134">Procedures that return void values (for example, subroutines in Visual Basic) can also be employed with the CALL keyword.</span></span> <span data-ttu-id="e433b-135">例如，如果您想要在 MDX 陳述式中使用函數 MyVoidFunction()，應使用以下的語法：</span><span class="sxs-lookup"><span data-stu-id="e433b-135">If, for example, you wanted to use the function MyVoidFunction() in an MDX statement, the following syntax would be employed:</span></span>  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e433b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e433b-136">See Also</span></span>  
 <span data-ttu-id="e433b-137">[多維度模型元件管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="e433b-137">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="e433b-138">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="e433b-138">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
