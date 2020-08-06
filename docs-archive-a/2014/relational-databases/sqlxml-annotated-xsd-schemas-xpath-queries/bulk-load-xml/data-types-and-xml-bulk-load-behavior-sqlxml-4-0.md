---
title: 資料類型與 XML 大量載入行為 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b03423f3bb88166d0d9ce5b0df450d4455e7ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597752"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a><span data-ttu-id="d24c3-102">資料類型與 XML 大量載入行為 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d24c3-102">Data Types and XML Bulk Load Behavior (SQLXML 4.0)</span></span>
  <span data-ttu-id="d24c3-103">除了在下列情況下之外，在對應結構描述 (XSD 或 XDR 類型和 `sql:datatype`) 中指定的資料類型通常會遭到忽略：</span><span class="sxs-lookup"><span data-stu-id="d24c3-103">The data types that are specified in the mapping schema (XSD or XDR type and `sql:datatype`) are generally ignored, except in the following cases:</span></span>  
  
 <span data-ttu-id="d24c3-104">在 XSD 中：</span><span class="sxs-lookup"><span data-stu-id="d24c3-104">In XSD:</span></span>  
  
-   <span data-ttu-id="d24c3-105">如果類型為 `dateTime` 或 `time`，您必須指定 `sql:datatype`，因為 XML 大量載入會在將資料傳送到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前，先執行資料轉換。</span><span class="sxs-lookup"><span data-stu-id="d24c3-105">If the type is `dateTime` or `time`, you must specify the `sql:datatype` because XML Bulk Load performs data conversion before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d24c3-106">當您要大量載入中類型的資料行 `uniqueidentifier` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，而且 XSD 值是包含大括弧 ( {和} ) 的 GUID 時，您必須指定**sql： datatype = "uniqueidentifier"** ，以在將值插入資料行之前移除大括弧。</span><span class="sxs-lookup"><span data-stu-id="d24c3-106">When you are bulk loading into a column of `uniqueidentifier` type in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and the XSD value is a GUID that includes braces ({ and }), you must specify **sql:datatype="uniqueidentifier"** to remove the braces before the value is inserted into the column.</span></span> <span data-ttu-id="d24c3-107">如果未指定 `sql:datatype`，值會跟著大括號傳送出去，而且插入動作會失敗。</span><span class="sxs-lookup"><span data-stu-id="d24c3-107">If `sql:datatype` is not specified, the value is sent with the braces and the insert fails.</span></span>  
  
 <span data-ttu-id="d24c3-108">如需的詳細資訊 `sql:datatype` ，請參閱[資料類型強制型轉和 sql： datatype 注釋 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d24c3-108">For more information about `sql:datatype`, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d24c3-109">在 XDR 中：</span><span class="sxs-lookup"><span data-stu-id="d24c3-109">In XDR:</span></span>  
  
-   <span data-ttu-id="d24c3-110">如果 `dt:type` 為 `datetime`、`time`、`dateTime.tz` 或 `time.tz`，您必須同時指定 `dt:type` 和 `sql:datatype` 資料類型，因為 XML 大量載入會在將資料傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前，先執行資料轉換。</span><span class="sxs-lookup"><span data-stu-id="d24c3-110">If the `dt:type` is `datetime`, `time`, `dateTime.tz`, or `time.tz`, you must specify both the `dt:type` and `sql:datatype` data types because XML Bulk Load performs data conversion before it sends the data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d24c3-111">如果您的 XML 資料類型為 `uuid` ，則 `sql:datatype` 必須指定;**dt： type = "uuid"** 也是必要的，除非資料是字串資料。</span><span class="sxs-lookup"><span data-stu-id="d24c3-111">If your XML data is of type `uuid`, `sql:datatype` must be specified; **dt:type="uuid"** is also required, unless the data is string data.</span></span> <span data-ttu-id="d24c3-112">如果您沒有指定 `dt:uuid`，XML 大量載入會接受包含大括號的字串 (並在需要時移除)。</span><span class="sxs-lookup"><span data-stu-id="d24c3-112">If you do not specify `dt:uuid`, XML Bulk Load accepts strings with braces (and removes them if needed).</span></span>  
  
-   <span data-ttu-id="d24c3-113">如果 XML 資料是 `bin.base64` 或 `bin.hex`，您必須使用 `dt:type` 指定 XML 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d24c3-113">If the XML data is `bin.base64` or `bin.hex`, you must specify the XML data type with `dt:type`.</span></span> <span data-ttu-id="d24c3-114">接著，XML 大量載入會將資料載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，做為資料的十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="d24c3-114">XML Bulk Load then loads the data into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a hexadecimal representation of the data.</span></span>  
  
  
