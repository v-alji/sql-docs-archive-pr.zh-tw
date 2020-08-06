---
title: SQL Server Agent 屬性 (作業系統頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 743a8d558e97e9ad83cfc66e9ef1adf2e1bc0c2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599306"
---
# <a name="sql-server-agent-properties-job-system-page"></a><span data-ttu-id="6ca32-102">SQL Server Agent 屬性 (作業系統頁面)</span><span class="sxs-lookup"><span data-stu-id="6ca32-102">SQL Server Agent Properties (Job System Page)</span></span>
  <span data-ttu-id="6ca32-103">使用此頁面來查看和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務管理作業的方式。</span><span class="sxs-lookup"><span data-stu-id="6ca32-103">Use this page to view and modify how the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service manages jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6ca32-104">選項</span><span class="sxs-lookup"><span data-stu-id="6ca32-104">Options</span></span>  
 <span data-ttu-id="6ca32-105">**關機逾時間隔 (以秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="6ca32-105">**Shutdown time-out interval (in seconds)**</span></span>  
 <span data-ttu-id="6ca32-106">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在關機之前，要等候作業完成的秒數。</span><span class="sxs-lookup"><span data-stu-id="6ca32-106">Specifies the number of seconds that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for jobs to complete before shutting down.</span></span> <span data-ttu-id="6ca32-107">如果在指定的時間間隔之後作業仍在執行， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就會強制停止作業。</span><span class="sxs-lookup"><span data-stu-id="6ca32-107">If the job is still running after the interval specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent forcefully stops the job.</span></span>  
  
 <span data-ttu-id="6ca32-108">**使用非管理員 Proxy 帳戶**</span><span class="sxs-lookup"><span data-stu-id="6ca32-108">**Use a non-administrator proxy account**</span></span>  
 <span data-ttu-id="6ca32-109">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的非管理員 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6ca32-109">Sets a non-administrator proxy account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="6ca32-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]和更新的版本支援多個 proxy，因此只有在管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時才適用此選項之前的代理程式版本 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ca32-110">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="6ca32-111">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="6ca32-111">**User name**</span></span>  
 <span data-ttu-id="6ca32-112">輸入非管理員 Proxy 帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6ca32-112">Type the name of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6ca32-113">支援多個 Proxy，因此只有在管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Agent 版本時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6ca32-113">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="6ca32-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="6ca32-114">**Password**</span></span>  
 <span data-ttu-id="6ca32-115">輸入非管理員 Proxy 帳戶的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="6ca32-115">Type the password of the user for the non-administrator proxy account.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="6ca32-116">和更新的版本支援多個 Proxy，因此只有在管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Agent 版本時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6ca32-116">and later versions support multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="6ca32-117">**網域**</span><span class="sxs-lookup"><span data-stu-id="6ca32-117">**Domain**</span></span>  
 <span data-ttu-id="6ca32-118">輸入非系統管理 Proxy 帳戶的使用者網域。</span><span class="sxs-lookup"><span data-stu-id="6ca32-118">Type the domain of the user for the non-administrative proxy account.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6ca32-119">支援多個 Proxy，因此只有在管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Agent 版本時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6ca32-119">supports multiple proxies, therefore this option is only applicable when managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent versions prior to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca32-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca32-120">See Also</span></span>  
 [<span data-ttu-id="6ca32-121">實作作業</span><span class="sxs-lookup"><span data-stu-id="6ca32-121">Implement Jobs</span></span>](implement-jobs.md)  
  
  
