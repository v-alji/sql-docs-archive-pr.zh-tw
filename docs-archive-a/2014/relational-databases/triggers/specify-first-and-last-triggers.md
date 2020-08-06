---
title: 指定第一個與最後一個觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- first triggers [SQL Server]
- last triggers
- DML triggers, first or last triggers
- INSTEAD OF triggers
- AFTER triggers
ms.assetid: 9e6c7684-3dd3-46bb-b7be-523b33fae4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddb352b00dc759362c8f6ef1e861e55b6f184f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606117"
---
# <a name="specify-first-and-last-triggers"></a><span data-ttu-id="4b9f8-102">指定第一個與最後一個觸發程序</span><span class="sxs-lookup"><span data-stu-id="4b9f8-102">Specify First and Last Triggers</span></span>
  <span data-ttu-id="4b9f8-103">您可以指定與資料表關聯的其中一個 AFTER 觸發程序，做為針對每一個 INSERT、DELETE 和 UPDATE 觸發動作而引發的第一個或最後一個 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-103">You can specify that one of the AFTER triggers associated with a table be either the first AFTER trigger or the last AFTER trigger that is fired for each INSERT, DELETE, and UPDATE triggering actions.</span></span> <span data-ttu-id="4b9f8-104">在第一個及最後一個觸發程序之間啟動的 AFTER 觸發程序，會以未定義的順序執行。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-104">The AFTER triggers that are fired between the first and last triggers are executed in undefined order.</span></span>  
  
 <span data-ttu-id="4b9f8-105">若要指定 AFTER 觸發程序的順序，請使用 **sp_settriggerorder** 預存程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-105">To specify the order for an AFTER trigger, use the **sp_settriggerorder** stored procedure.</span></span> <span data-ttu-id="4b9f8-106">**sp_settriggerorder** 具有下列選項。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-106">**sp_settriggerorder** has the following options.</span></span>  
  
|<span data-ttu-id="4b9f8-107">選項</span><span class="sxs-lookup"><span data-stu-id="4b9f8-107">Option</span></span>|<span data-ttu-id="4b9f8-108">描述</span><span class="sxs-lookup"><span data-stu-id="4b9f8-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4b9f8-109">**第一個**</span><span class="sxs-lookup"><span data-stu-id="4b9f8-109">**First**</span></span>|<span data-ttu-id="4b9f8-110">指定 DML 觸發程序為針對觸發動作而引發的第一個 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-110">Specifies that the DML trigger is the first AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="4b9f8-111">**最後一個**</span><span class="sxs-lookup"><span data-stu-id="4b9f8-111">**Last**</span></span>|<span data-ttu-id="4b9f8-112">指定 DML 觸發程序為針對觸發動作而引發的最後一個 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-112">Specifies that the DML trigger is the last AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="4b9f8-113">**None**</span><span class="sxs-lookup"><span data-stu-id="4b9f8-113">**None**</span></span>|<span data-ttu-id="4b9f8-114">指定 DML 觸發程序的引發並無特定的順序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-114">Specifies that there is no specific order in which the DML trigger should be fired.</span></span> <span data-ttu-id="4b9f8-115">主要用來重設第一個或最後一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-115">Used mainly to reset a trigger from being either first or last.</span></span>|  
  
 <span data-ttu-id="4b9f8-116">下列範例示範如何使用 **sp_settriggerorder**：</span><span class="sxs-lookup"><span data-stu-id="4b9f8-116">The following example shows using **sp_settriggerorder**:</span></span>  
  
```  
sp_settriggerorder @triggername = 'MyTrigger', @order = 'first', @stmttype = 'UPDATE'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b9f8-117">第一個及最後一個觸發程序，必須是兩個不同的 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-117">The first and last triggers must be two different DML triggers.</span></span>  
  
 <span data-ttu-id="4b9f8-118">可以同時對一個資料表定義 INSERT、UPDATE 及 DELETE 等觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-118">A table can have INSERT, UPDATE, and DELETE triggers defined on it at the same time.</span></span> <span data-ttu-id="4b9f8-119">每個陳述式類型都可以擁有它自己的第一個及最後一個觸發程序，但它們不得為相同的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-119">Each statement type can have its own first and last triggers, but they cannot be the same triggers.</span></span>  
  
 <span data-ttu-id="4b9f8-120">如果針對某資料表定義的第一個或最後一個觸發程序並不涵蓋觸發動作，例如未涵蓋 FOR UPDATE、FOR DELETE 或 FOR INSERT，則遺漏的動作不會有第一個或最後一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-120">If the first or last trigger defined for a table does not cover a triggering action, such as not covering FOR UPDATE, FOR DELETE, or FOR INSERT, there is no first or last trigger for the missing actions.</span></span>  
  
 <span data-ttu-id="4b9f8-121">INSTEAD OF 觸發程序不得被指定為第一個或最後一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-121">INSTEAD OF triggers cannot be specified as first or last triggers.</span></span> <span data-ttu-id="4b9f8-122">INSTEAD OF 觸發程序必須在更新基礎資料表之前啟動。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-122">INSTEAD OF triggers are fired before updates are made to the underlying tables.</span></span> <span data-ttu-id="4b9f8-123">如果是由 INSTEAD OF 觸發程序更新基礎資料表，則更新會發生在引發對資料表定義的 AFTER 觸發程序之前。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-123">If updates are made by an INSTEAD OF trigger to underlying tables, the updates occur before any AFTER triggers defined on the table are fired.</span></span> <span data-ttu-id="4b9f8-124">例如，如果在檢視上的 INSTEAD OF INSERT 觸發程序將資料插入基底資料表，而基底資料表本身包含 INSTEAD OF INSERT 觸發程序和三個 AFTER INSERT 觸發程序，就會引發基底資料表上的 INSTEAD OF INSERT 觸發程序，而不是插入動作，而且在基底資料表上的任何插入動作之後，都會引發基底資料表的 AFTER 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-124">For example, if an INSTEAD OF INSERT trigger on a view inserts data into a base table and the base table itself contains an INSTEAD OF INSERT trigger and three AFTER INSERT triggers, the INSTEAD OF INSERT trigger on the base table is fired instead of the inserting action, and the AFTER triggers on the base table are fired after any inserting action on the base table.</span></span> <span data-ttu-id="4b9f8-125">如需詳細資訊，請參閱 [DML Triggers](dml-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-125">For more information, see [DML Triggers](dml-triggers.md).</span></span>  
  
 <span data-ttu-id="4b9f8-126">如果 ALTER TRIGGER 陳述式變更第一個或最後一個觸發程序，則會捨棄 **First** 或 **Last** 屬性，並且將順序值設為 [None]  。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-126">If an ALTER TRIGGER statement changes a first or last trigger, the **First** or **Last** attribute is dropped and the order value is set to **None**.</span></span> <span data-ttu-id="4b9f8-127">順序必須使用 **sp_settriggerorder**進行重設。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-127">The order must be reset by using **sp_settriggerorder**.</span></span>  
  
 <span data-ttu-id="4b9f8-128">OBJECTPROPERTY 函數也會利用 **ExecIsFirstTrigger** 及 **ExecIsLastTrigger**屬性，來報告觸發程序究竟是第一個或最後一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-128">The OBJECTPROPERTY function reports whether a trigger is a first or last trigger by using the properties **ExecIsFirstTrigger** and **ExecIsLastTrigger**.</span></span>  
  
 <span data-ttu-id="4b9f8-129">複寫會為包含在即時更新或佇列式更新訂閱的資料表，自動產生第一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-129">Replication automatically generates a first trigger for any table that is included in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="4b9f8-130">複寫需要觸發程序是第一個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-130">Replication requires that its trigger be the first trigger.</span></span> <span data-ttu-id="4b9f8-131">當您嘗試將含有第一個觸發程序的資料表包括在立即更新或佇列更新訂閱中，複寫會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-131">Replication raises an error when you try to include a table with a first trigger in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="4b9f8-132">如果您嘗試在資料表已加入訂閱後，將觸發程序變成第一個觸發程序，則 **sp_settriggerorder** 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-132">If you try to make a trigger a first trigger after a table has been included in a subscription, **sp_settriggerorder** returns an error.</span></span> <span data-ttu-id="4b9f8-133">如果您對複寫觸發程序使用 ALTER，或使用 **sp_settriggerorder** 將複寫觸發程序變更為最後一個或無觸發程序，則訂閱將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="4b9f8-133">If you use ALTER on the replication trigger or use **sp_settriggerorder** to change the replication trigger to a last or none trigger, the subscription will not function correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9f8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b9f8-134">See Also</span></span>  
 <span data-ttu-id="4b9f8-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4b9f8-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="4b9f8-136">sp_settriggerorder &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4b9f8-136">sp_settriggerorder &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql)  
  
  
