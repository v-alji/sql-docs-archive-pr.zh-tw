---
title: 混合的類型與簡單的內容 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: rothja
ms.author: jroth
ms.openlocfilehash: eb46769ee4c4d635af36a3c50fda34e8e1801b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687558"
---
# <a name="mixed-type-and-simple-content"></a><span data-ttu-id="7a53d-102">混合的類型與簡單的內容</span><span class="sxs-lookup"><span data-stu-id="7a53d-102">Mixed Type and Simple Content</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7a53d-103">不支援將混合類型限制為簡單內容。</span><span class="sxs-lookup"><span data-stu-id="7a53d-103">does not support restricting a mixed type to a simple content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a53d-104">範例</span><span class="sxs-lookup"><span data-stu-id="7a53d-104">Example</span></span>  
 <span data-ttu-id="7a53d-105">在下列 XML 結構描述集合中， `myComplexTypeA` 是可以清空的複雜類型。</span><span class="sxs-lookup"><span data-stu-id="7a53d-105">In the following XML schema collection, `myComplexTypeA` is a complex type that can be emptied.</span></span> <span data-ttu-id="7a53d-106">也就是說，它的兩個元素都會將 `minOccurs` 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="7a53d-106">That is, both its elements have `minOccurs` set to 0.</span></span> <span data-ttu-id="7a53d-107">不支援透過在 `myComplexTypeB` 宣告中的方式，將此限制為簡單內容。</span><span class="sxs-lookup"><span data-stu-id="7a53d-107">The attempt to restrict this to a simple content, as in the `myComplexTypeB` declaration, is not supported.</span></span> <span data-ttu-id="7a53d-108">因此，下列 XML 結構描述集合的建立將會失敗：</span><span class="sxs-lookup"><span data-stu-id="7a53d-108">Therefore, the following XML schema collection creation fails:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a53d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a53d-109">See Also</span></span>  
 [<span data-ttu-id="7a53d-110">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="7a53d-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
