---
title: 使用完整路徑來註冊擴充預存程式 DLL 名稱 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700582"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a><span data-ttu-id="f11ac-102">使用完整路徑，註冊擴充預存程序 DLL 名稱</span><span class="sxs-lookup"><span data-stu-id="f11ac-102">Use the full path to register extended stored procedure DLL names</span></span>
  <span data-ttu-id="f11ac-103">先前未使用完整路徑註冊 DLL 名稱的擴充預存程序，可能無法在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中運作。</span><span class="sxs-lookup"><span data-stu-id="f11ac-103">Extended stored procedures that were previously registered without the full path for the DLL name may not work in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="f11ac-104">元件</span><span class="sxs-lookup"><span data-stu-id="f11ac-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="f11ac-105">描述</span><span class="sxs-lookup"><span data-stu-id="f11ac-105">Description</span></span>  
 <span data-ttu-id="f11ac-106">先前未使用完整路徑註冊 DLL 名稱的擴充預存程序，在升級之後可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="f11ac-106">Extended stored procedures that were previously registered without the full path for the DLL name may not work after you upgrade.</span></span> <span data-ttu-id="f11ac-107">這是因為在升級程序期間，舊的 BINN 目錄不會加入至新路徑。</span><span class="sxs-lookup"><span data-stu-id="f11ac-107">This is because the old BINN directory is not added to the new path during the upgrade process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f11ac-108">可能找不到擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="f11ac-108">may not be able to locate the extended stored procedures.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f11ac-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="f11ac-109">Corrective Action</span></span>  
 <span data-ttu-id="f11ac-110">升級之前，請針對未使用完整路徑名稱註冊的每個擴充預存程序遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="f11ac-110">Before you upgrade, follow these steps for each extended stored procedure that was not registered with a full path name:</span></span>  
  
1.  <span data-ttu-id="f11ac-111">執行 sp_dropextendedproc，以便移除擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="f11ac-111">Run sp_dropextendedproc to remove the extended stored procedure.</span></span>  
  
2.  <span data-ttu-id="f11ac-112">執行 sp_addextendedproc，以便使用完整路徑名稱來註冊擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="f11ac-112">Run sp_addextendedproc to register the extended stored procedure with the full path name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11ac-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11ac-113">See Also</span></span>  
 <span data-ttu-id="f11ac-114">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="f11ac-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="f11ac-115">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="f11ac-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
