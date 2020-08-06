---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702929"
---
# <a name="mssqlserver_21889"></a><span data-ttu-id="f2647-102">MSSQLSERVER_21889</span><span class="sxs-lookup"><span data-stu-id="f2647-102">MSSQLSERVER_21889</span></span>
    
## <a name="details"></a><span data-ttu-id="f2647-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2647-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2647-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f2647-104">Product Name</span></span>|<span data-ttu-id="f2647-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2647-105">SQL Server</span></span>|  
|<span data-ttu-id="f2647-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f2647-106">Event ID</span></span>|<span data-ttu-id="f2647-107">21889</span><span class="sxs-lookup"><span data-stu-id="f2647-107">21889</span></span>|  
|<span data-ttu-id="f2647-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f2647-108">Event Source</span></span>|<span data-ttu-id="f2647-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f2647-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f2647-110">元件</span><span class="sxs-lookup"><span data-stu-id="f2647-110">Component</span></span>|<span data-ttu-id="f2647-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f2647-111">SQLEngine</span></span>|  
|<span data-ttu-id="f2647-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f2647-112">Symbolic Name</span></span>|<span data-ttu-id="f2647-113">SQLErrorNum21889</span><span class="sxs-lookup"><span data-stu-id="f2647-113">SQLErrorNum21889</span></span>|  
|<span data-ttu-id="f2647-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f2647-114">Message Text</span></span>|<span data-ttu-id="f2647-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 '%s' 並不是複寫發行者。</span><span class="sxs-lookup"><span data-stu-id="f2647-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' is not a replication publisher.</span></span> <span data-ttu-id="f2647-116">請在具備散發者 '%s' 之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 '%s' 上執行 `sp_adddistributor`，以便讓執行個體主控發行資料庫 '%s'。</span><span class="sxs-lookup"><span data-stu-id="f2647-116">Run `sp_adddistributor` on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' with distributor '%s' in order to enable the instance to host the publishing database '%s'.</span></span> <span data-ttu-id="f2647-117">請確定將其登入和密碼指定為與原始發行者所使用者相同。</span><span class="sxs-lookup"><span data-stu-id="f2647-117">Make certain to specify the same login and password as that used for the original publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2647-118">說明</span><span class="sxs-lookup"><span data-stu-id="f2647-118">Explanation</span></span>  
 <span data-ttu-id="f2647-119">若要裝載發行者資料庫，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須是複寫發行者。</span><span class="sxs-lookup"><span data-stu-id="f2647-119">In order to host the publisher database, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be a replication publisher.</span></span> <span data-ttu-id="f2647-120">`sp_validate_redirected_publisher` 會呼叫遠端伺服器上的 `sp_helpdistributor`，以便判斷伺服器是否為複寫發行者。</span><span class="sxs-lookup"><span data-stu-id="f2647-120">`sp_validate_redirected_publisher` calls `sp_helpdistributor` at the remote server to determine whether the server is a replication publisher.</span></span> <span data-ttu-id="f2647-121">當 `sp_helpdistributor` 預存程序的執行結果表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的目標執行個體不是複寫發行者時，就會傳回此錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2647-121">This error is returned when execution of the stored procedure `sp_helpdistributor` indicates that the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not a replication publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2647-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f2647-122">User Action</span></span>  
 <span data-ttu-id="f2647-123">請在裝載發行者資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行 `sp_adddistributor`。</span><span class="sxs-lookup"><span data-stu-id="f2647-123">Execute `sp_adddistributor` at the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the publisher database.</span></span> <span data-ttu-id="f2647-124">執行 `sp_adddistributor` 時，請指定正確的散發者。</span><span class="sxs-lookup"><span data-stu-id="f2647-124">When running `sp_adddistributor`, specify the correct distributor.</span></span> <span data-ttu-id="f2647-125">針對參數使用與一開始在散發者端執行時所使用的相同值 *@password* `sp_adddistributor` 。</span><span class="sxs-lookup"><span data-stu-id="f2647-125">Use the same value for the *@password* parameter as that used when `sp_adddistributor` was initially run at the distributor.</span></span>  
  
  
