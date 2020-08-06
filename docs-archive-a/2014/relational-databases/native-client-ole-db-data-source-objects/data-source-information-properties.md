---
title: 資料來源資訊屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: rothja
ms.author: jroth
ms.openlocfilehash: c10a4e762bbe3421e720753941f5e0a5702832ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708238"
---
# <a name="data-source-information-properties"></a><span data-ttu-id="08259-102">資料來源資訊屬性</span><span class="sxs-lookup"><span data-stu-id="08259-102">Data Source Information Properties</span></span>
  <span data-ttu-id="08259-103">在提供者專用的屬性集 DBPROPSET_SQLSERVERDATASOURCEINFO 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義下列資料來源資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="08259-103">In the provider-specific property set DBPROPSET_SQLSERVERDATASOURCEINFO, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information properties.</span></span>  
  
|<span data-ttu-id="08259-104">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="08259-104">Property ID</span></span>|<span data-ttu-id="08259-105">描述</span><span class="sxs-lookup"><span data-stu-id="08259-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="08259-106">SSPROP_COLUMNLEVELCOLLATION</span><span class="sxs-lookup"><span data-stu-id="08259-106">SSPROP_COLUMNLEVELCOLLATION</span></span>|<span data-ttu-id="08259-107">輸入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="08259-107">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="08259-108">R/W：讀取</span><span class="sxs-lookup"><span data-stu-id="08259-108">R/W: Read</span></span><br /><br /> <span data-ttu-id="08259-109">預設值：VARIANT_TRUE</span><span class="sxs-lookup"><span data-stu-id="08259-109">Default: VARIANT_TRUE</span></span><br /><br /> <span data-ttu-id="08259-110">描述：用於判斷是否支援資料行定序。</span><span class="sxs-lookup"><span data-stu-id="08259-110">Description: Used to determine if column collation is supported.</span></span><br /><br /> <span data-ttu-id="08259-111">VARIANT_TRUE：支援資料行層級定序。</span><span class="sxs-lookup"><span data-stu-id="08259-111">VARIANT_TRUE: Column level collation is supported.</span></span><br /><br /> <span data-ttu-id="08259-112">VARIANT_FALSE：不支援資料行層級定序。</span><span class="sxs-lookup"><span data-stu-id="08259-112">VARIANT_FALSE: Column level collation is not supported.</span></span>|  
|<span data-ttu-id="08259-113">SSPROP_UNICODELCID</span><span class="sxs-lookup"><span data-stu-id="08259-113">SSPROP_UNICODELCID</span></span>|<span data-ttu-id="08259-114">類型：VT_I4 R/W：讀取</span><span class="sxs-lookup"><span data-stu-id="08259-114">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="08259-115">描述：Unicode 地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="08259-115">Description: Unicode locale ID.</span></span><br /><br /> <span data-ttu-id="08259-116">這是用於 Unicode 資料排序的地區設定。</span><span class="sxs-lookup"><span data-stu-id="08259-116">This is the locale used for Unicode data sorting.</span></span>|  
|<span data-ttu-id="08259-117">SSPROP_UNICODECOMPARISONSTYLE</span><span class="sxs-lookup"><span data-stu-id="08259-117">SSPROP_UNICODECOMPARISONSTYLE</span></span>|<span data-ttu-id="08259-118">類型：VT_I4 R/W：讀取</span><span class="sxs-lookup"><span data-stu-id="08259-118">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="08259-119">描述：Unicode 比較樣式。</span><span class="sxs-lookup"><span data-stu-id="08259-119">Description: Unicode comparison style.</span></span><br /><br /> <span data-ttu-id="08259-120">用於 Unicode 資料排序的排序選項。</span><span class="sxs-lookup"><span data-stu-id="08259-120">The sorting options used for Unicode data sorting.</span></span>|  
  
 <span data-ttu-id="08259-121">在提供者專屬的屬性集 DBPROPSET_SQLSERVERSTREAM 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會定義以下額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="08259-121">In the provider-specific property set DBPROPSET_SQLSERVERSTREAM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional property.</span></span>  
  
|<span data-ttu-id="08259-122">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="08259-122">Property ID</span></span>|<span data-ttu-id="08259-123">描述</span><span class="sxs-lookup"><span data-stu-id="08259-123">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="08259-124">SSPROP_STREAM_XMLROOT</span><span class="sxs-lookup"><span data-stu-id="08259-124">SSPROP_STREAM_XMLROOT</span></span>|<span data-ttu-id="08259-125">類型：VT_BSTR R/W：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="08259-125">Type: VT_BSTR R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="08259-126">描述：FOR XML 查詢的結果可能不是格式正確的文件。</span><span class="sxs-lookup"><span data-stu-id="08259-126">Description: The result of a FOR XML query may not be a well-formed document.</span></span> <span data-ttu-id="08259-127">指定此屬性時，'select ... for XML' 查詢的結果會包裝在此屬性提供的根標記中，以傳回格式正確的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="08259-127">When this property is specified, the result of a 'select ... for XML' query is wrapped in the root tag provided by this property to return a well formed XML document.</span></span> <span data-ttu-id="08259-128">如果在瀏覽器中執行查詢，載入結果時，它可能會使瀏覽器顯示剖析器錯誤。</span><span class="sxs-lookup"><span data-stu-id="08259-128">If the query is executed in the browser it may cause the browser to display parser errors when loading the result.</span></span> <span data-ttu-id="08259-129">為避免這個錯誤，SQL ISAPI 支援關鍵字 ROOT。</span><span class="sxs-lookup"><span data-stu-id="08259-129">To avoid the error, SQL ISAPI supports the keyword ROOT.</span></span> <span data-ttu-id="08259-130">此關鍵字會對應至 SSPROP_STREAM_XMLROOT 屬性。</span><span class="sxs-lookup"><span data-stu-id="08259-130">This keyword maps to SSPROP_STREAM_XMLROOT property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08259-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08259-131">See Also</span></span>  
 [<span data-ttu-id="08259-132">資料來源物件 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="08259-132">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
