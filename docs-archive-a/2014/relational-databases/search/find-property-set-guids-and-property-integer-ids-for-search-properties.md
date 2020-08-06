---
title: 尋找搜尋屬性的屬性集 GUID 與屬性整數識別碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], configuring
ms.assetid: 7db79165-8bcc-4be6-8d40-12d44deda79f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53c08d3a2f86c7e412fbdb1caa6d55d7d23bf407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700978"
---
# <a name="find-property-set-guids-and-property-integer-ids-for-search-properties"></a><span data-ttu-id="33021-102">尋找搜尋屬性的屬性集 GUID 與屬性整數識別碼</span><span class="sxs-lookup"><span data-stu-id="33021-102">Find Property Set GUIDs and Property Integer IDs for Search Properties</span></span>
  <span data-ttu-id="33021-103">本主題將討論如何取得將屬性加入至搜尋屬性清單，使全文檢索搜尋能夠進行搜尋所需的值。</span><span class="sxs-lookup"><span data-stu-id="33021-103">This topic discusses how to obtain the values that are required before you can add a property to a search property list and make it searchable by full-text search.</span></span> <span data-ttu-id="33021-104">這些值包括文件屬性的屬性集 GUID 和屬性整數識別碼。</span><span class="sxs-lookup"><span data-stu-id="33021-104">These values include the property set GUID and property integer identifier of a document property.</span></span>  
  
 <span data-ttu-id="33021-105">Ifilter 從二進位資料（也就是儲存在中的資料 `varbinary` `varbinary(max)` (，包括 `FILESTREAM`) 或資料類型資料行）所解壓縮的檔案屬性， `image` 可供全文檢索搜尋使用。</span><span class="sxs-lookup"><span data-stu-id="33021-105">Document properties that are extracted by IFilters from binary data - that is, from data stored in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` data type column - can be made available for full-text search.</span></span> <span data-ttu-id="33021-106">若要使擷取的屬性可搜尋，則必須手動將屬性加入至搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="33021-106">To make an extracted property searchable, the property must be manually added to a search property list.</span></span> <span data-ttu-id="33021-107">同時，搜尋屬性清單必須與一個或多個全文檢索索引產生關聯。</span><span class="sxs-lookup"><span data-stu-id="33021-107">The search property list must also be associated with one or more full-text indexes.</span></span> <span data-ttu-id="33021-108">如需詳細資訊，請參閱 [使用搜索屬性清單搜索文件屬性](search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="33021-108">For more information, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="33021-109">在屬性清單中加入可用屬性之前，您必須先找到有關屬性的兩項資訊：</span><span class="sxs-lookup"><span data-stu-id="33021-109">Before you can add an available property to a property list, you have to find 2 pieces of information about the property:</span></span>  
  
-   <span data-ttu-id="33021-110">屬性的屬性集 GUID。</span><span class="sxs-lookup"><span data-stu-id="33021-110">The property set GUID of the property.</span></span>  
  
-   <span data-ttu-id="33021-111">屬性的整數識別碼。</span><span class="sxs-lookup"><span data-stu-id="33021-111">The integer ID of the property.</span></span>  
  
 <span data-ttu-id="33021-112">(您將屬性加入至屬性清單時，也要提供名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="33021-112">(When you add a property to a property list, you also have to provide a name and description.</span></span> <span data-ttu-id="33021-113">不過，您不必使用屬性的正式名稱和描述)。</span><span class="sxs-lookup"><span data-stu-id="33021-113">However you do not have to use the canonical name and description of the property.)</span></span>  
  
 <span data-ttu-id="33021-114">本主題描述尋找可用屬性相關資訊的常用方法，尤其是有關 Microsoft 所定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-114">This topic describes the commonly-used methods to find information about available properties, especially about properties that are defined by Microsoft.</span></span> <span data-ttu-id="33021-115">如需有關協力廠商已定義屬性的詳細資訊，請參閱協力廠商文件集或連絡該廠商。</span><span class="sxs-lookup"><span data-stu-id="33021-115">For information about properties that have been defined by a third party, refer to the third-party documentation or contact the vendor.</span></span>  
  
##  <a name="finding-information-about-widely-used-well-known-microsoft-properties"></a><a name="wellknown"></a> <span data-ttu-id="33021-116">尋找廣泛使用之已知 Microsoft 屬性的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33021-116">Finding Information about Widely Used, Well-Known Microsoft Properties</span></span>  
 <span data-ttu-id="33021-117">Microsoft 定義了數百個文件屬性可用於許多內容，但是每一種檔案格式只會使用其中一小部分可用屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-117">Microsoft defines hundreds of document properties for use in many contexts, but only a small subset of the available properties are used by each file format.</span></span> <span data-ttu-id="33021-118">常用的 Windows 屬性包括少數泛型屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-118">Among the frequently used Windows properties is a small set of generic properties.</span></span> <span data-ttu-id="33021-119">下表將顯示已知泛型屬性的部分範例。</span><span class="sxs-lookup"><span data-stu-id="33021-119">Some examples of well-known generic properties are shown in the following table.</span></span> <span data-ttu-id="33021-120">下表顯示了已知名稱、Windows 正式名稱 (根據 Microsoft 發行的屬性描述)、屬性集 GUID、屬性整數識別碼和簡短說明。</span><span class="sxs-lookup"><span data-stu-id="33021-120">The table shows the well-known name, the Windows canonical name (from the property description published by Microsoft), the property set GUID, the property integer identifier, and a brief description.</span></span>  
  
|<span data-ttu-id="33021-121">已知名稱</span><span class="sxs-lookup"><span data-stu-id="33021-121">Well-known name</span></span>|<span data-ttu-id="33021-122">Windows 正式名稱</span><span class="sxs-lookup"><span data-stu-id="33021-122">Windows canonical name</span></span>|<span data-ttu-id="33021-123">屬性集 GUID</span><span class="sxs-lookup"><span data-stu-id="33021-123">Property set GUID</span></span>|<span data-ttu-id="33021-124">整數識別碼</span><span class="sxs-lookup"><span data-stu-id="33021-124">Integer ID</span></span>|<span data-ttu-id="33021-125">描述</span><span class="sxs-lookup"><span data-stu-id="33021-125">Description</span></span>|  
|----------------------|----------------------------|-----------------------|----------------|-----------------|  
|<span data-ttu-id="33021-126">Authors</span><span class="sxs-lookup"><span data-stu-id="33021-126">Authors</span></span>|`System.Author`|<span data-ttu-id="33021-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="33021-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="33021-128">4</span><span class="sxs-lookup"><span data-stu-id="33021-128">4</span></span>|<span data-ttu-id="33021-129">給定項目的一位或多位作者。</span><span class="sxs-lookup"><span data-stu-id="33021-129">Author or authors of a given item.</span></span>|  
|<span data-ttu-id="33021-130">標籤</span><span class="sxs-lookup"><span data-stu-id="33021-130">Tags</span></span>|`System.Keywords`|<span data-ttu-id="33021-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="33021-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="33021-132">5</span><span class="sxs-lookup"><span data-stu-id="33021-132">5</span></span>|<span data-ttu-id="33021-133">指派給項目的關鍵字集合 (也稱為標記)。</span><span class="sxs-lookup"><span data-stu-id="33021-133">Set of keywords (also known as tags) assigned to the item.</span></span>|  
|<span data-ttu-id="33021-134">類型</span><span class="sxs-lookup"><span data-stu-id="33021-134">Type</span></span>|`System.PerceivedType`|<span data-ttu-id="33021-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span><span class="sxs-lookup"><span data-stu-id="33021-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span></span>|<span data-ttu-id="33021-136">9</span><span class="sxs-lookup"><span data-stu-id="33021-136">9</span></span>|<span data-ttu-id="33021-137">以正式類型為基礎的認知檔案類型。</span><span class="sxs-lookup"><span data-stu-id="33021-137">Perceived file type based on its canonical type.</span></span>|  
|<span data-ttu-id="33021-138">Title</span><span class="sxs-lookup"><span data-stu-id="33021-138">Title</span></span>|`System.Title`|<span data-ttu-id="33021-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="33021-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="33021-140">2</span><span class="sxs-lookup"><span data-stu-id="33021-140">2</span></span>|<span data-ttu-id="33021-141">項目的標題。</span><span class="sxs-lookup"><span data-stu-id="33021-141">Title of the item.</span></span> <span data-ttu-id="33021-142">例如文件的標題、郵件的主旨、相片的標題或音樂曲目的名稱。</span><span class="sxs-lookup"><span data-stu-id="33021-142">For example, the title of a document, the subject of a message, the caption of a photo, or the name of a music track.</span></span>|  
  
 <span data-ttu-id="33021-143">為了鼓勵檔案格式的一致性，Microsoft 已經針對許多文件類別識別了常用且高優先順序的文件屬性子集。</span><span class="sxs-lookup"><span data-stu-id="33021-143">To encourage consistency among file formats, Microsoft has identified subsets of frequently used, high-priority document properties for several categories of documents.</span></span> <span data-ttu-id="33021-144">這些類別包括通訊、連絡人、文件、音樂檔案、圖片和視訊。</span><span class="sxs-lookup"><span data-stu-id="33021-144">These include communications, contacts, documents, music files, pictures, and videos.</span></span> <span data-ttu-id="33021-145">如需每個類別目錄前幾項排名屬性的詳細資訊，請參閱 Windows Search 文件集中的 [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) (自訂檔案格式的系統定義屬性)。</span><span class="sxs-lookup"><span data-stu-id="33021-145">For more information about the top-ranked properties for each category, see [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="33021-146">特定檔案格式可能會實作三種類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="33021-146">A specific file format might implement properties of three types:</span></span>  
  
-   <span data-ttu-id="33021-147">[!INCLUDE[msCoName](../../includes/msconame-md.md)]定義的泛型屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-147">Generic properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="33021-148">[!INCLUDE[msCoName](../../includes/msconame-md.md)]定義的特定類別目錄屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-148">Category-specific properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="33021-149">軟體廠商定義的自訂、應用程式專用屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-149">Custom, application-specific properties defined by the software vendor.</span></span>  
  
##  <a name="finding-information-about-available-properties-by-using-filtdumpexe"></a><a name="filtdump"></a> <span data-ttu-id="33021-150">使用 FILTDUMP.EXE 尋找可用屬性的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33021-150">Finding Information about Available Properties by using FILTDUMP.EXE</span></span>  
 <span data-ttu-id="33021-151">若要了解已安裝之 IFilter 所找到和擷取的屬性，您可以安裝並執行 **filtdump.exe** 公用程式 (屬於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK 的一部分)。</span><span class="sxs-lookup"><span data-stu-id="33021-151">To learn what properties are discovered and extracted by an installed IFilter, you can install and run the **filtdump.exe** utility, which is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK.</span></span>  
  
 <span data-ttu-id="33021-152">您可以從命令提示字元執行 **filtdump.exe** ，並提供單一引數。</span><span class="sxs-lookup"><span data-stu-id="33021-152">You run **filtdump.exe** from the command prompt and provide a single argument.</span></span> <span data-ttu-id="33021-153">此引數是個別檔案的名稱，而該檔案具有已安裝 IFilter 的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="33021-153">This argument is the name of an individual file that has a file type for which an IFilter is installed.</span></span> <span data-ttu-id="33021-154">此公用程式顯示文件中 IFilter 所找到之所有屬性的清單，還包含其屬性集 GUID、整數識別碼和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="33021-154">The utility displays a list of all the properties discovered by the IFilter in the document, with their property set GUIDs, integer IDs, and additional information.</span></span>  
  
 <span data-ttu-id="33021-155">如需安裝此軟體的相關資訊，請參閱 [Microsoft Windows SDK for Windows 7 和 .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279)。</span><span class="sxs-lookup"><span data-stu-id="33021-155">For information about installing this software, see [Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279).</span></span> <span data-ttu-id="33021-156">在您下載並安裝 SDK 之後，請查看下列資料夾中是否有 filtdump.exe 公用程式。</span><span class="sxs-lookup"><span data-stu-id="33021-156">After you download and install the SDK, look in the following folders for the filtdump.exe utility.</span></span>  
  
-   <span data-ttu-id="33021-157">針對 64 位版本，請查看 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`。</span><span class="sxs-lookup"><span data-stu-id="33021-157">For the 64-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`.</span></span>  
  
-   <span data-ttu-id="33021-158">針對 32 位版本，請查看 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`。</span><span class="sxs-lookup"><span data-stu-id="33021-158">For the 32-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`.</span></span>  
  
##  <a name="finding-values-for-a-search-property-from-a-windows-property-description"></a><a name="propdesc"></a><span data-ttu-id="33021-159">從 Windows 屬性描述尋找搜尋屬性的值</span><span class="sxs-lookup"><span data-stu-id="33021-159">Finding Values for a Search Property from a Windows Property Description</span></span>  
 <span data-ttu-id="33021-160">若為已知的 Windows 搜尋屬性 (Property)，您可以從屬性 (Property) 描述 (`formatID`) 的 `propID` 和 `propertyDescription` 屬性 (Attribute) 取得您需要的這項資訊。</span><span class="sxs-lookup"><span data-stu-id="33021-160">For a well-known Windows search property, you can obtain the information that you need from the `formatID` and `propID` attributes of the property description (`propertyDescription`).</span></span>  
  
 <span data-ttu-id="33021-161">下列範例將顯示一般 Microsoft 屬性描述的相關部分 (以 `System.Author` 屬性為例)。</span><span class="sxs-lookup"><span data-stu-id="33021-161">The following example shows the relevant part of a typical Microsoft property description, in this case, of the `System.Author` property.</span></span> <span data-ttu-id="33021-162">`formatID` 屬性 (Attribute) 會指定屬性 (Property) 集 GUID `F29F85E0-4FF9-1068-AB91-08002B27B3D9`，而 `propID` 屬性 (Attribute) 會指定屬性 (Property) 整數識別碼 `4.` 。請注意， `name` 屬性 (Attribute) 會指定 Windows 正式屬性 (Property) 名稱 `System.Author`</span><span class="sxs-lookup"><span data-stu-id="33021-162">The `formatID` attribute specifies the property set GUID, `F29F85E0-4FF9-1068-AB91-08002B27B3D9`, and the `propID` attribute specifies the property integer ID, `4.` Notice that the `name` attribute specifies the Windows canonical property name, `System.Author`.</span></span> <span data-ttu-id="33021-163">(這個範例省略了屬性描述中不相關的部分)。</span><span class="sxs-lookup"><span data-stu-id="33021-163">(This example omits portions of the property description that are not relevant.)</span></span>  
  
```  
.  
propertyDescription  
name = System.Author  
...  
formatID = F29F85E0-4FF9-1068-AB91-08002B27B3D9  
propID = 4  
...  
```  
  
 <span data-ttu-id="33021-164">如需此屬性的完整描述，請參閱 Windows Search 文件集中的 [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) 。</span><span class="sxs-lookup"><span data-stu-id="33021-164">For the complete description of this property, see [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="33021-165">如需 Windows 屬性的完整清單，請參閱同樣在 Windows Search 文件集中的 [Windows Properties](https://go.microsoft.com/fwlink/?LinkId=215013)Windows 屬性)。</span><span class="sxs-lookup"><span data-stu-id="33021-165">For a complete list of Windows properties, see [Windows Properties](https://go.microsoft.com/fwlink/?LinkId=215013), also in the Windows Search documentation.</span></span>  
  
##  <a name="adding-a-property-to-a-search-property-list"></a><a name="examples"></a><span data-ttu-id="33021-166">將屬性加入至搜尋屬性清單</span><span class="sxs-lookup"><span data-stu-id="33021-166">Adding a Property to a Search Property List</span></span>  
 <span data-ttu-id="33021-167">下列範例示範如何將屬性加入至搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="33021-167">The following example shows how to add a property to a search property list.</span></span> <span data-ttu-id="33021-168">此範例會使用 [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) 陳述式將 `System.Author` 屬性加入名為 `PropertyList1`的搜尋屬性清單，並且為屬性提供使用者易記名稱 `Author`。</span><span class="sxs-lookup"><span data-stu-id="33021-168">The example uses an [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add the `System.Author` property to a search property list named `PropertyList1`, and provides a user friendly name for the property, `Author`.</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST PropertyList1   
  ADD 'Author'  
    WITH (  
          PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',  
          PROPERTY_INT_ID = 4,   
          PROPERTY_DESCRIPTION = 'System.Author - the author or authors of the item'   
         )  
GO  
```  
  
 <span data-ttu-id="33021-169">如需建立搜尋屬性清單並將它與全文檢索索引產生關聯的詳細資訊，請參閱 [使用搜索屬性清單搜索文件屬性](search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="33021-169">For more information about creating a search property list and associating it with a full-text index, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33021-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33021-170">See Also</span></span>  
 <span data-ttu-id="33021-171">[使用搜尋屬性清單搜尋文件屬性](search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="33021-171">[Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="33021-172">設定及管理搜尋的篩選</span><span class="sxs-lookup"><span data-stu-id="33021-172">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
