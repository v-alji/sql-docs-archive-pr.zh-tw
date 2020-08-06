---
title: 不具決定性的內容模型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: rothja
ms.author: jroth
ms.openlocfilehash: 6182ff4a5ee0c9c109f6880c7d3337fb6dd20749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687553"
---
# <a name="non-deterministic-content-models"></a><span data-ttu-id="4a755-102">不具決定性的內容模型</span><span class="sxs-lookup"><span data-stu-id="4a755-102">Non-Deterministic Content Models</span></span>
  <span data-ttu-id="4a755-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會拒絕具有不具決定性之內容模型的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a755-103">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejected XML schemas that had non-deterministic content models.</span></span>  
  
 <span data-ttu-id="4a755-104">但是從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 開始，即使出現次數條件約束為 0、1 或未受約束，仍可接受不具決定性的內容模型。</span><span class="sxs-lookup"><span data-stu-id="4a755-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1, however, non-deterministic content models are accepted if the occurrence constraints are 0,1, or unbounded.</span></span>  
  
## <a name="example-non-deterministic-content-model-rejected"></a><span data-ttu-id="4a755-105">範例：拒絕不具決定性的內容模型</span><span class="sxs-lookup"><span data-stu-id="4a755-105">Example: Non-deterministic content model rejected</span></span>  
 <span data-ttu-id="4a755-106">下列範例會嘗試建立具有不具決定性之內容模型的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a755-106">The following example attempts to create an XML schema with a non-deterministic content model.</span></span> <span data-ttu-id="4a755-107">此程式碼會失敗，因為 `<root>` 元素是否應該具有兩個 `<a>` 元素的序列，或者 `<root>` 元素是否應該具有兩個序列 (每個序列含有一個 `<a>` 元素) 並不明確。</span><span class="sxs-lookup"><span data-stu-id="4a755-107">The code fails because it is not clear whether the `<root>` element should have a sequence of two `<a>` elements or if the `<root>` element should have two sequences, each with an `<a>` element.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 <span data-ttu-id="4a755-108">將出現次數條件約束移動至唯一位置，即可修正結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a755-108">The schema can be fixed by moving the occurrence constraint to a unique location.</span></span> <span data-ttu-id="4a755-109">例如，可將條件約束移動至包含順序物件：</span><span class="sxs-lookup"><span data-stu-id="4a755-109">For example, the constraint can be moved to the containing sequence particle:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 <span data-ttu-id="4a755-110">或者，可將條件約束移動至內含元素：</span><span class="sxs-lookup"><span data-stu-id="4a755-110">Or the constraint can be moved to the contained element:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a><span data-ttu-id="4a755-111">範例：接受不具決定性的內容模型</span><span class="sxs-lookup"><span data-stu-id="4a755-111">Example: Non-deterministic content model accepted</span></span>  
 <span data-ttu-id="4a755-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，下列結構描述會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="4a755-112">The following schema would be rejected in versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a755-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a755-113">See Also</span></span>  
 [<span data-ttu-id="4a755-114">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="4a755-114">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
