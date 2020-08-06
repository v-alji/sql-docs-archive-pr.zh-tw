---
title: 屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599051"
---
# <a name="attributes-master-data-services"></a><span data-ttu-id="a953b-102">屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a953b-102">Attributes (Master Data Services)</span></span>
  <span data-ttu-id="a953b-103">屬性是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 實體中包含的物件。</span><span class="sxs-lookup"><span data-stu-id="a953b-103">Attributes are objects that are contained in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] entities.</span></span> <span data-ttu-id="a953b-104">屬性值描述實體的成員。</span><span class="sxs-lookup"><span data-stu-id="a953b-104">Attribute values describe the members of the entity.</span></span> <span data-ttu-id="a953b-105">屬性可用來描述分葉成員、合併成員或集合。</span><span class="sxs-lookup"><span data-stu-id="a953b-105">An attribute can be used to describe a leaf member, a consolidated member, or a collection.</span></span>  
  
## <a name="how-attributes-relate-to-other-model-objects"></a><span data-ttu-id="a953b-106">屬性如何與其他的模型物件相關聯</span><span class="sxs-lookup"><span data-stu-id="a953b-106">How Attributes Relate to Other Model Objects</span></span>  
 <span data-ttu-id="a953b-107">您可以將屬性視為實體資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="a953b-107">You can think of an attribute as a column in an entity table.</span></span> <span data-ttu-id="a953b-108">屬性值是用來描述特定成員的值。</span><span class="sxs-lookup"><span data-stu-id="a953b-108">An attribute value is the value used to describe a specific member.</span></span>  
  
 <span data-ttu-id="a953b-109">![以資料表表示的 Master Data Services 實體](../../2014/master-data-services/media/mds-conc-entity-table.gif "以資料表表示的 Master Data Services 實體")</span><span class="sxs-lookup"><span data-stu-id="a953b-109">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>  
  
 <span data-ttu-id="a953b-110">當您建立包含多個屬性的實體時，您可以將屬性組織成屬性群組。</span><span class="sxs-lookup"><span data-stu-id="a953b-110">When you create an entity that contains many attributes, you can organize the attributes into attribute groups.</span></span> <span data-ttu-id="a953b-111">如需詳細資訊，請參閱 [屬性群組 &#40;Master Data Services&#41;](attribute-groups-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a953b-111">For more information, see [Attribute Groups &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).</span></span>  
  
## <a name="required-attributes"></a><span data-ttu-id="a953b-112">必要的屬性</span><span class="sxs-lookup"><span data-stu-id="a953b-112">Required Attributes</span></span>  
 <span data-ttu-id="a953b-113">當您建立實體時，會自動建立 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-113">When you create an entity, the Name and Code attributes are automatically created.</span></span> <span data-ttu-id="a953b-114">Code 需要一個值，而且在實體中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a953b-114">Code requires a value and must be unique within the entity.</span></span> <span data-ttu-id="a953b-115">您不能移除 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-115">You cannot remove the Name and Code attributes.</span></span>  
  
## <a name="attribute-types"></a><span data-ttu-id="a953b-116">屬性類型</span><span class="sxs-lookup"><span data-stu-id="a953b-116">Attribute Types</span></span>  
 <span data-ttu-id="a953b-117">屬性有三種類型：</span><span class="sxs-lookup"><span data-stu-id="a953b-117">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="a953b-118">自由格式的屬性，允許以自由格式輸入文字、數字、日期或連結。</span><span class="sxs-lookup"><span data-stu-id="a953b-118">Free-form attributes, which allow free-form input for text, numbers, dates, or links.</span></span>  
  
-   <span data-ttu-id="a953b-119">由實體擴展的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-119">Domain-based attributes, which are populated by entities.</span></span> <span data-ttu-id="a953b-120">如需詳細資訊，請參閱 [網域屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a953b-120">For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a953b-121">檔案屬性，用來儲存檔案、文件或影像。</span><span class="sxs-lookup"><span data-stu-id="a953b-121">File attributes, which are used to store files, documents, or images.</span></span> <span data-ttu-id="a953b-122">檔案屬性透過要求檔案有特定副檔名，有助於資料一致性。</span><span class="sxs-lookup"><span data-stu-id="a953b-122">File attributes are intended to help with the consistency of your data by requiring files to have a specific extension.</span></span> <span data-ttu-id="a953b-123">檔案屬性無法保證能防止惡意使用者上傳不同類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="a953b-123">File attributes cannot be guaranteed to prevent a malicious user from uploading a file of a different type.</span></span>  
  
### <a name="numeric-free-form-attributes"></a><span data-ttu-id="a953b-124">數值的自由格式屬性</span><span class="sxs-lookup"><span data-stu-id="a953b-124">Numeric Free-Form Attributes</span></span>  
 <span data-ttu-id="a953b-125">數值的自由格式屬性需要特殊處理，因為數值的自由格式屬性值僅限於 **SqlDouble** 數值類型。</span><span class="sxs-lookup"><span data-stu-id="a953b-125">Numeric free-form attributes require special handling, because numeric free-form attribute values are limited to the **SqlDouble** value type.</span></span>  
  
 <span data-ttu-id="a953b-126">根據預設，儘管內部最多維護 17 個位數，但 **SqlDouble** 值包含 15 個有效小數位數。</span><span class="sxs-lookup"><span data-stu-id="a953b-126">By default, a **SqlDouble** value contains 15 decimal digits of precision, although a maximum of 17 digits is maintained internally.</span></span> <span data-ttu-id="a953b-127">浮點數的有效位數有數個結果：</span><span class="sxs-lookup"><span data-stu-id="a953b-127">The precision of a floating-point number has several consequences:</span></span>  
  
-   <span data-ttu-id="a953b-128">對特定有效位數相等的兩個浮點數，可能因為它們的最低有效位數不同，而不相等。</span><span class="sxs-lookup"><span data-stu-id="a953b-128">Two floating-point numbers that appear equal for a particular precision might not compare equal because their least significant digits are different.</span></span>  
  
-   <span data-ttu-id="a953b-129">如果因為浮點數可能不完全近似十進位數字，而使用十進位數字，使用浮點數的數學或比較運算可能不會產生相同結果。</span><span class="sxs-lookup"><span data-stu-id="a953b-129">A mathematical or comparison operation that uses a floating-point number might not yield the same result if a decimal number is used because the floating-point number might not exactly approximate the decimal number.</span></span>  
  
-   <span data-ttu-id="a953b-130">如果牽涉到浮點數，值可能無法 *「往返」* (Roundtrip)。</span><span class="sxs-lookup"><span data-stu-id="a953b-130">A value might not *roundtrip* if a floating-point number is involved.</span></span> <span data-ttu-id="a953b-131">如果運算將原始浮點數轉換成另一個形式，反運算將轉換的形式轉換回浮點數，而最終浮點數等於原始浮點數，值稱為往返。</span><span class="sxs-lookup"><span data-stu-id="a953b-131">A value is said to roundtrip if an operation converts an original floating-point number to another form, an inverse operation transforms the converted form back to a floating-point number, and the final floating-point number is equal to the original floating-point number.</span></span> <span data-ttu-id="a953b-132">往返可能因為轉換中遺漏或變更一個或多個最低有效位數而失敗。</span><span class="sxs-lookup"><span data-stu-id="a953b-132">The roundtrip might fail because one or more least significant digits are lost or changed in a conversion.</span></span>  
  
## <a name="attribute-examples"></a><span data-ttu-id="a953b-133">屬性範例</span><span class="sxs-lookup"><span data-stu-id="a953b-133">Attribute Examples</span></span>  
 <span data-ttu-id="a953b-134">在下列範例中，實體有屬性：Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto。</span><span class="sxs-lookup"><span data-stu-id="a953b-134">In the following example, the entity has the attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto.</span></span> <span data-ttu-id="a953b-135">這些屬性描述成員。</span><span class="sxs-lookup"><span data-stu-id="a953b-135">These attributes describe the members.</span></span> <span data-ttu-id="a953b-136">每個成員都是由單一資料列的屬性值來表示。</span><span class="sxs-lookup"><span data-stu-id="a953b-136">Each member is represented by a single row of attribute values.</span></span>  
  
 <span data-ttu-id="a953b-137">![自行車產品實體資料表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行車產品實體資料表")</span><span class="sxs-lookup"><span data-stu-id="a953b-137">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>  
  
 <span data-ttu-id="a953b-138">在下列範例中，Product 實體包含：</span><span class="sxs-lookup"><span data-stu-id="a953b-138">In the following example, the Product entity contains:</span></span>  
  
-   <span data-ttu-id="a953b-139">Name、Code、StandardCost 和 ListPrice 自由格式的屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-139">The free-form attributes of Name, Code, StandardCost and ListPrice.</span></span>  
  
-   <span data-ttu-id="a953b-140">Subcategory 網域屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-140">The domain-based attribute of Subcategory.</span></span>  
  
-   <span data-ttu-id="a953b-141">FilePhoto 檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-141">The file attribute of FilePhoto.</span></span>  
  
 <span data-ttu-id="a953b-142">Subcategory 實體當做 Product 的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-142">Subcategory is an entity that is used as a domain-based attribute of Product.</span></span> <span data-ttu-id="a953b-143">Category 實體當做 Subcategory 的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-143">Category is an entity that is used as a domain-based attribute of Subcategory.</span></span> <span data-ttu-id="a953b-144">就像 Product 實體一樣，Category 和 Subcategory 實體每一個都包含預設的 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-144">Like the Product entity, the Category and Subcategory entities each contain the default Name and Code attributes.</span></span>  
  
 <span data-ttu-id="a953b-145">![產品實體樹狀結構](../../2014/master-data-services/media/mds-conc-entity-ui.gif "產品實體樹狀結構")</span><span class="sxs-lookup"><span data-stu-id="a953b-145">![Product Entity Tree Structure](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Product Entity Tree Structure")</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a953b-146">相關工作</span><span class="sxs-lookup"><span data-stu-id="a953b-146">Related Tasks</span></span>  
  
|<span data-ttu-id="a953b-147">工作描述</span><span class="sxs-lookup"><span data-stu-id="a953b-147">Task Description</span></span>|<span data-ttu-id="a953b-148">主題</span><span class="sxs-lookup"><span data-stu-id="a953b-148">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="a953b-149">建立新的自由格式文字屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-149">Create a new free-form text attribute.</span></span>|[<span data-ttu-id="a953b-150">建立文字屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-150">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-151">建立新的自由格式數值屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-151">Create a new free-form numeric attribute.</span></span>|[<span data-ttu-id="a953b-152">建立數值屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-152">Create a Numeric Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-153">建立新的自由格式連結屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-153">Create a new free-form link attribute.</span></span>|[<span data-ttu-id="a953b-154">建立連結屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-154">Create a Link Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-155">建立新的檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-155">Create a new file attribute.</span></span>|[<span data-ttu-id="a953b-156">建立檔案屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-156">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-157">建立新的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-157">Create a new domain-based attribute.</span></span>|[<span data-ttu-id="a953b-158">建立網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-158">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-159">變更現有屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a953b-159">Change the name of an existing attribute.</span></span>|[<span data-ttu-id="a953b-160">變更屬性名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-160">Change an Attribute Name &#40;Master Data Services&#41;</span></span>](change-an-attribute-name-and-data-type-master-data-services.md)|  
|<span data-ttu-id="a953b-161">將現有屬性加入至變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="a953b-161">Add existing attributes to a change tracking group.</span></span>|[<span data-ttu-id="a953b-162">將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-162">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="a953b-163">刪除現有屬性。</span><span class="sxs-lookup"><span data-stu-id="a953b-163">Delete an existing attribute.</span></span>|[<span data-ttu-id="a953b-164">刪除屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-164">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|<span data-ttu-id="a953b-165">變更屬性的順序。</span><span class="sxs-lookup"><span data-stu-id="a953b-165">Change the order of attributes.</span></span>|[<span data-ttu-id="a953b-166">變更屬性的順序</span><span class="sxs-lookup"><span data-stu-id="a953b-166">Change the Order of Attributes</span></span>](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a><span data-ttu-id="a953b-167">相關內容</span><span class="sxs-lookup"><span data-stu-id="a953b-167">Related Content</span></span>  
  
-   [<span data-ttu-id="a953b-168">網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-168">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [<span data-ttu-id="a953b-169">屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-169">Attribute Groups &#40;Master Data Services&#41;</span></span>](attribute-groups-master-data-services.md)  
  
-   [<span data-ttu-id="a953b-170">成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-170">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
-   [<span data-ttu-id="a953b-171">分葉權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-171">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [<span data-ttu-id="a953b-172">合併的許可權 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a953b-172">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
