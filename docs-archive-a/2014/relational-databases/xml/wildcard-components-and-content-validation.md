---
title: 萬用字元元件和內容驗證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: rothja
ms.author: jroth
ms.openlocfilehash: 76ff2b48efb8cff0b98827fe8522405682c294e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592553"
---
# <a name="wildcard-components-and-content-validation"></a><span data-ttu-id="5a1fa-102">萬用字元元件和內容驗證</span><span class="sxs-lookup"><span data-stu-id="5a1fa-102">Wildcard Components and Content Validation</span></span>
  <span data-ttu-id="5a1fa-103">萬用字元元件可用以增加可出現在內容模型中的內容彈性。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-103">Wildcard components are used to increase flexibility in what is allowed to appear in a content model.</span></span> <span data-ttu-id="5a1fa-104">在 XSD 語言中，可透過下列方式支援這些元件：</span><span class="sxs-lookup"><span data-stu-id="5a1fa-104">These components are supported in the XSD language in the following ways:</span></span>  
  
-   <span data-ttu-id="5a1fa-105">元素萬用字元元件。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-105">Element wildcard components.</span></span> <span data-ttu-id="5a1fa-106">這些是以 **\<xsd:any>** 元素表示。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-106">These are represented by the **\<xsd:any>** element.</span></span>  
  
-   <span data-ttu-id="5a1fa-107">屬性萬用字元元件。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-107">Attribute wildcard components.</span></span> <span data-ttu-id="5a1fa-108">這些是以 **\<xsd:anyAttribute>** 元素表示。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-108">These are represented by the **\<xsd:anyAttribute>** element.</span></span>  
  
 <span data-ttu-id="5a1fa-109">**\<xsd:any>** 與 **\<xsd:anyAttribute>** 這兩個萬用字元元素都支援使用 **processContents** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-109">Both wildcard character elements, **\<xsd:any>** and **\<xsd:anyAttribute>**, support the use of a **processContents** attribute.</span></span> <span data-ttu-id="5a1fa-110">這可讓您指定一個值，以指出 XML 應用程式如何處理與這些萬用字元元素關聯的文件內容驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-110">This lets you specify a value that indicates how XML applications handle the validation of document content associated with these wildcard character elements.</span></span> <span data-ttu-id="5a1fa-111">以下是不同的值所產生的效果：</span><span class="sxs-lookup"><span data-stu-id="5a1fa-111">These are the different values and their effect:</span></span>  
  
-   <span data-ttu-id="5a1fa-112">**strict** 值指定完整驗證內容。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-112">The **strict** value specifies that the contents are fully validated.</span></span>  
  
-   <span data-ttu-id="5a1fa-113">**skip** 值指定不驗證內容。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-113">The **skip** value specifies that the contents are not validated.</span></span>  
  
-   <span data-ttu-id="5a1fa-114">**lax** 值指定只會驗證可以使用結構描述定義的元素與屬性。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-114">The **lax** value specifies that only elements and attributes for which schema definitions are available are validated.</span></span>  
  
## <a name="lax-validation-and-xsanytype-elements"></a><span data-ttu-id="5a1fa-115">Lax 驗證和 xs:anyType 元素</span><span class="sxs-lookup"><span data-stu-id="5a1fa-115">Lax Validation and xs:anyType Elements</span></span>  
 <span data-ttu-id="5a1fa-116">XML 結構描述規格會針對 **anyType** 類型的元素使用 **lax** 驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-116">The XML Schema specification uses **lax** validation for elements of the **anyType** type.</span></span> <span data-ttu-id="5a1fa-117">因為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 不支援 Lax 驗證，因此會對 **anyType**的元素套用 Strict 驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-117">Because [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] did not support lax validation, strict validation was applied for elements of the **anyType**.</span></span> <span data-ttu-id="5a1fa-118">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始，Lax 驗證就有受到支援。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-118">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], lax validation is supported.</span></span> <span data-ttu-id="5a1fa-119">**anyType** 類型的元素內容將會使用 Lax 驗證加以驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-119">Content of elements of type **anyType** will be validated using lax validation.</span></span>  
  
 <span data-ttu-id="5a1fa-120">下列範例說明 Lax 驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-120">The following example illustrates the lax validation.</span></span> <span data-ttu-id="5a1fa-121">`e` 結構描述元素的類型為 **anyType** 。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-121">The schema element `e` is of the **anyType** type.</span></span> <span data-ttu-id="5a1fa-122">此範例會建立具類型的 **xml** 變數，並說明 **anyType** 類型元素的 Lax 驗證。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-122">The example creates typed **xml** variables and illustrates the lax validation of the element of the **anyType** type.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 <span data-ttu-id="5a1fa-123">下列範例會成功，因為 `<e>` 的驗證是成功的：</span><span class="sxs-lookup"><span data-stu-id="5a1fa-123">The following example succeeds, because the validation of `<e>` is successful:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="5a1fa-124">下列範例將會成功。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-124">The following example succeeds.</span></span> <span data-ttu-id="5a1fa-125">即使此結構描述中未定義任何 `<c>` 元素，還是可接受此結構描述：</span><span class="sxs-lookup"><span data-stu-id="5a1fa-125">The instance is accepted, even though no element `<c>` is defined in the schema:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="5a1fa-126">下列範例中的 XML 執行個體會遭到拒絕，因為 `<a>` 元素的定義不允許字串值。</span><span class="sxs-lookup"><span data-stu-id="5a1fa-126">The XML instance in the following example is rejected, because the definition of the `<a>` element does not allow a string value.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a1fa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a1fa-127">See Also</span></span>  
 [<span data-ttu-id="5a1fa-128">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="5a1fa-128">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
