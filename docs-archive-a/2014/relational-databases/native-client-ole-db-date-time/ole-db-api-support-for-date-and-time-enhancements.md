---
title: OLE DB API 對日期和時間增強功能的支援 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: rothja
ms.author: jroth
ms.openlocfilehash: cdb17f0d2104373ea797ff9403cc417dfaa3d868
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598852"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a><span data-ttu-id="9a079-102">OLE DB API 對日期和時間增強功能的支援</span><span class="sxs-lookup"><span data-stu-id="9a079-102">OLE DB API Support for Date and Time Enhancements</span></span>
  <span data-ttu-id="9a079-103">下列 OLE DB API 支援日期/時間增強功能。</span><span class="sxs-lookup"><span data-stu-id="9a079-103">The following OLE DB APIs support enhanced date/time features.</span></span>  
  
|<span data-ttu-id="9a079-104">函式</span><span class="sxs-lookup"><span data-stu-id="9a079-104">Function</span></span>|<span data-ttu-id="9a079-105">描述</span><span class="sxs-lookup"><span data-stu-id="9a079-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9a079-106">IAccessor::CreateAccessor</span><span class="sxs-lookup"><span data-stu-id="9a079-106">IAccessor::CreateAccessor</span></span>|<span data-ttu-id="9a079-107">在 DBBINDING 結構中加入一個旗標，好讓應用程式可以區分 `datetime`、`datetime2` 和 `smalldatetime` 值。</span><span class="sxs-lookup"><span data-stu-id="9a079-107">A flag is added in the DBBINDING structure to enable applications to discriminate between `datetime`, `datetime2`, and `smalldatetime` values.</span></span> <span data-ttu-id="9a079-108">如需詳細資訊，請參閱[參數和資料列集中繼資料](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-108">For more information, see [Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="9a079-109">IBCPSession::BCPColFmt</span><span class="sxs-lookup"><span data-stu-id="9a079-109">IBCPSession::BCPColFmt</span></span>|<span data-ttu-id="9a079-110">如需詳細資訊，請參閱[增強型日期和時間類型的大量複製變更 &#40;OLE DB 和 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-110">For more information, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>|  
|<span data-ttu-id="9a079-111">ICommandWithParameters::GetParameterInfo</span><span class="sxs-lookup"><span data-stu-id="9a079-111">ICommandWithParameters::GetParameterInfo</span></span>|<span data-ttu-id="9a079-112">如需詳細資訊，請參閱[參數和資料列集中繼資料](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-112">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="9a079-113">ICommandWithParameters::SetParameterinfo</span><span class="sxs-lookup"><span data-stu-id="9a079-113">ICommandWithParameters::SetParameterinfo</span></span>|<span data-ttu-id="9a079-114">如需詳細資訊，請參閱[參數和資料列集中繼資料](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-114">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="9a079-115">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="9a079-115">IColumnsRowset::GetColumnsRowset</span></span>|<span data-ttu-id="9a079-116">如需詳細資訊，請參閱[參數和資料列集中繼資料](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-116">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="9a079-117">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="9a079-117">IColumnsInfo::GetColumnInfo</span></span>|<span data-ttu-id="9a079-118">如需詳細資訊，請參閱[參數和資料列集中繼資料](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-118">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="9a079-119">IDBSchemaRowset::GetRowset</span><span class="sxs-lookup"><span data-stu-id="9a079-119">IDBSchemaRowset::GetRowset</span></span>|<span data-ttu-id="9a079-120">如需受影響結構描述資料列集的詳細資訊，請參閱[日期和時間以及結構描述資料列集](../native-client-ole-db-rowsets/rowsets.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-120">For details of the affected schema rowsets, see[Date and Time and Schema Rowsets](../native-client-ole-db-rowsets/rowsets.md).</span></span>|  
|<span data-ttu-id="9a079-121">IRowsetFastLoad</span><span class="sxs-lookup"><span data-stu-id="9a079-121">IRowsetFastLoad</span></span>|<span data-ttu-id="9a079-122">此介面支援新的日期/時間類型，但是它的介面沒有任何變更。</span><span class="sxs-lookup"><span data-stu-id="9a079-122">This interface supports the new date/time types, but there is no change to its interface.</span></span>|  
|<span data-ttu-id="9a079-123">ITableDefinition::CreateTable</span><span class="sxs-lookup"><span data-stu-id="9a079-123">ITableDefinition::CreateTable</span></span>|<span data-ttu-id="9a079-124">如需詳細資訊，請參閱[對 OLE DB 日期和時間改善的資料類型支援](data-type-support-for-ole-db-date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a079-124">For more information, see [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a079-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a079-125">See Also</span></span>  
 [<span data-ttu-id="9a079-126">日期和時間改善 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9a079-126">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
