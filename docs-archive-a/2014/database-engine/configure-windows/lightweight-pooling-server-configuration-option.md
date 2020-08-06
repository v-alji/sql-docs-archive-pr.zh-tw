---
title: 輕量型共用伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 549ff7451a31b48459b5a290b94ad406c3768a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596902"
---
# <a name="lightweight-pooling-server-configuration-option"></a><span data-ttu-id="3c371-102">輕量型共用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3c371-102">lightweight pooling Server Configuration Option</span></span>
  <span data-ttu-id="3c371-103">在對稱式多處理 (SMP) 環境中，有時候會出現內容切換過多的現象，[輕量型共用] 選項可用來減少這種現象對系統所造成的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="3c371-103">Use the **lightweight pooling** option to provide a means of reducing the system overhead associated with the excessive context switching sometimes seen in symmetric multiprocessing (SMP) environments.</span></span> <span data-ttu-id="3c371-104">發生內容切換過多的現象時，輕量型共用可以執行內容切換內嵌，藉此幫助減少使用者/核心的環狀轉換，而提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="3c371-104">When excessive context switching is present, lightweight pooling can provide better throughput by performing the context switching inline, thus helping to reduce user/kernel ring transitions.</span></span>  
  
 <span data-ttu-id="3c371-105">Fiber 模式適用於 UMS 工作者的環境切換是重大效能瓶頸的某些狀況。</span><span class="sxs-lookup"><span data-stu-id="3c371-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers are the critical bottleneck in performance.</span></span> <span data-ttu-id="3c371-106">因為這個狀況非常罕見，所以 Fiber 模式幾乎不太會提高一般系統上的效能或延展性。</span><span class="sxs-lookup"><span data-stu-id="3c371-106">Because this is rare, fiber mode rarely enhances performance or scalability on the typical system.</span></span> <span data-ttu-id="3c371-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 中改善的環境切換也減少了 Fiber 模式需求。</span><span class="sxs-lookup"><span data-stu-id="3c371-107">Improved context switching in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] has also reduced the need for fiber mode.</span></span> <span data-ttu-id="3c371-108">我們不建議您針對例行作業使用 Fiber 模式排程。</span><span class="sxs-lookup"><span data-stu-id="3c371-108">We do not recommend that you use fiber mode scheduling for routine operation.</span></span> <span data-ttu-id="3c371-109">這是因為 Fiber 模式可能會抑制內容切換通常會有的好處而降低效能，而且使用執行緒本機存放裝置 (TLS) 或執行緒擁有之物件 (例如 Win32 核心物件) 的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件無法在 Fiber 模式下正確運作。</span><span class="sxs-lookup"><span data-stu-id="3c371-109">This is because it can decrease performance by inhibiting the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a type of Win32 kernel object), cannot function correctly in fiber mode.</span></span>  
  
 <span data-ttu-id="3c371-110">將 **lightweight pooling** 設成 1 會使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切換成 Fiber 模式排程。</span><span class="sxs-lookup"><span data-stu-id="3c371-110">Setting **lightweight pooling** to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="3c371-111">這個選項的預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="3c371-111">The default value for this option is 0.</span></span>  
  
 <span data-ttu-id="3c371-112">**lightweight pooling** 屬於進階選項。</span><span class="sxs-lookup"><span data-stu-id="3c371-112">The **lightweight pooling** option is an advanced option.</span></span> <span data-ttu-id="3c371-113">如果您要使用 **sp_configure** 系統預存程序來變更此設定，只有當 **show advanced options** 設為 1 時，才能變更 **lightweight pooling** 。</span><span class="sxs-lookup"><span data-stu-id="3c371-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change **lightweight pooling** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="3c371-114">伺服器重新啟動之後，設定才會生效。</span><span class="sxs-lookup"><span data-stu-id="3c371-114">The setting takes effect after the server is restarted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c371-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP 不支援輕量型共用。</span><span class="sxs-lookup"><span data-stu-id="3c371-115">Lightweight pooling is not supported for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP.</span></span> [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] <span data-ttu-id="3c371-116">提供了輕量型共用的完整支援。</span><span class="sxs-lookup"><span data-stu-id="3c371-116">provides full support for lightweight pooling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c371-117">輕量型共用不支援 Common Language Runtime (CLR) 的執行。</span><span class="sxs-lookup"><span data-stu-id="3c371-117">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="3c371-118">停用下列兩個選項的其中一個："clr enabled" 或 "lightweight pooling"。</span><span class="sxs-lookup"><span data-stu-id="3c371-118">Disable one of two options: "clr enabled" or "lightweight pooling".</span></span> <span data-ttu-id="3c371-119">依賴 CLR 而且在 Fiber 模式下無法正常運作的功能包括了階層資料類型、複寫和以原則為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="3c371-119">Features that rely upon CLR and that do not work properly in fiber mode include the hierarchy data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c371-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c371-120">See Also</span></span>  
 <span data-ttu-id="3c371-121">[CLR 已啟用伺服器組態選項](clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="3c371-121">[clr enabled Server Configuration Option](clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="3c371-122">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c371-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="3c371-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3c371-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="3c371-124">CLR 已啟用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3c371-124">clr enabled Server Configuration Option</span></span>](clr-enabled-server-configuration-option.md)  
  
  
