---
title: 移除未記載之系統資料表的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704706"
---
# <a name="remove-references-to-undocumented-system-tables"></a><span data-ttu-id="ab941-102">移除未記載之系統資料表的參考</span><span class="sxs-lookup"><span data-stu-id="ab941-102">Remove references to undocumented system tables</span></span>
  <span data-ttu-id="ab941-103">在舊版本中未記載的許多系統資料表都已變更或不存在，因此，在升級之後，使用這些資料表可能導致錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="ab941-103">Many system tables that were undocumented in prior releases have changed or no longer exist; therefore, using these tables may cause errors after upgrading.</span></span> <span data-ttu-id="ab941-104">因為 Upgrade Advisor 會尋找系統資料表名稱的參考，所以它會報告與系統資料表有相同名稱的任何使用者資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="ab941-104">Because Upgrade Advisor looks for references to system table names, it will report references to any user tables that have the same names as system tables.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ab941-105">元件</span><span class="sxs-lookup"><span data-stu-id="ab941-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ab941-106">描述</span><span class="sxs-lookup"><span data-stu-id="ab941-106">Description</span></span>  
 <span data-ttu-id="ab941-107">下列未記載的系統資料表已移除：</span><span class="sxs-lookup"><span data-stu-id="ab941-107">The following undocumented system tables are removed:</span></span>  
  
-   <span data-ttu-id="ab941-108">**spt_datatype_info**</span><span class="sxs-lookup"><span data-stu-id="ab941-108">**spt_datatype_info**</span></span>  
  
-   <span data-ttu-id="ab941-109">**spt_datatype_info_ext**</span><span class="sxs-lookup"><span data-stu-id="ab941-109">**spt_datatype_info_ext**</span></span>  
  
-   <span data-ttu-id="ab941-110">**spt_provider_types**</span><span class="sxs-lookup"><span data-stu-id="ab941-110">**spt_provider_types**</span></span>  
  
-   <span data-ttu-id="ab941-111">**spt_server_info**</span><span class="sxs-lookup"><span data-stu-id="ab941-111">**spt_server_info**</span></span>  
  
-   <span data-ttu-id="ab941-112">**spt_values**</span><span class="sxs-lookup"><span data-stu-id="ab941-112">**spt_values**</span></span>  
  
-   <span data-ttu-id="ab941-113">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="ab941-113">**sysfulltextnotify**</span></span>  
  
-   <span data-ttu-id="ab941-114">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="ab941-114">**syslocks**</span></span>  
  
-   <span data-ttu-id="ab941-115">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="ab941-115">**sysproperties**</span></span>  
  
-   <span data-ttu-id="ab941-116">**sysprotects_aux**</span><span class="sxs-lookup"><span data-stu-id="ab941-116">**sysprotects_aux**</span></span>  
  
-   <span data-ttu-id="ab941-117">**sysprotects_view**</span><span class="sxs-lookup"><span data-stu-id="ab941-117">**sysprotects_view**</span></span>  
  
-   <span data-ttu-id="ab941-118">**SYSREMOTE_CATALOGS**</span><span class="sxs-lookup"><span data-stu-id="ab941-118">**SYSREMOTE_CATALOGS**</span></span>  
  
-   <span data-ttu-id="ab941-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="ab941-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="ab941-120">**SYSREMOTE_COLUMNS**</span><span class="sxs-lookup"><span data-stu-id="ab941-120">**SYSREMOTE_COLUMNS**</span></span>  
  
-   <span data-ttu-id="ab941-121">**SYSREMOTE_FOREIGN_KEYS**</span><span class="sxs-lookup"><span data-stu-id="ab941-121">**SYSREMOTE_FOREIGN_KEYS**</span></span>  
  
-   <span data-ttu-id="ab941-122">**SYSREMOTE_INDEXES**</span><span class="sxs-lookup"><span data-stu-id="ab941-122">**SYSREMOTE_INDEXES**</span></span>  
  
-   <span data-ttu-id="ab941-123">**SYSREMOTE_PRIMARY_KEYS**</span><span class="sxs-lookup"><span data-stu-id="ab941-123">**SYSREMOTE_PRIMARY_KEYS**</span></span>  
  
-   <span data-ttu-id="ab941-124">**SYSREMOTE_PROVIDER_TYPES**</span><span class="sxs-lookup"><span data-stu-id="ab941-124">**SYSREMOTE_PROVIDER_TYPES**</span></span>  
  
-   <span data-ttu-id="ab941-125">**SYSREMOTE_SCHEMATA**</span><span class="sxs-lookup"><span data-stu-id="ab941-125">**SYSREMOTE_SCHEMATA**</span></span>  
  
-   <span data-ttu-id="ab941-126">**SYSREMOTE_STATISTICS**</span><span class="sxs-lookup"><span data-stu-id="ab941-126">**SYSREMOTE_STATISTICS**</span></span>  
  
-   <span data-ttu-id="ab941-127">**SYSREMOTE_TABLE_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="ab941-127">**SYSREMOTE_TABLE_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="ab941-128">**SYSREMOTE_TABLES**</span><span class="sxs-lookup"><span data-stu-id="ab941-128">**SYSREMOTE_TABLES**</span></span>  
  
-   <span data-ttu-id="ab941-129">**SYSREMOTE_VIEWS**</span><span class="sxs-lookup"><span data-stu-id="ab941-129">**SYSREMOTE_VIEWS**</span></span>  
  
-   <span data-ttu-id="ab941-130">**syssegments**</span><span class="sxs-lookup"><span data-stu-id="ab941-130">**syssegments**</span></span>  
  
-   <span data-ttu-id="ab941-131">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="ab941-131">**sysxlogins**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ab941-132">更正動作</span><span class="sxs-lookup"><span data-stu-id="ab941-132">Corrective Action</span></span>  
 <span data-ttu-id="ab941-133">根據下表修改您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab941-133">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="ab941-134">取代</span><span class="sxs-lookup"><span data-stu-id="ab941-134">Instead of</span></span>|<span data-ttu-id="ab941-135">用法</span><span class="sxs-lookup"><span data-stu-id="ab941-135">Use</span></span>|  
|----------------|---------|  
|<span data-ttu-id="ab941-136">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="ab941-136">**sysfulltextnotify**</span></span>|<span data-ttu-id="ab941-137">OBJECTPROPERTYEX 函數的**TableFulltextPendingChanges**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab941-137">**TableFulltextPendingChanges** property of the OBJECTPROPERTYEX function.</span></span>|  
|<span data-ttu-id="ab941-138">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="ab941-138">**syslocks**</span></span>|<span data-ttu-id="ab941-139">**dm_tran_locks**動態管理檢視] 或 [sp_lock] 或 [ **sys.syslockinfo**相容性] 視圖。</span><span class="sxs-lookup"><span data-stu-id="ab941-139">**sys.dm_tran_locks** dynamic management view, or sp_lock, or the **sys.syslockinfo** compatibility view.</span></span>|  
|<span data-ttu-id="ab941-140">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="ab941-140">**sysproperties**</span></span>|<span data-ttu-id="ab941-141">**extended_properties**目錄檢視或**fn_listextendedproperty**函數</span><span class="sxs-lookup"><span data-stu-id="ab941-141">**sys.extended_properties** catalog view or the **fn_listextendedproperty** function</span></span>|  
|<span data-ttu-id="ab941-142">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="ab941-142">**sysxlogins**</span></span>|<span data-ttu-id="ab941-143">**server_principals**目錄檢視或**syslogins**相容性檢視。</span><span class="sxs-lookup"><span data-stu-id="ab941-143">**sys.server_principals** catalog view or **syslogins** compatibility view.</span></span>|  
|<span data-ttu-id="ab941-144">所有**spt_** 資料表</span><span class="sxs-lookup"><span data-stu-id="ab941-144">all **spt_** tables</span></span>|<span data-ttu-id="ab941-145">沒有可用的取代項目</span><span class="sxs-lookup"><span data-stu-id="ab941-145">No replacement available</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab941-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab941-146">See Also</span></span>  
 <span data-ttu-id="ab941-147">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ab941-147">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ab941-148">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="ab941-148">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
