---
title: 使用 SQLXML Managed 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXML Managed Classes, sample applications
- examples [SQLXML], managed classes
- Managed Classes [SQLXML], samples
ms.assetid: 3f021290-00ee-44e1-af4b-33d3ba8c6302
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 634a0e4110b13931201edd026ee95028cb94e859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701677"
---
# <a name="using-the-sqlxml-managed-classes"></a><span data-ttu-id="d1253-102">使用 SQLXML Managed 類別</span><span class="sxs-lookup"><span data-stu-id="d1253-102">Using the SQLXML Managed Classes</span></span>
  <span data-ttu-id="d1253-103">本節提供範例應用程式，示範如何使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="d1253-103">This section provides sample applications that demonstrate how to use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML Managed Classes.</span></span>  
  
 <span data-ttu-id="d1253-104">如需有關在 .NET Framework 記憶體取和修改資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] ，以及如何使用 diffgram 來更新資料表中資料的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱在[.NET 環境中存取 SQLXML 功能](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="d1253-104">For information about accessing and modifying data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] within the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, and about using DiffGrams to update data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, see [Accessing SQLXML Functionality in the .NET Environment](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1253-105">您也可以撰寫 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 應用程式，藉由使用 XML 大量載入來大量載入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d1253-105">You can also write [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio applications to bulk load XML documents by using XML Bulk Load.</span></span> <span data-ttu-id="d1253-106">如需詳細資訊，請參閱[執行 XML 資料的大量載入 &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d1253-106">For more information, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span> <span data-ttu-id="d1253-107">您必須在應用程式中加入 XML 大量載入 DLL (Xblkld4.dll) 的參考。</span><span class="sxs-lookup"><span data-stu-id="d1253-107">You must add a reference to the XML Bulk Load DLL (Xblkld4.dll) in your application.</span></span> <span data-ttu-id="d1253-108">這是 COM DLL，Visual Studio .NET 會自動為其建立包裝函數程式庫。</span><span class="sxs-lookup"><span data-stu-id="d1253-108">This is a COM DLL for which Visual Studio .NET automatically creates the wrapper library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1253-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="d1253-109">In This Section</span></span>  
 [<span data-ttu-id="d1253-110">&#40;SQLXML Managed 類別執行 SQL 查詢&#41;</span><span class="sxs-lookup"><span data-stu-id="d1253-110">Executing SQL Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
  [<span data-ttu-id="d1253-111">使用 ExecuteXMLReader 方法執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="d1253-111">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [<span data-ttu-id="d1253-112">在用戶端上處理 XML &#40;SQLXML Managed 類別&#41;</span><span class="sxs-lookup"><span data-stu-id="d1253-112">Processing XML on the Client Side &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [<span data-ttu-id="d1253-113">&#40;SQLXML Managed 類別執行 XPath 查詢&#41;</span><span class="sxs-lookup"><span data-stu-id="d1253-113">Executing XPath Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [<span data-ttu-id="d1253-114">使用 &#40;SQLXML Managed 類別的命名空間來執行 XPath 查詢&#41;</span><span class="sxs-lookup"><span data-stu-id="d1253-114">Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [<span data-ttu-id="d1253-115">使用 CommandText 屬性執行範本檔案</span><span class="sxs-lookup"><span data-stu-id="d1253-115">Executing Template Files by Using the CommandText Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [<span data-ttu-id="d1253-116">利用 CommandStream 屬性執行範本檔案</span><span class="sxs-lookup"><span data-stu-id="d1253-116">Executing Template Files by Using the CommandStream Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [<span data-ttu-id="d1253-117">&#40;SQLXML Managed 類別套用 XSL 轉換&#41;</span><span class="sxs-lookup"><span data-stu-id="d1253-117">Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  
