---
title: ad hoc distributed queries 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d07b3c038597916cdaf026e24e90aab9d6b61616
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584729"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a><span data-ttu-id="4c47b-102">特定分散式查詢伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="4c47b-102">ad hoc distributed queries Server Configuration Option</span></span>
  <span data-ttu-id="4c47b-103">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許使用 OPENROWSET 和 OPENDATASOURCE 進行特定分散式查詢。</span><span class="sxs-lookup"><span data-stu-id="4c47b-103">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc distributed queries using OPENROWSET and OPENDATASOURCE.</span></span> <span data-ttu-id="4c47b-104">當此選項設定為 1 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就會允許特定存取。</span><span class="sxs-lookup"><span data-stu-id="4c47b-104">When this option is set to 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows ad hoc access.</span></span> <span data-ttu-id="4c47b-105">當此選項未設定或設定為 0 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就不允許特定存取。</span><span class="sxs-lookup"><span data-stu-id="4c47b-105">When this option is not set or is set to 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow ad hoc access.</span></span>  
  
 <span data-ttu-id="4c47b-106">特定分散式查詢會使用 OPENROWSET 和 OPENDATASOURCE 函數，連接到使用 OLE DB 的遠端資料來源。</span><span class="sxs-lookup"><span data-stu-id="4c47b-106">Ad hoc distributed queries use the OPENROWSET and OPENDATASOURCE functions to connect to remote data sources that use OLE DB.</span></span> <span data-ttu-id="4c47b-107">OPENROWSET 與 OPENDATASOURCE 只能用來參考不常存取的 OLE DB 資料來源。</span><span class="sxs-lookup"><span data-stu-id="4c47b-107">OPENROWSET and OPENDATASOURCE should be used only to reference OLE DB data sources that are accessed infrequently.</span></span> <span data-ttu-id="4c47b-108">對於經常存取的資料來源，請定義連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c47b-108">For any data sources that will be accessed more than several times, define a linked server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4c47b-109">啟用特定名稱，表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何驗證登入都可以存取該提供者。</span><span class="sxs-lookup"><span data-stu-id="4c47b-109">Enabling the use of ad hoc names means that any authenticated login to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can access the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c47b-110">對於任何可安全由本機登入存取的提供者，系統管理員應該為他啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="4c47b-110">administrators should enable this feature for providers that are safe to be accessed by any local login.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c47b-111">備註</span><span class="sxs-lookup"><span data-stu-id="4c47b-111">Remarks</span></span>  
 <span data-ttu-id="4c47b-112">嘗試建立未啟用**特定分散式查詢**的特定連線，產生錯誤：訊息 7415、層級 16、狀態 1、行 1</span><span class="sxs-lookup"><span data-stu-id="4c47b-112">Attempting to make an ad hoc connection with **Ad Hoc Distributed Queries** not enabled results in error: Msg 7415, Level 16, State 1, Line 1</span></span>  
  
 <span data-ttu-id="4c47b-113">特定存取至 OLE DB 提供者 'Microsoft.ACE.OLEDB.12.0' 已經遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="4c47b-113">Ad hoc access to OLE DB provider 'Microsoft.ACE.OLEDB.12.0' has been denied.</span></span> <span data-ttu-id="4c47b-114">您必須透過連結伺服器來存取此提供者。</span><span class="sxs-lookup"><span data-stu-id="4c47b-114">You must access this provider through a linked server.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4c47b-115">範例</span><span class="sxs-lookup"><span data-stu-id="4c47b-115">Examples</span></span>  
 <span data-ttu-id="4c47b-116">下列範例會啟用特定分散式查詢，然後使用 `Seattle1` 函數來查詢名為 `OPENROWSET` 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4c47b-116">The following example enables ad hoc distributed queries and then queries a server named `Seattle1` using the `OPENROWSET` function.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c47b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c47b-117">See Also</span></span>  
 <span data-ttu-id="4c47b-118">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4c47b-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="4c47b-119">[連結的伺服器 &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="4c47b-119">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="4c47b-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c47b-120">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="4c47b-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c47b-121">[OPENDATASOURCE &#40;Transact-SQL&#41;](/sql/t-sql/functions/opendatasource-transact-sql) </span></span>  
 [<span data-ttu-id="4c47b-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4c47b-122">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  
