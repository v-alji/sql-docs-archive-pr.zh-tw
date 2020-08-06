---
title: 針對 OLE DB 資料表值參數而變更的結構描述資料列集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: rothja
ms.author: jroth
ms.openlocfilehash: e09d5127f332c8b6cc948be3eeb74e600bb856f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707441"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a><span data-ttu-id="486db-102">針對 OLE DB 資料表值參數而變更的結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="486db-102">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>
  <span data-ttu-id="486db-103">下列是已變更或加入來支援資料表值參數的結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="486db-103">The following are the schema rowsets that have been changed or added to support table-valued parameters.</span></span>  
  
|<span data-ttu-id="486db-104">結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="486db-104">Schema rowset</span></span>|<span data-ttu-id="486db-105">描述</span><span class="sxs-lookup"><span data-stu-id="486db-105">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="486db-106">DBSCHEMA_PROCEDURE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="486db-106">DBSCHEMA_PROCEDURE_PARAMETERS</span></span>|<span data-ttu-id="486db-107">兩個新的資料行會加在名為 SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMANAME 的資料列集結尾。</span><span class="sxs-lookup"><span data-stu-id="486db-107">Two new columns were added at the end of the rowset named SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMANAME.</span></span> <span data-ttu-id="486db-108">這些資料行可以針對未來的類型重複使用。</span><span class="sxs-lookup"><span data-stu-id="486db-108">These columns could be re-used for future types.</span></span> <span data-ttu-id="486db-109">TYPE_NAME 和 LOCAL_TYPE_NAME 資料行會包含 TABLE 類型的資料表值參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="486db-109">The TYPE_NAME and LOCAL_TYPE_NAME columns will contain the name of the table-valued parameter TABLE type.</span></span> <span data-ttu-id="486db-110">DATA_TYPE 資料行對於資料表值參數具有 DBTYPE_TABLE = 143 值。</span><span class="sxs-lookup"><span data-stu-id="486db-110">The DATA_TYPE column will have value DBTYPE_TABLE = 143 for table-valued parameters.</span></span>|  
|<span data-ttu-id="486db-111">DBSCHEMA_TABLE_TYPES</span><span class="sxs-lookup"><span data-stu-id="486db-111">DBSCHEMA_TABLE_TYPES</span></span>|<span data-ttu-id="486db-112">已新增這個資料列集來支援資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="486db-112">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="486db-113">這與 DBSCHEMA_TABLES 完全相同，但它只會針對資料表類型 (而不會針對資料表、檢視或同義字) 傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="486db-113">It is identical to DBSCHEMA_TABLES, except that it returns metadata only for table types, rather than for tables, views, or synonyms.</span></span> <span data-ttu-id="486db-114">TABLE_TYPE 資料行會具有 'TABLE TYPE' 值。</span><span class="sxs-lookup"><span data-stu-id="486db-114">The TABLE_TYPE column will have the value 'TABLE TYPE'.</span></span>|  
|<span data-ttu-id="486db-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="486db-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span></span>|<span data-ttu-id="486db-116">已新增這個資料列集來支援資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="486db-116">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="486db-117">這與 DBSCHEMA_PRIMARY_KEYS 完全相同，但它只會針對資料表類型 (而不會針對資料表) 傳回主索引鍵中繼資料。</span><span class="sxs-lookup"><span data-stu-id="486db-117">It is identical to DBSCHEMA_PRIMARY_KEYS, except that it returns primary keys metadata only for table types, rather than for tables.</span></span>|  
|<span data-ttu-id="486db-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="486db-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span></span>|<span data-ttu-id="486db-119">已新增這個資料列集來支援資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="486db-119">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="486db-120">這與 DBSCHEMA_COLUMNS 完全相同，但它只會針對資料表類型 (而不會針對資料表、檢視或同義字) 傳回資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="486db-120">It is identical to DBSCHEMA_COLUMNS, except that it returns column metadata only for table types, rather than for tables, views, or synonyms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="486db-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="486db-121">See Also</span></span>  
 <span data-ttu-id="486db-122">[資料表值參數 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="486db-122">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="486db-123">使用資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="486db-123">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
