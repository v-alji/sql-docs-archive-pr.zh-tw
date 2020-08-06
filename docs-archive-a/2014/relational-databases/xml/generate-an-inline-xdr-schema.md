---
title: 產生內嵌 XDR 結構描述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e2bb7b4b482b79ab5550540dd5b24ffdd8d6636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710434"
---
# <a name="generate-an-inline-xdr-schema"></a><span data-ttu-id="b2e0c-102">產生內嵌 XDR 結構描述</span><span class="sxs-lookup"><span data-stu-id="b2e0c-102">Generate an Inline XDR Schema</span></span>
  <span data-ttu-id="b2e0c-103">FOR XML 中的 **XMLDATA** 指示詞會將內嵌 XDR 結構描述連同查詢結果一起傳回。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-103">The **XMLDATA** directive in FOR XML returns an inline XDR schema together with the query result.</span></span> <span data-ttu-id="b2e0c-104">不過，XDR 結構描述並不支援 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更新版本中引進的所有新資料類型和其他的增強功能。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-104">However, the XDR schema does not support all the new data types and other enhancements introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="b2e0c-105">您可以改用 [XMLSCHEMA 指示詞](generate-an-inline-xsd-schema.md)來要求內嵌 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-105">Instead, you can request an inline XSD schema by using [the XMLSCHEMA directive](generate-an-inline-xsd-schema.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b2e0c-106">FOR XML 選項的 XMLDATA 指示詞已被取代。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-106">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="b2e0c-107">在 RAW 和 AUTO 模式的情況下，請使用 XSD 產生。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-107">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="b2e0c-108">EXPLICIT 模式中沒有 XMLDATA 指示詞的替代項目。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-108">There is no replacement for the XMLDATA directive in EXPLICIT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="b2e0c-109">也請注意下列有關於內嵌 XDR 結構描述支援的項目：</span><span class="sxs-lookup"><span data-stu-id="b2e0c-109">Also note the following about the inline XDR schema support:</span></span>  
  
-   <span data-ttu-id="b2e0c-110">如果 FOR XML 查詢結果包含 **xml** 類型的資料行，而且您要求內嵌 XDR 結構描述，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-110">If the FOR XML query result includes columns of **xml** type and you request an inline XDR schema, an error is returned.</span></span> <span data-ttu-id="b2e0c-111">內嵌 XDR 並不支援這些類型。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-111">Inline XDR does not support these types.</span></span>  
  
-   <span data-ttu-id="b2e0c-112">**(n)varchar(max)** 和 **(n)varbinary(max)** 類型會分別對應到 **(n)varchar(n)** 和 **varbinary(n)** 。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-112">The **(n)varchar(max)** and **(n)varbinary(max)** types will be mapped to **(n)varchar(n)** and **varbinary(n)**, respectively.</span></span>  
  
-   <span data-ttu-id="b2e0c-113">當相容性模式設定為 90 或更高時， **timestamp** 值會被視為 **varbinary(8)** 資料並當作二進位資料來處理，且會在結果中傳回，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2e0c-113">When compatibility mode is set to 90 or higher, **timestamp** values are considered as **varbinary(8)** data, are treated like binary data, and are returned in the result as follows:</span></span>  
  
    -   <span data-ttu-id="b2e0c-114">如果指定了 **binary base64** ，則會使用 Base 64 編碼。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-114">Base 64 encoding is used when **binary base64** is specified.</span></span>  
  
    -   <span data-ttu-id="b2e0c-115">如果未指定 **binary base64** ，則在 AUTO 模式中會使用 URL 編碼。</span><span class="sxs-lookup"><span data-stu-id="b2e0c-115">URL encoding is used in AUTO mode when **binary base64** is not specified.</span></span>  
  
  
