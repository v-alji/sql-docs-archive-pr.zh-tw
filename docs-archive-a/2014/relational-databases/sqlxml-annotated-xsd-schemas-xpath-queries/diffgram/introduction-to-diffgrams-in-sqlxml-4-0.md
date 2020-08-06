---
title: SQLXML 4.0 中的 Diffgram 簡介 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: rothja
ms.author: jroth
ms.openlocfilehash: e57d87d064ace47247f342ed002b162b920e627f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596592"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a><span data-ttu-id="d6936-102">DiffGrams 的 SQLXML 4.0 簡介</span><span class="sxs-lookup"><span data-stu-id="d6936-102">Introduction to DiffGrams in SQLXML 4.0</span></span>
  <span data-ttu-id="d6936-103">本主題提供 DiffGram 的簡介。</span><span class="sxs-lookup"><span data-stu-id="d6936-103">This topic provides a brief introduction to DiffGrams.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="d6936-104">DiffGram 格式</span><span class="sxs-lookup"><span data-stu-id="d6936-104">DiffGram Format</span></span>  
 <span data-ttu-id="d6936-105">這是一般 DiffGram 格式：</span><span class="sxs-lookup"><span data-stu-id="d6936-105">This is the general DiffGram format:</span></span>  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="d6936-106">DiffGram 格式由下列區塊組成：</span><span class="sxs-lookup"><span data-stu-id="d6936-106">The DiffGram format consists of these blocks:</span></span>  
  
 **\<DataInstance>**  
 <span data-ttu-id="d6936-107">此元素的名稱**DataInstance**是用於本檔中的說明。</span><span class="sxs-lookup"><span data-stu-id="d6936-107">The name of this element, **DataInstance**, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="d6936-108">例如，如果從 .NET Framework 中的資料集產生 DiffGram，則會使用資料集的**name**屬性值做為此元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6936-108">For example, if the DiffGram were generated from a dataset in the .NET Framework, the value of the **Name** property of the dataset would be used as the name of this element.</span></span> <span data-ttu-id="d6936-109">這個區塊包含變更之後的所有相關資料，可能包括尚未修改的資料。</span><span class="sxs-lookup"><span data-stu-id="d6936-109">This block contains all relevant data after the change, possibly including data that has not been modified.</span></span> <span data-ttu-id="d6936-110">DiffGram 處理邏輯會忽略此區塊中未指定**diffgr： hasChanges**屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="d6936-110">The DiffGram processing logic ignores the elements in this block for which the **diffgr:hasChanges** attribute is not specified.</span></span>  
  
 **\<diffgr:before>**  
 <span data-ttu-id="d6936-111">這個選擇性區塊包含必須更新或刪除的原始記錄執行個體 (元素)。</span><span class="sxs-lookup"><span data-stu-id="d6936-111">This optional block contains the original record instances (elements) that must be updated or deleted.</span></span> <span data-ttu-id="d6936-112">所有要修改的資料庫資料表 (DiffGram 所) 的更新或刪除，都必須在區塊中顯示為最上層的元素 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="d6936-112">All the database tables being modified (updated or deleted) by the DiffGram must appear as top-level elements in the **\<before>** block.</span></span>  
  
 **\<diffgr:errors>**  
 <span data-ttu-id="d6936-113">DiffGram 處理邏輯會忽略這個選擇性區塊。</span><span class="sxs-lookup"><span data-stu-id="d6936-113">This optional block is ignored by the DiffGram processing logic.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="d6936-114">DiffGram 註解</span><span class="sxs-lookup"><span data-stu-id="d6936-114">DiffGram Annotations</span></span>  
 <span data-ttu-id="d6936-115">這些注釋定義于 DiffGram 命名空間 **"urn：架構-microsoft-com： xml-DiffGram-01"** 中：</span><span class="sxs-lookup"><span data-stu-id="d6936-115">These annotations are defined in the DiffGram namespace **"urn:schemas-microsoft-com:xml-diffgram-01"**:</span></span>  
  
 <span data-ttu-id="d6936-116">**id**</span><span class="sxs-lookup"><span data-stu-id="d6936-116">**id**</span></span>  
 <span data-ttu-id="d6936-117">這個屬性是用來配對和區塊中的元素 **\<before>** **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="d6936-117">This attribute is used to pair the elements in the **\<before>** and the **\<DataInstance>** blocks.</span></span>  
  
 <span data-ttu-id="d6936-118">**hasChanges**</span><span class="sxs-lookup"><span data-stu-id="d6936-118">**hasChanges**</span></span>  
 <span data-ttu-id="d6936-119">若為插入或更新作業，DiffGram 必須使用已**插入**或**已修改**的值來指定此屬性。</span><span class="sxs-lookup"><span data-stu-id="d6936-119">For an insert or an update operation, the DiffGram must specify this attribute with the value **inserted** or **modified**.</span></span> <span data-ttu-id="d6936-120">如果這個屬性不存在，處理邏輯會忽略中的對應元素， **\<DataInstance>** 而且不會執行任何更新。</span><span class="sxs-lookup"><span data-stu-id="d6936-120">If this attribute is not present, the corresponding element in the **\<DataInstance>** is ignored by the processing logic and no updates are performed.</span></span> <span data-ttu-id="d6936-121">如需工作範例，請參閱[&#40;SQLXML 4.0&#41;的 DiffGram 範例](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d6936-121">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d6936-122">**parentID**</span><span class="sxs-lookup"><span data-stu-id="d6936-122">**parentID**</span></span>  
 <span data-ttu-id="d6936-123">這個屬性是用來在 DiffGram 的元素之間指定父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="d6936-123">This attribute is used to specify parent-child relationships among the elements in the DiffGram.</span></span> <span data-ttu-id="d6936-124">這個屬性只會出現在 \<before> 區塊中。</span><span class="sxs-lookup"><span data-stu-id="d6936-124">This attribute appears only in the \<before> block.</span></span> <span data-ttu-id="d6936-125">SQLXML 會在套用更新時使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="d6936-125">It is used by SQLXML when applying updates.</span></span> <span data-ttu-id="d6936-126">此父子式關聯性會用於決定處理 DiffGram 中元素的順序。</span><span class="sxs-lookup"><span data-stu-id="d6936-126">The parent-child relationship is used in determining the order in which the elements in the DiffGram are processed.</span></span>  
  
## <a name="understanding-the-diffgram-processing-logic"></a><span data-ttu-id="d6936-127">了解 DiffGram 處理邏輯</span><span class="sxs-lookup"><span data-stu-id="d6936-127">Understanding the DiffGram Processing Logic</span></span>  
 <span data-ttu-id="d6936-128">DiffGram 處理邏輯會使用特定規則來判斷某項作業是插入、更新或刪除作業。</span><span class="sxs-lookup"><span data-stu-id="d6936-128">The DiffGram processing logic uses certain rules to determine whether an operation is an insert, update, or delete operation.</span></span> <span data-ttu-id="d6936-129">下表將描述這些規則。</span><span class="sxs-lookup"><span data-stu-id="d6936-129">These rules are described in the following table.</span></span>  
  
|<span data-ttu-id="d6936-130">作業</span><span class="sxs-lookup"><span data-stu-id="d6936-130">Operation</span></span>|<span data-ttu-id="d6936-131">描述</span><span class="sxs-lookup"><span data-stu-id="d6936-131">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6936-132">Insert</span><span class="sxs-lookup"><span data-stu-id="d6936-132">Insert</span></span>|<span data-ttu-id="d6936-133">當元素出現在 **\<DataInstance>** 區塊中，而不是在對應的 **\<before>** 區塊中，而指定**diffgr： hasChanges**屬性時，DiffGram 表示插入作業， (**diffgr： hasChanges =** 在元素上插入) 。</span><span class="sxs-lookup"><span data-stu-id="d6936-133">A DiffGram indicates an insert operation when an element appears in the **\<DataInstance>** block but not in the corresponding **\<before>** block, and the **diffgr:hasChanges** attribute is specified (**diffgr:hasChanges=inserted**) on the element.</span></span> <span data-ttu-id="d6936-134">在此情況下，DiffGram 會將區塊中指定的記錄實例插入 **\<DataInstance>** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d6936-134">In this case, the DiffGram inserts the record instance that is specified in the **\<DataInstance>** block into the database.</span></span><br /><br /> <span data-ttu-id="d6936-135">如果未指定**diffgr： hasChanges**屬性，處理邏輯會忽略元素，而且不會執行任何插入。</span><span class="sxs-lookup"><span data-stu-id="d6936-135">If the **diffgr:hasChanges** attribute is not specified, the element is ignored by the processing logic and no insert is performed.</span></span> <span data-ttu-id="d6936-136">如需工作範例，請參閱[&#40;SQLXML 4.0&#41;的 DiffGram 範例](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d6936-136">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>|  
|<span data-ttu-id="d6936-137">更新</span><span class="sxs-lookup"><span data-stu-id="d6936-137">Update</span></span>|<span data-ttu-id="d6936-138">在區塊中有一個 (對應專案的區塊中有一個專案時，DiffGram 會指出更新作業 \<before> ，但 **\<DataInstance>** 這兩個專案都具有具有相同值的**diffgr： id**屬性) ，而且**diffgr： hasChanges**屬性是使用在區塊中的專案上**修改**的值所指定 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="d6936-138">The DiffGram indicates an update operation when there is an element in the \<before> block for which there is a corresponding element in the **\<DataInstance>** block (that is, both elements have a **diffgr:id** attribute with same value) and the **diffgr:hasChanges** attribute is specified with the value **modified** on the element in the **\<DataInstance>** block.</span></span><br /><br /> <span data-ttu-id="d6936-139">如果未在區塊的元素上指定**diffgr： hasChanges**屬性 **\<DataInstance>** ，處理邏輯就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6936-139">If the **diffgr:hasChanges** attribute is not specified on the element in the **\<DataInstance>** block, an error is returned by the processing logic.</span></span> <span data-ttu-id="d6936-140">如需工作範例，請參閱[&#40;SQLXML 4.0&#41;的 DiffGram 範例](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d6936-140">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="d6936-141">如果在區塊中指定**diffgr： parentid** **\<before>** ， **parentid**所指定之元素的父子式關聯性會用於判斷記錄的更新順序。</span><span class="sxs-lookup"><span data-stu-id="d6936-141">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are updated.</span></span>|  
|<span data-ttu-id="d6936-142">刪除</span><span class="sxs-lookup"><span data-stu-id="d6936-142">Delete</span></span>|<span data-ttu-id="d6936-143">當元素出現在區塊中， **\<before>** 而不是在對應的區塊中時，DiffGram 表示刪除作業 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="d6936-143">A DiffGram indicates a delete operation when an element appears in the **\<before>** block but not in the corresponding **\<DataInstance>** block.</span></span> <span data-ttu-id="d6936-144">在此情況下，DiffGram 會從資料庫中刪除在區塊中指定的記錄實例 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="d6936-144">In this case, the DiffGram deletes the record instance that is specified in the **\<before>** block from the database.</span></span> <span data-ttu-id="d6936-145">如需工作範例，請參閱[&#40;SQLXML 4.0&#41;的 DiffGram 範例](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d6936-145">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="d6936-146">如果在區塊中指定**diffgr： parentid** **\<before>** ， **parentid**所指定之元素的父子式關聯性會用於判斷刪除記錄的順序。</span><span class="sxs-lookup"><span data-stu-id="d6936-146">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are deleted.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d6936-147">參數無法傳遞給 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="d6936-147">Parameters cannot be passed to DiffGrams.</span></span>  
  
  
