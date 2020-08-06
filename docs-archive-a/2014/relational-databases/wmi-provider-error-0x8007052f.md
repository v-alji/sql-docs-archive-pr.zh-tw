---
title: WMI 錯誤 0x8007052f | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6e857e0ccaad9b6f34bbdc9b88aea2e6d7291d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710477"
---
# <a name="wmi-error-0x8007052f"></a><span data-ttu-id="72e32-102">WMI 錯誤 0x8007052f</span><span class="sxs-lookup"><span data-stu-id="72e32-102">WMI Error 0x8007052f</span></span>
    
## <a name="details"></a><span data-ttu-id="72e32-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="72e32-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72e32-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="72e32-104">Product Name</span></span>|<span data-ttu-id="72e32-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="72e32-105">SQL Server</span></span>|  
|<span data-ttu-id="72e32-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="72e32-106">Event ID</span></span>|<span data-ttu-id="72e32-107">0x8007052f</span><span class="sxs-lookup"><span data-stu-id="72e32-107">0x8007052f</span></span>|  
|<span data-ttu-id="72e32-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="72e32-108">Event Source</span></span>|<span data-ttu-id="72e32-109">WMI 提供者錯誤</span><span class="sxs-lookup"><span data-stu-id="72e32-109">WMI Provider Error</span></span>|  
|<span data-ttu-id="72e32-110">元件</span><span class="sxs-lookup"><span data-stu-id="72e32-110">Component</span></span>|<span data-ttu-id="72e32-111">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="72e32-111">SQL Server Configuration Manager</span></span>|  
|<span data-ttu-id="72e32-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="72e32-112">Symbolic Name</span></span>|<span data-ttu-id="72e32-113">NA</span><span class="sxs-lookup"><span data-stu-id="72e32-113">NA</span></span>|  
|<span data-ttu-id="72e32-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="72e32-114">Message Text</span></span>|<span data-ttu-id="72e32-115">登入失敗: 使用者帳戶限制。</span><span class="sxs-lookup"><span data-stu-id="72e32-115">Logon failure: user account restriction.</span></span> <span data-ttu-id="72e32-116">可能的原因為不允許空的密碼，登入時數限制，或強制的原則限制。</span><span class="sxs-lookup"><span data-stu-id="72e32-116">Possible reasons are blank passwords not allowed, login hour restrictions, or a policy restriction has been enforced.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72e32-117">說明</span><span class="sxs-lookup"><span data-stu-id="72e32-117">Explanation</span></span>  
 <span data-ttu-id="72e32-118">當 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在 Windows Server 叢集或 Windows Server 網域控制站上執行時，如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員來切換至內建帳戶 (網路服務、本機服務或本機系統)，就可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="72e32-118">This error can occur when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager to switch to the built-in accounts (Network Service, Local Service, or Local System) when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="72e32-119">請勿在 Windows Server 叢集或 Windows Server 網域控制站上，使用內建帳戶來執行服務。</span><span class="sxs-lookup"><span data-stu-id="72e32-119">Do not run services under built-in accounts on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="72e32-120">如需有關服務帳戶的建議事項，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的＜設定 Windows 服務帳戶＞主題。</span><span class="sxs-lookup"><span data-stu-id="72e32-120">For recommendations on service accounts, see the topic Setting Up Windows Service Accounts in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72e32-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="72e32-121">User Action</span></span>  
 <span data-ttu-id="72e32-122">將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 設定成使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="72e32-122">Configure [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use a domain account.</span></span>  
  
  
