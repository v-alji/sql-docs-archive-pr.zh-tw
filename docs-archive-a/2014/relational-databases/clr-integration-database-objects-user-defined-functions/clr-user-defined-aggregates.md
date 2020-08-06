---
title: CLR 使用者定義匯總 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596734"
---
# <a name="clr-user-defined-aggregates"></a><span data-ttu-id="76524-102">CLR 使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="76524-102">CLR User-Defined Aggregates</span></span>
  <span data-ttu-id="76524-103">彙總函式會根據一組值來執行計算，再傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="76524-103">Aggregate functions perform a calculation on a set of values and return a single value.</span></span> <span data-ttu-id="76524-104">傳統上， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 僅支援內建的彙總函式（例如 `SUM` 或），該函式 `MAX` 會在一組輸入純量值上運作，並從該集合產生單一匯總值。</span><span class="sxs-lookup"><span data-stu-id="76524-104">Traditionally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has supported only built-in aggregate functions, such as `SUM` or `MAX`, that operate on a set of input scalar values and generate a single aggregate value from that set.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="76524-105">與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Common Language Runtime (CLR) 的整合現在可讓開發人員以 Managed 程式碼建立自訂彙總函式，並讓這些函式可以存取 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="76524-105">integration with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) now allows developers to create custom aggregate functions in managed code, and to make these functions accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span>  
  
 <span data-ttu-id="76524-106">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="76524-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="76524-107">CLR 使用者定義彙總的需求</span><span class="sxs-lookup"><span data-stu-id="76524-107">Requirements for CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates-requirements.md)  
 <span data-ttu-id="76524-108">提供實作 CLR 使用者定義彙總函式之需求的概觀。</span><span class="sxs-lookup"><span data-stu-id="76524-108">Provides an overview of the requirements for implementing CLR user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="76524-109">叫用 CLR 使用者定義彙總函式</span><span class="sxs-lookup"><span data-stu-id="76524-109">Invoking CLR User-Defined Aggregate Functions</span></span>](clr-user-defined-aggregate-invoking-functions.md)  
 <span data-ttu-id="76524-110">說明如何叫用使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="76524-110">Explains how to invoke user-defined aggregates.</span></span>  
  
  
