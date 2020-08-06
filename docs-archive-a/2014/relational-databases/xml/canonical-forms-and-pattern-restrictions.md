---
title: 標準格式與模式限制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
author: rothja
ms.author: jroth
ms.openlocfilehash: 569e8c4a01ed1eb9ae26ea9e2f6d471b9aad9fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585191"
---
# <a name="canonical-forms-and-pattern-restrictions"></a><span data-ttu-id="47c94-102">標準格式與模式限制</span><span class="sxs-lookup"><span data-stu-id="47c94-102">Canonical Forms and Pattern Restrictions</span></span>
  <span data-ttu-id="47c94-103">XSD 模式 Facet 允許簡單類型的語彙空間限制。</span><span class="sxs-lookup"><span data-stu-id="47c94-103">The XSD pattern facet allows for the restriction of the lexical space of simple types.</span></span> <span data-ttu-id="47c94-104">當在有一個以上的可能語彙表示法之類型上設置模式限制時，有些值可能會在驗證時造成非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="47c94-104">When a pattern restriction is put on a type for which there is more than one possible lexical representation, some values could cause unexpected behavior upon validation.</span></span>  
  
 <span data-ttu-id="47c94-105">因為這些值的語彙表示法並未儲存在資料庫中，就會發生此行為。</span><span class="sxs-lookup"><span data-stu-id="47c94-105">This behavior occurs because lexical representations of these values are not stored in the database.</span></span> <span data-ttu-id="47c94-106">因此，當序列化為輸出時，這些值會轉換成其標準的表示法。</span><span class="sxs-lookup"><span data-stu-id="47c94-106">Therefore, the values are converted to their canonical representations when serialized as output.</span></span> <span data-ttu-id="47c94-107">當文件包含一個值，而值的標準格式不符合其類型的模式限制時，如果使用者嘗試重新插入它，將會拒絕該文件。</span><span class="sxs-lookup"><span data-stu-id="47c94-107">If a document contains a value whose canonical form does not comply with the pattern restriction for its type, the document is rejected if a user tries to reinsert it.</span></span>  
  
 <span data-ttu-id="47c94-108">為了避免此情形， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會拒絕包含無法重新插入的值之 XML 文件，因為違反了其標準格式的模式限制。</span><span class="sxs-lookup"><span data-stu-id="47c94-108">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any XML document that contains values that cannot be reinserted, because of the violation of pattern restrictions by their canonical forms.</span></span> <span data-ttu-id="47c94-109">例如，值 "33.000" 將不會針對具有 "33 **.0+" 模式限制之** xs:decimal\\所衍生的類型驗證。</span><span class="sxs-lookup"><span data-stu-id="47c94-109">For example, the value "33.000" does not validate against a type derived from **xs:decimal** with a pattern restriction of "33\\.0+".</span></span> <span data-ttu-id="47c94-110">雖然 "33.000" 符合此模式，但是標準格式 "33" 卻不符合。</span><span class="sxs-lookup"><span data-stu-id="47c94-110">Although "33.000" complies with this pattern, the canonical form, "33", does not.</span></span>  
  
 <span data-ttu-id="47c94-111">因此，當您將模式 Facet 套用到衍生自下列基本類型的類型時，應該要特別小心：`boolean`、`decimal`、`float`、`double`、`dateTime`、`time`、`date`、`hexBinary` 和 `base64Binary`。</span><span class="sxs-lookup"><span data-stu-id="47c94-111">Therefore, you should be careful when you apply pattern facets to types derived from the following primitive types: `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary`, and `base64Binary`.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47c94-112">就會發出警告。</span><span class="sxs-lookup"><span data-stu-id="47c94-112">issues a warning when you add any such components to a schema collection.</span></span>  
  
 <span data-ttu-id="47c94-113">不精確的浮點值序列化具有類似的問題。</span><span class="sxs-lookup"><span data-stu-id="47c94-113">Imprecise serialization of floating-point values has a similar problem.</span></span> <span data-ttu-id="47c94-114">由於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用浮點序列化演算法，類似的值有可以共用相同的標準格式。</span><span class="sxs-lookup"><span data-stu-id="47c94-114">Because of the floating-point serialization algorithm used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible for similar values to share the same canonical form.</span></span> <span data-ttu-id="47c94-115">當序列化和重新插入浮點值時，它有可能變更其值。</span><span class="sxs-lookup"><span data-stu-id="47c94-115">When a floating-point value is serialized and then reinserted, its value may change slightly.</span></span> <span data-ttu-id="47c94-116">在極少數的情況下，這可能會在重新插入時，產生違反下列任何 Facet 類型的值： **enumeration**、 **minInclusive**、 **minExclusive**、 **maxInclusive**或 **maxExclusive**。</span><span class="sxs-lookup"><span data-stu-id="47c94-116">In rare cases, this may result in a value that violates any of the following facets for its type on reinsertion: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**, or **maxExclusive**.</span></span> <span data-ttu-id="47c94-117">為了避免此情形， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會拒絕從無法序列化和重新插入的 `xs:float` 或 `xs:double` 所衍生的任何類型值。</span><span class="sxs-lookup"><span data-stu-id="47c94-117">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any values of types derived from `xs:float` or `xs:double` that cannot be serialized and reinserted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c94-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c94-118">See Also</span></span>  
 [<span data-ttu-id="47c94-119">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="47c94-119">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
