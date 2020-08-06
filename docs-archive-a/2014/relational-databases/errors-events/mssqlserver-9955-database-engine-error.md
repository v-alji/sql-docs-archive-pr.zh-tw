---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56b9f9b4b7923f8973bd7167c3c1bf77e92300c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595025"
---
# <a name="mssqlserver_9955"></a><span data-ttu-id="12023-102">MSSQLSERVER_9955</span><span class="sxs-lookup"><span data-stu-id="12023-102">MSSQLSERVER_9955</span></span>
    
## <a name="details"></a><span data-ttu-id="12023-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12023-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12023-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="12023-104">Product Name</span></span>|<span data-ttu-id="12023-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12023-105">SQL Server</span></span>|  
|<span data-ttu-id="12023-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="12023-106">Event ID</span></span>|<span data-ttu-id="12023-107">9955</span><span class="sxs-lookup"><span data-stu-id="12023-107">9955</span></span>|  
|<span data-ttu-id="12023-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="12023-108">Event Source</span></span>|<span data-ttu-id="12023-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12023-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12023-110">元件</span><span class="sxs-lookup"><span data-stu-id="12023-110">Component</span></span>|<span data-ttu-id="12023-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12023-111">SQLEngine</span></span>|  
|<span data-ttu-id="12023-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="12023-112">Symbolic Name</span></span>|<span data-ttu-id="12023-113">FTXT2_MSSEARCHACCESSDENY</span><span class="sxs-lookup"><span data-stu-id="12023-113">FTXT2_MSSEARCHACCESSDENY</span></span>|  
|<span data-ttu-id="12023-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="12023-114">Message Text</span></span>|<span data-ttu-id="12023-115">SQL Server 無法建立具名管道 '%ls' 來與全文檢索篩選背景程式進行通訊 (Windows 錯誤: %d)。</span><span class="sxs-lookup"><span data-stu-id="12023-115">SQL Server failed to create named pipe '%ls' to communicate with the full-text filter daemon (Windows error: %d).</span></span> <span data-ttu-id="12023-116">可能是篩選背景程式主機處理序已經有具名管道，系統資源不足，或是篩選背景程式帳戶群組的安全性識別碼 (SID) 查閱失敗。</span><span class="sxs-lookup"><span data-stu-id="12023-116">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span> <span data-ttu-id="12023-117">若要解決這個錯誤，請終止任何執行中的全文檢索篩選背景程式處理序，並視需要重新設定全文檢索背景程式啟動器服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="12023-117">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon launcher service account.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12023-118">說明</span><span class="sxs-lookup"><span data-stu-id="12023-118">Explanation</span></span>  
 <span data-ttu-id="12023-119">出現這則訊息的原因是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法建立具名管道來與全文檢索篩選背景程式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="12023-119">This message occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failed to create a named pipe to communicate with the full-text filter daemon.</span></span> <span data-ttu-id="12023-120">可能是篩選背景程式主機處理序已經有具名管道，系統資源不足，或是篩選背景程式帳戶群組的安全性識別碼 (SID) 查閱失敗。</span><span class="sxs-lookup"><span data-stu-id="12023-120">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12023-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="12023-121">User Action</span></span>  
 <span data-ttu-id="12023-122">若要解決這個錯誤，請終止任何執行中的全文檢索篩選背景程式處理序，並視需要使用 SQL Server 組態管理員來重新設定全文檢索背景程式的主機帳戶。</span><span class="sxs-lookup"><span data-stu-id="12023-122">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon host account by using the SQL Server Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12023-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12023-123">See Also</span></span>  
 <span data-ttu-id="12023-124">[SQL Server 組態管理員](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="12023-124">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="12023-125">[設定全文檢索篩選背景程式啟動器的服務帳戶](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="12023-125">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 [<span data-ttu-id="12023-126">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="12023-126">Full-Text Search</span></span>](../search/full-text-search.md)  
  
  
