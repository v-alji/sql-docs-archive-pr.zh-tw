---
title: 使用者定義函數和預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686527"
---
# <a name="user-defined-functions-and-stored-procedures"></a><span data-ttu-id="19247-102">使用者定義函數和預存程序</span><span class="sxs-lookup"><span data-stu-id="19247-102">User Defined Functions and Stored Procedures</span></span>
  <span data-ttu-id="19247-103">透過 ADOMD.NET 伺服器物件，您可以建立使用者定義函數， (UDF) 或預存程式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，以便與來自伺服器的中繼資料和資料互動。</span><span class="sxs-lookup"><span data-stu-id="19247-103">With ADOMD.NET server objects, you can create user defined function (UDF) or stored procedures for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that interact with metadata and data from the server.</span></span> <span data-ttu-id="19247-104">這些同處理序 (In-Process) 方法是透過「多維度運算式」(Multidimensional Expressions，MDX) 或「資料採礦延伸模組」(Data Mining Extensions，DMX) 陳述式來呼叫，以提供附加功能，並不會有與網路通訊關聯的延遲。</span><span class="sxs-lookup"><span data-stu-id="19247-104">These in-process methods are called through Multidimensional Expressions (MDX) or Data Mining Extensions (DMX) statements to provide added functionality without the latencies associated with network communications.</span></span>  
  
## <a name="udf-examples"></a><span data-ttu-id="19247-105">UDF 範例</span><span class="sxs-lookup"><span data-stu-id="19247-105">UDF Examples</span></span>  
 <span data-ttu-id="19247-106">UDF 是一種可以在 MDX 或 DMX 陳述式的內容中呼叫的方法，可以使用任何數目的參數，並且可以傳回任何類型的資料。</span><span class="sxs-lookup"><span data-stu-id="19247-106">A UDF is a method that can be called in the context of an MDX or DMX statement, can take any number of parameters, and can return any type of data.</span></span>  
  
 <span data-ttu-id="19247-107">使用 MDX 建立的 UDF 類似於為 DMX 建立的 UDF。</span><span class="sxs-lookup"><span data-stu-id="19247-107">A UDF created using MDX is similar to one created for DMX.</span></span> <span data-ttu-id="19247-108">主要的差別在於[microsoft.analysisservices. AdomdServer.](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) coNtext 物件的某些屬性（例如[microsoft.analysisservices. AdomdServer](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) ）僅適用于一種指令碼語言或另一種語言版本。 CurrentCube [\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120))屬性。（英文）。</span><span class="sxs-lookup"><span data-stu-id="19247-108">The main difference is that certain properties of the [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object, such as the [Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube\*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) and [Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) properties, are available only for one scripting language or the other.</span></span>  
  
 <span data-ttu-id="19247-109">下列範例示範如何使用 UDF 傳回節點描述、篩選 Tuple 以及將篩選套用至 Tuple。</span><span class="sxs-lookup"><span data-stu-id="19247-109">The following examples show how to use a UDF to return a node description, filter tuples, and apply a filter to a tuple.</span></span>  
  
### <a name="returning-a-node-description"></a><span data-ttu-id="19247-110">傳回節點描述</span><span class="sxs-lookup"><span data-stu-id="19247-110">Returning a Node Description</span></span>  
 <span data-ttu-id="19247-111">下列範例會建立 UDF，以傳回指定節點的節點描述。</span><span class="sxs-lookup"><span data-stu-id="19247-111">The following example creates a UDF that returns the node description for a specified node.</span></span> <span data-ttu-id="19247-112">UDF 會使用其執行所在的目前內容，並使用 DMX FROM 子句，從目前的採礦模型擷取節點。</span><span class="sxs-lookup"><span data-stu-id="19247-112">The UDF uses the current context in which it is being run, and uses a DMX FROM clause to retrieve the node from the current mining model.</span></span>  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 <span data-ttu-id="19247-113">一旦部署，就可以透過下列 DMX 運算式來呼叫上述 UDF 範例，這將可擷取最有可能的預測節點。</span><span class="sxs-lookup"><span data-stu-id="19247-113">Once deployed, the previous UDF example can be called by the following DMX expression, which retrieves the most-likely prediction node.</span></span> <span data-ttu-id="19247-114">描述包含構成預測節點的條件資訊。</span><span class="sxs-lookup"><span data-stu-id="19247-114">The description contains information that describes the conditions that make up the prediction node.</span></span>  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a><span data-ttu-id="19247-115">傳回 Tuple</span><span class="sxs-lookup"><span data-stu-id="19247-115">Returning Tuples</span></span>  
 <span data-ttu-id="19247-116">下列範例使用集合和傳回計數，以及從集合隨機擷取 Tuple，以傳回最後的子集：</span><span class="sxs-lookup"><span data-stu-id="19247-116">The following example takes a set and a return count, and randomly retrieves tuples from the set, returning a final subset:</span></span>  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 <span data-ttu-id="19247-117">在下列 MDX 範例中會呼叫上述範例。</span><span class="sxs-lookup"><span data-stu-id="19247-117">The previous example is called in the following MDX example.</span></span> <span data-ttu-id="19247-118">在此 MDX 範例中，會從「**艾德公司**」資料庫中取出五個隨機狀態或省份。</span><span class="sxs-lookup"><span data-stu-id="19247-118">In this MDX example, five random states or provinces are retrieved from the **Adventure Works** database.</span></span>  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a><span data-ttu-id="19247-119">將篩選套用至 Tuple</span><span class="sxs-lookup"><span data-stu-id="19247-119">Applying a Filter to a Tuple</span></span>  
 <span data-ttu-id="19247-120">在下列範例中，UDF 是定義成使用集合，並使用 Expression 物件，將篩選套用至集合中的每個 Tuple。</span><span class="sxs-lookup"><span data-stu-id="19247-120">In the following example, a UDF is defined that takes a set, and applies a filter to each tuple in the set, using the Expression object.</span></span> <span data-ttu-id="19247-121">任何符合篩選的 Tuple 都將加入傳回的集合。</span><span class="sxs-lookup"><span data-stu-id="19247-121">Any tuples that conform to the filter will be added to a set that is returned.</span></span>  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 <span data-ttu-id="19247-122">在下列 MDX 範例中會呼叫上述範例，以便將集合篩選成以 'A' 開頭的城市名稱。</span><span class="sxs-lookup"><span data-stu-id="19247-122">The previous example is called in the following MDX example, which filters the set to cities with names beginning with 'A'.</span></span>  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a><span data-ttu-id="19247-123">預存程序範例</span><span class="sxs-lookup"><span data-stu-id="19247-123">Stored Procedure Example</span></span>  
 <span data-ttu-id="19247-124">在下列範例中，以 MDX 為基礎的預存程序使用 AMO 為「網際網路銷售」建立資料分割 (若有需要的話)。</span><span class="sxs-lookup"><span data-stu-id="19247-124">In the following example, an MDX-based stored procedure uses AMO to create partitions, if needed, for Internet Sales.</span></span>  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
