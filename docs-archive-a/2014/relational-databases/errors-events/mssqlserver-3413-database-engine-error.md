---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a5d59ea61cff7051c3e1163a463c29443c553923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598904"
---
# <a name="mssqlserver_3413"></a><span data-ttu-id="c9c6a-102">MSSQLSERVER_3413</span><span class="sxs-lookup"><span data-stu-id="c9c6a-102">MSSQLSERVER_3413</span></span>
    
## <a name="details"></a><span data-ttu-id="c9c6a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c9c6a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9c6a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c9c6a-104">Product Name</span></span>|<span data-ttu-id="c9c6a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9c6a-105">SQL Server</span></span>|  
|<span data-ttu-id="c9c6a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c9c6a-106">Event ID</span></span>|<span data-ttu-id="c9c6a-107">3413</span><span class="sxs-lookup"><span data-stu-id="c9c6a-107">3413</span></span>|  
|<span data-ttu-id="c9c6a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c9c6a-108">Event Source</span></span>|<span data-ttu-id="c9c6a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c9c6a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c9c6a-110">元件</span><span class="sxs-lookup"><span data-stu-id="c9c6a-110">Component</span></span>|<span data-ttu-id="c9c6a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c9c6a-111">SQLEngine</span></span>|  
|<span data-ttu-id="c9c6a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c9c6a-112">Symbolic Name</span></span>|<span data-ttu-id="c9c6a-113">MARKDB</span><span class="sxs-lookup"><span data-stu-id="c9c6a-113">MARKDB</span></span>|  
|<span data-ttu-id="c9c6a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c9c6a-114">Message Text</span></span>|<span data-ttu-id="c9c6a-115">資料庫識別碼 %d。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-115">Database ID %d.</span></span> <span data-ttu-id="c9c6a-116">無法將資料庫標示為有疑問。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-116">Could not mark database as suspect.</span></span> <span data-ttu-id="c9c6a-117">sys.databases.database_id 上的 Getnext NC 掃描失敗。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-117">Getnext NC scan on sys.databases.database_id failed.</span></span> <span data-ttu-id="c9c6a-118">請參閱錯誤記錄檔中之前的錯誤，以找出原因，並修正所有相關問題。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-118">Refer to previous errors in the error log to identify the cause and correct any associated problems.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9c6a-119">說明</span><span class="sxs-lookup"><span data-stu-id="c9c6a-119">Explanation</span></span>  
 <span data-ttu-id="c9c6a-120">嘗試在目錄中將使用者資料庫標示為 SUSPECT 時發生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-120">There was an unexpected failure while trying to mark a user database as SUSPECT in the catalog.</span></span> <span data-ttu-id="c9c6a-121">SUSPECT 狀態不會保存下來。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-121">The SUSPECT state will not be persisted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9c6a-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c9c6a-122">User Action</span></span>  
 <span data-ttu-id="c9c6a-123">參閱先前的錯誤並更正問題。</span><span class="sxs-lookup"><span data-stu-id="c9c6a-123">See previous errors and correct the problem.</span></span>  
  
  
