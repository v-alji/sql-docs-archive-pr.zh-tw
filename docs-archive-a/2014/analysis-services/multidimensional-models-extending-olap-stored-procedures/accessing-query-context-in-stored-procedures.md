---
title: 存取預存程式中的查詢內容 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686524"
---
# <a name="accessing-query-context-in-stored-procedures"></a><span data-ttu-id="eb0be-102">在預存程序中存取查詢內容</span><span class="sxs-lookup"><span data-stu-id="eb0be-102">Accessing Query Context in Stored Procedures</span></span>
  <span data-ttu-id="eb0be-103">預存程序的執行內容可以在該預存程序的程式碼中使用，如同 ADOMD.NET 伺服器物件模型的 `Context` 物件。</span><span class="sxs-lookup"><span data-stu-id="eb0be-103">The execution context of a stored procedure is available within the code of the stored procedure as the `Context` object of the ADOMD.NET server object model.</span></span> <span data-ttu-id="eb0be-104">這是唯讀的內容，而且不能由預存程序加以修改。</span><span class="sxs-lookup"><span data-stu-id="eb0be-104">This is a read-only context and cannot be modified by the stored procedure.</span></span> <span data-ttu-id="eb0be-105">下列屬性可以在此物件上使用。</span><span class="sxs-lookup"><span data-stu-id="eb0be-105">The following properties are available on this object.</span></span>  
  
|<span data-ttu-id="eb0be-106">屬性</span><span class="sxs-lookup"><span data-stu-id="eb0be-106">Property</span></span>|<span data-ttu-id="eb0be-107">類型</span><span class="sxs-lookup"><span data-stu-id="eb0be-107">Type</span></span>|<span data-ttu-id="eb0be-108">描述</span><span class="sxs-lookup"><span data-stu-id="eb0be-108">Description</span></span>|  
|--------------|----------|-----------------|  
|<span data-ttu-id="eb0be-109">**CurrentCube**</span><span class="sxs-lookup"><span data-stu-id="eb0be-109">**CurrentCube**</span></span>|<span data-ttu-id="eb0be-110">Cube</span><span class="sxs-lookup"><span data-stu-id="eb0be-110">Cube</span></span>|<span data-ttu-id="eb0be-111">目前查詢內容的 Cube。</span><span class="sxs-lookup"><span data-stu-id="eb0be-111">The cube for the current query context.</span></span>|  
|<span data-ttu-id="eb0be-112">**CurrentDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="eb0be-112">**CurrentDatabaseName**</span></span>|<span data-ttu-id="eb0be-113">String</span><span class="sxs-lookup"><span data-stu-id="eb0be-113">String</span></span>|<span data-ttu-id="eb0be-114">目前資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb0be-114">The identifier of the current database.</span></span>|  
|<span data-ttu-id="eb0be-115">**CurrentConnection**</span><span class="sxs-lookup"><span data-stu-id="eb0be-115">**CurrentConnection**</span></span>|<span data-ttu-id="eb0be-116">Connection</span><span class="sxs-lookup"><span data-stu-id="eb0be-116">Connection</span></span>|<span data-ttu-id="eb0be-117">對目前內容中之連線物件的參考。</span><span class="sxs-lookup"><span data-stu-id="eb0be-117">A reference to the connection object in the current context.</span></span>|  
|<span data-ttu-id="eb0be-118">**通過**</span><span class="sxs-lookup"><span data-stu-id="eb0be-118">**Pass**</span></span>|<span data-ttu-id="eb0be-119">整數</span><span class="sxs-lookup"><span data-stu-id="eb0be-119">Integer</span></span>|<span data-ttu-id="eb0be-120">目前內容的行程數目。</span><span class="sxs-lookup"><span data-stu-id="eb0be-120">The pass number for the current context.</span></span>|  
  
 <span data-ttu-id="eb0be-121">預存程序中若使用到多維度運算式 (MDX) 物件模型，會有 `Context` 物件。</span><span class="sxs-lookup"><span data-stu-id="eb0be-121">The `Context` object exists when the Multidimensional Expressions (MDX) object model is used in a stored procedure.</span></span> <span data-ttu-id="eb0be-122">如果是在用戶端上使用 MDX 物件模型，則無法使用該物件。</span><span class="sxs-lookup"><span data-stu-id="eb0be-122">It is not available when the MDX object model is used on a client.</span></span> <span data-ttu-id="eb0be-123">`Context` 物件並未明確地傳遞至預存程序，或由預存程序傳回。</span><span class="sxs-lookup"><span data-stu-id="eb0be-123">The `Context` object is not explicitly passed to or returned by the stored procedure.</span></span> <span data-ttu-id="eb0be-124">在預存程序執行時可使用此物件。</span><span class="sxs-lookup"><span data-stu-id="eb0be-124">It is available during the execution of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0be-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb0be-125">See Also</span></span>  
 <span data-ttu-id="eb0be-126">[多維度模型元件管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="eb0be-126">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="eb0be-127">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="eb0be-127">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
