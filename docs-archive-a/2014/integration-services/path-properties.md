---
title: 路徑屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592096"
---
# <a name="path-properties"></a><span data-ttu-id="9eb83-102">路徑屬性</span><span class="sxs-lookup"><span data-stu-id="9eb83-102">Path Properties</span></span>
  <span data-ttu-id="9eb83-103">物件模型中的資料流程物件 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 具有元件層級、輸入和輸出，以及輸入資料行和輸出資料行的通用屬性和自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="9eb83-103">The data flow objects in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model have common properties and custom properties at the level of the component, inputs and outputs, and input columns and output columns.</span></span> <span data-ttu-id="9eb83-104">許多屬性都有唯讀的值，這些值是在執行階段由資料流程引擎所指派。</span><span class="sxs-lookup"><span data-stu-id="9eb83-104">Many properties have read-only values that are assigned at run time by the data flow engine.</span></span>  
  
 <span data-ttu-id="9eb83-105">本主題將列出及描述連接資料流程物件之路徑的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="9eb83-105">This topic lists and describes the custom properties of the paths that connect data flow objects.</span></span>  
  
## <a name="path-properties"></a><span data-ttu-id="9eb83-106">路徑屬性</span><span class="sxs-lookup"><span data-stu-id="9eb83-106">Path Properties</span></span>  
 <span data-ttu-id="9eb83-107">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件模型中，連接資料流程中元件的路徑會實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 介面。</span><span class="sxs-lookup"><span data-stu-id="9eb83-107">In the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model, a path that connects components in the data flow implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> interface.</span></span>  
  
 <span data-ttu-id="9eb83-108">下表將描述資料流程中路徑的可設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9eb83-108">The following table describes the configurable properties of the paths in a data flow.</span></span> <span data-ttu-id="9eb83-109">資料流程引擎也會將值指派給這裡未列出的其他唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="9eb83-109">The data flow engine also assigns values to additional read-only properties that are not listed here.</span></span>  
  
|<span data-ttu-id="9eb83-110">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="9eb83-110">Property name</span></span>|<span data-ttu-id="9eb83-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="9eb83-111">Data Type</span></span>|<span data-ttu-id="9eb83-112">描述</span><span class="sxs-lookup"><span data-stu-id="9eb83-112">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="9eb83-113">PathAnnotation</span><span class="sxs-lookup"><span data-stu-id="9eb83-113">PathAnnotation</span></span>|<span data-ttu-id="9eb83-114">整數 (列舉)</span><span class="sxs-lookup"><span data-stu-id="9eb83-114">Integer (enumeration)</span></span>|<span data-ttu-id="9eb83-115">指出設計師介面上是否應該與路徑一起顯示註解的值。</span><span class="sxs-lookup"><span data-stu-id="9eb83-115">A value that indicates whether an annotation should be displayed with the path on the designer surface.</span></span> <span data-ttu-id="9eb83-116">可能的值為 `AsNeeded`、`SourceName`、`PathName` 和 `Never`。</span><span class="sxs-lookup"><span data-stu-id="9eb83-116">The possible values are `AsNeeded`, `SourceName`, `PathName`, and `Never`.</span></span> <span data-ttu-id="9eb83-117">預設值是 `AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="9eb83-117">The default value is `AsNeeded`.</span></span>|  
|<span data-ttu-id="9eb83-118">DestinationName</span><span class="sxs-lookup"><span data-stu-id="9eb83-118">DestinationName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|<span data-ttu-id="9eb83-119">與路徑相關聯的輸入。</span><span class="sxs-lookup"><span data-stu-id="9eb83-119">The input associated with the path.</span></span>|  
|<span data-ttu-id="9eb83-120">SourceName</span><span class="sxs-lookup"><span data-stu-id="9eb83-120">SourceName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|<span data-ttu-id="9eb83-121">與路徑相關聯的輸出。</span><span class="sxs-lookup"><span data-stu-id="9eb83-121">The output associated with the path.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9eb83-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eb83-122">See Also</span></span>  
 <span data-ttu-id="9eb83-123">[Integration Services 路徑](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="9eb83-123">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="9eb83-124">[通用屬性](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9eb83-124">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="9eb83-125">[轉換自訂屬性](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9eb83-125">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="9eb83-126">可以使用運算式設定的資料流程屬性</span><span class="sxs-lookup"><span data-stu-id="9eb83-126">Data Flow Properties that Can Be Set by Using Expressions</span></span>](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
