---
title: 無效的字元和逸出規則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, invalid characters
- FOR XML clause, escape rules
ms.assetid: f2e9b997-f400-4963-b225-59d46c6b93e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 8624a31dea4e97e05da6d86c3c0c518b9c4d0aba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709021"
---
# <a name="invalid-characters-and-escape-rules"></a><span data-ttu-id="b9742-102">無效的字元和逸出規則</span><span class="sxs-lookup"><span data-stu-id="b9742-102">Invalid Characters and Escape Rules</span></span>
  <span data-ttu-id="b9742-103">此主題描述 FOR XML 子句如何處理無效的 XML 字元，並列出 XML 名稱中無效字元的逸出規則。</span><span class="sxs-lookup"><span data-stu-id="b9742-103">This topic describes how invalid XML characters are handled by the FOR XML clause, and lists the escape rules for characters that are invalid in XML names.</span></span>  
  
## <a name="for-xml-and-invalid-characters"></a><span data-ttu-id="b9742-104">XML 和無效的字元</span><span class="sxs-lookup"><span data-stu-id="b9742-104">For XML and Invalid Characters</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9742-105">在不使用 TYPE 指示詞的 FOR XML 查詢中傳回無效的 XML 字元時，會將這些字元實體化。</span><span class="sxs-lookup"><span data-stu-id="b9742-105">entitizes invalid XML characters when they are returned within FOR XML queries that do not use the TYPE directive.</span></span>  
  
 <span data-ttu-id="b9742-106">雖然不論這些字元是否已實體化，XML 1.0 相容剖析器都會引發剖析錯誤，但實體化格式與 XML 1.1 之間的相容性已有所提升。</span><span class="sxs-lookup"><span data-stu-id="b9742-106">Although XML 1.0 conformant parsers raise parse errors regardless of whether these characters are entitized or not, the entitized form is better aligned with XML 1.1.</span></span> <span data-ttu-id="b9742-107">實體化格式與未來的 XML 標準版本之間也將具有較好的相容性。</span><span class="sxs-lookup"><span data-stu-id="b9742-107">The entitized form is also potentially better aligned with future versions of the XML standard.</span></span> <span data-ttu-id="b9742-108">此外，它還可簡化偵錯作業，因為已可看見無效字元的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="b9742-108">Additionally, it makes debugging simpler, because the code point of the invalid character becomes visible.</span></span>  
  
 <span data-ttu-id="b9742-109">對於 XML 工具的使用者，則不需使用任何解決方案，因為無論如何 XML 剖析器都會在資料流中出現無效字元時失敗。</span><span class="sxs-lookup"><span data-stu-id="b9742-109">For users of XML tools, no workaround is required, because the XML parser will fail either way at the point where the invalid characters occur in the data stream.</span></span> <span data-ttu-id="b9742-110">若您使用非 XML 工具，則此項變更需要您更新程式設計邏輯，使其搜尋這些當做實體化值的字元。</span><span class="sxs-lookup"><span data-stu-id="b9742-110">If you use non-XML tools, this change can require you to update your programming logic to search for these characters as entitized values.</span></span>  
  
 <span data-ttu-id="b9742-111">目前已可透過不同的方式在 FOR XML 查詢中實體化下列空白字元，以便在往返過程中保留這些字元：</span><span class="sxs-lookup"><span data-stu-id="b9742-111">The following white space characters are entitized differently in FOR XML queries to preserve their presence through round-tripping:</span></span>  
  
-   <span data-ttu-id="b9742-112">在元素內容和屬性中： **hex(0D)** (歸位字元)</span><span class="sxs-lookup"><span data-stu-id="b9742-112">In element content and attributes: **hex(0D)** (carriage return)</span></span>  
  
-   <span data-ttu-id="b9742-113">在屬性內容中： **hex(09)** (定位字元)、 **hex(0A)** (換行字元)</span><span class="sxs-lookup"><span data-stu-id="b9742-113">In attribute content: **hex(09)** (tab), **hex(0A)** (line feed)</span></span>  
  
 <span data-ttu-id="b9742-114">輸出中會保留這些字元，且剖析器不會將其正規化。</span><span class="sxs-lookup"><span data-stu-id="b9742-114">These characters are preserved in output, and a parser will not normalize them.</span></span>  
  
## <a name="escape-rules"></a><span data-ttu-id="b9742-115">逸出規則</span><span class="sxs-lookup"><span data-stu-id="b9742-115">Escape Rules</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b9742-116">若名稱中含有對 XML 名稱而言無效的字元 (如空格)，則會在轉譯為 XML 名稱時，將該無效字元轉譯為逸出的數值實體編碼。</span><span class="sxs-lookup"><span data-stu-id="b9742-116">names that contain characters that are invalid in XML names, such as spaces, are translated into XML names in a way in which the invalid characters are translated into escaped numeric entity encoding.</span></span>  
  
 <span data-ttu-id="b9742-117">XML 名稱中只允許兩種非字母字元：冒號 (:) 和底線 (_)。</span><span class="sxs-lookup"><span data-stu-id="b9742-117">There are only two non-alphabetic characters that can occur within an XML name: the colon (:) and the underscore (_).</span></span> <span data-ttu-id="b9742-118">這是因為冒號已保留給命名空間，而底線已被選為逸出字元。</span><span class="sxs-lookup"><span data-stu-id="b9742-118">Because the colon is already reserved for namespaces, the underscore is chosen as the escape character.</span></span> <span data-ttu-id="b9742-119">以下是適用於編碼的逸出規則：</span><span class="sxs-lookup"><span data-stu-id="b9742-119">Following are the escape rules that are used for encoding:</span></span>  
  
-   <span data-ttu-id="b9742-120">根據 XML 1.0 規格，任何不屬於有效 XML 名稱字元的 UCS-2 字元，都會逸出為 _xHHHH\_。</span><span class="sxs-lookup"><span data-stu-id="b9742-120">Any UCS-2 character that is not a valid XML name character, according to the XML 1.0 specification, is escaped as _xHHHH\_.</span></span> <span data-ttu-id="b9742-121">HHHH 代表最高階位元優先順序之字元的四位數十六進位 UCS-2 碼。</span><span class="sxs-lookup"><span data-stu-id="b9742-121">The HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="b9742-122">例如，資料表名稱 **Order Details** 會編碼為 Order_x0020_Details。</span><span class="sxs-lookup"><span data-stu-id="b9742-122">For example, the table name **Order Details** is encoded as Order_x0020_Details.</span></span>  
  
-   <span data-ttu-id="b9742-123">不符合 UCS-2 範圍 (UCS-4 新增的，範圍介於 U+00010000 與 U+0010FFFF 之間) 的字元都會編碼為 _xHHHHHHHH\_。</span><span class="sxs-lookup"><span data-stu-id="b9742-123">Characters that do not fit into the UCS-2 realm (the UCS-4 additions of the range U+00010000 to U+0010FFFF) are encoded as _xHHHHHHHH\_.</span></span> <span data-ttu-id="b9742-124">在 SQL Server 2000 回溯相容性模式中，HHHHHHHH 代表字元的八位數十六進位 UCS-4 編碼。</span><span class="sxs-lookup"><span data-stu-id="b9742-124">The HHHHHHHH stands for the eight-digit hexadecimal UCS-4 encoding of the character, if under SQL Server 2000 backward compatibility mode.</span></span> <span data-ttu-id="b9742-125">在其他情況下，字元會編碼為 _xHHHHHH\_，以符合 ISO 標準。</span><span class="sxs-lookup"><span data-stu-id="b9742-125">Otherwise, the characters are encoded as_xHHHHHH\_, in order to align with the ISO standard.</span></span>  
  
-   <span data-ttu-id="b9742-126">除非下一個字元是 x，否則底線字元不需要逸出。</span><span class="sxs-lookup"><span data-stu-id="b9742-126">The underscore character does not have to be escaped unless it is followed by the character x.</span></span> <span data-ttu-id="b9742-127">例如，資料表名稱 **Order_Details** 就未編碼。</span><span class="sxs-lookup"><span data-stu-id="b9742-127">For example, the table name **Order_Details** is not encoded.</span></span>  
  
-   <span data-ttu-id="b9742-128">識別碼的冒號也不會逸出，因此命名空間元素及屬性名稱才能夠由 FOR XML 查詢產生。</span><span class="sxs-lookup"><span data-stu-id="b9742-128">The colon in identifiers is not escaped As a result, the namespace element and attribute names can be generated by the FOR XML query.</span></span> <span data-ttu-id="b9742-129">例如，下列查詢所產生的命名空間屬性在名稱中就有冒號：</span><span class="sxs-lookup"><span data-stu-id="b9742-129">For example, the following query generates a namespace attribute that has a colon in the name:</span></span>  
  
    ```  
    SELECT 'namespace-urn' as 'xmlns:namespace',   
     1 as 'namespace:a'   
    FOR XML RAW  
    ```  
  
     <span data-ttu-id="b9742-130">此查詢產生以下結果：</span><span class="sxs-lookup"><span data-stu-id="b9742-130">The query produces this result:</span></span>  
  
    ```  
    <row xmlns:namespace="namespace-urn" namespace:a="1"/>  
    ```  
  
     <span data-ttu-id="b9742-131">請注意，建議使用 WITH XMLNAMESPACES 來加入 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9742-131">Note that WITH XMLNAMESPACES is the recommended way to add XML namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9742-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9742-132">See Also</span></span>  
 [<span data-ttu-id="b9742-133">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9742-133">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
