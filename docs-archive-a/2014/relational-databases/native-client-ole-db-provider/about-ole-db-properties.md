---
title: 關於 OLE DB 屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4eb80ab9c0ab90da11d8580e9a2983455b676bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698131"
---
# <a name="about-ole-db-properties"></a><span data-ttu-id="e19f4-102">關於 OLE DB 屬性</span><span class="sxs-lookup"><span data-stu-id="e19f4-102">About OLE DB Properties</span></span>
  <span data-ttu-id="e19f4-103">取用者會設定屬性值來要求特定的物件行為。</span><span class="sxs-lookup"><span data-stu-id="e19f4-103">Consumers set property values to request specific object behavior.</span></span> <span data-ttu-id="e19f4-104">例如，取用者會使用屬性來指定要由某個資料列集公開的介面。</span><span class="sxs-lookup"><span data-stu-id="e19f4-104">For example, consumers use properties to specify the interfaces to be exposed by a rowset.</span></span> <span data-ttu-id="e19f4-105">取用者會取得屬性值來判斷物件 (例如資料列集、工作階段或資料來源物件) 的功能。</span><span class="sxs-lookup"><span data-stu-id="e19f4-105">Consumers get the property values to determine the capabilities of an object, such as a rowset, a session, or a data source object.</span></span>  
  
 <span data-ttu-id="e19f4-106">每個屬性 (Property) 都有一個值、類型、描述和讀取/寫入屬性 (Attribute)，而且資料列集屬性 (Property) 還會包含一個指標，表示它是否能夠以逐資料行的方式套用。</span><span class="sxs-lookup"><span data-stu-id="e19f4-106">Each property has a value, type, description, and read/write attribute, and for rowset properties, an indicator of whether it can be applied on a column-by-column basis.</span></span>  
  
 <span data-ttu-id="e19f4-107">屬性是由 GUID 以及代表屬性識別碼的整數所識別。</span><span class="sxs-lookup"><span data-stu-id="e19f4-107">A property is identified by a GUID and an integer representing the property ID.</span></span> <span data-ttu-id="e19f4-108">屬性集是共用相同 GUID 之所有屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="e19f4-108">A property set is a set of all properties that share the same GUID.</span></span> <span data-ttu-id="e19f4-109">除了預先定義的 OLE DB 屬性集以外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者也會在其中執行提供者特定的屬性集和屬性。</span><span class="sxs-lookup"><span data-stu-id="e19f4-109">In addition to the predefined OLE DB property sets, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements provider-specific property sets and properties in them.</span></span> <span data-ttu-id="e19f4-110">每個屬性都屬於一或多個屬性群組。</span><span class="sxs-lookup"><span data-stu-id="e19f4-110">Each property belongs to one or more property groups.</span></span> <span data-ttu-id="e19f4-111">屬性群組是套用至特定物件之所有屬性的群組。</span><span class="sxs-lookup"><span data-stu-id="e19f4-111">A property group is the group of all properties that apply to a particular object.</span></span> <span data-ttu-id="e19f4-112">某些屬性群組包括初始化屬性群組、資料來源屬性群組、工作階段屬性群組、資料列集屬性群組、資料表屬性群組和資料行屬性群組。</span><span class="sxs-lookup"><span data-stu-id="e19f4-112">Some property groups include the initialization property group, data source property group, session property group, rowset property group, table property group, and column property group.</span></span> <span data-ttu-id="e19f4-113">其中每個屬性群組都具有屬性。</span><span class="sxs-lookup"><span data-stu-id="e19f4-113">There are properties in each of these property groups.</span></span>  
  
 <span data-ttu-id="e19f4-114">設定屬性值包括：</span><span class="sxs-lookup"><span data-stu-id="e19f4-114">Setting property values involves:</span></span>  
  
1.  <span data-ttu-id="e19f4-115">決定要設定值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e19f4-115">Determining the properties for which to set values.</span></span>  
  
2.  <span data-ttu-id="e19f4-116">決定包含已識別之屬性的屬性集。</span><span class="sxs-lookup"><span data-stu-id="e19f4-116">Determining the property sets that contain the identified properties.</span></span>  
  
3.  <span data-ttu-id="e19f4-117">配置 DBPROPSET 結構的陣列 (針對每個已識別的屬性集配置一個結構)。</span><span class="sxs-lookup"><span data-stu-id="e19f4-117">Allocating an array of DBPROPSET structures, one for each identified property set.</span></span>  
  
4.  <span data-ttu-id="e19f4-118">針對每個屬性集配置 DBPROP 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="e19f4-118">Allocating an array of DBPROP structures for each property set.</span></span> <span data-ttu-id="e19f4-119">每個陣列中的元素數目就是屬於該屬性集的屬性數目 (在步驟 1 中識別)。</span><span class="sxs-lookup"><span data-stu-id="e19f4-119">The number of elements in each array is the number of properties (identified in Step 1) that belong to that property set.</span></span>  
  
5.  <span data-ttu-id="e19f4-120">填入每個屬性的 DBPROP 結構。</span><span class="sxs-lookup"><span data-stu-id="e19f4-120">Filling in the DBPROP structure for each property.</span></span>  
  
6.  <span data-ttu-id="e19f4-121">填入每個屬性集之 DBPROPSET 結構的資訊 (屬性集 GUID、元素數目計數，以及指向對應 DBPROP 陣列的指標)。</span><span class="sxs-lookup"><span data-stu-id="e19f4-121">Filling in information (property set GUID, count of number of elements, and a pointer to the corresponding DBPROP array) in the DBPROPSET structure for each property set.</span></span>  
  
7.  <span data-ttu-id="e19f4-122">呼叫方法來設定屬性並且傳遞 DBPROPSET 結構的計數和陣列。</span><span class="sxs-lookup"><span data-stu-id="e19f4-122">Calling a method to set properties and passing the count and the array of DBPROPSET structures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19f4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e19f4-123">See Also</span></span>  
 <span data-ttu-id="e19f4-124">[建立 SQL Server Native Client OLE DB 提供者應用程式](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="e19f4-124">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="e19f4-125">屬性 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="e19f4-125">Properties (OLE DB)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
