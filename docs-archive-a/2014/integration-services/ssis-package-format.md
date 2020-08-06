---
title: SSIS 封裝格式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 524c65ac5682b8efe8c4191697eb540f9acca82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700009"
---
# <a name="ssis-package-format"></a><span data-ttu-id="e447d-102">SSIS 封裝格式</span><span class="sxs-lookup"><span data-stu-id="e447d-102">SSIS Package Format</span></span>
  <span data-ttu-id="e447d-103">在目前的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]版本中，已經對封裝格式 (.dtsx 檔案) 做了重大變更，讓您更輕鬆地讀取此格式及比較封裝。</span><span class="sxs-lookup"><span data-stu-id="e447d-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], significant changes were made to the package format (.dtsx file) to make it easier to read the format and to compare packages.</span></span> <span data-ttu-id="e447d-104">您也可以更可靠地合併不包含衝突變更的封裝，或以二進位格式儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="e447d-104">You can also more reliably merge packages that don't contain conflicting changes or changes stored in binary format.</span></span>  
  
 <span data-ttu-id="e447d-105">若要查看目前的 .DTSX 封裝檔案格式，請參閱[ \[ .Dtsx \] ：資料轉換服務封裝 XML 檔案格式規格](https://go.microsoft.com/fwlink/?LinkId=233251)。</span><span class="sxs-lookup"><span data-stu-id="e447d-105">To view the current DTSX package file format, see [\[MS-DTSX\]: Data Transformation Services Package XML File Format Specification](https://go.microsoft.com/fwlink/?LinkId=233251).</span></span>  
  
 <span data-ttu-id="e447d-106">下列清單概述檔案格式變更。</span><span class="sxs-lookup"><span data-stu-id="e447d-106">The following list outlines the file format changes.</span></span> <span data-ttu-id="e447d-107">若要檢視這些變更的程式碼範例，請參閱 [SQL Server 2012 中的封裝格式變更](https://go.microsoft.com/fwlink/?LinkId=233255)。</span><span class="sxs-lookup"><span data-stu-id="e447d-107">To view code examples of these changes, see [Package Format Changes in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=233255).</span></span>  
  
-   <span data-ttu-id="e447d-108">已經套用格式化慣例，好讓您更輕鬆地讀取及了解 .dtsx 檔案。</span><span class="sxs-lookup"><span data-stu-id="e447d-108">Formatting conventions have been applied to make it easier to read and understand the .dtsx file.</span></span>  
  
-   <span data-ttu-id="e447d-109">此格式更為精簡。</span><span class="sxs-lookup"><span data-stu-id="e447d-109">The format is more concise.</span></span> <span data-ttu-id="e447d-110">每一個屬性 (Property) 的個別元素已經保存為屬性 (Attribute)，但是 PackageFormatVersion 除外。</span><span class="sxs-lookup"><span data-stu-id="e447d-110">Separate elements for each property have been persisted as attributes, with the exception of the PackageFormatVersion.</span></span> <span data-ttu-id="e447d-111">屬性 (Attribute) 會依照字母順序列出，而且擁有預設值的屬性 (Property) 將不再保存。</span><span class="sxs-lookup"><span data-stu-id="e447d-111">Attributes are listed alphabetically, and properties that have default values are no longer persisted.</span></span> <span data-ttu-id="e447d-112">最後，可出現多次的元素現在包含在父元素中。</span><span class="sxs-lookup"><span data-stu-id="e447d-112">Finally, elements that can appear multiple times, are now contained within a parent element.</span></span>  
  
-   <span data-ttu-id="e447d-113">封裝內可由其他物件參考的大多數物件現在擁有封裝 XML 中所定義的 `refId` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e447d-113">Most objects within a package that can be referred to by other objects now have a `refId` attribute defined in the package XML.</span></span> <span data-ttu-id="e447d-114">現在會保存 `refID`，而不會保存歷程識別碼。</span><span class="sxs-lookup"><span data-stu-id="e447d-114">Instead of persisting lineage IDs, the `refID` is now persisted.</span></span> <span data-ttu-id="e447d-115">歷程識別碼依然會在執行階段內使用，而且載入封裝時會重新產生。</span><span class="sxs-lookup"><span data-stu-id="e447d-115">Lineage IDs are still used within the runtime and regenerated when the package is loaded.</span></span>  
  
     <span data-ttu-id="e447d-116">`refId` 值是可讀取及可了解的唯一字串 (相較於 GUID 或整數值)。</span><span class="sxs-lookup"><span data-stu-id="e447d-116">The `refId` value is a unique string that is readable and understandable, compared to GUIDs or integer values.</span></span> <span data-ttu-id="e447d-117">此字串類似於在舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中用於封裝組態的路徑值。</span><span class="sxs-lookup"><span data-stu-id="e447d-117">The string is similar to path values used for package configurations in previous releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="e447d-118">如果您要合併兩個封裝版本之間的變更，則 `refId` 可用於尋找/取代作業，以確保該物件的所有參考都已經正確更新。</span><span class="sxs-lookup"><span data-stu-id="e447d-118">If you are merging changes between two versions of a package, the `refId` can be used in find/replace operations to ensure that all references to that object have been correctly updated.</span></span>  
  
-   <span data-ttu-id="e447d-119">配置資訊包含在 CData 區段內。</span><span class="sxs-lookup"><span data-stu-id="e447d-119">The layout information is contained in a CData section.</span></span>  
  
-   <span data-ttu-id="e447d-120">註解會以純文字格式保存。</span><span class="sxs-lookup"><span data-stu-id="e447d-120">Annotations are persisted in cleartext.</span></span> <span data-ttu-id="e447d-121">如此可讓您更輕鬆地針對自動產生的文件集擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="e447d-121">This makes it easier to extract the information for automated generation of documentation.</span></span>  
  
  
