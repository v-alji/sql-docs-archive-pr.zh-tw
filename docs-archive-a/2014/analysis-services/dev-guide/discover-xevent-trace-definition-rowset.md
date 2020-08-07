---
title: DISCOVER_XEVENT_TRACE_DEFINITION 資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
ms.openlocfilehash: bedd6ec66a188738ac9a522b4802b3b431e82f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703398"
---
# <a name="discover_xevent_trace_definition-rowset"></a><span data-ttu-id="4fbb6-102">DISCOVER_XEVENT_TRACE_DEFINITION 資料列集</span><span class="sxs-lookup"><span data-stu-id="4fbb6-102">DISCOVER_XEVENT_TRACE_DEFINITION Rowset</span></span>
  <span data-ttu-id="4fbb6-103">提供有關伺服器上目前使用中 XEvent 追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-103">Provides information about XEvent traces that are currently active on the server.</span></span>  
  
 <span data-ttu-id="4fbb6-104">**適用于：** 表格式模型、多維度模型</span><span class="sxs-lookup"><span data-stu-id="4fbb6-104">**Applies to:** tabular models, multidimensional models</span></span>  
  
## <a name="rowset-columns"></a><span data-ttu-id="4fbb6-105">資料列集資料行</span><span class="sxs-lookup"><span data-stu-id="4fbb6-105">Rowset Columns</span></span>  
 <span data-ttu-id="4fbb6-106">`DISCOVER_XEVENT_TRACE_DEFINITION` 資料列集包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-106">The `DISCOVER_XEVENT_TRACE_DEFINITION` rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="4fbb6-107">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="4fbb6-107">Column name</span></span>|<span data-ttu-id="4fbb6-108">類型指標</span><span class="sxs-lookup"><span data-stu-id="4fbb6-108">Type indicator</span></span>|<span data-ttu-id="4fbb6-109">長度</span><span class="sxs-lookup"><span data-stu-id="4fbb6-109">Length</span></span>|<span data-ttu-id="4fbb6-110">描述</span><span class="sxs-lookup"><span data-stu-id="4fbb6-110">Description</span></span>|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||<span data-ttu-id="4fbb6-111">XEvent 追蹤的 XML 定義。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-111">The XML definition of the XEvent trace.</span></span>|  
  
 <span data-ttu-id="4fbb6-112">這個結構描述資料列集並未排序。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-112">This schema rowset is not sorted.</span></span>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a><span data-ttu-id="4fbb6-113">使用 ADOMD.NET 傳回資料列集</span><span class="sxs-lookup"><span data-stu-id="4fbb6-113">Using ADOMD.NET to return the rowset</span></span>  
 <span data-ttu-id="4fbb6-114">使用 ADOMD.NET 和結構描述資料列集來擷取中繼資料時，您可以使用 GUID 或字串，在 GetSchemaDataSet 方法中參考結構描述資料列集物件。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-114">When using ADOMD.NET and the schema rowset to retrieve metadata, you can use either the GUID or string to reference a schema rowset object in the GetSchemaDataSet method.</span></span> <span data-ttu-id="4fbb6-115">如需詳細資訊，請參閱 [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets)。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-115">For more information, see [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets).</span></span>  
  
 <span data-ttu-id="4fbb6-116">下表將提供可識別此資料列集的 GUID 和字串值。</span><span class="sxs-lookup"><span data-stu-id="4fbb6-116">The following table provides the GUID and string values that identify this rowset.</span></span>  
  
|<span data-ttu-id="4fbb6-117">引數</span><span class="sxs-lookup"><span data-stu-id="4fbb6-117">Argument</span></span>|<span data-ttu-id="4fbb6-118">值</span><span class="sxs-lookup"><span data-stu-id="4fbb6-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="4fbb6-119">GUID</span><span class="sxs-lookup"><span data-stu-id="4fbb6-119">GUID</span></span>|<span data-ttu-id="4fbb6-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span><span class="sxs-lookup"><span data-stu-id="4fbb6-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span></span>|  
|<span data-ttu-id="4fbb6-121">String</span><span class="sxs-lookup"><span data-stu-id="4fbb6-121">String</span></span>|<span data-ttu-id="4fbb6-122">DISCOVER_XEVENT_TRACE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="4fbb6-122">DISCOVER_XEVENT_TRACE_DEFINITION</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fbb6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fbb6-123">See Also</span></span>  
 <span data-ttu-id="4fbb6-124">[XML for Analysis 架構資料列集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span><span class="sxs-lookup"><span data-stu-id="4fbb6-124">[XML for Analysis Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span></span>  
 <span data-ttu-id="4fbb6-125">[使用 SQL Server 擴充事件 &#40;XEvents&#41; 監視 Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="4fbb6-125">[Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span></span>  
 [<span data-ttu-id="4fbb6-126">使用動態管理檢視 &#40;DMV&#41; 監視 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="4fbb6-126">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
