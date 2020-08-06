---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34414754ea9d25ad89f6aba767197eb1dfc10d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596030"
---
# <a name="mssqlserver_3151"></a><span data-ttu-id="3c279-102">MSSQLSERVER_3151</span><span class="sxs-lookup"><span data-stu-id="3c279-102">MSSQLSERVER_3151</span></span>
    
## <a name="details"></a><span data-ttu-id="3c279-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c279-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c279-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3c279-104">Product Name</span></span>|<span data-ttu-id="3c279-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3c279-105">SQL Server</span></span>|  
|<span data-ttu-id="3c279-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3c279-106">Event ID</span></span>|<span data-ttu-id="3c279-107">3151</span><span class="sxs-lookup"><span data-stu-id="3c279-107">3151</span></span>|  
|<span data-ttu-id="3c279-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3c279-108">Event Source</span></span>|<span data-ttu-id="3c279-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3c279-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3c279-110">元件</span><span class="sxs-lookup"><span data-stu-id="3c279-110">Component</span></span>|<span data-ttu-id="3c279-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3c279-111">SQLEngine</span></span>|  
|<span data-ttu-id="3c279-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3c279-112">Symbolic Name</span></span>|<span data-ttu-id="3c279-113">LDDB_MASTER_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="3c279-113">LDDB_MASTER_LOAD_FAILED</span></span>|  
|<span data-ttu-id="3c279-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3c279-114">Message Text</span></span>|<span data-ttu-id="3c279-115">無法還原 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c279-115">Failed to restore master database.</span></span> <span data-ttu-id="3c279-116">正在關閉 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="3c279-116">Shutting down SQL Server.</span></span> <span data-ttu-id="3c279-117">Check the error logs, and rebuild the master database.</span><span class="sxs-lookup"><span data-stu-id="3c279-117">Check the error logs, and rebuild the master database.</span></span> <span data-ttu-id="3c279-118">如需有關如何重建 master 資料庫的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="3c279-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c279-119">說明</span><span class="sxs-lookup"><span data-stu-id="3c279-119">Explanation</span></span>  
 <span data-ttu-id="3c279-120">這是指出 **master** 資料庫發生各種問題的一般錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3c279-120">This is a general error message indicating various problems with the **master** database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c279-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3c279-121">User Action</span></span>  
 <span data-ttu-id="3c279-122">檢查錯誤記錄檔以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3c279-122">Check the error logs for more information.</span></span> <span data-ttu-id="3c279-123">若要建立可以使用的 **master** 資料庫，請執行 Setup.exe，並指定 REBUILDDATABASE 選項。</span><span class="sxs-lookup"><span data-stu-id="3c279-123">To create a usable **master** database, run Setup.exe with the REBUILDDATABASE option.</span></span> <span data-ttu-id="3c279-124">如需詳細資訊，請參閱＜如何：從命令提示字元安裝 SQL Server＞(位於《SQL Server 線上叢書》中)。</span><span class="sxs-lookup"><span data-stu-id="3c279-124">For more information see "How to: Install SQL Server from the Command Prompt" in SQL Server Books Online.</span></span>  
  
  
