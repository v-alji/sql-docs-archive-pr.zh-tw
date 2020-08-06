---
title: 唯一物件屬性條件約束 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: rothja
ms.author: jroth
ms.openlocfilehash: 7416aa4ea14539f3bf633207768783aa439ec818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686855"
---
# <a name="unique-particle-attribution-constraint"></a><span data-ttu-id="806bd-102">唯一物件屬性條件約束</span><span class="sxs-lookup"><span data-stu-id="806bd-102">Unique Particle Attribution Constraint</span></span>
  <span data-ttu-id="806bd-103">在 XSD 中，會以唯一物件屬性 (UPA) 條件約束規則來限制複雜的內容模型。</span><span class="sxs-lookup"><span data-stu-id="806bd-103">In XSD, complex content models are constrained by the unique particle attribution (UPA) constraint rule.</span></span> <span data-ttu-id="806bd-104">此規則要求執行個體文件中的每個元素，都要明確地對應至其父系內容模型中的一個 `<xsd:element>` 或 `<xsd:any>` 物件。</span><span class="sxs-lookup"><span data-stu-id="806bd-104">This rule requires that each element in an instance document correspond unambiguously to exactly one `<xsd:element>` or `<xsd:any>` particle in its parent's content model.</span></span> <span data-ttu-id="806bd-105">若有任何結構描述，其包含的類型可能含有模稜兩可的內容模型，都會被拒絕。</span><span class="sxs-lookup"><span data-stu-id="806bd-105">Any schema that contains a type with a potentially ambiguous content model is rejected.</span></span>  
  
 <span data-ttu-id="806bd-106">導致內容模型模稜兩可的最常見原因，就是 `<xsd:any>` 萬用字元，以及具有變動出現範圍的物件，例如：minOccurs < maxOccurs。</span><span class="sxs-lookup"><span data-stu-id="806bd-106">The most common causes of ambiguity are `<xsd:any>` wildcard characters and particles that have variable occurrence ranges, such as minOccurs < maxOccurs.</span></span> <span data-ttu-id="806bd-107">例如，下列內容模型是模稜兩可的，因為 <`e1`> 元素可以符合 `<xsd:element>`，也可以符合 `<xsd:any>` 元素。</span><span class="sxs-lookup"><span data-stu-id="806bd-107">For example, the following content model is ambiguous, because an <`e1`> element could match either the `<xsd:element>` or the `<xsd:any>` element.</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="806bd-108">下列內容模型也是不明確的：</span><span class="sxs-lookup"><span data-stu-id="806bd-108">The following content model is also ambiguous:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="806bd-109">雖然 `<root><e1/><e2/><e1/></root>` 這類文件可以明確地加以驗證，但是 `<root><e1/><e1/></root>` 這類文件沒有辦法，因為第二個 `<xsd:element>` 所對應的目標 `<e1/>` 並不清楚。</span><span class="sxs-lookup"><span data-stu-id="806bd-109">Although a document such as `<root><e1/><e2/><e1/></root>` can be validated unambiguously, a document such as `<root><e1/><e1/></root>` cannot, because it is not clear to which `<xsd:element>` the second `<e1/>` corresponds.</span></span> <span data-ttu-id="806bd-110">即使某些文件可以被明確地驗證，但是結構描述還是會被拒絕，因為它們潛藏著不明確性。</span><span class="sxs-lookup"><span data-stu-id="806bd-110">Even though some documents can be validated unambiguously, the schema will be rejected, because of the potential for ambiguity.</span></span>  
  
 <span data-ttu-id="806bd-111">請注意，若要讓內容模型有效，需在不必往前查看的情況下，就能明確地驗證任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="806bd-111">Note that for a content model to be valid, it must be possible to validate any instance unambiguously without looking ahead.</span></span> <span data-ttu-id="806bd-112">例如，請考量下列內容模型：</span><span class="sxs-lookup"><span data-stu-id="806bd-112">For example, consider the following content model:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="806bd-113">像 `<root><e1/><e3/></root>`這類文件，序列 `<e1/><e3/>` 明確地符合第二個 `<xsd:sequence>`。</span><span class="sxs-lookup"><span data-stu-id="806bd-113">For a document such as `<root><e1/><e3/></root>`, the sequence `<e1/><e3/>` unambiguously matches the second `<xsd:sequence>`.</span></span> <span data-ttu-id="806bd-114">然而，因為 `<xsd:element>` 所對應的 `<e1/>` 在沒有往前查看 `<e3/>`的情況下，即無法做出判斷，所以內容模型違反了 UPA 條件約束規則。</span><span class="sxs-lookup"><span data-stu-id="806bd-114">However, because the `<xsd:element>` to which `<e1/>` corresponds cannot be determined without looking ahead to `<e3/>`, the content model violates the UPA constraint rule.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="806bd-115">尋找詳細資訊</span><span class="sxs-lookup"><span data-stu-id="806bd-115">Finding More Information</span></span>  
 <span data-ttu-id="806bd-116">下列文件是由全球資訊網協會 (W3C) 所發行，其中包含唯一物件屬性條件約束的技術說明：</span><span class="sxs-lookup"><span data-stu-id="806bd-116">The following document is published by the World Wide Web Consortium (W3C) and contains the technical description of the unique particle attribution constraint:</span></span>  
  
 <span data-ttu-id="806bd-117">"XML Schema Part 1:Structures Second Edition, W3C Proposed Edited Recommendation" (XML 結構描述第 1 部分：結構第二版，W3C 提出的編輯建議)：</span><span class="sxs-lookup"><span data-stu-id="806bd-117">"XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation":</span></span>  
  
-   <span data-ttu-id="806bd-118">3\.8.6 節：Constraints on Model Group Schema Components (模型群組結構描述元件的條件約束)</span><span class="sxs-lookup"><span data-stu-id="806bd-118">Section 3.8.6: Constraints on Model Group Schema Components</span></span>  
  
-   <span data-ttu-id="806bd-119">附錄 H：Analysis of the Unique Particle Attribution Constraint (non-normative) (唯一物件屬性條件約束的分析 (非標準))</span><span class="sxs-lookup"><span data-stu-id="806bd-119">Appendix H: Analysis of the Unique Particle Attribution Constraint (non-normative)</span></span>  
  
 <span data-ttu-id="806bd-120">若要查看文件，請瀏覽 [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881)。</span><span class="sxs-lookup"><span data-stu-id="806bd-120">To see the document, visit [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="806bd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="806bd-121">See Also</span></span>  
 [<span data-ttu-id="806bd-122">XML 結構描述集合 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="806bd-122">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
