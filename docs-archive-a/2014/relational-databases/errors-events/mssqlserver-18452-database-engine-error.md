---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597148"
---
# <a name="mssqlserver_18452"></a><span data-ttu-id="a24be-102">MSSQLSERVER_18452</span><span class="sxs-lookup"><span data-stu-id="a24be-102">MSSQLSERVER_18452</span></span>
    
## <a name="details"></a><span data-ttu-id="a24be-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a24be-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a24be-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a24be-104">Product Name</span></span>|<span data-ttu-id="a24be-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a24be-105">SQL Server</span></span>|  
|<span data-ttu-id="a24be-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a24be-106">Event ID</span></span>|<span data-ttu-id="a24be-107">18452</span><span class="sxs-lookup"><span data-stu-id="a24be-107">18452</span></span>|  
|<span data-ttu-id="a24be-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a24be-108">Event Source</span></span>|<span data-ttu-id="a24be-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a24be-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a24be-110">元件</span><span class="sxs-lookup"><span data-stu-id="a24be-110">Component</span></span>|<span data-ttu-id="a24be-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a24be-111">SQLEngine</span></span>|  
|<span data-ttu-id="a24be-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a24be-112">Symbolic Name</span></span>|<span data-ttu-id="a24be-113">LOGON_INVALID_CONNECT</span><span class="sxs-lookup"><span data-stu-id="a24be-113">LOGON_INVALID_CONNECT</span></span>|  
|<span data-ttu-id="a24be-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a24be-114">Message Text</span></span>|<span data-ttu-id="a24be-115">使用者 '%.\*ls' 的登入失敗。</span><span class="sxs-lookup"><span data-stu-id="a24be-115">Login failed for user '%.\*ls'.</span></span> <span data-ttu-id="a24be-116">此登入為 SQL Server 登入，不能用於 Windows 驗證。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="a24be-116">The login is a SQL Server login and cannot be used with Windows Authentication.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a24be-117">說明</span><span class="sxs-lookup"><span data-stu-id="a24be-117">Explanation</span></span>  
 <span data-ttu-id="a24be-118">使用者嘗試使用無法驗證的認證進行登入。</span><span class="sxs-lookup"><span data-stu-id="a24be-118">The user attempted to login with credentials that cannot be validated.</span></span> <span data-ttu-id="a24be-119">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="a24be-119">Possible causes are:</span></span>  
  
-   <span data-ttu-id="a24be-120">此登入可能是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，但是伺服器只接受 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a24be-120">The login may be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login but the server only accepts Windows Authentication.</span></span>  
  
-   <span data-ttu-id="a24be-121">您正嘗試使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接，但是所使用的登入不存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上。</span><span class="sxs-lookup"><span data-stu-id="a24be-121">You are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but the login used does not exist on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a24be-122">此登入可能使用 Windows 驗證，但是此登入是無法辨識的 Windows 主體。</span><span class="sxs-lookup"><span data-stu-id="a24be-122">The login may use Windows Authentication but the login is an unrecognized Windows principal.</span></span> <span data-ttu-id="a24be-123">無法辨識的 Windows 主體是表示 Windows 無法驗證此登入。</span><span class="sxs-lookup"><span data-stu-id="a24be-123">An unrecognized Windows principal means that the login cannot be verified by Windows.</span></span> <span data-ttu-id="a24be-124">這可能是因為 Windows 登入來自於不受信任的網域。</span><span class="sxs-lookup"><span data-stu-id="a24be-124">This could be because the Windows login is from an untrusted domain.</span></span>  
  
 <span data-ttu-id="a24be-125">類似的問題可能會導致較常見的錯誤 18456。</span><span class="sxs-lookup"><span data-stu-id="a24be-125">Similar problems can cause the less-specific error 18456.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a24be-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a24be-126">User Action</span></span>  
 <span data-ttu-id="a24be-127">如果您正嘗試使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接，請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是在混合驗證模式下設定。</span><span class="sxs-lookup"><span data-stu-id="a24be-127">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="a24be-128">如果您正嘗試使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接，請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入存在。</span><span class="sxs-lookup"><span data-stu-id="a24be-128">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists.</span></span>  
  
 <span data-ttu-id="a24be-129">如果您正嘗試使用 Windows 驗證進行連接，請確定您已適當地登入正確的網域。</span><span class="sxs-lookup"><span data-stu-id="a24be-129">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
  
