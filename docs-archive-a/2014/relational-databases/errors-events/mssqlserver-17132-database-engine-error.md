---
title: MSSQLSERVER_17132 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 609b9cea138db15cefd002f494620b5a1da7b208
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699697"
---
# <a name="mssqlserver_17132"></a><span data-ttu-id="2bb1e-102">MSSQLSERVER_17132</span><span class="sxs-lookup"><span data-stu-id="2bb1e-102">MSSQLSERVER_17132</span></span>
    
## <a name="details"></a><span data-ttu-id="2bb1e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2bb1e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2bb1e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2bb1e-104">Product Name</span></span>|<span data-ttu-id="2bb1e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2bb1e-105">SQL Server</span></span>|  
|<span data-ttu-id="2bb1e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2bb1e-106">Event ID</span></span>|<span data-ttu-id="2bb1e-107">17132</span><span class="sxs-lookup"><span data-stu-id="2bb1e-107">17132</span></span>|  
|<span data-ttu-id="2bb1e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2bb1e-108">Event Source</span></span>|<span data-ttu-id="2bb1e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2bb1e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2bb1e-110">元件</span><span class="sxs-lookup"><span data-stu-id="2bb1e-110">Component</span></span>|<span data-ttu-id="2bb1e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2bb1e-111">SQLEngine</span></span>|  
|<span data-ttu-id="2bb1e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2bb1e-112">Symbolic Name</span></span>|<span data-ttu-id="2bb1e-113">INIT_NODESSPACE</span><span class="sxs-lookup"><span data-stu-id="2bb1e-113">INIT_NODESSPACE</span></span>|  
|<span data-ttu-id="2bb1e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2bb1e-114">Message Text</span></span>|<span data-ttu-id="2bb1e-115">由於描述項的記憶體不足使伺服器無法啟動。</span><span class="sxs-lookup"><span data-stu-id="2bb1e-115">Server startup failed due to insufficient memory for descriptor.</span></span> <span data-ttu-id="2bb1e-116">請減少非必要的記憶體載入或增加系統記憶體。</span><span class="sxs-lookup"><span data-stu-id="2bb1e-116">Reduce non-essential memory load or increase system memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2bb1e-117">說明</span><span class="sxs-lookup"><span data-stu-id="2bb1e-117">Explanation</span></span>  
 <span data-ttu-id="2bb1e-118">無法配置足夠的記憶體來儲存伺服器內部描述項。</span><span class="sxs-lookup"><span data-stu-id="2bb1e-118">Failed to allocate enough memory to store server internal descriptor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2bb1e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2bb1e-119">User Action</span></span>  
 <span data-ttu-id="2bb1e-120">為電腦增加更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="2bb1e-120">Add more memory to the machine.</span></span> <span data-ttu-id="2bb1e-121">一般記憶體疑難排解步驟可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="2bb1e-121">Generic memory troubleshooting steps may be useful.</span></span>  
  
  
