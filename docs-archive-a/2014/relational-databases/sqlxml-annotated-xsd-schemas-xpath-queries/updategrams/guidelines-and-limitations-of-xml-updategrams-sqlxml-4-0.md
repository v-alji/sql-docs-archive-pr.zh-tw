---
title: XML Updategram (SQLXML 4.0) 的方針和限制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e01e366edc2889691862de639f69220ac4bb439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700873"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a><span data-ttu-id="9ff79-102">XML Updategram 的指導方針和限制 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="9ff79-102">Guidelines and Limitations of XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="9ff79-103">使用 XML Updategram 時，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="9ff79-103">Remember the following when using XML updategrams:</span></span>  
  
-   <span data-ttu-id="9ff79-104">如果您針對僅具有一組和區塊的插入作業使用 updategram **\<before>** **\<after>** ，則 **\<before>** 可以省略區塊。</span><span class="sxs-lookup"><span data-stu-id="9ff79-104">If you are using an updategram for an insert operation with only a single pair of **\<before>** and **\<after>** blocks, the **\<before>** block can be omitted.</span></span> <span data-ttu-id="9ff79-105">相反地，在刪除作業時， **\<after>** 可以省略區塊。</span><span class="sxs-lookup"><span data-stu-id="9ff79-105">Conversely, in case of a delete operation, the **\<after>** block can be omitted.</span></span>  
  
-   <span data-ttu-id="9ff79-106">如果您在標記中使用具有多個 **\<before>** 和區塊的 updategram，則 **\<after>** **\<sync>** **\<before>** 必須同時 **\<after>** 指定區塊和區塊來形成 **\<before>** 和 **\<after>** 配對。</span><span class="sxs-lookup"><span data-stu-id="9ff79-106">If you are using an updategram with multiple **\<before>** and **\<after>** blocks in the **\<sync>** tag, both **\<before>** blocks and **\<after>** blocks must be specified to form **\<before>** and **\<after>** pairs.</span></span>  
  
-   <span data-ttu-id="9ff79-107">Updategram 中的更新會套用到 XML 結構描述所提供的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="9ff79-107">The updates in an updategram are applied to the XML view that is provided by the XML schema.</span></span> <span data-ttu-id="9ff79-108">因此，若要讓預設的對應成功，您必須在 Updategram 中指定結構描述檔案名稱，或者，如果沒有提供檔案名稱，元素和屬性名稱必須符合資料庫中的資料表和資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="9ff79-108">Therefore, for the default mapping to succeed either you must specify the schema file name in the updategram or, if the file name is not provided, the element and attribute names must match the table and column names in the database.</span></span>  
  
-   <span data-ttu-id="9ff79-109">SQLXML 4.0 要求 Updategram 中的所有資料行值都必須在提供的結構描述 (XDR 或 XSD) 中明確對應，才能構成其子元素的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="9ff79-109">SQLXML 4.0 requires that all column values in an updategram must be explicitly mapped in the schema (either XDR or XSD) provided to compose the XML view for its child elements.</span></span> <span data-ttu-id="9ff79-110">此行為與舊版 SQLXML 不同，如果這意味著 `sql:relationship` 註解中外部索引鍵的一部分，則允許在結構描述中不對應資料行的值 </span><span class="sxs-lookup"><span data-stu-id="9ff79-110">This behavior differs from earlier versions of SQLXML, which allowed a value for a column not mapped in the schema if it was implied as part of the foreign Key in a `sql:relationship` annotation.</span></span> <span data-ttu-id="9ff79-111">(請注意，此變更不會影響主索引鍵值傳播到子元素，如果沒有針對子元素明確指定任何值，仍然會發生在 SQLXML 4.0 上。</span><span class="sxs-lookup"><span data-stu-id="9ff79-111">(Note that this change does not affect propagation of primary key values to child elements, which still occurs for SQLXML 4.0 if no value is explicitly specified for the child element.</span></span>  
  
-   <span data-ttu-id="9ff79-112">如果您要使用 updategram 來修改二進位資料行中的資料 (例如) 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` 資料類型，您必須提供對應架構，其中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (例如 `sql:datatype="image"`) 和 XML 資料類型 (例如， `dt:type="binhex"` 或 `dt:type="binbase64` 必須指定) 。</span><span class="sxs-lookup"><span data-stu-id="9ff79-112">If you are using an updategram to modify data in a binary column (such as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` data type), you must provide a mapping schema in which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (for example, `sql:datatype="image"`) and the XML data type (for example, `dt:type="binhex"` or `dt:type="binbase64`) must be specified.</span></span> <span data-ttu-id="9ff79-113">二進位資料行的資料必須在 Updategram 中指定；Updategram 會忽略在對應結構描述中指定的 `sql:url-encode` 註解。</span><span class="sxs-lookup"><span data-stu-id="9ff79-113">The data for the binary column must be specified in the updategram; the `sql:url-encode` annotation that is specified in the mapping schema is ignored by the updategram.</span></span>  
  
-   <span data-ttu-id="9ff79-114">當您要撰寫 XSD 結構描述時，如果您針對 `sql:relation` 或 `sql:field` 註解指定的值包含特殊字元，如空白字元 (例如，在 "Order Details" 資料表名稱中)，則必須以方括號括住這個值 (例如，"[Order Details]")。</span><span class="sxs-lookup"><span data-stu-id="9ff79-114">When you are writing an XSD schema, if the value you specify for the `sql:relation` or `sql:field` annotation includes a special character, such as a space character (for example, in the "Order Details" table name), this value must be enclosed in brackets (for example, "[Order Details]").</span></span>  
  
-   <span data-ttu-id="9ff79-115">使用 Updategram 時，不支援鏈結關聯性。</span><span class="sxs-lookup"><span data-stu-id="9ff79-115">When using updategrams, chain relationships are not supported.</span></span> <span data-ttu-id="9ff79-116">例如，如果資料表 A 和 C 透過使用資料表 B 的鏈結關聯性相關聯，嘗試執行 Updategram 時，會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="9ff79-116">For example, if tables A and C are related through a chain relationship that uses table B, the following error will occur when attempting to run and execute the updategram:</span></span>  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     <span data-ttu-id="9ff79-117">即使結構描述和 Updategram 都正確而且格式有效，如果存在鏈結關聯性，則會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ff79-117">Even if both schema and updategram are otherwise correct and validly formed, this error will occur if a chain relationship is present.</span></span>  
  
-   <span data-ttu-id="9ff79-118">在更新期間，Updategram 不允許將 `image` 類型資料當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="9ff79-118">Updategrams do not permit the passing of `image` type data as parameters during updates.</span></span>  
  
-   <span data-ttu-id="9ff79-119">使用 updategram 時，二進位大型物件 (BLOB) 類型（例如 `text/ntext` 和影像）不應該在中的區塊中使用 **\<before>** ，因為這會包含它們以用於並行控制中。</span><span class="sxs-lookup"><span data-stu-id="9ff79-119">Binary large object (BLOB) types like `text/ntext` and images should not be used in the **\<before>** block in when working with updategrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="9ff79-120">這可能會因為 BLOB 類型的比較限制而造成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的問題。</span><span class="sxs-lookup"><span data-stu-id="9ff79-120">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="9ff79-121">例如，WHERE 子句中的 LIKE 關鍵字用於 `text` 資料類型之資料行間的比較，不過，如果 BLOB 類型中，資料大小大於 8K，則比較將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ff79-121">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="9ff79-122">`ntext` 資料中的特殊字元可能會因為 BLOB 類型的比較限制而造成 SQLXML 4.0 的問題。</span><span class="sxs-lookup"><span data-stu-id="9ff79-122">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="9ff79-123">例如，在類型資料行的並行檢查中使用 "[Serializable]" 時，在 updategram 的區塊中使用 "[Serializable]" **\<before>** `ntext` 將會失敗，並出現下列 SQLOLEDB 錯誤描述：</span><span class="sxs-lookup"><span data-stu-id="9ff79-123">For example, the use of "[Serializable]" in the **\<before>** block of an updategrams when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9ff79-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ff79-124">See Also</span></span>  
 [<span data-ttu-id="9ff79-125">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="9ff79-125">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
