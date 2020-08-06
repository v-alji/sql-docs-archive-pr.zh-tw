---
title: 形成傳回之 XML 的 AUTO 模式啟發學習法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, heuristics in shaping returned XML
ms.assetid: 6c5cb6c1-2921-4ba1-8100-0bf8074f9103
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a64cda8989e1e45d4ad869f8883e1c9d65f4b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585194"
---
# <a name="auto-mode-heuristics-in-shaping-returned-xml"></a><span data-ttu-id="a8017-102">用來形成傳回之 XML 的 AUTO 模式啟發式方法</span><span class="sxs-lookup"><span data-stu-id="a8017-102">AUTO Mode Heuristics in Shaping Returned XML</span></span>
  <span data-ttu-id="a8017-103">AUTO 模式可依據查詢來決定所傳回之 XML 的外觀。</span><span class="sxs-lookup"><span data-stu-id="a8017-103">AUTO mode determines the shape of returned XML based on the query.</span></span> <span data-ttu-id="a8017-104">在決定如何將元素進行巢狀化時，AUTO 模式啟發式方法會比較相鄰資料列中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="a8017-104">In determining how elements are to be nested, AUTO mode heuristics compare column values in adjacent rows.</span></span> <span data-ttu-id="a8017-105">除了 **ntext**、 **text**、 **image**和 **xml**之外，所有類型的資料行都會加以比較。</span><span class="sxs-lookup"><span data-stu-id="a8017-105">Columns of all types, except **ntext**, **text**, **image**, and **xml**, are compared.</span></span> <span data-ttu-id="a8017-106">**(n)varchar(max)** 和 **varbinary(max)** 類型的資料行也會比較。</span><span class="sxs-lookup"><span data-stu-id="a8017-106">Columns of type **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="a8017-107">下列範例說明用來決定所產生之 XML 外觀的 AUTO 模式啟發式方法：</span><span class="sxs-lookup"><span data-stu-id="a8017-107">The following example illustrates the AUTO mode heuristics that determine the shape of the resulting XML:</span></span>  
  
```  
SELECT T1.Id, T2.Id, T1.Name  
FROM   T1, T2  
WHERE ...  
FOR XML AUTO  
ORDER BY T1.Id  
```  
  
 <span data-ttu-id="a8017-108">在決定新的 <`T1`> 元素要從哪裡開始時，若沒有指定 T1 資料表上的索引鍵，就會比較 T1 的所有資料行值 (**ntext**、**text**、**image** 和 **xml** 除外)。</span><span class="sxs-lookup"><span data-stu-id="a8017-108">To determine where a new <`T1`> element starts, all column values of T1, except **ntext**, **text**, **image** and **xml**, are compared if the key on the table T1 is not specified.</span></span> <span data-ttu-id="a8017-109">接著，假設 **Name** 資料行是 **nvarchar(40)** ，且 SELECT 陳述式傳回下列資料列集：</span><span class="sxs-lookup"><span data-stu-id="a8017-109">Next, assume that the **Name** column is **nvarchar(40)** and the SELECT statement returns this rowset:</span></span>  
  
```  
T1.Id  T1.Name  T2.Id  
-----------------------  
1       Andrew    2  
1       Andrew    3  
1       Nancy     4  
```  
  
 <span data-ttu-id="a8017-110">AUTO 模式啟發式方法會比較 T1 資料表中，Id 及 Name 資料行的所有值。</span><span class="sxs-lookup"><span data-stu-id="a8017-110">The AUTO mode heuristics compare all the values of table T1, the Id and Name columns.</span></span> <span data-ttu-id="a8017-111">因為前兩個資料列的 ID 及 Name 資料行具有相同值，因此結果中會新增一個具有兩個 \<T2> 子項目的 \<T1> 項目。</span><span class="sxs-lookup"><span data-stu-id="a8017-111">Because the first two rows have the same values for the Id and Name columns, one \<T1> element having two \<T2> child elements is added in the result.</span></span>  
  
 <span data-ttu-id="a8017-112">以下是所傳回的 XML：</span><span class="sxs-lookup"><span data-stu-id="a8017-112">Following is the XML that is returned:</span></span>  
  
```  
<T1 Id="1" Name="Andrew">  
    <T2 Id="2" />  
    <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
      <T2 Id="4" />  
</T>  
```  
  
 <span data-ttu-id="a8017-113">現在，假設 Name 資料行的類型為 **text** 。</span><span class="sxs-lookup"><span data-stu-id="a8017-113">Now assume that the Name column is of **text** type.</span></span> <span data-ttu-id="a8017-114">AUTO 模式啟發式方法不會比較此類型的值，</span><span class="sxs-lookup"><span data-stu-id="a8017-114">The AUTO mode heuristics do not compare the values for this type.</span></span> <span data-ttu-id="a8017-115">反之，它會假設這些值都不一樣。</span><span class="sxs-lookup"><span data-stu-id="a8017-115">Instead, it assumes that the values are not the same.</span></span> <span data-ttu-id="a8017-116">所產生的 XML 結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="a8017-116">This results in XML generation as shown in the following:</span></span>  
  
```  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="2" />  
</T1>  
<T1 Id="1" Name="Andrew" >  
  <T2 Id="3" />  
</T1>  
<T1 Id="1" Name="Nancy" >  
  <T2 Id="4" />  
</T1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8017-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8017-117">See Also</span></span>  
 [<span data-ttu-id="a8017-118">搭配 FOR XML 使用 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="a8017-118">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
