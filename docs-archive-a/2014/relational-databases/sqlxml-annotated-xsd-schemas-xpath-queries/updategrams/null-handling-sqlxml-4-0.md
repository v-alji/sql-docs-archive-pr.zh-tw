---
title: Null 處理 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597747"
---
# <a name="null-handling-sqlxml-40"></a><span data-ttu-id="6fae5-102">NULL 處理 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6fae5-102">NULL Handling (SQLXML 4.0)</span></span>
  <span data-ttu-id="6fae5-103">XML 語法表示 NULL 不存在 </span><span class="sxs-lookup"><span data-stu-id="6fae5-103">XML syntax denotes NULL as an absence.</span></span> <span data-ttu-id="6fae5-104"> (例如，如果屬性或專案值為 Null，則 XML 檔中不存在該屬性或元素。在 SQLXML 中 ) [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ， `updg:nullvalue` 屬性可為元素或屬性值指定 Null。</span><span class="sxs-lookup"><span data-stu-id="6fae5-104">(For example, if an attribute or element value is NULL, that attribute or element is absent from the XML document.) In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, the `updg:nullvalue` attribute enables specifying NULL for an element or attribute value.</span></span>  
  
 <span data-ttu-id="6fae5-105">例如，下列 updategram 可確保**ContactID**為64之連絡人的**標題**值為 Null，然後將**標題**值更新為「Mr」。</span><span class="sxs-lookup"><span data-stu-id="6fae5-105">For example, the following updategram ensures that the **Title** value for a contact with **ContactID** of 64 is NULL, and then updates the **Title** value to "Mr."</span></span> <span data-ttu-id="6fae5-106">。</span><span class="sxs-lookup"><span data-stu-id="6fae5-106">for this contact.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="6fae5-107">當參數傳遞到 Updategram 時，NULL 可以當做參數值傳遞。</span><span class="sxs-lookup"><span data-stu-id="6fae5-107">When parameters are passed to an updategram, NULL can be passed as the parameter value.</span></span> <span data-ttu-id="6fae5-108">這可以透過指定 `nullvalue` 區塊中的 `<updg:header>` 屬性完成。</span><span class="sxs-lookup"><span data-stu-id="6fae5-108">This is done by specifying the `nullvalue` attribute in the `<updg:header>` block.</span></span> <span data-ttu-id="6fae5-109">如需範例，請參閱[將參數傳遞至 updategram &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="6fae5-109">For an example, see [Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fae5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fae5-110">See Also</span></span>  
 [<span data-ttu-id="6fae5-111">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="6fae5-111">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
