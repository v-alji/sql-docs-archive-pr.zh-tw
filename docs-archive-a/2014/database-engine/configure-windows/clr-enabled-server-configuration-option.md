---
title: CLR 已啟用伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585596"
---
# <a name="clr-enabled-server-configuration-option"></a><span data-ttu-id="c3310-102">CLR 已啟用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="c3310-102">clr enabled Server Configuration Option</span></span>
  <span data-ttu-id="c3310-103">使用 clr enabled 選項來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]是否能執行使用者組件。</span><span class="sxs-lookup"><span data-stu-id="c3310-103">Use the clr enabled option to specify whether user assemblies can be run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c3310-104">clr enabled 選項提供下列值。</span><span class="sxs-lookup"><span data-stu-id="c3310-104">The clr enabled option provides the following values.</span></span>  
  
|<span data-ttu-id="c3310-105">值</span><span class="sxs-lookup"><span data-stu-id="c3310-105">Value</span></span>|<span data-ttu-id="c3310-106">描述</span><span class="sxs-lookup"><span data-stu-id="c3310-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3310-107">0</span><span class="sxs-lookup"><span data-stu-id="c3310-107">0</span></span>|<span data-ttu-id="c3310-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上不允許組件執行。</span><span class="sxs-lookup"><span data-stu-id="c3310-108">Assembly execution not allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="c3310-109">1</span><span class="sxs-lookup"><span data-stu-id="c3310-109">1</span></span>|<span data-ttu-id="c3310-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上允許組件執行。</span><span class="sxs-lookup"><span data-stu-id="c3310-110">Assembly execution allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
 <span data-ttu-id="c3310-111">WOW64 伺服器必須重新啟動之後，對此設定的變更才能生效。</span><span class="sxs-lookup"><span data-stu-id="c3310-111">WOW64 servers must be restarted before the changes to this setting will take effect.</span></span> <span data-ttu-id="c3310-112">對於其他伺服器類型，則不需要重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c3310-112">Restart is not required for other server types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3310-113">執行 RECONFIGURE 且 clr enabled 選項的執行值從 1 變更為 0 時，會立即卸載包含使用者組件的所有應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="c3310-113">When RECONFIGURE is run and the run value of the clr enabled option is changed from 1 to 0, all application domains containing user assemblies are immediately unloaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3310-114">輕量型共用不支援 Common Language Runtime (CLR) 的執行。</span><span class="sxs-lookup"><span data-stu-id="c3310-114">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="c3310-115">停用下列一或兩個選項："clr enabled" 或 "lightweight pooling"。</span><span class="sxs-lookup"><span data-stu-id="c3310-115">Disable one of two options: "clr enabled" or "lightweight pooling.</span></span> <span data-ttu-id="c3310-116">依賴 CLR 而且在 Fiber 模式下無法正常運作的功能包括 `hierarchy` 資料類型、複寫和以原則為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="c3310-116">Features that rely upon CLR and that do not work properly in fiber mode include the `hierarchy` data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3310-117">範例</span><span class="sxs-lookup"><span data-stu-id="c3310-117">Example</span></span>  
 <span data-ttu-id="c3310-118">以下範例會先顯示使用 clr 已啟用選項的目前設定，然後將選項值設定為 1 來啟用選項。</span><span class="sxs-lookup"><span data-stu-id="c3310-118">The following example first displays the current setting of the clr enabled option and then enables the option by setting the option value to 1.</span></span> <span data-ttu-id="c3310-119">若要停用此選項，請將值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="c3310-119">To disable the option, set the value to 0.</span></span>  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3310-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3310-120">See Also</span></span>  
 <span data-ttu-id="c3310-121">[輕量型共用伺服器組態選項](lightweight-pooling-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="c3310-121">[lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md) </span></span>  
 <span data-ttu-id="c3310-122">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c3310-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c3310-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c3310-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c3310-124">輕量型共用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="c3310-124">lightweight pooling Server Configuration Option</span></span>](lightweight-pooling-server-configuration-option.md)  
  
  
