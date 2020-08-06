---
title: 實作 DDL 觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, implementing
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
author: rothja
ms.author: jroth
ms.openlocfilehash: 110e69aca31df75d4b4d7a732de5c58556bd3e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606124"
---
# <a name="implement-ddl-triggers"></a><span data-ttu-id="efad0-102">實作 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="efad0-102">Implement DDL Triggers</span></span>
  <span data-ttu-id="efad0-103">本主題提供資訊以協助您建立 DDL 觸發程式、修改 DDL 觸發程式並停用或卸除 DDL 觸發程式。</span><span class="sxs-lookup"><span data-stu-id="efad0-103">This topic provides information to help you create DDL triggers, modify DDL triggers, and disable or drop DDL triggers.</span></span>  
  
## <a name="creating-ddl-triggers"></a><span data-ttu-id="efad0-104">建立 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="efad0-104">Creating DDL Triggers</span></span>  
 <span data-ttu-id="efad0-105">您可以使用 DDL 觸發程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER 陳述式，建立 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="efad0-105">DDL triggers are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement for DDL triggers.</span></span>  
  
 <span data-ttu-id="efad0-106">**建立 DDL 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="efad0-106">**To create a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="efad0-108">從觸發程序傳回結果集的功能，將會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]未來的版本中移除。</span><span class="sxs-lookup"><span data-stu-id="efad0-108">The ability to return result sets from triggers will be removed in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efad0-109">傳回結果集的觸發程序可能會導致非專用的應用程式發生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="efad0-109">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span> <span data-ttu-id="efad0-110">請在新的開發工作中避免從觸發程序傳回結果集，並計畫修改目前如此運作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="efad0-110">Avoid returning result sets from triggers in new development work, and plan to modify applications that currently do this.</span></span> <span data-ttu-id="efad0-111">若要避免在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中從觸發程序傳回結果集，請將 [不允許來自觸發程序的結果選項](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) 設為 1。</span><span class="sxs-lookup"><span data-stu-id="efad0-111">To prevent triggers from returning result sets in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], set the [disallow results from triggers Option](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) to 1.</span></span> <span data-ttu-id="efad0-112">在未來版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，此選項的預設值會是 1。</span><span class="sxs-lookup"><span data-stu-id="efad0-112">The default setting of this option will be 1 in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="modifying-ddl-triggers"></a><span data-ttu-id="efad0-113">修改 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="efad0-113">Modifying DDL Triggers</span></span>  
 <span data-ttu-id="efad0-114">如果您必須修改 DDL 觸發程序的定義，您可以卸除觸發程序後重新加以建立，或是在單一步驟中重新定義現有的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="efad0-114">If you have to modify the definition of a DDL trigger, you can either drop and re-create the trigger or redefine the existing trigger in a single step.</span></span>  
  
 <span data-ttu-id="efad0-115">如果您變更 DDL 觸發程序所參考的物件名稱，就必須修改觸發程序使其文字反映新名稱。</span><span class="sxs-lookup"><span data-stu-id="efad0-115">If you change the name of an object that is referenced by a DDL trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="efad0-116">因此，在改變物件名稱時，首先要檢視此物件的相依性以判斷是否有相關的觸發程序受到影響。</span><span class="sxs-lookup"><span data-stu-id="efad0-116">Therefore, before renaming an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="efad0-117">您也可以將觸發程序的定義修改為加密的形態。</span><span class="sxs-lookup"><span data-stu-id="efad0-117">A trigger can also be modified to encrypt its definition.</span></span>  
  
 <span data-ttu-id="efad0-118">**修改觸發程序**</span><span class="sxs-lookup"><span data-stu-id="efad0-118">**To modify a trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-trigger-transact-sql)  
  
 <span data-ttu-id="efad0-120">**檢視觸發程序的相依性**</span><span class="sxs-lookup"><span data-stu-id="efad0-120">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="efad0-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="efad0-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="disabling-and-dropping-ddl-triggers"></a><span data-ttu-id="efad0-124">停用和卸除 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="efad0-124">Disabling and Dropping DDL Triggers</span></span>  
 <span data-ttu-id="efad0-125">不再需要 DDL 觸發程序時，可以將它停用或刪除。</span><span class="sxs-lookup"><span data-stu-id="efad0-125">When a DDL trigger is no longer needed, you can disable it or delete it.</span></span>  
  
 <span data-ttu-id="efad0-126">停用 DDL 觸發程序不會將它卸除。</span><span class="sxs-lookup"><span data-stu-id="efad0-126">Disabling a DDL trigger does not drop it.</span></span> <span data-ttu-id="efad0-127">該觸發程序仍然會以物件形式存在於目前的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="efad0-127">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="efad0-128">不過，只要編寫它的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式在執行時，觸發程序就不會引發。</span><span class="sxs-lookup"><span data-stu-id="efad0-128">However, the trigger will not fire when any [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on which it was programmed are run.</span></span> <span data-ttu-id="efad0-129">已停用的 DDL 觸發程序可重新啟用。</span><span class="sxs-lookup"><span data-stu-id="efad0-129">DDL triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="efad0-130">啟用 DDL 觸發程序會讓它以原先建立時相同的方式引發。</span><span class="sxs-lookup"><span data-stu-id="efad0-130">Enabling a DDL trigger causes it to fire in the same way the trigger did when it was originally created.</span></span> <span data-ttu-id="efad0-131">建立 DDL 觸發程序時，預設是啟用的。</span><span class="sxs-lookup"><span data-stu-id="efad0-131">When DDL triggers are created, they are enabled by default.</span></span>  
  
 <span data-ttu-id="efad0-132">刪除 DDL 觸發程序時，會從目前的資料庫卸除。</span><span class="sxs-lookup"><span data-stu-id="efad0-132">When a DDL trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="efad0-133">DDL 觸發程序所參考的任何物件或資料都不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="efad0-133">Any objects or data upon which the DDL trigger is scoped are not affected.</span></span>  
  
 <span data-ttu-id="efad0-134">**停用 DDL 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="efad0-134">**To disable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/disable-trigger-transact-sql)  
  
-   [<span data-ttu-id="efad0-136">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-136">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="efad0-137">**啟用 DDL 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="efad0-137">**To enable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/enable-trigger-transact-sql)  
  
-   [<span data-ttu-id="efad0-139">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-139">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="efad0-140">**刪除 DDL 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="efad0-140">**To delete a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="efad0-141">DROP TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="efad0-141">DROP TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-trigger-transact-sql)  
  
  
