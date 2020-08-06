---
title: SQLXML Managed 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: rothja
ms.author: jroth
ms.openlocfilehash: bb8d2d4f2d2fc512901e4ad37f0e46cf696b9475
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584353"
---
# <a name="sqlxml-managed-classes"></a><span data-ttu-id="643c5-102">SQLXML Managed 類別</span><span class="sxs-lookup"><span data-stu-id="643c5-102">SQLXML Managed Classes</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="643c5-103">SQLXML Managed 類別會在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 內部公開 SQLXML 4.0 的功能。</span><span class="sxs-lookup"><span data-stu-id="643c5-103">SQLXML Managed Classes exposes the functionality of SQLXML 4.0 inside the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="643c5-104">您可以利用 SQLXML Managed 類別撰寫 C# 應用程式來存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體中的 XML 資料、將資料帶到 .NET Framework 環境、處理資料，以及將更新傳回 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 做為 DiffGram 來套用更新。</span><span class="sxs-lookup"><span data-stu-id="643c5-104">With SQLXML Managed Classes, you can write a C# application to access XML data from an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], bring the data into the .NET Framework environment, process the data, and send the updates back to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a DiffGram to apply the updates.</span></span> <span data-ttu-id="643c5-105">使用 SQLXML Managed 類別，將更新套用到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫時，您必須使用對應的結構描述。</span><span class="sxs-lookup"><span data-stu-id="643c5-105">You must use a mapping schema when applying updates to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using SQLXML Managed Classes.</span></span> <span data-ttu-id="643c5-106">如需實用範例，請參閱[存取 .Net 環境中的 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="643c5-106">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="643c5-107">若要搭配 SQLXML 4.0 使用 SQLXML Managed 類別，您必須安裝 Microsoft Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="643c5-107">To use the SQLXML Managed Classes with SQLXML 4.0, you must install Microsoft Visual Studio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="643c5-108">.NET Framework 包含 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="643c5-108">The .NET Framework includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Data Provider.</span></span> <span data-ttu-id="643c5-109">此提供者可用於存取 .NET 環境中的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，不過，它僅能處理傳統的 SQL 查詢 (也就是除了 FOR XML 查詢之外的關聯式資料庫查詢)。</span><span class="sxs-lookup"><span data-stu-id="643c5-109">This provider can be used to access [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the .NET environment; however, it can handle only traditional SQL queries (that is, relational database queries with the exception of FOR XML queries).</span></span> <span data-ttu-id="643c5-110">您無法在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中執行 XML 範本或伺服器端的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="643c5-110">You cannot execute XML templates or the server-side XPath queries in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="643c5-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="643c5-111">In This Section</span></span>  
 [<span data-ttu-id="643c5-112">SQLXML Managed 類別物件模型</span><span class="sxs-lookup"><span data-stu-id="643c5-112">SQLXML Managed Classes Object Model</span></span>](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 <span data-ttu-id="643c5-113">記載 SQLXML Managed 類別及其屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="643c5-113">Documents SQLXML Managed Classes and their properties and methods.</span></span>  
  
 [<span data-ttu-id="643c5-114">使用 SQLXML Managed 類別</span><span class="sxs-lookup"><span data-stu-id="643c5-114">Using the SQLXML Managed Classes</span></span>](sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="643c5-115">提供使用 SQLXML Managed 類別的範例。</span><span class="sxs-lookup"><span data-stu-id="643c5-115">Provides examples of using SQLXML Managed Classes.</span></span>  
  
  
