---
title: " (DTA) 的 Server 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab67e0303c2b629c3774886441474f5ef5b10a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598095"
---
# <a name="server-element-dta"></a><span data-ttu-id="d8ba3-102">Server 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="d8ba3-102">Server Element (DTA)</span></span>
  <span data-ttu-id="d8ba3-103">包含您要微調的資料庫所在之伺服器的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-103">Contains the identifying information for the server on which the databases reside that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ba3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8ba3-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d8ba3-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="d8ba3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d8ba3-106">特性</span><span class="sxs-lookup"><span data-stu-id="d8ba3-106">Characteristic</span></span>|<span data-ttu-id="d8ba3-107">描述</span><span class="sxs-lookup"><span data-stu-id="d8ba3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d8ba3-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="d8ba3-108">**Data type and length**</span></span>|<span data-ttu-id="d8ba3-109">無。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-109">None.</span></span>|  
|<span data-ttu-id="d8ba3-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="d8ba3-110">**Default value**</span></span>|<span data-ttu-id="d8ba3-111">無。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-111">None.</span></span>|  
|<span data-ttu-id="d8ba3-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="d8ba3-112">**Occurrence**</span></span>|<span data-ttu-id="d8ba3-113">(必要) 每個 `DTAInput` 元素出現一次。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-113">Required once per `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d8ba3-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="d8ba3-114">Element Relationships</span></span>  
  
|<span data-ttu-id="d8ba3-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="d8ba3-115">Relationship</span></span>|<span data-ttu-id="d8ba3-116">元素</span><span class="sxs-lookup"><span data-stu-id="d8ba3-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d8ba3-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="d8ba3-117">**Parent element**</span></span>|[<span data-ttu-id="d8ba3-118">DTAInput 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d8ba3-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="d8ba3-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="d8ba3-119">**Child elements**</span></span>|[<span data-ttu-id="d8ba3-120">伺服器的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d8ba3-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="d8ba3-121">伺服器的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d8ba3-121">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="d8ba3-122">備註</span><span class="sxs-lookup"><span data-stu-id="d8ba3-122">Remarks</span></span>  
 <span data-ttu-id="d8ba3-123">您只能 `Server` 為元素指定一個元素 `DTAInput` 。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-123">You can specify only one `Server` element for the `DTAInput` element.</span></span> <span data-ttu-id="d8ba3-124">在 DTA XML 結構描述中，這個元素是 **ServerDetailsTypecomplexType** 名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-124">This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema.</span></span> <span data-ttu-id="d8ba3-125">請勿混淆這個 `Server` 元素和 `Configuration` 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-125">Do not confuse this `Server` element with the one that is the child of the `Configuration` element.</span></span> <span data-ttu-id="d8ba3-126">如需詳細資訊，請參閱[組態的 Server 元素 &#40;DTA&#41;](server-element-for-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ba3-126">For more information, see [Server Element for Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8ba3-127">範例</span><span class="sxs-lookup"><span data-stu-id="d8ba3-127">Example</span></span>  
 <span data-ttu-id="d8ba3-128">下列範例顯示如何在 SERVER001 的 **AdventureWorks** 資料庫中，指定 **Sales.SalesPerson** 資料表：</span><span class="sxs-lookup"><span data-stu-id="d8ba3-128">The following example shows how to specify the **Sales.SalesPerson** table in the **AdventureWorks** database on SERVER001:</span></span>  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8ba3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ba3-129">See Also</span></span>  
 [<span data-ttu-id="d8ba3-130">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="d8ba3-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
