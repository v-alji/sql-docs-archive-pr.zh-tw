---
title: 執行 XML 資料的大量載入 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
author: rothja
ms.author: jroth
ms.openlocfilehash: ec540ff082b02fa43b9abd9f294752073eb68d5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686877"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a><span data-ttu-id="7244e-102">執行 XML 資料的大量載入 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7244e-102">Performing Bulk Load of XML Data (SQLXML 4.0)</span></span>
  <span data-ttu-id="7244e-103">XML 大量載入是獨立的 COM 物件，可讓您將半結構化的 XML 資料載入至 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="7244e-103">XML Bulk Load is a standalone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7244e-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="7244e-104">In This Section</span></span>  
 [<span data-ttu-id="7244e-105">XML 大量載入簡介 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-105">Introduction to XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-106">提供有關使用 XML 大量載入公用程式來大量載入 XML 資料的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="7244e-106">Provides general information about bulk loading XML data with the XML Bulk Load utility.</span></span> <span data-ttu-id="7244e-107">主題包含 XML 資料流以及交易與非交易大量載入作業。</span><span class="sxs-lookup"><span data-stu-id="7244e-107">Topics include XML data streaming and transacted vs. nontransacted bulk load operations.</span></span>  
  
 [<span data-ttu-id="7244e-108">記錄產生進程 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-108">Record Generation Process &#40;SQLXML 4.0&#41;</span></span>](record-generation-process-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-109">描述藉以產生 XML 大量載入之記錄的程序和規則。</span><span class="sxs-lookup"><span data-stu-id="7244e-109">Describes the process and rules by which records are generated for XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="7244e-110">&#40;SQLXML 4.0&#41;的注釋轉譯</span><span class="sxs-lookup"><span data-stu-id="7244e-110">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-111">描述 XML 大量載入如何解譯 XSD 和 XDR 結構描述中的註解。</span><span class="sxs-lookup"><span data-stu-id="7244e-111">Describes how XML Bulk Load interprets annotations in XSD and XDR schemas.</span></span>  
  
 [<span data-ttu-id="7244e-112">SQL Server XML 大量載入物件模型 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-112">SQL Server XML Bulk Load Object Model &#40;SQLXML 4.0&#41;</span></span>](sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-113">描述 Sqlxmlbulkload.sqlxmlbulkload.4.0 物件及其方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="7244e-113">Describes the SQLXMLBulkLoad object and its methods and properties.</span></span>  
  
 [<span data-ttu-id="7244e-114">XML 大量載入範例 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-114">XML Bulk Load Examples &#40;SQLXML 4.0&#41;</span></span>](xml-bulk-load-examples-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-115">提供使用 XML 大量載入的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="7244e-115">Provides example code that uses XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="7244e-116">資料類型與 XML 大量載入行為 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-116">Data Types and XML Bulk Load Behavior &#40;SQLXML 4.0&#41;</span></span>](data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-117">描述 XML 大量載入在處理 XSD 和 XDR 中的不同類型時的行為。</span><span class="sxs-lookup"><span data-stu-id="7244e-117">Describes XML Bulk Load Behavior with different types in XSD and XDR.</span></span>  
  
 [<span data-ttu-id="7244e-118">XML 大量載入的指導方針和限制 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7244e-118">Guidelines and Limitations of XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="7244e-119">列出一些在使用 XML 大量載入時要注意的問題。</span><span class="sxs-lookup"><span data-stu-id="7244e-119">Lists some issues to be aware of when working with XML Bulk Load.</span></span>  
  
  
