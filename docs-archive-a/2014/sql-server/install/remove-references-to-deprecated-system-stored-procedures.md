---
title: 移除已被取代之系統預存程式的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704705"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a><span data-ttu-id="b0316-102">移除已被取代之系統預存程序的參考</span><span class="sxs-lookup"><span data-stu-id="b0316-102">Remove references to deprecated system stored procedures</span></span>
  <span data-ttu-id="b0316-103">Upgrade Advisor 偵測到陳述式參考了未記載的系統預存程序和擴充預存程序，而這些預存程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中已無法使用。</span><span class="sxs-lookup"><span data-stu-id="b0316-103">Upgrade Advisor detected statements that reference undocumented system stored procedures and extended stored procedures that are no longer available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b0316-104">參考這些物件的陳述式會失敗。</span><span class="sxs-lookup"><span data-stu-id="b0316-104">Statements that reference these objects will fail.</span></span> <span data-ttu-id="b0316-105">請勿使用未記載的系統物件或 API，因為這些功能在未來的版本中會變更或移除，而不另行通知。</span><span class="sxs-lookup"><span data-stu-id="b0316-105">Do not use undocumented system objects or APIs as the functionality might change or be removed without notification in a future release.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b0316-106">元件</span><span class="sxs-lookup"><span data-stu-id="b0316-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b0316-107">描述</span><span class="sxs-lookup"><span data-stu-id="b0316-107">Description</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="b0316-108">已記載的系統預存程序</span><span class="sxs-lookup"><span data-stu-id="b0316-108">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="b0316-109">下列已記載的系統預存程序已經被移除了：</span><span class="sxs-lookup"><span data-stu-id="b0316-109">The following documented system stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="b0316-110">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="b0316-110">sp_addalias</span></span>  
  
-   <span data-ttu-id="b0316-111">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="b0316-111">sp_addgroup</span></span>  
  
-   <span data-ttu-id="b0316-112">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="b0316-112">sp_changegroup</span></span>  
  
-   <span data-ttu-id="b0316-113">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="b0316-113">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="b0316-114">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="b0316-114">sp_helpgroup</span></span>  
  
### <a name="undocumented-system-stored-procedures"></a><span data-ttu-id="b0316-115">未記載的系統預存程序</span><span class="sxs-lookup"><span data-stu-id="b0316-115">Undocumented System Stored Procedures</span></span>  
 <span data-ttu-id="b0316-116">下列未記載的系統預存程序和擴充預存程序已經被移除了：</span><span class="sxs-lookup"><span data-stu-id="b0316-116">The following undocumented system stored procedures and extended stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="b0316-117">sp_articlesynctranprocs</span><span class="sxs-lookup"><span data-stu-id="b0316-117">sp_articlesynctranprocs</span></span>  
  
-   <span data-ttu-id="b0316-118">sp_diskdefault</span><span class="sxs-lookup"><span data-stu-id="b0316-118">sp_diskdefault</span></span>  
  
-   <span data-ttu-id="b0316-119">sp_EventLog</span><span class="sxs-lookup"><span data-stu-id="b0316-119">sp_EventLog</span></span>  
  
-   <span data-ttu-id="b0316-120">sp_GetMBCSCharLen</span><span class="sxs-lookup"><span data-stu-id="b0316-120">sp_GetMBCSCharLen</span></span>  
  
-   <span data-ttu-id="b0316-121">sp_helplog</span><span class="sxs-lookup"><span data-stu-id="b0316-121">sp_helplog</span></span>  
  
-   <span data-ttu-id="b0316-122">sp_helpsql</span><span class="sxs-lookup"><span data-stu-id="b0316-122">sp_helpsql</span></span>  
  
-   <span data-ttu-id="b0316-123">sp_IsMBCSLeadByte</span><span class="sxs-lookup"><span data-stu-id="b0316-123">sp_IsMBCSLeadByte</span></span>  
  
-   <span data-ttu-id="b0316-124">sp_lock2</span><span class="sxs-lookup"><span data-stu-id="b0316-124">sp_lock2</span></span>  
  
-   <span data-ttu-id="b0316-125">sp_MSget_current_activity</span><span class="sxs-lookup"><span data-stu-id="b0316-125">sp_MSget_current_activity</span></span>  
  
-   <span data-ttu-id="b0316-126">sp_MSset_current_activity</span><span class="sxs-lookup"><span data-stu-id="b0316-126">sp_MSset_current_activity</span></span>  
  
-   <span data-ttu-id="b0316-127">sp_MSobjessearch</span><span class="sxs-lookup"><span data-stu-id="b0316-127">sp_MSobjessearch</span></span>  
  
-   <span data-ttu-id="b0316-128">xp_enum_ActiveScriptEngines</span><span class="sxs-lookup"><span data-stu-id="b0316-128">xp_enum_ActiveScriptEngines</span></span>  
  
-   <span data-ttu-id="b0316-129">xp_eventlog</span><span class="sxs-lookup"><span data-stu-id="b0316-129">xp_eventlog</span></span>  
  
-   <span data-ttu-id="b0316-130">xp_GetAdminGroupName</span><span class="sxs-lookup"><span data-stu-id="b0316-130">xp_GetAdminGroupName</span></span>  
  
-   <span data-ttu-id="b0316-131">xp_GetFileDetails</span><span class="sxs-lookup"><span data-stu-id="b0316-131">xp_GetFileDetails</span></span>  
  
-   <span data-ttu-id="b0316-132">xp_GetLocalSystemAccountName</span><span class="sxs-lookup"><span data-stu-id="b0316-132">xp_GetLocalSystemAccountName</span></span>  
  
-   <span data-ttu-id="b0316-133">xp_IsNTAdmin</span><span class="sxs-lookup"><span data-stu-id="b0316-133">xp_IsNTAdmin</span></span>  
  
-   <span data-ttu-id="b0316-134">xp_MSLocalSystem</span><span class="sxs-lookup"><span data-stu-id="b0316-134">xp_MSLocalSystem</span></span>  
  
-   <span data-ttu-id="b0316-135">xp_MSnt2000</span><span class="sxs-lookup"><span data-stu-id="b0316-135">xp_MSnt2000</span></span>  
  
-   <span data-ttu-id="b0316-136">xp_MSplatform</span><span class="sxs-lookup"><span data-stu-id="b0316-136">xp_MSplatform</span></span>  
  
-   <span data-ttu-id="b0316-137">xp_SetSecurity</span><span class="sxs-lookup"><span data-stu-id="b0316-137">xp_SetSecurity</span></span>  
  
-   <span data-ttu-id="b0316-138">xp_varbintohexstr</span><span class="sxs-lookup"><span data-stu-id="b0316-138">xp_varbintohexstr</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b0316-139">更正動作</span><span class="sxs-lookup"><span data-stu-id="b0316-139">Corrective Action</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="b0316-140">已記載的系統預存程序</span><span class="sxs-lookup"><span data-stu-id="b0316-140">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="b0316-141">根據下表修改您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0316-141">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="b0316-142">取代</span><span class="sxs-lookup"><span data-stu-id="b0316-142">Instead of</span></span>|<span data-ttu-id="b0316-143">執行方式</span><span class="sxs-lookup"><span data-stu-id="b0316-143">Do this</span></span>|  
|----------------|-------------|  
|<span data-ttu-id="b0316-144">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="b0316-144">sp_addalias</span></span>|<span data-ttu-id="b0316-145">以使用者帳戶和資料庫角色的組合來取代別名。</span><span class="sxs-lookup"><span data-stu-id="b0316-145">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="b0316-146">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜CREATE USER (Transact-SQL)＞和＜CREATE ROLE (Transact-SQL)＞。</span><span class="sxs-lookup"><span data-stu-id="b0316-146">For more information, see "CREATE USER (Transact-SQL)" and "CREATE ROLE (Transact-SQL)" in SQL Server Books Online.</span></span> <span data-ttu-id="b0316-147">使用 sp_dropalias 移除已升級之資料庫中的別名。</span><span class="sxs-lookup"><span data-stu-id="b0316-147">Remove aliases in upgraded databases by using sp_dropalias.</span></span>|  
|<span data-ttu-id="b0316-148">sp_addgroupsp_changegroup</span><span class="sxs-lookup"><span data-stu-id="b0316-148">sp_addgroupsp_changegroup</span></span><br /><br /> <span data-ttu-id="b0316-149">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="b0316-149">sp_dropgroup</span></span><br /><br /> <span data-ttu-id="b0316-150">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="b0316-150">sp_helpgroup</span></span>|<span data-ttu-id="b0316-151">使用角色。</span><span class="sxs-lookup"><span data-stu-id="b0316-151">Use roles.</span></span> <span data-ttu-id="b0316-152">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜伺服器層級角色＞和＜資料庫層級角色＞。</span><span class="sxs-lookup"><span data-stu-id="b0316-152">For more information, see "Server-Level Roles" and "Database-Level Roles" in SQL Server Books Online.</span></span>|  
  
### <a name="undocmented-system-stored-procedures"></a><span data-ttu-id="b0316-153">未記載的系統預存程序</span><span class="sxs-lookup"><span data-stu-id="b0316-153">Undocmented System Stored Procedures</span></span>  
 <span data-ttu-id="b0316-154">您可以建立含有對等功能的 CLR 預存程序來取代未記載的系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="b0316-154">You can create CLR stored procedures with equivalent functionality to replace the undocumented system stored procedures.</span></span> <span data-ttu-id="b0316-155">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜CLR 預存程序＞主題。</span><span class="sxs-lookup"><span data-stu-id="b0316-155">For more information, see the topic "CLR Stored Procedures" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0316-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0316-156">See Also</span></span>  
 <span data-ttu-id="b0316-157">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b0316-157">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b0316-158">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="b0316-158">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
