---
title: XML 資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML [SQL Server]
- XML [SQL Server], about XML
ms.assetid: 6a1793c9-9856-485c-aac5-88fda62f61a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 48ddec1de8492c86aecfd80ea960c4a01673c24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592551"
---
# <a name="xml-data-sql-server"></a><span data-ttu-id="83648-102">XML 資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="83648-102">XML Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="83648-103">提供了功能強大的平台，可針對半結構化的資料管理來開發豐富的應用程式。</span><span class="sxs-lookup"><span data-stu-id="83648-103">provides a powerful platform for developing rich applications for semi-structured data management.</span></span> <span data-ttu-id="83648-104">支援將 XML 整合至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的所有元件，並包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="83648-104">Support for XML is integrated into all the components in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and includes the following:</span></span>  
  
-   <span data-ttu-id="83648-105">`xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="83648-105">The `xml` data type.</span></span> <span data-ttu-id="83648-106">XML 值可用原生方式儲存在 `xml` 資料類型資料行中，依照 XML 結構描述的集合來設定類型，或維持不具類型。</span><span class="sxs-lookup"><span data-stu-id="83648-106">XML values can be stored natively in an `xml` data type column that can be typed according to a collection of XML schemas, or left untyped.</span></span> <span data-ttu-id="83648-107">您可以編製 XML 資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="83648-107">You can index the XML column.</span></span>  
  
-   <span data-ttu-id="83648-108">可以針對儲存在 `xml` 類型之資料行與變數中的 XML 資料，指定 XQuery 查詢。</span><span class="sxs-lookup"><span data-stu-id="83648-108">The ability to specify an XQuery query against XML data stored in columns and variables of the `xml` type.</span></span>  
  
-   <span data-ttu-id="83648-109">OPENROWSET 的增強功能允許大量載入 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="83648-109">Enhancements to OPENROWSET to allow bulk loading of XML data.</span></span>  
  
-   <span data-ttu-id="83648-110">FOR XML 子句，用來擷取 XML 格式的關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="83648-110">The FOR XML clause, to retrieve relational data in XML format.</span></span>  
  
-   <span data-ttu-id="83648-111">OPENXML 函數，用來擷取關聯式格式的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="83648-111">The OPENXML function, to retrieve XML data in relational format.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83648-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="83648-112">In This Section</span></span>  
 [<span data-ttu-id="83648-113">XML 資料類型和資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-113">XML Data Type and Columns &#40;SQL Server&#41;</span></span>](xml-data-type-and-columns-sql-server.md)  
 [<span data-ttu-id="83648-114">XML 索引 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-114">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
 [<span data-ttu-id="83648-115">XML 結構描述集合 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-115">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
 [<span data-ttu-id="83648-116">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-116">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
 [<span data-ttu-id="83648-117">OPENXML &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-117">OPENXML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openxml-transact-sql)  
  
## <a name="related-content"></a><span data-ttu-id="83648-118">相關內容</span><span class="sxs-lookup"><span data-stu-id="83648-118">Related Content</span></span>  
 [<span data-ttu-id="83648-119">大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-119">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
 [<span data-ttu-id="83648-120">XQuery 語言參考 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="83648-120">XQuery Language Reference &#40;SQL Server&#41;</span></span>](/sql/xquery/xquery-language-reference-sql-server)  
  
