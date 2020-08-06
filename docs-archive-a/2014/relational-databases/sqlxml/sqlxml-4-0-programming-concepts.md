---
title: SQLXML 4.0 程式設計概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
- SQLXML
ms.assetid: 5a11cda2-b8a3-4453-848f-641afdaa7024
author: rothja
ms.author: jroth
ms.openlocfilehash: 90a383d2a12e073f262d24a94abe1b094509713c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597707"
---
# <a name="sqlxml-40-programming-concepts"></a><span data-ttu-id="71a8f-102">SQLXML 4.0 程式設計概念</span><span class="sxs-lookup"><span data-stu-id="71a8f-102">SQLXML 4.0 Programming Concepts</span></span>
  <span data-ttu-id="71a8f-103">SQLXML 3.0 會以 Web 發行的形式提供了額外的用戶端 XML 功能以及現有功能的增強功能，例如註解 XSD 結構描述、XML 大量載入、Web 服務 (SOAP) 支援和 Updategram。</span><span class="sxs-lookup"><span data-stu-id="71a8f-103">SQLXML 3.0 was offered as a Web release to provide additional client-side XML functionality and enhancements to existing features, such as annotated XSD schemas, XML bulk load, Web services (SOAP) support, and updategrams.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="71a8f-104">導入了 SQLXML 4.0，繼續提供與 SQLXML 3.0 相同的功能，以及配合 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所導入之新功能的其他更新。</span><span class="sxs-lookup"><span data-stu-id="71a8f-104">introduced SQLXML 4.0, which continues to deliver the same functionality as SQLXML 3.0 plus additional updates provided to accommodate new features introduced with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="71a8f-105">本節會提供 SQLXML 4.0 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="71a8f-105">This section provides information about SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="71a8f-106">SQLXML 不會安裝在 SQL Server 中</span><span class="sxs-lookup"><span data-stu-id="71a8f-106">SQLXML Is Not Installed in SQL Server</span></span>](sqlxml-is-not-installed-in-sql-server.md)  
 <span data-ttu-id="71a8f-107">說明如何安裝 SQLXML 4.0。</span><span class="sxs-lookup"><span data-stu-id="71a8f-107">Describes how to install SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="71a8f-108">SQLXML 4.0 SP1 的新功能</span><span class="sxs-lookup"><span data-stu-id="71a8f-108">What's New in SQLXML 4.0 SP1</span></span>](what-s-new-in-sqlxml-4-0-sp1.md)  
 <span data-ttu-id="71a8f-109">說明 SQLXML 4.0 中的更新和增強功能，並提供此文件中的相關主題連結。</span><span class="sxs-lookup"><span data-stu-id="71a8f-109">Describes the updates and enhancements in SQLXML 4.0, and provides links to relevant topics in this documentation.</span></span>  
  
 [<span data-ttu-id="71a8f-110">使用 ADO 執行 SQLXML 4.0 查詢</span><span class="sxs-lookup"><span data-stu-id="71a8f-110">Using ADO to Execute SQLXML 4.0 Queries</span></span>](using-ado-to-execute-sqlxml-4-0-queries.md)  
 <span data-ttu-id="71a8f-111">描述如何使用 ADO 進行 SQLXML 查詢。</span><span class="sxs-lookup"><span data-stu-id="71a8f-111">Describes how to use ADO for SQLXML queries.</span></span> <span data-ttu-id="71a8f-112">ADO 在 SQLXML 4.0 中的功能遠比在舊版中強大。</span><span class="sxs-lookup"><span data-stu-id="71a8f-112">ADO is more prominent in SQLXML 4.0 than in previous versions.</span></span>  
  
 [<span data-ttu-id="71a8f-113">xml 資料類型在 SQLXML 4.0 中的支援</span><span class="sxs-lookup"><span data-stu-id="71a8f-113">xml Data Type Support in SQLXML 4.0</span></span>](xml-data-type-support-in-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-114">描述已針對 SQLXML 4.0 新增的 xml 資料類型支援。</span><span class="sxs-lookup"><span data-stu-id="71a8f-114">Describes the support for the xml data type that has been added for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="71a8f-115">執行 SQLXML 範例的需求</span><span class="sxs-lookup"><span data-stu-id="71a8f-115">Requirements for Running SQLXML Examples</span></span>](requirements-for-running-sqlxml-examples.md)  
 <span data-ttu-id="71a8f-116">描述從所提供的 SQLXML 範例建立工作範例的需求。</span><span class="sxs-lookup"><span data-stu-id="71a8f-116">Describe the requirements for creating working samples from the SQLXML examples provided.</span></span>  
  
 [<span data-ttu-id="71a8f-117">用戶端和伺服器端格式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a8f-117">Client-side and Server-side Formatting &#40;SQLXML 4.0&#41;</span></span>](formatting/client-side-and-server-side-formatting-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-118">提供用戶端和伺服器端之格式設定的相關資訊和比較，包括用來建構 XML 文件的 FOR XML 命令。</span><span class="sxs-lookup"><span data-stu-id="71a8f-118">Provides information about and comparisons of client-side and server-side formatting, including the FOR XML command for constructing XML documents.</span></span>  
  
 [<span data-ttu-id="71a8f-119">SQLXML 4.0 中的註解式 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="71a8f-119">Annotated XSD Schemas in SQLXML 4.0</span></span>](annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-120">提供在 SQLXML 4.0 中使用註解 XSD 結構描述的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="71a8f-120">Provides information about using annotated XSD schemas in SQLXML 4.0.</span></span> <span data-ttu-id="71a8f-121">也提供用於舊版應用程式的註解 XDR 結構描述的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="71a8f-121">Also provides information about annotated XDR schemas for use in legacy applications.</span></span>  
  
 [<span data-ttu-id="71a8f-122">在 SQLXML 4.0 中使用 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="71a8f-122">Using XPath Queries in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-123">描述如何使用 XPath 語言的子集來查詢由註解 XSD 結構描述所建立的 XML 檢視，並且提供範例。</span><span class="sxs-lookup"><span data-stu-id="71a8f-123">Describes how to use a subset of the XPath language to query the XML views created by an annotated XSD schema, and provides examples.</span></span>  
  
 [<span data-ttu-id="71a8f-124">使用 Updategram 來修改 SQLXML 4.0 中的資料</span><span class="sxs-lookup"><span data-stu-id="71a8f-124">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-125">提供有關 Updategram 的相關資訊，Updategram 會針對 XSD (或 XDR) 註解結構描述所提供的 XML 檢視進行作業，以修改資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="71a8f-125">Provides information about updategrams, which modify data in a database by working against the XML views provided by XSD (or XDR) annotated schemas.</span></span>  
  
 [<span data-ttu-id="71a8f-126">執行 XML 資料的大量載入 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a8f-126">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-127">描述如何在 SQLXML 4.0 中大量載入 XML。</span><span class="sxs-lookup"><span data-stu-id="71a8f-127">Describes how to bulk load XML in SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="71a8f-128">SQLXML 4.0 Data Access Components</span><span class="sxs-lookup"><span data-stu-id="71a8f-128">SQLXML 4.0 Data Access Components</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/sqlxml-4-0-data-access-components-sqlxmloledb-provider.md)  
 <span data-ttu-id="71a8f-129">提供 SQLXMLOLEDB 提供者的說明以及其他 SQLXML 4.0 資料存取元件的連結。</span><span class="sxs-lookup"><span data-stu-id="71a8f-129">Documents the SQLXMLOLEDB Provider and provides links to other SQLXML 4.0 data access components.</span></span>  
  
 [<span data-ttu-id="71a8f-130">SQLXML 4.0 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="71a8f-130">SQLXML 4.0 .NET Framework Support</span></span>](../../database-engine/dev-guide/sqlxml-4-0-net-framework-support.md)  
 <span data-ttu-id="71a8f-131">描述 .NET Framework 的 SQLXML 4.0 支援。</span><span class="sxs-lookup"><span data-stu-id="71a8f-131">Describes the SQLXML 4.0 support for the .NET Framework.</span></span>  
  
 [<span data-ttu-id="71a8f-132">快取範本、XSL 和架構 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="71a8f-132">Caching Templates, XSL, and Schemas &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/caching-templates-xsl-and-schemas-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-133">描述 SQLXML 為增強效能而提供的快取功能。</span><span class="sxs-lookup"><span data-stu-id="71a8f-133">Describes the caching functionality provided in SQLXML to improve performance.</span></span>  
  
 [<span data-ttu-id="71a8f-134">SQLXML 4.0 安全性考量</span><span class="sxs-lookup"><span data-stu-id="71a8f-134">SQLXML 4.0 Security Considerations</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/sqlxml-4-0-security-considerations.md)  
 <span data-ttu-id="71a8f-135">討論與 SQLXML 4.0 相關的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="71a8f-135">Discusses security issues relevant to SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="71a8f-136">SQLXML 4.0 的指導方針和限制</span><span class="sxs-lookup"><span data-stu-id="71a8f-136">Guidelines and Limitations of SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/guidelines-and-limitations-of-sqlxml-4-0.md)  
 <span data-ttu-id="71a8f-137">列出在使用 SQLXML 4.0 時要注意的問題。</span><span class="sxs-lookup"><span data-stu-id="71a8f-137">Lists issues to remember when working with SQLXML 4.0.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a8f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71a8f-138">See Also</span></span>  
 [<span data-ttu-id="71a8f-139">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="71a8f-139">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
