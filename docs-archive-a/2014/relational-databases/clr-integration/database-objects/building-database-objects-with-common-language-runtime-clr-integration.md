---
title: 使用 Common Language Runtime 建立資料庫物件 (CLR) 整合 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c849c095a3be1c590e6fcb3ce87a0725eb795c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597162"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a><span data-ttu-id="fa844-102">利用 Common Language Runtime (CLR) 整合建置資料庫物件</span><span class="sxs-lookup"><span data-stu-id="fa844-102">Building Database Objects with Common Language Runtime (CLR) Integration</span></span>
  <span data-ttu-id="fa844-103">您可以使用來建立資料庫物件， [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 稱為「CLR 常式」。</span><span class="sxs-lookup"><span data-stu-id="fa844-103">You can build database objects using the [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is referred to as a "CLR routine."</span></span> <span data-ttu-id="fa844-104">這些常式包括：</span><span class="sxs-lookup"><span data-stu-id="fa844-104">These routines include:</span></span>  
  
-   <span data-ttu-id="fa844-105">純量值的使用者定義函數 (純量 UDF)</span><span class="sxs-lookup"><span data-stu-id="fa844-105">Scalar-valued user-defined functions (scalar UDFs)</span></span>  
  
-   <span data-ttu-id="fa844-106">資料表值使用者定義函數 (TVF)</span><span class="sxs-lookup"><span data-stu-id="fa844-106">Table-valued user-defined functions (TVFs)</span></span>  
  
-   <span data-ttu-id="fa844-107">使用者定義程序 (UDP)</span><span class="sxs-lookup"><span data-stu-id="fa844-107">User-defined procedures (UDPs)</span></span>  
  
-   <span data-ttu-id="fa844-108">使用者定義觸發程序</span><span class="sxs-lookup"><span data-stu-id="fa844-108">User-defined triggers</span></span>  
  
 <span data-ttu-id="fa844-109">CLR 常式在 Managed 程式碼中包含三個相同的結構。</span><span class="sxs-lookup"><span data-stu-id="fa844-109">CLR routines have the same structure in managed code.</span></span> <span data-ttu-id="fa844-110">這三個結構會對應到類別的 public、static (在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 中則為 shared) 方法。</span><span class="sxs-lookup"><span data-stu-id="fa844-110">They are mapped to public, static (shared in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) methods of a class.</span></span> <span data-ttu-id="fa844-111">除了常式之外，使用者定義型別 (UDT) 和使用者定義彙總函式也可以使用 .NET Framework 來定義。</span><span class="sxs-lookup"><span data-stu-id="fa844-111">In addition to routines, user-defined types (UDTs) and user-defined aggregate functions can also be defined using the .NET Framework.</span></span> <span data-ttu-id="fa844-112">UDT 和使用者定義彙總都會對應到整個 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="fa844-112">UDTs and user-defined aggregates are mapped to entire .NET Framework classes.</span></span>  
  
 <span data-ttu-id="fa844-113">每種類型的 .NET Framework 常式都有 [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可以使用對等的。</span><span class="sxs-lookup"><span data-stu-id="fa844-113">Each type of .NET Framework routine has a [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] that the [!INCLUDE[tsql](../../../includes/tsql-md.md)] equivalent can be used.</span></span> <span data-ttu-id="fa844-114">例如，純量 UDF 可以在任何純量運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="fa844-114">For instance, scalar UDFs can be used in any scalar expression.</span></span> <span data-ttu-id="fa844-115">TVF 可以在任何 FROM 子句中使用。</span><span class="sxs-lookup"><span data-stu-id="fa844-115">A TVF can be used in any FROM clause.</span></span> <span data-ttu-id="fa844-116">程序可以在 EXEC 陳述式中叫用，或從用戶端應用程式叫用。</span><span class="sxs-lookup"><span data-stu-id="fa844-116">A procedure can be invoked in an EXEC statement or invoked from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa844-117">Common Language Runtime 上的 CLR 物件 (使用者定義函數、使用者定義類型或觸發程序) 可以在多個執行緒上執行 (平行計畫)，如果查詢最佳化工具判定這是有幫助的。</span><span class="sxs-lookup"><span data-stu-id="fa844-117">Execution of a CLR object (user-defined function, user-defined type, or trigger) on the common language runtime can take place on multiple threads (parallel plan), if the query optimizer decides it is beneficial.</span></span> <span data-ttu-id="fa844-118">不過，如果使用者定義函數存取資料，則是以序列計畫執行。</span><span class="sxs-lookup"><span data-stu-id="fa844-118">However, if a user-defined function accesses data, execution will be  on a serial plan.</span></span> <span data-ttu-id="fa844-119">在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 之前的伺服器版本上執行時，如果使用者定義函數包含 LOB 參數或傳回值，也必須以序列計畫執行。</span><span class="sxs-lookup"><span data-stu-id="fa844-119">When executed on a server version prior to [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], if a user-defined function contains LOB parameters or return values, execution also must be on a serial plan.</span></span>  
  
 <span data-ttu-id="fa844-120">下表列出此章節所涵蓋的主題。</span><span class="sxs-lookup"><span data-stu-id="fa844-120">The following table lists the topics covered in this section.</span></span>  
  
 [<span data-ttu-id="fa844-121">CLR 整合使用者入門</span><span class="sxs-lookup"><span data-stu-id="fa844-121">Getting Started with CLR Integration</span></span>](getting-started-with-clr-integration.md)  
 <span data-ttu-id="fa844-122">提供搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用 CLR 整合編譯物件所需之程式庫與命名空間的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="fa844-122">Provides a brief overview of the libraries and namespaces required to compile object using CLR integration with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fa844-123">包含範例 "Hello World" CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="fa844-123">Includes an example "Hello World" CLR stored procedure.</span></span>  
  
 [<span data-ttu-id="fa844-124">支援的 .NET Framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="fa844-124">Supported .NET Framework Libraries</span></span>](supported-net-framework-libraries.md)  
 <span data-ttu-id="fa844-125">提供 CLR 整合支援之 .NET Framework 程式庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa844-125">Provides information on the .NET Framework libraries supported by CLR integration.</span></span>  
  
 [<span data-ttu-id="fa844-126">CLR 整合程式設計模型限制</span><span class="sxs-lookup"><span data-stu-id="fa844-126">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
 <span data-ttu-id="fa844-127">提供 CLR 整合程式設計模型限制的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa844-127">Provides information about CLR integration programming model restrictions.</span></span>  
  
 [<span data-ttu-id="fa844-128">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="fa844-128">SQL Server Data Types in the .NET Framework</span></span>](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 <span data-ttu-id="fa844-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型及其 .NET Framework 對等項目的概觀。</span><span class="sxs-lookup"><span data-stu-id="fa844-129">An overview of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types and their .NET Framework equivalents.</span></span>  
  
 [<span data-ttu-id="fa844-130">CLR 整合自訂屬性的概觀</span><span class="sxs-lookup"><span data-stu-id="fa844-130">Overview of CLR Integration Custom Attributes</span></span>](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 <span data-ttu-id="fa844-131">提供 CLR 整合自訂屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa844-131">Provides information about CLR integration custom attributes.</span></span>  
  
 [<span data-ttu-id="fa844-132">CLR 使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="fa844-132">CLR User-Defined Functions</span></span>](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 <span data-ttu-id="fa844-133">描述如何實作與使用各種類型的 CLR 函數：資料表值函式、純量函數，以及使用者定義彙總函式。</span><span class="sxs-lookup"><span data-stu-id="fa844-133">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="fa844-134">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="fa844-134">CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="fa844-135">描述如何實作及使用 CLR 使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="fa844-135">Describes how to implement and use CLR user-defined types.</span></span>  
  
 [<span data-ttu-id="fa844-136">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="fa844-136">CLR Stored Procedures</span></span>](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 <span data-ttu-id="fa844-137">描述如何實作及使用 CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="fa844-137">Describes how to implement and use CLR stored procedures.</span></span>  
  
 [<span data-ttu-id="fa844-138">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="fa844-138">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
 <span data-ttu-id="fa844-139">描述如何實作及使用 CLR 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="fa844-139">Describes how to implement and use CLR triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa844-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa844-140">See Also</span></span>  
 [<span data-ttu-id="fa844-141">Common Language Runtime &#40;CLR&#41; 整合總覽</span><span class="sxs-lookup"><span data-stu-id="fa844-141">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](../common-language-runtime-integration-overview.md)  
  
  
