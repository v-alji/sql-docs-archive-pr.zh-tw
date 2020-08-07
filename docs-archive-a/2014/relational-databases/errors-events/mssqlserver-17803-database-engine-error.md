---
title: MSSQLSERVER_17803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be63b3d05bff2ebf90122f66af4297d77376fce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598931"
---
# <a name="mssqlserver_17803"></a><span data-ttu-id="aefa8-102">MSSQLSERVER_17803</span><span class="sxs-lookup"><span data-stu-id="aefa8-102">MSSQLSERVER_17803</span></span>
    
## <a name="details"></a><span data-ttu-id="aefa8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aefa8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aefa8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aefa8-104">Product Name</span></span>|<span data-ttu-id="aefa8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aefa8-105">SQL Server</span></span>|  
|<span data-ttu-id="aefa8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aefa8-106">Event ID</span></span>|<span data-ttu-id="aefa8-107">17803</span><span class="sxs-lookup"><span data-stu-id="aefa8-107">17803</span></span>|  
|<span data-ttu-id="aefa8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aefa8-108">Event Source</span></span>|<span data-ttu-id="aefa8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aefa8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aefa8-110">元件</span><span class="sxs-lookup"><span data-stu-id="aefa8-110">Component</span></span>|<span data-ttu-id="aefa8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aefa8-111">SQLEngine</span></span>|  
|<span data-ttu-id="aefa8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aefa8-112">Symbolic Name</span></span>|<span data-ttu-id="aefa8-113">SRV_NOMEMORY</span><span class="sxs-lookup"><span data-stu-id="aefa8-113">SRV_NOMEMORY</span></span>|  
|<span data-ttu-id="aefa8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aefa8-114">Message Text</span></span>|<span data-ttu-id="aefa8-115">建立連接期間發生記憶體配置錯誤。</span><span class="sxs-lookup"><span data-stu-id="aefa8-115">There was a memory allocation failure during connection establishment.</span></span> <span data-ttu-id="aefa8-116">請減少非必要的記憶體載入，或增加系統記憶體。</span><span class="sxs-lookup"><span data-stu-id="aefa8-116">Reduce nonessential memory load, or increase system memory.</span></span> <span data-ttu-id="aefa8-117">此連接已經關閉。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="aefa8-117">The connection has been closed.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aefa8-118">說明</span><span class="sxs-lookup"><span data-stu-id="aefa8-118">Explanation</span></span>  
 <span data-ttu-id="aefa8-119">伺服器記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="aefa8-119">Server is running out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aefa8-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aefa8-120">User Action</span></span>  
 <span data-ttu-id="aefa8-121">判斷伺服器記憶體不足的原因。</span><span class="sxs-lookup"><span data-stu-id="aefa8-121">Determine the cause for server running out of memory.</span></span> <span data-ttu-id="aefa8-122">一般記憶體疑難排解步驟可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="aefa8-122">Generic memory troubleshooting steps may be useful</span></span>  
  
  
