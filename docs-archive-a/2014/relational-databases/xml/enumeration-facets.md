---
title: 列舉 Facet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e06598890d9b652879327e0351db5113cc17e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585176"
---
# <a name="enumeration-facets"></a><span data-ttu-id="bf86f-102">列舉 Facet</span><span class="sxs-lookup"><span data-stu-id="bf86f-102">Enumeration Facets</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bf86f-103">會拒絕類型含有模式 Facet 或列舉違反這些 Facet 的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="bf86f-103">rejects XML schemas with types that have pattern facets or enumerations that violate those facets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf86f-104">範例</span><span class="sxs-lookup"><span data-stu-id="bf86f-104">Example</span></span>  
 <span data-ttu-id="bf86f-105">下列結構描述將遭到拒絕，因為主要的列舉值包含大小字母混合的值。</span><span class="sxs-lookup"><span data-stu-id="bf86f-105">The following schema would be rejected, because the featured enumeration value includes a mixed-case value.</span></span> <span data-ttu-id="bf86f-106">它也將遭到拒絕，因為此值違反值只能是小寫字母的模式值。</span><span class="sxs-lookup"><span data-stu-id="bf86f-106">It would also be rejected because this value violates the pattern value that limits values to only lowercase letters.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf86f-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf86f-107">See Also</span></span>  
 [<span data-ttu-id="bf86f-108">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="bf86f-108">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
