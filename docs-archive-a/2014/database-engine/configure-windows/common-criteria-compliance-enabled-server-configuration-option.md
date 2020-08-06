---
title: 通用條件合規性已啟用伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6722d05351b8b9e80240abb4edef0633a97b6da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585598"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a><span data-ttu-id="a7897-102">通用條件符合已啟用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="a7897-102">common criteria compliance enabled Server Configuration Option</span></span>
  <span data-ttu-id="a7897-103">common criteria compliance enabled 選項會啟用通用條件所需的下列元素。</span><span class="sxs-lookup"><span data-stu-id="a7897-103">The common criteria compliance enabled option enables the following elements that are required for the Common Criteria.</span></span>  
  
|<span data-ttu-id="a7897-104">準則</span><span class="sxs-lookup"><span data-stu-id="a7897-104">Criteria</span></span>|<span data-ttu-id="a7897-105">描述</span><span class="sxs-lookup"><span data-stu-id="a7897-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a7897-106">剩餘資訊保護 (RIP)</span><span class="sxs-lookup"><span data-stu-id="a7897-106">Residual Information Protection (RIP)</span></span>|<span data-ttu-id="a7897-107">在記憶體重新配置到新的資源之前，RIP 需要使用已知的位元模式來覆寫記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="a7897-107">RIP requires a memory allocation to be overwritten with a known pattern of bits before memory is reallocated to a new resource.</span></span> <span data-ttu-id="a7897-108">符合 RIP 標準可促使安全性改善。不過，覆寫記憶體配置可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="a7897-108">Meeting the RIP standard can contribute to improved security; however, overwriting the memory allocation can slow performance.</span></span> <span data-ttu-id="a7897-109">啟用 common criteria compliance enabled 選項之後，就會進行覆寫。</span><span class="sxs-lookup"><span data-stu-id="a7897-109">After the common criteria compliance enabled option is enabled, the overwriting occurs.</span></span>|  
|<span data-ttu-id="a7897-110">檢視登入統計資料的功能</span><span class="sxs-lookup"><span data-stu-id="a7897-110">The ability to view login statistics</span></span>|<span data-ttu-id="a7897-111">啟用 common criteria compliance enabled 選項之後，就會啟用登入稽核。</span><span class="sxs-lookup"><span data-stu-id="a7897-111">After the common criteria compliance enabled option is enabled, login auditing is enabled.</span></span> <span data-ttu-id="a7897-112">每次使用者成功登入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，就會提供一些資訊，包括上次登入成功的時間、上次登入不成功的時間，以及上次登入成功與目前登入時間之間的登入嘗試次數。</span><span class="sxs-lookup"><span data-stu-id="a7897-112">Each time a user successfully logs in to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], information about the last successful login time, the last unsuccessful login time, and the number of attempts between the last successful and current login times is made available.</span></span> <span data-ttu-id="a7897-113">您可以透過查詢 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 動態管理檢視，檢視這些登入統計資料。</span><span class="sxs-lookup"><span data-stu-id="a7897-113">These login statistics can be viewed by querying the [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) dynamic management view.</span></span>|  
|<span data-ttu-id="a7897-114">資料行 GRANT 不應覆寫資料表 DENY</span><span class="sxs-lookup"><span data-stu-id="a7897-114">That column GRANT should not override table DENY</span></span>|<span data-ttu-id="a7897-115">啟用 common criteria compliance enabled 選項之後，資料表層級 DENY 的優先順序便高於資料行層級 GRANT。</span><span class="sxs-lookup"><span data-stu-id="a7897-115">After the common criteria compliance enabled option is enabled, a table-level DENY takes precedence over a column-level GRANT.</span></span> <span data-ttu-id="a7897-116">如果沒有啟用此選項，資料行層級 GRANT 的優先順序會高於資料表層級 DENY。</span><span class="sxs-lookup"><span data-stu-id="a7897-116">When the option is not enabled, a column-level GRANT takes precedence over a table-level DENY.</span></span>|  
  
 <span data-ttu-id="a7897-117">[通用條件符合已啟用] 選項是一個進階選項。</span><span class="sxs-lookup"><span data-stu-id="a7897-117">The common criteria compliance enabled option is an advanced option.</span></span> <span data-ttu-id="a7897-118">Common Criteria 只會針對 Enterprise Edition 和 Datacenter Edition 進行評估和認證。</span><span class="sxs-lookup"><span data-stu-id="a7897-118">Common criteria is only evaluated and certified for the Enterprise edition and Datacenter edition.</span></span> <span data-ttu-id="a7897-119">如需有關 Common Criteria 認證的最新狀態，請參閱 [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) 網站。</span><span class="sxs-lookup"><span data-stu-id="a7897-119">For the latest status of common criteria certification, see the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a7897-120">除了啟用 common criteria compliance enabled 選項之外，您也必須下載並執行可將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為符合通用條件評估保證層級 4 (EAL4+) 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a7897-120">In addition to enabling the common criteria compliance enabled option, you also must download and run a script that finishes configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to comply with Common Criteria Evaluation Assurance Level 4+ (EAL4+).</span></span> <span data-ttu-id="a7897-121">您可以從 [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) 網站下載此指令碼。</span><span class="sxs-lookup"><span data-stu-id="a7897-121">You can download this script from the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
 <span data-ttu-id="a7897-122">如果您要使用 sp_configure 系統預存程序來變更此設定，只有當 show advanced options 設為 1 時，才能變更 common criteria compliance enabled。</span><span class="sxs-lookup"><span data-stu-id="a7897-122">If you are using the sp_configure system stored procedure to change the setting, you can change common criteria compliance enabled only when show advanced options is set to 1.</span></span> <span data-ttu-id="a7897-123">伺服器重新啟動之後，設定才會生效。</span><span class="sxs-lookup"><span data-stu-id="a7897-123">The setting takes effect after the server is restarted.</span></span> <span data-ttu-id="a7897-124">可能的值為 0 和 1：</span><span class="sxs-lookup"><span data-stu-id="a7897-124">The possible values are 0 and 1:</span></span>  
  
-   <span data-ttu-id="a7897-125">0 表示通用條件符合未啟用。</span><span class="sxs-lookup"><span data-stu-id="a7897-125">0 indicates that common criteria compliance is not enabled.</span></span> <span data-ttu-id="a7897-126">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a7897-126">This is the default.</span></span>  
  
-   <span data-ttu-id="a7897-127">1 表示通用條件符合已啟用。</span><span class="sxs-lookup"><span data-stu-id="a7897-127">1 indicates that common criteria compliance is enabled.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a7897-128">範例</span><span class="sxs-lookup"><span data-stu-id="a7897-128">Examples</span></span>  
 <span data-ttu-id="a7897-129">下列範例會啟用通用條件符合。</span><span class="sxs-lookup"><span data-stu-id="a7897-129">The following example enables common criteria compliance.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7897-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7897-130">See Also</span></span>  
 [<span data-ttu-id="a7897-131">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7897-131">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
