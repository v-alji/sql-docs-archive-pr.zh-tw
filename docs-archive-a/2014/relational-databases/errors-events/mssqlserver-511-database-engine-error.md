---
title: MSSQLSERVER_511 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b69d2c043997e2947563de119bc4ee89fdf4e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698239"
---
# <a name="mssqlserver_511"></a><span data-ttu-id="a1819-102">MSSQLSERVER_511</span><span class="sxs-lookup"><span data-stu-id="a1819-102">MSSQLSERVER_511</span></span>
    
## <a name="details"></a><span data-ttu-id="a1819-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1819-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1819-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a1819-104">Product Name</span></span>|<span data-ttu-id="a1819-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a1819-105">SQL Server</span></span>|  
|<span data-ttu-id="a1819-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a1819-106">Event ID</span></span>|<span data-ttu-id="a1819-107">511</span><span class="sxs-lookup"><span data-stu-id="a1819-107">511</span></span>|  
|<span data-ttu-id="a1819-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a1819-108">Event Source</span></span>|<span data-ttu-id="a1819-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a1819-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a1819-110">元件</span><span class="sxs-lookup"><span data-stu-id="a1819-110">Component</span></span>|<span data-ttu-id="a1819-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a1819-111">SQLEngine</span></span>|  
|<span data-ttu-id="a1819-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a1819-112">Symbolic Name</span></span>|<span data-ttu-id="a1819-113">ROW_TOOBIG</span><span class="sxs-lookup"><span data-stu-id="a1819-113">ROW_TOOBIG</span></span>|  
|<span data-ttu-id="a1819-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a1819-114">Message Text</span></span>|<span data-ttu-id="a1819-115">當 %d 大小的資料列大於允許的最大 %d 時，便無法建立它。</span><span class="sxs-lookup"><span data-stu-id="a1819-115">Cannot create a row of size %d which is greater than the allowable maximum of %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a1819-116">說明</span><span class="sxs-lookup"><span data-stu-id="a1819-116">Explanation</span></span>  
 <span data-ttu-id="a1819-117">您嘗試執行的作業超出資料列大小的上限。</span><span class="sxs-lookup"><span data-stu-id="a1819-117">The operation you have tried has exceeded the maximum size of a row.</span></span> <span data-ttu-id="a1819-118">通常資料列大小的上限為 8,060 個位元組。</span><span class="sxs-lookup"><span data-stu-id="a1819-118">Usually, the maximum size of a row is 8,060 bytes.</span></span> <span data-ttu-id="a1819-119">某些儲存格式包含的負擔可能會減少資料可使用的資料列大小。</span><span class="sxs-lookup"><span data-stu-id="a1819-119">Some storage formats contain overhead that can reduce the row size that is available for data.</span></span> <span data-ttu-id="a1819-120">例如，當您使用疏鬆資料行時，資料列大小的上限為 8,018 個位元組。</span><span class="sxs-lookup"><span data-stu-id="a1819-120">For example, when you use sparse columns, the maximum size of a row is 8,018 bytes.</span></span> <span data-ttu-id="a1819-121">加入或移除資料列的某些作業及變更資料行之資料類型的某些作業需要將資料列重寫到資料頁面，然後移除原始的資料列。</span><span class="sxs-lookup"><span data-stu-id="a1819-121">Some operations that add or remove rows and some operations that change the data type of a column require the row to be rewritten on the data page, and then the original row is removed.</span></span> <span data-ttu-id="a1819-122">在這些作業中，資料列大小的有效限制為上限的一半。</span><span class="sxs-lookup"><span data-stu-id="a1819-122">In these operations, the effective limit to the size of the row is half the maximum limit.</span></span> <span data-ttu-id="a1819-123">這是因為原始的資料列和修改過的資料列短期內都必須包含在資料頁面上。</span><span class="sxs-lookup"><span data-stu-id="a1819-123">This is because the original row and the modified row must both be contained on the data page for a short period.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a1819-124">每個非 null 的\*\*Varchar (max) **或**Nvarchar (max) \*\*資料行都需要額外24個位元組的固定配置，以在排序作業期間計算8060位元組的資料列限制。</span><span class="sxs-lookup"><span data-stu-id="a1819-124">Each non-null  **varchar(max)** or **nvarchar(max)** column requires 24 bytes of additional fixed allocation which counts against the 8,060 byte row limit during a sort operation.</span></span> <span data-ttu-id="a1819-125">這可能會對可在資料表中建立的非 null \*\*Varchar (max) **或**Nvarchar (最大) \*\*資料行數目建立隱含限制。</span><span class="sxs-lookup"><span data-stu-id="a1819-125">This can create an implicit limit to the number of non-null **varchar(max)** or **nvarchar(max)** columns that can be created in a table.</span></span> <span data-ttu-id="a1819-126">建立資料表時 (高於最大資料列大小超過允許上限 8060 位元組所引發的一般警告) 或插入資料時，不會提供任何特殊錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1819-126">No special error is provided when the table is created (beyond the usual warning that the maximum row size exceeds the allowed maximum of 8060 bytes) or at the time of data insertion.</span></span> <span data-ttu-id="a1819-127">如此大型的資料列可能會在某些一般作業 (如叢集索引鍵更新) 期間造成錯誤 (如錯誤 512)，或讓使用者直到執行作業前都無法預期多種完整資料行集。</span><span class="sxs-lookup"><span data-stu-id="a1819-127">This large row size can cause errors (such as error 512) during some normal operations, such as a clustered index key update, or sorts of the full column set, which users cannot anticipate until performing an operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1819-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a1819-128">User Action</span></span>  
 <span data-ttu-id="a1819-129">如果可能的話，請縮減此資料列的大小。</span><span class="sxs-lookup"><span data-stu-id="a1819-129">If it is possible, reduce the size of the row.</span></span>  
  
 <span data-ttu-id="a1819-130">如果您認為問題是因為資料列的就地更新所造成，您必須使用多個步驟變更資料表。</span><span class="sxs-lookup"><span data-stu-id="a1819-130">If you think the problem is caused by an in-place update of the row, you must change the table in multiple steps.</span></span> <span data-ttu-id="a1819-131">建立新的資料表，然後將資料傳送到新的資料表內。</span><span class="sxs-lookup"><span data-stu-id="a1819-131">Create a new table, and transfer the data into the new table.</span></span> <span data-ttu-id="a1819-132">然後刪除原始資料表並將新的資料表重新命名，或是截斷原始資料表、修改原始資料表內的資料列，然後將資料移回其中。</span><span class="sxs-lookup"><span data-stu-id="a1819-132">Then, either delete the original table and rename the new table, or truncate the original table, modify the rows in the original table, and then move the data back into it.</span></span>  
  
  
