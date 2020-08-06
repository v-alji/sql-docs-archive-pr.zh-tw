---
title: 設定屬性類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time dimensions [Analysis Services]
- attributes [Analysis Services], types
- slowly changing dimensions
- account dimensions [Analysis Services]
- currency dimensions [Analysis Services]
- Type property
ms.assetid: c2c6a3da-555e-4362-a83f-88da28427520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3431d26d383ef5348f66a5a54a0f445a1d84872a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708818"
---
# <a name="configure-attribute-types"></a><span data-ttu-id="63076-102">設定屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-102">Configure Attribute Types</span></span>
  <span data-ttu-id="63076-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，屬性類型有助於根據商務功能來分類屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attribute types help classify an attribute in terms of business functionality.</span></span> <span data-ttu-id="63076-104">屬性類型有很多，而且大部份可供用戶端應用程式用來顯示或支援屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-104">There are many attribute types, most of which are used by client applications to display or support an attribute.</span></span> <span data-ttu-id="63076-105">不過，有些屬性類型對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]也有特定意義。</span><span class="sxs-lookup"><span data-stu-id="63076-105">However, some attribute types also have specific meaning to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="63076-106">例如，有些屬性類型會針對時間維度，識別代表各種日曆之時間週期的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-106">For example, some attribute types identify attributes that represent time periods in various calendars for time dimensions.</span></span>  
  
##  <a name="setting-attribute-types"></a><a name="setting_attibute_types"></a> <span data-ttu-id="63076-107">設定屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-107">Setting Attribute Types</span></span>  
 <span data-ttu-id="63076-108">屬性 (Attribute) 之 `Type` 屬性 (Property) 的值決定該屬性 (Attribute) 的屬性 (Attribute) 類型。</span><span class="sxs-lookup"><span data-stu-id="63076-108">The value of the `Type` property for an attribute determines the attribute type for that attribute.</span></span> <span data-ttu-id="63076-109">定義維度或屬性時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的數個精靈會設定屬性類型。</span><span class="sxs-lookup"><span data-stu-id="63076-109">Several wizards in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] set attribute types when defining dimensions or attributes.</span></span> <span data-ttu-id="63076-110">這些 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 精靈] 將其他功能加入維度時，也會設定屬性類型。</span><span class="sxs-lookup"><span data-stu-id="63076-110">These [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wizards also set attribute types when the wizards add functionality to dimensions.</span></span> <span data-ttu-id="63076-111">例如，當商業智慧精靈加入帳戶智慧來識別包含維度之名稱、程式碼、號碼和帳戶結構的屬性時，精靈會將數個屬性類型套用至維度中的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-111">For example, the Business Intelligence Wizard applies several attribute types to attributes in a dimension when the wizard adds account intelligence to identify attributes that contain the names, codes, numbers, and structure of accounts in the dimension.</span></span> <span data-ttu-id="63076-112">商業智慧精靈也會耗用屬性類型，例如貨幣的轉換。</span><span class="sxs-lookup"><span data-stu-id="63076-112">The Business Intelligence Wizard also consumes attribute types, such as for currency conversion.</span></span> <span data-ttu-id="63076-113">如需詳細資訊，請參閱 [建立貨幣類型維度](database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-113">For more information, see [Create a Currency type Dimension](database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="63076-114">下表列出 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]可用的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="63076-114">The following tables list the attribute types available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="63076-115">這些資料表將屬性類型分成下列類別目錄：</span><span class="sxs-lookup"><span data-stu-id="63076-115">These tables separate attribute types into the following categories:</span></span>  
  
|<span data-ttu-id="63076-116">詞彙</span><span class="sxs-lookup"><span data-stu-id="63076-116">Term</span></span>|<span data-ttu-id="63076-117">定義</span><span class="sxs-lookup"><span data-stu-id="63076-117">Definition</span></span>|  
|----------|----------------|  
|[<span data-ttu-id="63076-118">一般屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-118">General attribute types</span></span>](#general_attribute_types)|<span data-ttu-id="63076-119">這些值可供所有屬性使用，而且只用於讓用戶端應用程式進行屬性分類。</span><span class="sxs-lookup"><span data-stu-id="63076-119">These values are available to all attributes, and exist only to enable classification of attributes for client application purposes.</span></span>|  
|[<span data-ttu-id="63076-120">帳戶維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-120">Account dimension attribute types</span></span>](#account_dimension_attribute_types)|<span data-ttu-id="63076-121">這些值會識別屬於帳戶維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-121">These values identify an attribute that belongs to an account dimension.</span></span> <span data-ttu-id="63076-122">如需帳戶維度的詳細資訊，請參閱 [建立父子式類型維度的財務帳戶](database-dimensions-finance-account-of-parent-child-type.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-122">For more information about account dimension, see [Create a Finance Account of parent-child type Dimension](database-dimensions-finance-account-of-parent-child-type.md).</span></span>|  
|[<span data-ttu-id="63076-123">貨幣維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-123">Currency dimension attribute type</span></span>](#currency_dimension_attribute_types)|<span data-ttu-id="63076-124">這些值會識別屬於貨幣維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-124">These values identify an attribute that belongs to a currency dimension.</span></span> <span data-ttu-id="63076-125">如需貨幣維度的詳細資訊，請參閱 [建立貨幣類型維度](database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-125">For more information about currency dimensions, see [Create a Currency type Dimension](database-dimensions-create-a-currency-type-dimension.md).</span></span>|  
|[<span data-ttu-id="63076-126">緩時變維度屬性</span><span class="sxs-lookup"><span data-stu-id="63076-126">Slowly changing dimension attributes</span></span>](#slowly_changing_dimension_attribute_types)|<span data-ttu-id="63076-127">這些值會識別屬於緩時變維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-127">These values identify an attribute that belongs to a slowly changing dimension.</span></span>|  
|[<span data-ttu-id="63076-128">時間維度屬性</span><span class="sxs-lookup"><span data-stu-id="63076-128">Time dimension attributes</span></span>](#time_dimension_attribute_types)|<span data-ttu-id="63076-129">這些值會識別屬於時間維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-129">These values identify an attribute that belongs to a time dimension.</span></span> <span data-ttu-id="63076-130">如需時間維度的詳細資訊，請參閱 [建立日期類型維度](database-dimensions-create-a-date-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-130">For more information about time dimensions, see [Create a Date type Dimension](database-dimensions-create-a-date-type-dimension.md).</span></span>|  
  
###  <a name="general-attribute-types"></a><a name="general_attribute_types"></a><span data-ttu-id="63076-131">一般屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-131">General Attribute Types</span></span>  
  
|<span data-ttu-id="63076-132">屬性類型值</span><span class="sxs-lookup"><span data-stu-id="63076-132">Attribute Type Value</span></span>|<span data-ttu-id="63076-133">描述</span><span class="sxs-lookup"><span data-stu-id="63076-133">Description</span></span>|  
|--------------------------|-----------------|  
|`Address`|<span data-ttu-id="63076-134">代表地址。</span><span class="sxs-lookup"><span data-stu-id="63076-134">Represents an address.</span></span>|  
|`AddressBuilding`|<span data-ttu-id="63076-135">代表地址的建築物識別碼。</span><span class="sxs-lookup"><span data-stu-id="63076-135">Represents a building identifier for an address.</span></span>|  
|`AddressCity`|<span data-ttu-id="63076-136">代表地址的城市。</span><span class="sxs-lookup"><span data-stu-id="63076-136">Represents a city for an address.</span></span>|  
|`AddressCountry`|<span data-ttu-id="63076-137">代表地址的國家或地區。</span><span class="sxs-lookup"><span data-stu-id="63076-137">Represents a country or region for an address.</span></span>|  
|`AddressFax`|<span data-ttu-id="63076-138">代表傳真電話號碼。</span><span class="sxs-lookup"><span data-stu-id="63076-138">Represents a fax telephone number.</span></span>|  
|`AddressFloor`|<span data-ttu-id="63076-139">代表地址的樓層識別碼。</span><span class="sxs-lookup"><span data-stu-id="63076-139">Represents a floor identifier for an address.</span></span>|  
|`AddressHouse`|<span data-ttu-id="63076-140">代表地址的房屋號碼。</span><span class="sxs-lookup"><span data-stu-id="63076-140">Represents a house number for an address.</span></span>|  
|`AddressPhone`|<span data-ttu-id="63076-141">代表電話號碼。</span><span class="sxs-lookup"><span data-stu-id="63076-141">Represents a telephone number.</span></span>|  
|`AddressQuarter`|<span data-ttu-id="63076-142">代表地址的宅所。</span><span class="sxs-lookup"><span data-stu-id="63076-142">Represents a quarter for an address.</span></span>|  
|`AddressRoom`|<span data-ttu-id="63076-143">代表地址的房間識別碼。</span><span class="sxs-lookup"><span data-stu-id="63076-143">Represents a room identifier for an address.</span></span>|  
|`AddressStateOrProvince`|<span data-ttu-id="63076-144">代表地址的州或省。</span><span class="sxs-lookup"><span data-stu-id="63076-144">Represents a state or province for an address.</span></span>|  
|`AddressStreet`|<span data-ttu-id="63076-145">代表地址的街。</span><span class="sxs-lookup"><span data-stu-id="63076-145">Represents the street for an address.</span></span>|  
|`AddressZip`|<span data-ttu-id="63076-146">代表地址的郵遞區號。</span><span class="sxs-lookup"><span data-stu-id="63076-146">Represents a ZIP Code or Postal Code for an address.</span></span>|  
|`BomResource`|<span data-ttu-id="63076-147">代表用料表 (BOM) 的資源。</span><span class="sxs-lookup"><span data-stu-id="63076-147">Represents a resource for a bill of materials (BOM).</span></span>|  
|`Caption`|<span data-ttu-id="63076-148">代表標題。</span><span class="sxs-lookup"><span data-stu-id="63076-148">Represents a caption.</span></span>|  
|`CaptionAbbreviation`|<span data-ttu-id="63076-149">代表縮寫。</span><span class="sxs-lookup"><span data-stu-id="63076-149">Represents an abbreviation.</span></span>|  
|`CaptionDescription`|<span data-ttu-id="63076-150">代表描述。</span><span class="sxs-lookup"><span data-stu-id="63076-150">Represents a description.</span></span>|  
|`Channel`|<span data-ttu-id="63076-151">代表通路。</span><span class="sxs-lookup"><span data-stu-id="63076-151">Represents a channel.</span></span>|  
|`City`|<span data-ttu-id="63076-152">代表縣 (市)。</span><span class="sxs-lookup"><span data-stu-id="63076-152">Represents a city.</span></span>|  
|`Company`|<span data-ttu-id="63076-153">代表公司。</span><span class="sxs-lookup"><span data-stu-id="63076-153">Represents a company.</span></span>|  
|`Continent`|<span data-ttu-id="63076-154">代表大陸。</span><span class="sxs-lookup"><span data-stu-id="63076-154">Represents a continent.</span></span>|  
|`Country`|<span data-ttu-id="63076-155">代表國家或地區。</span><span class="sxs-lookup"><span data-stu-id="63076-155">Represents a country or region.</span></span>|  
|`County`|<span data-ttu-id="63076-156">代表國家 (地區)。</span><span class="sxs-lookup"><span data-stu-id="63076-156">Represents a county.</span></span>|  
|`CustomerGroup`|<span data-ttu-id="63076-157">代表客戶的群組。</span><span class="sxs-lookup"><span data-stu-id="63076-157">Represents a group of customers.</span></span>|  
|`CustomerHousehold`|<span data-ttu-id="63076-158">代表客戶家庭成員。</span><span class="sxs-lookup"><span data-stu-id="63076-158">Represents a household of customers.</span></span>|  
|`Customers`|<span data-ttu-id="63076-159">代表客戶。</span><span class="sxs-lookup"><span data-stu-id="63076-159">Represents a customer.</span></span>|  
|`DateCanceled`|<span data-ttu-id="63076-160">代表取消日期。</span><span class="sxs-lookup"><span data-stu-id="63076-160">Represents a cancellation date.</span></span>|  
|`DateDuration`|<span data-ttu-id="63076-161">代表持續時間。</span><span class="sxs-lookup"><span data-stu-id="63076-161">Represents a duration.</span></span>|  
|`DateEnded`|<span data-ttu-id="63076-162">代表結束日期。</span><span class="sxs-lookup"><span data-stu-id="63076-162">Represents an end date.</span></span>|  
|`DateModified`|<span data-ttu-id="63076-163">代表修改日期。</span><span class="sxs-lookup"><span data-stu-id="63076-163">Represents a modification date.</span></span>|  
|`DateStart`|<span data-ttu-id="63076-164">代表開始日期。</span><span class="sxs-lookup"><span data-stu-id="63076-164">Represents a start date.</span></span>|  
|<span data-ttu-id="63076-165">**DeletedFlag**</span><span class="sxs-lookup"><span data-stu-id="63076-165">**DeletedFlag**</span></span>|<span data-ttu-id="63076-166">指出是否要刪除或應刪除成員 (在商務功能上)。</span><span class="sxs-lookup"><span data-stu-id="63076-166">Indicates whether a member is or should be deleted (in terms of business functionality.)</span></span><br /><br /> <span data-ttu-id="63076-167">注意： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 不會使用此屬性類型來決定是否要刪除成員。</span><span class="sxs-lookup"><span data-stu-id="63076-167">Note: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not use this attribute type to determine whether a member should be deleted.</span></span> <span data-ttu-id="63076-168">反之，此屬性類型只是為了供用戶端應用程式顯示而已。</span><span class="sxs-lookup"><span data-stu-id="63076-168">Instead, this attribute type is intended to be used by client applications for display purposes only.</span></span>|  
|`FormattingColor`|<span data-ttu-id="63076-169">代表格式化使用的色彩。</span><span class="sxs-lookup"><span data-stu-id="63076-169">Represents the color used in formatting.</span></span>|  
|`FormattingFont`|<span data-ttu-id="63076-170">代表格式化使用的字型。</span><span class="sxs-lookup"><span data-stu-id="63076-170">Represents the font used in formatting.</span></span>|  
|`FormattingFontEffects`|<span data-ttu-id="63076-171">代表格式化使用的字型效果。</span><span class="sxs-lookup"><span data-stu-id="63076-171">Represents the font effects used in formatting.</span></span>|  
|`FormattingFontSize`|<span data-ttu-id="63076-172">代表格式化使用的字型大小。</span><span class="sxs-lookup"><span data-stu-id="63076-172">Represents the font size used in formatting.</span></span>|  
|`FormattingOrder`|<span data-ttu-id="63076-173">代表格式化使用的順序。</span><span class="sxs-lookup"><span data-stu-id="63076-173">Represents the order used in formatting.</span></span>|  
|`FormattingSubtotal`|<span data-ttu-id="63076-174">代表小計。</span><span class="sxs-lookup"><span data-stu-id="63076-174">Represents a subtotal.</span></span>|  
|`GeoBoundaryBottom`|<span data-ttu-id="63076-175">代表地理界限的最底部值。</span><span class="sxs-lookup"><span data-stu-id="63076-175">Represents the bottommost value of a geographic boundary.</span></span>|  
|`GeoBoundaryFront`|<span data-ttu-id="63076-176">代表地理界限的最前方值。</span><span class="sxs-lookup"><span data-stu-id="63076-176">Represents the value at the front of a geographic boundary.</span></span>|  
|`GeoBoundaryLeft`|<span data-ttu-id="63076-177">代表地理界限的最左方值。</span><span class="sxs-lookup"><span data-stu-id="63076-177">Represents the leftmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryPolygon`|<span data-ttu-id="63076-178">代表地理界限的多邊形定義。</span><span class="sxs-lookup"><span data-stu-id="63076-178">Represents the polygon definition of a geographic boundary.</span></span>|  
|`GeoBoundaryRear`|<span data-ttu-id="63076-179">代表地理界限的最後方值。</span><span class="sxs-lookup"><span data-stu-id="63076-179">Represents the rearmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryRight`|<span data-ttu-id="63076-180">代表地理界限的最右方值。</span><span class="sxs-lookup"><span data-stu-id="63076-180">Represents the rightmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryTop`|<span data-ttu-id="63076-181">代表地理界限的最頂部值。</span><span class="sxs-lookup"><span data-stu-id="63076-181">Represents the topmost value of a geographic boundary.</span></span>|  
|`GeoCentroidX`|<span data-ttu-id="63076-182">代表地理區域的 X 軸距心。</span><span class="sxs-lookup"><span data-stu-id="63076-182">Represents an X-axis centroid for a geographic region.</span></span>|  
|`GeoCentroidY`|<span data-ttu-id="63076-183">代表地理區域的 Y 軸距心。</span><span class="sxs-lookup"><span data-stu-id="63076-183">Represents a Y-axis centroid for a geographic region.</span></span>|  
|`GeoCentroidZ`|<span data-ttu-id="63076-184">代表地理區域的 Z 軸距心。</span><span class="sxs-lookup"><span data-stu-id="63076-184">Represents a Z-axis centroid for a geographic region.</span></span>|  
|`ID`|<span data-ttu-id="63076-185">代表識別碼 (ID) 或索引鍵。</span><span class="sxs-lookup"><span data-stu-id="63076-185">Represents an identifier (ID) or key.</span></span>|  
|`Image`|<span data-ttu-id="63076-186">代表未定義之圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-186">Represents an image in an undefined graphic format.</span></span>|  
|`ImageBmp`|<span data-ttu-id="63076-187">代表點陣圖圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-187">Represents an image in bitmap graphic format.</span></span>|  
|`ImageGif`|<span data-ttu-id="63076-188">代表圖形交換格式 (GIF) 圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-188">Represents an image in Graphics Interchange Format (GIF) graphic format.</span></span>|  
|`ImageJpg`|<span data-ttu-id="63076-189">代表 JPEG 圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-189">Represents an image in Joint Photographic Experts Group (JPEG) graphic format.</span></span>|  
|`ImagePng`|<span data-ttu-id="63076-190">代表可攜式網路圖形 (PNG) 圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-190">Represents an image in Portable Network Graphics (PNG) graphic format.</span></span>|  
|`ImageTiff`|<span data-ttu-id="63076-191">代表 TIFF 圖形格式的影像。</span><span class="sxs-lookup"><span data-stu-id="63076-191">Represents an image in Tagged Image File Format (TIFF) graphic format.</span></span>|  
|`OrganizationalUnit`|<span data-ttu-id="63076-192">代表組織單位。</span><span class="sxs-lookup"><span data-stu-id="63076-192">Represents an organizational unit.</span></span>|  
|`OrgTitle`|<span data-ttu-id="63076-193">代表組織標題。</span><span class="sxs-lookup"><span data-stu-id="63076-193">Represents an organizational title.</span></span>|  
|`PercentOwnership`|<span data-ttu-id="63076-194">代表擁有權百分比。</span><span class="sxs-lookup"><span data-stu-id="63076-194">Represents a percent of ownership.</span></span>|  
|`PercentVoteRight`|<span data-ttu-id="63076-195">代表投票權的百分比。</span><span class="sxs-lookup"><span data-stu-id="63076-195">Represents a percent of voting rights.</span></span>|  
|`Person`|<span data-ttu-id="63076-196">代表個人。</span><span class="sxs-lookup"><span data-stu-id="63076-196">Represents a person.</span></span>|  
|`PersonContact`|<span data-ttu-id="63076-197">代表個人的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="63076-197">Represents contact information for a person.</span></span>|  
|`PersonDemographic`|<span data-ttu-id="63076-198">代表個人的人口統計資訊。</span><span class="sxs-lookup"><span data-stu-id="63076-198">Represents demographic information for a person.</span></span>|  
|`PersonFirstName`|<span data-ttu-id="63076-199">代表個人的名字。</span><span class="sxs-lookup"><span data-stu-id="63076-199">Represents the first name of a person.</span></span>|  
|`PersonFullName`|<span data-ttu-id="63076-200">代表個人的全名。</span><span class="sxs-lookup"><span data-stu-id="63076-200">Represents the full name of a person.</span></span>|  
|`PersonLastName`|<span data-ttu-id="63076-201">代表個人的姓氏。</span><span class="sxs-lookup"><span data-stu-id="63076-201">Represents the surname (last name) of a person.</span></span>|  
|`PersonMiddleName`|<span data-ttu-id="63076-202">代表個人的中間名。</span><span class="sxs-lookup"><span data-stu-id="63076-202">Represents the middle name of a person.</span></span>|  
|`PhysicalColor`|<span data-ttu-id="63076-203">代表色彩。</span><span class="sxs-lookup"><span data-stu-id="63076-203">Represents a color.</span></span>|  
|`PhysicalDensity`|<span data-ttu-id="63076-204">代表密度。</span><span class="sxs-lookup"><span data-stu-id="63076-204">Represents density.</span></span>|  
|`PhysicalDepth`|<span data-ttu-id="63076-205">代表深度。</span><span class="sxs-lookup"><span data-stu-id="63076-205">Represents depth.</span></span>|  
|`PhysicalHeight`|<span data-ttu-id="63076-206">代表高度。</span><span class="sxs-lookup"><span data-stu-id="63076-206">Represents height.</span></span>|  
|`PhysicalSize`|<span data-ttu-id="63076-207">代表大小。</span><span class="sxs-lookup"><span data-stu-id="63076-207">Represents a size.</span></span>|  
|`PhysicalVolume`|<span data-ttu-id="63076-208">代表體積。</span><span class="sxs-lookup"><span data-stu-id="63076-208">Represents volume.</span></span>|  
|`PhysicalWeight`|<span data-ttu-id="63076-209">代表重量。</span><span class="sxs-lookup"><span data-stu-id="63076-209">Represents weight.</span></span>|  
|`PhysicalWidth`|<span data-ttu-id="63076-210">代表寬度。</span><span class="sxs-lookup"><span data-stu-id="63076-210">Represents width.</span></span>|  
|`Point`|<span data-ttu-id="63076-211">代表點。</span><span class="sxs-lookup"><span data-stu-id="63076-211">Represents a point.</span></span>|  
|`PostalCode`|<span data-ttu-id="63076-212">表示郵遞區號。</span><span class="sxs-lookup"><span data-stu-id="63076-212">Represents a postal code.</span></span>|  
|`Product`|<span data-ttu-id="63076-213">代表產品。</span><span class="sxs-lookup"><span data-stu-id="63076-213">Represents a product.</span></span>|  
|`ProductBrand`|<span data-ttu-id="63076-214">代表產品品牌。</span><span class="sxs-lookup"><span data-stu-id="63076-214">Represents a product brand.</span></span>|  
|`ProductCategory`|<span data-ttu-id="63076-215">代表產品類別目錄。</span><span class="sxs-lookup"><span data-stu-id="63076-215">Represents a product category.</span></span>|  
|`ProductGroup`|<span data-ttu-id="63076-216">代表產品群組。</span><span class="sxs-lookup"><span data-stu-id="63076-216">Represents a product group.</span></span>|  
|`ProductSKU`|<span data-ttu-id="63076-217">代表產品存貨保持單元 (SKU)。</span><span class="sxs-lookup"><span data-stu-id="63076-217">Represents a product stock keeping unit (SKU).</span></span>|  
|`Project`|<span data-ttu-id="63076-218">代表專案。</span><span class="sxs-lookup"><span data-stu-id="63076-218">Represents a project.</span></span>|  
|`ProjectCode`|<span data-ttu-id="63076-219">代表專案代碼。</span><span class="sxs-lookup"><span data-stu-id="63076-219">Represents a project code.</span></span>|  
|`ProjectCompletion`|<span data-ttu-id="63076-220">代表專案的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="63076-220">Represents the completion status of a project.</span></span>|  
|`ProjectEndDate`|<span data-ttu-id="63076-221">代表專案結束日期。</span><span class="sxs-lookup"><span data-stu-id="63076-221">Represents a project end date.</span></span>|  
|`ProjectName`|<span data-ttu-id="63076-222">代表專案名稱。</span><span class="sxs-lookup"><span data-stu-id="63076-222">Represents a project name.</span></span>|  
|`ProjectStartDate`|<span data-ttu-id="63076-223">代表專案開始日期。</span><span class="sxs-lookup"><span data-stu-id="63076-223">Represents a project start date.</span></span>|  
|`Promotion`|<span data-ttu-id="63076-224">代表促銷。</span><span class="sxs-lookup"><span data-stu-id="63076-224">Represents a promotion.</span></span>|  
|`QtyRangeHigh`|<span data-ttu-id="63076-225">代表數量範圍的最大值。</span><span class="sxs-lookup"><span data-stu-id="63076-225">Represents the highest value of a range of quantities.</span></span>|  
|`QtyRangeLow`|<span data-ttu-id="63076-226">代表數量範圍的最小值。</span><span class="sxs-lookup"><span data-stu-id="63076-226">Represents the lowest value of a range of quantities.</span></span>|  
|`Quantitative`|<span data-ttu-id="63076-227">代表數量的屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-227">Represents a quantitative attribute.</span></span>|  
|`Rate`|<span data-ttu-id="63076-228">代表比率。</span><span class="sxs-lookup"><span data-stu-id="63076-228">Represents a rate.</span></span>|  
|`RateType`|<span data-ttu-id="63076-229">代表比率類型。</span><span class="sxs-lookup"><span data-stu-id="63076-229">Represents a rate type.</span></span>|  
|`Region`|<span data-ttu-id="63076-230">代表客戶自訂的區域。</span><span class="sxs-lookup"><span data-stu-id="63076-230">Represents a customer-defined region.</span></span>|  
|`Regular`|<span data-ttu-id="63076-231">代表一般屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-231">Represents a regular attribute.</span></span>|  
|`RelationToParent`|<span data-ttu-id="63076-232">代表與父系的關聯性。</span><span class="sxs-lookup"><span data-stu-id="63076-232">Represents a relation to a parent.</span></span>|  
|`Representative`|<span data-ttu-id="63076-233">表示代表。</span><span class="sxs-lookup"><span data-stu-id="63076-233">Represents a representative.</span></span>|  
|`Scenario`|<span data-ttu-id="63076-234">代表狀況。</span><span class="sxs-lookup"><span data-stu-id="63076-234">Represents a scenario.</span></span>|  
|`Sequence`|<span data-ttu-id="63076-235">代表順序屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-235">Represents a sequence attribute.</span></span>|  
|`ShortCaption`|<span data-ttu-id="63076-236">代表簡短標題。</span><span class="sxs-lookup"><span data-stu-id="63076-236">Represents a short caption.</span></span>|  
|`StateOrProvince`|<span data-ttu-id="63076-237">代表省份。</span><span class="sxs-lookup"><span data-stu-id="63076-237">Represents a state or province.</span></span>|  
|`Utility`|<span data-ttu-id="63076-238">代表公用程式。</span><span class="sxs-lookup"><span data-stu-id="63076-238">Represents a utility.</span></span>|  
|`Version`|<span data-ttu-id="63076-239">代表版本。</span><span class="sxs-lookup"><span data-stu-id="63076-239">Represents a version.</span></span>|  
|`WebHtml`|<span data-ttu-id="63076-240">代表 HTML 內容。</span><span class="sxs-lookup"><span data-stu-id="63076-240">Represents HTML content.</span></span>|  
|`WebMailAlias`|<span data-ttu-id="63076-241">代表電子郵件別名。</span><span class="sxs-lookup"><span data-stu-id="63076-241">Represents an e-mail alias.</span></span>|  
|`WebUrl`|<span data-ttu-id="63076-242">代表 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="63076-242">Represents a URL address.</span></span>|  
|`WebXmlOrXsl`|<span data-ttu-id="63076-243">代表 XML 或 XSL 內容。</span><span class="sxs-lookup"><span data-stu-id="63076-243">Represents XML or XSL content.</span></span>|  
  
###  <a name="account-dimension-attribute-types"></a><a name="account_dimension_attribute_types"></a> <span data-ttu-id="63076-244">Account Dimension Attribute Types</span><span class="sxs-lookup"><span data-stu-id="63076-244">Account Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="63076-245">屬性類型值</span><span class="sxs-lookup"><span data-stu-id="63076-245">Attribute Type Value</span></span>|<span data-ttu-id="63076-246">描述</span><span class="sxs-lookup"><span data-stu-id="63076-246">Description</span></span>|  
|--------------------------|-----------------|  
|`Account`|<span data-ttu-id="63076-247">代表帳戶的父系。</span><span class="sxs-lookup"><span data-stu-id="63076-247">Represents the parent of an account.</span></span> <span data-ttu-id="63076-248">此屬性類型通常會套用至帳戶維度的父系屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-248">This attribute type is typically applied to the parent attribute of an account dimension.</span></span>|  
|`AccountName`|<span data-ttu-id="63076-249">代表帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="63076-249">Represents the name of an account.</span></span> <span data-ttu-id="63076-250">此屬性類型通常會套用至帳戶維度的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-250">This attribute type is typically applied to the key attributes of an account dimension.</span></span>|  
|`AccountNumber`|<span data-ttu-id="63076-251">代表帳戶的號碼。</span><span class="sxs-lookup"><span data-stu-id="63076-251">Represents the number of an account.</span></span>|  
|`AccountType`|<span data-ttu-id="63076-252">代表帳戶的類型。</span><span class="sxs-lookup"><span data-stu-id="63076-252">Represents the type of an account.</span></span> <span data-ttu-id="63076-253">這個屬性類型會識別 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中帳戶類型維度內帳戶成員的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="63076-253">This attribute type identifies the aggregation function of an account member in an account type dimension in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>|  
  
###  <a name="currency-dimension-attribute-types"></a><a name="currency_dimension_attribute_types"></a> <span data-ttu-id="63076-254">貨幣維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-254">Currency Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="63076-255">屬性類型值</span><span class="sxs-lookup"><span data-stu-id="63076-255">Attribute Type Value</span></span>|<span data-ttu-id="63076-256">描述</span><span class="sxs-lookup"><span data-stu-id="63076-256">Description</span></span>|  
|--------------------------|-----------------|  
|`CurrencyDestination`|<span data-ttu-id="63076-257">代表貨幣兌換的目標貨幣。</span><span class="sxs-lookup"><span data-stu-id="63076-257">Represents the destination currency of a currency exchange.</span></span> <span data-ttu-id="63076-258">此屬性類型通常會套用至報表維度的索引鍵屬性，以用於貨幣轉換。</span><span class="sxs-lookup"><span data-stu-id="63076-258">This attribute type is typically applied to the key attribute of a reporting dimension, for use in currency conversion.</span></span> <span data-ttu-id="63076-259">如需貨幣轉換的詳細資訊，請參閱[貨幣轉換 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-259">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencyIsoCode`|<span data-ttu-id="63076-260">代表貨幣的國際標準組織 (ISO) 代碼。</span><span class="sxs-lookup"><span data-stu-id="63076-260">Represents the International Standards Organization (ISO) code of a currency.</span></span> <span data-ttu-id="63076-261">如需貨幣轉換的詳細資訊，請參閱[貨幣轉換 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-261">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencyName`|<span data-ttu-id="63076-262">代表貨幣的名稱。</span><span class="sxs-lookup"><span data-stu-id="63076-262">Represents the name of a currency.</span></span> <span data-ttu-id="63076-263">如需貨幣轉換的詳細資訊，請參閱[貨幣轉換 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-263">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencySource`|<span data-ttu-id="63076-264">代表貨幣兌換的來源貨幣。</span><span class="sxs-lookup"><span data-stu-id="63076-264">Represents the source currency of a currency exchange.</span></span> <span data-ttu-id="63076-265">此屬性類型通常會套用至貨幣維度的索引鍵屬性，以用於貨幣轉換。</span><span class="sxs-lookup"><span data-stu-id="63076-265">This attribute type is typically applied to the key attribute of a currency dimension, for use in currency conversion.</span></span> <span data-ttu-id="63076-266">如需貨幣轉換的詳細資訊，請參閱[貨幣轉換 &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="63076-266">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
  
###  <a name="slowly-changing-dimension-attribute-types"></a><a name="slowly_changing_dimension_attribute_types"></a> <span data-ttu-id="63076-267">緩時變維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-267">Slowly Changing Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="63076-268">屬性類型值</span><span class="sxs-lookup"><span data-stu-id="63076-268">Attribute Type Value</span></span>|<span data-ttu-id="63076-269">描述</span><span class="sxs-lookup"><span data-stu-id="63076-269">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="63076-270">**ScdEndDate**</span><span class="sxs-lookup"><span data-stu-id="63076-270">**ScdEndDate**</span></span>|<span data-ttu-id="63076-271">代表緩時變維度中的成員之有效結束日期。</span><span class="sxs-lookup"><span data-stu-id="63076-271">Represents the effective end date for a member in a slowly changing dimension.</span></span>|  
|<span data-ttu-id="63076-272">**ScdOriginalID**</span><span class="sxs-lookup"><span data-stu-id="63076-272">**ScdOriginalID**</span></span>|<span data-ttu-id="63076-273">代表緩時變維度中的成員之原始識別碼。</span><span class="sxs-lookup"><span data-stu-id="63076-273">Represents the original identifier for a member in a slowly changing dimension.</span></span>|  
|<span data-ttu-id="63076-274">**ScdStartDate**</span><span class="sxs-lookup"><span data-stu-id="63076-274">**ScdStartDate**</span></span>|<span data-ttu-id="63076-275">代表緩時變維度中的成員之有效開始日期。</span><span class="sxs-lookup"><span data-stu-id="63076-275">Represents the effective start date for a member in a slowly changing dimension.</span></span>|  
|`ScdStatus`|<span data-ttu-id="63076-276">代表緩時變維度中的成員之有效狀態。</span><span class="sxs-lookup"><span data-stu-id="63076-276">Represents the effective status of a member in a slowly changing dimension.</span></span>|  
  
###  <a name="time-dimension-attribute-types"></a><a name="time_dimension_attribute_types"></a> <span data-ttu-id="63076-277">時間維度屬性類型</span><span class="sxs-lookup"><span data-stu-id="63076-277">Time Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="63076-278">屬性類型值</span><span class="sxs-lookup"><span data-stu-id="63076-278">Attribute Type Value</span></span>|<span data-ttu-id="63076-279">描述</span><span class="sxs-lookup"><span data-stu-id="63076-279">Description</span></span>|  
|--------------------------|-----------------|  
|`Date`|<span data-ttu-id="63076-280">代表日期。</span><span class="sxs-lookup"><span data-stu-id="63076-280">Represents a date.</span></span> <span data-ttu-id="63076-281">此屬性類型通常會套用至時間維度或伺服器時間維度的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="63076-281">This attribute type is typically applied to the key attribute of a time dimension or server time dimension.</span></span>|  
|`DayOfHalfYear`|<span data-ttu-id="63076-282">代表半年中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-282">Represents the day ordinal of a half-year.</span></span>|  
|`DayOfMonth`|<span data-ttu-id="63076-283">代表月中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-283">Represents the day ordinal of a month.</span></span>|  
|`DayOfQuarter`|<span data-ttu-id="63076-284">代表季中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-284">Represents the day ordinal of a quarter.</span></span>|  
|`DayOfTenDays`|<span data-ttu-id="63076-285">代表十天週期中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-285">Represents the day ordinal of a ten-day period.</span></span>|  
|`DayOfTrimester`|<span data-ttu-id="63076-286">代表每四個月中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-286">Represents the day ordinal of a trimester.</span></span>|  
|`DayOfWeek`|<span data-ttu-id="63076-287">代表週中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-287">Represents the day ordinal of a week.</span></span>|  
|`DayOfYear`|<span data-ttu-id="63076-288">代表年中的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-288">Represents the day ordinal of a year.</span></span>|  
|`Days`|<span data-ttu-id="63076-289">代表天數。</span><span class="sxs-lookup"><span data-stu-id="63076-289">Represents days.</span></span>|  
|`FiscalDate`|<span data-ttu-id="63076-290">代表會計日曆中的日期。</span><span class="sxs-lookup"><span data-stu-id="63076-290">Represents a date in a fiscal calendar.</span></span>|  
|`FiscalDayOfHalfYear`|<span data-ttu-id="63076-291">代表會計日曆中之半年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-291">Represents the day ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalDayOfMonth`|<span data-ttu-id="63076-292">代表會計日曆中之月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-292">Represents the day ordinal of a month in a fiscal calendar.</span></span>|  
|`FiscalDayOfQuarter`|<span data-ttu-id="63076-293">代表會計日曆中之季的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-293">Represents the day ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalDayOfTrimester`|<span data-ttu-id="63076-294">代表會計日曆中之每四個月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-294">Represents the day ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalDayOfWeek`|<span data-ttu-id="63076-295">代表會計日曆中之週的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-295">Represents the day ordinal of a week in a fiscal calendar.</span></span>|  
|`FiscalDayOfYear`|<span data-ttu-id="63076-296">代表會計日曆中之年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-296">Represents the day ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalHalfYears`|<span data-ttu-id="63076-297">代表會計日曆中的半年度。</span><span class="sxs-lookup"><span data-stu-id="63076-297">Represents half-years in a fiscal calendar.</span></span>|  
|`FiscalHalfYearOfYear`|<span data-ttu-id="63076-298">代表會計日曆中之年的半年度序數。</span><span class="sxs-lookup"><span data-stu-id="63076-298">Represents the half-year ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalMonths`|<span data-ttu-id="63076-299">代表會計日曆中的月份。</span><span class="sxs-lookup"><span data-stu-id="63076-299">Represents months in a fiscal calendar.</span></span>|  
|`FiscalMonthOfHalfYear`|<span data-ttu-id="63076-300">代表會計日曆中之半年度的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-300">Represents the month ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalMonthOfQuarter`|<span data-ttu-id="63076-301">代表會計日曆中之季的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-301">Represents the month ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalMonthOfTrimester`|<span data-ttu-id="63076-302">代表會計日曆中之每四個月的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-302">Represents the month ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalMonthOfYear`|<span data-ttu-id="63076-303">代表會計日曆中之年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-303">Represents the month ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalQuarters`|<span data-ttu-id="63076-304">代表會計日曆中的季數。</span><span class="sxs-lookup"><span data-stu-id="63076-304">Represents quarters in a fiscal calendar.</span></span>|  
|`FiscalQuarterOfHalfYear`|<span data-ttu-id="63076-305">代表會計日曆中之半年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-305">Represents the quarter ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalQuarterOfYear`|<span data-ttu-id="63076-306">代表會計日曆中之年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-306">Represents the quarter ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalTrimesters`|<span data-ttu-id="63076-307">代表會計日曆中的每四個月。</span><span class="sxs-lookup"><span data-stu-id="63076-307">Represents trimesters in a fiscal calendar.</span></span>|  
|`FiscalTrimesterOfYear`|<span data-ttu-id="63076-308">代表會計日曆中之年的每四個月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-308">Represents the trimester ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalWeeks`|<span data-ttu-id="63076-309">代表會計日曆中的週。</span><span class="sxs-lookup"><span data-stu-id="63076-309">Represents weeks in a fiscal calendar.</span></span>|  
|`FiscalWeekOfHalfYear`|<span data-ttu-id="63076-310">代表會計日曆中之半年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-310">Represents the week ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalWeekOfMonth`|<span data-ttu-id="63076-311">代表會計日曆中之月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-311">Represents the week ordinal of a month in a fiscal calendar.</span></span>|  
|`FiscalWeekOfQuarter`|<span data-ttu-id="63076-312">代表會計日曆中之季的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-312">Represents the week ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalWeekOfTrimester`|<span data-ttu-id="63076-313">代表會計日曆中之每四個月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-313">Represents the week ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalWeekOfYear`|<span data-ttu-id="63076-314">代表會計日曆中之年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-314">Represents the week ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalYears`|<span data-ttu-id="63076-315">代表會計日曆中的年。</span><span class="sxs-lookup"><span data-stu-id="63076-315">Represents years in a fiscal calendar.</span></span>|  
|`HalfYears`|<span data-ttu-id="63076-316">代表半年度。</span><span class="sxs-lookup"><span data-stu-id="63076-316">Represents half-years.</span></span>|  
|`HalfYearOfYear`|<span data-ttu-id="63076-317">代表年中的半年度序數。</span><span class="sxs-lookup"><span data-stu-id="63076-317">Represents the half-year ordinal of a year.</span></span>|  
|`Hours`|<span data-ttu-id="63076-318">代表小時。</span><span class="sxs-lookup"><span data-stu-id="63076-318">Represents hours.</span></span>|  
|`IsHoliday`|<span data-ttu-id="63076-319">指出日期是否為假日。</span><span class="sxs-lookup"><span data-stu-id="63076-319">Indicates whether a date is a holiday.</span></span>|  
|`ISO8601Date`|<span data-ttu-id="63076-320">代表 ISO 8601 日曆中的日期。</span><span class="sxs-lookup"><span data-stu-id="63076-320">Represents a date in an ISO 8601 calendar.</span></span>|  
|`ISO8601DayOfWeek`|<span data-ttu-id="63076-321">代表 ISO 8601 日曆中之週的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-321">Represents the day ordinal of a week in an ISO 8601 calendar.</span></span>|  
|`ISO8601DayOfYear`|<span data-ttu-id="63076-322">代表 ISO 8601 日曆中之年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-322">Represents the day ordinal of a year in an ISO 8601 calendar.</span></span>|  
|`ISO8601Weeks`|<span data-ttu-id="63076-323">代表 ISO 8601 日曆中的週。</span><span class="sxs-lookup"><span data-stu-id="63076-323">Represents weeks in an ISO 8601 calendar.</span></span>|  
|`ISO8601WeekOfYear`|<span data-ttu-id="63076-324">代表 ISO 8601 日曆中之年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-324">Represents the week ordinal of a year in an ISO 8601 calendar.</span></span>|  
|`ISO8601Years`|<span data-ttu-id="63076-325">代表 ISO 8601 日曆中的年。</span><span class="sxs-lookup"><span data-stu-id="63076-325">Represents years in an ISO 8601 calendar.</span></span>|  
|`IsPeakDay`|<span data-ttu-id="63076-326">指出日期是否為尖峰日。</span><span class="sxs-lookup"><span data-stu-id="63076-326">Indicates whether a date is a peak day.</span></span>|  
|`IsWeekDay`|<span data-ttu-id="63076-327">指出日期是否為工作日。</span><span class="sxs-lookup"><span data-stu-id="63076-327">Indicates whether a date is a weekday.</span></span>|  
|`IsWorkingDay`|<span data-ttu-id="63076-328">指出日期是否為工作日。</span><span class="sxs-lookup"><span data-stu-id="63076-328">Indicates whether a date is a working day.</span></span>|  
|`ManufacturingDate`|<span data-ttu-id="63076-329">代表製造日曆中的日期。</span><span class="sxs-lookup"><span data-stu-id="63076-329">Represents a date in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfHalfYear`|<span data-ttu-id="63076-330">代表製造日曆中之半年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-330">Represents the day ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfMonth`|<span data-ttu-id="63076-331">代表製造日曆中之月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-331">Represents the day ordinal of a month in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfQuarter`|<span data-ttu-id="63076-332">代表製造日曆中之季的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-332">Represents the day ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfTrimester`|<span data-ttu-id="63076-333">代表製造日曆中之每四個月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-333">Represents the day ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfWeek`|<span data-ttu-id="63076-334">代表製造日曆中之週的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-334">Represents the day ordinal of a week in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfYear`|<span data-ttu-id="63076-335">代表製造日曆中之年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-335">Represents the day ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingHalfYears`|<span data-ttu-id="63076-336">代表製造日曆中的半年度。</span><span class="sxs-lookup"><span data-stu-id="63076-336">Represents half-years in a manufacturing calendar.</span></span>|  
|`ManufacturingHalfYearOfYear`|<span data-ttu-id="63076-337">代表製造日曆中之年的半年度序數。</span><span class="sxs-lookup"><span data-stu-id="63076-337">Represents the half-year ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingMonths`|<span data-ttu-id="63076-338">代表製造日曆中的月份。</span><span class="sxs-lookup"><span data-stu-id="63076-338">Represents months in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfHalfYear`|<span data-ttu-id="63076-339">代表製造日曆中之半年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-339">Represents the month ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfQuarter`|<span data-ttu-id="63076-340">代表製造日曆中之季的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-340">Represents the month ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfTrimester`|<span data-ttu-id="63076-341">代表製造日曆中之每四個月的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-341">Represents the month ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfYear`|<span data-ttu-id="63076-342">代表製造日曆中之年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-342">Represents the month ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarters`|<span data-ttu-id="63076-343">代表製造日曆中的季數。</span><span class="sxs-lookup"><span data-stu-id="63076-343">Represents quarters in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarterOfHalfYear`|<span data-ttu-id="63076-344">代表製造日曆中之半年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-344">Represents the quarter ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarterOfYear`|<span data-ttu-id="63076-345">代表製造日曆中之年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-345">Represents the quarter ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingWeeks`|<span data-ttu-id="63076-346">代表製造日曆中的週。</span><span class="sxs-lookup"><span data-stu-id="63076-346">Represents weeks in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfHalfYear`|<span data-ttu-id="63076-347">代表製造日曆中之半年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-347">Represents the week ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfMonth`|<span data-ttu-id="63076-348">代表製造日曆中之月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-348">Represents the week ordinal of a month in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfQuarter`|<span data-ttu-id="63076-349">代表製造日曆中之季的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-349">Represents the week ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfTrimester`|<span data-ttu-id="63076-350">代表製造日曆中之每四個月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-350">Represents the week ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfYear`|<span data-ttu-id="63076-351">代表製造日曆中之年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-351">Represents the week ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingYears`|<span data-ttu-id="63076-352">代表製造日曆中的年。</span><span class="sxs-lookup"><span data-stu-id="63076-352">Represents years in a manufacturing calendar.</span></span>|  
|`Minutes`|<span data-ttu-id="63076-353">代表分鐘數。</span><span class="sxs-lookup"><span data-stu-id="63076-353">Represents minutes.</span></span>|  
|`Months`|<span data-ttu-id="63076-354">代表月份。</span><span class="sxs-lookup"><span data-stu-id="63076-354">Represents months.</span></span>|  
|`MonthOfHalfYear`|<span data-ttu-id="63076-355">代表半年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-355">Represents the month ordinal of a half-year.</span></span>|  
|`MonthOfQuarter`|<span data-ttu-id="63076-356">代表季的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-356">Represents the month ordinal of a quarter.</span></span>|  
|`MonthOfTrimester`|<span data-ttu-id="63076-357">代表每四個月的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-357">Represents the month ordinal of a trimester.</span></span>|  
|`MonthOfYear`|<span data-ttu-id="63076-358">代表年中的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-358">Represents the month ordinal of a year.</span></span>|  
|`Quarters`|<span data-ttu-id="63076-359">代表季數。</span><span class="sxs-lookup"><span data-stu-id="63076-359">Represents quarters.</span></span>|  
|`QuarterOfHalfYear`|<span data-ttu-id="63076-360">代表半年中的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-360">Represents the quarter ordinal of a half-year.</span></span>|  
|`QuarterOfYear`|<span data-ttu-id="63076-361">代表年中的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-361">Represents the quarter ordinal of a year.</span></span>|  
|`ReportingDate`|<span data-ttu-id="63076-362">代表報表日曆中的日期。</span><span class="sxs-lookup"><span data-stu-id="63076-362">Represents a date in a reporting calendar.</span></span>|  
|`ReportingDayOfHalfYear`|<span data-ttu-id="63076-363">代表報表日曆中之半年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-363">Represents the day ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingDayOfMonth`|<span data-ttu-id="63076-364">代表報表日曆中之月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-364">Represents the day ordinal of a month in a reporting calendar.</span></span>|  
|`ReportingDayOfQuarter`|<span data-ttu-id="63076-365">代表報表日曆中之季的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-365">Represents the day ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingDayOfTrimester`|<span data-ttu-id="63076-366">代表報表日曆中之每四個月的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-366">Represents the day ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingDayOfWeek`|<span data-ttu-id="63076-367">代表報表日曆中之週的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-367">Represents the day ordinal of a week in a reporting calendar.</span></span>|  
|`ReportingDayOfYear`|<span data-ttu-id="63076-368">代表報表日曆中之年的日序數。</span><span class="sxs-lookup"><span data-stu-id="63076-368">Represents the day ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingHalfYears`|<span data-ttu-id="63076-369">代表報表日曆中的半年度。</span><span class="sxs-lookup"><span data-stu-id="63076-369">Represents half-years in a reporting calendar.</span></span>|  
|`ReportingHalfYearOfYear`|<span data-ttu-id="63076-370">代表報表日曆中之年的半年度序數。</span><span class="sxs-lookup"><span data-stu-id="63076-370">Represents the half-year ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingMonths`|<span data-ttu-id="63076-371">代表報表日曆中的月份。</span><span class="sxs-lookup"><span data-stu-id="63076-371">Represents months in a reporting calendar.</span></span>|  
|`ReportingMonthOfHalfYear`|<span data-ttu-id="63076-372">代表報表日曆中之半年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-372">Represents the month ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingMonthOfQuarter`|<span data-ttu-id="63076-373">代表報表日曆中之季的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-373">Represents the month ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingMonthOfTrimester`|<span data-ttu-id="63076-374">代表報表日曆中之每四個月的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-374">Represents the month ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingMonthOfYear`|<span data-ttu-id="63076-375">代表報表日曆中之年的月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-375">Represents the month ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingQuarters`|<span data-ttu-id="63076-376">代表報表日曆中的季數。</span><span class="sxs-lookup"><span data-stu-id="63076-376">Represents quarters in a reporting calendar.</span></span>|  
|`ReportingQuarterOfHalfYear`|<span data-ttu-id="63076-377">代表報表日曆中之半年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-377">Represents the quarter ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingQuarterOfYear`|<span data-ttu-id="63076-378">代表報表日曆中之年的季序數。</span><span class="sxs-lookup"><span data-stu-id="63076-378">Represents the quarter ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingTrimesters`|<span data-ttu-id="63076-379">代表報表日曆中的每四個月。</span><span class="sxs-lookup"><span data-stu-id="63076-379">Represents trimesters in a reporting calendar.</span></span>|  
|`ReportingTrimesterOfYear`|<span data-ttu-id="63076-380">代表報表日曆中之年的每四個月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-380">Represents the trimester ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingWeeks`|<span data-ttu-id="63076-381">代表報表日曆中的週。</span><span class="sxs-lookup"><span data-stu-id="63076-381">Represents weeks in a reporting calendar.</span></span>|  
|`ReportingWeekOfHalfYear`|<span data-ttu-id="63076-382">代表報表日曆中之半年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-382">Represents the week ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingWeekOfMonth`|<span data-ttu-id="63076-383">代表報表日曆中之月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-383">Represents the week ordinal of a month in a reporting calendar.</span></span>|  
|`ReportingWeekOfQuarter`|<span data-ttu-id="63076-384">代表報表日曆中之季的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-384">Represents the week ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingWeekOfTrimester`|<span data-ttu-id="63076-385">代表報表日曆中之每四個月的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-385">Represents the week ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingWeekOfYear`|<span data-ttu-id="63076-386">代表報表日曆中之年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-386">Represents the week ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingYears`|<span data-ttu-id="63076-387">代表報表日曆中的年。</span><span class="sxs-lookup"><span data-stu-id="63076-387">Represents years in a reporting calendar.</span></span>|  
|`Seconds`|<span data-ttu-id="63076-388">代表秒數。</span><span class="sxs-lookup"><span data-stu-id="63076-388">Represents seconds.</span></span>|  
|`TenDayOfHalfYear`|<span data-ttu-id="63076-389">代表半年的十天週期序數。</span><span class="sxs-lookup"><span data-stu-id="63076-389">Represents the ten-day period ordinal of a half-year.</span></span>|  
|`TenDayOfMonth`|<span data-ttu-id="63076-390">代表月的十天週期序數。</span><span class="sxs-lookup"><span data-stu-id="63076-390">Represents the ten-day period ordinal of a month.</span></span>|  
|`TenDayOfQuarter`|<span data-ttu-id="63076-391">代表季的十天週期序數。</span><span class="sxs-lookup"><span data-stu-id="63076-391">Represents the ten-day period ordinal of a quarter.</span></span>|  
|`TenDayOfTrimester`|<span data-ttu-id="63076-392">代表每四個月的十天週期序數。</span><span class="sxs-lookup"><span data-stu-id="63076-392">Represents the ten-day period ordinal of a trimester.</span></span>|  
|`TenDayOfYear`|<span data-ttu-id="63076-393">代表年的十天週期序數。</span><span class="sxs-lookup"><span data-stu-id="63076-393">Represents the ten-day period ordinal of a year.</span></span>|  
|`TenDays`|<span data-ttu-id="63076-394">代表十天週期。</span><span class="sxs-lookup"><span data-stu-id="63076-394">Represents ten-day periods.</span></span>|  
|`Trimesters`|<span data-ttu-id="63076-395">代表每四個月。</span><span class="sxs-lookup"><span data-stu-id="63076-395">Represents trimesters.</span></span>|  
|`TrimesterOfYear`|<span data-ttu-id="63076-396">代表年的每四個月序數。</span><span class="sxs-lookup"><span data-stu-id="63076-396">Represents the trimester ordinal of a year.</span></span>|  
|`UndefinedTime`|<span data-ttu-id="63076-397">代表未定義的時間週期。</span><span class="sxs-lookup"><span data-stu-id="63076-397">Represents an undefined time period.</span></span>|  
|`WeekOfYear`|<span data-ttu-id="63076-398">代表年的週序數。</span><span class="sxs-lookup"><span data-stu-id="63076-398">Represents the week ordinal of a year.</span></span>|  
|`Weeks`|<span data-ttu-id="63076-399">代表週。</span><span class="sxs-lookup"><span data-stu-id="63076-399">Represents weeks.</span></span>|  
|<span data-ttu-id="63076-400">**WinterSummerSeason**</span><span class="sxs-lookup"><span data-stu-id="63076-400">**WinterSummerSeason**</span></span>|<span data-ttu-id="63076-401">指出日期是否為冬季/夏季的一部份。</span><span class="sxs-lookup"><span data-stu-id="63076-401">Indicates whether the date is part of the winter/summer season.</span></span>|  
|`Years`|<span data-ttu-id="63076-402">代表年。</span><span class="sxs-lookup"><span data-stu-id="63076-402">Represents years.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63076-403">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63076-403">See Also</span></span>  
 <span data-ttu-id="63076-404">[屬性和屬性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="63076-404">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="63076-405">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="63076-405">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
