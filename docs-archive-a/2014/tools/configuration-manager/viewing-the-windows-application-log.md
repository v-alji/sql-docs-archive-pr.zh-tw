---
title: 檢視 Windows 應用程式記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22f900a0b203e652bbc9cc6e9638711d138756c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595330"
---
# <a name="viewing-the-windows-application-log"></a><span data-ttu-id="ac932-102">檢視 Windows 應用程式記錄</span><span class="sxs-lookup"><span data-stu-id="ac932-102">Viewing the Windows Application Log</span></span>
  <span data-ttu-id="ac932-103">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設成使用 Microsoft Windows 應用程式記錄檔時，每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段都會將新事件寫入該記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac932-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Microsoft Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="ac932-104">您每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，並不會建立新的應用程式記錄檔，這和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤記錄檔不同。</span><span class="sxs-lookup"><span data-stu-id="ac932-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ac932-105">使用「Windows 事件檢視器」或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的記錄檢視器，可以檢視和管理 Windows 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac932-105">View and manage the Windows application log by using Windows Event Viewer or the Log Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ac932-106">使用「事件檢視器」可以檢視三個記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac932-106">There are three logs that can be viewed with Event Viewer.</span></span>  
  
|<span data-ttu-id="ac932-107">Windows 記錄類型</span><span class="sxs-lookup"><span data-stu-id="ac932-107">Windows log type</span></span>|<span data-ttu-id="ac932-108">描述</span><span class="sxs-lookup"><span data-stu-id="ac932-108">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="ac932-109">系統記錄檔</span><span class="sxs-lookup"><span data-stu-id="ac932-109">System log</span></span>|<span data-ttu-id="ac932-110">記錄由 Windows 作業系統元件所記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="ac932-110">Records events logged by the Windows operating system components.</span></span> <span data-ttu-id="ac932-111">例如，啟動時無法載入驅動程式或其他系統元件，就會記錄於系統記錄檔內。</span><span class="sxs-lookup"><span data-stu-id="ac932-111">For example, the failure of a driver or other system component to load during startup is recorded in the system log.</span></span>|  
|<span data-ttu-id="ac932-112">安全性記錄檔</span><span class="sxs-lookup"><span data-stu-id="ac932-112">Security log</span></span>|<span data-ttu-id="ac932-113">記錄安全性事件，例如失敗的登入嘗試。</span><span class="sxs-lookup"><span data-stu-id="ac932-113">Records security events, such as failed login attempts.</span></span> <span data-ttu-id="ac932-114">這有助於追蹤安全性系統的變更，並找出可能破壞安全性的漏洞。</span><span class="sxs-lookup"><span data-stu-id="ac932-114">This helps track changes to the security system and identify possible breaches to security.</span></span> <span data-ttu-id="ac932-115">例如，您可設定使用者管理員中的稽核選項，將嘗試登入至系統的事件記錄於安全性記錄檔內。</span><span class="sxs-lookup"><span data-stu-id="ac932-115">For example, attempts to log on to the system may be recorded in the security log, depending on the audit settings in the User Manager.</span></span><br /><br /> <span data-ttu-id="ac932-116">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員可以檢視安全性記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac932-116">Only members of the **sysadmin** fixed server role can view the security log.</span></span>|  
|<span data-ttu-id="ac932-117">應用程式記錄</span><span class="sxs-lookup"><span data-stu-id="ac932-117">Application log</span></span>|<span data-ttu-id="ac932-118">記錄應用程式所記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="ac932-118">Records events that are logged by applications.</span></span> <span data-ttu-id="ac932-119">例如，資料庫應用程式可能會將檔案錯誤記錄於應用程式記錄檔內。</span><span class="sxs-lookup"><span data-stu-id="ac932-119">For example, a database application might record a file error in the application log.</span></span>|  
  
 <span data-ttu-id="ac932-120">如需有關使用「事件檢視器」、管理應用程式記錄檔，以及了解它所呈現的資訊，請參閱 Windows 文件。</span><span class="sxs-lookup"><span data-stu-id="ac932-120">For more information about using Event Viewer, managing the application log, and understanding the information it presents, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="ac932-121">**若要檢視 Windows 應用程式記錄檔**</span><span class="sxs-lookup"><span data-stu-id="ac932-121">**To view the Windows application log**</span></span>  
  
 [<span data-ttu-id="ac932-122">檢視 Windows 應用程式記錄檔 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="ac932-122">View the Windows Application Log &#40;Windows&#41;</span></span>](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
