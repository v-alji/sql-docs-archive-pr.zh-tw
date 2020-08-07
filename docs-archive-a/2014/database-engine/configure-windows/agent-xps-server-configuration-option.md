---
title: Agent XPs 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597350"
---
# <a name="agent-xps-server-configuration-option"></a><span data-ttu-id="d0967-102">Agent XPs 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="d0967-102">Agent XPs Server Configuration Option</span></span>
  <span data-ttu-id="d0967-103">使用 **代理程式 XP** 選項以啟用此伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0967-103">Use the **Agent XPs** option to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures on this server.</span></span> <span data-ttu-id="d0967-104">未啟用此選項時，「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件總管」中就沒有 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Agent 節點可用。</span><span class="sxs-lookup"><span data-stu-id="d0967-104">When this option is not enabled, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer.</span></span>  
  
 <span data-ttu-id="d0967-105">當您使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具來啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務時，就會自動啟用這些擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0967-105">When you use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tool to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, these extended stored procedures are enabled automatically.</span></span> <span data-ttu-id="d0967-106">如需詳細資訊，請參閱＜ [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d0967-106">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0967-107">不論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務狀態為何，除非已啟用這些擴充預存程序，否則 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 物件總管不會顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的內容。</span><span class="sxs-lookup"><span data-stu-id="d0967-107">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Object Explorer does not display the contents of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent node unless these extended stored procedures are enabled regardless of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service state.</span></span>  
  
 <span data-ttu-id="d0967-108">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="d0967-108">The possible values are:</span></span>  
  
-   <span data-ttu-id="d0967-109">**0**，表示無法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 擴充預存程式 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d0967-109">**0**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are not available (the default).</span></span>  
  
-   <span data-ttu-id="d0967-110">**1**，代表可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 擴充預存程式。</span><span class="sxs-lookup"><span data-stu-id="d0967-110">**1**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are available.</span></span>  
  
 <span data-ttu-id="d0967-111">設定立即生效，伺服器不必停止再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="d0967-111">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d0967-112">範例</span><span class="sxs-lookup"><span data-stu-id="d0967-112">Examples</span></span>  
 <span data-ttu-id="d0967-113">下列範例會啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="d0967-113">The following example enables the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0967-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0967-114">See Also</span></span>  
 <span data-ttu-id="d0967-115">[自動化管理工作 &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="d0967-115">[Automated Administration Tasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="d0967-116">啟動、停止或暫停 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="d0967-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
