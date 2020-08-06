---
title: 使用 sql： identity 和 sql： guid 注釋 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc5c08f158911edb0a1a0638fc4bcee1e05a248c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595906"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a><span data-ttu-id="efb4a-102">使用 sql:identity 和 sql:guid 註解</span><span class="sxs-lookup"><span data-stu-id="efb4a-102">Using the sql:identity and sql:guid Annotations</span></span>
  <span data-ttu-id="efb4a-103">您可以在 `sql:identity` `sql:guid` 對應至中資料庫資料行的任何節點上，于 XSD 架構中指定和批註 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="efb4a-103">You can specify the `sql:identity` and `sql:guid` annotations in an XSD schema on any node that maps to a database column in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efb4a-104">updategram 格式支援 `updg:at-identity` 和 `updg:guid` 屬性，而 DiffGram 格式則不支援。</span><span class="sxs-lookup"><span data-stu-id="efb4a-104">Whereas the updategram format supports the `updg:at-identity` and `updg:guid` attributes, the DiffGram format does not.</span></span> <span data-ttu-id="efb4a-105">`updg:at-identity` 屬性會定義更新 IDENTITY 類型之資料行時的行為。</span><span class="sxs-lookup"><span data-stu-id="efb4a-105">The `updg:at-identity` attribute defines the behavior in updating an IDENTITY-type column.</span></span> <span data-ttu-id="efb4a-106">`updg:guid` 屬性可讓您從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 取得 GUID 值，並將其用在 updategram 中。</span><span class="sxs-lookup"><span data-stu-id="efb4a-106">The `updg:guid` attribute allows you to obtain a GUID value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and use it in the updategram.</span></span> <span data-ttu-id="efb4a-107">如需詳細資訊和工作範例，請參閱[使用 XML Updategram 插入資料 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="efb4a-107">For more information and working samples, see [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="efb4a-108">`sql:identity` 和 `sql:guid` 註解會將此功能擴充到 DiffGrams。</span><span class="sxs-lookup"><span data-stu-id="efb4a-108">The `sql:identity` and `sql:guid` annotations extend this functionality to DiffGrams.</span></span>  
  
 <span data-ttu-id="efb4a-109">當您執行 DiffGram 時，會先將其轉換為 updategram，然後再執行 updategram。</span><span class="sxs-lookup"><span data-stu-id="efb4a-109">When you execute a DiffGram, it is first converted to an updategram, and then the updategram is executed.</span></span> <span data-ttu-id="efb4a-110">透過在 XSD 結構描述中指定 `sql:identity` 和 `sql:guid` 註解，您實際上就在定義 updategram 的行為。</span><span class="sxs-lookup"><span data-stu-id="efb4a-110">By specifying the `sql:identity` and `sql:guid` annotations in the XSD schema, you are in fact defining the behavior of an updategram.</span></span> <span data-ttu-id="efb4a-111">因此，所有註解的描述都在 updategram 的內容中。</span><span class="sxs-lookup"><span data-stu-id="efb4a-111">Therefore, all the annotations are described in the context of an updategram.</span></span> <span data-ttu-id="efb4a-112">註解可以同時用於 DiffGrams 和 updategrams，不過，updategrams 已經提供更強大的方式來處理識別與 GUID 值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-112">The annotations can be used both for DiffGrams and updategrams; however, updategrams already provide a more powerful way of handling identity and GUID values.</span></span>  
  
 <span data-ttu-id="efb4a-113">`sql:identity` 和 `sql:guid` 註解可以在複雜內容元素上定義。</span><span class="sxs-lookup"><span data-stu-id="efb4a-113">The `sql:identity` and `sql:guid` annotations can be defined on a complex content element.</span></span>  
  
## <a name="sqlidentity-annotation"></a><span data-ttu-id="efb4a-114">sql:identity 註解</span><span class="sxs-lookup"><span data-stu-id="efb4a-114">sql:identity Annotation</span></span>  
 <span data-ttu-id="efb4a-115">您可以在對應到 IDENTITY 類型之資料庫資料行的任何節點上，指定 XSD 結構描述的 `sql:identity` 註解。</span><span class="sxs-lookup"><span data-stu-id="efb4a-115">You can specify the `sql:identity` annotation in the XSD schema on any node that maps to an IDENTITY-type database column.</span></span> <span data-ttu-id="efb4a-116">針對此批註指定的值會定義如何使用 updategram 中提供的值來修改資料行，或藉由忽略值來 (更新識別類型資料行，在此情況下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將產生的值用於此資料行) 。</span><span class="sxs-lookup"><span data-stu-id="efb4a-116">The value specified for this annotation defines how the IDENTITY-type column is updated (either by using the value provided in the updategram to modify the column or by ignoring the value, in which case a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generated value is used for this column).</span></span>  
  
 <span data-ttu-id="efb4a-117">系統可以指派兩個值給 `sql:identity` 註解：</span><span class="sxs-lookup"><span data-stu-id="efb4a-117">The `sql:identity` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="efb4a-118">ignore</span><span class="sxs-lookup"><span data-stu-id="efb4a-118">ignore</span></span>  
 <span data-ttu-id="efb4a-119">導向 updategram 忽略 updategram 中針對該資料行提供的任何值，並依賴 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產生識別值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-119">Directs the updategram to ignore any value that is provided in the updategram for that column and to rely on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate the identity value.</span></span>  
  
 <span data-ttu-id="efb4a-120">useValue</span><span class="sxs-lookup"><span data-stu-id="efb4a-120">useValue</span></span>  
 <span data-ttu-id="efb4a-121">導向 updategram 使用 updategram 中提供的值，來更新 IDENTITY 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="efb4a-121">Directs the updategram to use the value that is provided in the updategram to update the IDENTITY-type column.</span></span> <span data-ttu-id="efb4a-122">updategram 不會檢查資料行是否是識別值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-122">An updategram does not check whether the column is an identity value or not.</span></span>  
  
 <span data-ttu-id="efb4a-123">如果 updategram 指定 IDENTITY 類型資料行的值，必須在結構描述中指定 `sql:identity="useValue"`。</span><span class="sxs-lookup"><span data-stu-id="efb4a-123">If the updategram specifies a value for the IDENTITY-type column, the `sql:identity="useValue"` must be specified in the schema.</span></span>  
  
## <a name="sqlguid-annotation"></a><span data-ttu-id="efb4a-124">sql:guid 註解</span><span class="sxs-lookup"><span data-stu-id="efb4a-124">sql:guid Annotation</span></span>  
 <span data-ttu-id="efb4a-125">updategram 可以讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產生 GUID 值，然後在 updategram 中使用此值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-125">An updategram can have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generate a GUID value and then use this value in the updategram.</span></span> <span data-ttu-id="efb4a-126">在 DiffGrams 的內容中，您可以使用 `sql:guid` 註解來指定要使用 SQL Server 所產生的 GUID 值，還是使用 updategram 中針對該資料行提供的值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-126">In the context of DiffGrams, you can use the `sql:guid` annotation to specify whether to use a GUID value that is generated by SQL Server or use the value that is provided in the updategram for that column.</span></span>  
  
 <span data-ttu-id="efb4a-127">系統可以指派兩個值給 `sql:guid` 註解：</span><span class="sxs-lookup"><span data-stu-id="efb4a-127">The `sql:guid` annotation can be assigned two values:</span></span>  
  
 <span data-ttu-id="efb4a-128">generate</span><span class="sxs-lookup"><span data-stu-id="efb4a-128">generate</span></span>  
 <span data-ttu-id="efb4a-129">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所產生的 GUID 用於更新作業中的該資料行。</span><span class="sxs-lookup"><span data-stu-id="efb4a-129">Specifies that the GUID generated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] be used for that column in the update operation.</span></span>  
  
 <span data-ttu-id="efb4a-130">useValue</span><span class="sxs-lookup"><span data-stu-id="efb4a-130">useValue</span></span>  
 <span data-ttu-id="efb4a-131">指定在 updategram 中指定的值用於該資料行。</span><span class="sxs-lookup"><span data-stu-id="efb4a-131">Specifies that the value specified in the updategram be used for the column.</span></span> <span data-ttu-id="efb4a-132">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="efb4a-132">This is the default value.</span></span>  
  
  
