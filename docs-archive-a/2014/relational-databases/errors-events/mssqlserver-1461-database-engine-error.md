---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6667728b2cc134632ddc538b662d73533ee4d6ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598952"
---
# <a name="mssqlserver_1461"></a><span data-ttu-id="94ed9-102">MSSQLSERVER_1461</span><span class="sxs-lookup"><span data-stu-id="94ed9-102">MSSQLSERVER_1461</span></span>
    
## <a name="details"></a><span data-ttu-id="94ed9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="94ed9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94ed9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="94ed9-104">Product Name</span></span>|<span data-ttu-id="94ed9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="94ed9-105">SQL Server</span></span>|  
|<span data-ttu-id="94ed9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="94ed9-106">Event ID</span></span>|<span data-ttu-id="94ed9-107">1461</span><span class="sxs-lookup"><span data-stu-id="94ed9-107">1461</span></span>|  
|<span data-ttu-id="94ed9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="94ed9-108">Event Source</span></span>|<span data-ttu-id="94ed9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="94ed9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="94ed9-110">元件</span><span class="sxs-lookup"><span data-stu-id="94ed9-110">Component</span></span>|<span data-ttu-id="94ed9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="94ed9-111">SQLEngine</span></span>|  
|<span data-ttu-id="94ed9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="94ed9-112">Symbolic Name</span></span>|<span data-ttu-id="94ed9-113">DBM_SAFETY_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="94ed9-113">DBM_SAFETY_MISMATCH</span></span>|  
|<span data-ttu-id="94ed9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="94ed9-114">Message Text</span></span>|<span data-ttu-id="94ed9-115">在各伺服器上偵測到資料庫 "%.\*ls" 的不同資料庫鏡像安全性層級。</span><span class="sxs-lookup"><span data-stu-id="94ed9-115">Different database mirroring safety levels among servers were detected for database "%.\*ls".</span></span> <span data-ttu-id="94ed9-116">將會使用 FULL 安全性層級。</span><span class="sxs-lookup"><span data-stu-id="94ed9-116">The FULL safety level will be used.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94ed9-117">說明</span><span class="sxs-lookup"><span data-stu-id="94ed9-117">Explanation</span></span>  
 <span data-ttu-id="94ed9-118">由於主體和鏡像資料庫上的交易安全性設定不一致，因此，當修改交易安全性層級時，鏡像連接會中斷。</span><span class="sxs-lookup"><span data-stu-id="94ed9-118">Mirroring connections were broken when the transaction safety level was modified because the transaction safety settings were inconsistent on the principal and mirror databases.</span></span> <span data-ttu-id="94ed9-119">將會使用完整交易安全性的預設安全性設定。</span><span class="sxs-lookup"><span data-stu-id="94ed9-119">The default safety setting of full-transaction safety will be used.</span></span> <span data-ttu-id="94ed9-120">工作階段將以高安全性模式執行。</span><span class="sxs-lookup"><span data-stu-id="94ed9-120">The session will run in high-safety mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94ed9-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="94ed9-121">User Action</span></span>  
 <span data-ttu-id="94ed9-122">若要將交易安全性設為關閉，請在主體資料庫上重新執行 ALTER DATABASE *database_name* SET PARTNER SAFETY OFF 陳述式。</span><span class="sxs-lookup"><span data-stu-id="94ed9-122">To set transaction safety off, rerun the ALTER DATABASE *database_name* SET PARTNER SAFETY OFF statement on the principal database.</span></span>  
  
  
