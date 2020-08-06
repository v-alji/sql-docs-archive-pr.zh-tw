---
title: ADOMD.NET 伺服器功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f00215c6bcc0104c920be29e0837288a469b252e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687321"
---
# <a name="adomdnet-server-functionality"></a><span data-ttu-id="a6811-102">ADOMD.NET 伺服器功能</span><span class="sxs-lookup"><span data-stu-id="a6811-102">ADOMD.NET Server Functionality</span></span>
  <span data-ttu-id="a6811-103">所有的 ADOMD.NET 伺服器物件，都可用唯讀方式存取伺服器上的資料與中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a6811-103">All ADOMD.NET server objects provide read-only access to the data and metadata on the server.</span></span> <span data-ttu-id="a6811-104">若要擷取資料與中繼資料，使用 ADOMD.NET 伺服器物件模型做為伺服器物件模型，並不支援結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="a6811-104">To retrieve data and metadata, you use the ADOMD.NET server object model as the server object model does not support schema rowsets.</span></span>  
  
 <span data-ttu-id="a6811-105">透過 ADOMD.NET 伺服器物件，您可以 (UDF) 或的預存程式建立使用者定義函數 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6811-105">With ADOMD.NET server objects, you can create a user defined function (UDF) or a stored procedure for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a6811-106">這些同處理序方法是透過以多維度運算式 (MDX)、資料採礦延伸模組 (DMX) 或是 SQL 等語言所建立的查詢陳述式來呼叫。</span><span class="sxs-lookup"><span data-stu-id="a6811-106">These in-process methods are called through query statements created in languages such as Multidimensional Expressions (MDX), Data Mining Extensions (DMX), or SQL.</span></span> <span data-ttu-id="a6811-107">這些同處理序方法也提供與網路通訊關聯且沒有延遲的附加功能。</span><span class="sxs-lookup"><span data-stu-id="a6811-107">These in-process methods also provide added functionality without the latencies associated with network communications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6811-108">[Microsoft.analysisservices. AdomdServer. AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120))物件僅支援 DMX。</span><span class="sxs-lookup"><span data-stu-id="a6811-108">The [Microsoft.AnalysisServices.AdomdServer.AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) object only supports DMX.</span></span>  
  
## <a name="what-is-a-udf"></a><span data-ttu-id="a6811-109">何謂 UDF？</span><span class="sxs-lookup"><span data-stu-id="a6811-109">What is a UDF?</span></span>  
 <span data-ttu-id="a6811-110">*UDF*是具有下列特性的方法：</span><span class="sxs-lookup"><span data-stu-id="a6811-110">A *UDF* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="a6811-111">您可以在查詢內容中呼叫 UDF。</span><span class="sxs-lookup"><span data-stu-id="a6811-111">You can call the UDF in the context of a query.</span></span>  
  
-   <span data-ttu-id="a6811-112">UDF 可以採取任何數目的參數。</span><span class="sxs-lookup"><span data-stu-id="a6811-112">The UDF can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="a6811-113">UDF 可以傳回各種類型的資料。</span><span class="sxs-lookup"><span data-stu-id="a6811-113">The UDF can return various types of data.</span></span>  
  
 <span data-ttu-id="a6811-114">下列範例使用虛構的 UDF `FinalSalesNumber`：</span><span class="sxs-lookup"><span data-stu-id="a6811-114">The following example uses the fictional UDF, `FinalSalesNumber`:</span></span>  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a><span data-ttu-id="a6811-115">何謂預存程序？</span><span class="sxs-lookup"><span data-stu-id="a6811-115">What is a Stored Procedure?</span></span>  
 <span data-ttu-id="a6811-116">*預存*程式是具有下列特性的方法：</span><span class="sxs-lookup"><span data-stu-id="a6811-116">A *stored procedure* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="a6811-117">您可以使用 MDX [call](/sql/mdx/mdx-data-manipulation-call)語句，自行呼叫預存程式。</span><span class="sxs-lookup"><span data-stu-id="a6811-117">You call a stored procedure on its own with the MDX [CALL](/sql/mdx/mdx-data-manipulation-call) statement.</span></span>  
  
-   <span data-ttu-id="a6811-118">預存程序可以使用任何數目的參數。</span><span class="sxs-lookup"><span data-stu-id="a6811-118">A stored procedure can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="a6811-119">預存程序可以傳回資料集、`IDataReader` 或是空的結果。</span><span class="sxs-lookup"><span data-stu-id="a6811-119">A stored procedure can return a dataset, an `IDataReader`, or an empty result.</span></span>  
  
 <span data-ttu-id="a6811-120">下列範例使用虛構的預存程序 `FinalSalesNumbers`：</span><span class="sxs-lookup"><span data-stu-id="a6811-120">The following example uses the fictional stored procedure, `FinalSalesNumbers`:</span></span>  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6811-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6811-121">See Also</span></span>  
 [<span data-ttu-id="a6811-122">ADOMD.NET 伺服器程式設計</span><span class="sxs-lookup"><span data-stu-id="a6811-122">ADOMD.NET Server Programming</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
