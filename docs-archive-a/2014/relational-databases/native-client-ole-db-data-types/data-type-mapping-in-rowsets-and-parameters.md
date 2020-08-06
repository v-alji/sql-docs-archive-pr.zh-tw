---
title: 資料列集和參數中的資料類型對應 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: rothja
ms.author: jroth
ms.openlocfilehash: 83923eb611ddc7baedc38c70b23c2ff5e17556d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598856"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="609fb-102">資料列集和參數中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="609fb-102">Data Type Mapping in Rowsets and Parameters</span></span>
  <span data-ttu-id="609fb-103">在資料列集和參數值中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用下列 OLE DB 定義的資料類型（在**IColumnsInfo：： GetColumnInfo**和**ICommandWithParameters：： GetParameterInfo**函數中報告的）來代表資料。</span><span class="sxs-lookup"><span data-stu-id="609fb-103">In rowsets and as parameter values, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider represents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data by using the following OLE DB defined data types, reported in the functions **IColumnsInfo::GetColumnInfo** and **ICommandWithParameters::GetParameterInfo**.</span></span>  
  
|<span data-ttu-id="609fb-104">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="609fb-104">SQL Server data type</span></span>|<span data-ttu-id="609fb-105">OLE DB 資料類型</span><span class="sxs-lookup"><span data-stu-id="609fb-105">OLE DB data type</span></span>|  
|--------------------------|----------------------|  
|<span data-ttu-id="609fb-106">**bigint**</span><span class="sxs-lookup"><span data-stu-id="609fb-106">**bigint**</span></span>|<span data-ttu-id="609fb-107">DBTYPE_I8</span><span class="sxs-lookup"><span data-stu-id="609fb-107">DBTYPE_I8</span></span>|  
|<span data-ttu-id="609fb-108">**binary**</span><span class="sxs-lookup"><span data-stu-id="609fb-108">**binary**</span></span>|<span data-ttu-id="609fb-109">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="609fb-109">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="609fb-110">**bit**</span><span class="sxs-lookup"><span data-stu-id="609fb-110">**bit**</span></span>|<span data-ttu-id="609fb-111">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="609fb-111">DBTYPE_BOOL</span></span>|  
|<span data-ttu-id="609fb-112">**char**</span><span class="sxs-lookup"><span data-stu-id="609fb-112">**char**</span></span>|<span data-ttu-id="609fb-113">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="609fb-113">DBTYPE_STR</span></span>|  
|<span data-ttu-id="609fb-114">**datetime**</span><span class="sxs-lookup"><span data-stu-id="609fb-114">**datetime**</span></span>|<span data-ttu-id="609fb-115">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="609fb-115">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="609fb-116">**datetime2**</span><span class="sxs-lookup"><span data-stu-id="609fb-116">**datetime2**</span></span>|<span data-ttu-id="609fb-117">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="609fb-117">DBTYPE_DBTIME2</span></span>|  
|<span data-ttu-id="609fb-118">**decimal**</span><span class="sxs-lookup"><span data-stu-id="609fb-118">**decimal**</span></span>|<span data-ttu-id="609fb-119">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="609fb-119">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="609fb-120">**float**</span><span class="sxs-lookup"><span data-stu-id="609fb-120">**float**</span></span>|<span data-ttu-id="609fb-121">DBTYPE_R8</span><span class="sxs-lookup"><span data-stu-id="609fb-121">DBTYPE_R8</span></span>|  
|<span data-ttu-id="609fb-122">**image**</span><span class="sxs-lookup"><span data-stu-id="609fb-122">**image**</span></span>|<span data-ttu-id="609fb-123">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="609fb-123">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="609fb-124">**int**</span><span class="sxs-lookup"><span data-stu-id="609fb-124">**int**</span></span>|<span data-ttu-id="609fb-125">DBTYPE_I4</span><span class="sxs-lookup"><span data-stu-id="609fb-125">DBTYPE_I4</span></span>|  
|<span data-ttu-id="609fb-126">**money**</span><span class="sxs-lookup"><span data-stu-id="609fb-126">**money**</span></span>|<span data-ttu-id="609fb-127">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="609fb-127">DBTYPE_CY</span></span>|  
|<span data-ttu-id="609fb-128">**nchar**</span><span class="sxs-lookup"><span data-stu-id="609fb-128">**nchar**</span></span>|<span data-ttu-id="609fb-129">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="609fb-129">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="609fb-130">**ntext**</span><span class="sxs-lookup"><span data-stu-id="609fb-130">**ntext**</span></span>|<span data-ttu-id="609fb-131">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="609fb-131">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="609fb-132">**numeric**</span><span class="sxs-lookup"><span data-stu-id="609fb-132">**numeric**</span></span>|<span data-ttu-id="609fb-133">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="609fb-133">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="609fb-134">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="609fb-134">**nvarchar**</span></span>|<span data-ttu-id="609fb-135">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="609fb-135">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="609fb-136">**real**</span><span class="sxs-lookup"><span data-stu-id="609fb-136">**real**</span></span>|<span data-ttu-id="609fb-137">DBTYPE_R4</span><span class="sxs-lookup"><span data-stu-id="609fb-137">DBTYPE_R4</span></span>|  
|<span data-ttu-id="609fb-138">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="609fb-138">**smalldatetime**</span></span>|<span data-ttu-id="609fb-139">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="609fb-139">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="609fb-140">**smallint**</span><span class="sxs-lookup"><span data-stu-id="609fb-140">**smallint**</span></span>|<span data-ttu-id="609fb-141">DBTYPE_I2</span><span class="sxs-lookup"><span data-stu-id="609fb-141">DBTYPE_I2</span></span>|  
|<span data-ttu-id="609fb-142">**smallmoney**</span><span class="sxs-lookup"><span data-stu-id="609fb-142">**smallmoney**</span></span>|<span data-ttu-id="609fb-143">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="609fb-143">DBTYPE_CY</span></span>|  
|<span data-ttu-id="609fb-144">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="609fb-144">**sql_variant**</span></span>|<span data-ttu-id="609fb-145">DBTYPE_VARIANT、DBTYPE_SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="609fb-145">DBTYPE_VARIANT, DBTYPE_SQLVARIANT</span></span>|  
|<span data-ttu-id="609fb-146">**sysname**</span><span class="sxs-lookup"><span data-stu-id="609fb-146">**sysname**</span></span>|<span data-ttu-id="609fb-147">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="609fb-147">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="609fb-148">**text**</span><span class="sxs-lookup"><span data-stu-id="609fb-148">**text**</span></span>|<span data-ttu-id="609fb-149">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="609fb-149">DBTYPE_STR</span></span>|  
|<span data-ttu-id="609fb-150">**timestamp**</span><span class="sxs-lookup"><span data-stu-id="609fb-150">**timestamp**</span></span>|<span data-ttu-id="609fb-151">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="609fb-151">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="609fb-152">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="609fb-152">**tinyint**</span></span>|<span data-ttu-id="609fb-153">DBTYPE_UI1</span><span class="sxs-lookup"><span data-stu-id="609fb-153">DBTYPE_UI1</span></span>|  
|<span data-ttu-id="609fb-154">**UDT**</span><span class="sxs-lookup"><span data-stu-id="609fb-154">**UDT**</span></span>|<span data-ttu-id="609fb-155">DBTYPE_UDT</span><span class="sxs-lookup"><span data-stu-id="609fb-155">DBTYPE_UDT</span></span>|  
|<span data-ttu-id="609fb-156">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="609fb-156">**uniqueidentifier**</span></span>|<span data-ttu-id="609fb-157">DBTYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="609fb-157">DBTYPE_GUID</span></span>|  
|<span data-ttu-id="609fb-158">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="609fb-158">**varbinary**</span></span>|<span data-ttu-id="609fb-159">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="609fb-159">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="609fb-160">**varchar**</span><span class="sxs-lookup"><span data-stu-id="609fb-160">**varchar**</span></span>|<span data-ttu-id="609fb-161">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="609fb-161">DBTYPE_STR</span></span>|  
|<span data-ttu-id="609fb-162">**XML**</span><span class="sxs-lookup"><span data-stu-id="609fb-162">**XML**</span></span>|<span data-ttu-id="609fb-163">DBTYPE_XML</span><span class="sxs-lookup"><span data-stu-id="609fb-163">DBTYPE_XML</span></span>|  
  
 <span data-ttu-id="609fb-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援取用者要求的資料轉換，如圖所示。</span><span class="sxs-lookup"><span data-stu-id="609fb-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-requested data conversions as shown in the illustration.</span></span>  
  
 <span data-ttu-id="609fb-165">**sql_variant** 物件可保存任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的資料，下列類型除外：text、ntext、image、varchar(max)、nvarchar(max)、varbinary(max)、xml、timestamp 和 Microsoft .NET Framework Common Language Runtime (CLR) 使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="609fb-165">The **sql_variant** objects can hold data of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type except text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp, and Microsoft .NET Framework common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="609fb-166">sql_variant 資料的執行個體不能用 sql_variant 做為它的基礎基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-166">An instance of sql_variant data also cannot have sql_variant as its underlying base data type.</span></span> <span data-ttu-id="609fb-167">例如，資料行可以在某些資料列中包含 **smallint** 值，在其他資料列中包含 **float** 值，而在剩餘的資料列中包含 **char**/**nchar** 值。</span><span class="sxs-lookup"><span data-stu-id="609fb-167">For example, the column can contain **smallint** values for some rows, **float** values for other rows, and **char**/**nchar** values in the remainder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="609fb-168">**Sql_variant**資料類型類似于 Microsoft Visual Basic？中的 variant 資料類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-168">The **sql_variant** data type is similar to the Variant data type in Microsoft Visual Basic??</span></span> <span data-ttu-id="609fb-169">和 DBTYPE_VARIANT，DBTYPE_SQLVARIANT 在 OLEDB 中。</span><span class="sxs-lookup"><span data-stu-id="609fb-169">and the DBTYPE_VARIANT, DBTYPE_SQLVARIANT in OLEDB.</span></span>  
  
 <span data-ttu-id="609fb-170">以 DBTYPE_VARIANT 擷取 **sql_variant** 資料時，會將該資料置於緩衝區的 VARIANT 結構中。</span><span class="sxs-lookup"><span data-stu-id="609fb-170">When **sql_variant** data is fetched as DBTYPE_VARIANT, it is put in a VARIANT structure in the buffer.</span></span> <span data-ttu-id="609fb-171">但是 VARIANT 結構中的子類型可能不會對應到定義於 **sql_variant** 資料類型中的子類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-171">But the subtypes in the VARIANT structure may not map to subtypes defined in the **sql_variant** data type.</span></span> <span data-ttu-id="609fb-172">接下來必須以 DBTYPE_SQLVARIANT 擷取 **sql_variant** 資料，才能讓所有的子類型相互對應。</span><span class="sxs-lookup"><span data-stu-id="609fb-172">The **sql_variant** data must then be fetched as DBTYPE_SQLVARIANT in order for all the subtypes to match.</span></span>  
  
## <a name="dbtype_sqlvariant-data-type"></a><span data-ttu-id="609fb-173">DBTYPE_SQLVARIANT 資料類型</span><span class="sxs-lookup"><span data-stu-id="609fb-173">DBTYPE_SQLVARIANT Data Type</span></span>  
 <span data-ttu-id="609fb-174">為了支援**SQL_variant**資料類型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會公開稱為 DBTYPE_SQLVARIANT 的提供者特定資料類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-174">To support the **sql_variant** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes a provider-specific data type called DBTYPE_SQLVARIANT.</span></span> <span data-ttu-id="609fb-175">以 DBTYPE_SQLVARIANT 擷取 **sql_variant** 資料時，該資料會儲存在提供者特定的 SSVARIANT 結構中。</span><span class="sxs-lookup"><span data-stu-id="609fb-175">When **sql_variant** data is fetched in as DBTYPE_SQLVARIANT, it is stored in a provider-specific SSVARIANT structure.</span></span> <span data-ttu-id="609fb-176">SSVARIANT 結構包含的所有子類型都符合 **sql_variant** 資料類型的子類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-176">The SSVARIANT structure contains all of the subtypes that match the subtypes of the **sql_variant** data type.</span></span>  
  
 <span data-ttu-id="609fb-177">工作階段屬性 SSPROP_ALLOWNATIVEVARIANT 也必須設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="609fb-177">The session property SSPROP_ALLOWNATIVEVARIANT must also be set to TRUE.</span></span>  
  
## <a name="provider-specific-property-ssprop_allownativevariant"></a><span data-ttu-id="609fb-178">提供者特定的屬性 SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="609fb-178">Provider-Specific Property SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="609fb-179">您在提取資料時，可以明確地指定要針對資料行或參數傳回何種資料類型。</span><span class="sxs-lookup"><span data-stu-id="609fb-179">In fetching data, you can specify explicitly what kind of data type should be returned for a column or for a parameter.</span></span> <span data-ttu-id="609fb-180">**IColumnsInfo** 也可以用來取得資料行資訊，並用該資訊來進行繫結。</span><span class="sxs-lookup"><span data-stu-id="609fb-180">**IColumnsInfo** can also be used to get the column information and use that to do the binding.</span></span> <span data-ttu-id="609fb-181">使用 **IColumnsInfo** 來取得用於繫結用途的資料行資訊時，如果 SSPROP_ALLOWNATIVEVARIANT 工作階段屬性為 FALSE (預設值)，則會針對 **sql_variant** 資料行傳回 DBTYPE_VARIANT。</span><span class="sxs-lookup"><span data-stu-id="609fb-181">When **IColumnsInfo** is used to obtain column information for binding purposes, if the SSPROP_ALLOWNATIVEVARIANT session property is FALSE (default value), DBTYPE_VARIANT is returned for **sql_variant** columns.</span></span> <span data-ttu-id="609fb-182">如果 SSPROP_ALLOWNATIVEVARIANT 屬性為 FALSE，則 DBTYPE_SQLVARIANT 不受支援。</span><span class="sxs-lookup"><span data-stu-id="609fb-182">If SSPROP_ALLOWNATIVEVARIANT property is FALSE DBTYPE_SQLVARIANT is not supported.</span></span> <span data-ttu-id="609fb-183">如果 SSPROP_ALLOWNATIVEVARIANT 屬性設定為 TRUE，則資料行類型會傳回為 DBTYPE_SQLVARIANT，在此種情況下，緩衝區會保存 SSVARIANT 結構。</span><span class="sxs-lookup"><span data-stu-id="609fb-183">If SSPROP_ALLOWNATIVEVARIANT property is set to TRUE, the column type is returned as DBTYPE_SQLVARIANT, in which case the buffer will hold the SSVARIANT structure.</span></span> <span data-ttu-id="609fb-184">以 DBTYPE_SQLVARIANT 擷取 **sql_variant** 資料時，工作階段屬性 SSPROP_ALLOWNATIVEVARIANT 必須設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="609fb-184">In fetching **sql_variant** data as DBTYPE_SQLVARIANT, the session property SSPROP_ALLOWNATIVEVARIANT must be set to TRUE.</span></span>  
  
 <span data-ttu-id="609fb-185">SSPROP_ALLOWNATIVEVARIANT 屬性是提供者特定之 DBPROPSET_SQLSERVERSESSION 屬性集的一部分，而且是工作階段屬性。</span><span class="sxs-lookup"><span data-stu-id="609fb-185">SSPROP_ALLOWNATIVEVARIANT property is part of the provider-specific DBPROPSET_SQLSERVERSESSION property set, and is a session property.</span></span>  
  
 <span data-ttu-id="609fb-186">DBTYPE_VARIANT 適用於所有其他的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="609fb-186">DBTYPE_VARIANT applies to all other OLE DB providers.</span></span>  
  
## <a name="ssprop_allownativevariant"></a><span data-ttu-id="609fb-187">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="609fb-187">SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="609fb-188">SSPROP_ALLOWNATIVEVARIANT 是工作階段屬性，而且是 DBPROPSET_SQLSERVERSESSION 屬性集的一部分。</span><span class="sxs-lookup"><span data-stu-id="609fb-188">SSPROP_ALLOWNATIVEVARIANT is a session property and is part of DBPROPSET_SQLSERVERSESSION  property set.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="609fb-189">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="609fb-189">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="609fb-190">類型：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="609fb-190">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="609fb-191">R/W：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="609fb-191">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="609fb-192">預設值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="609fb-192">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="609fb-193">描述：決定所提取的資料是否為 DBTYPE_VARIANT 或 DBTYPE_SQLVARIANT。</span><span class="sxs-lookup"><span data-stu-id="609fb-193">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="609fb-194">VARIANT_TRUE：資料行類型是以 DBTYPE_SQLVARIANT 傳回，在此種情況下，緩衝區會保存 SSVARIANT 結構。</span><span class="sxs-lookup"><span data-stu-id="609fb-194">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="609fb-195">VARIANT_FALSE：資料行類型是以 DBTYPE_VARIANT 傳回，而且緩衝區將具有 VARIANT 結構。</span><span class="sxs-lookup"><span data-stu-id="609fb-195">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="609fb-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="609fb-196">See Also</span></span>  
 [<span data-ttu-id="609fb-197">資料類型 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="609fb-197">Data Types &#40;OLE DB&#41;</span></span>](data-types-ole-db.md)  
  
  
