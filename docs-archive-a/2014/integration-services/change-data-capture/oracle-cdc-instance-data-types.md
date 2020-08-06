---
title: Oracle CDC 執行個體資料類型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71d4ce02db89c1bfd11fe9a3a3535fc92fbc49fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687103"
---
# <a name="oracle-cdc-instance-data-types"></a><span data-ttu-id="cf44e-102">Oracle CDC 執行個體資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-102">Oracle CDC Instance Data Types</span></span>
  <span data-ttu-id="cf44e-103">Oracle CDC 執行個體支援大多數的 Oracle 資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf44e-103">The Oracle CDC Instance supports most Oracle data types.</span></span> <span data-ttu-id="cf44e-104">以下章節描述支援的資料類型和不支援的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf44e-104">The following sections describe the supported data types and the non-supported data types.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="cf44e-105">支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-105">Supported Data Types</span></span>  
 <span data-ttu-id="cf44e-106">下表描述可以擷取的 Oracle 資料類型，以及變更資料表中這些類型與 SQL Server 資料類型的預設對應。</span><span class="sxs-lookup"><span data-stu-id="cf44e-106">The following table describes the Oracle data types that can be captured and their default mapping to SQL Server data types in the change tables.</span></span> <span data-ttu-id="cf44e-107">為來源 Oracle 資料表加入擷取執行個體時，您可以覆寫這些對應的一部分。</span><span class="sxs-lookup"><span data-stu-id="cf44e-107">When adding a capture instance for a source Oracle table, you can override some of these mappings.</span></span>  
  
|<span data-ttu-id="cf44e-108">Oracle 資料庫資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-108">Oracle Database Data Type</span></span>|<span data-ttu-id="cf44e-109">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-109">SQL Server Data Type</span></span>|  
|-------------------------------|--------------------------|  
|<span data-ttu-id="cf44e-110">BINARY_FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-110">BINARY_FLOAT</span></span>|<span data-ttu-id="cf44e-111">real</span><span class="sxs-lookup"><span data-stu-id="cf44e-111">REAL</span></span>|  
|<span data-ttu-id="cf44e-112">BINARY_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="cf44e-112">BINARY_DOUBLE</span></span>|<span data-ttu-id="cf44e-113">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-113">FLOAT</span></span>|  
|<span data-ttu-id="cf44e-114">CHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-114">CHAR</span></span>|<span data-ttu-id="cf44e-115">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-115">NVARCHAR</span></span>|  
|<span data-ttu-id="cf44e-116">日期</span><span class="sxs-lookup"><span data-stu-id="cf44e-116">DATE</span></span>|<span data-ttu-id="cf44e-117">DATETIME</span><span class="sxs-lookup"><span data-stu-id="cf44e-117">DATETIME</span></span>|  
|<span data-ttu-id="cf44e-118">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-118">FLOAT</span></span>|<span data-ttu-id="cf44e-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-119">FLOAT</span></span>|  
|<span data-ttu-id="cf44e-120">INT</span><span class="sxs-lookup"><span data-stu-id="cf44e-120">INT</span></span>|<span data-ttu-id="cf44e-121">NUMERIC (38)</span><span class="sxs-lookup"><span data-stu-id="cf44e-121">NUMERIC (38)</span></span>|  
|<span data-ttu-id="cf44e-122">INTERVAL</span><span class="sxs-lookup"><span data-stu-id="cf44e-122">INTERVAL</span></span>|<span data-ttu-id="cf44e-123">DATETIME</span><span class="sxs-lookup"><span data-stu-id="cf44e-123">DATETIME</span></span>|  
|<span data-ttu-id="cf44e-124">NCHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-124">NCHAR</span></span>|<span data-ttu-id="cf44e-125">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-125">NVARCHAR</span></span>|  
|<span data-ttu-id="cf44e-126">NUMBER</span><span class="sxs-lookup"><span data-stu-id="cf44e-126">NUMBER</span></span>|<span data-ttu-id="cf44e-127">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-127">FLOAT</span></span>|  
|<span data-ttu-id="cf44e-128">NAVARCHAR2</span><span class="sxs-lookup"><span data-stu-id="cf44e-128">NAVARCHAR2</span></span>|<span data-ttu-id="cf44e-129">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-129">NVARCHAR</span></span>|  
|<span data-ttu-id="cf44e-130">RAW</span><span class="sxs-lookup"><span data-stu-id="cf44e-130">RAW</span></span>|<span data-ttu-id="cf44e-131">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="cf44e-131">VARBINARY</span></span>|  
|<span data-ttu-id="cf44e-132">real</span><span class="sxs-lookup"><span data-stu-id="cf44e-132">REAL</span></span>|<span data-ttu-id="cf44e-133">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cf44e-133">FLOAT</span></span>|  
|<span data-ttu-id="cf44e-134">timestamp</span><span class="sxs-lookup"><span data-stu-id="cf44e-134">TIMESTAMP</span></span>|<span data-ttu-id="cf44e-135">DATETIME2</span><span class="sxs-lookup"><span data-stu-id="cf44e-135">DATETIME2</span></span>|  
|<span data-ttu-id="cf44e-136">TIMESTAMP WITH TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="cf44e-136">TIMESTAMP WITH TIME ZONE</span></span>|<span data-ttu-id="cf44e-137">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="cf44e-137">VARCHAR (37)</span></span>|  
|<span data-ttu-id="cf44e-138">TIMESTAMP WITH LOCAL TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="cf44e-138">TIMESTAMP WITH LOCAL TIME ZONE</span></span>|<span data-ttu-id="cf44e-139">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="cf44e-139">VARCHAR (37)</span></span>|  
|<span data-ttu-id="cf44e-140">VARCHAR2</span><span class="sxs-lookup"><span data-stu-id="cf44e-140">VARCHAR2</span></span>|<span data-ttu-id="cf44e-141">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf44e-141">VARCHAR</span></span>|  
|<span data-ttu-id="cf44e-142">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="cf44e-142">XMLTYPE</span></span>|<span data-ttu-id="cf44e-143">NVARCHAR (MAX)</span><span class="sxs-lookup"><span data-stu-id="cf44e-143">NVARCHAR (MAX)</span></span>|  
  
## <a name="non-supported-data-types"></a><span data-ttu-id="cf44e-144">不支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-144">Non-Supported Data Types</span></span>  
 <span data-ttu-id="cf44e-145">如果來源 Oracle 資料表中的資料行具有以下 Oracle 資料類型，則無法擷取這些資料表。</span><span class="sxs-lookup"><span data-stu-id="cf44e-145">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span> <span data-ttu-id="cf44e-146">如果擷取的資料行具有這些資料類型，則會顯示為 null；但是，其值的變更會在擷取之資料表的變更遮罩中指示。</span><span class="sxs-lookup"><span data-stu-id="cf44e-146">Captured columns with these data types will show as null; however, a change in their value is indicated in the change mask of the captured tables.</span></span>  
  
-   <span data-ttu-id="cf44e-147">LONG</span><span class="sxs-lookup"><span data-stu-id="cf44e-147">LONG</span></span>  
  
-   <span data-ttu-id="cf44e-148">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="cf44e-148">XMLTYPE</span></span>  
  
-   <span data-ttu-id="cf44e-149">BLOB</span><span class="sxs-lookup"><span data-stu-id="cf44e-149">BLOB</span></span>  
  
-   <span data-ttu-id="cf44e-150">CLOB</span><span class="sxs-lookup"><span data-stu-id="cf44e-150">CLOB</span></span>  
  
 <span data-ttu-id="cf44e-151">如果來源 Oracle 資料表中的資料行具有以下 Oracle 資料類型，則無法擷取這些資料表。</span><span class="sxs-lookup"><span data-stu-id="cf44e-151">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span>  
  
-   <span data-ttu-id="cf44e-152">BFILE</span><span class="sxs-lookup"><span data-stu-id="cf44e-152">BFILE</span></span>  
  
-   <span data-ttu-id="cf44e-153">ROWID</span><span class="sxs-lookup"><span data-stu-id="cf44e-153">ROWID</span></span>  
  
-   <span data-ttu-id="cf44e-154">REF</span><span class="sxs-lookup"><span data-stu-id="cf44e-154">REF</span></span>  
  
-   <span data-ttu-id="cf44e-155">UROWID</span><span class="sxs-lookup"><span data-stu-id="cf44e-155">UROWID</span></span>  
  
-   <span data-ttu-id="cf44e-156">巢狀資料表</span><span class="sxs-lookup"><span data-stu-id="cf44e-156">Nested Table</span></span>  
  
 <span data-ttu-id="cf44e-157">如果資料表中有以下資料類型存在，這些資料類型會讓 LogMinder 無法針對資料表的任何資料行取得任何資料：</span><span class="sxs-lookup"><span data-stu-id="cf44e-157">If the following data types are present in a table they will prevent the LogMinder from getting any data for any column of the table:</span></span>  
  
-   <span data-ttu-id="cf44e-158">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="cf44e-158">User-defined data types</span></span>  
  
-   <span data-ttu-id="cf44e-159">VARRAY</span><span class="sxs-lookup"><span data-stu-id="cf44e-159">VARRAY</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf44e-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf44e-160">See Also</span></span>  
 <span data-ttu-id="cf44e-161">[Attunity Oracle 異動資料擷取設計工具](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="cf44e-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="cf44e-162">Oracle CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="cf44e-162">The Oracle CDC Instance</span></span>](the-oracle-cdc-instance.md)  
  
  
