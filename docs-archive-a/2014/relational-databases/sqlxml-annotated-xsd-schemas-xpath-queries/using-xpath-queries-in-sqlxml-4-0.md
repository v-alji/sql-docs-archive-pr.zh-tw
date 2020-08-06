---
title: 在 SQLXML 4.0 中使用 XPath 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML]
- annotated XSD schemas, XPath queries
- queries [SQLXML], XPath
- XML views [SQLXML]
ms.assetid: 7814d099-81ec-4fb8-894a-729cdbb5015a
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d82513b22d2a50aedb37955a210dd33746db86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597736"
---
# <a name="using-xpath-queries-in-sqlxml-40"></a><span data-ttu-id="ee42b-102">在 SQLXML 4.0 中使用 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="ee42b-102">Using XPath Queries in SQLXML 4.0</span></span>
  <span data-ttu-id="ee42b-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對於註解式 XSD 結構描述的支援可讓您建立資料庫中儲存之關聯式資料的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="ee42b-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support for annotated XSD schemas allows you to create XML views of the relational data stored in the database.</span></span> <span data-ttu-id="ee42b-104">您可以使用 XPath 語言的子集來查詢註解式 XSD 結構描述所建立的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="ee42b-104">You can use a subset of the XPath language to query the XML views created by an annotated XSD schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee42b-105">若要了解 SQLXML 4.0 中的 XPath 查詢，您必須熟悉 XML 檢視和相關的概念，例如範本與對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="ee42b-105">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="ee42b-106">如需詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="ee42b-106">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="ee42b-107">如需 XPath 的詳細資訊，請參閱全球資訊網協會所定義的 XPath 標準 (W3C) ，網址為 http://www.w3.org/TR/xpath 。</span><span class="sxs-lookup"><span data-stu-id="ee42b-107">For more information about XPath, see the XPath standard defined by the World Wide Web Consortium (W3C) at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee42b-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="ee42b-108">In This Section</span></span>  
 [<span data-ttu-id="ee42b-109">使用 XPath 查詢的簡介 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="ee42b-109">Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;</span></span>](introduction-to-using-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="ee42b-110">提供 SQLXML 4.0 中關於 XPath 查詢的簡介資訊，包括支援與不支援之 W3C XPath 規格中的功能。</span><span class="sxs-lookup"><span data-stu-id="ee42b-110">Provides introductory information about XPath queries in SQLXML 4.0, including supported and unsupported functionality from the W3C XPath specification.</span></span>  
  
 [<span data-ttu-id="ee42b-111">指定位置路徑 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="ee42b-111">Specifying a Location Path &#40;SQLXML 4.0&#41;</span></span>](location-path/specifying-a-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="ee42b-112">描述如何在 XPath 查詢中指定位置路徑。</span><span class="sxs-lookup"><span data-stu-id="ee42b-112">Describes how to specify location paths in XPath queries.</span></span>  
  
 [<span data-ttu-id="ee42b-113">&#40;SQLXML 4.0&#41;的範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="ee42b-113">Sample XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/sample-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="ee42b-114">提供適用於 SQLXML 4.0 的 XPath 查詢範例。</span><span class="sxs-lookup"><span data-stu-id="ee42b-114">Provides sample XPath queries for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="ee42b-115">&#40;SQLXML 4.0&#41;的 XPath 資料類型</span><span class="sxs-lookup"><span data-stu-id="ee42b-115">XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="ee42b-116">描述與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 XSD 之資料類型大為不同的 XPath 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ee42b-116">Describes XPath data types, which are significantly different from those of both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee42b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee42b-117">See Also</span></span>  
 [<span data-ttu-id="ee42b-118">用戶端 XML 格式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="ee42b-118">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
