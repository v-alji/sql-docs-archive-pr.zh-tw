---
title: MSSQLSERVER_18752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a463e4019875f4a233ae2920f32bc2252376a41c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595079"
---
# <a name="mssqlserver_18752"></a><span data-ttu-id="99041-102">MSSQLSERVER_18752</span><span class="sxs-lookup"><span data-stu-id="99041-102">MSSQLSERVER_18752</span></span>
    
## <a name="details"></a><span data-ttu-id="99041-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99041-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99041-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99041-104">Product Name</span></span>|<span data-ttu-id="99041-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="99041-105">SQL Server</span></span>|  
|<span data-ttu-id="99041-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99041-106">Event ID</span></span>|<span data-ttu-id="99041-107">18752</span><span class="sxs-lookup"><span data-stu-id="99041-107">18752</span></span>|  
|<span data-ttu-id="99041-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="99041-108">Event Source</span></span>|<span data-ttu-id="99041-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="99041-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="99041-110">元件</span><span class="sxs-lookup"><span data-stu-id="99041-110">Component</span></span>|<span data-ttu-id="99041-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="99041-111">SQLEngine</span></span>|  
|<span data-ttu-id="99041-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99041-112">Symbolic Name</span></span>|<span data-ttu-id="99041-113">REPL_INUSE</span><span class="sxs-lookup"><span data-stu-id="99041-113">REPL_INUSE</span></span>|  
|<span data-ttu-id="99041-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99041-114">Message Text</span></span>|<span data-ttu-id="99041-115">一次只有一個記錄讀取器代理程式或記錄檔相關程序 (sp_repldone, sp_replcmds, and sp_replshowcmds) 可連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="99041-115">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="99041-116">若您已執行記錄檔相關程序，請卸除執行程序的連接，或者利用該連接執行 sp_replflush 之後，再啟動記錄讀取器代理程式或執行其他記錄檔相關程序。</span><span class="sxs-lookup"><span data-stu-id="99041-116">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99041-117">說明</span><span class="sxs-lookup"><span data-stu-id="99041-117">Explanation</span></span>  
 <span data-ttu-id="99041-118">每次只有一個記錄讀取器代理程式或記錄檔相關程序可以連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="99041-118">Only one Log Reader agent or log-related procedure can connect to a database at a time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99041-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99041-119">User Action</span></span>  
 <span data-ttu-id="99041-120">確定沒有其他記錄讀取器正在針對相同的發行資料庫執行，而且沒有其他使用中的連接先前已經執行 sp_replcmds/sp_repltrans/sp_repldone 而事後沒有執行 sp_replflush 或中斷連接。</span><span class="sxs-lookup"><span data-stu-id="99041-120">Make sure no other logreader is running for the same publishing database, and no other active connection had previously run sp_replcmds/sp_repltrans/sp_repldone without running sp_replflush afterwards or disconnecting.</span></span>  
  
  
