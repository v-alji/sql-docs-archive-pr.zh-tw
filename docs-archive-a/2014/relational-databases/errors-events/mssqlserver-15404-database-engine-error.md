---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beb854c866256728574e06f8c9efb50fb354e15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598949"
---
# <a name="mssqlserver_15404"></a><span data-ttu-id="79030-102">MSSQLSERVER_15404</span><span class="sxs-lookup"><span data-stu-id="79030-102">MSSQLSERVER_15404</span></span>
    
## <a name="details"></a><span data-ttu-id="79030-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="79030-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79030-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="79030-104">Product Name</span></span>|<span data-ttu-id="79030-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="79030-105">SQL Server</span></span>|  
|<span data-ttu-id="79030-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="79030-106">Event ID</span></span>|<span data-ttu-id="79030-107">15404</span><span class="sxs-lookup"><span data-stu-id="79030-107">15404</span></span>|  
|<span data-ttu-id="79030-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="79030-108">Event Source</span></span>|<span data-ttu-id="79030-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="79030-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="79030-110">元件</span><span class="sxs-lookup"><span data-stu-id="79030-110">Component</span></span>|<span data-ttu-id="79030-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="79030-111">SQLEngine</span></span>|  
|<span data-ttu-id="79030-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="79030-112">Symbolic Name</span></span>|<span data-ttu-id="79030-113">SEC_NTGRP_ERROR</span><span class="sxs-lookup"><span data-stu-id="79030-113">SEC_NTGRP_ERROR</span></span>|  
|<span data-ttu-id="79030-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="79030-114">Message Text</span></span>|<span data-ttu-id="79030-115">無法獲得關於 Windows NT 群組/使用者 '*user*' 的資訊，錯誤碼 *code*。</span><span class="sxs-lookup"><span data-stu-id="79030-115">Could not obtain information about Windows NT group/user '*user*', error code *code*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="79030-116">說明</span><span class="sxs-lookup"><span data-stu-id="79030-116">Explanation</span></span>  
 <span data-ttu-id="79030-117">如果指定的是無效的主體，驗證時會使用 15404。</span><span class="sxs-lookup"><span data-stu-id="79030-117">15404 is used in authentication when an invalid principal is specified.</span></span> <span data-ttu-id="79030-118">或者，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和 Windows 帳戶的網域之間沒有完全信任關係，所以 Windows 帳戶模擬失敗。</span><span class="sxs-lookup"><span data-stu-id="79030-118">Or, impersonation of a Windows account fails because there is no full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79030-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="79030-119">User Action</span></span>  
 <span data-ttu-id="79030-120">請確定 Windows 主體存在，並且沒有拼字錯誤。</span><span class="sxs-lookup"><span data-stu-id="79030-120">Check that the Windows principal exists and is not misspelled.</span></span>  
  
 <span data-ttu-id="79030-121">如果這個錯誤是因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶和 Windows 帳戶的網域之間缺少完全信任關係，則採取下列其中一個動作就能解決問題：</span><span class="sxs-lookup"><span data-stu-id="79030-121">If this error is the result of a lack of a full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account, one of the following actions can resolve the error:</span></span>  
  
-   <span data-ttu-id="79030-122">使用與 Windows 使用者位於相同網域的帳戶來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="79030-122">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="79030-123">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是使用電腦帳戶 (例如「網路服務」或「本機系統」)，則這部電腦必須受到包含 Windows 使用者的網域信任。</span><span class="sxs-lookup"><span data-stu-id="79030-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows User.</span></span>  
  
-   <span data-ttu-id="79030-124">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。</span><span class="sxs-lookup"><span data-stu-id="79030-124">Use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
  
