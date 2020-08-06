---
title: 搭配 FOR XML 使用 PATH 模式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: rothja
ms.author: jroth
ms.openlocfilehash: ce0cf811f1e610d14a94993b54c51ea079f613e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596560"
---
# <a name="use-path-mode-with-for-xml"></a><span data-ttu-id="87a2f-102">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="87a2f-102">Use PATH Mode with FOR XML</span></span>
  <span data-ttu-id="87a2f-103">如 [使用 FOR XML 建構 XML](for-xml-sql-server.md)所述，PATH 模式提供比較簡單的方式來混合元素與屬性。</span><span class="sxs-lookup"><span data-stu-id="87a2f-103">As described in [Constructing XML Using FOR XML](for-xml-sql-server.md), the PATH mode provides a simpler way to mix elements and attributes.</span></span> <span data-ttu-id="87a2f-104">PATH 模式也是導入其他巢狀以代表複雜屬性的較簡單方式。</span><span class="sxs-lookup"><span data-stu-id="87a2f-104">PATH mode is also a simpler way to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="87a2f-105">您可以使用 FOR XML EXPLICIT 模式查詢來建構從資料列集而來的這類 XML，但是 PATH 模式對於可能會比較繁雜的 EXPLICIT 模式查詢提供較簡單的替代方案。</span><span class="sxs-lookup"><span data-stu-id="87a2f-105">You can use FOR XML EXPLICIT mode queries to construct such XML from a rowset, but the PATH mode provides a simpler alternative to the potentially cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="87a2f-106">PATH 模式還可撰寫巢狀 FOR XML 查詢及 TYPE 指示詞，以傳回 **xml** 類型執行個體，這將可讓您撰寫較不複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="87a2f-106">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span>  
  
 <span data-ttu-id="87a2f-107">在 PATH 模式中，資料行名稱或資料行別名是被視為 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="87a2f-107">In PATH mode, column names or column aliases are treated as XPath expressions.</span></span> <span data-ttu-id="87a2f-108">這些運算式指出值如何對應至 XML。</span><span class="sxs-lookup"><span data-stu-id="87a2f-108">These expressions indicate how the values are being mapped to XML.</span></span> <span data-ttu-id="87a2f-109">每個 XPath 運算式都是提供項目類型的相對 XPath，這些項目類型包括屬性、元素、純量值、將會產生與資料列元素相對的節點名稱與階層。</span><span class="sxs-lookup"><span data-stu-id="87a2f-109">Each XPath expression is a relative XPath that provides the item type., such as the attribute, element, and scalar value, and the name and hierarchy of the node that will be generated relative to the row element.</span></span>  
  
 <span data-ttu-id="87a2f-110">本章節描述各種條件下資料列集中的對應資料行，並提供範例。</span><span class="sxs-lookup"><span data-stu-id="87a2f-110">This section describes mapping columns in a rowset under various conditions, and provides examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87a2f-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="87a2f-111">In This Section</span></span>  
  
-   [<span data-ttu-id="87a2f-112">沒有名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="87a2f-112">Columns without a Name</span></span>](columns-without-a-name.md)  
  
-   [<span data-ttu-id="87a2f-113">有名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="87a2f-113">Columns with a Name</span></span>](columns-with-a-name.md)  
  
-   [<span data-ttu-id="87a2f-114">以萬用字元 (\*) 指定名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="87a2f-114">Columns with a Name Specified as a Wildcard Character</span></span>](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [<span data-ttu-id="87a2f-115">具有 XPath 節點測試名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="87a2f-115">Columns with the Name of an XPath Node Test</span></span>](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [<span data-ttu-id="87a2f-116">以 data&#40;&#41; 指定路徑的資料行名稱</span><span class="sxs-lookup"><span data-stu-id="87a2f-116">Column Names with the Path Specified as data&#40;&#41;</span></span>](column-names-with-the-path-specified-as-data.md)  
  
-   [<span data-ttu-id="87a2f-117">預設包含 NULL 值的資料行</span><span class="sxs-lookup"><span data-stu-id="87a2f-117">Columns that Contain a Null Value By Default</span></span>](columns-that-contain-a-null-value-by-default.md)  
  
-   [<span data-ttu-id="87a2f-118">PATH 模式中的命名空間支援</span><span class="sxs-lookup"><span data-stu-id="87a2f-118">Namespace Support in PATH Mode</span></span>](namespace-support-in-path-mode.md)  
  
-   [<span data-ttu-id="87a2f-119">範例：使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="87a2f-119">Examples: Using PATH Mode</span></span>](examples-using-path-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="87a2f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87a2f-120">See Also</span></span>  
 <span data-ttu-id="87a2f-121">[使用 WITH XMLNAMESPACES 將命名空間加入至查詢](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="87a2f-121">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="87a2f-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87a2f-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="87a2f-123">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87a2f-123">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
