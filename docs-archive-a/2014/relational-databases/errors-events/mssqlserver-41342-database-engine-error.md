---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0269322b30cee88e5ba3d50b6d391464b735f54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597875"
---
# <a name="mssqlserver_41342"></a><span data-ttu-id="e4de0-102">MSSQLSERVER_41342</span><span class="sxs-lookup"><span data-stu-id="e4de0-102">MSSQLSERVER_41342</span></span>
    
## <a name="details"></a><span data-ttu-id="e4de0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e4de0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4de0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e4de0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="e4de0-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e4de0-105">Event ID</span></span>|<span data-ttu-id="e4de0-106">41342</span><span class="sxs-lookup"><span data-stu-id="e4de0-106">41342</span></span>|  
|<span data-ttu-id="e4de0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e4de0-107">Event Source</span></span>|<span data-ttu-id="e4de0-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e4de0-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e4de0-109">元件</span><span class="sxs-lookup"><span data-stu-id="e4de0-109">Component</span></span>|<span data-ttu-id="e4de0-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e4de0-110">SQLEngine</span></span>|  
|<span data-ttu-id="e4de0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e4de0-111">Symbolic Name</span></span>|<span data-ttu-id="e4de0-112">HK_HW_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="e4de0-112">HK_HW_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="e4de0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e4de0-113">Message Text</span></span>|<span data-ttu-id="e4de0-114">系統上的處理器型號不支援建立 *construct*。</span><span class="sxs-lookup"><span data-stu-id="e4de0-114">The model of the processor on the system does not support creating *construct*.</span></span> <span data-ttu-id="e4de0-115">此錯誤通常會在舊型處理器上發生。</span><span class="sxs-lookup"><span data-stu-id="e4de0-115">This error typically occurs with older processors.</span></span> <span data-ttu-id="e4de0-116">如需支援型號的資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e4de0-116">See [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for information on supported models.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e4de0-117">說明</span><span class="sxs-lookup"><span data-stu-id="e4de0-117">Explanation</span></span>  
 <span data-ttu-id="e4de0-118">記憶體最佳化資料表需要支援在 128 位元值上進行不可部分完成的比較與交換作業的處理器型號，這動作需要組件指令 CMPXCHG16B。</span><span class="sxs-lookup"><span data-stu-id="e4de0-118">Memory-optimized tables require a processor model that supports atomic compare-and-exchange operations on 128-bit values, which require the assembly instruction CMPXCHG16B.</span></span> <span data-ttu-id="e4de0-119">某些舊版 AMD 處理器模型不支援 CMPXCHG16B 指令。</span><span class="sxs-lookup"><span data-stu-id="e4de0-119">Certain older AMD processor models do not support the CMPXCHG16B instruction.</span></span> <span data-ttu-id="e4de0-120">此外，某些虛擬化環境預設為不啟用這個指令。</span><span class="sxs-lookup"><span data-stu-id="e4de0-120">Also, certain virtualization environments do not enable this instruction by default.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e4de0-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e4de0-121">User Action</span></span>  
 <span data-ttu-id="e4de0-122">升級處理器。</span><span class="sxs-lookup"><span data-stu-id="e4de0-122">Upgrade your processor.</span></span> <span data-ttu-id="e4de0-123">如果您的處理器支援該指令，而且您是在虛擬機器上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請變更組態以支援指令 CMPXCHG16B。</span><span class="sxs-lookup"><span data-stu-id="e4de0-123">If your processor supports the instruction and you are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a virtual machine, change the configuration to support the instruction CMPXCHG16B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4de0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4de0-124">See Also</span></span>  
 [<span data-ttu-id="e4de0-125">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="e4de0-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
