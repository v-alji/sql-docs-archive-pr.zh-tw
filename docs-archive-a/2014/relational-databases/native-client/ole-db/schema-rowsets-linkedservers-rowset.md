---
title: LINKEDSERVERS 資料列集 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: rothja
ms.author: jroth
ms.openlocfilehash: 80eded31ebae744e272757a53a7fd1f4b56bf358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592652"
---
# <a name="linkedservers-rowset-ole-db"></a><span data-ttu-id="1d3b8-102">LINKEDSERVERS 資料列集 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1d3b8-102">LINKEDSERVERS Rowset (OLE DB)</span></span>
  <span data-ttu-id="1d3b8-103">**LINKEDSERVERS** 資料列集會列舉可以參與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散式查詢的組織資料來源。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-103">The **LINKEDSERVERS** rowset enumerates organization data sources that can participate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries.</span></span>  
  
 <span data-ttu-id="1d3b8-104">**LINKEDSERVERS** 資料列集包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-104">The **LINKEDSERVERS** rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="1d3b8-105">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="1d3b8-105">Column name</span></span>|<span data-ttu-id="1d3b8-106">類型指標</span><span class="sxs-lookup"><span data-stu-id="1d3b8-106">Type indicator</span></span>|<span data-ttu-id="1d3b8-107">描述</span><span class="sxs-lookup"><span data-stu-id="1d3b8-107">Description</span></span>|  
|-----------------|--------------------|-----------------|  
|<span data-ttu-id="1d3b8-108">SVR_NAME</span><span class="sxs-lookup"><span data-stu-id="1d3b8-108">SVR_NAME</span></span>|<span data-ttu-id="1d3b8-109">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-109">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-110">連結伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-110">Name of a linked server.</span></span>|  
|<span data-ttu-id="1d3b8-111">SVR_PRODUCT</span><span class="sxs-lookup"><span data-stu-id="1d3b8-111">SVR_PRODUCT</span></span>|<span data-ttu-id="1d3b8-112">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-112">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-113">製造商或是識別由連結伺服器名稱表示之資料存放區類型的其他名稱。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-113">Manufacturer or other name identifying the type of data store represented by the name of the linked server.</span></span>|  
|<span data-ttu-id="1d3b8-114">SVR_PROVIDERNAME</span><span class="sxs-lookup"><span data-stu-id="1d3b8-114">SVR_PROVIDERNAME</span></span>|<span data-ttu-id="1d3b8-115">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-115">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-116">用來耗用伺服器中之資料的 OLE DB 提供者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-116">Friendly name of the OLE DB provider used to consume data from the server.</span></span>|  
|<span data-ttu-id="1d3b8-117">SVR_DATASOURCE</span><span class="sxs-lookup"><span data-stu-id="1d3b8-117">SVR_DATASOURCE</span></span>|<span data-ttu-id="1d3b8-118">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-118">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-119">用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_DATASOURCE 字串。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-119">OLE DB DBPROP_INIT_DATASOURCE string used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="1d3b8-120">SVR_PROVIDERSTRING</span><span class="sxs-lookup"><span data-stu-id="1d3b8-120">SVR_PROVIDERSTRING</span></span>|<span data-ttu-id="1d3b8-121">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-121">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-122">用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_PROVIDERSTRING 值。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-122">OLE DB DBPROP_INIT_PROVIDERSTRING value used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="1d3b8-123">SVR_LOCATION</span><span class="sxs-lookup"><span data-stu-id="1d3b8-123">SVR_LOCATION</span></span>|<span data-ttu-id="1d3b8-124">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="1d3b8-124">DBTYPE_WSTR</span></span>|<span data-ttu-id="1d3b8-125">用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_LOCATION 字串。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-125">OLE DB DBPROP_INIT_LOCATION string used to acquire a data source from the provider.</span></span>|  
  
 <span data-ttu-id="1d3b8-126">資料列集會根據 SRV_NAME 排序，而且 SRV_NAME 上可支援單一限制。</span><span class="sxs-lookup"><span data-stu-id="1d3b8-126">The rowset is sorted on SRV_NAME and a single restriction is supported on SRV_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d3b8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3b8-127">See Also</span></span>  
 [<span data-ttu-id="1d3b8-128">結構描述資料列集支援 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="1d3b8-128">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
  
