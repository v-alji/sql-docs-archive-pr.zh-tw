---
title: .NET Framework 中的 SQL Server 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- System.Data library
- System.Data.SqlTypes namespace
- data types [CLR integration]
- SqlTypes library
- database objects [CLR integration], data types
- common language runtime [SQL Server], data types
- building database objects [CLR integration], data types
- mapping data types [CLR integration]
ms.assetid: c70d3ffe-2c32-45a5-849b-ef113dda09b9
author: rothja
ms.author: jroth
ms.openlocfilehash: fe0ed680e7050c58738301256575e4138f21276f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709630"
---
# <a name="sql-server-data-types-in-the-net-framework"></a><span data-ttu-id="5c097-102">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="5c097-102">SQL Server Data Types in the .NET Framework</span></span>
  <span data-ttu-id="5c097-103">`SqlTypes` 程式庫是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 基底類別庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="5c097-103">The `SqlTypes` library is part of the base class library of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="5c097-104">其設計為提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中之資料類型具有相同語意及精確度的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c097-104">It is designed to provide data types with the same semantics and precision as those found in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="5c097-105">本主題描述 .NET Framework 程式設計人員的新語意，並介紹 `System.Data.SqlTypes` 程式庫隨附之 `System.Data` 命名空間中實作的類型。</span><span class="sxs-lookup"><span data-stu-id="5c097-105">This topic describes the new semantics to .NET Framework programmers, and introduces the types implemented in the `System.Data.SqlTypes` namespace that is included in the `System.Data` library.</span></span>  
  
 <span data-ttu-id="5c097-106">下表列出本節中的主題。</span><span class="sxs-lookup"><span data-stu-id="5c097-106">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="5c097-107">Null 屬性和三值邏輯比較</span><span class="sxs-lookup"><span data-stu-id="5c097-107">Nullability and Three-Value Logic Comparisons</span></span>](nullability-and-three-value-logic-comparisons.md)  
 <span data-ttu-id="5c097-108">討論如何處理包含 Common Language Runtime (CLR) 整合資料類型的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="5c097-108">Discusses how NULL values are handled with common language runtime (CLR) integration data types.</span></span>  
  
 [<span data-ttu-id="5c097-109">定序和 CLR 整合資料類型</span><span class="sxs-lookup"><span data-stu-id="5c097-109">Collation and CLR Integration Data Types</span></span>](collation-and-clr-integration-data-types.md)  
 <span data-ttu-id="5c097-110">描述如何處理包含 CLR 整合的定序。</span><span class="sxs-lookup"><span data-stu-id="5c097-110">Describes how collations are handled with CLR integration.</span></span>  
  
 [<span data-ttu-id="5c097-111">處理 CLR 中的大型物件 &#40;LOB&#41; 參數</span><span class="sxs-lookup"><span data-stu-id="5c097-111">Handling Large Object &#40;LOB&#41; Parameters in the CLR</span></span>](handling-large-object-lob-parameters-in-the-clr.md)  
 <span data-ttu-id="5c097-112">描述如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 CLR 之間傳遞 LOB 類型。</span><span class="sxs-lookup"><span data-stu-id="5c097-112">Describes how to pass LOB types between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the CLR.</span></span>  
  
 [<span data-ttu-id="5c097-113">對應 CLR 參數資料</span><span class="sxs-lookup"><span data-stu-id="5c097-113">Mapping CLR Parameter Data</span></span>](mapping-clr-parameter-data.md)  
 <span data-ttu-id="5c097-114">顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、CLR 整合和 .NET Framework 之間的資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="5c097-114">Shows data type mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CLR integration, and the .NET Framework.</span></span>  
  
  
