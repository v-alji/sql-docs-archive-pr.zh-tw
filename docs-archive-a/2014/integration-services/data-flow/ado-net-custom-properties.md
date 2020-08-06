---
title: ADO NET 自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bada6f512770d0f9f07ddc3693070c8aad309cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687095"
---
# <a name="ado-net-custom-properties"></a><span data-ttu-id="c7cee-102">ADO NET 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="c7cee-102">ADO NET Custom Properties</span></span>
  <span data-ttu-id="c7cee-103">**來源自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="c7cee-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="c7cee-104">ADO NET 來源同時具有自訂屬性以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-104">The ADO NET source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="c7cee-105">下表將描述 ADO NET 來源的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-105">The following table describes the custom properties of the ADO NET source.</span></span> <span data-ttu-id="c7cee-106">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="c7cee-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="c7cee-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c7cee-107">Property name</span></span>|<span data-ttu-id="c7cee-108">資料類型</span><span class="sxs-lookup"><span data-stu-id="c7cee-108">Data Type</span></span>|<span data-ttu-id="c7cee-109">描述</span><span class="sxs-lookup"><span data-stu-id="c7cee-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="c7cee-110">CommandTimeout</span><span class="sxs-lookup"><span data-stu-id="c7cee-110">CommandTimeout</span></span>|<span data-ttu-id="c7cee-111">String</span><span class="sxs-lookup"><span data-stu-id="c7cee-111">String</span></span>|<span data-ttu-id="c7cee-112">一個值，指定 SQL 命令逾時之前的秒數。值為 0 表示此命令永遠不會逾時。</span><span class="sxs-lookup"><span data-stu-id="c7cee-112">A value that specifies the number of seconds before the SQL command times out. A value of 0 indicates that the command never times out.</span></span>|  
|<span data-ttu-id="c7cee-113">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="c7cee-113">SqlCommand</span></span>|<span data-ttu-id="c7cee-114">String</span><span class="sxs-lookup"><span data-stu-id="c7cee-114">String</span></span>|<span data-ttu-id="c7cee-115">ADO NET 來源用來擷取資料的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7cee-115">The SQL statement that the ADO NET source uses to extract data.</span></span><br /><br /> <span data-ttu-id="c7cee-116">載入封裝時，您可以使用 ADO NET 來源即將使用的 SQL 陳述式，以動態方式更新此屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-116">When the package loads, you can dynamically update this property with the SQL statement that the ADO NET source will use.</span></span> <span data-ttu-id="c7cee-117">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md)和[在封裝中使用屬性運算式](../expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="c7cee-117">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>|  
|<span data-ttu-id="c7cee-118">AllowImplicitStringConversion</span><span class="sxs-lookup"><span data-stu-id="c7cee-118">AllowImplicitStringConversion</span></span>|<span data-ttu-id="c7cee-119">Boolean</span><span class="sxs-lookup"><span data-stu-id="c7cee-119">Boolean</span></span>|<span data-ttu-id="c7cee-120">指出是否會發生下列情況的值：</span><span class="sxs-lookup"><span data-stu-id="c7cee-120">A value that indicates whether the following occurs:</span></span><br /><br /> <span data-ttu-id="c7cee-121">如果外部中繼資料類型與屬於字串 (DT_WSTR 或 DT_NTEXT) 的輸出資料行類型之間具有不符項目，就不會產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7cee-121">No generation of a validation error if there is a mismatch between external metadata types and output column types that are strings (DT_WSTR or DT_NTEXT).</span></span><br /><br /> <span data-ttu-id="c7cee-122">將外部中繼資料類型隱含轉換成輸出資料行所使用的字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="c7cee-122">Implicit conversion of external metadata types to the string data type that the output column uses.</span></span><br /><br /> <br /><br /> <span data-ttu-id="c7cee-123">預設值為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c7cee-123">The default value is TRUE.</span></span><br /><br /> <span data-ttu-id="c7cee-124">如需詳細資訊，請參閱 [ADO NET 來源](ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="c7cee-124">For more information, see [ADO NET Source](ado-net-source.md).</span></span>|  
  
 <span data-ttu-id="c7cee-125">ADO NET 來源的輸出和輸出資料行沒有任何自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-125">The output and the output columns of the ADO NET source have no custom properties.</span></span>  
  
 <span data-ttu-id="c7cee-126">如需詳細資訊，請參閱 [ADO NET 來源](ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="c7cee-126">For more information, see [ADO NET Source](ado-net-source.md).</span></span>  
  
 <span data-ttu-id="c7cee-127">**目的地自訂屬性**</span><span class="sxs-lookup"><span data-stu-id="c7cee-127">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="c7cee-128">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目的地同時具有自訂屬性，以及所有資料流程元件通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-128">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="c7cee-129">下表描述 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目的地的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-129">The following table describes the custom properties of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination.</span></span> <span data-ttu-id="c7cee-130">所有屬性都是可讀寫的。</span><span class="sxs-lookup"><span data-stu-id="c7cee-130">All properties are read/write.</span></span> <span data-ttu-id="c7cee-131">雖然您無法在 [ADO NET 目的地編輯器]  中使用這些屬性，但是可以使用 [進階編輯器]  來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="c7cee-131">These properties are not available in the **ADO NET Destination Editor**, but can be set by using the **Advanced Editor**.</span></span>  
  
|<span data-ttu-id="c7cee-132">屬性</span><span class="sxs-lookup"><span data-stu-id="c7cee-132">Property</span></span>|<span data-ttu-id="c7cee-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="c7cee-133">Data Type</span></span>|<span data-ttu-id="c7cee-134">描述</span><span class="sxs-lookup"><span data-stu-id="c7cee-134">Description</span></span>|  
|--------------|---------------|-----------------|  
|<span data-ttu-id="c7cee-135">BatchSize</span><span class="sxs-lookup"><span data-stu-id="c7cee-135">BatchSize</span></span>|<span data-ttu-id="c7cee-136">整數</span><span class="sxs-lookup"><span data-stu-id="c7cee-136">Integer</span></span>|<span data-ttu-id="c7cee-137">傳送給伺服器之批次內的資料列數。</span><span class="sxs-lookup"><span data-stu-id="c7cee-137">The number of rows in a batch that is sent to the server.</span></span> <span data-ttu-id="c7cee-138">值為 **0** 表示批次大小與內部緩衝區大小相符。</span><span class="sxs-lookup"><span data-stu-id="c7cee-138">A value of **0** indicates that the batch size matches the internal buffer size.</span></span> <span data-ttu-id="c7cee-139">這個屬性的預設值為 **0**。</span><span class="sxs-lookup"><span data-stu-id="c7cee-139">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="c7cee-140">CommandTimeout</span><span class="sxs-lookup"><span data-stu-id="c7cee-140">CommandTimeOut</span></span>|<span data-ttu-id="c7cee-141">整數</span><span class="sxs-lookup"><span data-stu-id="c7cee-141">Integer</span></span>|<span data-ttu-id="c7cee-142">逾時之前 SQL 命令可以執行的秒數上限。值為 **0** 指出無限的時間。</span><span class="sxs-lookup"><span data-stu-id="c7cee-142">The maximum number of seconds that the SQL command can run before timing out. A value of **0** indicates an infinite time.</span></span> <span data-ttu-id="c7cee-143">這個屬性的預設值為 **0**。</span><span class="sxs-lookup"><span data-stu-id="c7cee-143">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="c7cee-144">TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="c7cee-144">TableOrViewName</span></span>|<span data-ttu-id="c7cee-145">String</span><span class="sxs-lookup"><span data-stu-id="c7cee-145">String</span></span>|<span data-ttu-id="c7cee-146">目的地資料表或檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7cee-146">The name of the destination table or view.</span></span>|  
  
 <span data-ttu-id="c7cee-147">如需詳細資訊，請參閱 [ADO NET 目的地](ado-net-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="c7cee-147">For more information, see [ADO NET Destination](ado-net-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cee-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7cee-148">See Also</span></span>  
 [<span data-ttu-id="c7cee-149">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c7cee-149">Common Properties</span></span>](../common-properties.md)  
  
  
