---
title: 順序屬性 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sequence.general.f1
ms.assetid: 0187f413-cdf0-48a2-b2e6-9b3578cd5811
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc969dc09663da8150461529ad1e1f1fb094539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709042"
---
# <a name="sequence-properties-general-page"></a><span data-ttu-id="c0e7c-102">順序屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="c0e7c-102">Sequence Properties (General Page)</span></span>
  <span data-ttu-id="c0e7c-103">建立順序物件，並指定其屬性。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-103">Creates a sequence object and specifies its properties.</span></span> <span data-ttu-id="c0e7c-104">序列是使用者定義之結構描述繫結的物件，該物件會根據建立序列所使用的規格產生一連串的數值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-104">A sequence is a user-defined schema bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="c0e7c-105">數值序列會在定義的間隔依照遞增或遞減順序來產生，而且在用完時可設定為重新啟動 (循環)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-105">The sequence of numeric values is generated in an ascending or descending order at a defined interval and can be configured to restart (cycle) when exhausted.</span></span> <span data-ttu-id="c0e7c-106">順序不會與特定資料表產生關聯，與識別欄位不同。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-106">Sequences, unlike identity columns, are not associated with specific tables.</span></span> <span data-ttu-id="c0e7c-107">應用程式會參考順序物件，以擷取它的下一個值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-107">Applications refer to a sequence object to retrieve its next value.</span></span> <span data-ttu-id="c0e7c-108">順序與資料表之間的關聯性是由應用程式所控制。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-108">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="c0e7c-109">使用者的應用程式可以參考序列物件，並協調跨越多個資料列和資料表的值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-109">User applications can reference a sequence object and coordinate the values across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="c0e7c-110">不同於插入時產生的識別資料行值，應用程式可以藉由呼叫 [NEXT VALUE FOR 函數](/sql/t-sql/functions/next-value-for-transact-sql)取得下一個序數，而不需要插入資料列。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-110">Unlike identity columns values which are generated at the time of insert, an application can obtain the next sequence number without inserting the row by calling the [NEXT VALUE FOR function](/sql/t-sql/functions/next-value-for-transact-sql).</span></span> <span data-ttu-id="c0e7c-111">您可以使用 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 一次取得多個序號。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-111">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="c0e7c-112">如需使用 **CREATE SEQUENCE** 和 **NEXT VALUE FOR** 函數的相關資訊和案例，請參閱 [序號](sequence-numbers.md)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-112">For information and scenarios that use both **CREATE SEQUENCE** and the **NEXT VALUE FOR** function, see [Sequence Numbers](sequence-numbers.md).</span></span>  
  
 <span data-ttu-id="c0e7c-113">此頁面可經由兩種方式存取：以滑鼠右鍵按一下 [物件總管] 中的 [順序]  ，然後按一下 [新增順序]  ，或者以滑鼠右鍵按一下現有的順序，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-113">This page is accessed in two ways: either by right-clicking **Sequences** in Object Explorer and clicking **New Sequence**, or by right-clicking an existing sequence and clicking **Properties**.</span></span> <span data-ttu-id="c0e7c-114">以滑鼠右鍵按一下現有的順序，然後按一下 [屬性]  時，無法編輯選項。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-114">When you right-click an existing sequence and click **Properties**, the options are not editable.</span></span> <span data-ttu-id="c0e7c-115">若要變更順序選項，請使用 [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) 陳述式或卸除然後重新建立順序物件。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-115">To change the sequence options use the [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) statement or drop and recreate the sequence object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0e7c-116">選項。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-116">Options</span></span>  
 <span data-ttu-id="c0e7c-117">**順序名稱**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-117">**Sequence name**</span></span>  
 <span data-ttu-id="c0e7c-118">在此處輸入順序名稱。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-118">Enter the sequence name here.</span></span>  
  
 <span data-ttu-id="c0e7c-119">**順序結構描述**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-119">**Sequence schema**</span></span>  
 <span data-ttu-id="c0e7c-120">指定將擁有此順序的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-120">Specify the schema that will own this sequence.</span></span>  
  
 <span data-ttu-id="c0e7c-121">**Data type**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-121">**Data type**</span></span>  
 <span data-ttu-id="c0e7c-122">順序可以定義為任何整數類型。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-122">A sequence can be defined as any integer type.</span></span> <span data-ttu-id="c0e7c-123">這包括：</span><span class="sxs-lookup"><span data-stu-id="c0e7c-123">This includes:</span></span>  
  
|<span data-ttu-id="c0e7c-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="c0e7c-124">Data type</span></span>|<span data-ttu-id="c0e7c-125">範圍</span><span class="sxs-lookup"><span data-stu-id="c0e7c-125">Range</span></span>|  
|---------------|-----------|  
|`tinyint`|<span data-ttu-id="c0e7c-126">0 至 255</span><span class="sxs-lookup"><span data-stu-id="c0e7c-126">0 to 255</span></span>|  
|`smallint`|<span data-ttu-id="c0e7c-127">-32,768 至 32,767</span><span class="sxs-lookup"><span data-stu-id="c0e7c-127">-32,768 to 32,767</span></span>|  
|`int`|<span data-ttu-id="c0e7c-128">-2,147,483,648 至 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="c0e7c-128">-2,147,483,648 to 2,147,483,647</span></span>|  
|`bigint`|<span data-ttu-id="c0e7c-129">-9,223,372,036,854,775,808 至 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="c0e7c-129">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|  
  
-   <span data-ttu-id="c0e7c-130">`decimal` 或小數位數為 0 的 `numeric`。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-130">`decimal` or `numeric` with a scale of 0.</span></span>  
  
-   <span data-ttu-id="c0e7c-131">以這些類型之一為基礎的任何使用者定義的資料類型 (別名類型)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-131">Any user-defined data type (alias type) that is based on one of these types.</span></span>  
  
 <span data-ttu-id="c0e7c-132">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-132">**Precision**</span></span>  
 <span data-ttu-id="c0e7c-133">如果是 `decimal` 或 `numeric` 資料類型，請指定有效位數 </span><span class="sxs-lookup"><span data-stu-id="c0e7c-133">For `decimal` or `numeric` data types, specify the precision.</span></span> <span data-ttu-id="c0e7c-134">(小數位數一定是 0)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-134">(The scale is always 0.)</span></span>  
  
 <span data-ttu-id="c0e7c-135">**開始值**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-135">**Start with value**</span></span>  
 <span data-ttu-id="c0e7c-136">順序物件會傳回的第一個值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-136">The first value that will be returned by the sequence object.</span></span> <span data-ttu-id="c0e7c-137">**START** 值必須是小於或等於順序物件的最大值，而且大於或等於最小值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-137">The **START** value must be a value that is less than or equal to the maximum and greater than or equal to the minimum value of the sequence object.</span></span> <span data-ttu-id="c0e7c-138">新順序物件的預設開始值是遞增順序物件的最小值，是遞減順序物件的最大值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-138">The default start value for a new sequence object is the minimum value for an ascending sequence object and the maximum value for a descending sequence object.</span></span>  
  
 <span data-ttu-id="c0e7c-139">**遞增量**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-139">**Increment by**</span></span>  
 <span data-ttu-id="c0e7c-140">每次呼叫 **NEXT VALUE FOR** 函數時，用來遞增順序物件值的值 (如果是負數則遞減)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-140">The value that is used to increment (or decrement if negative) the value of the sequence object for each call to the **NEXT VALUE FOR** function.</span></span> <span data-ttu-id="c0e7c-141">如果增量是負值，則會遞減順序物件，否則會遞增。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-141">If the increment is a negative value the sequence object is descending, otherwise, it is ascending.</span></span> <span data-ttu-id="c0e7c-142">增量不能為 0。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-142">The increment cannot be 0.</span></span>  
  
 <span data-ttu-id="c0e7c-143">**最小值**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-143">**Minimum value**</span></span>  
 <span data-ttu-id="c0e7c-144">指定順序物件的界限。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-144">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="c0e7c-145">新序列物件的預設最小值是序列物件之資料類型的最小值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-145">The default minimum value for a new sequence object is the minimum value of the data type of the sequence object.</span></span> <span data-ttu-id="c0e7c-146">如果是 `tinyint` 資料類型，這是零，如果是所有其他資料類型，則為負數。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-146">This is zero for the `tinyint` data type and a negative number for all other data types.</span></span>  
  
 <span data-ttu-id="c0e7c-147">**最大值**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-147">**Maximum value**</span></span>  
 <span data-ttu-id="c0e7c-148">指定順序物件的界限。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-148">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="c0e7c-149">新序列物件的預設最大值是序列物件之資料類型的最大值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-149">The default maximum value for a new sequence object is the maximum value of the data type of the sequence object.</span></span>  
  
 <span data-ttu-id="c0e7c-150">**在達到限制時循環順序將會重新啟動**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-150">**Cycle-sequence will restart on reaching limit**</span></span>  
 <span data-ttu-id="c0e7c-151">選取以允許當超出其最小值或最大值時，順序物件從最小值 (或是遞減順序物件的最大值) 重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-151">Select to allow the sequence object to restart from the minimum value (or maximum for descending sequence objects) when its minimum or maximum value is exceeded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0e7c-152">循環並不會從開始值重新啟動，而是從最小值/最大值重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-152">Cycling does not restart from the start value but rather from the minimum/maximum value.</span></span>  
  
 <span data-ttu-id="c0e7c-153">**快取選項**</span><span class="sxs-lookup"><span data-stu-id="c0e7c-153">**Cache options**</span></span>  
 <span data-ttu-id="c0e7c-154">建立順序值的快取，可藉由減少建立序號所需的磁碟 IO 數目，對使用順序物件的應用程式提升效能。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-154">Creating a cache of sequence values can increase performance for applications that use sequence objects by minimizing the number of disk IOs that are required to create sequence numbers.</span></span>  
  
-   <span data-ttu-id="c0e7c-155">預設快取大小 - [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會選取大小，但是使用者不應該依賴此選取來取得一致的結果。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-155">Default cache size - The [!INCLUDE[ssDE](../../includes/ssde-md.md)] will select a size, however users should not rely upon the selection being consistent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c0e7c-156">可能變更計算快取大小的方法，而不另行通知。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-156">might change the method of calculating the cache size without notice.</span></span>  
  
-   <span data-ttu-id="c0e7c-157">無快取 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會快取序號。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-157">No cache - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will not cache sequence numbers.</span></span>  
  
-   <span data-ttu-id="c0e7c-158">快取與大小 - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會快取順序值。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-158">Cache with size - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will cache sequence values.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c0e7c-159">會追蹤目前值，以及留在快取中的值數目。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-159">keeps track of the current value and the number of values left in the cache.</span></span> <span data-ttu-id="c0e7c-160">因此，儲存快取所需的記憶體數量永遠是順序物件之資料類型的兩個執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-160">Therefore, the amount of memory that is required to store the cache is always two instances of the data type of the sequence object</span></span>  
  
 <span data-ttu-id="c0e7c-161">以 CACHE 選項建立時，非預期關閉 (例如停電) 可能會失去快取中的序號。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-161">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="c0e7c-162">如需有關建立順序選項的詳細資訊，請參閱 [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-162">For additional information about the create sequence options, see [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c0e7c-163">權限</span><span class="sxs-lookup"><span data-stu-id="c0e7c-163">Permissions</span></span>  
 <span data-ttu-id="c0e7c-164">需要 SCHEMA 的 **CREATE SEQUENCE**、 **ALTER**或 **CONTROL** 權限。</span><span class="sxs-lookup"><span data-stu-id="c0e7c-164">Requires **CREATE SEQUENCE**, **ALTER**, or **CONTROL** permission on the SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e7c-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0e7c-165">See Also</span></span>  
 [<span data-ttu-id="c0e7c-166">sys.sequences &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c0e7c-166">sys.sequences &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)  
  
  
