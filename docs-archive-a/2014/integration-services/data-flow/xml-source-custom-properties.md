---
title: XML 來源自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e152b23b4f59ca46cb8272ca677dc1161b3efec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599073"
---
# <a name="xml-source-custom-properties"></a><span data-ttu-id="3bf3f-102">XML 來源自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3bf3f-102">XML Source Custom Properties</span></span>
  <span data-ttu-id="3bf3f-103">XML 來源同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-103">The XML source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="3bf3f-104">下表描述的是 XML 來源的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-104">The following table describes the custom properties of the XML source.</span></span> <span data-ttu-id="3bf3f-105">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-105">All properties are read/write.</span></span>  
  
|<span data-ttu-id="3bf3f-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="3bf3f-106">Property name</span></span>|<span data-ttu-id="3bf3f-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="3bf3f-107">Data Type</span></span>|<span data-ttu-id="3bf3f-108">描述</span><span class="sxs-lookup"><span data-stu-id="3bf3f-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="3bf3f-109">AccessMode</span><span class="sxs-lookup"><span data-stu-id="3bf3f-109">AccessMode</span></span>|<span data-ttu-id="3bf3f-110">整數</span><span class="sxs-lookup"><span data-stu-id="3bf3f-110">Integer</span></span>|<span data-ttu-id="3bf3f-111">用來存取 XML 資料的模式。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-111">The mode used to access the XML data.</span></span>|  
|<span data-ttu-id="3bf3f-112">UseInlineSchema</span><span class="sxs-lookup"><span data-stu-id="3bf3f-112">UseInlineSchema</span></span>|<span data-ttu-id="3bf3f-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="3bf3f-113">Boolean</span></span>|<span data-ttu-id="3bf3f-114">一個值，指出是否要使用 XML 來源中的內嵌結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-114">A value that indicates whether to use an inline schema definition within the XML source.</span></span> <span data-ttu-id="3bf3f-115">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-115">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="3bf3f-116">XMLData</span><span class="sxs-lookup"><span data-stu-id="3bf3f-116">XMLData</span></span>|<span data-ttu-id="3bf3f-117">String</span><span class="sxs-lookup"><span data-stu-id="3bf3f-117">String</span></span>|<span data-ttu-id="3bf3f-118">要從中擷取 XML 資料的檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-118">The file or variables from which to retrieve the XML data.</span></span><br /><br /> <span data-ttu-id="3bf3f-119">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-119">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="3bf3f-120">XMLSchemaDefinition</span><span class="sxs-lookup"><span data-stu-id="3bf3f-120">XMLSchemaDefinition</span></span>|<span data-ttu-id="3bf3f-121">String</span><span class="sxs-lookup"><span data-stu-id="3bf3f-121">String</span></span>|<span data-ttu-id="3bf3f-122">結構描述定義檔 (.xsd) 的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-122">The path and file name of the schema definition file (.xsd).</span></span><br /><br /> <span data-ttu-id="3bf3f-123">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-123">The value of this property can be specified by using a property expression.</span></span>|  
  
 <span data-ttu-id="3bf3f-124">下表描述的是 XML 來源之輸出的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-124">The following table describes the custom properties of the output of the XML source.</span></span> <span data-ttu-id="3bf3f-125">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-125">All properties are read/write.</span></span>  
  
|<span data-ttu-id="3bf3f-126">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="3bf3f-126">Property name</span></span>|<span data-ttu-id="3bf3f-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="3bf3f-127">Data Type</span></span>|<span data-ttu-id="3bf3f-128">描述</span><span class="sxs-lookup"><span data-stu-id="3bf3f-128">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="3bf3f-129">RowsetID</span><span class="sxs-lookup"><span data-stu-id="3bf3f-129">RowsetID</span></span>|<span data-ttu-id="3bf3f-130">String</span><span class="sxs-lookup"><span data-stu-id="3bf3f-130">String</span></span>|<span data-ttu-id="3bf3f-131">一個值，可識別與輸出相關聯的資料列集。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-131">A value that identifies the rowset associated with the output.</span></span>|  
  
 <span data-ttu-id="3bf3f-132">XML 來源的輸出資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-132">The output columns of the XML source have no custom properties.</span></span>  
  
 <span data-ttu-id="3bf3f-133">如需詳細資訊，請參閱 [XML 來源](xml-source.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf3f-133">For more information, see [XML Source](xml-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf3f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bf3f-134">See Also</span></span>  
 [<span data-ttu-id="3bf3f-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3bf3f-135">Common Properties</span></span>](../common-properties.md)  
  
  
