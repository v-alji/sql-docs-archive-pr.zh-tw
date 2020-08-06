---
title: " (SQLXML 4.0) 的注釋轉譯 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: rothja
ms.author: jroth
ms.openlocfilehash: c31d56f7dd577b4b5a5b582eb0e3b1db312109a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597756"
---
# <a name="annotation-interpretation-sqlxml-40"></a><span data-ttu-id="34ff9-102">註解的解譯 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="34ff9-102">Annotation Interpretation (SQLXML 4.0)</span></span>
  <span data-ttu-id="34ff9-103">本章節的主題描述 XML 大量載入要如何解譯 XSD 結構描述中的註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-103">The topics in this section describe how XML Bulk Load interprets annotations in the XSD schema.</span></span> <span data-ttu-id="34ff9-104">這裡所述的行為也適用於 XDR 結構描述中的註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-104">The behavior described here also applies to the annotations in the XDR schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34ff9-105">這些主題的資訊只會描述 XML 大量載入在處理時所使用的註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-105">The information in these topics describes only the annotations used by XML Bulk Load in its processing.</span></span> <span data-ttu-id="34ff9-106">如需 SQLXML 4.0 支援之 XSD 架構的批註完整清單，請參閱[在 Xsd 架構中使用批註 &#40;sqlxml 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="34ff9-106">For a complete list of annotations for the XSD schema that are supported by SQLXML 4.0, see [Using Annotations in XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="34ff9-107">如需 XDR 架構支援的注釋清單，請參閱[SQLXML 4.0&#41;中 &#40;已被取代的批註式 XDR 架構](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="34ff9-107">For a list of supported annotations for XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34ff9-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="34ff9-108">In This Section</span></span>  
 [<span data-ttu-id="34ff9-109">sql：關聯性和索引鍵排序規則 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34ff9-109">sql:relationship and the Key Ordering Rule &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 <span data-ttu-id="34ff9-110">描述如何在 XML 大量載入內解譯 `sql:relationship` 註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-110">Describes how the `sql:relationship` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34ff9-111">sql：對應 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34ff9-111">sql:mapped &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-mapped.md)  
 <span data-ttu-id="34ff9-112">描述如何在 XML 大量載入內解譯 `sql:mapped` 註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-112">Describes how the `sql:mapped` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34ff9-113">sql： limit-field 和 sql： limit-value &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34ff9-113">sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="34ff9-114">描述如何在 XML 大量載入內解譯 `sql:limit-field` 和 `sql:limit-value` 註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-114">Describes how the `sql:limit-field` and `sql:limit-value` annotations are interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34ff9-115">sql：溢位欄位 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34ff9-115">sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="34ff9-116">描述如何在 XML 大量載入內解譯 `sql:overflow` 註解。</span><span class="sxs-lookup"><span data-stu-id="34ff9-116">Describes how the `sql:overflow` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34ff9-117">&#40;SQLXML 4.0&#41;的其他批註</span><span class="sxs-lookup"><span data-stu-id="34ff9-117">Other Annotations &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-other-annotations.md)  
 <span data-ttu-id="34ff9-118">描述如何在 XML 大量載入內解譯下列註解：`sql:id-prefix`、`sql:use-cdata`、`sql:url-encode`、`sql:is-mapping-schema`、`sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="34ff9-118">Describes how the following annotations are interpreted in XML Bulk Load: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.</span></span>  
  
  
