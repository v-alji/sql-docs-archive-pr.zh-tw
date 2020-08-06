---
title: 使用 SQLXMLOLEDB 提供者 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e3c53eecd657d610c2fe90e108e0290e9b05b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596605"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a><span data-ttu-id="ed9f6-102">使用 SQLXMLOLEDB 提供者 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ed9f6-102">Using the SQLXMLOLEDB Provider (SQLXML 4.0)</span></span>
  <span data-ttu-id="ed9f6-103">本章節的主題提供了 ADO 範例應用程式來說明 SQLXMLOLEDB 提供者特定之屬性的使用。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-103">The topics in this section provide ADO sample applications that illustrate the use of SQLXMLOLEDB Provider-specific properties.</span></span>  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a><span data-ttu-id="ed9f6-104">SQLXMLOLEDB 4.0 提供者的應用程式需求</span><span class="sxs-lookup"><span data-stu-id="ed9f6-104">Application Requirements for SQLXMLOLEDB 4.0 Provider</span></span>  
 <span data-ttu-id="ed9f6-105">若要建立可使用 SQLXMLOLEDB 4.0 的工作範例，您必須執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="ed9f6-105">To create working samples that use SQLXMLOLEDB 4.0, you must do the following:</span></span>  
  
1.  <span data-ttu-id="ed9f6-106">建立 Microsoft Visual Basic .exe 應用程式，並加入下列其中一個參考：</span><span class="sxs-lookup"><span data-stu-id="ed9f6-106">Create a Microsoft Visual Basic .exe application and add one of the following references:</span></span>  
  
    -   <span data-ttu-id="ed9f6-107">Microsoft ActiveX Data Objects 2.6 程式庫</span><span class="sxs-lookup"><span data-stu-id="ed9f6-107">Microsoft ActiveX Data Objects 2.6 Library</span></span>  
  
    -   <span data-ttu-id="ed9f6-108">Microsoft ActiveX Data Objects 2.7 程式庫</span><span class="sxs-lookup"><span data-stu-id="ed9f6-108">Microsoft ActiveX Data Objects 2.7 Library</span></span>  
  
    -   <span data-ttu-id="ed9f6-109">Microsoft ActiveX Data Objects 2.8 程式庫</span><span class="sxs-lookup"><span data-stu-id="ed9f6-109">Microsoft ActiveX Data Objects 2.8 Library</span></span>  
  
2.  <span data-ttu-id="ed9f6-110">部署及安裝 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-110">Deploy and install SQLXML 4.0 and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
     <span data-ttu-id="ed9f6-111">如需詳細資訊，請參閱[SQLXML 4.0 程式設計概念](../../sqlxml/sqlxml-4-0-programming-concepts.md)和[安裝 SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-111">For more information, see on [SQLXML 4.0 Programming Concepts](../../sqlxml/sqlxml-4-0-programming-concepts.md) and [Installing SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed9f6-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="ed9f6-112">In This Section</span></span>  
 [<span data-ttu-id="ed9f6-113">&#40;SQLXMLOLEDB 提供者&#41;執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="ed9f6-113">Executing SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-114">說明如何使用 ClientSideXML 和 xml 根屬性來執行 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-114">Illustrates the use of the ClientSideXML and xml root properties to execute SQL queries.</span></span>  
  
 [<span data-ttu-id="ed9f6-115">&#40;SQLXMLOLEDB 提供者執行包含 SQL 查詢的範本&#41;</span><span class="sxs-lookup"><span data-stu-id="ed9f6-115">Executing Templates That Contain SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-116">說明如何使用 ClientSideXML 屬性。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-116">Illustrates the use of the ClientSideXML property.</span></span>  
  
 [<span data-ttu-id="ed9f6-117">&#40;SQLXMLOLEDB 提供者&#41;執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="ed9f6-117">Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-118">說明如何使用 ClientSideXML、基底路徑和對應架構屬性。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-118">Illustrates the use of the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="ed9f6-119">使用命名空間執行 XPath 查詢 &#40;SQLXMLOLEDB 提供者&#41;</span><span class="sxs-lookup"><span data-stu-id="ed9f6-119">Executing XPath Queries with Namespaces &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-120">說明如何針對符合命名空間的結構描述執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-120">Illustrates how to query against namespace-qualified schemas.</span></span>  
  
 [<span data-ttu-id="ed9f6-121">&#40;SQLXMLOLEDB 提供者執行包含 XPath 查詢的範本&#41;</span><span class="sxs-lookup"><span data-stu-id="ed9f6-121">Executing Templates That Contain XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-122">說明如何使用 ClientSideXML、基底路徑和對應架構屬性來執行具有 SQL 查詢的範本。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-122">Illustrates how to execute templates with SQL queries using the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="ed9f6-123">&#40;SQLXMLOLEDB 提供者套用 XSL 轉換&#41;</span><span class="sxs-lookup"><span data-stu-id="ed9f6-123">Applying an XSL Transformation &#40;SQLXMLOLEDB Provider&#41;</span></span>](applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 <span data-ttu-id="ed9f6-124">說明在套用 XSL 轉換時，使用 ClientSideXML 和 xsl 屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="ed9f6-124">Illustrates the use of the ClientSideXML and xsl properties in applying an XSL transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed9f6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed9f6-125">See Also</span></span>  
 [<span data-ttu-id="ed9f6-126">SQL Server Native Client 的系統需求</span><span class="sxs-lookup"><span data-stu-id="ed9f6-126">System Requirements for SQL Server Native Client</span></span>](../../native-client/system-requirements-for-sql-server-native-client.md)  
  
  
