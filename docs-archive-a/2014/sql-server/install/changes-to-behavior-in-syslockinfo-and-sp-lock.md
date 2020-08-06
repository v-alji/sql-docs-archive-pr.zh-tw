---
title: Syslockinfo 和 sp_lock 中行為的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595522"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a><span data-ttu-id="57dc1-102">syslockinfo 與 sp_lock 中之行為的變更</span><span class="sxs-lookup"><span data-stu-id="57dc1-102">Changes to behavior in syslockinfo and sp_lock</span></span>
  <span data-ttu-id="57dc1-103">**syslockinfo**和**sp_lock**可能會傳回非預期的值。</span><span class="sxs-lookup"><span data-stu-id="57dc1-103">**syslockinfo** and **sp_lock** may return unexpected values.</span></span> <span data-ttu-id="57dc1-104">它們也可能會傳回額外的資料列，而舊版的**syslockinfo**和**sp_lock**則會針對每個鎖定資源傳回最多兩個數據列。</span><span class="sxs-lookup"><span data-stu-id="57dc1-104">They may also return additional rows, whereas previous versions of **syslockinfo** and **sp_lock** returned a maximum of two rows per lock resource.</span></span>  
  
 <span data-ttu-id="57dc1-105">若要從**syslockinfo**或執行**sp_lock**存取訊號，需要伺服器的 VIEW SERVER STATE 許可權。</span><span class="sxs-lookup"><span data-stu-id="57dc1-105">To access information from **syslockinfo** or execute **sp_lock** requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="component"></a><span data-ttu-id="57dc1-106">元件</span><span class="sxs-lookup"><span data-stu-id="57dc1-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="57dc1-107">描述</span><span class="sxs-lookup"><span data-stu-id="57dc1-107">Description</span></span>  
 <span data-ttu-id="57dc1-108">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ， **syslockinfo**中的**rsc_objid**和**rsc_indid**資料行以及**sp_lock**中的**objid**和**indid**資料行一致地傳回物件識別碼和索引識別碼。</span><span class="sxs-lookup"><span data-stu-id="57dc1-108">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the **rsc_objid** and **rsc_indid** columns in **syslockinfo** and the **objid** and **indid** columns in **sp_lock** consistently return the object ID and index ID.</span></span> <span data-ttu-id="57dc1-109">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，可能會傳回 0 值。</span><span class="sxs-lookup"><span data-stu-id="57dc1-109">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a value of 0 may be returned.</span></span>  
  
 <span data-ttu-id="57dc1-110">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ， **syslockinfo**和**sp_lock**會針對單一交易中的任何指定鎖定資源，傳回最多兩個數據列。</span><span class="sxs-lookup"><span data-stu-id="57dc1-110">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** and **sp_lock** return a maximum of two rows for any given lock resource in a single transaction.</span></span> <span data-ttu-id="57dc1-111">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，啟用鎖定分割區時，可能會為單一交易底下執行的相同資源傳回多個資料列。</span><span class="sxs-lookup"><span data-stu-id="57dc1-111">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], when lock partitioning is enabled, multiple rows for the same resource running under one transaction may be returned.</span></span> <span data-ttu-id="57dc1-112">最多可能會傳回 N + 1 個數據列，其中 N 是 Cpu 的數目。</span><span class="sxs-lookup"><span data-stu-id="57dc1-112">There may be up to N + 1 rows returned, where N is the number of CPUs.</span></span> <span data-ttu-id="57dc1-113">另外，現在還可以為相同資源顯示 GRANTED 和 WAITING 要求，而這在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中是不可行的。</span><span class="sxs-lookup"><span data-stu-id="57dc1-113">Also, it is now possible to have GRANTED and WAITING requests displayed for the same resource, which was not possible in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="57dc1-114">權限</span><span class="sxs-lookup"><span data-stu-id="57dc1-114">Permissions</span></span>  
 <span data-ttu-id="57dc1-115">需要伺服器的 VIEW SERVER STATE 權限。</span><span class="sxs-lookup"><span data-stu-id="57dc1-115">Requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57dc1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57dc1-116">See Also</span></span>  
 <span data-ttu-id="57dc1-117">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="57dc1-117">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="57dc1-118">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="57dc1-118">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
