---
title: '&lt;xsd:redefine&gt; 項目 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: rothja
ms.author: jroth
ms.openlocfilehash: ce439e81cf87e97b4afe6e25a201e1ab0cb2a458
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703962"
---
# <a name="the-ltxsdredefinegt-element"></a><span data-ttu-id="cc35d-102">&lt;xsd:redefine&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="cc35d-102">The &lt;xsd:redefine&gt; Element</span></span>
  <span data-ttu-id="cc35d-103">W3C XSD **redefine** 元素支援重新定義結構描述的元件。</span><span class="sxs-lookup"><span data-stu-id="cc35d-103">The W3C XSD **redefine** element provides support for redefining schema components.</span></span> <span data-ttu-id="cc35d-104">不過，對此指示詞的支援可能會耗用很高的效能，而且也需要重新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證 `xml` 與重新定義的架構相關聯之資料類型的所有實例。</span><span class="sxs-lookup"><span data-stu-id="cc35d-104">However, support for this directive is potentially costly to performance and also requires that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalidate all instances of the `xml` data type associated with the redefined schema.</span></span> <span data-ttu-id="cc35d-105">因此， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援此元素。</span><span class="sxs-lookup"><span data-stu-id="cc35d-105">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support this element.</span></span> <span data-ttu-id="cc35d-106">伺服器將會拒絕包含 **\<xsd:redefine>** 元素的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="cc35d-106">XML schemas that include the **\<xsd:redefine>** element are rejected by the server.</span></span>  
  
 <span data-ttu-id="cc35d-107">若要更新結構描述或是其元件，您可以改為執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cc35d-107">To update a schema or its components, you can do the following instead:</span></span>  
  
1.  <span data-ttu-id="cc35d-108">使用修改過的結構描述元件建立新的 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="cc35d-108">Create a new XML Schema collection with the modified schema components.</span></span>  
  
2.  <span data-ttu-id="cc35d-109">重新輸入可使用要重新定義之 XML 結構描述集合的所有 `xml` 資料類型 (XML DT)，以改用新的 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="cc35d-109">Retype all `xml` data types (XML DT) that use the XML Schema collection to be redefined to use the new XML Schema collection instead.</span></span> <span data-ttu-id="cc35d-110">若要這樣做，請使用 ALTER TABLE 命令的 ALTER COLUMN 選項來重新輸入資料行，或是變更變數或參數上的 XML 結構描述集合條件約束。</span><span class="sxs-lookup"><span data-stu-id="cc35d-110">To do this, use the ALTER COLUMN option of the ALTER TABLE command for retyping columns, or change the XML Schema collection constraints on variables or parameters.</span></span>  
  
3.  <span data-ttu-id="cc35d-111">捨棄舊版的 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="cc35d-111">Drop the old version of the XML Schema collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc35d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc35d-112">See Also</span></span>  
 [<span data-ttu-id="cc35d-113">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="cc35d-113">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
